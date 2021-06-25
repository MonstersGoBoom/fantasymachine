# fantasymachine
Thoughts and emulator for fantasy 8 bit machine 

# Cells 

Cells are 8x8 pixels in 3 bits per pixel. enabling 8 colors per cell.

# Colors 

Colors are stored as RGB444 like OCS Amiga. 

eg.

  WHITE 0xFFF.
  
  BLUE  0x00F.


# Display 

Featuring a none traditional display. there is no framebuffer nor traditional tilemaps. 

the display is made from moveable objects. these can be thought of as tilemaps with freedom to position anywhere on screen at any size. 

each "object" is made up of 8x8 cells. and can be displayed at any pixel position on screen. 

this is essentially a hybrid between traditional tilemaps and traditional sprites

```
+------+
|ABCDEF|
|GHIJKL|
|MNOPQR|
+------+
```

```
; pixels
  WORD xpos 
  BYTE ypos
; in 8 pixel cells
  BYTE width  
; in 8 pixel cells
  BYTE height
  BYTE flag 
; 16 bit pointer to the 8bit "map" data
  WORD char_data    
; 16 bit pointer to the 8bit "attributes" data ( optional ) 
  WORD attrib_data  
```





