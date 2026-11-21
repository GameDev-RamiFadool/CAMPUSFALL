# Project: CAMPUSFALL

Course: Computer Game Development, Ariel University (2-7063810), winter 5787. Student: Rami Fadool.
Course site: https://github.com/gamedev-at-ariel/gamedev-5787 · GitHub org: https://github.com/GameDev-RamiFadool · itch.io: https://ramifadool.itch.io

## What we are doing now
HW3 Part B: implement **Level 1 (Tutorial): The Library** as described in `Level_Design.md` (diagram: `images/levels/level1_library.png`).
- Assignment text: `docs/homework_3.pdf`. Milestones: `docs/3-plan.md`.
- Game concept: 2D top-down pixel-art story game. 23:00, gunmen take over Ariel University; a student escapes the library. Puzzles gate progress, shooting in between. The hero rescues, not attacks; the gunmen belong to a fictional group.
- AI use is allowed in this assignment, but Rami must understand and be able to explain every line in class. Explain what you wrote in simple terms after each milestone.

## Stack
- Unity 6000.3.x (check ProjectSettings/ProjectVersion.txt), URP 2D, new Input System only (InputAction). Never use the old Input class.
- Scripts in Assets/Scripts/<System>/, editor tools in Assets/Editor/, prefabs in Assets/Prefabs/, scenes in Assets/Scenes/.
- Placeholder art (solid-colour sprites, primitives) until milestone M8.

## Course code rules (graded)
- Readable, documented code: a short comment above every field and method. No magic numbers: tunable values are `[SerializeField] private` fields.
- Keep game logic in plain C# classes where possible (easy to test); MonoBehaviours stay thin.
- `.github/workflows/linter.yml` runs `dotnet-format --check` on Assets/Scripts. Do not modify it. Keep standard .NET formatting so the check is green.
- README.md is the showcase, in Hebrew inside `<div dir="rtl">`. Don't remove the existing sections (formal elements, market research, level design).

## Working with the editor (Unity CLI)
- Check the connection with `unity status`. If the editor isn't connected, say so and stop. Don't fall back to editing scene files.
- Never hand-edit .unity, .prefab or .asset YAML. Build scenes, GameObjects and prefabs with `unity command eval` / `eval_file`, or a `[CliCommand]` in Assets/Editor/.
- Save scenes after changes (EditorSceneManager.SaveOpenScenes).

## Definition of done for every milestone
1. `unity recompile --strict` passes with no errors or warnings.
2. `unity test` passes (exit 0). Add edit-mode tests for new logic.
3. For gameplay: enter Play mode via eval, check the expected state, report it, exit Play mode.
4. Summarize what changed, explain the code simply, and list what Rami should playtest by hand.

## Rules
- One milestone from docs/3-plan.md at a time. Don't start the next one unasked.
- Don't commit or push until Rami says the milestone is accepted. Before any commit run `git status` and make sure Library/, Temp/, Logs/ and UserSettings/ are not included.
- When a milestone is accepted: tick it in docs/3-plan.md and add a one-line "Notes" entry under it.
