# Initiation au scripting
---


Votre script doit fonctionner sur votre machine, mais également sur n'importe quelle autre machine Windows afin de pouvoir être réutilisé à plus grande échelle.

- Vérifiez à l'aide d'un langage de script si vous avez les KB5049622, KB5049625 et Un KB présent de votre choix présent sur votre OS Windows. Le script devra afficher en Vert les KB présents et en rouge les KB absents.

- Une fois que votre script fonctionne, placer la liste des KB dans un fichier texte nommé kb_list.txt, le script devra lire ce fichier pour obtenir la liste des KB.

- Proposer une procédure, à écrire en commentaire du script, pour appliquer ce script sur un parc Windows AD.

- Signer votre script afin d'en prouver l'integrité et l'authenticité. (Certificat autosigné toleré)

Langages recommandés : Powershell.

---

#### **Snapshot des correctifs Windows installés avec Get-HotFix -->**
```powershell
Get-Hotfix

```

<img width="735" height="258" alt="KB_JiJi" src="https://github.com/user-attachments/assets/cd9877a0-5926-4dc5-a957-66a927f2f202" />

---

#### **Script PowerShell + Création du fichier "kb_list.txt" -->**
```powershell

$KBtest = @("KB5049622", "KB5049625", "KB5067360")
$kb_list = @()  # tableau vide pour stocker les lignes

foreach ($i in $KBtest) {
    $result = Get-HotFix -Id $i -ErrorAction SilentlyContinue
    if ($result) {
        Write-Host "$i" -ForegroundColor Green
        $kb_list += "$i"
    }
    else {
        Write-Host "$i" -ForegroundColor Red
        $kb_list += "$i"
    }
}

Set-Content -Path "kb_list.txt" -Value $kb_list

```

<img width="1018" height="976" alt="script" src="https://github.com/user-attachments/assets/4bd55c8a-fac9-4403-99ba-ce6f0dd08465" />

<bvr><bvr>

<img width="281" height="166" alt="creation_fichier_txt" src="https://github.com/user-attachments/assets/9b7d262f-4d74-4ff8-b7f4-beebf70ae860" />

---

#### **Exécution du script sur PowerShell -->**

<img width="779" height="510" alt="execution_script_powershell" src="https://github.com/user-attachments/assets/7c29aae3-b280-4fbb-83a1-8f41290fac73" />

---

#### **Signature du script -->**
```powershell

$SelfSignedCert = New-SelfSignedCertificate -Subject "ScriptPowerShell" -Type CodeSigningCert -CertStoreLocation Cert:\LocalMachine\My -FriendlyName "Signer scripts PowerShell" -NotAfter (Get-Date).AddYears(5)

```

```powershell

Export-Certificate -Cert $SelfSignedCert -FilePath "C:\Users\JiJi\Desktop\certificat.cer"

```

```powershell

Import-Certificate -FilePath "C:\Users\JiJi\Desktop\certificat.cer" -CertStoreLocation Cert:\LocalMachine\Root

```

<img width="1920" height="1032" alt="signature_certificat1" src="https://github.com/user-attachments/assets/a2bc9c14-db41-407f-a1e4-9c23d1785c50" />

---

<bvr><bvr>

```powershell

Import-Certificate -FilePath "C:\Users\JiJi\Desktop\certificat.cer" -CertStoreLocation Cert:\LocalMachine\TrustedPublisher

```

```powershell

Set-AuthenticodeSignature -FilePath "C:\Users\JiJi\Desktop\Simplon\Projet_Warmup\Projet_WARMUP_DeadlyBruisers\test.ps1" -Certificate $SelfSignedCert

```

```powershell

Get-AuthenticodeSignature -FilePath "C:\Users\JiJi\Desktop\Simplon\Projet_Warmup\Projet_WARMUP_DeadlyBruisers\test.ps1"

```

<img width="1485" height="417" alt="signature_certificat2" src="https://github.com/user-attachments/assets/196050b0-9f61-4f7d-816d-45309360ff62" />

---

<img width="1020" height="865" alt="signature _script" src="https://github.com/user-attachments/assets/6e44e6e8-6f65-4f53-b432-8af5a64f43e1" />

---

#### **Certificat -->**


<img width="403" height="514" alt="Certificat_image" src="https://github.com/user-attachments/assets/3b6015f6-e9db-4c03-aa33-5f3b469eab6d" />
