Spritify.com
============
Issue tracker and tutorial for [Spritify](http://spritify.com).  
Spritify is a tool for the procedural generation of 2D pixel art.  
It transforms input images consisting of conditional pixels into many distinct output images with varying properties, such as gradient, noise and color.  

Input:  

![Input](/images/input.png?raw=true "Input")  

Possible output:

![Output](/images/output.png?raw=true "Output")  

Bugs / Ideas
------------

Please use the issue tracker here to report bugs or request features.  
I'd love to hear your feedback, so don't be shy :)

Guide
-----
Written for version 1.9.0 of `Spritify`.

### Brushes / input pixels
[Spritify](http://spritify.com) offers several pixels for the creation of input images.  
There's two categories of brushes or input pixels. `Solid` or `final` pixels, and `changing` or `evolving` pixels.  

![Brushes](/images/brushes.png?raw=true "Brushes")  

#### Solid pixels (Empty, Border, Body)
These pixels don't change during the procedural generation.  

##### Empty
This pixel does nothing and will later turn into the given background color.

##### Border
This pixel will later have the defined border color.

##### Body
This pixel will later vary in color, shading and noise level.

##### Solid pixels example
![Solid Input](/images/solidinput.png?raw=true "Solid Input")  
(black: `Border`, red: `Body`)  

![Solid Output](/images/solidoutput.png?raw=true "Solid Output")  
(`Border` pixels are all solid black, while `Body` pixels vary)  

#### Changing pixels

##### By Chance (A | B)
These are pixels which have the same chance of becoming an A or B pixel.  
`Boder|Empty` has a 50/50 chance to either become a `Border` or `Empty` pixel.   

![Or Input](/images/orinput.png?raw=true "Or Input")  
(green: `Border|Empty`, cyan: `Body|Empty`, blue: `Border|Body`, magenta: `Border|Body|Empty`)  

![Or Output](/images/oroutput.png?raw=true "Or Output")  
The first column's pixels either become background or the solid border color.  
Pixels within the second column became either the varying color or background.  


##### Conditional (if neighbour)
These pixels are only non-`Empty` if they have a neighbouring pixel.  
 `Border|Empty if neighbour` will be `Empty` if it has no neighbour, otherwise there's a 50% each for it becoming `Border` or `Empty`. These pixels can be used to toggle entire groups or have growing structures.  

![Conditional Input](/images/conditionalinput.png?raw=true "Conditional Input")  
(first row: many `Border|Empty if neighbour` next to `Body|Empty`, second row: many `Border if neighbour`, third row: solid `Body`)

![Conditional Output](/images/conditionaloutput.png?raw=true "Conditional Output")  
Note how the first row which could also produce `Empty` varies in length, while the second row is either fully presend or not.  

##### Walkers  
These pixels leave trails while moving randomly. They either stop if hitting another pixel or by chance.  

![Walker Input](/images/walkerinput.png?raw=true "Walker Input")  
(A `Body walker` within a `Body` box)  

![Walker Output](/images/walkeroutput.png?raw=true "Walker Output")  
(The walker generated a random path)

##### Fillers  
Filler pixels behave similary to walker pixels. Instead of walking or spreading into one direction, they spread radially. They stop at other pixels or after a random number of iterations.  

![Filler Input](/images/fillerinput.png?raw=true "Filler Input")  
(A `Border filler` close to `Body` pixels)  

![Filler Output](/images/filleroutput.png?raw=true "Filler Output")  
(The empty space has been filled randomly with `Border` pixels)


### Controls  
![Controls](/images/controls.png?raw=true "Controls")  

The controls are grouped within a panel.  
- `<-` `->` Undo/Redo
- `++` `--` Zoom In/Out
- `+` `-` Add or remove columns and rows
- `v` `^` Import/Export  
- `Clear` the drawing area  

#### Flags  

##### Mirror right/down
Mirror the input to create symmetrical shapes.  

![Mirroring off](/images/mirroroff.png?raw=true "Mirroring off")  
(Mirroring disabled)  

![Mirroring right](/images/mirrorright.png?raw=true "Mirroring right")  
(`Mirror right` checked)

##### Border on edges
On the final image all edge pixels will be turned into border pixels.  

![Border on edges off](/images/borderonedgesoff.png?raw=true "Border on edges off")  
(Border on edges off)  

![Border on edges on](/images/borderonedgeson.png?raw=true "Border on edges on")  
(Border on edges on)

##### Remove lonely
Removes as final step all pixels which don't have any neighbours.

#### Sprite size
`Sprite x` and `Sprite y` define how many images are within the output sprite.  

#### Shading  
The shading settings add a brightness gradient with the provided strength and direction.

#### Noise
The `Noise` value defines how noisy the `Body` pixels of the output will be.  

![Noise off](/images/noiseoff.png?raw=true "Noise off")  
(`Noise` set to 0)  

![Noise on](/images/noiseon.png?raw=true "Noise on")  
(`Noise` set to 0.85)  

#### Scaling factor  
This factor scales the entire image once the smart pixel logic is done.  

![Scaling factor of 1](/images/scaling1.png?raw=true "Scaling factor of 1")  
(`Scaling factor` set to 1)  

![Scaling factor of 4](/images/scaling4.png?raw=true "Scaling factor of 4")  
(`Scaling factor` set to 4)  

#### Colors
The colors of `Empty` or `Border` pixels can be set here.  

#### Image as color source  
As default `Body` pixels will be assigned any random color. If a color source is set, its pixels will be used to define the `Body` pixels' color.  

![Color source off](/images/colorsourceoff.png?raw=true "Color source off")  
(No color source set, the colors are chosen at random)  

![Color source on](/images/colorsourceon.png?raw=true "Color source on")  
(Image of flames used as color source)
