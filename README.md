# The Grand Cookbook of Dreams

A cozy, engine-free 3D adventure platformer that runs entirely in the browser — four sweet
realms, four stolen recipe pages, and one spun-sugar guide named Pip.

A mischievous gust has torn four pages from the Grand Cookbook of Dreams and every realm has
gone delightfully haywire. Travel from the **Breakfast Uplands** to the **Confectionery
Coast**, through the **Midnight Patisserie**, and up to the **Cloud-Nine Confection** to bind
the pages home and uncover the master recipe: the Dreamcake of Eternity.

Everything is generated at runtime: geometry, textures, music and sound effects. There are no
downloaded art or audio assets — just Three.js, TypeScript and a lot of sugar.

## Play

```bash
npm install
npm run dev
```

Then open http://localhost:5173/ and press **Begin the adventure**. Finished realms stay
unlocked on the title screen, with best times remembered per realm.

Production build:

```bash
npm run build     # typechecks, then bundles to dist/
npm run preview   # serves the built game locally
```

The `dist/` folder is fully static and can be dropped on any web host.

## The four realms

| Chapter | Realm               | Recipe                    | Trial                                            | Page teaches |
| ------- | ------------------- | ------------------------- | ------------------------------------------------ | ------------ |
| One     | Breakfast Uplands   | Fluffy Pancake Recipe     | Waffle trail, butter barge, toast cliffs         | Bounce-Jump  |
| Two     | Confectionery Coast | Neapolitan Sundae Recipe  | Repair 3 heat valves to melt the jawbreaker reef | Ice-Skate Dash |
| Three   | Midnight Patisserie | Midnight Truffle Recipe   | 3 sugar-crystal keys rewind the great clock      | Shadow-Step  |
| Four    | Cloud-Nine Confection | Dreamcake of Eternity   | Bind 3 pages, ride the rainbow ascent            | The master recipe |

Abilities carry forward: marshmallow pads fling you high, `Q` skates you over wide gaps, and
`E` turns you into a whisper of sugar for a heartbeat — the only way through the shadow veils
of the final ascent. Mandatory jumps never require them; clever play is always rewarded.

## Controls

| Action            | Keyboard             | Touch                     |
| ----------------- | -------------------- | ------------------------- |
| Move              | `WASD` / arrows      | left joystick             |
| Jump / double     | `Space` (×2)         | jump button (×2)          |
| Glide / float     | hold `Space` falling | hold jump button          |
| Sprint            | `Shift`              | —                         |
| Ice-Skate Dash    | `Q` (Chapter Two+)   | dash button               |
| Shadow-Step       | `E` (Chapter Three+) | phase button              |
| Look              | drag with mouse      | drag anywhere             |
| Zoom              | mouse wheel          | —                         |
| Pip's hint        | `H`                  | hint button               |
| Pause             | `Esc` / `P`          | pause button              |
| Mute              | `M`                  | sound button              |

## The adventure

1. Follow Pip's cinnamon sense — the page radar always points toward the next wonder.
2. Cupcake checkpoints remember your progress and refill your gingerbread grit (3 hearts).
3. Falls cost one heart. Lose all three and the run ends — retry the realm from its start or return to the title. Pages already saved stay safe in the cookbook.
4. Collect the page of each realm, watch the land restore itself, and beat your best time
   (stored locally, per realm).

Every realm has its own weather — lemonade rain, floating sugar gusts, warm caramel drizzle
and aurora glitter. Sugar gusts are more than pretty: hold `Space` and you'll float on them.

## Tech

- **Three.js** for rendering: custom toon-ish pastel lighting, PMREM environment, soft
  shadows, subtle bloom (EffectComposer) and a procedural shader sky.
- **Custom AABB platformer physics** (`src/physics/PhysicsWorld.ts`) with moving platforms,
  coyote time, jump buffering, double jump, glide, dash, phase-through veils and forgiving
  camera collision.
- **Procedural everything else**: canvas-drawn waffle/pancake/toast/lollipop/gelato textures,
  particle weather, and a tiny Web Audio synthesizer for the score and sound effects.
- **DOM/CSS HUD** layered over the canvas: cookbook progress (x/4), page radar, gingerbread
  health, chapter cards, Pip's dialogue, realm select, pause, failure and recipe-page results screens.
- **Save data v2**: per-realm best times, completion flags and gentle v1 migration.

## Source map

```
src/
  game/       Game loop, UI, story beats, input, audio, save data
  levels/     Level definitions (one per realm) and the shared level kit
  world/      Level manager, landmarks, candy props, materials, textures, sky, syrup, weather
  player/     Player model/controller, camera rig, Pip companion
  physics/    Collision world and moving platforms
  utils/      Small math helpers
```
