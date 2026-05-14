# Formation DevOps Azure
## Guide d'installation du poste de travail Windows

> **Destiné aux apprenants DevOps Azure**  
> Version 1.0 | Année 2025-2026

---

## Table des matières

1. [Introduction](#1-introduction)
2. [Prérequis matériels et logiciels](#2-prérequis-matériels-et-logiciels)
3. [Configuration initiale de Windows](#3-configuration-initiale-de-windows)
4. [Outils de développement essentiels](#4-outils-de-développement-essentiels)
5. [Outils Microsoft Azure](#5-outils-microsoft-azure)
6. [Outils de conteneurisation](#6-outils-de-conteneurisation)
7. [Infrastructure as Code (IaC)](#7-infrastructure-as-code-iac)
8. [Outils CI/CD et gestion de code](#8-outils-cicd-et-gestion-de-code)
9. [Sécurité et bonnes pratiques](#9-sécurité-et-bonnes-pratiques)
10. [Vérification de l'installation](#10-vérification-de-linstallation)
11. [Ressources et liens utiles](#11-ressources-et-liens-utiles)

---

## 1. Introduction

Ce guide a pour objectif de vous accompagner pas à pas dans la mise en place d'un environnement de travail complet sous Windows, adapté aux besoins d'un apprenant en formation DevOps Azure.

À l'issue de cette installation, vous disposerez de tous les outils nécessaires pour :

- Gérer du code source avec Git et GitHub / Azure DevOps
- Travailler avec les services Microsoft Azure via CLI et PowerShell
- Conteneuriser des applications avec Docker et Kubernetes
- Automatiser des déploiements avec Terraform, Bicep et Ansible
- Mettre en place des pipelines CI/CD
- Explorer et gérer des bases de données avec DBeaver
- Appliquer les bonnes pratiques de sécurité DevSecOps

> **ℹ️ Note :** Ce guide est conçu pour Windows 10 (version 21H2 minimum) ou Windows 11. Certaines étapes peuvent légèrement différer selon la version et l'édition de Windows.

> **ℹ️ Pour les profils en reconversion :** Certaines étapes font appel au **terminal** (aussi appelé *invite de commandes* ou *ligne de commande*). C'est une fenêtre noire dans laquelle on tape des instructions textuelles pour piloter l'ordinateur. C'est un outil du quotidien en DevOps — ne pas s'inquiéter si c'est nouveau, tout est expliqué étape par étape.

---

## 2. Prérequis matériels et logiciels

### 2.1 Configuration matérielle recommandée

| Composant       | Spécification                                                          |
|-----------------|------------------------------------------------------------------------|
| Processeur      | Intel Core i5/i7 ou AMD Ryzen 5/7 (8e génération ou supérieur)        |
| RAM             | 16 Go minimum — 32 Go recommandés                                      |
| Stockage        | 256 Go SSD minimum — 512 Go recommandés                                |
| Réseau          | Connexion Internet stable (téléchargements volumineux)                 |
| Virtualisation  | Virtualisation matérielle activée dans le BIOS (VT-x / AMD-V)         |

### 2.2 Système d'exploitation

- Windows 10 version **21H2** (build 19044) ou supérieure
- Windows 11 version **22H2** ou supérieure
- Édition **Professionnel** ou **Entreprise** (requis pour Hyper-V et WSL2)

---

## 3. Configuration initiale de Windows

### 3.1 Mises à jour Windows

Avant toute installation, il est essentiel que le système soit à jour.

1. Ouvrir **Paramètres → Windows Update**
2. Cliquer sur **Rechercher les mises à jour**
3. Installer toutes les mises à jour disponibles et redémarrer si nécessaire
4. Répéter l'opération jusqu'à ce qu'aucune mise à jour ne soit disponible

### 3.2 Activation de la virtualisation (BIOS/UEFI)

La virtualisation matérielle est indispensable pour WSL2 et Docker Desktop.

1. Redémarrer l'ordinateur et accéder au BIOS/UEFI (touche **F2**, **F10**, **DEL** ou **Suppr** selon le fabricant)
2. Localiser l'option **Intel Virtualization Technology (VT-x)** ou **AMD-V / SVM Mode**
3. Activer l'option
4. Sauvegarder et quitter le BIOS

> **ℹ️ Vérification :** Ouvrir le Gestionnaire des tâches → onglet Performances → CPU. Le champ « Virtualisation » doit afficher *Activé*.

### 3.3 Activation de Windows Subsystem for Linux (WSL2)

WSL2 permet d'exécuter un environnement Linux natif sous Windows, essentiel pour de nombreux outils DevOps.

1. Ouvrir **PowerShell en tant qu'Administrateur**
2. Exécuter la commande suivante :
   ```powershell
   wsl --install
   ```
3. Redémarrer l'ordinateur lorsque demandé
4. Au redémarrage, Ubuntu s'installe automatiquement — créer un nom d'utilisateur et un mot de passe Linux
5. Vérifier l'installation :
   ```powershell
   wsl --list --verbose
   ```
   → Doit afficher Ubuntu en **version 2**

> **ℹ️ Note :** Si la commande ne fonctionne pas, activer manuellement depuis **Activer ou désactiver des fonctionnalités Windows** : *Plateforme de machine virtuelle* et *Sous-système Windows pour Linux*, puis redémarrer.

### 3.4 Installation de PowerShell 7

PowerShell 7 est la version moderne et multiplateforme, recommandée pour Azure.

1. Télécharger depuis : https://github.com/PowerShell/PowerShell/releases
2. Choisir le fichier `.msi` pour Windows (ex : `PowerShell-7.x.x-win-x64.msi`)
3. Lancer l'installeur — cocher **Ajouter PowerShell au PATH**
4. Vérifier :
   ```powershell
   pwsh --version
   ```

---

## 4. Outils de développement essentiels

### 4.1 Visual Studio Code

| Paramètre           | Valeur                                              |
|---------------------|-----------------------------------------------------|
| Téléchargement      | https://code.visualstudio.com/                      |
| Version recommandée | Stable (dernière version)                           |
| Options             | Cocher « Ajouter au PATH » et « Ouvrir avec Code »  |

**Extensions à installer** (Ctrl+Shift+X) :

- Azure Tools *(pack complet Microsoft)*
- Docker
- Kubernetes
- Terraform *(HashiCorp)*
- Bicep *(Microsoft)*
- GitLens
- YAML
- Pylance + Python
- Remote – WSL
- Remote – SSH
- GitHub Copilot *(optionnel)*

### 4.2 Git

| Paramètre             | Valeur                                             |
|-----------------------|----------------------------------------------------|
| Téléchargement        | https://git-scm.com/download/win                   |
| Éditeur par défaut    | Visual Studio Code                                 |
| Fins de ligne         | Checkout Windows-style, commit Unix-style          |

**Configuration initiale** (dans Git Bash ou PowerShell) :

```bash
git config --global user.name "Prénom Nom"
git config --global user.email "email@exemple.com"
git config --global core.editor "code --wait"
git config --global init.defaultBranch main
```

### 4.3 Windows Terminal

1. Ouvrir le **Microsoft Store**
2. Rechercher **Windows Terminal** et installer
3. Dans les paramètres, configurer **Ubuntu WSL** comme profil par défaut

### 4.4 Node.js

| Paramètre           | Valeur                                                    |
|---------------------|-----------------------------------------------------------|
| Téléchargement      | https://nodejs.org/ — choisir la version **LTS**         |

```powershell
node --version   # Vérification Node.js
npm --version    # Vérification npm
```

> **ℹ️ Note :** Pour gérer plusieurs versions de Node.js, utiliser **NVM for Windows** : https://github.com/coreybutler/nvm-windows

### 4.5 Python

| Paramètre           | Valeur                                             |
|---------------------|----------------------------------------------------|
| Téléchargement      | https://www.python.org/downloads/                  |
| Version recommandée | Python **3.11** ou **3.12**                        |

1. Cocher impérativement **Add Python to PATH** avant d'installer
2. Vérifier :
   ```powershell
   python --version
   pip --version
   ```

### 4.6 DBeaver Community

DBeaver est un outil graphique gratuit pour se connecter à des bases de données et les explorer visuellement, sans avoir à taper des commandes SQL dans un terminal.

| Paramètre      | Valeur                                             |
|----------------|----------------------------------------------------|
| Téléchargement | https://dbeaver.io/download/                       |
| Édition        | **Community Edition** (gratuite)                   |

1. Télécharger le fichier `.exe` Windows Installer
2. Lancer l'installeur et suivre les étapes (options par défaut suffisent)

> **ℹ️ Note :** DBeaver supporte plus de 80 types de bases de données différents (PostgreSQL, MySQL, SQLite, SQL Server, Azure SQL…). Un seul outil pour tous les projets.

---

## 5. Outils Microsoft Azure

### 5.1 Azure CLI

| Paramètre       | Valeur                                                                               |
|-----------------|--------------------------------------------------------------------------------------|
| MSI             | https://learn.microsoft.com/fr-fr/cli/azure/install-azure-cli-windows               |
| Via winget      | `winget install --exact --id Microsoft.AzureCLI`                                    |

```powershell
az --version          # Vérifier l'installation
az login              # Se connecter à Azure
az account show       # Vérifier la connexion
```

### 5.2 Azure PowerShell (module Az)

Ouvrir PowerShell 7 en tant qu'Administrateur :

```powershell
Install-Module -Name Az -Scope CurrentUser -Repository PSGallery -Force
Connect-AzAccount     # Se connecter
Get-AzSubscription    # Vérifier les abonnements
```

### 5.3 Azure Storage Explorer

| Paramètre      | Valeur                                                              |
|----------------|---------------------------------------------------------------------|
| Téléchargement | https://azure.microsoft.com/fr-fr/features/storage-explorer/       |

1. Télécharger et installer Azure Storage Explorer
2. Se connecter avec le compte Azure de la formation

### 5.4 Azure Data Studio *(optionnel)*

Outil de gestion de bases de données Azure SQL et SQL Server.

| Paramètre      | Valeur                                                                                        |
|----------------|-----------------------------------------------------------------------------------------------|
| Téléchargement | https://learn.microsoft.com/fr-fr/azure-data-studio/download-azure-data-studio               |

---

## 6. Outils de conteneurisation

### 6.1 Docker Desktop

| Paramètre      | Valeur                                                          |
|----------------|-----------------------------------------------------------------|
| Téléchargement | https://www.docker.com/products/docker-desktop/                 |
| Prérequis      | WSL2 activé, Virtualisation BIOS activée                        |

1. Télécharger Docker Desktop pour Windows
2. Lancer l'installeur (droits Administrateur requis)
3. Sélectionner **WSL2** comme backend *(recommandé)*
4. Redémarrer l'ordinateur
5. Lancer Docker Desktop et attendre le démarrage du démon
6. Vérifier :
   ```powershell
   docker --version
   docker run hello-world
   ```

> **ℹ️ Note :** Docker Desktop nécessite une licence pour un usage professionnel commercial (entreprise > 250 personnes). Dans le cadre de la formation, l'usage est gratuit.

### 6.2 kubectl (Kubernetes CLI)

```powershell
# Inclus avec Docker Desktop (activer Kubernetes dans les paramètres)
# Ou installer séparément :
winget install --id Kubernetes.kubectl

# Vérification
kubectl version --client
```

### 6.3 Helm

Helm est le gestionnaire de packages pour Kubernetes.

```powershell
winget install --id Helm.Helm   # Installation
helm version                    # Vérification
```

---

## 7. Infrastructure as Code (IaC)

### 7.1 Terraform

| Paramètre      | Valeur                                                          |
|----------------|-----------------------------------------------------------------|
| Téléchargement | https://developer.hashicorp.com/terraform/downloads             |
| Via winget     | `winget install --id Hashicorp.Terraform`                       |

```powershell
terraform --version   # Vérification
terraform init        # Initialiser un projet
```

> **ℹ️ Note :** L'extension VS Code **HashiCorp Terraform** apporte la coloration syntaxique, l'autocomplétion et la validation des fichiers `.tf`.

### 7.2 Ansible (via WSL2)

Ansible s'installe dans l'environnement Linux WSL2 (Ubuntu) :

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install ansible -y
ansible --version   # Vérification
```

### 7.3 Bicep (Azure Resource Manager)

Bicep est le langage d'Infrastructure as Code natif d'Azure, alternative simplifiée aux ARM Templates.

```powershell
az bicep install      # Installation via Azure CLI
az bicep version      # Vérification
```

> **ℹ️ Note :** Installer l'extension **Bicep** dans VS Code pour l'autocomplétion et la validation.

---

## 8. Outils CI/CD et gestion de code

### 8.1 GitHub Desktop *(optionnel)*

| Paramètre      | Valeur                       |
|----------------|------------------------------|
| Téléchargement | https://desktop.github.com/  |

1. Télécharger et installer GitHub Desktop
2. Se connecter avec le compte GitHub de la formation

### 8.2 Configuration SSH pour GitHub / Azure DevOps

```powershell
# 1. Générer une clé SSH
ssh-keygen -t ed25519 -C "email@exemple.com"

# 2. Démarrer l'agent SSH
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent

# 3. Ajouter la clé
ssh-add ~/.ssh/id_ed25519

# 4. Afficher la clé publique (à copier dans GitHub / Azure DevOps)
cat ~/.ssh/id_ed25519.pub

# 5. Tester la connexion
ssh -T git@github.com
```

### 8.3 Azure DevOps

1. Se rendre sur : https://dev.azure.com/
2. Créer ou rejoindre une organisation Azure DevOps
3. Créer un premier projet et un dépôt Git
4. Lier avec l'Azure CLI :
   ```powershell
   az devops configure --defaults organization=https://dev.azure.com/NomOrga
   ```

---

## 9. Sécurité et bonnes pratiques

### 9.1 Gestionnaire de mots de passe

Utiliser un gestionnaire de mots de passe pour stocker les credentials Azure en toute sécurité.

- **Bitwarden** *(gratuit, open source)* : https://bitwarden.com/
- **1Password** : https://1password.com/
- **KeePass** *(local)* : https://keepass.info/

### 9.2 Multi-Factor Authentication (MFA)

1. Activer le MFA sur le **compte Azure** de formation
2. Installer **Microsoft Authenticator** sur votre mobile
3. Activer également le MFA sur **GitHub** et **Azure DevOps**

### 9.3 Gestion des secrets

> ⚠️ Ne jamais stocker de secrets (clés API, mots de passe, tokens) en clair dans le code.

- Utiliser des variables d'environnement ou des fichiers `.env` non versionnés
- Ajouter `.env` au fichier `.gitignore`
- Utiliser **Azure Key Vault** pour les secrets de production
- Pour Terraform : utiliser des variables d'entrée ou le provider Azure Key Vault

### 9.4 Windows Defender

Windows Defender peut parfois bloquer certains outils DevOps. Si nécessaire :

- Ajouter des exclusions pour le dossier de développement (ex : `C:\Users\[user]\dev`)
- Ajouter des exclusions pour Docker Desktop et WSL
- ⚠️ Ne jamais désactiver complètement Windows Defender

---

## 10. Vérification de l'installation

Une fois toutes les installations terminées, vérifier chaque outil dans PowerShell ou Windows Terminal :

| Outil          | Commande de vérification          | Résultat attendu                           |
|----------------|------------------------------------|--------------------------------------------|
| Git            | `git --version`                   | git version 2.x.x                          |
| Node.js        | `node --version`                  | v20.x.x ou supérieur                       |
| Python         | `python --version`                | Python 3.11.x ou supérieur                 |
| DBeaver        | Lancer l'application              | Fenêtre principale visible                 |
| Azure CLI      | `az --version`                    | azure-cli 2.x.x                            |
| Terraform      | `terraform --version`             | Terraform v1.x.x                           |
| Docker         | `docker --version`                | Docker version 26.x.x                      |
| kubectl        | `kubectl version --client`        | Client Version: v1.x.x                     |
| Helm           | `helm version`                    | version.BuildInfo{Version:"v3.x.x"}        |
| PowerShell 7   | `pwsh --version`                  | PowerShell 7.x.x                           |
| WSL2           | `wsl --list --verbose`            | Ubuntu Running (WSL 2)                     |
| Ansible (WSL)  | `ansible --version`               | ansible [core 2.x.x]                       |
| Bicep          | `az bicep version`                | Bicep CLI version x.x.x                    |

---

## 11. Ressources et liens utiles

### 11.1 Documentation officielle

- **Microsoft Learn (Azure)** : https://learn.microsoft.com/fr-fr/azure/
- **Azure CLI** : https://learn.microsoft.com/fr-fr/cli/azure/
- **Docker** : https://docs.docker.com/
- **Terraform sur Azure** : https://developer.hashicorp.com/terraform/tutorials/azure-get-started
- **Kubernetes** : https://kubernetes.io/fr/docs/home/
- **Ansible** : https://docs.ansible.com/
- **Bicep** : https://learn.microsoft.com/fr-fr/azure/azure-resource-manager/bicep/

### 11.2 Comptes à créer

- **Compte Microsoft Azure** *(essai gratuit – 200 $ de crédit)* : https://azure.microsoft.com/fr-fr/free/
- **Compte GitHub** : https://github.com/
- **Compte Docker Hub** : https://hub.docker.com/
- **Azure DevOps** *(gratuit pour 5 utilisateurs)* : https://dev.azure.com/

### 11.3 Parcours de formation recommandés (Microsoft Learn)

- **AZ-900** : Fondamentaux Azure
- **AZ-104** : Administration Azure
- **AZ-400** : DevOps Engineer Expert
- **Parcours DevOps** : https://learn.microsoft.com/fr-fr/training/paths/devops-dojo-white-belt-foundation/

---

*Formation DevOps Azure | Simplon | 2025-2026*
