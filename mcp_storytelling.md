# Script de présentation MCP : Les API du Futur pour l'IA

*Durée totale prévue : ~40 minutes (rythme soutenu)*

## Introduction (0:00 - 3:00)

### Slide 1 - Titre
*[0:00 - 1:30]*

**Titre:**
MCP: La Révolution des API pour l'IA
*Comment donner des super-pouvoirs à vos agents IA*
Les **3U** : *Useful, Usable, Used*

**Notes:**
- Bienvenue! Aujourd'hui nous plongeons dans le **Model Context Protocol**, ou MCP - un standard qui transforme radicalement la façon dont l'IA interagit avec le monde numérique.
- Imaginez des assistants IA qui ne sont plus limités à une simple conversation, mais capables d'agir concrètement sur vos systèmes - c'est ce que permet le MCP.
- Ce protocole est en train de devenir le langage universel entre les agents IA et les outils numériques.
- Nous découvrirons ensemble les "**3U**" essentiels: comment créer des outils véritablement *Utiles*, facilement *Utilisables* et effectivement *Utilisés* par les systèmes d'IA.

## Comprendre les LLMs: Le Langage est la clé

### L'importance du "L" dans LLM
- **L**arge **L**anguage **M**odel
- Le **langage** est l'interface naturelle entre humains
- Les LLMs comprennent et génèrent du **texte comme un humain**
- Nous passons de la **programmation** à la **conversation**

**Transformation fondamentale:**
- Code → Texte
- Requêtes → Questions
- Inputs/Outputs → Dialogues
- API → Conversation

**Notes:**
- Le "L" de LLM représente "Language" - c'est la caractéristique fondamentale
- Avant: interfaces spécialisées (code, APIs, requêtes SQL)
- Maintenant: langage naturel - l'interface universelle
- Démocratisation de l'accès à la technologie - n'importe qui peut "parler" à l'IA

### Moteur d'inférence: le cerveau du LLM

**Comment fonctionne un LLM:**
- L'**inférence** est le processus de génération de réponses
- Prédiction du **mot suivant le plus probable**
- Basé sur les **milliards de paramètres** appris
- Les performances dépendent de la **taille du modèle** et de sa **qualité d'entraînement**

**Notes:**
- Un LLM fonctionne comme un "compléteur de phrases" ultra-sophistiqué
- Il lit le texte précédent et prédit "Quel est le mot qui devrait suivre?"
- Cette prédiction se base sur tous les textes qu'il a "lus" pendant son entraînement
- Le moteur d'inférence est le composant qui exécute ces calculs en temps réel

### Context Window: la mémoire temporaire du LLM

- Espace "mémoire" pour la conversation en cours
- Limitée en taille (4K-128K tokens selon modèles)
- Tout ce qui est **hors context window est oublié**
- Impact direct sur la **pertinence** des réponses

**Analogie:**
- La context window est comme...
- La mémoire à court terme humaine
- Une page blanche limitée
- Un tableau qui s'efface quand il est plein

**Notes:**
- La context window est comme une conversation à une soirée
- Vous pouvez vous rappeler ce qui a été dit récemment (dans la fenêtre)
- Mais vous oubliez ce qui a été dit il y a longtemps (hors de la fenêtre)
- L'IA ne "se souvient" que de ce qui est dans sa context window actuelle
- Contrairement aux humains, le LLM n'a pas de mémoire à long terme native!

### Caractéristique fondamentale: LLMs sont Stateless

**Qu'est-ce que "stateless"?**
- Pas de **mémoire persistante** entre les appels
- Tout contexte doit être **explicitement fourni**
- Comme une personne avec **amnésie** à court terme
- Grande limitation pour les **agents autonomes**

**Exemple:**
```
Appel 1:
Utilisateur: "Mon nom est Olivier"
LLM: "Bonjour Olivier!"

Appel 2 (nouveau contexte):
Utilisateur: "Quel est mon nom?"
LLM: "Je ne connais pas votre nom, vous ne me l'avez pas dit."
```

**Notes:**
- Un LLM est comme un interlocuteur qui a une excellente compréhension et mémoire à court terme...
- ...mais qui "redémarre" complètement entre deux conversations
- Comme dans le film "Memento" - chaque interaction démarre sans souvenir des précédentes
- Les applications doivent gérer l'historique et le contexte elles-mêmes
- Cette nature "stateless" est à la fois une force (sécurité, prévisibilité) et une faiblesse (manque d'autonomie)

### La puissance des fonctions avec les LLMs

- Les fonctions permettent au LLM **d'agir** sur le monde
- Le LLM **génère du JSON** pour appeler une fonction
- Le serveur **exécute** et renvoie le résultat
- C'est ce qui transforme un **modèle** en **agent**

**Exemple:**
```json
// Définition de la fonction
{
  "name": "get_weather",
  "description": "Obtenir la météo",
  "parameters": {
    "location": {
      "type": "string",
      "description": "La ville"
    }
  }
}

// Appel par le LLM
{
  "name": "get_weather",
  "arguments": {
    "location": "Paris"
  }
}
```

**Notes:**
- Une "fonction" pour un LLM est une capacité qui lui est donnée d'interagir avec le monde extérieur
- Le processus se déroule en 4 étapes:
  1. On décrit la fonction au LLM (nom, description, paramètres attendus)
  2. Quand l'utilisateur demande quelque chose qui nécessite cette fonction, le LLM génère un appel structuré en JSON
  3. Le système intercepte cet appel, exécute réellement la fonction
  4. Le résultat est renvoyé au LLM qui peut poursuivre sa réponse
- C'est cette capacité qui permet de passer d'un simple "conversationaliste" à un véritable agent capable d'actions

### Le défi de l'intégration des fonctions

**Problèmes actuels:**
- Nécessite de **modifier le serveur d'inférence**
- **Couplage fort** entre LLM et fonctions
- Difficulté pour **ajouter** de nouvelles capacités
- Besoin d'une approche **standardisée**

**Solutions:**
- **Plugins/Add-ons**: Architecture extensible
- **API standardisées**: Découplage
- **MCP**: Protocole universel
- Passage de **l'intégration** à **l'interopérabilité**

**Et c'est exactement ce que résout le Model Context Protocol (MCP)!**

**Notes:**
- Pour ajouter des fonctions à un LLM, il faut traditionnellement:
  1. Modifier le serveur d'inférence lui-même
  2. Intégrer directement le code des fonctions au système
  3. Redéployer l'ensemble à chaque ajout de fonction
- Cela crée plusieurs problèmes:
  - Couplage fort entre l'IA et les outils
  - Complexité opérationnelle
  - Difficultés de maintenance
  - Impossibilité pour les utilisateurs d'étendre facilement les capacités
- Les premiers modèles ont tenté de résoudre ce problème avec des systèmes de plugins
- C'est précisément ce problème que le MCP vient résoudre - créer un standard universel pour connecter n'importe quel LLM à n'importe quel outil

## La solution: MCP, l'espéranto des agents IA

### L'architecture MCP en un coup d'œil

- **Hôte** : ChatGPT, Claude, etc. qui contient le modèle de langage
- **Client MCP** : "traducteur universel" entre l'IA et les outils
- **Serveurs MCP** : exposent différents outils et capacités

**MCP rend les outils numériques *visibles et utilisables* par n'importe quelle IA**

**Notes:**
- C'est comme ce qui s'est passé avec le Web:
- Avant: chaque service avait sa propre interface propriétaire
- Après: standard HTTP et HTML → explosion de la connectivité et des usages
- MCP fait la même chose pour les IA: standard universel d'accès aux outils
- Le point crucial: avec MCP, les outils deviennent "découvrables" par l'IA - ils s'annoncent et expliquent comment les utiliser

### MCP: Le langage universel des outils pour IA

- Lancé fin 2024 par *Anthropic*, rapidement adopté
- **Un standard ouvert permettant aux IA de découvrir et d'utiliser des outils externes de manière autonome et standardisée**
- Donne un **mode d'emploi autodescriptif** pour chaque fonction
- Les IA deviennent enfin **agents** capables d'agir!

**Exemple:**
```json
{
  "function_name": "get_weather",
  "description": "Récupère la météo pour un lieu.",
  "arguments": [
    {
      "name": "location",
      "type": "string",
      "description": "La ville à consulter."
    }
  ]
}
```

**Notes:**
- MCP est comme une "étiquette universelle" pour les outils numériques
- Chaque outil se présente: "Voici qui je suis, ce que je peux faire, et comment m'utiliser"
- L'IA peut alors "lire l'étiquette" et savoir exactement comment interagir avec l'outil
- **Autodescription**: L'outil se décrit lui-même en langage que l'IA comprend
- **Standardisation**: Format uniforme adopté par toutes les grandes entreprises d'IA
- **Simplicité**: Basé sur JSON, technologie largement maîtrisée

## Les 3 super-pouvoirs que MCP donne aux outils

### Le trio magique du MCP

**👁️ 1. Resources**
- **Les yeux** de l'IA
- Accès en lecture aux données
- Ex: lire un profil, consulter un prix

**✋ 2. Actions**
- **Les mains** de l'IA
- Modifier l'environnement
- Ex: envoyer un email, réserver

**🧠 3. Prompts**
- **Le mode d'emploi**
- Guide l'IA dans l'utilisation
- Le composant souvent négligé mais crucial!

**C'est l'association des trois qui crée la vraie puissance!**

**Notes:**
- Resources - Les yeux de l'IA
  - Équivalent des requêtes GET en REST
  - Permet à l'IA de "voir" les données du monde extérieur
  - Exemples concrets: liste des produits, météo d'une ville, profil utilisateur
  - Sans resources, l'IA reste limitée à sa connaissance interne
- Actions - Les mains de l'IA
  - Équivalent des requêtes POST en REST
  - Permet à l'IA d'agir et modifier l'environnement
  - Exemples vivants: envoyer un email, passer une commande, programmer un rendez-vous
  - C'est ce qui transforme réellement un assistant en agent
- Prompts - Le cerveau augmenté
  - Élément unique au MCP, sans équivalent REST
  - Fournit des guides, des templates et des connaissances à l'IA
  - Exemples: comment structurer une demande, quelles options sont disponibles
  - Composant souvent négligé mais absolument crucial pour qu'un outil soit effectivement utilisé

### La règle des 3U: créer des outils que les IA utiliseront vraiment

**🎯 Useful (Utile)**
- Résout un **vrai problème**
- Apporte une **valeur unique**
- A un **but clair**

**🔌 Usable (Utilisable)**
- Techniquement **accessible**
- Suit le **standard MCP**
- Interface **bien définie**

**👆 Used (Utilisé) - Le plus souvent négligé!**
- L'IA **choisit réellement** d'utiliser votre outil
- Clarté des noms, descriptions et **exemples**
- Les **Prompts MCP** sont la clé du succès ici

**Notes:**
- Useful (Utile) - Le fond
  - Un outil doit d'abord résoudre un problème réel et concret
  - Question clé: "Quelle valeur unique cet outil apporte-t-il?"
  - De nombreux outils échouent dès cette étape - ils n'ont pas de but clair
- Usable (Utilisable) - La forme
  - L'outil doit être techniquement accessible selon les standards MCP
  - Aspect technique: implémentation correcte de JSON-RPC, description des fonctions, etc.
  - C'est souvent l'aspect sur lequel les développeurs se concentrent le plus
- Used (Utilisé) - Le plus négligé!
  - L'aspect le plus subtil et souvent ignoré
  - Un outil peut être utile et utilisable, mais jamais choisi par l'IA
  - Analogie: un excellent restaurant caché dans une ruelle sans enseigne
  - Les Prompts MCP jouent un rôle crucial ici - ils guident l'IA vers votre outil
  - La plupart des outils échouent sur le "Used" - ils sont théoriquement bons mais pratiquement invisibles pour l'IA

## MCP: Les API REST du futur

### Une analogie puissante

**🧑‍💻 API REST = révolution du Web**
- Pour les **humains**
- A propulsé les **applications web**
- Interfaces pour les **développeurs**

**🤖 MCP = révolution des agents**
- Pour les **IA**
- Va propulser les **agents autonomes**
- Interfaces pour les **modèles de langage**

| API REST | MCP |
|----------|-----|
| `GET` (lecture) | **Resources** (lecture) |
| `POST` (action) | **Actions** (action) |
| *n'existe pas* | **Prompts** (guide) |

**Notes:**
- Les API REST ont révolutionné le développement web
  - Avant: Interfaces propriétaires, silos d'applications
  - Après: Écosystème interconnecté, explosion des applications web
- Même potentiel transformateur pour l'IA
  - Avant (maintenant): IA isolées, limitées à leur interface
  - Après: Écosystème d'outils interconnectés, explosion des agents IA
- Les correspondances techniques:
  - GET REST → Resources MCP (accès en lecture)
  - POST REST → Actions MCP (modification)
  - NOUVEAUTÉ: Prompts MCP (sans équivalent REST direct)
- L'innovation fondamentale:
  - REST supposait des développeurs humains qui lisaient la documentation
  - MCP est conçu pour que l'IA elle-même comprenne comment utiliser l'outil
  - C'est pourquoi les Prompts sont si cruciaux - ils sont le "manuel d'utilisation embarqué"

### Les prompts: le secret d'un outil MCP réussi

**🧠 Ce qu'ils font:**
- Guident l'IA vers le **bon outil** au bon moment
- Fournissent un **mode d'emploi contextuel**
- Définissent des **workflows** spécifiques

**📊 Exemple d'usage:**
- Graphe de connaissances structuré
- Ontologie commune pour la cohérence
- Vocabulaire standardisé (au lieu de synonymes aléatoires)

**Sans bons prompts, même l'outil le plus utile sera ignoré par l'IA!**

*Exemple : Sans prompt guidé, l'IA pourrait utiliser "créer_ticket" ou "log_issue". Avec un prompt spécifiant l'ontologie, elle utilisera toujours "enregistrer_incident(description, priorité)".*

**Notes:**
- Les prompts sont à l'IA ce que les panneaux de signalisation sont aux conducteurs:
  - Ils indiquent quand tourner (quand utiliser l'outil)
  - Ils montrent le chemin à suivre (comment utiliser l'outil)
  - Ils avertissent des dangers (les erreurs à éviter)
- Exemple concret: le graphe de connaissances
  - Problème: Sans guide, l'IA invente des termes différents à chaque utilisation
    - Session 1: "MCP" "est utilisé par" "Claude"
    - Session 2: "Claude" "implémente" "MCP"
    - Résultat: Graphe incohérent, impossible à interroger efficacement
  - Solution: Prompt MCP qui définit une ontologie stricte
    - Relations autorisées: uniquement "implémente", "étend", "utilise"
    - Classes d'entités: "Modèle", "Protocole", "Entreprise"
    - L'IA suit naturellement ces contraintes dans ses interactions
- Sans prompts bien conçus, l'outil peut être parfaitement fonctionnel mais jamais utilisé - l'IA ne saura pas quand et comment y faire appel

## Comment passer à l'action avec MCP

### MCP aujourd'hui: déjà une réalité

**🚀 Adoption rapide:**
- Standard adopté par **tous les grands acteurs**: Anthropic, OpenAI, Google
- Momentum croissant dans l'**industrie du logiciel**
- Intégrations **multiplateformes** en cours

**🛠️ Où le voir en action:**
- **Outils dev**: Claude Code, Cursor, GitHub Copilot
- **Plateformes**: Salesforce Einstein, ServiceNow
- **Systèmes internes**: Bases de connaissances, CI/CD

**⚠️ Le moment critique: être présent dès maintenant**
Les premiers à maîtriser MCP créeront les outils qui deviendront incontournables

**Notes:**
- Le momentum impressionnant:
  - Anthropic l'a présenté en décembre 2023
  - OpenAI a rapidement suivi avec GPT-4o
  - Google a annoncé son support
  - Cette adoption universelle est exceptionnelle dans l'histoire des standards!
- Exemples concrets d'utilisation actuelle:
  - Outils de développement: Claude Code, GitHub Copilot, Cursor
    - Permettent d'interagir avec le code, exécuter des commandes, manipuler des fichiers
    - Les développeurs sont le premier public cible (adoption facile)
  - Plateformes d'entreprise:
    - Salesforce intègre des capacités MCP à Einstein
    - ServiceNow expérimente avec des outils MCP pour l'automatisation
  - Systèmes internes: Bases de connaissances, CI/CD, BDD
- Nous sommes au début d'une vague - les premiers à déployer des outils MCP efficaces auront un avantage concurrentiel substantiel

### Comment démarrer concrètement avec MCP

**🏁 Plan d'action en 4 étapes:**
1. **Identifier** un cas d'usage à fort impact
2. **Prototyper** un serveur MCP simple
3. **Tester** avec des utilisateurs réels
4. **Itérer** en mesurant l'utilisation

**✅ Premiers cas d'usage idéaux:**
- Accès à des **connaissances internes**
- Automatisation de **tâches répétitives**
- Requêtes **SQL en langage naturel**
- Intégration avec **outils métier** existants

**Bonne nouvelle: MCP coexiste parfaitement avec vos API REST actuelles!**

**Notes:**
- Comment choisir votre premier projet MCP:
  - Critères de sélection:
    - Problème clairement défini avec valeur évidente
    - Fonctionnalité qui bénéficierait d'une interface en langage naturel
    - Système bien documenté (APIs ou services existants)
  - Exemples idéaux pour commencer:
    - Interface en langage naturel vers votre base de connaissances
    - Accès aux données métier (CRM, ERP) via conversation
    - Automatisation de tâches administratives (création de tickets, rapports)
- Approche de développement recommandée:
  - Commencer petit - un seul serveur MCP avec 2-3 fonctions bien conçues
  - Architecture: Adaptateur sur APIs existantes (pas besoin de tout reconstruire)
  - Cycle court: Prototype → Test → Mesure → Amélioration
  - Focus sur les prompts: Ils sont souvent négligés mais cruciaux pour l'adoption
- Erreurs courantes à éviter:
  - Trop de fonctions confuses (mieux vaut 3 claires que 20 vagues)
  - Descriptions trop techniques (pensez à comment une IA interprète votre outil)
  - Oublier de mesurer l'utilisation réelle de vos outils MCP
- Le MCP n'est pas une technologie de remplacement - c'est une couche d'adaptation pour rendre vos systèmes actuels accessibles aux agents IA

## Demain et après-demain: ce qui nous attend

### La feuille de route du MCP

**🔮 Prochaines évolutions:**
- **Notifications asynchrones** - pour les tâches longues
- **Communication inter-agents** (A2A)
- **Écosystèmes dédiés** par industrie
- **Standards d'interface** évolués

**⚠️ Défis à résoudre:**
- **Sécurité** - authentification et permissions
- **Gouvernance** - qui peut créer quels outils?
- **Design pour IA** - nouvelle expertise
- **Découvrabilité** - trouver les bons outils

**Phase actuelle: Construction (II/III)**

| **I. Genèse** | **II. Construction** | **III. Écosystème** |
|---------------|----------------------|---------------------|
| ✅ Terminée   | 🔄 En cours         | ⏳ Futur            |

**Notes:**
- Évolutions imminentes (12-18 mois):
  - Notifications asynchrones: Permettra aux agents de gérer des tâches de longue durée
    - Exemple: "Je vais analyser cette base de données et te notifier quand j'aurai terminé"
    - Franchira une barrière majeure pour l'autonomie des agents
  - Déploiements à grande échelle: Intégration dans les plateformes mainstream
    - Les entreprises vont standardiser leurs approches MCP internes
    - Les plateformes SaaS proposeront des interfaces MCP natives
- Défis à résoudre:
  - Sécurité: MCP lui-même ne spécifie pas les mécanismes d'authentification
    - Solution: Utiliser des standards existants (OAuth, etc.) comme couche complémentaire
    - Question critique: Quelles permissions donner aux agents?
    - Note : MCP lui-même ne spécifie pas l'authentification, mais s'appuie généralement sur des standards comme OAuth2/JWT transmis via les headers ou le contexte de l'appel
  - Gouvernance: Risque de prolifération désordonnée d'outils MCP
    - Besoin de politiques internes: Qui peut publier? Quels standards de qualité?
    - Probable émergence de "places de marché" certifiées d'outils MCP
- Cycle d'Évolution - où nous en sommes:
  - Phase I (Genèse): Définition du standard, preuves de concept → TERMINÉE
  - Phase II (Construction): Déploiements réels, premières intégrations → ACTUEL
  - Phase III (Écosystème): Web d'outils MCP interconnectés → FUTUR (2-3 ans)
- Nous sommes actuellement à un moment critique - assez matures pour des déploiements réels, mais encore assez tôt pour influencer l'écosystème

## Un exemple concret: la mémoire collective pour les développeurs

### Le défi de la mémoire collective

**Aujourd'hui:**
- Chaque IA a sa propre mémoire **isolée**
- Perte de contexte entre sessions
- Duplication du travail d'équipe
- Inconsistance des connaissances
- Pas de mémoire institutionnelle

**Solution MCP:**
- Graphe de connaissances **partagé** via MCP
- Les IA ont accès aux **décisions architecturales** de l'équipe
- Chaque interaction **enrichit** la base commune
- Les **bonnes pratiques** sont automatiquement partagées
- Les nouveaux membres bénéficient immédiatement du **savoir collectif**

**Notes:**
- Le problème de mémoire des IA:
  - Imaginez une équipe où chaque personne perd la mémoire chaque soir:
    - Chaque matin, tout le monde doit réapprendre les décisions prises hier
    - Impossible de capitaliser sur les expériences passées
    - Chacun redécouvre les mêmes problèmes de manière isolée
  - C'est exactement ce qui se passe avec les assistants IA actuels:
    - ChatGPT, Copilot et autres assistants ont une mémoire limitée à la session
    - Entre chaque session ou utilisateur, tout est "oublié"
    - Le même problème peut être résolu 10 fois différemment par 10 membres d'équipe
- La solution MCP expliquée:
  - Architecture: Un serveur MCP exposant un "graphe de connaissances"
    - Format simple: stockage de triplets (Sujet, Prédicat, Objet)
    - Exemple: "Notre système" "utilise" "PostgreSQL"
  - Fonctionnement:
    - Les IA peuvent interroger ce graphe pour comprendre le contexte d'équipe
    - Elles peuvent également y ajouter des informations pertinentes
    - Toute l'équipe bénéficie des interactions individuelles
- L'importance des prompts MCP ici:
  - Sans prompt guidant, chaque IA crée des relations différentes:
    - "PostgreSQL" "est la base de données de" "Notre système"
    - "Notre système" "dépend de" "PostgreSQL"
    - "On utilise" "PostgreSQL" "pour notre projet"
  - Avec prompts MCP appropriés:
    - Vocabulaire contrôlé: seuls certains prédicats sont autorisés
    - Relations standardisées: uniquement "utilise", "dépend de", etc.
    - Résultat: graphe cohérent qui peut être interrogé efficacement

## Ce qu'il faut retenir pour demain

### La troisième vague de la révolution numérique

**1990-2010: Web & API REST**
- Services accessibles depuis chez soi

**2010-2020s: Mobile & Apps**
- Services accessibles partout

**2024-2030: Agents IA & MCP**
- Délégation cognitive des tâches

**MCP sera aux agents IA ce que les API REST ont été au Web**

**Notes:**
- Les trois révolutions numériques:
  - Vague 1 - Web (1990-2010):
    - Avant: Services accessibles uniquement en personne ou par téléphone
    - Innovation technique: HTTP, HTML, API REST
    - Résultat: Services accessibles depuis son domicile
  - Vague 2 - Mobile (2010-2020):
    - Avant: Services accessibles uniquement depuis un ordinateur fixe
    - Innovation technique: Apps mobiles, 4G, services cloud
    - Résultat: Services accessibles n'importe où, n'importe quand
  - Vague 3 - Agents IA (2020-2030):
    - Avant (maintenant): Services nécessitant une attention humaine constante
    - Innovation technique: LLMs, MCP!
    - Résultat: Services exécutés automatiquement par des agents autonomes
- Le parallèle historique clé:
  - Les API REST ont joué un rôle catalyseur dans la révolution Web:
    - Avant: Chaque service avait son propre protocole
    - Après: Standard commun, explosion des possibilités de connexion
  - MCP joue exactement le même rôle pour la révolution des agents IA:
    - Avant: Chaque outil a son propre format d'intégration avec l'IA
    - Après: Standard commun, explosion de l'écosystème d'outils IA
- Ceux qui ont saisi l'importance des API REST au début des années 2000 ont pris une avance considérable. La même opportunité se présente aujourd'hui avec MCP

### 3 clés pour réussir avec MCP

**🔑 1. Le nouveau standard**
- MCP est aux agents IA ce que REST a été au Web
- **Intégrez-le** maintenant dans votre stratégie

**👁️ 2. L'affordance pour IA**
- Un outil doit **guider** l'IA sur quand et comment l'utiliser
- Les **prompts** sont le mode d'emploi

**🎯 3. Les 3U**
- **U**seful (Utile)
- **U**sable (Utilisable)
- **U**sed (Utilisé)
- Le dernier est le plus **souvent négligé**

**Notes:**
- Clé #1: MCP = Le standard essentiel
  - Ce n'est pas juste un autre protocole technique
  - C'est le fondement de la prochaine génération d'applications IA
  - Adopté massivement par tous les grands acteurs (Anthropic, OpenAI, Google...)
  - Message d'action: Commencez à l'intégrer dans votre réflexion stratégique dès maintenant
- Clé #2: L'affordance pour IA est différente
  - Nouveau paradigme: concevoir pour un utilisateur IA, pas humain
  - L'affordance pour humains est souvent visuelle (boutons, icônes)
  - L'affordance pour IA est textuelle et contextuelle
  - Les prompts MCP sont cruciaux - ils sont le véritable guide d'utilisation
- Clé #3: Cadre d'évaluation des 3U
  - Useful: Résout un vrai problème (le "quoi")
  - Usable: Techniquement accessible via le protocole standard (le "comment")
  - Used: Effectivement choisi par l'IA parmi les options disponibles (le "est-ce que")
  - Ce dernier point est le plus souvent négligé mais essentiel - un outil peut être utile et utilisable mais jamais choisi!
- Conseil d'action: Commencez avec un cas d'usage simple mais à fort impact - une interface en langage naturel vers vos données ou systèmes les plus utilisés

### L'enjeu de pouvoir que personne ne voit venir

**🏆 La course aux assistants**
- Qui décidera quels outils MCP seront utilisés?
- Les plus **pertinents**... ou les plus **rentables**?

**⚠️ Questions cruciales**
- Qui **contrôlera** l'assistant?
- Comment seront **classés** les outils?
- Quelle **transparence** sur les choix?
- Quelles **données** seront collectées?
- Risque de nouveaux **monopoles**

**Notes:**
- Un parallèle historique instructif:
  - Rappel du précédent: Google et le référencement
    - Contrôler le moteur de recherche = contrôler l'accès au web
    - Modèle économique basé sur la valorisation de cette position dominante
  - Ce qui se profile avec les assistants IA:
    - Contrôler l'assistant = contrôler l'accès aux outils numériques
    - Potentiel modèle: "payer pour être recommandé" par l'IA
- Questions stratégiques:
  - Pour les entreprises:
    - Comment s'assurer que vos outils sont "visibles" par les assistants IA?
    - Faudra-t-il "payer" pour être bien référencé dans l'écosystème MCP?
  - Pour la société:
    - Risque de concentration de pouvoir encore plus importante qu'aujourd'hui
    - Nécessité potentielle d'une régulation spécifique
    - Enjeu de transparence sur les critères de recommandation
- Anticiper cet enjeu dès maintenant en positionnant vos outils de manière stratégique dans l'écosystème MCP naissant

### Votre plan d'action

**📋 À court terme (1-3 mois)**
- Former vos équipes aux concepts MCP
- Identifier 1-2 cas d'usage à fort impact
- Créer un prototype simple de serveur MCP

**🔍 À moyen terme (3-6 mois)**
- Déployer un premier outil MCP en production
- Créer des prompts MCP efficaces
- Établir des guidelines d'affordance pour IA

**🚀 À long terme (6-12 mois)**
- Développer une stratégie MCP d'entreprise
- Créer un écosystème d'outils interopérables
- Explorer les notifications asynchrones

**⭐ Le conseil clé**
- Commencez petit, mesurez l'usage, et itérez rapidement!
- Un seul outil MCP bien conçu vaut mieux que dix outils négligés.

**Notes:**
- Actions immédiates (1-3 mois):
  - Formation: Sensibiliser vos équipes tech aux concepts et potentiel de MCP
    - Partager cette présentation en interne
    - Organiser un atelier pratique sur MCP
  - Cas d'usage: Identifier 1-2 applications internes qui bénéficieraient d'une interface IA
    - Privilégier: Base de connaissances, outils développeurs, données structurées
    - Choisir un cas à valeur ajoutée claire mais techniquement simple
- Actions à moyen terme (3-6 mois):
  - Implémentation: Créer votre premier outil MCP opérationnel
    - Se concentrer sur les 3U: utile, utilisable, utilisé
    - Porter une attention particulière aux prompts
  - Mesure: Mettre en place un suivi d'usage pour comprendre comment l'IA utilise vos outils
    - Quels outils sont choisis? Lesquels sont ignorés?
    - Itérer rapidement pour améliorer la "découvrabilité"
- Vision à long terme (6-12 mois):
  - Stratégie: Intégrer MCP dans votre architecture d'entreprise
    - Définir une gouvernance claire
    - Établir des standards d'implémentation
  - Écosystème: Créer un ensemble cohérent d'outils interopérables
    - Ontologies communes
    - Interface cohérente pour l'IA
- L'important est de commencer maintenant, même modestement - l'expertise se construit en faisant

### Merci! Des questions?

Pour continuer la conversation:
- Documentation officielle: [MCP @ Anthropic](https://blog.anthropic.com/introducing-model-context-protocol)
- @owulveryck sur Bluesky et olivier.wulveryck sur LinkedIn

*Le futur des interactions IA-outils est en train de s'écrire maintenant...*