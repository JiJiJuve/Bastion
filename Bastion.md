# Mise en place d’un bastion d’administration avec Teleport

## Contexte et objectifs du projet

L’entreprise a été sollicitée pour concevoir une infrastructure réseau **robuste**, **performante** et **hautement disponible**, capable de supporter des applications critiques et temps réel.

L’objectif est d’assurer une **continuité de service** tout en garantissant la **sécurité des accès administratifs** aux serveurs internes.

---

## Qu'est-ce qu'un bastion informatique ?

Un **bastion** est un serveur spécialement sécurisé, placé entre un réseau interne protégé et un réseau non sécurisé, comme Internet.  
Il agit comme une **barrière de protection** en filtrant le trafic et en empêchant les intrusions malveillantes.

Il permet également de **contrôler et surveiller les accès** au réseau interne, en vérifiant l’identité et les autorisations des utilisateurs afin de **renforcer la sécurité globale**.

---

## Étude comparative : Teleport vs Apache Guacamole

| **Critères**       | **Teleport (solution retenue)**                          | **Apache Guacamole**                    |
|--------------------|----------------------------------------------------------|-----------------------------------------|
| **Sécurité**       | Zero Trust, MFA, certificats éphémères                   | Authentification classique, mot de passe |
| **Audit**          | Journaux + enregistrements vidéo                         | Logs texte simples                      |
| **Accès**          | SSH, RDP, Web, DB, K8s                                   | RDP, SSH, VNC                           |
| **Administration** | RBAC granulaire + accès temporaire                       | ACL basique                             |
| **Déploiement**    | Modulaire (Auth, Proxy, Node)                            | Stack Java + Tomcat + SQL              |
| **Objectif**       | Bastion d’administration complet                         | Passerelle d’accès Web                 |

---

## Architecture technique

| **Composant**       | **Rôle**                                    | **Configuration**                                                            |
|---------------------|---------------------------------------------|------------------------------------------------------------------------------|
| **VM Bastion (Teleport)** | Serveur proxy d’accès et d’authentification | Debian, Teleport 18.2.4, IP `192.168.1.172`, `teleport.jiji.local`           |
| **VM Client**       | Poste d’administration simulant un utilisateur externe | Ubuntu 24.04.2, IP `192.168.1.165`                                           |

---

## Justification du choix de Teleport

Teleport offre :

- Une **sécurité avancée** basée sur le modèle **Zero Trust** (certificats temporaires, MFA).
- Une **traçabilité complète** des sessions utilisateurs (audit, relecture vidéo).
- Une **architecture modulaire évolutive**, adaptée à des environnements critiques.
- Une expérience mixte **CLI/Web professionnelle et intuitive**.

✅ Ce choix s’aligne avec les **exigences du client** : sécurité, résilience et continuité de service.  

**Page d’accueil Teleport accessible via navigateur depuis la VM client.**


<img width="1350" height="816" alt="acces_interface_web_Teleport_depuis_Client" src="https://github.com/user-attachments/assets/7485bbc4-05ca-4ae8-acc6-27ed8de5a677" />

<img width="1332" height="799" alt="Interface_Web_client" src="https://github.com/user-attachments/assets/9bac956b-31b3-4436-be0a-b42bb7328268" />



**Terminal client montrant la commande tsh login et la connexion réussie au bastion Teleport.** 


<img width="969" height="604" alt="connexion_tsh_terminal" src="https://github.com/user-attachments/assets/07e3be4e-d3b1-4485-822f-026c05b6a2b4" />


**Enregistrement (ou ajout) d'une ressource dans mon bastion Teleport**



<img width="966" height="599" alt="ajout_ressources1" src="https://github.com/user-attachments/assets/16998740-1b47-4243-8c0d-49012bff34ff" />


<img width="1599" height="938" alt="ajout_ressources2" src="https://github.com/user-attachments/assets/ca2bdd60-2853-4ebe-8b42-56691b1bb347" />

**Connexion  session SSH sur la ressource via le bastion depuis ma VM client, en mode zéro-trust, sans clé SSH manuelle**

<img width="964" height="575" alt="connexion_ssh_ressource_depuis_bastion" src="https://github.com/user-attachments/assets/2683e685-4516-464e-8006-1702878683a6" />



