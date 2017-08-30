##### Virtuelle Azure-Netzwerke

Durch das Einrichten eines virtuellen Azure-Netzwerk können Sie den Adressbereich der privaten IP-Adressen definieren, die durch die Azure-DHCP-Funktionen zugeordnet werden. In standortübergreifenden Szenarios wird der definierte IP-Adressbereich weiterhin mithilfe von DHCP von Azure zugeordnet. Allerdings erfolgt die Auflösung von Domänennamen lokal (vorausgesetzt, dass die virtuellen Computer einer lokalen Domäne angehören). Darum können auch Adressen außerhalb der verschiedenen Azure-Clouddienste aufgelöst werden.

[comment]: <> (MSSedusch still needed? TODO  Ursprünglich wurde ein virtuelles Azure-Netzwerk an eine Affinitätsgruppe gebunden. Damit war ein virtuelles Netzwerk in Azure auf die Azure-Skalierungseinheit beschränkt, die der Affinitätsgruppe zugewiesen wurde. Das bedeutete im Endeffekt, dass das virtuelle Netzwerk auf die Ressourcen beschränkt war, die in der Azure-Skalierungseinheit verfügbar waren. Dies wurde seitdem geändert, und jetzt können sich virtuelle Azure-Netzwerke über mehrere Azure-Skalierungseinheiten erstrecken. Das erfordert jedoch, dass virtuelle Azure-Netzwerke bei der Erstellung **KEINEN** Affinitätsgruppen mehr zugeordnet werden. Wie bereits erwähnt, sollten Sie entgegen den Empfehlungen von vor einem Jahr **KEINE Azure-Affinitätsgruppen mehr nutzen**. Weitere Informationen finden Sie unter: <https://azure.microsoft.com/blog/regional-virtual-networks/>)

Alle virtuellen Computer in Azure müssen mit einem virtuellen Netzwerk verbunden sein.

Weitere Informationen finden Sie in [diesem Artikel][resource-groups-networking] und auf [dieser Seite](https://azure.microsoft.com/documentation/services/virtual-network/).

[comment]: <> (MShermannd TODO Couldn't find an article which includes the OpenLDAP topic + ARM;)  
[comment]: <> (MSSedusch <https://channel9.msdn.com/Blogs/Open/Load-balancing-highly-available-Linux-services-on-Windows-Azure-OpenLDAP-and-MySQL>)  

> [AZURE.NOTE] Standardmäßig können Sie nach der Bereitstellung eines virtuellen Computers die Konfiguration des virtuellen Netzwerks nicht mehr ändern. Die TCP/IP-Einstellungen müssen dem Azure-DHCP-Server überlassen werden. Das Standardverhalten ist die dynamische IP-Zuweisung.

Die MAC-Adresse der virtuellen Netzwerkkarte kann sich ändern, z.B. nach einer Größenanpassung, und das Windows- oder Linux-Gastbetriebssystem erkennt die neue Netzwerkkarte und verwendet automatisch DHCP zum Zuweisen der IP- und DNS-Adressen.

##### Statische IP-Zuweisung
Es ist möglich, virtuellen Computern in einem virtuellen Azure-Netzwerk feste oder reservierte IP-Adressen zuzuweisen. Das Ausführen der virtuellen Computer in einem virtuellen Azure-Netzwerk eröffnet eine gute Möglichkeit, um diese Funktion für einige Szenarios im Bedarfsfall zu nutzen. Die IP-Zuweisung bleibt während des gesamten Lebenszyklus des virtuellen Computers gültig, unabhängig davon, ob der virtuelle Computer ausgeführt oder heruntergefahren wird. Daher müssen Sie die Gesamtzahl der virtuellen Computer (ausgeführte und beendete virtuelle Computer) berücksichtigen, wenn Sie den IP-Adressbereich für das virtuelle Netzwerk definieren. Die IP-Adresse bleibt zugewiesen, bis der virtuelle Computer und seine Netzwerkschnittstelle gelöscht werden oder bis die Zuweisung der IP-Adresse wieder aufgehoben wird. Ausführliche Informationen finden Sie in [diesem Artikel][virtual-networks-static-private-ip-arm-pportal].

##### Mehrere NICs pro virtuellen Computer
Sie können mehrere virtuelle Netzwerkschnittstellenkarten (vNIC) für virtuelle Azure-Computer definieren. Dank der Möglichkeit, mehrere vNICs einzusetzen, können Sie mit der Einrichtung der Netzwerkdatenverkehrstrennung beginnen. Dabei wird z.B. der Clientdatenverkehr über eine vNIC und der Back-End-Datenverkehr über eine zweite vNIC weitergeleitet. Je nach Typ des virtuellen Computers gibt es unterschiedliche Einschränkungen im Hinblick auf die Anzahl von vNICs. Informationen zu Details, Funktionen und Einschränkungen finden Sie in den folgenden Artikeln:
 
* [Erstellen eines virtuellen Computers mit mehreren Netzwerkschnittstellenkarten (NICs)][virtual-networks-multiple-nics]
* [Bereitstellen von Multi-NIC-VMs mithilfe einer Vorlage][virtual-network-deploy-multinic-arm-template]
* [Bereitstellen von Multi-NIC-VMs mit PowerShell][virtual-network-deploy-multinic-arm-ps]
* [Bereitstellen von Multi-NIC-VMs mithilfe der Azure-CLI][virtual-network-deploy-multinic-arm-cli]

#### Standort-zu-Standort-Konnektivität
"Standortübergreifend" bezieht sich darauf, dass virtuelle Azure-Computer und lokale Computer über eine transparente und permanente VPN-Verbindung verknüpft sind. Dieses Konzept wird wahrscheinlich zum häufigsten SAP-Bereitstellungsmuster in Azure werden. Die Annahme ist, dass betriebliche Verfahren und Prozesse mit SAP-Instanzen in Azure transparent arbeiten sollten. Das bedeutet, dass Sie in der Lage sein sollten, aus diesen Systemen heraus zu drucken und das SAP Transport Management System (TMS) zu verwenden, um Änderungen aus einem Entwicklungssystem in Azure in ein lokal bereitgestelltes Testsystem zu übertragen. Weitere Dokumentationen zu „Standort-zu-Standort“ finden Sie in [diesem Artikel][vpn-gateway-create-site-to-site-rm-powershell].

The rats are on parade
Another mad charade
What you gonna do?
The hounds are on the chase
Everything's erased
What you gonna do?

mehrere Azure-Regionen für ein bestimmtes Abonnement über standortübergreifende Konfigurationen genutzt werden.

Weitere Dokumentationen finden Sie in [diesem Artikel][vpn-gateway-create-site-to-site-rm-powershell].
[comment]: <> (MShermannd TODO found no ARM docu link)

#### VNet-zu-VNet-Verbindung
