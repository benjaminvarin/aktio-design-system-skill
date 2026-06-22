# Changelog

Suivi des évolutions du skill `aktio-design-system`.

## [Non publié]
### Ajouté
- **Prérequis** : avertir l'utilisateur d'activer la librairie `Aktio - Design System (C14)` dans le fichier + étape 0 de vérification pour l'agent (`getAvailableLibraryVariableCollectionsAsync`).
- Section **Layout rules** (radius cards 24px, rythme spacing 16/8px, padding main container 40px, header bar + top nav bar obligatoires, usage du vrai composant drawer).
- Apprentissages des tests live : récolte de tokens via bindings, append avant FILL, config des composants imbriqués, icônes par défaut des chips.
- Fiche d'usage : `Value Card` (carte de chiffre clé cliquable, bouton d'action en état Empty, chip de variation / tag / sélection).
- Fiches d'usage : `lightbox`, `block`, `Stacked-List` (skeleton), `action-rail`.
### Corrigé
- Radius des cards : `rounded/6` (24px) au lieu de `rounded/2` (8px).
- Binding des tokens : `getLocalVariablesAsync` ne marche pas hors fichier DS → technique de récolte documentée.
- Comportement détaillé du `drawer` (ancrage, offset 8px, masque 30%, header fixed, animation).
- Masque de fond (`neutral/900` @ 30%) sur `modal` et `drawer`.

### À venir
- Fiches : Value Card, Segmented Buttons, Datepicker, checkbox/radio.
- Patterns d'écran complets (import FEC, tableau d'analyse).

## [0.1.0]
### Ajouté
- Tokens (couleurs, typographie, spacing, radius, icônes, effets, breakpoints).
- Catalogue de composants avec clés vérifiées + composants dépréciés.
- Fiches d'usage des 12 composants prioritaires.
- Workflow Figma MCP et pitfalls.
