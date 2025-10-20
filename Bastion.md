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
🌐 **Page d’accueil Teleport accessible via navigateur** depuis la VM client.

---

## Captures et exemples de fonctionnement

### 🔐 Connexion au bastion via CLI

Terminal client montrant la commande :

```bash
tsh login --proxy=teleport.jiji.local --user=admin
