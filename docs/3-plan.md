# CAMPUSFALL – HW3 Part B milestone plan

Implement **Level 1 (Tutorial): The Library** from `Level_Design.md` as a playable graybox.
Every assignment requirement is covered by at least one milestone (see the table at the end).
Work on one milestone at a time. After each one: verify, report, wait for Rami to playtest and commit.

## M0: Project setup  [ ]
Build: Unity 6000.3.x project (Universal 2D, URP, new Input System) in the repo root. Folders: Assets/Scripts/{Player,Enemies,Puzzles,Managers,UI,Mobile}, Assets/Prefabs, Assets/Scenes, Assets/Sprites, Assets/Editor. Scenes: MainMenu, Library, Win, GameOver (all in Build Settings).
Check: `git status` shows only Assets/, Packages/, ProjectSettings/ and docs. Library/, Temp/, Logs/, UserSettings/ are ignored. `unity recompile --strict` passes.

## M1: Library graybox + player movement  [ ]
Build: library layout from `images/levels/level1_library.png` with placeholder sprites (reading area, lobby with turnstiles, loan desk, staff room, computers, stairs, basement, book stacks with 12 shelf rows, 3 study rooms, emergency exit). Walls, shelves and tables use BoxCollider2D. Player: Rigidbody2D + CircleCollider2D, walk 3 / run 5 / crouch 1.5 units per second via InputAction (WASD + arrows). Camera follows the player.
Check: player cannot walk through walls or shelves (Play-mode eval).
Playtest: does movement feel responsive? Is the library readable?

## M2: Phone pickup, blackout, flashlight  [ ]
Build: phone pickup (trigger, E). On pickup: gunshot sound placeholder, global light dims to near-black. Flashlight = URP Light2D cone on the player, toggled with F. On-screen hint text for each step.
Playtest: is the darkness scary but still playable?

## M3: Generator minigame  [ ]
Build: interact with the generator in the basement opens a UI panel: needle sweeps a bar, green zone 50–75%. Start slow (full sweep 2.5 s). Success: +30% speed, smoke, screen shake. Miss: count and speed reset. 3 successes in a row: lights turn on row by row, staff-room door unlocks.
Check: edit-mode tests for the minigame logic (pure C# class): hit, miss reset, speed increase, win after 3.
Playtest: is it satisfying? too fast / too slow?

## M4: Gunman prefab, patrol, vision, hiding, spawning  [ ]
Build: Gunman prefab (patrol between waypoints, vision cone with range/angle, states Patrol → Suspicious → Alert → Search). Hide spots under computer desks (trigger: player hidden while crouching). G1 is scripted and spawned by a GunmanSpawner when the generator turns on; if G1 sees the player in the tutorial: freeze, "Hide!" message, rewind 3 seconds. G2 patrols the book-stack aisles.
Requirement covered: prefab + spawn.
Check: tests for the state machine; Play-mode eval: G1 spawns after the generator.

## M5: Pistol and combat  [ ]
Build: wounded guard NPC gives the pistol + 12 ammo. Bullet prefab spawned on shoot (left click), Rigidbody2D + collider; hits a gunman (2 hits = down) or a wall (destroyed). G2 shoots back slowly (1 heart per 2.5 s).
Requirement covered: collisions (+ physics).
Check: tests for health and ammo logic.

## M6: Level management: GameManager, checkpoints, Win / Game Over  [ ]
Build: GameManager singleton with DontDestroyOnLoad keeps hearts, ammo, time, deaths and checkpoint. 4 checkpoints. Reaching the emergency exit loads the Win scene; 0 hearts loads the GameOver scene. Both scenes show the stored values (time, ammo left, deaths) and offer Retry / Menu.
Requirement covered: level management with saved variables (Singleton + DontDestroyOnLoad).
Check: tests for GameManager; Play-mode: values survive the scene change.

## M7: Mobile UI  [ ]
Build: on-screen joystick + buttons (shoot, interact, flashlight, crouch) shown only on touch devices. Canvas Scaler (Scale With Screen Size), SafeAreaHandler and CameraAspectController (reuse from HW2). Generator: tap anywhere.
Requirement covered: mobile UI.
Playtest: Device Simulator, portrait and landscape.

## M8: AI-generated sprites  [ ]
Build: replace placeholders for the player, gunman, wounded guard, generator and crates with pixel-art sprites generated with AI, imported into the existing prefabs. Document which tool made them in the README.
Requirement covered: prefabs made from AI-generated models.

## M9: Builds and submission  [ ]
Build: WebGL build → upload to itch.io (test in the phone's browser). Android build (APK) → install on a phone, record a gameplay video. README: how to play, controls, links GitHub ↔ itch.io, video link, answers on what each requirement uses.
Check: linter green check on GitHub.

## Requirement coverage
| HW3 requirement | Milestone |
|---|---|
| Prefab + spawn, incl. AI-generated models | M4, M5, M8 |
| Collisions | M1, M5 |
| Level management + saved values (Singleton / DontDestroyOnLoad) | M6 |
| Mobile UI | M7 |
| WebGL on itch.io + phone browser | M9 |
| Android build + video | M9 |
