# Discrete Event Simulation using Kotlin coroutines

A discrete event simulation implemented as a kotlin custom event loop.
Unfortunately, not all APIs required to pull it off are stable:
 - the [EventLoop][event-loop] API is private, which prevents hooking into [runBlocking][runBlocking].
   `runSimulation` is an equivalent of `runBlocking`, reconstructed using the public API.
 - the [Delay][delay-api] API is required to properly hook into the [delay function][delay-func]. 
   This API is public, but marked as internal, which requires `@OptIn(InternalCoroutinesApi::class)`.

[event-loop]: https://github.com/Kotlin/kotlinx.coroutines/blob/master/kotlinx-coroutines-core/common/src/EventLoop.common.kt
[runBlocking]: https://github.com/Kotlin/kotlinx.coroutines/blob/master/kotlinx-coroutines-core/jvm/src/Builders.kt#L53
[delay-api]: https://github.com/Kotlin/kotlinx.coroutines/blob/master/kotlinx-coroutines-core/common/src/Delay.kt
[delay-func]: https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines/delay.html