# fantasymachine
Thoughts and emulator for fantasy 8 bit machine 

# Control 

Access | Address | System | Description
--- | --- | --- | ---
R/W | $FFE0 | VIDEO | address of CELL definition data 
R/W | $FFE2 | VIDEO | address of color definition data 
R/W | $FFE4 | VIDEO | address of OBJECT MEMORY 


# CELL 

Cells are 8x8 pixels in 3 bits per pixel. enabling 8 colors per cell.

```
Plane 0 
11111111
00000000
00000000
00000000
00000000
00000000
00000000
00000000
Plane 1 
00000000
11111111
00000000
00000000
00000000
00000000
00000000
00000000
Plane 2 
00000000
00001111
00000000
00000000
00000000
00000000
00000000
00000000
```
combined to 
```
11111111
22226666
00000000
00000000
00000000
00000000
00000000
00000000
```





# Colors 

Colors are stored as RGB444 like OCS Amiga. 

eg.

  WHITE 0xFFF.
  
  BLUE  0x00F.


# Display 

Featuring a none traditional display. there is no framebuffer nor traditional tilemaps. 

The display is made from moveable objects. these can be thought of as tilemaps with freedom to position anywhere on screen at any size. 

Where each "object" is made up of 8x8 cells. and can be displayed at any pixel position on screen. 

This is essentially a hybrid between traditional tilemaps and traditional sprites

Objects can be flipped in the X or Y direction as a global object. Individual CELLS inside an Object can be flipped also via the attribute data.


MAP data
```
+------+
|ABCDEF|
|GHIJKL|
|MNOPQR|
+------+
```

ATTRIBUTE data 

If enabled can control individual CELLS palette of 32 palettes and X or Y Flipped.


OBJECT data
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





