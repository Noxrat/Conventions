## Class code structure
- **Instance** classes may not contain static information.
Instance class must contain a few mandatory regions in this order:
```csharp
class <SomeType>{
// This region contain all instance variables.
#region Data
public int someVariable1;
public string someVariable2;

private int _someVariable3;
private string _someVariable4;
#endregion

// This region will contain all non-static constructors of the class
#region Constructors
public <SomeType>(int var1, int var2, string var3){
someVariabl1 = var1;
_someVariable3 = var2;
_someVariable4 = var3;
Method0();
_Method1();
}
#endregion

// This region has methods of the class
#region Methods
public void Method0(){}
private void _Method1(){}
#endregion
}
```

- **Singleton** classes's instance methods and variables must be public and may contain public/private static methods and fields.
Singleton class is for Unity-only Managers and has the following structure:
```csharp
class _<SomeType> : UnitySingleton {
// Override to get casted instance
public override _<SomeType> instance { get => (_<SomeType>) _instance; }

// This region contain all instance variables.
#region Data
public int someVariable1;
public string someVariable2;

// public static fields are discouraged
#endregion

// This region has static methods of the class
#region Static Methods
public static void Method0(){}
//private static methods are descouraged
#endregion

// This region has instance methods of the class
#region Methods
public void Method3(){}
// if Awake() method is required
void Awake(){
  base.Awake();
  // code here ...
}
#endregion
}
```
- **Static** classes's structure:
```csharp
static class <SOME_TYPE> {

// This region contain all instance variables.
#region Data
public static int someVar1;
public static int someVar2;

private static int _someVar3;
private static int _someVar4;
#endregion

// This region has static methods of the class
#region Static Methods
public static void Method0(){}

public static void _Method1(){}
#endregion
}
```
