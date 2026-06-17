# Aktio — Design System Skills

Skills (au sens « instructions pour une IA ») décrivant le design system **Aktio — Design System (C14)** et comment l'utiliser pour générer des maquettes et prototypes, principalement dans Figma via le MCP.

## Contenu

| Skill | Description |
|---|---|
| [`skills/aktio-design-system`](skills/aktio-design-system/SKILL.md) | Tokens (couleurs, typo, spacing, radius, effets), catalogue de composants avec clés vérifiées, fiches d'usage par composant, et workflow Figma MCP. |

## Fichiers Figma de référence

- **Design System (source) :** `zJxaJRtHPZOHKN5meFlFIw`
- **Fichier de travail (instances) :** `EjuZtLgmnmge6ZlxamyKK9`
- **Librairie facteurs d'émission :** `rEhc4mC1R1u3oQ4WFSglkz`

## Comment utiliser ce skill

Coller le contenu de `SKILL.md` dans le contexte de l'IA (ou le déposer comme skill/projet) avant de lui demander de générer ou éditer du design dans le fichier Figma Aktio.

## Convention de travail

- `main` contient la version de référence validée.
- Travailler les évolutions sur une branche (`git switch -c maj-composants`), puis fusionner.
- Un commit = un changement cohérent (ex. « ajoute fiche Value Card »).

## Maintenance

Les clés de composants et tokens reflètent l'état de la librairie à la date du dernier commit. Si un import échoue (« component not found »), le composant a été renommé/republié : relancer une recherche dans le fichier source pour récupérer la clé à jour.
