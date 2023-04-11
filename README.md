# Game Variables

An implementation of the Scriptable Variables system described by Ryan Hipple at [Unite 2017 - Game Architecture with Scriptable Objects](https://www.youtube.com/watch?v=raQ3iHhE_Kk).

Game Variables are Scriptable Objects that can be used to communicate values between scenes without tightly coupling. 
Many primitive types are provided by default, and custom types are easily created.

## Using Game Variables

This example will walk through the creation and usage of a Float Game Variable.

### Game Variable Assets

1. Create a Game Variable in the Project window: `Create > Game Variable > Float Variable`
2. The GameVariable's default value can be modified in the inspector. 
   - Note that editing the value from the inspector will overwrite the old value, even in play mode.
   - Modifying the value from a C# script will not persist after play mode is exited.

### Game References

Game References are the best way to refer to Game Variables in C# scripts. They give designers the option between referencing a Game Variable asset, or specifying a constant value directly in the editor.

```csharp
public class Player : MonoBehaviour {
    public FloatRef health;
    // public FloatVar health;  // This can be used instead, but it requires the use of a Game Variable asset.

    private void FixedUpdate() {
        if (health.val < 30) {
            health.val += 1;
        }
    }
}
```

## Custom Game Variable Types

Custom Game Variable types can be generated using the CodeGen tool provided: `Tools > Game Variables > Create New GameVariable Type`

Fill out the wizard fields with your C# namespace, the data type you want to store in the variable, and the Create Menu sorting order (default ordering: 2).