# my-i3-config
cat << 'EOF' > ~/.config/i3/config
set $m Mod4
font pango:monospace 10
exec --no-startup-id dex --autostart --environment i3
exec --no-startup-id xss-lock --transfer-sleep-lock -- i3lock --nofork
exec --no-startup-id nm-applet
set $ri killall -SIGUSR1 i3status
bindsym XF86AudioRaiseVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ +10% && $ri
bindsym XF86AudioLowerVolume exec --no-startup-id pactl set-sink-volume @DEFAULT_SINK@ -10% && $ri
bindsym XF86AudioMute exec --no-startup-id pactl set-sink-mute @DEFAULT_SINK@ toggle && $ri
bindsym XF86AudioMicMute exec --no-startup-id pactl set-source-mute @DEFAULT_SOURCE@ toggle && $ri
floating_modifier $m
tiling_drag modifier titlebar
bindsym $m+Return exec i3-sensible-terminal
bindsym $m+Shift+Q kill
bindsym $m+d exec --no-startup-id dmenu_run
bindsym $m+j focus left
bindsym $m+k focus down
bindsym $m+l focus up
bindsym $m+semicolon focus right
bindsym $m+Left focus left
bindsym $m+Down focus down
bindsym $m+Up focus up
bindsym $m+Right focus right
bindsym $m+Shift+j move left
bindsym $m+Shift+k move down
bindsym $m+Shift+l move up
bindsym $m+Shift+colon move right
bindsym $m+Shift+Left move left
bindsym $m+Shift+Down move down
bindsym $m+Shift+Up move up
bindsym $m+Shift+Right move right
bindsym $m+h split h
bindsym $m+v split v
bindsym $m+f fullscreen toggle
bindsym $m+s layout stacking
bindsym $m+w layout tabbed
bindsym $m+e layout toggle split
bindsym $m+Shift+space floating toggle
bindsym $m+space focus mode_toggle
bindsym $m+a focus parent
set $w1 "1"
set $w2 "2"
set $w3 "3"
set $w4 "4"
set $w5 "5"
set $w6 "6"
set $w7 "7"
set $w8 "8"
set $w9 "9"
set $w0 "10"
bindsym $m+1 workspace number $w1
bindsym $m+2 workspace number $w2
bindsym $m+3 workspace number $w3
bindsym $m+4 workspace number $w4
bindsym $m+5 workspace number $w5
bindsym $m+6 workspace number $w6
bindsym $m+7 workspace number $w7
bindsym $m+8 workspace number $w8
bindsym $m+9 workspace number $w9
bindsym $m+0 workspace number $w0
bindsym $m+Shift+1 move container to workspace number $w1
bindsym $m+Shift+2 move container to workspace number $w2
bindsym $m+Shift+3 move container to workspace number $w3
bindsym $m+Shift+4 move container to workspace number $w4
bindsym $m+Shift+5 move container to workspace number $w5
bindsym $m+Shift+6 move container to workspace number $w6
bindsym $m+Shift+7 move container to workspace number $w7
bindsym $m+Shift+8 move container to workspace number $w8
bindsym $m+Shift+9 move container to workspace number $w9
bindsym $m+Shift+0 move container to workspace number $w0
bindsym $m+Shift+c reload
bindsym $m+Shift+r restart
bindsym $m+Shift+e exec "i3-nagbar -t warning -m 'Exit i3?' -B 'Yes' 'i3-msg exit'"
mode "r" {
        bindsym j resize shrink width 10 px or 10 ppt
        bindsym k resize grow height 10 px or 10 ppt
        bindsym l resize shrink height 10 px or 10 ppt
        bindsym semicolon resize grow width 10 px or 10 ppt
        bindsym Left resize shrink width 10 px or 10 ppt
        bindsym Down resize grow height 10 px or 10 ppt
        bindsym Up resize shrink height 10 px or 10 ppt
        bindsym Right resize grow width 10 px or 10 ppt
        bindsym Return mode "default"
        bindsym Escape mode "default"
        bindsym $m+r mode "default"
}
bindsym $m+r mode "r"
set $bg #101010
set $ia #303030
set $tx #ffffff
set $ac #00ff00
set $ur #bd2c40
default_border pixel 1
default_floating_border pixel 1
gaps inner 0
gaps outer 0
client.focused          $ac $ac $bg $ac $ac
client.focused_inactive $ia $ia $tx $ia $ia
client.unfocused        $ia $bg $tx $ia $ia
client.urgent           $ur $ur $tx $ur $ur
client.placeholder      $ia $ia $tx $ia $ia
client.background       $bg
bar {
        status_command i3status
        position top
        colors {
                background $bg
                statusline $tx
                separator  $ia
                focused_workspace  $ac $ac $bg
                active_workspace   $ia $ia $tx
                inactive_workspace $bg $bg $tx
                urgent_workspace   $ur $ur $tx
                binding_mode       $ur $ur $tx
        }
}
exec_always feh --bg-fill ~/afs/dedsec-firewalls-comic-style-artwork-4wbzbw0t7fm0en4g.png
bindsym $m+Shift+x exec i3lock -i ~/afs/wallpaperflare.com_wallpaper.png
EOF
