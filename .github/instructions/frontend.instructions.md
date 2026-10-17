---
applyTo: "**/*.ts,**/*.html,**/*.scss"
---
# Frontend (Angular + Ionic + Capacitor)

- Une seule base de code pour web (PWA) et mobile (Capacitor iOS/Android) ; mobile-first, responsive jusqu'au desktop.
- Composants standalone, typage strict, `OnPush`, signals/RxJS ; aucune logique de scoring côté client (le client affiche les scores du backend).
- Écran principal : **pile de cartes swipeable** (like / pass / super like), avec gestes tactiles, boutons et raccourcis clavier ; animation fluide, undo du dernier swipe, préchargement des cartes suivantes.
- Carte bien : photo, prix, surface, score de compatibilité %, sous-scores ("pourquoi ce match"), mini-carte Leaflet.
- Écrans : onboarding/profil, **curseurs de critères modifiables en direct** (recalcul du feed), matchs, comparaison, dashboard, historique, import d'annonce.
- Services API dédiés ; modèles TypeScript alignés avec les DTOs backend ; plugins Capacitor encapsulés derrière des services (notifications, géolocalisation, partage).
- Accessibilité (WCAG AA), alternatives non-gestuelles au swipe, textes en français i18n-ready.
- Gérer états chargement/vide ("plus de biens, élargis tes critères")/erreur et mode hors ligne basique.
