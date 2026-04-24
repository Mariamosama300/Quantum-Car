# Quantum-Car
Design decisions explained:

Strategy Pattern — Engine is an abstract base class; GasEngine, ElectricEngine, and HybridEngine are interchangeable strategies injected into Car.

Factory Pattern — CarFactory centralises both car creation and engine replacement, keeping that logic out of Car.

Hybrid cost optimisation — HybridEngine.notify_speed() activates only one sub-engine at a time (Electric below 50, Gas at 50+) and resets the idle one to 0, so they never run simultaneously.

Stop guard — Car.stop() refuses to stop if speed isn't 0 first, as required.
Engine replacement — set_engine() on Car + replace_engine() on the factory allows hot-swapping the engine on any existing car.
