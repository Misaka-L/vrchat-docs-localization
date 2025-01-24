---
upstreamCommit: 4d76fd612a37de18fd85c39062bade59afffb7cf
---

# TooltipManager

The TooltipManager will display text in the world above a given interactable object. Tooltips in ClientSim only display text, unlike VRChat which also displays an icon of the respective button needed to use the interact. In SDK3, it appears that the option to set a tooltip location for an interactable is ignored. Tooltips always display at the top center of the first collider on the interactable object. There is no set limit to the number of tooltips that can be displayed, but only 2 tooltips are expected through ClientSim, one per player hand. Displaying tooltips can be disabled in the [ClientSimSettings](settings.md).