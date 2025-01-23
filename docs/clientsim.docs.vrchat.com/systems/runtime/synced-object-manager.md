---
upstreamCommit: 4d76fd612a37de18fd85c39062bade59afffb7cf
---

# SyncedObjectManager

The SyncedObjectManager keeps track of all initialized synced objects (IClientSimSyncable) in the scene. These synced objects are put into two lists: one list for all synced objects, and another for all position-synced objects. The SyncedObjectManager currently has only two main functions. The first is to check all position-synced objects to verify they are above the respawn height. If they fall below the respawn height, they are respawned to their start position or destroyed, depending on the settings in the [SceneManager](scene-manager.md). The second function is to ensure objects have the correct owners when a player leaves. The manager listens for the OnPlayerLeft [Event](event-dispatcher.md), goes through all objects to check if that player was the  owner, and then sets those objects to be owned by the master player instead. This ownership transfer happens before Udon Programs are notified of the player leaving.


VRC.SDK3.ClientSim.ClientSimSyncedObjectManager