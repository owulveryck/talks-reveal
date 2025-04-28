# Script de présentation MCP : Les API du Futur pour l'IA

*Durée totale prévue : ~40 minutes (rythme soutenu)*

## Introduction (0:00 - 3:00)

### Slide 1 - Titre
*[0:00 - 1:30]*

**[Nouvelle Accroche]**
Bonjour à tous. On parle beaucoup de la puissance croissante des IA, des modèles de langage toujours plus performants. Mais **et si la *vraie* clé pour débloquer l'efficacité de l'IA ne résidait pas seulement dans l'intelligence du modèle... mais dans la qualité des outils logiciels auxquels elle a accès ?** Et si le principal frein actuel était que nos IA, si brillantes soient-elles, sont souvent cantonnées à une "boîte de dialogue" sans pouvoir *agir* efficacement sur nos systèmes ?

Aujourd'hui, nous allons explorer le **Model Context Protocol (MCP)**. Ce n'est pas juste un acronyme technique de plus. C'est le standard émergent qui transforme nos logiciels en outils *réellement* exploitables par l'IA, le pont qui permet aux agents IA de passer de la simple conversation à l'action concrète.

Au cœur de cette transformation, nous découvrirons les **"3U"** : comment concevoir des outils pour l'IA qui soient vraiment **U**tiles, facilement **U**tilisables, et surtout, effectivement **U**tilisés.

### Slide 2 - Structure
*[1:30 - 3:00]*

Notre exploration se fera en quatre temps :

1.  **Fondamentaux :** Pourquoi les agents IA ont besoin d'interagir avec leur environnement et les limites actuelles.
2.  **Le Protocole MCP :** Qu'est-ce que c'est, son architecture, et ses capacités uniques (Ressources, Actions, et les cruciaux **Prompts**).
3.  **Conception d'Outils IA :** Comment le MCP se compare aux API REST et surtout, comment créer des outils qui respectent les **3U** en pensant "Affordance pour l'IA".
4.  **Mise en Œuvre & Avenir :** Des cas d'usage concrets (comme améliorer la productivité dev), les défis et les prochaines étapes.

*[Note: S'assurer que l'image illustre bien l'IA interagissant avec DIVERS outils/environnements.]*

## Partie 1: Contexte et fondamentaux (3:00 - 9:00)

### Slide 3 - Section Fondamentaux
*[3:00 - 3:15]*

Commençons par poser les bases : pourquoi cette interaction Agent-Outil est-elle si fondamentale ?

### Slide 4 - Bases des Systèmes Agents
*[3:15 - 5:00]*

Qu'est-ce qu'un agent IA ? Une entité (artificielle ou humaine) qui perçoit son environnement et agit dessus.
L'environnement est **observable** (l'agent reçoit de l'info) et offre des **capacités** (l'agent peut agir).

**Point Clé :** Un agent qui ne peut *rien faire* dans son environnement est inutile. L'observation seule ne suffit pas. L'action est essentielle.

L'**autonomie** est sa capacité à agir sans intervention humaine constante. Plus elle est élevée, plus l'agent est puissant.
*(Distinction Agent vs Workflow peut être rapide ici, focus sur la liberté décisionnelle de l'agent)* `[Keep concise]`

*[Suggestion Visuel: Schéma simple: Agent <-> (Perception/Action) <-> Environnement]*

### Slide 5 - Limites des Environnements IA Actuels
*[5:00 - 7:00]*

Le problème ? Aujourd'hui, l'environnement principal de beaucoup d'IA, c'est la **fenêtre de chat**. C'est limité !
Pour être vraiment utiles, les IA doivent sortir de cette boîte et interagir avec la multitude d'outils que *nous*, humains, utilisons : applications métier, bases de données, API, services cloud...

**[Question Rhétorique possible]** Qui n'a jamais rêvé que son assistant IA puisse *directement* aller chercher l'info dans le CRM ou lancer une commande dans le système de build, au lieu de juste vous donner des instructions ?

Comment leur donner accès à ces outils de manière standardisée et efficace ?

### Slide 6 - Le Défi de Liaison Agent-Outil
*[7:00 - 9:00]* `[Rythme potentiellement rapide ici]`

Le défi : **Traduire** l'intention en langage naturel de l'IA ("Trouve les emails des clients importants à Paris") en appels structurés vers les bons outils (API du CRM, etc.).

Les SDK spécifiques créent un **couplage fort** : l'agent dépend de l'outil, l'outil de l'agent. C'est rigide.

L'idéal : des **outils découplés**, évoluant indépendamment, contrôlés par leurs propriétaires, formant un **écosystème ouvert**.
Pour cela, il faut un **standard**. C'est là qu'intervient le MCP.

## Partie 2: Introduction au MCP (9:00 - 16:30)

### Slide 7 - Section Introduction au MCP
*[9:00 - 9:15]*

Voyons maintenant ce standard : le Model Context Protocol.

### Slide 8 - Architecture MCP
*[9:15 - 10:45]*

*[Visuel Essentiel : Schéma très clair Hôte (LLM) <-> Client MCP <-> Serveur(s) MCP (Outils)]* `[Ensure diagram is ultra-clear, simple labels]`

Trois acteurs clés :
1.  **Hôte :** L'application qui exécute le LLM (ChatGPT, Claude, Copilot...).
2.  **Client MCP :** Intégré à l'hôte, parle le protocole MCP.
3.  **Serveur(s) MCP :** Exposent les outils (capacités) via le protocole.

Le MCP standardise la communication entre Client et Serveur, permettant à *n'importe quel* hôte compatible d'utiliser *n'importe quel* outil MCP. **Interopérabilité !**

### Slide 9 - Le Model Context Protocol
*[10:45 - 12:30]*

Apparu fin 2023 (initié par Anthropic), le MCP vise à **standardiser comment les logiciels exposent leurs capacités aux IA** (pas directement aux humains).
C'est le "chaînon manquant" pour passer d'**assistants** (qui suggèrent) à des **agents** (qui agissent).

*[Exemple JSON simplifié et lisible à l'écran]* `[Simplify JSON for readability]`
Exemple : Un outil `getWeather` qui prend `city: string` et retourne `forecast: string`. Cette description JSON permet à une IA de comprendre et utiliser l'outil sans code spécifique.

### Slide 10 - Section Cadre Technique
*[12:30 - 12:45]*

Quelles sont les capacités concrètes offertes par un serveur MCP ?

### Slide 11 - Capacités MCP
*[12:45 - 14:30]*

Trois types de capacités fondamentales :

1.  **Ressources :** Obtenir des données (GET REST). Ex: `getProductList`, `getUserProfile`.
2.  **Actions :** Exécuter des tâches (POST REST). Ex: `sendEmail`, `calculateDistance`, `createTicket`.
3.  **Prompts :** **LA nouveauté clé de MCP !** Des modèles de texte pour *guider le raisonnement* de l'IA. Ex: templates de description, règles de formatage, "recettes" pour utiliser l'outil.

C'est via ces capacités, et surtout les Prompts, qu'on travaille l'**Affordance pour l'IA** : comment l'outil "suggère" sa propre utilité et son mode d'emploi à une IA. **[Question Rhétorique possible]** Comment un simple bouton "sait" qu'il doit être cliqué ? Pour une IA, cette "invitation à l'action" passe par le texte et les prompts !

### Slide 12 - Les 3 U et Aspects Techniques
*[14:30 - 16:30]*

Rappel des **3 U** pour un outil MCP réussi :
-   **Useful (Utile) :** Résout un vrai problème pour l'IA.
-   **Usable (Utilisable) :** Techniquement accessible via MCP standard.
-   **Used (Utilisé) :** L'IA le choisit et l'utilise effectivement (grâce à une bonne affordance !).

Techniquement : basé sur **JSON-RPC** (léger).
Évolutions prévues : Server-Sent Events (notifications asynchrones), découverte d'outils. `[Keep concise]`

En bref : **MCP est aux IA ce que REST a été à la transformation digitale.**

## Partie 3: MCP vs API REST et Composants Clés (16:30 - 22:00)

### Slide 13 - Section MCP vs API REST
*[16:30 - 16:45]*

Comparons plus en détail avec les API REST.

### Slide 14 - MCP: Les "API REST" pour les IA
*[16:45 - 18:30]*

Le parallèle est fort :
-   REST : Pour applications utilisées par des **humains** (via des UI).
-   MCP : Pour outils utilisés par des **agents IA**.

Même rôle de catalyseur, mais pour un *utilisateur* différent.

Correspondances :
-   Actions MCP ≈ POST REST
-   Resources MCP ≈ GET REST
-   **Prompts MCP : Pas d'équivalent direct REST !**

**Pourquoi cette différence ?** Les humains ont l'intuition, l'inférence contextuelle face à une UI. L'IA a besoin d'un **guidage textuel explicite**, que les Prompts fournissent. `[Emphasize visual comparison if possible]`

### Slide 15 - L'Importance Cruciale des Prompts
*[18:30 - 20:30]* `[Crucial point - make it concrete]`

Ne sous-estimez JAMAIS les Prompts MCP ! C'est bien plus que de la doc :

1.  **Simplifient la collecte de contexte :** L'IA sait *quoi* demander (logs, code, etc.) pour comprendre un problème.
2.  **Rendent l'outil découvrable et compréhensible :** L'IA apprend *quand* et *comment* utiliser l'outil sans entraînement spécifique.
    *   **Exemple Simple :** Plutôt qu'une API `calculerPrix(produitID)`, un Prompt MCP pourrait guider : *"Si le contexte utilisateur indique 'Client VIP', utilise l'action `calculerPrixRemise` avec `produitID` et `taux=0.15`. Sinon, utilise l'action `calculerPrixStandard` avec `produitID`."*
3.  **Transforment potentiel abstrait en action guidée.**

Le Prompt est comme un **mode d'emploi intelligent et exécutable pour l'IA**, fourni par l'outil lui-même.

### Slide 16 - Section Adoption et Mise en œuvre
*[20:30 - 20:45]*

Où en est-on aujourd'hui ?

### Slide 17 - Importance et Écosystème Actuel
*[20:45 - 22:00]*

MCP s'impose comme un **standard de fait** (Anthropic, OpenAI, Google...).
Permet un **écosystème d'outils IA interopérables**, comme le web des API.
**Catalyseur** de la révolution des agents IA.

Premiers utilisateurs : Développeurs IT (Cursor, Claude Code, Copilot utilisent des concepts similaires).
Intérêt pour les entreprises :
-   Connecter l'IA aux systèmes internes (KB, CI/CD, BDD...).
-   Exposer des capacités métier spécifiques.

Écosystème externe en croissance (Salesforce, ServiceNow...).

## Partie 4: Mise en œuvre et défis (22:00 - 27:30)

### Slide 18 - Stratégie de Mise en Œuvre
*[22:00 - 24:30]*

Comment démarrer avec MCP ? 4 étapes :

1.  **Analyse :** Identifier les workflows pertinents. "Quelles tâches l'IA pourrait-elle faire si elle avait les bons outils ?"
2.  **Conception :** Intégrer MCP comme un **adaptateur** (port) dans votre architecture (coexiste bien avec REST). Penser "Affordance IA" dès le début.
3.  **Développement :** **Itératif !** Commencer simple, tester, mesurer l'usage réel (`Used`), améliorer.
4.  **Sensibilisation :** Former les équipes. C'est encore nouveau.

Bonne nouvelle : MCP s'appuie sur des bases solides d'ingénierie logicielle (les 3U !).

### Slide 19 - Section Évolution future
*[24:30 - 24:45]*

Qu'attendre pour la suite ?

### Slide 20 - Évolutions et Défis Clés
*[24:45 - 27:30]* `[Focus on key points]`

Évolutions attendues :
1.  Outils avec meilleure **affordance IA**.
2.  **Notifications asynchrones** (Server-Sent Events) : L'outil prévient l'IA (tâche finie, événement...). Essentiel pour des agents vraiment proactifs.
3.  Protocoles Agent-to-Agent (A2A) : Plus lointain.
4.  Écosystème d'outils riche.

Défis :
1.  **Sécurité / Accréditation :** MCP ne le spécifie pas. Doit être géré *au-dessus* (OAuth2, tokens...). `[Add note on security layer]` Comme pour REST !
2.  **Gouvernance / Standards internes :** Comment gérer la prolifération d'outils MCP ?
3.  **Architecture de déploiement.**
4.  **Apprendre à concevoir pour l'IA :** Le plus grand défi ! Passer de l'UI visuelle à l'affordance textuelle/conceptuelle via descriptions, noms clairs et **Prompts intelligents**. `[Reiterate affordance concept]`

## Partie 5: Cas d'usage spécifique (27:30 - 32:30)

### Slide 21 - Section Cas d'usage
*[27:30 - 27:45]*

Illustrons avec un cas concret : la productivité des développeurs.

### Slide 22 - Mémoire Partagée pour Équipes Dev via Knowledge Graph
*[27:45 - 31:00]* `[Highlight the inconsistency problem/solution clearly]`

Problème : Les assistants IA Dev (Copilot...) ont un contexte limité (session, code ouvert). Il manque le **contexte partagé de l'équipe** (bonnes pratiques, décisions d'archi...).

Solution MCP : Un serveur exposant une **"mémoire d'équipe"** (ex: Knowledge Graph) via MCP.

Bénéfices :
-   L'IA interroge ce service pour les standards de l'équipe.
-   L'équipe enrichit la KB via l'IA.
-   Cohérence accrue.

**Exemple concret avec un Knowledge Graph :**
Le KG stocke des triplets : `(sujet, prédicat, objet)`.
Ex: `(MCP, améliore, Agents IA)`.

Défi : L'IA peut être inconsistante !
Session 1 : `(MCP, evolutionAnalyzedWith, WardleyMap)`
Session 2 : `(WardleyMap, appliedTo, MCPEvolution)` -> Incohérent !

**Solution via Prompts MCP + Ontologie :**
Le Prompt MCP guide l'IA en utilisant une ontologie prédéfinie :
-   Classes : `Protocole`, `Théorie`, `Personne`...
-   Prédicats standardisés : `analyzedUsing`, `writtenBy`...
-   Le Prompt dit à l'IA : "Pour ajouter une relation d'analyse, utilise le prédicat `analyzedUsing` avec un sujet de type `Concept` et un objet de type `Théorie`."

Cela montre la puissance des Prompts pour assurer la **cohérence** et l'**utilisabilité** (`Usable` + `Used`) de l'outil par l'IA.

### Slide 23 - Section Conclusion
*[31:00 - 31:15]*

Résumons les points essentiels.

### Slide 24 - MCP: Catalyseur d'une Nouvelle Révolution
*[31:15 - 32:30]*

MCP est le catalyseur technique de la prochaine révolution numérique :
1.  Internet : Services accessibles de partout.
2.  Smartphone : Services nomades.
3.  **IA + MCP : Délégation de tâches cognitives et actions à des agents IA.**

MCP joue le rôle que **REST** a joué pour le web et le mobile. Il standardise l'interaction Agent-Outil.

## Takeaways et conclusion (32:30 - 40:00)

### Slide 25 - Takeaway 1: MCP = Les Nouvelles API pour l'IA
*[32:30 - 34:00]*

**Retenez ceci : MCP n'est pas juste un protocole. C'est l'équivalent des API REST, mais conçu spécifiquement pour les IA.**
Standard émergent adopté par les géants (Anthropic, OpenAI, Google...).
Deviendra probablement incontournable.
**Action : Intégrez MCP dans votre réflexion stratégique et architecturale dès maintenant.**

### Slide 26 - Takeaway 2: Pensez "Affordance pour l'IA"
*[34:00 - 35:30]* `[Reiterate affordance concept]`

L'affordance change de nature :
-   Humain : Visuelle, intuitive (bouton, poignée).
-   **IA : Textuelle, conceptuelle.** L'IA doit comprendre via le texte :
    -   *Quoi ?* (Fonction de l'outil)
    -   *Quand ?* (Contexte d'utilisation)
    -   *Comment ?* (Paramètres, contraintes)

C'est le rôle des **descriptions claires** et surtout des **Prompts MCP**. Ce sont des guides d'utilisation *actifs* pour l'IA.
**Action : Concevez vos outils MCP en vous demandant : "Comment une IA comprendra-t-elle cet outil et comment l'utiliser correctement ?"**

### Slide 27 - Takeaway 3: Respectez les 3 U
*[35:30 - 37:30]* `[Link 'Used' directly to affordance/prompts]`

Le cadre simple mais puissant pour évaluer vos outils MCP :
-   **Useful (Utile) :** Apporte une vraie valeur. Résout un besoin.
-   **Usable (Utilisable) :** Techniquement accessible (standard MCP, interface claire).
-   **Used (Utilisé) :** L'IA le choisit et l'emploie. **C'est là que l'affordance et les Prompts sont CRUCIAUX.** Un outil utile et utilisable mais mal décrit ou avec des prompts confus sera ignoré par l'IA.
**Action : Évaluez vos initiatives MCP selon ces 3 axes, en portant une attention particulière au 'Used' via l'affordance.**

### Slide 28 - Nouvel Enjeu Commercial
*[37:30 - 38:30]* `[Keep concise, tailor to audience]`

Attention aux enjeux :
-   Course aux assistants dominants.
-   Pouvoir de diriger les utilisateurs vers certains outils/entreprises.
-   Valeur des données d'usage.
-   Choix de l'IA : Pertinence ou profit ?
Implications économiques et éthiques.

### Slide 29 - Prochaines Étapes
*[38:30 - 40:00]*

Pour aller plus loin :
1.  Explorer les **notifications asynchrones** (potentiel énorme).
2.  Développer des **ontologies** métier pour guider les IA (cf. cas d'usage).
3.  Construire des **écosystèmes d'outils MCP** internes/externes.
4.  Mettre en place une **gouvernance** pour vos outils MCP.
5.  Intégrer MCP dans votre **stratégie d'architecture**.
6.  **[Action Immédiate Suggérée]** Commencez petit : Identifiez **un** processus simple dans votre équipe qui pourrait bénéficier d'un premier outil MCP expérimental.

Merci pour votre attention. Questions ?
