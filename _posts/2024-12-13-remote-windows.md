---
title: "Configurazione amministrazione remota di windows con powershell"
categories:
  - blog
tags:
  - windows
  - powershell
  - controllo remoto

permalink: /blog/windows-remoto/
---

TLDR: comandi per configurare connessione remota powershell.

Per abilitare PowerShell remoting su computer Windows 10/11 in una LAN (non in dominio), sono necessarie alcune configurazioni per garantire che il computer "master" possa comunicare in modo sicuro con gli altri computer. Ecco i passaggi dettagliati:

---

### **1. Abilitare PowerShell Remoting**
Sui computer remoti (client), è necessario abilitare il remoting di PowerShell:

1. **Abilita PSRemoting**:
   - Apri PowerShell come amministratore sul computer remoto.
   - Esegui il comando:
     ```powershell
     Enable-PSRemoting -Force
     ```
   Questo comando:
   - Configura il servizio WinRM.
   - Crea regole del firewall per consentire il traffico WS-Management.

2. **Consenti connessioni non in dominio**:
   - Poiché i computer non sono in un dominio, esegui:
     ```powershell
     Set-Item wsman:\localhost\Client\TrustedHosts -Value "*"
     ```
   Oppure specifica singoli host con:
     ```powershell
     Set-Item wsman:\localhost\Client\TrustedHosts -Value "IP_ComputerMaster"
     ```
   Questo configura gli host attendibili per WinRM.

---

### **2. Configurare il firewall**
Devi assicurarti che il traffico di PowerShell remoting non venga bloccato:

- **Aggiungi regole del firewall**:
  - Sul computer remoto, esegui:
    ```powershell
    New-NetFirewallRule -Name "PSRemoting" -DisplayName "PowerShell Remoting" -Enabled True -Direction Inbound -Protocol TCP -LocalPort 5985
    ```
  - Se vuoi abilitare connessioni HTTPS (porta 5986):
    ```powershell
    Enable-PSRemoting -Force
    winrm quickconfig -Transport:https
    ```

---

### **3. Configurare il servizio WinRM**
Assicurati che il servizio Windows Remote Management (WinRM) sia attivo su tutti i computer remoti:

1. **Abilita e avvia il servizio**:
   ```powershell
   Set-Service -Name WinRM -StartupType Automatic
   Start-Service -Name WinRM
   ```

2. **Verifica la configurazione di WinRM**:
   - Per controllare lo stato di WinRM:
     ```powershell
     winrm enumerate winrm/config/listener
     ```

---

### **4. Impostare l'host master**
Sul computer "master", configura PowerShell per connettersi ai computer remoti:

1. **Abilita TrustedHosts**:
   - Aggiungi i computer remoti agli host attendibili:
     ```powershell
     Set-Item wsman:\localhost\Client\TrustedHosts -Value "IP1,IP2"
     ```

2. **Testa la connessione remota**:
   - Prova a eseguire un comando remoto:
     ```powershell
     Invoke-Command -ComputerName IP_Remoto -ScriptBlock { Get-Process }
     ```

---

### **5. Gestione dei permessi**
1. **Utente amministratore**:
   - L'utente che esegue i comandi remoti deve essere amministratore sul computer remoto.
   - Puoi anche abilitare l'accesso remoto per utenti non amministratori tramite l'aggiunta di privilegi al gruppo `Remote Management Users`.

   ```powershell
   Add-LocalGroupMember -Group "Remote Management Users" -Member "Utente"
   ```

2. **Autenticazione (non in dominio)**:
   - Specifica le credenziali dell'utente remoto durante la connessione:
     ```powershell
     Invoke-Command -ComputerName IP_Remoto -Credential (Get-Credential) -ScriptBlock { Get-Process }
     ```

---

### **6. (Opzionale) Configurare HTTPS per maggiore sicurezza**
Per una comunicazione sicura:
1. Configura un certificato SSL.
2. Registra un listener HTTPS per WinRM:
   ```powershell
   winrm quickconfig -Transport:https
   ```

---

### **7. Test finale**
- Esegui un comando di test dal computer master:
  ```powershell
  Test-WSMan -ComputerName IP_Remoto
  ```
- Inizia a gestire i computer remoti:
  ```powershell
  Enter-PSSession -ComputerName IP_Remoto
  ```

