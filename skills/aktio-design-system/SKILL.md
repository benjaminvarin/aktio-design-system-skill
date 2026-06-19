---
name: aktio-design-system
description: Generate and edit Aktio designs in Figma using the official "Aktio — Design System (C14)" library. Use whenever building screens, mockups, or prototypes in the Aktio Figma file (key EjuZtLgmnmge6ZlxamyKK9) via the Figma MCP — to apply the correct tokens (colors, typography, spacing, radius, shadows) and to import components by their verified keys instead of recreating them or hardcoding values.
---

# Aktio — Design System (C14)

Reference for generating Aktio product UI in Figma via the MCP `use_figma` / `search_design_system` tools. Targets **desktop-only** interfaces.

- **Working file:** `EjuZtLgmnmge6ZlxamyKK9`
- **Active library:** `Aktio - Design System (C14)`
- **Library key:** `lk-6ddc3941d4bbe8ebd76a8bcbab4e86558c64adabf1ea1d3ff9bc747d56a5fddb81e17ec4f52d498b4bfd06003d232906dd218556145db85d72fb431c4d49f8ad`
- **Type face:** `Inter` (only). Note Figma style names use a space: `Semi Bold`, `Extra Bold` — never `SemiBold`.

## Golden rules

1. **Never hardcode a value that exists as a variable.** Bind fills, strokes, spacing, radius, and effects to the variables below. Use `setBoundVariable` / `setRangeBoundVariableForPaint` rather than raw hex/numbers.
2. **Never recreate a component.** Always `search_design_system` (scoped to the library key above) then import by key with `importComponentByKeyAsync` / `importComponentSetByKeyAsync`.
3. **Restrict `search_design_system` to the active library key.** The file pulls in stale libraries (Concrete, Aktio.cc, Component Tutorial, 🧩 emoji libs). Ignore anything whose `libraryName` is not `Aktio - Design System (C14)`.
4. **Avoid deprecated / legacy.** Skip any name containing `[Deprecated]`, `[deprecated]`, or the legacy `Aktio - Font/…` and `Color (à déplacer)/…` token groups. Prefer `[New]` / `[NEW]` variants.
5. **Search queries must be short.** One or two words ("chip", "drawer", "table"). Long multi-word queries return empty.
6. **Use literal property names.** Variant values are **PascalCase** (`Filled`, `Enabled`, `Danger`) — not lowercase, despite what library descriptions suggest. Content properties carry a `#id` suffix (e.g. `Label#4736:2`, `Title#3933:0`). Pass these exact strings to `setProperties`; a reformatted name silently no-ops. Exception: `Toggle` uses lowercase variant values (`selected`, `unselected`).
7. **Overlay hierarchy.** Pick the least intrusive surface that fits: toaster (transient confirmation) < information message (inline, persistent) < drawer (edit one item, keeps context) < modal (blocking decision). Never use a modal for routine feedback.

## Tokens

### Colors

Primary brand is **purple**; the neutral ramp is `neutral/000→900`. Semantic ramps (green/yellow/red/blue) each run 100→900. `illustrative/*` are for charts and data viz only — not UI chrome.

| Role | Token | Hex |
|---|---|---|
| Brand / primary | `purple/500` | `#796ddb` |
| Brand hover (darker) | `purple/600` | `#5239b5` |
| Brand tint (bg) | `purple/100` | `#f8f7fd` |
| Brand tint (border) | `purple/200` | `#e4e2f8` |
| Surface / white | `neutral/000` | `#ffffff` |
| App background | `neutral/100` | `#f9fafa` |
| Border subtle | `neutral/300` | `#e8eaea` |
| Border default | `neutral/500` | `#d1d4d5` |
| Text disabled / icon | `neutral/400` | `#babec0` |
| Text secondary | `neutral/600` | `#747d81` |
| Text body | `neutral/800` | `#455157` |
| Text strong / headings | `neutral/900` | `#17262d` |
| Danger | `red/500` | `#f68d7c` |
| Success | `green/500` | `#75cbae` |
| Warning | `yellow/500` | `#fdc933` |

Semantic tints follow the same pattern: `…/100` background, `…/200`–`/300` border, `…/500`–`/600` text/icon (e.g. a success banner = `green/100` bg, `green/600` text).

Icon is colored regarding text it is featured with. For instance if text is `neutral/800` icon is `neutral/800`

**Do not use:** the duplicated `Black/*`, `Purple/*` (capitalized), `Neutral Black / Night`, `Primary`/`Secondary`/`Danger` aliases, or `Color (à déplacer)/*`. These are legacy aliases of the canonical lowercase tokens above.

### Typography

Canonical scale is the `Display / Heading / Body / Label` groups (all Inter). Ignore the legacy `Aktio - Font/Aktio-*` group.

| Token | Style | Size / LH / LS |
|---|---|---|
| `Display/Display-1` | Light | 80 / 80 / -1 |
| `Display/Display-2` | Light | 56 / 56 / -1 |
| `Display/Display-3` | Regular | 40 / 40 / -1 |
| `Display/Display-4` | Regular | 28 / 32 / 0 |
| `Heading/Heading-1` | Medium | 24 / 32 / 0 |
| `Heading/Heading-2` | Semi Bold | 18 / 28 / 0 |
| `Heading/Heading-3` | Medium | 16 / 24 / 0 |
| `Heading/Heading-4` | Medium | 12 / 24 / 3 (uppercase label) |
| `Body/Body-1` | Regular | 16 / 24 / 0 |
| `Body/Body-1-Med` | Medium | 16 / 24 / 0 |
| `Body/Body-2` | Regular | 14 / 20 / 0 |
| `Body/Body-2-Med` | Medium | 14 / 20 / 0 |
| `Label/Label-1` | Regular | 12 / 16 / 3 |
| `Label/Label-1-Med` | Medium | 12 / 16 / 3 |
| `Label/Label-2` | Regular | 8 / 12 / 3 |

### Spacing

Base-4 scale, token group `spacing/*`: `0,5`=2, `1`=4, `1,5`=6, `2`=8, `4`=16, `6`=24, `8`=32, `10`=40. Use `Spacing/space-*` aliases only if a component already references them. Default gutter inside cards/rows = `spacing/4` (16); section gaps = `spacing/6`–`8`.

### Radius

Token group `rounded/*`: `1`=4, `2`=8 (default for inputs, buttons, cards), `4`=16, `6`=24, `full`=9999 (pills, chips, avatars). `Radius/radius-s`=8 is the alias.

### Icon sizes

`icon/xs`=14, `icon/s`=16, `icon/m`=18, `icon/l`=20.

### Elevation & glow effects

| Token | Use |
|---|---|
| `Elevation/M` | Drop shadow for drawers, menus, popovers, raised cards |
| `Glow/Hover` | Purple focus/hover glow on interactive elements |
| `Glow/Danger` | Error-state glow |
| `Glow/Warning` | Warning-state glow |

### Breakpoints (desktop)

`breakpoint/laptop`=1280. The `dim/*` group holds fixed widths (e.g. `dim/240`=960, `dim/360`=1440). Badge rails switch density at 1440px.

## Component catalogue (verified keys)

Import sets with `importComponentSetByKeyAsync(key)` then pick the variant; import single components with `importComponentByKeyAsync(key)`.

### Actions & inputs

| Component | Type | Key | Notes |
|---|---|---|---|
| `[NEW] Button` | set | `0c027d234b8da770591ef02e687a030658f2356b` | Variants: Style (filled/transparent/danger), State (enabled/hovered/focused/pressed/disabled), UI (light/dark). Icon sits left of label. |
| `icon-button` | set | `fe2296044d57b6c5355ec4937d78afb55659b894` | |
| `Segmented Buttons` | set | `89aa795e8fcd2ccb566ddf369989751eabc6f794` | |
| `[New] Input` | set | `f8b373817ea0bdc33e9e286976be3d7bda73ee54` | |
| `Select` | set | `ae9713df2b4c0a4f5ee58098aa09b1cad49f3d26` | |
| `Menu` | component | `903315072750d2a51def1871d3987db98a32d074` | Dropdown menu surface for Select. |
| `Edit-text-box` | set | `cd741809aaef9b0b44ecead8a83dcae8c2185371` | Inline editable text field. |
| `checkbox` | set | `4f4872efe5f73480de77af2fa5e5ff4cf962691b` | |
| `check box with text` | set | `6e0c8c883fedd8aa7cdee47c3eb8093f7649bbe0` | Checkbox + label row with hover. |
| `radio` | set | `aacec95a7b60ded2ec2ab928fd1fd2c3c360eb22` | |
| `radio with text` | set | `f8f6ca0242b37ed96d13d93406b82775695bd5d1` | |
| `Toggle` | set | `797a4191277c0e1bb1f3ef5b4d7283fd803cc43f` | |

### Chips, tags, badges

| Component | Type | Key | Notes |
|---|---|---|---|
| `[New] chips` | set | `3039d84d4058febd1e51d9b2fd93158e95858e98` | Sizes SM/S/XS; styles défaut/neutre/succès… Use for filters, selections, input units. |
| `Chips display` | set | `51888a424468c3af1593385225104dfa67fe3299` | Container that lays out multiple chips. |
| `railing-chips` | set | `bab5bc2b4207d24a7f50b4455c1fc2716d46c607` | |
| `Tag/Colored` | set | `54c51267ca34ea58390c889d8560a73570c701fa` | |
| `Badges rail` | set | `be3e93fef6d072d695e1b66bfb0724d65929286f` | Caps at 4 badges ≥1440px, 2 below, then "+N". |

### Surfaces & overlays

| Component | Type | Key | Notes |
|---|---|---|---|
| `drawer` | component | `71f17e78ee18b1316ed9829f09f2acb9cf169180` | Right-side panel. Pair with `Elevation/M`. |
| `lightbox` | component | `84357d26143503e9727d3a8cc70a1e06a3591d17` | Modal. |
| `Lightbox heading bar` | component | `d6ab68a7c08ed93c636deee4e550f7cec53f4108` | Title bar for lightbox. |
| `[New] Toaster` | set | `1f811c5c0a888b40287d8775d42c901a9eba68f2` | Bottom-right transient feedback. |
| `Value Card` | set | `80ef843e981cc469de7ffc5b335ba5ede7cb7474` | KPI / metric card. |

### Table system

`table` is the container; build rows from the cell primitives. Assemble in this order: `table` → `Table Tilte Row` (header) using `table column title` cells → `Table Row` using `table cell text` / `table cell - element` cells → `table footer`. `[NEW] top control bar` will replace the raw of `table column title` when raw are selected.

| Component | Type | Key |
|---|---|---|
| `table` | component | `88c9f660f8b822c1b4ef56103aa21308f2f10446` |
| `table-with-heading` | component | `23178fbeb9ccb1160f98ea3c050964372b1cdea7` |
| `[NEW] top control bar` | set | `c3a406d78444dce3ce366e5208ed2a57d440793d` |
| `Table Tilte Row` | component | `12d6c39a5c4db345f97b935f67e641ab07bf71ac` |
| `table column title` | component | `2fc0460911e1cb49329400ee55a38b57c6d64f4f` |
| `table column title with element` | component | `4ef83047fdca0fa09f34fe5df2b2182374de625f` |
| `table - column checkbox` | component | `3c61f902362cee457807dc4eab33a4b1c6df660d` |
| `Table Row` | component | `0f78d2c4350f36af70cf587887d42f008580e439` |
| `table cell text` | component | `54aeb99f3e050031c5e207468a3955940b3a56e6` |
| `table cell text element` | component | `9c60c3619e658b6f6aec0d2f4dfdc6c2a36a2d5f` |
| `table cell - text small` | component | `bbcbf7345dc776393005472ec8848321184151a0` |
| `table cell - text small + element` | component | `06d59aa9c76d173e73fce2d03a6f7bbc5ada9325` |
| `table cell - element` | component | `01ce695cffc9257ec0706136a10489771d3ae7f1` |
| `table cell - checkbox` | component | `bcc64e8c08cae55ed27e40ddaf7a8c5372eee100` |
| `table footer` | component | `599e2f59525efbb09f89364bf396497d719fa880` |

### Navigation & layout

| Component | Type | Key |
|---|---|---|
| `Menu Vertical` | set | `f263210436b923559e155f802419a6fde6c9d1c2` |
| `screen-fullwidth` | component | `888d7ff39887ff52fe882a9f680562feb1f61ec6` |

> Keys reflect the library as of June 2026. If `importComponentByKeyAsync` throws "not found", the component was renamed/republished — re-run `search_design_system` (scoped to the library key) to get the fresh key rather than guessing.

## Component usage guides (top 12)

Each guide lists the real variant/content properties (extracted from the source DS file `zJxaJRtHPZOHKN5meFlFIw`) plus when to use it. Lines marked ⚠️ are assumed usage rules — **Benjamin to confirm/correct.** Format per component: *Variants · Content props · When · Tokens · Pose*.

### `[NEW] Button` — set · `0c027d234b8da770591ef02e687a030658f2356b`
- **Variants:** `Style` = Filled | Transparent | Danger (def. Filled) · `State` = Enabled | Hovered | Focused | Pressed | Disabled · `On dark` = False | True · `With icon` = True | False
- **Content:** `Label#4736:2` (text) · `Icon#4736:1` (instance swap)
- **When:** exactly one `Filled` (primary action) per zone/screen · `Transparent` = secondary actions · `Danger` = destructive actions only (delete…) · `On dark=True` only on dark surfaces · never stack two primaries side by side.
- **Tokens:** label `Body/Body-1-Med` · radius `rounded/2` · fill `purple/500` (hover `purple/600`).
- **Pose:** `setProperties({ Style:"Filled", State:"Enabled", "On dark":"False", "With icon":"True" })`

### `[New] Input` — set · `f8b373817ea0bdc33e9e286976be3d7bda73ee54`
- **Variants:** `States` = Enabled | Hovered | Focused | Disabled | Danger | Read Only | Opened · `Is Filled` = False | True
- **Content (bool + text):** `With label#7233:51`, `Label#4942:7`, `With support text#4942:9`, `Support text#4942:6`, `Placeholder#4942:10`, `With L element#4962:0` + `Left element#4962:14` (swap), `With R element#4962:21` + `Right element#4962:28` (swap), `Reset#7230:0`, `Text filled#7253:13`
- **When:** `States=Danger` for validation errors, with the support text used as the error message · `Read Only` for non-editable values · L/R element for an icon or a unit chip on the right.
- **Tokens:** text `Body/Body-2` · radius `rounded/2` · border `neutral/300` (focus `purple/500` + `Glow/Hover`).
- **Pose:** `setProperties({ States:"Enabled", "Is Filled":"False", "With label#7233:51":true })`

### `Select` — set · `ae9713df2b4c0a4f5ee58098aa09b1cad49f3d26`
- **Variants:** `Style` = Input | Chips · `States` = Enabled | Opened | Filled | Disabled
- **Composition:** dropdown surface = `Menu` (`903315072750d2a51def1871d3987db98a32d074`) + `.Menu Item` rows.
- **When:** `Style=Input` inside forms · `Style=Chips` for an inline filter · `Opened` only while the menu is shown.
- **Pose:** `setProperties({ Style:"Input", States:"Enabled" })`

### `[New] chips` — set · `3039d84d4058febd1e51d9b2fd93158e95858e98`
- **Variants:** `Style` = Default | Neutral | Success | Warning | Danger · `States` = Enabled | Hovered | Pressed | Selected | Disabled · `Size` = SM | S | XS
- **Content:** `Label#3255:6`, `With text#3266:0`, `With icon left#3255:9` + `Icon left#3255:7` (swap), `With icon right#3255:5` + `Icon right#3255:8` (swap)
- **When:** filters, multi-selections, input units, third level action · semantic colour reflects meaning (Success/Warning/Danger = status, not decoration) · `Selected` for the active filter state.
- **Pose:** `setProperties({ Style:"Default", States:"Enabled", Size:"SM" })`

### `Toggle` — set · `797a4191277c0e1bb1f3ef5b4d7283fd803cc43f`
- **Variants:** `States` = selected | unselected (+ hover/pressed/disabled of each). ⚠️ **lowercase** — exception to the PascalCase rule.
- **When:** immediate on/off with no confirmation · for a labelled choice prefer `toggle with text` (`46acd9a8ec25b8335b1751d836bfe0e4591f0ccf`) or `toggle bloc with text` (`9284835d0d7287c23b763497d5b59e9bd4ae4e84`).
- **Pose:** `setProperties({ States:"unselected" })`

### Table system — assembled, not a single component
- **Skeleton:** `[NEW] top control bar` (`c3a406…`) on top → header `Table Tilte Row` (`12d6c3…`) built from `table column title` (+ `table - column checkbox` if selectable) → rows `Table Row` (`0f78d2…`) built from cells (`table cell text`, `table cell - element`, `table cell - checkbox`…) → `table footer` (`599e2f…`) for pagination. Container `table` / `table-with-heading` wraps it. When a raw is hovered, you can display, at the right-hand 8px margin right, an `action-rail`, this action rail is used for quick actions (edit, duplicate, delete…).
- **When:** Use to display information or list in table · add the checkbox column whenever multi-select / bulk actions exist. · If information to display are few, you can use a `Stacked-list`made of `Stacked-list-item`.

### `drawer` — component · `71f17e78ee18b1316ed9829f09f2acb9cf169180`
- **Props:** `Title#3933:0` (text) · `content#8555:2` (SLOT to fill)
- **Already contains:** `icon-button` (close) · `[NEW] Button` (bottom actions).
- **When:** edit/qualify **one** item without leaving the table (table+drawer pattern). For a blocking decision or critical message use `modal` instead.
- **Layout & behaviour:** side panel over the content, anchored **right**, full screen height, **offset 8px** top / right / bottom. Backdrop mask over the content below: `neutral/900` at **30% opacity**. The header is **fixed**; only the body content scrolls inside. Enters by **sliding right→left**, exits left→right.
- **Tokens:** shadow `Elevation/M` · mask `neutral/900` @ 30%.

### `modal` — set · `76ac1c2a5272979e1eff9ff24d5b5902c59eb61d`
- **Variants:** `Type` = Basic | Error · slot `Container#8347:0` · internal bars `.modal - heading bar` (`d41336…`) / `.modal - bottom bar` (`b05dd4…`).
- **When:** important info or blocking decision, centre-screen · `Error` for destructive confirmation / severe error · otherwise prefer drawer (edit) or toaster (non-blocking feedback).
- **Backdrop:** mask over the content below, `neutral/900` at **30% opacity** (same as drawer).
- **Pose:** `setProperties({ Type:"Basic" })`

### `Badges` — set · `fbc999c975fa3505709fad058b97aa3adee726cb`
- **Variants:** `Style` = Portrait | Letter · `Size` = S · **Content:** `Label#201:0`
- **Composition:** for several users use `Badges rail` (`be3e93…`) which handles the "+N" overflow (4 badges ≥1440px, 2 below).
- **When:** represent a user (Portrait if photo, Letter otherwise).
- **Pose:** `setProperties({ Style:"Letter", Size:"S" })`

### `Information message` — set · `91c9764ba86c8a94ce6a5b296952f18a561f4367`
- **Variants:** `Style` = Transparent | Filled | Alert | Warning · **Content:** `Text#236:1`
- **When:** inline message that persists in the page (≠ transient toaster) · Use mainly `Filled` · `Alert` = error/critical · `Warning` = caution · `Filled`/`Transparent` = neutral info.
- **Pose:** `setProperties({ Style:"Transparent" })`

### `[New] Toaster` — set · `1f811c5c0a888b40287d8775d42c901a9eba68f2`
- **When:** transient bottom-right (24px margin left and bottom) feedback after an action (save succeeded…) · auto-dismisses · never for info that must stay visible (→ Information message).

### Navigation
- `Top nav bar` — component · `10012a780047d4cfb289f0c388cb1ea16dea6112` · prop `Page Title#7028:0` · embeds `Tab Bar` + chips + breadcrumb chevrons. Top of every app screen.
- `Header nav bar` — component · `d0569e659a4d55ea9ae0f533b59dbdb75829c1ee`.
- `Tab Bar` — component · `2133c9f142324f7369e5f1458398c269d67d73e3` · items `.tab bar - item` (`b9cb6e…`). ⚠️ Navigate between sections of one page.
- `Heading navigation` — set · `12d978d80a1d2b0019f49be3eb7dff516994bdaf`.

### `lightbox` — component · `84357d26143503e9727d3a8cc70a1e06a3591d17`
- **Props:** `main container#8553:0` (SLOT) · pair with `Lightbox heading bar` (`d6ab68a7c08ed93c636deee4e550f7cec53f4108`).
- **Already contains:** `Lightbox heading bar`, `icon-button` (close), `[NEW] Button`.
- **When:** full-page modal. Can also act as a standalone page. Does **not** use the standard navigation chrome — it carries its **own fixed header**. Use it when a task needs the whole viewport but stays outside the normal nav structure.

### `block` — component · `761dcb078e419340fd4244dbf454a72617efeb0d`
- **Props:** `Content#8553:1` (SLOT). Child of the **Card** family (`🧩 Card` page).
- **When:** the base content container — essentially a card. **One block per topic/theme.** E.g. a drawer offering duration / address / user options is composed of 3 blocks (Durée / Adresse / Utilisateur).
- **Spacing:** vertical gap **16px** (`spacing/4`) between blocks and inside a block.

### `Stacked-List` — skeleton, not a single component
- **Skeleton:** there is no published `Stacked-List` container — assemble it by hand: stack several `Stacked-list-item` (`2c25b663123bdc711521c0cdd3b192675e302067`) in an auto-layout frame, spaced **8px** (`spacing/2`) apart. Same approach as the table system.
- **When:** display lists of elements — e.g. attachments / files, emission factors. For emission factors there is a dedicated component in the **FE — Facteur d'émission** library (file `rEhc4mC1R1u3oQ4WFSglkz`, node `641-198`) — use that instead of a plain item.

### `action-rail` — set · `3664bbd45a9d9a952868ac1d2d9315c82659cffe`
- **Variants:** `Style` = Outlined | Transparent (def. Outlined). Built from `icon-button` instances in an inline row.
- **When:** inline row of icon-buttons shown **only on hover** of an element — mainly a table row (at the right-hand 8px margin), also a `Stacked-list-item`. For quick actions (edit, duplicate, delete…). Use the `three-dots-vertical` icon to open a dropdown `Menu` with more options.


## Recommended workflow for `use_figma`

1. **Resolve the component** — `search_design_system(fileKey, query, includeLibraryKeys: [<active key>])` with a 1-word query. Confirm `libraryName === "Aktio - Design System (C14)"`.
2. **Import** — `const set = await figma.importComponentSetByKeyAsync(key)` (or `importComponentByKeyAsync`). For sets, `set.defaultVariant` or find the variant via `componentPropertyDefinitions`.
3. **Instantiate** — `const inst = component.createInstance()`; set variant props with `inst.setProperties({...})`.
   To discover a component's real props (when it's not in the guides above), read them rather than guess:
   ```js
   const node = await figma.getNodeByIdAsync(setId);
   node.componentPropertyDefinitions; // { "Style": {type:"VARIANT", variantOptions:[...]}, "Label#…": {type:"TEXT"}, ... }
   ```
   (`get_context_for_code_connect` requires a Figma Developer seat and is unavailable here — use `componentPropertyDefinitions` instead.)
4. **Bind tokens, don't hardcode** — load variables by collection and bind:
   ```js
   const vars = await figma.variables.getLocalVariablesAsync();
   const purple500 = vars.find(v => v.name === "purple/500");
   node.setBoundVariable("fills", purple500); // or setRangeBoundVariableForPaint
   ```
   Same approach for `itemSpacing`/`padding…` (spacing tokens), `cornerRadius` (rounded tokens), and effects.
5. **Auto-layout** — set `layoutMode`, and use `layoutSizingHorizontal/Vertical` = `"FILL"` / `"HUG"` / `"FIXED"` rather than manual width math. Use spacing tokens for `itemSpacing` and padding.
6. **Type** — load fonts before setting text: `await figma.loadFontAsync({family:"Inter", style:"Semi Bold"})`. Map sizes/line-heights to the typography tokens above.

## Common pitfalls (carried over from prior sessions)

- **Recursive traversal:** to restyle nested instance content, walk `findAllWithCriteria` / recurse `children`; overrides on instance descendants need the descendant node, not the instance root.
- **Component instance styling:** exposed nested props appear in the instance's `componentProperties`; deeper overrides require reaching the child node directly (instances allow per-node fill/text overrides but not structural changes).
- **Layout sizing:** `layoutSizingHorizontal = "FILL"` only works when the parent has `layoutMode` set; otherwise it silently no-ops — set the parent's auto-layout first.
