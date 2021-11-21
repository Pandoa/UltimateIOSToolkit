# C++ Setup
This section contains the steps required to start using the plugin with C++. These steps are not needed if you don't plan to use the plugin with C++.

## Linking the Module
To use the plugin using C++, you need to include the `UltimateIOSToolkit` module.  
To do so, open your `Project.Build.cs` file and add the following line in the constructor:
```csharp
PublicDependencyModuleNames.Add("UltimateIOSToolkit");
```

## About Callbacks
In this documentation, lambdas are used for the callbacks. There exists several other ways to bind a method to a callback but here are
the most used ones:
### Lambdas
```cpp
Function(FTheCallback::CreateLambda([](/* Parameters... */) -> void
{
    // Code called when Function fires the callback.
    // You need to explicitly capture everything you want to use here
    // and should not capture any UObject pointers without warping it in
    // a TWeakObjectPtr<> or equivalent.
}));
```
### UObject
```cpp
// A dummy header-only example UObject-based class
UCLASS()
class UMyClass : public UObject
{
    GENERATED_BODY()
public:
    // The callback.
    void MyCallback(/* Parameters... */)
    {
        // Code called when Function fires the Callback.
        // We have access to the `this` pointer.
    }

    // The function launching the asynchronous work.
    void MyOtherFunction()
    {
        // We create a callback bound to the member method.
        // We don't have to take care about dangling pointers due to garbage collection.
        // However, if this object gets garbage collected, the callback won't fire.
        Functions(FTheCallback::CreateUObject(this, &ThisClass::MyCallback));
    }
}
```

!> All C++ callbacks are called on the Game Thread.

