# supreme-winner
VS add-in solution explorer context menu group

`CommandPlacement` usage to have [the same menu item for several different add-in menus](https://stackoverflow.com/a/62384773/940182)

To duplicate the same group with submenu items I removed the parent element from the `grpIdMenuProjectItem` group declaration
```
<Group guid="guidCmdSet" id="grpIdMenuProjectItem" priority="0x0700">
</Group>
```

and have added three command placements for item, project and folder parents
```
<CommandPlacements>
    <CommandPlacement guid="guidCmdSet" id="grpIdMenuProjectItem" priority="0xF00">
			<Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_ITEMNODE" />
    </CommandPlacement>
    <CommandPlacement guid="guidCmdSet" id="grpIdMenuProjectItem" priority="0xF00">
			<Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_PROJNODE" />
    </CommandPlacement>
    <CommandPlacement guid="guidCmdSet" id="grpIdMenuProjectItem" priority="0xF00">
			<Parent guid="guidSHLMainMenu" id="IDM_VS_CTXT_FOLDERNODE" />
    </CommandPlacement>
</CommandPlacements>
```
The `CommandPlacements` node should be added after the `Commands` node [as documented](https://docs.microsoft.com/en-us/visualstudio/extensibility/creating-reusable-groups-of-buttons?view=vs-2019#to-put-a-reusable-group-of-buttons-on-a-menu).
