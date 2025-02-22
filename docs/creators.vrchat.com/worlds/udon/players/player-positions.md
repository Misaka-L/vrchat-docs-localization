---
title: "Player Positions"
upstreamCommit: 85cb3e281463697dff436fdb034a8d4e1bc29eb3
---

# Player Positions

Here are the nodes relating to Players' positions. For nodes that deal with forces relating to Players, see [Player Forces](/creators.vrchat.com/worlds/udon/players/player-forces). 

### GetPosition

_returns Vector3 in World Space_  
Gets the position of the Player.

### GetRotation

_returns UnityEngine.Quaternion in World Space_  
Gets the rotation of the Player.

### GetBonePosition

_returns Vector3 in World Space_  
Gets the position of the specified Bone in the Player's Avatar, or Vector3.Zero (0,0,0) if the bone does not exist. Note that Avatars may not have all the same bones in the places you expect, so be careful making assumptions about attributes like a player's height, pose etc based on the position of bones.

### GetBoneRotation

_returns Quaternion in World Space_  
Gets the rotation of the specified Bone in the Player's Avatar, or Quaternion.Identity (0,0,0,1) if the bone does not exist. Note that Avatars may not have all the same bones in the places you expect, so be careful making assumptions about attributes like a player's height, pose etc based on the rotation of bones.

### GetTrackingData

_returns TrackingData for the given TrackingDataType: Head, LeftHand, RightHand, Origin, or AvatarRoot_  
Gets a struct called TrackingData, which contains separate Position and Rotation data. This is the suggested way to get position and rotation data for a Player's head and hands. This returns data from the TrackingManager for a Local Player (ie the data coming from their headset / trackers) and from the RightHand, LeftHand and Head bones for a Remote Player. Origin returns the center of the local VR user's playspace, while returning the player's position for local Desktop users and all remote users. AvatarRoot returns data for the root transform of the avatar (the same transform that the player capsule is attached to). For users in Fully-Body Tracking, AvatarRoot will not rotate with the head facing direction. If you need data reflecting the general forward facing direction of a Player, consider using GetRotation instead.

### GetVelocity / SetVelocity

_returns Vector3 in World Space_  
Get and set the speed and direction of the player's movement. If SetVelocity is called on a LocalPlayer, their 'IsGrounded' property is set to false since they are not in direct control of their movements while this is happening.

### IsPlayerGrounded

_returns Boolean_  
Get whether the player is touching the ground, which enables Jump.

### TeleportTo

_takes a Vector3 World Position and Quaternion World Rotation_  
Send a Player to a new spot and specified rotation, unless a Station does not allow it.

::: info Teleporting other players

TeleportTo only works with the [local player](/creators.vrchat.com/worlds/udon/players/getting-players#networkingget-localplayer). You can use [networking](/creators.vrchat.com/worlds/udon/networking/) to cause other players to teleport themselves. 

:::

