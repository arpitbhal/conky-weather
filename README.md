conky-weather
=============
# Conky settings #
background no
update_interval 1
double_buffer yes
no_buffers yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
#own_window_argb_value 255
#own_window_colour 2D2D2D

minimum_size 200

# Alignment #
alignment tl
gap_x 50
gap_y 50

border_inner_margin 15
border_outer_margin 0

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftdaniel 0
xftfont daniel bold:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color grey

color1 0099CC
color2 9933CC
color3 669900
color4 FF8800
color5 CC0000
color6 AAAAAA
color7 DDDDDD

TEXT
#Jatni 2290138, bbsr 2294941
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=2294941&u=c" -o ~/.cache/weather.xml}${font daniel:size=15}${color green}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}, ${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}
${font daniel:size=70}${alignr}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}${voffset -35}
${execi 300 cp -f ~/.weathericons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,45 -s 60x60}
${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tr '[a-z]' '[A-Z]'}
${image ~/.weathericons/wind.png -p 0,135 -s 15x15}${goto 35}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${image ~/.weathericons/humidity.png -p 0,155 -s 15x15}${goto 35}${execi 300 grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}%${voffset 15}
${color grey}${goto 18}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1' | tr '[a-z]' '[A-Z]'}${goto 88}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${goto 158}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3' | tr '[a-z]' '[A-Z]'}${goto 228}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4' | tr '[a-z]' '[A-Z]'}${goto 298}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5' | tr '[a-z]' '[A-Z]'}
${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 0,210 -s 30x30}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image ~/.cache/weather-2.png -p 70,210 -s 30x30}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p 140,210 -s 30x30}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 210,210 -s 30x30}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image ~/.cache/weather-5.png -p 280,210 -s 30x30}${voffset 20}
${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${goto 230}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°${goto 300}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°
${goto 20}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°${goto 90}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==2'}°${goto 160}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'}°${goto 230}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4'}°${goto 300}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'}°
