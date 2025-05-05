# Programme de formation MCP

## Contexte

Formation d'une journée sur le Model Context Protocol (MCP) pour une audience mixte comprenant des développeurs, des data scientists et des profils métiers. Cette formation vise à faciliter la compréhension de l'intérêt du MCP et son application pratique à travers des cas d'usage emblématiques.

## Objectifs

- Comprendre les fondamentaux des LLMs et du MCP
- Maîtriser le fonctionnement technique des appels au LLM via MCP
- Découvrir les cas d'usage concrets du MCP
- Expérimenter la création et l'utilisation d'outils MCP

## Programme de la matinée

### 8h30 - 9h00 : Accueil des participants

- Café d'accueil
- Tour de table et présentation des objectifs de la journée

### 9h00 - 10h30 : Plénière d'acculturation sur le MCP

#### 1. Comprendre les LLMs (30 min)
- L'importance du langage comme interface naturelle
- Fonctionnement du moteur d'inférence
- La context window et ses limites
- La nature "stateless" des LLMs

#### 2. Introduction au MCP (30 min)
- Définition et architecture MCP
- Le langage universel des outils pour IA
- Les 3 super-pouvoirs du MCP :
  - Resources (accès en lecture)
  - Actions (modification)
  - Prompts (guides d'utilisation)

#### 3. Comparaison avec les API REST (30 min)
- MCP comme successeur des API REST
- L'importance cruciale des prompts
- La règle des 3U : Useful, Usable, Used

### 10h30 - 10h45 : Pause café

### 10h45 - 12h30 : Démonstrations et cas d'usage

#### 1. État actuel de l'adoption du MCP (15 min)
- Les grands acteurs (Anthropic, OpenAI, Google)
- Exemples concrets d'implémentation (Claude Code, GitHub Copilot)

#### 2. Cas d'usage de mémoire collective (30 min)
- Le problème de la mémoire isolée des LLMs
- Solution MCP : graphe de connaissances partagé
- Bénéfices concrets pour les équipes

#### 3. Démonstration technique (45 min)
- Anatomie d'un serveur MCP
- Communication entre client et serveur MCP
- Analyse des échanges et du protocole en action
- Les défis de sécurité et d'authentification

#### 4. Discussion et questions (15 min)
- Échanges sur les implications pour les participants
- Préparation aux ateliers pratiques de l'après-midi

## Programme de l'après-midi (Travaux pratiques)

### 13h30 - 16h30 : Ateliers pratiques

Les participants seront répartis en groupes mixtes (développeurs, data scientists, profils métiers) pour travailler sur des cas d'usage emblématiques. Chaque groupe aura à concevoir, implémenter et tester un outil MCP simple.

#### Atelier 1 : Création d'un outil MCP simple (3h avec pauses)
- Configuration d'un environnement de développement MCP
- Définition des ressources et actions
- Création des prompts efficaces
- Test et itération

#### Cas d'usage proposés :
1. **Accès à une base de connaissances interne**
2. **Interface en langage naturel pour des requêtes SQL**
3. **Automatisation de tâches administratives**

### 16h30 - 17h30 : Restitution et planification

- Présentation des projets par chaque groupe
- Identification des cas d'usage pertinents pour un POC plus ambitieux
- Discussion sur les prochaines étapes potentielles
- Plan d'action pour un POC de plus grande envergure

## Suites envisagées

Cette journée de formation constituera la base pour envisager un POC de plus grande envergure, dans un cadre de travail plus étendu dans le temps. L'objectif sera d'identifier, à partir des retours et des idées générées lors de cette journée, un ou plusieurs cas d'usage stratégiques qui pourraient bénéficier significativement de l'intégration du MCP.