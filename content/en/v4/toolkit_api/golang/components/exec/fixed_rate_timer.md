---
type: docs
title: "FixedRateTimer"
linkTitle: "FixedRateTimer"
gitUrl: "https://github.com/pip-services4/pip-services4-go/tree/main/pip-services4-components-go"
description: >
    Timer that is triggered in equal time intervals.

---

**Implements:** [IClosable](../iclosable)

### Description

The FixerRateTimer class represents a timer that is triggered in equal time intervals.

Important points

- It has symmetric cross-language implementation and is often used by the Pip.Services toolkit to perform periodic processing and cleanup in microservices.

### Constructors
Creates new instance of the timer and sets its values.

> `public` constructor(taskOrCallback: any = null, interval: number = null, delay: number = null)

- **taskOrCallback**: any - (optional) Notifiable object or callback function to call when timer is triggered.
- **interval**: number - (optional) interval to trigger timer in milliseconds.
- **delay**: number - (optional) delay before the first triggering in milliseconds.

### Instance methods

#### close
Closes the timer.

This is required by the [IClosable](../iclosable) interface,
but besides that it is identical to [stop()](#stop).

> `public` close(context: [IContext](../../context/context)): Promise\<void\>

- **context**: [IContext](../../context/context) - (optional) execution context to trace execution through call chain.

#### getCallback
Gets the callback function that is called when this timer is triggered.

> `public` getCallback(): () => void

- **returns**: function - callback function or null if it is not set. 


#### getDelay
Gets an initial delay before the timer is triggered for the first time.

> `public` getDelay(): number

- **returns**: number - delay in milliseconds.

#### getInterval
Gets a periodic timer triggering interval.

> `public` getInterval(): number

- **returns**: number - interval in milliseconds


#### getTask
Gets the INotifiable object that receives notifications from this timer.

> `public` getTask(): [INotifiable](../inotifiable)

- **returns**: [INotifiable](../inotifiable) - INotifiable object or null if it is not set.


#### setTask
Sets a new INotifiable object to receive notifications from this timer.

> `public` setTask(value: [INotifiable](../inotifiable)): void

- **value**: [INotifiable](../inotifiable) - INotifiable object to be triggered.

#### isStarted
Checks if the timer is started.

> `public` isStarted(): boolean

- **returns**: boolean - true if the timer is started and false if it is stopped.

#### setCallback
Sets the callback function that is called when this timer is triggered.

> `public` setCallback(value: () => void)

- **value**: function - callback function to be called.

#### setDelay
Sets an initial delay before the timer is triggered for the first time.

> `public` setDelay(value: number): void

- **value**: number - delay in milliseconds. 

#### setInterval
Sets a periodic timer triggering interval.

> `public` setInterval(value: number): void

- **value**: number - interval in milliseconds.


#### start
Starts the timer.

Initially. the timer is triggered after delay.
After that, it is triggered after interval until it is stopped.

> `public` start(): void


#### stop
Stops the timer.

> `public` stop(): void

### Examples
```go
type MyComponent {
			timer FixedRateTimer
		}
		...
		func (mc* MyComponent) Open(ctx, context.Context) {
			...
			mc.timer = NewFixedRateTimerFromCallback(func(ctx context.Context){ this.cleanup }, 60000, 0, 5);
			mc.timer.Start(ctx);
			...
		}
		func (mc* MyComponent) Close(ctx, context.Context) {
			...
			mc.timer.Stop(ctx);
			...
		}

```

### See also
- #### [INotifiable](../inotifiable)

