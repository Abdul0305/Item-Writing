+++
title = "Crop an Image in C#"
date = 2021-03-16
draft = false
keywords = ["Crop an Image in C#"]
description = "In this tutorial, learn the different methods of drawing and editing an image in C# with examples. Use the Graphics.DrawImage() method."
postlink = 734930
inarticle = true
tags = ["Csharp", "Csharp Array"]
author = "Abdullahi Salawudeen"

+++

This article will introduce how to draw a specified image at the specified location with the original size using the C# code.

## Use the `Graphics.DrawImage()` method to draw an image in C#

`Graphics` can be found in the `System.Drawing` namespace and primarily used to display or draw graphics/image in `.Net-based` Windows Applications. `.Net` provides, multiple classes to deal with graphics objects and shapes such as pen, brush, rectangle, circle, etc.

Graphics and Image .Net classes were used to render an image on a Windows Form.

The `DrawImage()` class draws a portion of an image at a specified location. Below is the code snippet for the `DrawImage` class.

```c#
public void DrawImage (System.Drawing.Image image, float x, float y, System.Drawing.RectangleF srcRect, System.Drawing.GraphicsUnit srcUnit);
```

The parameters are explained below:

 `image` parameter specifies the image to draw.

`x` parameter specifies the x-coordinate of the upper-left corner of the drawn image.

`y` parameter specifies the y-coordinate of the upper-left corner of the drawn image.

`srcRect` parameter is a `RectangleF`structure that specifies the portion of the image to draw.

`srcUnit` parameter is a member of the `GraphicsUnit` enumeration that specifies the units of measure used by the `srcRect` parameter.

The following example of code is designed for use with Windows Forms, and it requires `PaintEventArgs e` which is a parameter of the `Paint` event handler.

The code performs the following actions:

- Creates an image from a JPEG file Koala.jpg in the folder "C:\Users\lolaa\Downloads".
- Creates the coordinates at which to draw the upper-left corner of the image.
- Creates a source rectangle from which to extract a portion of the image.
- Sets the unit of measure of the source rectangle to pixels.
- Draws the image to the screen.

The size of the source rectangle determines what portion of the unscaled original image is drawn to the screen.

```c#
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CreatingImageObject
{
    public partial class Form1 : Form
    {
        Image img = null;
        public Form1()
        {
            InitializeComponent();
        }



        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            if (img == null)
            {
                img = Image.FromFile(@"C:\Users\lolaa\Downloads\Koala.jpg");

            }
           
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            if(img != null)
            {
                //Graphics g = e.Graphics;
                Graphics g = this.CreateGraphics();
                g.DrawImage(img, 0, 0, this.Width, this.Height);

                g.Dispose();

            }

            
        }
    }
}
```

Output:

![image-20220319205035965](C:\Users\lolaa\AppData\Roaming\Typora\typora-user-images\image-20220319205035965.png)



Click on the `button` and the image below is displayed:

![image-20220319205212320](C:\X\Private\Freelance\Item Writing\MS2\image-20220319205212320.png)



Output:

```text
![image-20220319205212320](C:\X\Private\Freelance\Item Writing\MS2\image-20220319205212320.png)
```

```c#

Rectangle cropRect = new Rectangle(...);
Bitmap src = Image.FromFile(fileName) as Bitmap;
Bitmap target = new Bitmap(cropRect.Width, cropRect.Height);

using(Graphics g = Graphics.FromImage(target))
{
   g.DrawImage(src, new Rectangle(0, 0, target.Width, target.Height), 
                    cropRect,                        
                    GraphicsUnit.Pixel);
}
```

### Using the `DrawImage(Image, Single, Single, RectangleF, GraphicsUnit)`with 5 Parameters

Updating the above code would give a different output. Below is the updated code example.

```c#
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CreatingImageObject
{
    public partial class Form1 : Form
    {
        Image img = null;
        public Form1()
        {
            InitializeComponent();
        }



        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            if (img == null)
            {
                // Create image.
                img = Image.FromFile(@"C:\Users\lolaa\Downloads\Koala.jpg");

            }
           
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            if(img != null)
            {
                
                Graphics g = this.CreateGraphics();               

                // Create coordinates for upper-left corner of image.
                float x = 100.0F;
                float y = 100.0F;

                // Create rectangle for source image.
                RectangleF srcRect = new RectangleF(50.0F, 50.0F, 150.0F, 150.0F);
                GraphicsUnit units = GraphicsUnit.Pixel;

                // Draw image to screen.
                g.DrawImage(img, x, y, srcRect, units);
                g.Dispose();

            }


        }
    }
}

```



Output:

![image-20220319222453754](C:\Users\lolaa\AppData\Roaming\Typora\typora-user-images\image-20220319222453754.png)



### Using the `DrawImage(Image, Rectangle, Single, Single, Single, Single, GraphicsUnit, ImageAttributes, Graphics+DrawImageAbort, IntPtr)`to draw a specified portion of the specified image at the specified location and with the specified size.

```c#
public void DrawImage (System.Drawing.Image image, System.Drawing.Rectangle destRect, float srcX, float srcY, float srcWidth, float srcHeight, System.Drawing.GraphicsUnit srcUnit, System.Drawing.Imaging.ImageAttributes? imageAttrs, System.Drawing.Graphics.DrawImageAbort? callback, IntPtr callbackData);
```

Updating the above code would give a different output. Below is the updated code example.

The parameters are explained below:

 `image` parameter specifies the image to draw.

`destRect` parameter is a `Rectangle` structure that specifies the location and size of the drawn image. The image is scaled to fit the rectangle.

`srcX` parameter specifies the x-coordinate of the upper-left corner of the drawn image.

`srcY` parameter specifies the y-coordinate of the upper-left corner of the drawn image.

`srcWidth` parameter specifies the width of the portion of the source image to draw .

`srcHeight` parameter specifies the height of the portion of the source image to draw.

`srcUnit` parameter is a member of the `GraphicsUnit` enumeration that specifies the units of measure used by the `srcRect` parameter.

`imageAttrs` is an `ImageAttributes` instance that specifies recoloring and gamma information for image objects.

`callback` is a `Graphics.DrawImageAbort` delegate that specifies a method to call during the drawing of the image. This method is called frequently to check whether to stop the execution of the `DrawImage(Image, Rectangle, Single, Single, Single, Single, GraphicsUnit, ImageAttributes, Graphics+DrawImageAbort, IntPtr)` method depending on the application specification.

`callbackData` is a value specifying additional data for the `Graphics.DrawImageAbort` delegate to use when checking whether to stop the execution of the `DrawImage` method.



The following example of code is designed for use with Windows Forms, and it requires `PaintEventArgs e` which is a parameter of the `Paint` event handler. The code first defines a `callback` method for the `Graphics.DrawImageAbort` delegate. 

The code performs the following actions:

- Creates an instance of the `Graphics.DrawImageAbort` callback method.
- Creates an image from a JPEG file Koala.jpg in the folder "C:\Users\lolaa\Downloads".
- Creates points that define a destination rectangle in which to draw the image.
- tests to see whether the `DrawImage` method calls it with a null `callBackData` parameter.
- Creates a source rectangle to select the portion of the image to draw.
- Sets the graphics drawing unit to pixel.
- Draws the original image to the screen.
- Creates an additional destination rectangle in which to draw an adjusted image.
- Creates and sets the attributes of the adjusted image to have a larger-than-usual gamma value.
- Draws the adjusted image to the screen.

The `Graphics.DrawImageAbort` callback returns `false` which causes the `DrawImage` method to continue, and the adjusted image is drawn to the screen. The size of the source rectangle determines what portion of the unscaled original image is drawn to the screen.

For the original, unadjusted destination rectangle, the position locates the image on the screen, the size of the source rectangle as well as the size and shape of the destination rectangle determines the scaling of the drawn image.

```c#
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Drawing.Imaging;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CreatingImageObject
{
    public partial class Form1 : Form
    {
        Image img = null;
        public Form1()
        {
            InitializeComponent();
        }



        private void Form1_Load(object sender, EventArgs e)
        {

        }


        // Define DrawImageAbort callback method.
        private bool DrawImageCallback8(IntPtr callBackData)
        {

            // Test for call that passes callBackData parameter.
            if (callBackData == IntPtr.Zero)
            {

                // If no callBackData passed, abort DrawImage method.
                return true;
            }
            else
            {

                // If callBackData passed, continue DrawImage method.
                return false;
            }
        }
        private void button1_Click(object sender, EventArgs e)
        {
            if (img == null)
            {
                // Create image.
                img = Image.FromFile(@"C:\Users\lolaa\Downloads\Koala.jpg");

            }
           
        }

        private void Form1_Paint(object sender, PaintEventArgs e)
        {
            if(img != null)
            {

                Graphics g = this.CreateGraphics();

               

                // Create callback method.
                Graphics.DrawImageAbort imageCallback
                    = new Graphics.DrawImageAbort(DrawImageCallback8);
                IntPtr imageCallbackData = new IntPtr(1);

                // Create image.
                //Image newImage = Image.FromFile(@"C:\Users\lolaa\Downloads\Koala.jpg");
                //img = Image.FromFile(@"C:\Users\lolaa\Downloads\Koala.jpg");

                // Create rectangle for displaying original image.
                Rectangle destRect1 = new Rectangle(100, 25, 450, 150);

                // Create coordinates of rectangle for source image.
                float x = 50.0F;
                float y = 50.0F;
                float width = 150.0F;
                float height = 150.0F;
                GraphicsUnit units = GraphicsUnit.Pixel;

                // Draw original image to screen.
                g.DrawImage(img, destRect1, x, y, width, height, units);

                // Create rectangle for adjusted image.
                Rectangle destRect2 = new Rectangle(100, 175, 450, 150);

                // Create image attributes and set large gamma.
                ImageAttributes imageAttr = new ImageAttributes();
                imageAttr.SetGamma(4.0F);

                // Draw adjusted image to screen.
                try
                {
                    checked
                    {

                        // Draw adjusted image to screen.
                        g.DrawImage(
                            img,
                            destRect2,
                            x, y,
                            width, height,
                            units,
                            imageAttr,
                            imageCallback,
                            imageCallbackData);
                    }
                }
                catch (Exception ex)
                {
                    g.DrawString(
                        ex.ToString(),
                        new Font("Arial", 8),
                        Brushes.Black,
                        new PointF(0, 0));
                }



            }


        }

        public void DrawImageRect4FloatAttribAbortData(PaintEventArgs e)
        {

           
        }
    }
}
```



Output:

![image-20220319225230581](C:\Users\lolaa\AppData\Roaming\Typora\typora-user-images\image-20220319225230581.png)

Further discussion on other overloaded `DrawImage` methods is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.graphics.drawimage?view=dotnet-plat-ext-6.0#system-drawing-graphics-drawimage(system-drawing-image-system-drawing-rectangle-system-single-system-single-system-single-system-single-system-drawing-graphicsunit-system-drawing-imaging-imageattributes-system-drawing-graphics-drawimageabort-system-intptr)).