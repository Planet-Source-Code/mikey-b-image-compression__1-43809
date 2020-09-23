<div align="center">

## Image Compression


</div>

### Description

hello peeps! I have an idea but i dont know if it will work (if my maths it wrong) so maybe you can go through it and see if it will work or not. My idea is image compression...
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Mikey B](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/mikey-b.md)
**Level**          |Intermediate
**User Rating**    |4.3 (13 globes from 3 users)
**Compatibility**  |VB 3\.0, VB 4\.0 \(16\-bit\), VB 4\.0 \(32\-bit\), VB 5\.0, VB 6\.0
**Category**       |[Graphics](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics__1-46.md)
**World**          |[Visual Basic](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/visual-basic.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/mikey-b-image-compression__1-43809/archive/master.zip)





### Source Code

Hello, If your new to compression or dont know what it is, heres a quick overview.<br>
Compression is when a file or a length of data is made smaller than the orginal size. The main factor in compression is repeats. the more repeats in a string or file the higher the compression.<br>
Example.<br>
"hello hello hello hello "<br>
this string above is 24 charecters long. And this example can be compressed down to..<br>
"4~hello "<br>
which is 8 charecters long. Compression :) (This compression is RLE (Run Length Encoding) Very basic and isnt that powerful.<br>
I hope your following ok :) (If theres any bad spelling in here sorry, cant spell at all!)<br><br>
So.. the key to compression is repeats, My idea is to take an image. 64 by 64, and run throw the image reading each 8 by 8 block, scanning the picture of blocks that are the same.<br>
is that bad english? hmmm heres what i mean
Step 1) Get the block at X,Y (8by8)<br>
Step 2) Scan throw the image From X,Y to the end of the picture (8by8)<br>
Step 3) Compare the blocks. If the same (or 90% similar) Record its position and the block its the same to.<br>
Step 4) Move X,Y and repeat<br><br>
Better?<br>
Now the maths.... A Pixel is made up of 3 colours (If true colour :P) Red Green Blue (0-255,0-255,0-255) and that is 24bits.<br>
8 by 8 blocks.. at 24bits depth. <br>
so 8x8x24 = 1536bits, Each block that we HAVE to store is 1536bits big. But storing the repeating blocks (The easyest way i can think of, If u think of a better idea email me!) is to use a header.<br>
The header must tell you how many blocks are repeated.. and this could be a very large number depending on the image size. so a 16bit number would be used at the beginning. Then .. each block repeated must have the X,Y<br><br>
X,Y is 4 bits each (64/8 = 8 = 4bits) so in total thats 8bits for a 8x8x24 block..<br><br>
... Now to test it?<br>
A completly blank sheet 64x64, <br>
64/8 = 8<br>
there is 64 blocks in total (8*8). Now coz only 1 block is needed and the rest are repeats.. <br>
1 MASTER BLOCK = 1536bits<br>
1 HEADER = 16bits<br>
63 COPYS = 8bits * 63 = 504bits<br>
The total is 2056bits compressed... instead of(1536*64) 98304bits.<br>
Compression of <br>
2056 / 98304 * 100 ~ 2.0914<br>
100 - 2.0914 = 97.90%!<br>
Now ofcouse this can be changed .. because the more repeats you can get the better compression so mayb change it to compare layers instead of whole pictures (RGB)? and instead of 90%, 95% for better qual? or 50% of better compression. And ofcourse.. the compression will go down when changing the size of the picture (X,Y when saved has to be bigger) but in princable it should (crosses fingers) work... email me if you find a fault with my code or find a better way of doing things. (Vectors mayb?)<br><br> :) xxx Mike xxx

