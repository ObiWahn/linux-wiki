# Sway WM

## Tools
- `wdisplays` - arandar fro wayland

## List output positions
```sh
$ swaymsg -t get_outputs | jq -r '.[].rect | "\(.x),\(.y) \(.width)x\(.height)"'
0,0 1280x800
```
### With Names
```sh
$ swaymsg -t get_outputs | jq -r '.[] | {name} + .rect | "\(.x),\(.y) \(.width)x\(.height) \(.name)"'
0,0 1280x800 Virtual-1
```

## Select windows
```sh
$ swaymsg -t get_tree | jq -r \
> '.. | (.nodes? // empty)[] | select(.pid and .visible) | .rect | "\(.x),\(.y) \(.width)x\(.height)"'
1280,47 1280x1553
0,47 1280x764
0,836 1280x764
```
### With Names
```sh
$ swaymsg -t get_tree | jq -r \
> '.. | (.nodes? // empty)[] | select(.pid and .visible) | {name} + .rect
  | "\(.x),\(.y) \(.width)x\(.height) \(.name)"'
```

## Misc (Untested, or for older Sway versions)

### Select whole output
```sg
swaymsg -t get_outputs | jq -r '.[] | select(.active) | .rect | "\(.x),\(.y) \(.width)x\(.height)"' | slurp
```

### Windows from workspace where id = 4
```sh
swaymsg -t get_tree | jq '.. | (.nodes? // empty)[] | select(.type == "workspace" and .id == 4) | (.nodes? // empty)[] | select(.pid) | .rect | "\(.x),\(.y) \(.width)x\(.height)"' | slurp
```

### All windows from all visible workspaces
```sh
swaymsg -t get_tree | jq --argjson visible "$(swaymsg -t get_workspaces | jq -c '[.[] | select(.visible) | .id]')" '.. | (.nodes? // empty)[] | select(.type == "workspace" and .id == $visible[]) | .. | (.nodes? // empty)[] | select(.pid) | .rect | "\(.x),\(.y) \(.width)x\(.height)"' | slurp
```

### Windows *and* outputs
```sh
swaymsg -t get_tree | jq -r 'recurse(.nodes[]?, .floating_nodes[]?) | select(.visible or (.type == "output" and .active)) | .rect | "\(.x),\(.y) \(.width)x\(.height)"'
```
