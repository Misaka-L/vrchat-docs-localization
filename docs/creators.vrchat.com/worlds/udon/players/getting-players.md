---
title: "Getting Players"
upstreamCommit: 6f545f4364a91073763e7f0bdf20784e2fb0e94d
---

# Getting Players

These nodes are useful for getting an individual Player, a group of them, or all of them.

### Networking.get LocalPlayer
*VRCPlayerApi*

::: info

Please note that this function is a member of the Networking class, but it is being included here.

:::
The local player is the Player that this Udon script is currently running on-- alternately, the local player is *you*. It's very important to know yourself!

### GetPlayerCount
*int*

Gets the actual number of Players in the instance when it is called.

### GetPlayers
*VRCPlayerApi[]*

This is how you get all the Players in your world so you can go through them in a For Loop and apply settings, make changes, look for a particular name, etc. To use it, you *first need to create a VRCPlayerApi Array*.

![The bare minimum for a working call to GetPlayers. A better approach would be to construct VRCPlayerApi[] as a variable so you can reuse it.](/creators.vrchat.com/images/worlds/graphgetplayers.png)

Above, you can see the bare minimum for a working call to GetPlayers. A better approach would be to construct VRCPlayerApi\[\] as a variable so you can reuse it.

### GetPlayerById
*int*

Get a VRCPlayerApi object for the given player Id if it exists.

### get playerId
*int*

Get the cached PlayerId, calls GetPlayerId if it hasn't been cached yet.

### GetPlayerId
*int*

Gets the Player's Network Id from the source.

## Player Tag System
This system is a quick-and-dirty way of assigning strings to players without creating your own variables and collections.

### SetPlayerTag / GetPlayerTag
Set: *string, string*

Get: *string*

Sets a string variable that you can look up later. For example, you could set the "role" of a player in a cooking game to "chef" or "customer". Then you could GetPlayerTag for "role" and get back either "chef" or "customer".

### ClearPlayerTags
*VRCPlayerApi*

Remove all tags that you've set on a Player.

### GetPlayersWithTag

::: warning

Not currently working. Returns a List, which is unavailable in Udon.

You will be able to pass in an array of VRCPlayerApi objects and a tag and the method will fill the array with Players who have that tag set.

:::