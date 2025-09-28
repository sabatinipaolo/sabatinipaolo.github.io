---
classes: wide
title: "Sessione remota di power shell"
categories:
  - blog
tags:
  - windows
  - powershell
  - controllo remoto

permalink: /blog/powershell-remota/
---

TLDR: comandi per inviare comandi remotamente in powershell.

Per eseguire un comando remoto con `Invoke-Command` come un utente amministratore, devi specificare le credenziali appropriate durante l'invocazione. Ecco come fare:

---

### **Prerequisiti**
configurare le stazioni come in [questo post ]({{ site.baseurl }}/blog/windows-remoto/)

 
---

### **Comando Base**
Usa il parametro `-Credential` con `Invoke-Command` per specificare le credenziali di un utente amministratore.

Esempio:
```powershell
$cred = Get-Credential
Invoke-Command -ComputerName "IP_Remoto" -Credential $cred -ScriptBlock { Get-Process }
```
- **`Get-Credential`** apre una finestra per inserire le credenziali (nome utente e password) dell'amministratore remoto.
- **`-ComputerName`** specifica l'host remoto.
- **`-ScriptBlock`** contiene i comandi da eseguire.

---

### **Passare le credenziali direttamente**
Se conosci già le credenziali, puoi passarle direttamente:
```powershell
$cred = New-Object System.Management.Automation.PSCredential ("AdminUsername", (ConvertTo-SecureString "AdminPassword" -AsPlainText -Force))
Invoke-Command -ComputerName "IP_Remoto" -Credential $cred -ScriptBlock { Get-Service }
```

---

### **Specificare un amministratore di dominio**
Se stai lavorando in un ambiente di dominio e l'utente amministratore appartiene al dominio:
```powershell
$cred = Get-Credential
Invoke-Command -ComputerName "IP_Remoto" -Credential $cred -ScriptBlock { Restart-Service Spooler }
```
Nel prompt delle credenziali, inserisci il nome utente nel formato:  
`DOMINIO\NomeUtente` o `NomeUtente@dominio.local`.

---

### **Eseguire il comando su più computer**
Puoi eseguire il comando su più computer contemporaneamente:
```powershell
$cred = Get-Credential
Invoke-Command -ComputerName "IP1", "IP2", "IP3" -Credential $cred -ScriptBlock { Get-Service }
```

---


### **Sessione remota**
- Esegui un comando di test dal computer master:
  ```powershell
  Test-WSMan -ComputerName IP_Remoto
  ```
- Inizia a gestire i computer remoti:
  ```powershell
  Enter-PSSession -ComputerName IP_Remoto
  ```

- Se conosci già le credenziali, puoi passarle direttamente:
```powershell
$cred = New-Object System.Management.Automation.PSCredential ("AdminUsername", (ConvertTo-SecureString "AdminPassword" -AsPlainText -Force))
Enter-PSSession -ComputerName "IP_Remoto" -Credential $cred 
```


---


### **Verificare i permessi e testare la connessione**
1. **Testa la connessione remota**:
   ```powershell
   Test-WSMan -ComputerName "IP_Remoto"
   ```
2. **Verifica se l'utente ha i permessi corretti**:
   ```powershell
   Invoke-Command -ComputerName "IP_Remoto" -Credential $cred -ScriptBlock { whoami }
   ```
   Dovresti vedere qualcosa come:  
   `IP_REMOTO\Administrator`.

---

Con questi passaggi, puoi eseguire `Invoke-Command` come amministratore remoto in modo sicuro e senza problemi.












Con queste configurazioni, avrai PowerShell remoting funzionante in una rete LAN non in dominio.