# Auto Service Tycoon

A 3D idle / management portfolio prototype built with Unity 6 and URP. Players operate a car service, expand its facilities and automate work with staff.

[![Auto Service Tycoon gameplay](https://img.youtube.com/vi/9n1WJOhTLrE/hqdefault.jpg)](https://youtu.be/9n1WJOhTLrE)

[Watch the gameplay demo](https://youtu.be/9n1WJOhTLrE)

## Implemented systems

- Vehicle routing, entry queues, parking and service bays.
- Service operations and consumable supplies for the player and staff.
- Economy, facility upgrades, hiring and location progression.
- A second location with vehicle appearance customization.
- Save / continue flow and an in-game debug console.

## Code organization

The project separates domain models from gameplay services and Unity presentation using assembly definitions. Dependencies are composed in entry points with a small custom container.

```text
Presentation ---> Services ---> Domain
Infrastructure -------------> Services, Domain
Bootstrap ------------------> Composition and scene setup
```

Examples to review:

- [Wallet](Assets/_Project/Scripts/Domain/Economy/Wallet.cs): balance changes and affordability checks.
- [Save storage](Assets/_Project/Scripts/Infrastructure/Save/FileSaveStorage.cs): temporary-file writes, replacement and a backup file.
- [Bootstrap](Assets/_Project/Scripts/Bootstrap): dependency registration and scene entry points.
- [EditMode tests](Assets/_Project/Tests/EditMode): domain and service behavior checks.

## Open and explore

1. Open the project with **Unity 6000.3.17f1** and let Unity resolve its packages.
2. Open `Assets/_Project/Scenes/Boot.unity` and enter Play Mode.
3. Start a new game. Use `F1` or the on-screen F1 button to open the debug console.
4. Add money and levels to explore buildings, staff and the second location without waiting for normal progression.
5. Return to the main menu and choose Continue to inspect the save flow.

To run the included tests, open Unity's Test Runner and select EditMode. No passing-test count or coverage percentage is asserted by this README; use the result of a fresh run.

## Scope

This is a portfolio prototype, not a published commercial release. It demonstrates gameplay systems and code organization. Mobile-device performance and allocation figures are not reported here.

The project uses Kenney assets; see the asset folders for included license information.
