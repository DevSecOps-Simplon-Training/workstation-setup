# Fiche mémo – Les outils du poste DevOps Azure

> **Formation DevOps Azure | Simplon | 2025-2026**  
> Une fiche par outil : ce que c'est, à quoi ça sert, comment vérifier.

Cette fiche est pensée pour les profils en reconversion. Pour chaque outil, vous trouverez une explication simple, une analogie du quotidien pour ancrer le concept, et son utilité concrète dans le métier de DevOps.

---

## 🖥️ Système & Terminal

---

### WSL2 — Windows Subsystem for Linux

**C'est quoi ?**  
WSL2 (Windows Subsystem for Linux, version 2) permet de faire tourner un vrai système Linux (Ubuntu) directement dans Windows, sans avoir à installer une machine virtuelle séparée. En clair : vous restez sur votre ordinateur Windows, mais vous pouvez ouvrir un terminal Linux à tout moment.

> 💡 **Analogie :** C'est comme avoir un studio aménagé dans votre maison. Vous vivez dans la maison (Windows) mais vous pouvez entrer dans le studio (Linux) à tout moment, avec ses propres outils et son propre rangement — sans déménager.

**À quoi ça sert en DevOps ?**  
La plupart des serveurs, conteneurs et outils DevOps fonctionnent sous Linux. WSL2 permet de travailler avec ces outils depuis Windows, d'exécuter des scripts Bash, d'installer Ansible, etc. C'est l'environnement de base incontournable.

**Commande de vérification :**
```powershell
wsl --list --verbose
```

---

### Windows Terminal

**C'est quoi ?**  
Un terminal moderne développé par Microsoft qui regroupe en un seul endroit PowerShell, l'invite de commandes Windows et le terminal Linux (WSL2). On peut passer de l'un à l'autre via des onglets.

> 💡 **Analogie :** C'est comme un bureau avec plusieurs tiroirs ouverts simultanément. Plutôt que d'avoir trois fenêtres différentes éparpillées sur l'écran, tout est au même endroit et on passe de l'un à l'autre en un clic.

**À quoi ça sert en DevOps ?**  
On passe sa journée dans le terminal en DevOps. Windows Terminal remplace tous les anciens terminaux et permet de travailler proprement avec plusieurs environnements en parallèle.

**Vérification :** Lancer Windows Terminal depuis le menu Démarrer.

---

### PowerShell 7

**C'est quoi ?**  
PowerShell 7 est la version moderne et multiplateforme de PowerShell (Windows/Linux/Mac). C'est à la fois un terminal et un langage de script puissant.

> 💡 **Analogie :** C'est comme une télécommande universelle programmable. Plutôt que d'aller appuyer sur chaque bouton de chaque appareil à la main, vous écrivez une séquence une fois, et la télécommande exécute tout automatiquement.

**À quoi ça sert en DevOps ?**  
C'est le langage de script natif pour automatiser les tâches Windows et Azure. On l'utilise pour installer des modules Azure, lancer des scripts d'administration, automatiser des déploiements.

**Commande de vérification :**
```powershell
pwsh --version
```

---

## 🛠️ Outils de développement

---

### Visual Studio Code (VS Code)

**C'est quoi ?**  
VS Code est un éditeur de code gratuit et open source développé par Microsoft. C'est l'un des éditeurs les plus utilisés au monde, toutes spécialités confondues.

> 💡 **Analogie :** C'est comme un atelier de menuiserie bien équipé. Vous pouvez y travailler avec les outils de base, mais surtout y installer exactement les outils dont vous avez besoin selon votre projet : scie (Docker), niveau (Git), perceuse (Azure)… tout rangé au même endroit.

**À quoi ça sert en DevOps ?**  
On s'en sert pour écrire du code, des scripts, des fichiers de configuration (YAML, JSON, Terraform, Bicep…). Grâce à ses extensions, il devient un véritable environnement de travail intégré : on peut gérer Git, Docker, Azure et Kubernetes directement depuis l'éditeur.

**Extensions installées :**

| Extension | Rôle |
|---|---|
| Azure Tools | Gérer les ressources Azure depuis VS Code |
| Docker | Gérer les conteneurs et images Docker |
| Kubernetes | Explorer et gérer des clusters Kubernetes |
| Terraform | Coloration et autocomplétion des fichiers `.tf` |
| Bicep | Coloration et validation des fichiers `.bicep` |
| GitLens | Visualiser l'historique Git directement dans le code |
| YAML | Validation et coloration des fichiers YAML (pipelines CI/CD) |
| Pylance + Python | Support complet du langage Python |
| Remote – WSL | Ouvrir et éditer des fichiers Linux depuis VS Code |
| Remote – SSH | Se connecter à un serveur distant via SSH |

**Commande de vérification :**
```powershell
code --version
```

---

### Git

**C'est quoi ?**  
Git est le système de gestion de versions le plus utilisé au monde. Il permet de sauvegarder l'historique de son code, de travailler en équipe sur les mêmes fichiers et de revenir en arrière en cas d'erreur.

> 💡 **Analogie :** C'est comme un Google Docs avec un historique illimité et une machine à remonter le temps. Chaque modification est enregistrée avec qui l'a faite, quand, et pourquoi. Si quelqu'un casse quelque chose, on revient en arrière en une commande. Et toute l'équipe travaille sur le même document sans s'écraser mutuellement.

**À quoi ça sert en DevOps ?**  
En DevOps, tout est versionné : le code applicatif, les scripts, les fichiers d'infrastructure (Terraform, Bicep, Ansible). Git est la base de tout pipeline CI/CD — sans lui, rien ne se déclenche.

**Commande de vérification :**
```bash
git --version
git config --list   # Vérifier que user.name et user.email sont configurés
```

---

### Node.js & npm

**C'est quoi ?**  
Node.js est un environnement d'exécution JavaScript côté serveur. npm (Node Package Manager) est son gestionnaire de paquets, qui permet d'installer des bibliothèques et outils JavaScript.

> 💡 **Analogie :** Node.js c'est le moteur. npm c'est le concessionnaire de pièces détachées. Vous avez votre voiture (Node.js), et si vous avez besoin d'un nouveau composant (une librairie), vous allez chez le concessionnaire (npm) et vous l'installez en une commande.

**À quoi ça sert en DevOps ?**  
De nombreux outils DevOps et CLI sont écrits en JavaScript et nécessitent Node.js pour fonctionner. On l'utilise aussi pour construire et tester des applications web avant de les conteneuriser.

**Commande de vérification :**
```powershell
node --version
npm --version
```

---

### Python & pip

**C'est quoi ?**  
Python est un langage de programmation très lisible et polyvalent. pip est son gestionnaire de paquets (équivalent de npm pour Python).

> 💡 **Analogie :** Python c'est le couteau suisse des langages. Pas toujours le meilleur outil pour une tâche précise, mais il peut tout faire : écrire un script rapide, analyser des données, automatiser une tâche répétitive, communiquer avec une API… pip c'est la boutique pour lui ajouter des lames supplémentaires.

**À quoi ça sert en DevOps ?**  
Python est omniprésent en DevOps : scripts d'automatisation, outils de monitoring, SDK Azure, Ansible (qui est écrit en Python). C'est le langage de script incontournable sur Linux.

**Commande de vérification :**
```powershell
python --version
pip --version
```

---

### DBeaver Community

**C'est quoi ?**  
DBeaver est un outil graphique gratuit et universel pour se connecter à des bases de données. Une base de données, c'est l'endroit où une application stocke ses données de façon structurée (utilisateurs, commandes, produits, logs…). DBeaver permet de les consulter, les modifier et les interroger visuellement, sans connaître les commandes spécifiques de chaque système.

> 💡 **Analogie :** C'est comme un traducteur universel pour les bases de données. Chaque base (MySQL, PostgreSQL, SQL Server, Azure SQL…) a son propre « dialecte ». DBeaver parle tous ces dialectes et vous offre toujours la même interface, quelle que soit la base que vous ouvrez. C'est comme avoir le même cockpit pour piloter n'importe quel avion.

**À quoi ça sert en DevOps ?**  
Un DevOps est souvent amené à inspecter des bases de données pour déboguer une application, vérifier qu'un déploiement a bien migré les données ou comprendre la structure d'un projet. DBeaver évite d'apprendre les commandes spécifiques de chaque base — une interface unique, tous les projets.

**Commande de vérification :**
```
Lancer DBeaver depuis le menu Démarrer
→ Le panneau "Database Navigator" doit s'afficher à gauche
```

---

## ☁️ Outils Microsoft Azure

---

### Azure CLI (`az`)

**C'est quoi ?**  
L'Azure CLI (Command Line Interface, soit « interface en ligne de commande ») est un outil qui permet de gérer toutes les ressources Microsoft Azure directement depuis un terminal, en tapant des commandes textuelles. Le raccourci pour l'appeler est simplement `az`.

> 💡 **Analogie :** C'est comme la télécommande du portail Azure. Tout ce que vous pouvez faire en cliquant sur le site web Azure (créer un serveur, configurer un réseau, voir les factures), vous pouvez le faire avec une commande texte — et donc l'automatiser et le répéter à l'identique.

**À quoi ça sert en DevOps ?**  
C'est l'outil principal pour interagir avec Azure en DevOps : créer des machines virtuelles, déployer des applications, gérer des réseaux, consulter des logs… Tout ce qu'on peut faire dans le portail Azure, on peut le scripter avec `az`.

**Commandes de base :**
```powershell
az --version        # Vérifier l'installation
az login            # Se connecter à son compte Azure
az account show     # Vérifier la connexion
```

---

### Azure PowerShell (module Az)

**C'est quoi ?**  
Le module Az est l'équivalent de l'Azure CLI mais pour PowerShell. Il fournit des commandes PowerShell (appelées *cmdlets*) pour gérer Azure.

> 💡 **Analogie :** C'est la même télécommande Azure, mais dans un format compatible avec les scripts PowerShell déjà existants dans votre entreprise. Même résultat, syntaxe différente — comme avoir le même livre traduit en deux langues.

**À quoi ça sert en DevOps ?**  
Utilisé principalement dans les environnements Windows ou quand les scripts d'automatisation sont déjà écrits en PowerShell. Les pipelines Azure DevOps l'utilisent fréquemment.

**Commandes de base :**
```powershell
Connect-AzAccount       # Se connecter à Azure
Get-AzSubscription      # Lister les abonnements disponibles
```

---

### Azure Storage Explorer

**C'est quoi ?**  
C'est une application graphique (interface visuelle) pour naviguer et gérer les stockages Azure : Blob Storage, Files, Tables, Queues.

> 💡 **Analogie :** C'est l'explorateur de fichiers Windows (comme l'Explorateur de fichiers classique), mais pour vos fichiers stockés dans le cloud Azure. Vous naviguez dans des dossiers, vous glissez-déposez des fichiers, vous supprimez — exactement comme sur votre ordinateur.

**À quoi ça sert en DevOps ?**  
Permet d'explorer facilement les fichiers stockés dans Azure (logs, sauvegardes, artefacts de build) sans avoir à écrire de commandes. Très pratique pour déboguer ou vérifier qu'un fichier a bien été uploadé.

**Vérification :** Lancer l'application depuis le menu Démarrer et se connecter avec son compte Azure.

---

## 🐳 Conteneurisation

---

### Docker Desktop

**C'est quoi ?**  
Docker est la technologie de conteneurisation la plus utilisée au monde. Un conteneur est un environnement isolé et portable qui contient une application et tout ce dont elle a besoin pour fonctionner.

> 💡 **Analogie :** C'est comme une boîte de déménagement standardisée. Avant Docker, livrer une application c'était comme déménager des meubles en espérant que l'appartement de destination aura les bons branchements électriques. Avec Docker, on met tout dans une boîte hermétique — l'application, ses dépendances, sa configuration — et elle fonctionne partout pareil, que ce soit sur votre ordinateur, celui d'un collègue ou un serveur en production.

**À quoi ça sert en DevOps ?**  
Docker résout le problème du « ça marche sur ma machine ». En DevOps, on conteneurise les applications pour qu'elles se déploient de façon identique en développement, en test et en production. C'est la base des pipelines CI/CD modernes.

**Commandes de base :**
```powershell
docker --version
docker run hello-world          # Tester que Docker fonctionne
docker ps                       # Lister les conteneurs en cours
docker images                   # Lister les images locales
```

---

### kubectl — Kubernetes CLI

**C'est quoi ?**  
`kubectl` (prononcé « kube-control » ou « kube-CTL ») est l'outil en ligne de commande pour interagir avec un cluster Kubernetes. Kubernetes (souvent abrégé **K8s** — le « 8 » remplace les 8 lettres entre le K et le s) est la plateforme d'orchestration de conteneurs la plus utilisée. Un *cluster* Kubernetes, c'est un ensemble de serveurs qui travaillent ensemble pour faire tourner vos applications.

> 💡 **Analogie :** Si Docker c'est la boîte de déménagement, Kubernetes c'est le chef de chantier qui décide combien de boîtes ouvrir, lesquelles remplacer si elles sont abîmées, et comment les répartir dans l'entrepôt. `kubectl` c'est le talkie-walkie pour lui donner des ordres.

**À quoi ça sert en DevOps ?**  
Quand une application tourne dans des conteneurs Docker, Kubernetes les orchestre : il gère le démarrage, l'arrêt, la mise à l'échelle et la répartition de charge. `kubectl` permet de piloter tout ça depuis le terminal.

**Commandes de base :**
```powershell
kubectl version --client        # Vérifier l'installation
kubectl get pods                # Lister les pods d'un cluster
kubectl get nodes               # Lister les nœuds du cluster
```

---

### Helm

**C'est quoi ?**  
Helm est le gestionnaire de paquets pour Kubernetes. Un "chart" Helm est un paquet qui contient tout ce qu'il faut pour déployer une application sur Kubernetes.

> 💡 **Analogie :** C'est l'IKEA de Kubernetes. Plutôt que de fabriquer votre meuble planche par planche (écrire des dizaines de fichiers YAML à la main), vous prenez un pack IKEA préconçu (un chart Helm), vous choisissez vos options (la couleur, la taille), et vous l'assemblez en une commande.

**À quoi ça sert en DevOps ?**  
Plutôt que d'écrire des dizaines de fichiers YAML Kubernetes à la main, Helm permet d'utiliser des templates réutilisables et paramétrables. On déploie une base de données ou un serveur web en une seule commande.

**Commandes de base :**
```powershell
helm version
helm repo add stable https://charts.helm.sh/stable    # Ajouter un dépôt
helm install mon-app stable/nginx                      # Déployer une app
```

---

## 🏗️ Infrastructure as Code (IaC)

---

### Terraform

**C'est quoi ?**  
Terraform est un outil d'**Infrastructure as Code** (IaC — « infrastructure en tant que code »). Le principe : au lieu de créer des serveurs et des réseaux à la main en cliquant dans un portail web, on les décrit dans des fichiers texte (du « code »), et Terraform les crée automatiquement. Développé par HashiCorp, il fonctionne avec tous les grands fournisseurs cloud : Azure, AWS, Google Cloud…

> 💡 **Analogie :** C'est comme le plan d'un architecte, mais magique. Vous dessinez le plan de votre maison (vous écrivez ce que vous voulez comme serveurs, réseaux, stockage), et la maison se construit toute seule. Si vous changez le plan, Terraform calcule exactement ce qu'il faut modifier et le fait. Vous ne retournez jamais sur le chantier à la main.

**À quoi ça sert en DevOps ?**  
Au lieu de créer des ressources Azure à la main via le portail, on écrit du code Terraform. L'infrastructure devient versionnée, reproductible et automatisable — exactement comme du code applicatif.

**Commandes de base :**
```powershell
terraform --version
terraform init      # Initialiser un projet Terraform
terraform plan      # Prévisualiser les changements
terraform apply     # Appliquer les changements (créer/modifier l'infra)
terraform destroy   # Supprimer l'infrastructure
```

---

### Ansible (via WSL2)

**C'est quoi ?**  
Ansible est un outil d'automatisation et de gestion de configuration. Il permet d'installer des logiciels, configurer des serveurs et déployer des applications sur des machines distantes, sans avoir à s'y connecter manuellement.

> 💡 **Analogie :** Imaginez que vous devez installer le même logiciel sur 50 ordinateurs. Sans Ansible, vous y allez un par un. Avec Ansible, c'est comme envoyer un message groupé à 50 assistants avec une liste de tâches précise — ils font tous la même chose en même temps, sans que vous ayez à bouger.

**À quoi ça sert en DevOps ?**  
Ansible s'utilise pour configurer des serveurs de façon automatisée et reproductible. On décrit dans un fichier YAML ("playbook") ce que la machine doit avoir installé, et Ansible s'en charge. Il est très utilisé pour les déploiements et la gestion de parcs de serveurs.

**Commandes de base (dans WSL/Ubuntu) :**
```bash
ansible --version
ansible-playbook mon_playbook.yml    # Exécuter un playbook
ansible all -m ping                  # Tester la connectivité aux machines
```

---

### Bicep

**C'est quoi ?**  
Bicep est le langage d'Infrastructure as Code natif de Microsoft Azure. C'est une alternative simplifiée aux ARM Templates (fichiers JSON complexes) pour déployer des ressources Azure.

> 💡 **Analogie :** Si Terraform est un architecte universel qui peut construire n'importe où dans le monde, Bicep est un architecte spécialisé dans les constructions Azure. Il connaît tous les détails de la plateforme sur le bout des doigts et s'exprime dans un langage plus simple que les plans techniques bruts (ARM Templates).

**À quoi ça sert en DevOps ?**  
Là où Terraform est multi-cloud, Bicep est spécialisé Azure. Il permet de déployer des ressources Azure de façon déclarative avec une syntaxe plus lisible que les ARM Templates classiques.

**Commandes de base :**
```powershell
az bicep version
az bicep build --file main.bicep        # Compiler un fichier Bicep
az deployment group create --template-file main.bicep   # Déployer
```

---

## 🔄 CI/CD & Gestion de code

---

### GitHub Desktop *(optionnel)*

**C'est quoi ?**  
GitHub Desktop est une interface graphique pour Git et GitHub. Il permet de gérer ses dépôts, commits et branches sans passer par la ligne de commande.

> 💡 **Analogie :** C'est la version "boîte automatique" de Git. La ligne de commande Git c'est la boîte manuelle — plus de contrôle, mais il faut apprendre. GitHub Desktop c'est la boîte automatique — on arrive au même résultat, avec une interface visuelle et des clics.

**À quoi ça sert en DevOps ?**  
Utile pour visualiser les changements et l'historique d'un projet. En pratique, un DevOps utilise surtout Git en ligne de commande, mais GitHub Desktop est un bon complément pour débuter.

**Vérification :** Lancer l'application et se connecter à son compte GitHub.

---

### Configuration SSH (GitHub / Azure DevOps)

**C'est quoi ?**  
SSH (Secure Shell — « shell sécurisé ») est un protocole de communication chiffré. Une clé SSH est une paire de fichiers générés sur votre ordinateur : une **clé privée** (que vous gardez secret) et une **clé publique** (que vous partagez avec les services distants). Ensemble, elles permettent de prouver votre identité sans jamais taper de mot de passe.

> 💡 **Analogie :** C'est comme un badge d'accès magnétique personnalisé. Plutôt que de montrer votre carte d'identité (taper votre mot de passe) à chaque porte que vous franchissez, vous avez un badge unique (votre clé privée) reconnu instantanément. Vous gardez le badge dans votre poche, et vous donnez une copie de la "serrure" (clé publique) à chaque service qui doit vous reconnaître.

**À quoi ça sert en DevOps ?**  
Indispensable pour pousser du code sur GitHub ou Azure DevOps sans saisir son mot de passe à chaque fois. C'est aussi la méthode utilisée pour se connecter à des serveurs Linux distants.

**Vérification :**
```bash
ssh -T git@github.com      # Tester la connexion SSH à GitHub
```

---

### Azure DevOps

**C'est quoi ?**  
Azure DevOps est la plateforme Microsoft pour gérer l'ensemble du cycle de vie d'un projet : dépôts Git, pipelines CI/CD, tableaux de suivi, tests automatisés et artefacts.

> 💡 **Analogie :** C'est le quartier général d'un projet. Imaginez un immeuble avec : une salle des archives (dépôt Git), une chaîne de montage automatisée (pipelines CI/CD), un tableau de bord de suivi (gestion de tâches) et un entrepôt de livraisons (artefacts). Tout au même endroit, pour toute l'équipe.

**À quoi ça sert en DevOps ?**  
C'est la plateforme centrale de la formation. On y hébergera le code, on y créera des pipelines qui automatisent les tests et déploiements, et on y gérera les tâches du projet.

**Accès :** https://dev.azure.com/

---

## 🔐 Sécurité

---

### Gestionnaire de mots de passe (ex : Bitwarden)

**C'est quoi ?**  
Un gestionnaire de mots de passe stocke et chiffre tous tes identifiants dans un coffre-fort sécurisé. Tu n'as plus qu'un seul mot de passe maître à retenir.

> 💡 **Analogie :** C'est le trousseau de clés universel. Plutôt que d'avoir 30 clés identiques (le même mot de passe partout — dangereux) ou 30 clés différentes que vous oubliez en permanence, vous avez un trousseau sécurisé avec une clé maître. Vous ouvrez le trousseau une fois, et il vous donne la bonne clé pour chaque porte.

**À quoi ça sert en DevOps ?**  
Un DevOps gère de nombreux accès : Azure, GitHub, Docker Hub, serveurs SSH, APIs… Réutiliser des mots de passe ou les noter dans un fichier texte est une faille de sécurité majeure. Le gestionnaire de mots de passe est une bonne pratique professionnelle indispensable.

---

### MFA — Authentification Multi-Facteurs

**C'est quoi ?**  
Le MFA (Multi-Factor Authentication) ajoute une deuxième vérification lors de la connexion à un compte : en plus du mot de passe, on valide via une application mobile (Microsoft Authenticator, Google Authenticator…).

> 💡 **Analogie :** C'est comme un coffre-fort avec deux verrous. Le premier verrou c'est votre mot de passe (quelque chose que vous connaissez). Le second verrou c'est votre téléphone (quelque chose que vous possédez). Même si quelqu'un vole votre mot de passe, il ne peut pas ouvrir le coffre sans avoir aussi votre téléphone en main.

**À quoi ça sert en DevOps ?**  
Les comptes Azure, GitHub et Azure DevOps donnent accès à des ressources critiques. Sans MFA, un mot de passe volé suffit pour tout compromettre. Le MFA est exigé dans la quasi-totalité des entreprises.

---

*Formation DevOps Azure | Simplon | 2025-2026*
