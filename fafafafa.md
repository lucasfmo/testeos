#### Azure-Standardspeicher
Azure-Standard-BLOB-Speicher war der verfügbare Speichertyp, als Azure IaaS veröffentlicht wurde. IOPS-Kontingente wurden für jede einzelne VHD erzwungen. Die Latenz unterschied sich grundlegend von SAN/NAS-Geräten, wie sie in der Regel für lokal gehostete High-End-SAP-Systeme bereitgestellt werden. Dennoch erwies sich der Azure-Standardspeicher für mehrere Hunderte von SAP-Systemen, die in der Zwischenzeit in Azure bereitgestellt wurden, als ausreichend.

Der Azure-Standardspeicher wird basierend auf den tatsächlich gespeicherten Daten, der Menge der Speichertransaktionen, den ausgehenden Datenübertragungen und der ausgewählten Redundanzoption in Rechnung gestellt. Viele VHDs können mit der Maximalgröße von 1 TB erstellt werden, aber solange sie leer bleiben, werden sie nicht in Rechnung gestellt. Wenn Sie dann eine virtuelle Festplatte mit 100 GB füllen, wird Ihnen das Speichern von 100 GB in Rechnung gestellt, nicht die nominale Größe, mit der die virtuelle Festplatte erstellt wurde.

#### <a name="ff5ad0f9-f7f4-4022-9102-af07aef3bc92"></a>Azure Storage Premium
Im April 2015 stellte Microsoft Azure Storage Premium vor. Storage Premium wurde mit dem Ziel, Folgendes bereitzustellen, eingeführt:

* Bessere E/A-Latenz.
* Besserer Durchsatz.
* Weniger variierende E/A-Latenz.

Zu diesem Zweck wurden viele Änderungen eingeführt. Die beiden wichtigsten sind folgende:

* Verwendung von SSD-Laufwerken in Azure Storage-Knoten
* Ein neuer Lesecache, der durch die lokale SSD eines Azure-Serverknotens unterstützt wird

Im Gegensatz zum standardmäßigen Speicher, bei dem sich Funktionen nicht abhängig von der Größe der Festplatte (oder der VHD) änderten, verfügt Storage Premium derzeit über drei unterschiedliche Datenträgerkategorien, die Sie am Ende dieses Artikels vor dem FAQ-Abschnitt sehen können: <https://azure.microsoft.com/pricing/details/storage/>

Sie sehen, dass IOPS-/VHD- und Datenträgerdurchsatz von der Größenkategorie der Datenträger abhängen.

Kostenbasis im Falle von Storage Premium ist nicht der tatsächliche Datenumfang, der in diesen VHDs gespeichert wird, sondern die Größenkategorie einer solchen virtuellen Festplatte, unabhängig von der Datenmenge, die auf der virtuellen Festplatte gespeichert wird.

Sie können auch virtuelle Festplatten in Storage Premium erstellen, die den unten gezeigten Größenkategorien nicht direkt zugeordnet sind. Insbesondere beim Kopieren von VHDs aus dem Standardspeicher zu Storage Premium kann dies der Fall sein. Hier erfolgt eine Zuordnung zur nächstgrößeren Storage Premium-Datenträgeroption.

Beachten Sie, dass nur bestimmte VM-Serien von Azure Storage Premium profitieren können. Stand Dezember 2015 sind das die DS- und die GS-Serien. Die DS-Serie entspricht im Grunde der D-Serie, mit der Ausnahme, dass die DS-Serie die Möglichkeit hat, Storage Premium-basierte virtuelle Computer zusätzlich zu virtuellen Festplatten, die im Azure-Standardspeicher gehostet werden, bereitzustellen. Dasselbe gilt für die G-Serie im Vergleich zur GS-Serie.

Wenn Sie sich den Teil zu virtuellen Computern der DS-Serie [in diesem Artikel][virtual-machines-sizes] ansehen, erkennen Sie auch, dass es Datenmengeneinschränkungen für Storage Premium-VHDs bezüglich der Granularität der VM-Stufe gibt. Unterschiedliche virtuelle Computer der DS-Serie oder der GS-Serie verfügen auch über andere Einschränkungen im Hinblick auf die Anzahl der virtuellen Festplatten, die bereitgestellt werden können. Diese Einschränkungen werden ebenfalls im oben erwähnten Artikel dokumentiert. Aber im Wesentlichen bedeutet das Folgendes: Wenn Sie z.B. 32 P30-Datenträger/-VHDs auf einem einzelnen virtuellen DS14-Computer bereitstellen, erhalten Sie NICHT das 32-fache des maximalen Durchsatzes eines P30-Datenträgers. Stattdessen beschränkt der maximale Durchsatz auf VM-Ebene, wie im Artikel dokumentiert, den Datendurchsatz.

Weitere Informationen zu Storage Premium finden Sie hier: <http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2>

#### Azure-Speicherkonten
Wenn Sie Dienste oder virtuelle Computer in Azure bereitstellen, muss die Bereitstellung von VHDs und VM-Images in so genannten Azure-Speicherkonten organisiert werden. Wenn Sie eine Azure-Bereitstellung planen, müssen Sie die Einschränkungen von Azure sorgfältig berücksichtigen. Einerseits gibt es eine begrenzte Anzahl von Speicherkonten pro Azure-Abonnement. Obwohl jedes Azure-Speicherkonto eine große Anzahl von VHD-Dateien enthalten kann, besteht eine feste Obergrenze für die Gesamt-IOPS pro Speicherkonto. Bei der Bereitstellung von Hunderten von SAP-VMs mit DBMS-Systemen, die umfassende E/A-Aufrufe erzeugen, wird empfohlen, virtuelle Computer mit hoher IOPS DBMS auf mehrere Azure-Speicherkonten zu verteilen. Achten Sie darauf, das aktuelle Limit für Azure-Speicherkonten pro Abonnement nicht zu überschreiten. Da der Speicher ein wesentlicher Teil der Datenbankbereitstellung für ein SAP-System ist, wird dieses Konzept detaillierter im bereits erwähnten [DBMS-Bereitstellungshandbuch][dbms-guide] erläutert.

Weitere Informationen zu Azure-Speicherkonten finden Sie in [diesem Artikel][storage-scalability-targets]. In diesem Artikel werden Sie feststellen, dass es Unterschiede hinsichtlich der Einschränkungen zwischen Azure-Standardspeicherkonten und Storage Premium-Konten gibt. Hauptunterschied ist die Datenmenge, die innerhalb eines solchen Speicherkontos gespeichert werden kann. Beim Standardspeicher ist die Menge wesentlich größer als bei Storage Premium. Auf der anderen Seite ist das Standardspeicherkonto hinsichtlich IOPS stark eingeschränkt (siehe Spalte "Total Request Rate"), während das Azure Storage Premium-Konto keine solche Einschränkung aufweist. Bei der Erörterung der Bereitstellung von SAP-Systemen, insbesondere der DBMS-Server, werden Details und Ergebnisse dieser Unterschiede erläutert.

Innerhalb eines Speicherkontos haben Sie die Möglichkeit, unterschiedliche Container für die Organisation und Kategorisierung verschiedener VHDs zu erstellen. Diese Container werden in der Regel verwendet, um z.B. virtuelle Festplatten unterschiedlicher virtueller Computer zu trennen. Es gibt keine Leistungseinbußen bei der Verwendung von nur einem Container oder mehrerer Container unter einem einzelnen Azure-Speicherkonto.

Innerhalb von Azure folgt ein VHD-Name der folgenden Benennungskonvention, die einen eindeutigen Namen für die virtuelle Festplatte in Azure bereitstellen muss:

	http(s)://<storage account name>.blob.core.windows.net/<container name>/<vhd name>

Wie bereits erwähnt, muss die oben genannten Zeichenfolge die virtuellen Festplatte, die in Azure Storage gespeichert ist, eindeutig identifizieren.

### <a name="61678387-8868-435d-9f8c-450b2424f5bd"></a>Microsoft Azure-Netzwerk
Microsoft Azure stellt eine Netzwerkinfrastruktur bereit, die die Zuordnung aller Szenarios ermöglicht, die wir mit SAP-Software umsetzen möchten. Die Funktionen sind:

* Zugriff von außen direkt auf die virtuellen Computer über Windows Terminal Services oder ssh/VNC
* Zugriff auf Dienste und bestimmte Ports, die von Anwendungen auf den virtuellen Computern verwendet werden
* Interne Kommunikation und Namensauflösung zwischen einer Gruppe von virtuellen Computern, die als virtuelle Azure-Computer bereitgestellt werden
* Standortübergreifende Konnektivität zwischen einem lokalen Kundennetzwerk und dem Azure-Netzwerk
* Azure-Region-übergreifende Konnektivität oder Rechenzentrumskonnektivität zwischen Azure-Standorten

Weitere Informationen finden Sie hier: <https://azure.microsoft.com/documentation/services/virtual-network/>

Es gibt viele verschiedene Möglichkeiten zum Konfigurieren der Namens- und IP-Auflösung in Azure. In diesem Dokument benötigen Nur-Cloud-Szenarios die standardmäßige Verwendung von Azure DNS (im Gegensatz zum Definieren eines eigenen DNS-Diensts). Es gibt auch einen neueren Azure DNS-Dienst, der verwendet werden kann, anstatt einen eigenen DNS-Server einzurichten. Weitere Informationen finden Sie in [diesem Artikel][virtual-networks-manage-dns-in-vnet] und auf [dieser Seite](https://azure.microsoft.com/services/dns/).

Für standortübergreifende Szenarios verlassen wir uns auf die Tatsache, dass das lokale AD/OpenLDAP/DNS über VPN- oder private Verbindungen zu Azure erweitert wurde. Für bestimmte hier dokumentierte Szenarios kann es notwendig sein, ein AD/OpenLDAP-Replikat in Azure zu installieren.

Da Netzwerk und Namensauflösung wesentliche Teile der Datenbankbereitstellung für ein SAP-System sind, wird dieses Konzept detaillierter im [DBMS-Bereitstellungshandbuch][dbms-guide] erläutert.


##### Virtuelle Azure-Netzwerke

Durch das Einrichten eines virtuellen Azure-Netzwerk können Sie den Adressbereich der privaten IP-Adressen definieren, die durch die Azure-DHCP-Funktionen zugeordnet werden. In standortübergreifenden Szenarios wird der definierte IP-Adressbereich weiterhin mithilfe von DHCP von Azure zugeordnet. Allerdings erfolgt die Auflösung von Domänennamen lokal (vorausgesetzt, dass die virtuellen Computer einer lokalen Domäne angehören). Darum können auch Adressen außerhalb der verschiedenen Azure-Clouddienste aufgelöst werden.

[comment]: <> (MSSedusch still needed? TODO
Ursprünglich wurde ein virtuelles Azure-Netzwerk an eine Affinitätsgruppe gebunden. Damit war ein virtuelles Netzwerk in Azure auf die Azure-Skalierungseinheit beschränkt, die der Affinitätsgruppe zugewiesen wurde. Das bedeutete im Endeffekt, dass das virtuelle Netzwerk auf die Ressourcen beschränkt war, die in der Azure-Skalierungseinheit verfügbar waren. Dies wurde seitdem geändert, und jetzt können sich virtuelle Azure-Netzwerke über mehrere Azure-Skalierungseinheiten erstrecken. Das erfordert jedoch, dass virtuelle Azure-Netzwerke bei der Erstellung **KEINEN** Affinitätsgruppen mehr zugeordnet werden. Wie bereits erwähnt, sollten Sie entgegen den Empfehlungen von vor einem Jahr **KEINE Azure-Affinitätsgruppen mehr nutzen**. Weitere Informationen finden Sie unter: <https://azure.microsoft.com/blog/regional-virtual-networks/>

Alle virtuellen Computer in Azure müssen mit einem virtuellen Netzwerk verbunden sein.

Weitere Informationen finden Sie in [diesem Artikel][resource-groups-networking] und auf [dieser Seite](https://azure.microsoft.com/documentation/services/virtual-network/).

[comment]: <> (MShermannd TODO Couldn't find an article which includes the OpenLDAP topic + ARM; ) 
[comment]: <> (MSSedusch <https://channel9.msdn.com/Blogs/Open/Load-balancing-highly-available-Linux-services-on-Windows-Azure-OpenLDAP-and-MySQL>)

> [AZURE.NOTE] Standardmäßig können Sie nach der Bereitstellung eines virtuellen Computers die Konfiguration des virtuellen Netzwerks nicht mehr ändern. Die TCP/IP-Einstellungen müssen dem Azure-DHCP-Server überlassen werden. Das Standardverhalten ist die dynamische IP-Zuweisung.

Die MAC-Adresse der virtuellen Netzwerkkarte kann sich ändern, z.B. nach einer Größenanpassung, und das Windows- oder Linux-Gastbetriebssystem erkennt die neue Netzwerkkarte und verwendet automatisch DHCP zum Zuweisen der IP- und DNS-Adressen.

##### Statische IP-Zuweisung
Es ist möglich, virtuellen Computern in einem virtuellen Azure-Netzwerk feste oder reservierte IP-Adressen zuzuweisen. Das Ausführen der virtuellen Computer in einem virtuellen Azure-Netzwerk eröffnet eine gute Möglichkeit, um diese Funktion für einige Szenarios im Bedarfsfall zu nutzen. Die IP-Zuweisung bleibt während des gesamten Lebenszyklus des virtuellen Computers gültig, unabhängig davon, ob der virtuelle Computer ausgeführt oder heruntergefahren wird. Daher müssen Sie die Gesamtzahl der virtuellen Computer (ausgeführte und beendete virtuelle Computer) berücksichtigen, wenn Sie den IP-Adressbereich für das virtuelle Netzwerk definieren. Die IP-Adresse bleibt zugewiesen, bis der virtuelle Computer und seine Netzwerkschnittstelle gelöscht werden oder bis die Zuweisung der IP-Adresse wieder aufgehoben wird. Ausführliche Informationen finden Sie in [diesem Artikel][virtual-networks-static-private-ip-arm-pportal].
