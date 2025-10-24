# Initiation à la classification des vulnérabilités

---

#### **En tant que spécialiste IT, vous êtes chargé de comprendre et évaluer différents types de vulnérabilité.**

<BVR><BVR>

#### **Évaluer les vulnérabilités ci-dessous:**

- [Eternal Blue](#eternal-blue)
- [Krack](#krack)
- [log4shell](#log4shell)
- [Looney-tunables](#looney-tunables)
- [Une vulnérabilité récente de votre choix issue du site du CERT-Fr](#une-vulnérabilité-récente-de-votre-choix-issue-du-site-du-cert-fr)


 #### **Pour chacune des vulnérabilités :**

- Donnez la référence CVE

- Décrire la vulnérabilité en une phrase

- Citez des éléments d'infrastructure pouvant être concernés

- Trouvez, mettez à jour ou calculez le score base CVSS (dernière version)

- Déterminer si un exploit est disponible publiquement, si oui en prendre connaissance et le citer en référence.

- Trouver si un score EPSS existe pour cette vulnérabilité


## **Eternal Blue**

<img width="658" height="299" alt="eternal_blue" src="https://github.com/user-attachments/assets/d5d8673a-d205-45b7-a375-c46593e010e1" />

##### EternalBlue est un exploit informatique développé par la National Security Agency (NSA), qui a été révélé par le groupe de hackers The Shadow Brokers le 14 avril 2017. Cet exploit utilise une faille de sécurité dans le protocole SMBv1, qui a été exploitée pour mener des cyberattaques à grande échelle, notamment lors de l'épidémie de ransomware WannaCry en 2017. Bien que Microsoft ait publié un correctif en mars 2017, de nombreux utilisateurs de Windows n'ont pas installé ce patch, ce qui a permis à EternalBlue de continuer à causer des problèmes de sécurité. Cette vulnérabilité a été utilisée pour infecter des systèmes d'exploitation Windows, y compris des versions obsolètes comme Windows XP et Windows 8, et a eu un impact international significatif. 

- CVE : CVE‑2017‑0144 --> est une faille SMBv1 de Windows permettant à un pirate d’exécuter du code à distance et ne nécessitant pas d'authentification.

- CVSS :
 
  <img width="452" height="100" alt="cvss_Eblue_V2" src="https://github.com/user-attachments/assets/3bc163ad-9a13-45ad-81bb-1791bb498f9d" />

  <img width="418" height="151" alt="cvss_Eblue_V3" src="https://github.com/user-attachments/assets/9eff110e-9ff8-4811-9680-86bbd26166a9" />

- Exploit :

  <img width="1463" height="114" alt="exploit_Eblue" src="https://github.com/user-attachments/assets/87935e71-a891-4291-af9e-d0d135c69be4" />


---

## **Krack**

<img width="729" height="435" alt="krack_vuln" src="https://github.com/user-attachments/assets/fecb3617-a3ff-43db-9cc2-a2eb893f9623" />

#### La vulnérabilité KRACK (Key Reinstallation Attack) exploite une faille dans le protocole WPA2, qui sécurise la plupart des connexions Wi-Fi. Cette attaque permet aux pirates de voler des données transmises sur les réseaux sans fil en réinstallant des clés de session. Elle affecte presque tous les appareils utilisant WPA2, rendant la sécurité des connexions Wi-Fi compromise.

- CVE : CVE-2017-13077 à 13088  --> est une attaque qui exploite une faille dans le protocole Wi-Fi WPA2 en réinstallant des clés de chiffrement déjà utilisées, permettant à un attaquant situé à proximité d’intercepter et de manipuler les données transmises sur le réseau sans fil.

- CVSS :

  <img width="382" height="335" alt="cve_cvss_Krack" src="https://github.com/user-attachments/assets/1dfd7d42-4a73-4eaa-949f-8268afdb0db2" />

Exploit : 

https://www.krackattacks.com/

---

## **log4shell**
#### La vulnérabilité Log4Shell, également connue sous le nom de CVE-2021-44228, est une vulnérabilité critique dans la bibliothèque Java Log4j. Elle a été révélée en novembre 2021 et a été exploitée par des cybercriminels pour exécuter du code arbitraire sur des systèmes, ce qui a conduit à des millions d'attaques. Log4Shell a été attribué une note CVSS de 10, ce qui indique une vulnérabilité extrêmement grave. Bien que des correctifs aient été publiés, certaines versions de Log4j continuent d'être utilisées, ce qui signifie que de nouveaux systèmes peuvent être compromis. Les entreprises sont donc encouragées à mettre à jour leurs systèmes pour éviter d'autres attaques potentielles. 


  - CVE-2021-44228 --> est une faille critique dans la bibliothèque de journalisation Apache Log4j qui permet à un attaquant distant d’exécuter du code arbitraire sur un système vulnérable, menant potentiellement à un contrôle total de ce système.
  
  - CVSS :

<img width="482" height="121" alt="cvss_log4shell" src="https://github.com/user-attachments/assets/8b2dba00-0aa4-4a0d-8ab3-df6a0c931509" />

  - CVE-2021-45046 : Permet l’exécution de code arbitraire dans des configurations spécifiques malgré le premier correctif, rendant certains systèmes vulnérables même après patch initial.

  - CVSS :

    <img width="459" height="151" alt="cvss2_log4shell" src="https://github.com/user-attachments/assets/e4bc5bde-fcef-4c91-98ef-526652e3b7eb" />

  - CVE-2021-45105 : Provoque un déni de service (DoS) via des chaînes de journalisation malveillantes sur des versions corrigées de Log4j.

  - CVSS :
    
  <img width="464" height="100" alt="cvss3_log4shell" src="https://github.com/user-attachments/assets/3ace4031-6e7a-4976-9ab8-d599f28be932" />


https://www.trendmicro.com/fr_fr/what-is/apache-log4j-vulnerability.html

---

## **Looney-tunables**
#### La vulnérabilité Looney Tunables, également connue sous le nom de CVE-2023-4911. Elle est liée à la bibliothèque glibc, un composant essentiel du noyau Linux. Cette vulnérabilité, qui a été introduite dans la bibliothèque glibc en avril 2021, permet à un attaquant d'escalader les privilèges et de devenir root sur la machine. 

 - CVE-2023-4911 --> est une faille d’escalade de privilèges locale dans la bibliothèque GNU C Library (glibc), permettant à un attaquant local d’obtenir des privilèges élevés sur le système.

- CVSS :

  <img width="504" height="155" alt="cvss_" src="https://github.com/user-attachments/assets/b9faf847-a589-4a29-ae9d-20588a0d89fb" />

---

## **Une vulnérabilité récente de votre choix issue du site du CERT-Fr**

---
