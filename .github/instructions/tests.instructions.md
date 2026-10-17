---
applyTo: "**/*Tests*/**,**/*.spec.ts,**/*Tests.cs,**/*Test.cs"
---
# Tests

- Backend : xUnit + FluentAssertions (ou Assert), NSubstitute/Moq ; SQLite in-memory pour tests d'intégration EF Core ; `WebApplicationFactory` pour l'API.
- Frontend : Jasmine/Karma ou Jest selon la config du projet ; `HttpTestingController` pour les services.
- Nommage : `Method_Scenario_ExpectedResult`, structure Arrange/Act/Assert.
- Priorité : Scoring Engine (cas nominaux, bornes, données manquantes, pondérations), imports de données, comparaison de biens.
- Tests déterministes : pas d'appel réseau réel, pas de dépendance à l'heure ou à l'ordre d'exécution.
- Un test de non-régression par bug corrigé.
