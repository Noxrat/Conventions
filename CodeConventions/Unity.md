## Class code structure
Files above 100 lines have to follow these conventions to provide structured and clean code.<br/>
The 100 line limitation comes from existing codebase to help migrate code to new standard.

<hr/>

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
`Singleton<T>` class usage should be refefered to in [Unity Architecture](https://github.com/Noxrat/Conventions/blob/main/Architecture/Unity.md)


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
