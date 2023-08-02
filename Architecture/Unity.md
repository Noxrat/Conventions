## Unity Architecture
Strongly enforced NOXRAT architecture.

**Object Scope** - an object and any children. 
Example, Object Scope of Child1 is `[Child1, Child1-1]`
```
Scene
- Camera
- Object1
--- Child1
----- Child1-1
--- Child2
```

**Logical Object** - an object containing primary logic (game or UI).
For example, UpgradeCard will have many components (Image, Text, Audio), but only root object will have controlling logic:
```
Canvas
- UpgradeCard (UpgradeButtonLogic.cs, Animator, AudioSource, HorizontalLayout)
--- Icon (Image)
--- Anchor
----- NameText (TMPro)
----- DescriptionText (TMPro)
----- TriviaText (TMPro)
----- Button (Button)
```
This is also true for game objects that are part of game logic.
```
Gameplay (Gamemode, DataManager)
- NeutralPlayer (NPlayer)
--- UnitBasic (NAgent, Animator, Rigidbody2D)
----- Sprite (Collider2D, SpriteRenderer)
----- MainGun (CastPoint)
--- UnitBasic (NAgent, Animator, Rigidbody2D)
----- Sprite (Collider2D, SpriteRenderer)
----- MainGun (CastPoint)
--- UnitBasic (NAgent, Animator, Rigidbody2D)
----- Sprite (Collider2D)
----- MainGun (CastPoint)
----- MoreSprites
------- Sprite1 (Collider2D, SpriteRenderer)
------- Sprite2 (Collider2D, SpriteRenderer)
```

---

### MonoBehaviour
Use MonoBehaviours on prefab basis. Any references in MonoBehaviours should *ONLY* be within the object scope. Any outside references should be resolved by in-code.
Any config: game convars, KVs etc. must be defined through ScriptableObject.

### ScriptableObject
Game config, KVs, convars are stored in ScriptableObjects.

### Managers
Isolated managing classes that manage scopedobjects. For example, a `MenuManager.cs` is not statically exposed manager of menus. If, at some point the manager is required (to switch to some menu through code), *ANOTHER* class `MenuService.cs` will be responsible for exposing menu manager and perform calls to the MenuManager.

### Services
Statically-exposed (Singleton<T>) or purely static class that manages a certain aspect of the game.

### UI Hierarchy
Any scripts in the UI hierarchy must always be attached to the non-visual root `logical object`.
