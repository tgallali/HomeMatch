---
applyTo: "**/*.cs,**/*.csproj"
---
# Backend (ASP.NET Core 9 / EF Core)

- API REST, DTOs séparés des entités, validation des entrées, codes HTTP cohérents, `ProblemDetails` pour les erreurs.
- EF Core Code First + migrations ; accès aux données via interfaces Repository définies côté Domain/Application, implémentées dans Infrastructure.
- Pas de SQL brut ni de fonctions spécifiques SQLite ; rester compatible PostgreSQL/PostGIS.
- Scoring Engine : classes pures, sans I/O, pondérations configurables, résultat détaillé par critère.
- Imports de données (OSM, data.gouv, INSEE, IDFM) : idempotents, normalisés, géocodés, isolés dans Infrastructure.
- `async/await` partout avec `CancellationToken` ; injection de dépendances ; nullable activé.
- Aucun appel IA dans le chemin de décision (IA = V2+, explication uniquement).
