# Sport Quest — local visual assets

Runtime art is served only from this folder. No CDNs, remote fonts, runtime downloads, or backend are required.

## Sources and licenses

All files under `kenney/` are original, unmodified Kenney artwork, licensed CC0. The original license is included in each pack folder.

| Folder | Source | Selected artwork |
|---|---|---|
| `kenney/sports/` | https://kenney.nl/assets/sports-pack | `element (64)` → hoop, `element (69)` → goal net; basketball, soccer ball, green and checkered flags |
| `kenney/boardgame/` | https://kenney.nl/assets/boardgame-pack | `pieceBlue/Red/Green/Purple_multi01` → four pawns |
| `kenney/icons/` | https://kenney.nl/assets/board-game-icons | book_open, pawns, dice_3D, award (клетка «Сюрприз») used in game; arrow_right kept, unused since stage 2; PNG Double (128px) |
| `kenney/particles/` | https://kenney.nl/assets/particle-pack | transparent `star_04` → star.png |

`campus/` contains original Sport Quest SVG supplements: tree, bench, cone, training equipment, trophy and dumbbell. These are not Kenney assets. Terrain, court markings, podium and tile surfaces are original SVG compositions in Board layers.

## Replacing art

The typed runtime manifest is `src/components/board/assets.ts`. Replace a file at the same path, or change the matching manifest entry. Keep transparency and aspect ratios. Pawn PNGs are 64×64; TokenLayer crops their transparent padding with a nested SVG viewBox and applies the team's color and depth shading through an alpha mask. Source PNGs remain unchanged. Update the crop there if replacing the pawn images.

The original downloaded archives and previews are retained for reference under `artifacts/kenney-source/` (ignored by Git and excluded from the production bundle). Only selected files in `public/assets/` are copied to `dist/`.

## Rendering

BoardBackground → TerrainLayer → SportsDecorLayer → PathLayer → CellsLayer → TokenLayer → EffectsLayer.

Decorative animation uses CSS opacity/transform only: one selected-cell pulse, four 1.5px pawn floats and five small finish sparks. `prefers-reduced-motion` disables them. Movement between cells remains the existing motion/react animation and reducer-driven timing.
