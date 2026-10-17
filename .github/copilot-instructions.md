# HomeMatch AI – Copilot instructions

## Product
Copilot immobilier d'aide à la décision pour les familles (pas un portail d'annonces). Il analyse un bien, un quartier et son adéquation avec le projet de vie de l'utilisateur.
Critères : prix, surface, trajet travail, écoles, crèches, sécurité, santé, commerces, espaces verts, potentiel de valorisation.

## Expérience "dating app" (web + mobile)
- Concept : un "Tinder du logement". L'utilisateur **swipe** des biens (droite = like, gauche = pass, haut = super like) ; chaque bien est une carte avec photo, prix, surface et **score de compatibilité en %** avec les critères de l'utilisateur.
- **Match** = bien dont le score dépasse le seuil de l'utilisateur ET qui est liké ; les matchs alimentent Favorites et la comparaison.
- Les **critères sont modifiables à tout moment** (curseurs de priorité : sécurité, écoles, transports, santé, budget, trajet…) ; le feed et les scores sont recalculés immédiatement. Chaque swipe alimente SearchHistory pour affiner (apprentissage = V3, règles explicites avant).
- Chaque carte doit afficher "pourquoi ce match" (sous-scores) ; explication IA en langage naturel à partir de la V2 uniquement.
- Une seule base de code : **Angular + Ionic + Capacitor** → PWA web + apps iOS/Android. Mobile-first, gestes tactiles + équivalents clavier/boutons sur web.
- Le backend expose des endpoints : feed paginé classé par score, swipe (like/pass), matchs, mise à jour des critères.

## Principes non négociables
- Le moteur de décision repose sur les **données et règles métier** (scoring déterministe). L'IA générative n'intervient qu'à partir de la V2, pour **expliquer et assister**, jamais pour décider.
- Priorités : sécurité, éducation, transports, santé, qualité de vie.
- Roadmap : V1 scoring → V2 IA explicative (Azure OpenAI) → V3 agent autonome → V4 marketplace. Ne pas implémenter une version future sans demande explicite.

## Stack
- Frontend : Angular + Ionic + Capacitor (web PWA + iOS/Android), Angular Material pour le web/desktop, Leaflet/OpenStreetMap.
- Backend : ASP.NET Core 9, REST, EF Core Code First, Repository pattern.
- BDD : SQLite (V1) → migration prévue PostgreSQL/PostGIS.
- Déploiement : Docker local.
- Données : OpenStreetMap, data.gouv.fr, INSEE, Île-de-France Mobilités.

## Architecture
- Couches : Domain (règles, scoring, sans dépendance) / Application / Infrastructure (EF Core, imports, géocodage) / API.
- **Aucune requête SQL spécifique SQLite** dans le domaine ; infrastructure isolée ; migrations EF Core obligatoires pour tout changement de schéma.
- Tables : Users, UserPreferences, Properties, Scores, Schools, HealthcareFacilities, Stations, Favorites, SearchHistory.

## Conventions
- Code, identifiants et commits en anglais ; textes UI et documentation produit en français.
- Pas de secrets dans le code (clés Azure OpenAI via configuration/variables d'environnement).
- Le scoring doit être testable, reproductible et expliquable (chaque score expose ses sous-critères et pondérations).
- Respect RGPD : données utilisateur minimales, pas de données personnelles dans les logs.
- Modifications ciblées ; ajouter/mettre à jour les tests avec chaque changement.

## Agents et prompts
Agents : `@dev`, `@tester`, `@code-reviewer` (`.github/agents`). Prompts : `/dev-feature`, `/write-tests`, `/code-review` (`.github/prompts`). Instructions par zone : `.github/instructions`.
Documents de vision : `C:\Users\DC6526\source\Ideas\HomeMatchAI_Completed`.
