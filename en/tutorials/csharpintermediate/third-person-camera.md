# Third person camera

This C# Intermediate tutorial covers the implementation of a third person camera.

## Explanation

Since it reuses a large portion of the [First person camera](first-person-camera.md), it is recommended that you watch that tutorial first.

This tutorial teaches about how to use raycasting to position the camera behind the player. If the player is to close any walls, the camera will be moved closer to the player. Too close to the player? We simply switch to first person mode.

> [!Video https://www.youtube.com/embed/qSFZ4ISFcrE]

## Third person camera
[!code-csharp[firstpersoncamera](../../../../stride/samples/Tutorials/CSharpIntermediate/CSharpIntermediate/CSharpIntermediate.Game/10_ThirdPersonCamera/ThirdPersonCamera.cs)]

## Character movement
[!code-csharp[firstpersoncamera](../../../../stride/samples/Tutorials/CSharpIntermediate/CSharpIntermediate/CSharpIntermediate.Game/10_ThirdPersonCamera/CharacterMovement.cs)]