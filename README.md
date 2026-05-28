```
 ██████╗  ██████╗ ████████╗███████╗██╗██╗     ███████╗███████╗
 ██╔══██╗██╔═══██╗╚══██╔══╝██╔════╝██║██║     ██╔════╝██╔════╝
 ██║  ██║██║   ██║   ██║   █████╗  ██║██║     █████╗  ███████╗
 ██║  ██║██║   ██║   ██║   ██╔══╝  ██║██║     ██╔══╝  ╚════██║
 ██████╔╝╚██████╔╝   ██║   ██║     ██║███████╗███████╗███████║
 ╚═════╝  ╚═════╝    ╚═╝   ╚═╝     ╚═╝╚══════╝╚══════╝╚══════╝
```
## ScreenShot
<img width="1920" height="1080" alt="20260528_17h51m40s_grim" src="https://github.com/user-attachments/assets/07605d51-34ba-4f99-b4a2-c71048fbe261" />

<img width="1920" height="1080" alt="20260528_17h53m37s_grim" src="https://github.com/user-attachments/assets/716ec979-5780-4ded-8429-f9e6ce21b41a" />
<img width="1920" height="1080" alt="20260528_17h53m43s_grim" src="https://github.com/user-attachments/assets/b0908b02-2e0c-46ea-94b2-2aee89fb5b21" />

<img width="1920" height="1080" alt="20260528_17h52m07s_grim" src="https://github.com/user-attachments/assets/82b2688b-1bcf-4041-82d2-f8c554209182" />

---

## What Software I use

---

- **OS** : Linux / Arch-based setup
- **WM/Compositor** : [Sway](https://github.com/swaywm/sway) / SwayFX-ready config
- **Bar** : [Waybar](https://github.com/Alexays/Waybar)
- **Application Launcher** : [Wofi](https://hg.sr.ht/~scoopta/wofi)
- **Terminal** : [Alacritty](https://github.com/alacritty/alacritty)
- **File Manager** : [Ranger](https://github.com/ranger/ranger)
- **Text Editor / IDE** : [VSCodium](https://vscodium.com/)
- **Browser** : [Firefox](https://www.mozilla.org/firefox/)
- **Notification daemon** : [Mako](https://github.com/emersion/mako)
- **Wallpaper Utility** : [swaybg](https://github.com/swaywm/swaybg)
- **Screenshot** : [Grim](https://sr.ht/~emersion/grim/) + [Slurp](https://github.com/emersion/slurp)
- **Password Manager** : [KeePassXC](https://keepassxc.org/)
- **Power Management** : [TLP](https://linrunner.de/tlp/)
- **Battery/Power alerts** : poweralertd
- **Audio** : PipeWire / PulseAudio tools via `pactl`
- **Brightness** : brightnessctl
- **Keyboard Layouts** : `us`, `ru`
- **Font** : Terminus 10

#### Main shortcuts

| Shortcut | Action |
|---|---|
| `Mod + Enter` | Open terminal |
| `Mod + d` | Open Wofi app launcher |
| `Mod + Shift + q` | Kill focused window |
| `Mod + Shift + c` | Reload Sway config |
| `Mod + Shift + e` | Exit Sway session with confirmation |
| `Mod + Shift + f` | Open Firefox |
| `Mod + c` | Open VSCodium |
| `Mod + Shift + p` | Open KeePassXC |
| `Mod + Shift + s` | Select area screenshot with Grim + Slurp |
| `Mod + Shift + x` | Open custom Wofi power menu |
| `Print` | Take screenshot with Grim |
| `Mod + r` | Enter resize mode |
| `Mod + Shift + -` | Move focused window to scratchpad |
| `Mod + -` | Show scratchpad |

`Mod` is set to `Mod4`, usually the Super/Windows key.

#### Movement

The config uses Vim-style movement keys:

```bash
set $left h
set $down j
set $up k
set $right l
```

So window focus can be moved with:

```bash
Mod + h/j/k/l
```

Focused windows can be moved with:

```bash
Mod + Shift + h/j/k/l
```

Arrow key alternatives are also enabled.

## Monitor layout

---

This setup is configured for three displays:

| Output | Scale | Transform | Position | Notes |
|---|---:|---|---|---|
| `eDP-1` | `1` | normal | `3360,2576` | Laptop display |
| `DP-5` | `0.9` | normal | `1920,0` | Main external display |
| `DP-3` | `0.8` | `90` | `0,2360` | Rotated display |

The wallpaper is set from:

```bash
~/.config/sway/pexels-mati-12763699.jpg
```

#### Clamshell mode

Laptop lid handling is enabled:

```bash
set $laptop eDP-1
bindswitch lid:on output $laptop disable
bindswitch lid:off output $laptop enable
```

When the lid is closed, `eDP-1` is disabled. When opened, it is enabled again.

## Workspaces

---

Workspaces are pinned to specific outputs:

| Workspaces | Output |
|---|---|
| `1`, `2`, `3` | `DP-5` |
| `4`, `5` | `DP-3` |
| `6`, `7`, `8`, `9`, `10` | `eDP-1` |

#### Application rules

Some applications are automatically assigned to workspaces:

| Workspace | Applications |
|---|---|
| `1` | Alacritty |
| `2` | Firefox |
| `3` | VSCodium / Code |
| `4` | Telegram / Ristretto |
| `5` | AmneziaVPN |

## Appearance

---

The config uses gaps, smart borders and a dark color palette.

```bash
gaps inner 15
gaps outer 15

default_orientation horizontal

default_border pixel 3
default_floating_border pixel 1
hide_edge_borders smart
smart_gaps on
smart_borders on

focus_follows_mouse no
mouse_warping output
```

#### Colors

```bash
client.focused          #555a5a  #202323    #f1f4f4 #747a7a   #555a5a
client.focused_inactive #3d4141  #171919    #a7adad #3d4141   #3d4141
client.unfocused        #2a2d2d  #111313    #747a7a #2a2d2d   #2a2d2d
client.urgent           #f1f4f4  #202323    #ffffff #f1f4f4   #f1f4f4
client.placeholder      #2a2d2d  #111313    #747a7a #2a2d2d   #2a2d2d
```

#### Optional SwayFX effects

SwayFX options are already included, but commented out:

```bash
# blur enable
# blur_passes 3
# blur_radius 4
#
# shadows enable
# shadow_blur_radius 24
# shadow_color #00000099
# shadow_offset 0 8
#
# corner_radius 3
#
# default_dim_inactive 0.15
# dim_inactive_colors.unfocused #00000055
```

Uncomment them if you use SwayFX and want blur, shadows, rounded corners and inactive-window dimming.

## Autostart

---

The following services/apps are started automatically:

```bash
exec_always mako
exec_always tlp start
exec_always swaybg -i ~/.config/sway/pexels-mati-12763699.jpg
exec poweralertd
```

## Installation

---

#### Important packages

```bash
sudo pacman -S --needed sway waybar wofi alacritty ranger firefox vscodium mako swaybg grim slurp brightnessctl tlp poweralertd keepassxc
```

#### Audio

```bash
sudo pacman -S --needed pipewire wireplumber pipewire-pulse pipewire-audio pavucontrol
```

#### Optional SwayFX

If you want to use the commented blur/shadow/corner-radius options, install SwayFX instead of regular Sway:

```bash
sudo pacman -S --needed swayfx
```

#### Useful extras

```bash
sudo pacman -S --needed xdg-desktop-portal-wlr xdg-desktop-portal-gtk polkit-gnome networkmanager blueman
```

## Symlinks

---

Copy the config to your Sway config directory:

```bash
mkdir -p ~/.config/sway
cp config ~/.config/sway/config
```

Or symlink it from your dotfiles repository:

```bash
ln -sf /path/to/dotfiles/sway/config ~/.config/sway/config
```

The wallpaper path expected by the config is:

```bash
~/.config/sway/pexels-mati-12763699.jpg
```

Make sure the image exists there, or edit the path in the config.

## Keyboard layout

---

The config enables English and Russian layouts:

```bash
input * {
    xkb_layout us,ru
    xkb_options grp:win_space_toggle
}
```

Layout switching is done with:

```bash
Super + Space
```

## Notes

---

This is a Sway config focused on a multi-monitor Wayland workflow with:

- three-display layout;
- clamshell mode for laptop usage;
- Vim-style navigation;
- Waybar status bar;
- Wofi launcher and power menu;
- Alacritty terminal workflow;
- Firefox, VSCodium and KeePassXC shortcuts;
- predefined workspace-to-output and app-to-workspace rules;
- optional SwayFX visual effects.

Feel free to copy, modify and mix it with your own dotfiles.
