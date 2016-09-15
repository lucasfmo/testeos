<properties
    pageTitle="Windows Backup to Azure Backup/Schedule backup for a Windows Server or a client"
    description="Windows Backup -> Azure Backup/Plánování zálohování pro Windows Server nebo klienta"
    service="microsoft.recoveryservices"
    resource="vaults"
    authors="aashu"
    displayOrder=""
    selfHelpType="generic"
    supportTopicIds="32447383"
    resourceTags=""
    productPesIds="15207"
    cloudEnvironments="public"
/>

# Windows Backup Azure Backup/Plánování zálohování pro Windows Server nebo klienta

Pokud se potýkáte s problémy, že zálohování souborů a složek Windows Serveru je velmi pomalé, zkuste prosím některé z dál uvedených pokynů.

## **Doporučené kroky**

* Zálohovaný server naráží na omezení výkonu, což způsobuje pomalé zálohování. <br>
[Čítače výkonu a doporučené rozsahy pro optimální zálohování](https://azure.microsoft.com/en-us/documentation/articles/backup-azure-troubleshoot-slow-backup-performance-issue/#cause-1-backup-slow-due-to-performance-bottlenecks-on-the-computer-thats-being-backed-up)

* Jiný proces nebo antivirový program interferuje se službou Azure Backup, což způsobuje, že je zálohování pomalé nebo selhává. <br>
[Kroky k zajištění, že nedochází ke konfliktům s jiným procesem nebo antivirovým programem](https://azure.microsoft.com/en-us/documentation/articles/backup-azure-troubleshoot-slow-backup-performance-issue/#cause-2-another-process-or-antivirus-software-is-interfering-with-the-azure-backup-process)

* Zálohování jednotlivých souborů a složek ve virtuálním počítači Azure IaaS je velmi pomalé. <br>
[Kroky k optimalizaci výkonu pro virtuální počítač Azure](https://azure.microsoft.com/en-us/documentation/articles/backup-azure-troubleshoot-slow-backup-performance-issue/#cause-3-the-backup-agent-is-running-in-an-azure-virtual-machine-vm)

* Zálohování velkého počtu (mnoha milionů) malých souborů je velmi pomalé. <br>
[Kroky k pochopení problémových míst v případě velkého počtu souborů](https://azure.microsoft.com/en-us/documentation/articles/backup-azure-troubleshoot-slow-backup-performance-issue/#cause-4-backing-up-a-large-number-multi-millions-of-files)

* Podrobný návod pro nastavení zálohování souborů a složek pomocí agenta Azure Backup <br>
[Konfigurace trezoru zálohování](https://azure.microsoft.com/en-us/documentation/articles/backup-configure-vault/)


<!--HONumber=Jul16_HO4-->

