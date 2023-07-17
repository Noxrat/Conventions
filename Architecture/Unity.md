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

---

### MonoBehaviour
Use MonoBehaviours on prefab basis. Any references in MonoBehaviours should *ONLY* be within the object scope. Any outside references should be resolved by in-code.
Any config: game convars, KVs etc. must be defined through ScriptableObject.

Classes that need to manage children MonoBehaviours are called `ServiceProvider`.

Classes that need a single state are called `ServiceReciever`, and must have a parent that implements `ServiceProvider`.

### ScriptableObject
Game config, KVs, convars are stored in ScriptableObjects.
