# EventDispatcher API

## `EventDispatcher` Class

This class is a singleton that manages event subscription, unsubscription, and dispatching.

### Methods

- `Subscribe(string eventType, string eventName, Action handler)`: Subscribes a handler to an event.
- `Unsubscribe(string eventType, string eventName, Action handler)`: Unsubscribes a handler from an event.
- `Dispatch(string eventType, string eventName)`: Dispatches an event.
- `Subscribe<T>(string eventType, string eventName, Action<T> handler)`: Subscribes a handler to an event with a parameter.
- `Unsubscribe<T>(string eventType, string eventName, Action<T> handler)`: Unsubscribes a handler from an event with a parameter.
- `Dispatch<T>(string eventType, string eventName, T eventParam)`: Dispatches an event with a parameter.
- `Subscribe(string eventType, string eventName, Action<object[]> handler)`: Subscribes a handler to an event with multiple parameters.
- `Unsubscribe(string eventType, string eventName, Action<object[]> handler)`: Unsubscribes a handler from an event with multiple parameters.
- `Dispatch(string eventType, string eventName, params object[] eventParams)`: Dispatches an event with multiple parameters.
- `Subscribe<T, TResult>(string eventType, string eventName, Func<T, TResult> handler)`: Subscribes a handler to an event that returns a value.
- `Unsubscribe<T, TResult>(string eventType, string eventName, Func<T, TResult> handler)`: Unsubscribes a handler from an event that returns a value.
- `Dispatch<T, TResult>(string eventType, string eventName, T eventParam)`: Dispatches an event that returns a value.
- `Subscribe<TResult>(string eventType, string eventName, Func<object[], TResult> handler)`: Subscribes a handler to an event that returns a value with multiple parameters.
- `Unsubscribe<TResult>(string eventType, string eventName, Func<object[], TResult> handler)`: Unsubscribes a handler from an event that returns a value with multiple parameters.
- `Dispatch<TResult>(string eventType, string eventName, params object[] eventParams)`: Dispatches an event that returns a value with multiple parameters.
- `Subscribe<TResult>(string eventType, string eventName, Func<TResult> handler)`: Subscribes a handler to an event that returns a value without parameter passing.
- `Unsubscribe<TResult>(string eventType, string eventName, Func<TResult> handler)`: Unsubscribes a handler from an event that returns a value without parameter passing.
- `Dispatch<TResult>(string eventType, string eventName)`: Dispatches an event that returns a value without parameter passing.

### Specially

Please use a `ConstLib` (in this project is `EventTypeAndNameLib`) Manage all string variables.

### Example

#### In accordance with the project standards.

```C#
using Const;
using Services.EventDispatcherService;

// Subscribe
EventDispatcher.Instance.Subscribe(EventTypeAndNameLib.GameFlowEvents, 
    EventTypeAndNameLib.OnGameStart, () => {});

// Dispatch
EventDispatcher.Instance.Dispatch(EventTypeAndNameLib.GameFlowEvents, 
    EventTypeAndNameLib.OnGameStart);

// Unsubscribe
EventDispatcher.Instance.Unsubscribe(EventTypeAndNameLib.
    GameFlowEvents, EventTypeAndNameLib.OnGameStart, () => {});
```

#### General usage

```C#
// Create an instance of the EventDispatcher
EventDispatcher eventDispatcher = EventDispatcher.Instance;

// Define some handlers
Action myAction = () => Console.WriteLine("Event triggered!");
Action<string> myActionWithParam = (param) => 
    Console.WriteLine($"Event triggered with parameter: {param}");
Action<object[]> myActionWithMultipleParams = (params) => 
    Console.WriteLine($"Event triggered with multiple parameters: " + 
    "{string.Join(", ", params)}");
Func<int, string> myFunc = (param) => 
    $"Event triggered with parameter: {param}, and returned a value!";

// Subscribe to some events
eventDispatcher.Subscribe("MyEvent", "OnTrigger", myAction);
eventDispatcher.Subscribe("MyEventWithParam", 
    "OnTrigger", myActionWithParam);
eventDispatcher.Subscribe("MyEventWithMultipleParams", 
    "OnTrigger", myActionWithMultipleParams);
eventDispatcher.Subscribe<int, string>("MyFuncEvent", 
    "OnTrigger", myFunc);

// Dispatch some events
eventDispatcher.Dispatch("MyEvent", "OnTrigger");
eventDispatcher.Dispatch("MyEventWithParam", 
    "OnTrigger", "Hello, world!");
eventDispatcher.Dispatch("MyEventWithMultipleParams", 
    "OnTrigger", new object[] { "Hello,", "world!" });
string result = eventDispatcher.Dispatch<int, string>("MyFuncEvent", 
    "OnTrigger", 123);

// Unsubscribe from some events
eventDispatcher.Unsubscribe("MyEvent", "OnTrigger", myAction);
eventDispatcher.Unsubscribe("MyEventWithParam", 
    "OnTrigger", myActionWithParam);
eventDispatcher.Unsubscribe("MyEventWithMultipleParams", 
    "OnTrigger", myActionWithMultipleParams);
eventDispatcher.Unsubscribe<int, string>("MyFuncEvent", 
    "OnTrigger", myFunc);
```

Please note that the `EventDispatcher` class is not fully implemented yet.