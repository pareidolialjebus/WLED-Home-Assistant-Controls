# WLED-Home-Assistant-Controls
Some examples of using Home Assistant to control WLED

This assumes the user has added an MQTT broker and linked this to a WLED install in Home Assistant

Control Pallette

To control the palette from a drop down box, first set up an input_select.  
This is the drop down control you will later add to the home assistant front end.  
Give it a name (I just used WLED Palette).  
You will probably need multiple copies of this if controlling multiple led strips this way.

input_select:

  wled_palette:
  
  name: WLED Palette

    options:
      - "00-Default"
      - "01-Random Cycle"
      - "02-Primary Color"
      - "03-Based on Primary"
      - "04-Set Colors"
      - "05-Based on Set"
      - "06-Party"
      - "07-Cloud"
      - "08-Lava"
      - "09-Ocean"
      - "10-Forest"
      - "11-Rainbow"
      - "12-Rainbow Bands"
      - "13-Sunset"
      - "14-Rivendell"
      - "15-Breeze"
      - "16-Red & Blue"
      - "17-Yellowout"
      - "18-Analogous"
      - "19-Splash"
      - "20-Pastel"
      - "21-Sunset 2"
      - "22-Beech"
      - "23-Vintage"
      - "24-Departure"
      - "25-Landscape"
      - "26-Beach"
      - "27-Sherbet"
      - "28-Hult"
      - "29-Hult 64"
      - "30-Drywet"
      - "31-Jul"
      - "32-Grintage"
      - "33-Rewhi"
      - "34-Tertiary"
      - "35-Fire"
      - "36-Icefire"
      - "37-Cyane"
      - "38-Light Pink"
      - "39-Autumn"
      - "40-Magenta"
      - "41-Magred"
      - "42-Yelmag"
      - "43-Yelblu"
      - "44-Orange & Teal"
      - "45-Tiamat"
      - "46-April Night"
      - "47-Orangery"
      - "48-C9"
      - "49-Sakura"

- id: wled_select345335345
  alias: wled_select
  trigger:
  - entity_id: input_select.wled_palette
    platform: state
  condition: []
  action:
  - data_template:
      topic: "wled/wled1/api"
      payload: 'FP={{ states(''input_select.wled_palette'')[:2] }}'
    service: mqtt.publish
    
