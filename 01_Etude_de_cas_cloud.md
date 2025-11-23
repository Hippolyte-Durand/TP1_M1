---
sticker: lucide//download-cloud
---
# Étude de Cas : Quel Type de Cloud pour Quels Besoins ?

Voici l'analyse complète des différents cas présentés dans l'exercice.

---

### **Cas n°1: Eldo**

*   **Entreprise:** Start-up (60 employés) développant un logiciel de mise en relation et un CRM pour le BTP.
*   **Question:** Quelle solution pour héberger les logiciels Eldo ?

#### **Solution préconisée : PaaS sur Cloud Public**

*   **Type de Cloud:** **Cloud Public** (ex: AWS, Azure, Google Cloud). Un cloud privé serait financièrement et techniquement démesuré pour une start-up. Le cloud public offre un modèle de coût flexible (OPEX) sans investissement initial (CAPEX).
*
*   **Modèle de service:** **PaaS (Platform as a Service)**. Ce modèle permet à l'équipe de se concentrer sur le développement de son application et de son CRM sans gérer la complexité de l'infrastructure sous-jacente (serveurs, OS, réseau).

*   **Coût:** L'estimation de départ se situe entre **150€ et 300€ par mois**, avec une augmentation progressive en fonction de la croissance du nombre d'utilisateurs.

---

### **Cas n°2: MySecureProtect**

*   **Entreprise:** Société (150 employés) qui gère plus d'un million d'objets connectés pour la sécurité des habitations.
*   **Spécificité:** Trafic intermittent avec des pics prévisibles (matin/soir) et des pics rares (alertes).
*   **Question:** Quelle solution optimale et pourquoi ?

#### **Solution préconisée : PaaS/IaaS sur Cloud Public avec des services IoT**

*   **Type de Cloud:** **Cloud Public**. Gérer plus d'un million d'appareils nécessite une infrastructure massive, hautement disponible et sécurisée que seul un grand fournisseur de cloud public peut offrir de manière rentable. Bien qu'un cloud privé puisse être un argument marketing ("vos données de sécurité sont chez nous"), la sécurité des plateformes publiques est extrêmement robuste et certifiée, rendant cet argument moins pertinent.
* 
*   **Modèle de service:** Un mélange de **PaaS** et **IaaS**.
    *   **PaaS/Serverless pour les pics de trafic :** Les activations/désactivations sont des événements parfaits pour des fonctions "Serverless" (ex: **AWS Lambda**, **Azure Functions**). Elles ne tournent (et ne coûtent) que lorsqu'elles sont appelées, ce qui est idéal pour un trafic intermittent.
    
    *   **Services IoT dédiés :** Une plateforme comme **Azure IoT Hub** ou **AWS IoT Core** est indispensable. Elle est conçue pour ingérer de manière sécurisée et fiable les données de millions d'appareils, gérer leur authentification et router les messages.
    
*   **Coût:** Environ 100 000€ si l'on considère le coût **annuel** à grande échelle. Pour plus d'un million d'appareils, les coûts incluent : la connexion et la messagerie des appareils (facturées par million de messages), le traitement des données, le stockage, et l'infrastructure de l'application mobile. 
---

### **Cas n°3: Paul**

*   **Besoin:** Un particulier de 37 ans avec des compétences informatiques limitées souhaite stocker 800 Go de photos, y accéder depuis plusieurs appareils et **reprendre le contrôle de ses données**.
*   **Question:** Que conseillez-vous à Paul ?

#### **Solution préconisée : NAS (Network Attached Storage)**

*   **Pourquoi un NAS ?** La motivation principale de Paul est de "reprendre le contrôle de ses données". Cela exclut les services SaaS comme Google Drive, Dropbox ou iCloud, où les données sont stockées chez un tiers. Un NAS est un boîtier de disques durs connecté à son réseau domestique.
*   **Avantages pour Paul :**
    1.  **Contrôle total:** Ses fichiers sont physiquement chez lui. Il est le seul propriétaire de l'infrastructure et des données.
    2.  **Accès unifié:** Les NAS modernes viennent avec des applications simples qui permettent de synchroniser et d'accéder aux fichiers depuis un ordinateur, un smartphone ou une tablette, de manière sécurisée, même depuis l'extérieur.
    3.  **Coût unique:** C'est principalement un achat matériel initial (le boîtier et les disques durs), sans abonnement mensuel environ quelques centaines d'euro au départ.
    4.  **Simplicité:** Des marques comme Synology ou QNAP proposent des interfaces très conviviales, accessibles même pour des utilisateurs avec des compétences limitées.

---

### **Cas n°4: Fournisseur confidentiel des armées**

*   **Entreprise:** Grande entreprise (5000 employés), fournisseur de l'armée, avec des besoins en infrastructure qui évoluent rapidement.
*   **Contrainte:** Nom confidentiel, accréditation par le ministère des armées.
*   **Question:** Quelle solution pour moderniser l'infrastructure ?

#### **Solution préconisée : Cloud Privé (potentiellement certifié)**

*   **Type de Cloud:** **Cloud Privé**. Le niveau de confidentialité et de sécurité exigé par un client comme l'armée rend l'utilisation d'un cloud public (même souverain) très compliquée, voire impossible. Un cloud privé, hébergé dans les propres datacenters de l'entreprise ou chez un hébergeur de confiance dédié est une bonne option.

*   **Souveraineté et Sécurité:** La localisation des données doit être sur le territoire national et gérée par du personnel habilité. 

*   **Agilité:** Un cloud privé bien conçu (avec des outils comme OpenStack, VMware, ou Azure Stack) peut offrir la même agilité (provisionnement rapide de serveurs, stockage, etc.) qu'un cloud public mais demande plus de compétence en interne.

---

### **Cas n°5: TheFoodStore**

*   **Entreprise:** Très petite entreprise (5 employés) souhaitant lancer un site e-commerce rapidement.
*   **Question:** Quelle est la solution la plus adaptée ?

#### **Solution préconisée : SaaS (Software as a Service)**

*   **Pourquoi le SaaS ?** L'objectif est la **rapidité** et la **simplicité** pour générer les premières ventes. Une solution SaaS est un produit clé en main.
*   **Exemples:** Des plateformes comme **Shopify**, **Wix e-commerce**, ou **Squarespace**.
*   **Avantages:**
    1.  **Aucune compétence technique requise:** Pas besoin de gérer un serveur, un déploiement ou du code.
    2.  **Mise en ligne immédiate:** Le site peut être configuré et mis en ligne en quelques heures.
    3.  **Tout est inclus:** L'hébergement, la sécurité (certificats SSL), les paiements, la maintenance sont gérés par le fournisseur.
*   **Coût:** Conforme aux notes, les abonnements pour ces plateformes varient typiquement de **10€ à 100€ par mois** selon les fonctionnalités choisies.

---

### **Cas n°6: DeliverEats**

*   **Entreprise:** Plateforme de livraison de repas avec application mobile (clients, livreurs) et application tablette (restaurateurs).
*   **Question:** Quels types d'architecture envisager ?

#### **Solution préconisée : PaaS sur Cloud Public

*   **Type de Cloud:** **Cloud Public**. Pour une plateforme qui doit servir de nombreux utilisateurs (clients, livreurs, restaurateurs) de manière géographiquement distribuée et avec des pics d'utilisation (midi et soir), le cloud public est une bonne option pour la scalabilité.

*   **Modèle de service:** **PaaS**, plus spécifiquement une plateforme de conteneurisation managée. 

*   **Architecture (Microservices sur Kubernetes):**
    *   L'application peut être découpée en plusieurs services indépendants (microservices) : un pour les commandes, un pour l'authentification, un pour la géolocalisation des livreurs, etc.
    
    *   **Kubernetes (K8s)** est l'outil idéal pour orchestrer ces services.

---

### **Cas n°7: Onenveutpa**

*   **Entreprise:** Société avec de très nombreux télévendeurs travaillant partout dans le monde.
*   **Besoin:** Un nouveau système pour la gestion des informations des prospects.
*   **Question:** Quelle solution proposez-vous ?

#### **Solution préconisée : SaaS sur Cloud Public**

*   **Pourquoi le SaaS ?** L'entreprise a besoin d'une solution de **CRM (Customer Relationship Management)** accessible globalement, immédiatement, et sans maintenance / gestion du scaling et de la disponibilité autour du monde.
*   **Avantages:**
    1.  **Accessibilité mondiale:** Les solutions SaaS sont conçues pour être accessibles depuis n'importe où avec une simple connexion internet.
    2.  **Clé en main:** Pas de développement nécessaire. L'entreprise s'abonne et peut commencer à utiliser le service le jour même.
    3.  **Collaboration:** Ces outils sont nativement collaboratifs, permettant à des équipes distribuées de travailler sur les mêmes données de manière cohérente.
*   **Exemples:** Des leaders du marché comme **Salesforce**, **HubSpot**, ou **Zoho CRM**. Ce sont des plateformes robustes, sécurisées et éprouvées pour la gestion de la relation client à grande échelle.

