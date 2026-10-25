# Controller controls

The names below use the Meta Touch layout. OpenXR controller profiles map their corresponding buttons to the same actions; controllers with different layouts may need their runtime's binding editor. These are the Review Version defaults. Weapon transfers, dropping, and item/body grabbing remain experimental and may require the game's native inventory/action flow in some situations.

## During gameplay

| Input | Action |
| --- | --- |
| Left stick | Move relative to the direction you are looking. |
| Left stick click | Toggle sprint. Crouching or beginning a body drag cancels sprint. |
| Right stick | Turn. |
| Right stick click | Open/close the native inventory. |
| Hold right stick click | Recenter the view (about 650 ms). |
| Right trigger | Fire the right-hand firearm or use the held weapon. |
| Left trigger | Fire the left-hand firearm. |
| A | Reload; held firearms use the game's native reload sequence. |
| B tap | Toggle sneak posture. |
| B hold | Crouch (about 450 ms); press B again to clear the posture. |
| X hold | Open actions and health/ammo information beside the left hand. Move the stick to select; release X to perform the selected action. |
| Y tap | Holster/unholster the weapon. |
| Y hold | Drop the weapon (about 650 ms). |
| Grip near an item | Pick up/interact with the item in that hand. Weapon grip uses a toggle: releasing the grip does not immediately drop a picked-up weapon. |
| Hold left grip near a right-held long gun's fore-end | Support the weapon with the second hand. Release to stop supporting it. |
| Hold grip near a draggable body | Start/maintain the native body drag; release to let go. |
| Menu | Open the game's standard pause menu. |

The Meta system button retains its normal runtime function.

## Sniper scopes and binoculars

Bring the **trigger controller** of a sniper rifle close to the headset to enter its native scope view. Lower the weapon to leave the scope; **A** exits and requests a reload. The support grip alone does not determine whether you are looking through the scope.

While using optics, move the **right stick up/down** to change zoom. **B** or **Menu** exits the optics. Binocular viewing follows the headset direction.

Crosshair markers are optional and are separate from the sniper scope. The release has Crosshair disabled by default.

## Actions, map and briefing

Hold **X** to open the action list at your left hand. The health and per-hand magazine/reserve counts appear beside it. **Map** and **Briefing** are at the bottom of the list, after **Cancel**, so they do not replace ordinary nearby interactions.

| Map input | Action |
| --- | --- |
| Left stick | Pan the map. |
| Right stick | Select map buttons. |
| A | Activate the selected button, including Map/floor selection. |
| Right trigger / left trigger | Zoom in / out. |
| Either stick in a floor or legend submenu | Select an entry. |
| B / Menu | Return from a submenu; close the map from its root. |

## Menus and inventory

| Input | Action |
| --- | --- |
| Either stick | Select entries in native menus, including nested load/save screens. |
| A / right trigger | Confirm. |
| B / Menu | Go back through the current submenu. |
| X / Y in native menus | Next / previous tab. |
| Sticks in inventory | Select an item. |
| A / right trigger in inventory | Equip/confirm. |
| B / Menu / right stick click in inventory | Close inventory. |

If the game loses desktop focus, a controller action can focus it. Release that input and press again to perform the action.

Keyboard fallbacks: **F7** recenters the view; **F9** toggles VR output while the game is focused.
