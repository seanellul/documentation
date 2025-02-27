---
date: 2020-08-04
title: Move a player
description: Change a player's position inside the scene
categories:
  - development-guide
type: Document
url: /creator/development-guide/sdk7/move-player/
weight: 2
---

To change the player's position in the scene, set the position of the `Transform` component for the `engine.PlayerEntity` entity.

<!-- - `position`: Where to move the player, expressed as an object with _x_, _y_, and _z_ properties.
- `cameraTarget`: (optional) What direction to make the player face, expressed as an object with _x_, _y_, and _z_ properties that represent the coordinates of a point in space to stare at. If no value is provided, the player will maintain the same rotation as before moving. -->

```ts
const playerTransform = Transform.getMutable(engine.PlayerEntity)
playerTransform.position = {x: 1, y: 10, z: 1}
```

The `engine.PlayerEntity` entity may not be available to modify while the scene is being loaded. The example below performs the player's movement after the scene is loaded, each time an entity is clicked.

```ts
// create entity
const myEntity = engine.addEntity()
MeshRenderer.setBox(myEntity)
MeshCollider.setBox(myEntity)

Transform.create(myEntity, {
  position: {x:4, y:1, z:4}
})

// give entity behavior
pointerEventsSystem.onPointerDown(
  entity,
  function () {
     respawnPlayer()
  },
  {
    button: InputAction.IA_POINTER,
    hoverText: 'Click'
  }
)

// function to handle respawn
function respawnPlayer(){
 const playerTransform = Transform.getMutable(engine.PlayerEntity)
	  playerTransform.position = {x: 1, y: 10, z: 1}
}
```



The player's movement occurs instantly, without any confirmation screens or camera transitions.

> Note: Players can only be moved if they already are standing inside the scene's bounds, and can only be moved to locations that are inside the limits of the scene's bounds. You can't use `movePlayerTo()` to transport a player to another scene. To move a player to another scene, see [Teleports]({{< ref "/content/creator/sdk7/interactivity/external-links.md#teleports">}}).

You must first add the `ALLOW_TO_MOVE_PLAYER_INSIDE_SCENE` permission to the `scene.json` file before you can use this feature. If not yet present, create a `requiredPermissions` property at root level in the JSON file to assign it this permission.

```json
"requiredPermissions": [
    "ALLOW_TO_MOVE_PLAYER_INSIDE_SCENE"
  ],
```

See [Required permissions]({{< ref "/content/creator/sdk7/projects/scene-metadata.md#required-permissions">}}) for more details.

> Note: To prevent abusive behavior that might damage a player's experience, the ability to move a player is handled as a permission. Currently, this permission has no effect in how the player experiences the scene. In the future, players who walk into a scene with this permission in the `scene.json` file will be requested to grant the scene the ability to move them.
