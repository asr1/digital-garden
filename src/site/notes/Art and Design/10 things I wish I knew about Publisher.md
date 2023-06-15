---
{"dg-publish":true,"permalink":"/art-and-design/10-things-i-wish-i-knew-about-publisher/","tags":["design"],"noteIcon":1}
---


# 10 things I wish I knew about Affinity Publisher
([source](https://www.skeletoncodemachine.com/p/10-affinity-publisher-tips))
##  1. Find some favorite blend modes
_Tip: Experiment with different blend modes to find ones you like._

Darken, color burn, screen, overlay, and divide are just a few of the [blend mode types](https://affinity.help/publisher/en-US.lproj/index.html?page=pages/Layers/layerBlendModes.html?title=Layer%20blending) available. I’ve found these to be useful when giving [public domain art](https://www.skeletoncodemachine.com/p/public-domain-art-resources) a unified look across a project, especially by adding some grunge textures. There’s no faster way to learn how to use them than by just playing around.

What I didn’t know at first was that not all of these will work the same way across all platforms when exported to PDF. I’ve found color burn and linear burn to be particularly unpredictable. One workaround is to export everything to PNG or TIFF and then add that back in as a static image layer.

## 2. Understand CMYK vs. RGB

_Tip: Use CMYK safe colors if you want your print to look like it did on your screen._

I had heard of CMYK but I had no idea how important it is when first designing for print!

**RGB color is an additive model.** This is how your monitor and other electronic displays show color. Colors are formed by adding different intensities of colored light. The display starts as black and can range in color all the way to white.

**CMYK color is a subtractive model.** The paper starts white and can have ink added all the way to black by reducing the amount of reflected light.

When I started, I thought any color from the default Affinity “Colors” swatch palette was fine, but that may not be true. It’s much harder to pick colors that look very similar in both RGB and CMYK color spaces. If you are using Mixam as your printer, they have a [list of colors](https://mixam.com/support/cmykchart) “considered reliable for offset printing.”

Want a better CMYK swatch palette to use vs. the default one? Import the **[EP CMYK Palette](https://exeuntpress.itch.io/cmyk-color)** based on the Mixam list above.

If you choose a “Press Ready” preset in Affinity Publisher, it will use CMYK color for the document.

## 3. Know when to use Rich Black

_Tip: Use Standard Black for text, and Rich Black only when you need it._

This one is related to the CMYK colors above, but deserves it’s own item.

**Standard black** is simply 100% black (K) ink, and it’s what is used most often for text, line art, and simple black and white images. It can reproduce very fine details, and works in almost every application.

**Rich black** includes other colors such as cyan, magenta, and yellow to make it appear as a deeper, richer black color when printed. The problem is that because it uses multiple colors, it can cause [ghosting](https://mixam.com/support/standardvsrichblack) or appear blurry when used for text or fine details.

Typical [Rich Black](https://en.wikipedia.org/wiki/Rich_black) (C:60 M:40 Y:40 K:100) is what you might see most of the time, and is recommended in the [Unofficial MÖRK BORG Design Primer](https://docs.google.com/document/d/e/2PACX-1vTjDn-lRynqw_W-xLWzM2yTHOIoHrdRkygMVqNAzLIkQzV85kHYTR-Bsv1431JOE_DLHITirIiAPjj-/pub). Mixam recommends two different Rich Blacks including C:30 M:30 Y:30 K:100 and C:60 M:30 Y:30 K:100.

## 4. Beware bleed and safe zones

_Tip: Keep important stuff away from the bleed and in the safe zone._

**Bleed** is the area that extends past the final trimmed area of the page, and will be cut off. It’s important because if there is any misalignment in the trimming process, you want to make sure the final product still looks OK. This is done by ensuring that all background images and/or art extend past the printed edge and completely fill the bleed.

**Safe Zones** are the inner portion of the page that contains the most important parts of the design, usually the text. Keeping your text inside the safe zone ensures that the important parts are never cut off even if the trimming isn’t quite right.

If you choose a “Press Ready” preset in Affinity Publisher, you get a 3 mm bleed and 17 mm margin which is pretty standard. Press Ctrl+Shift+W to turn bleed visibility on and off for previewing.

## 5. Have a plan for linked resources

_Tip: Decide how you want to store art before you start linking to it._

In Affinity Publisher you can choose to embed or link your image files when adding them to a project:

- **Embedding** puts a copy of the whole file into the document. Modifications to the original file won’t impact the project, and the file comes with the document if it’s moved. The downside is that embedding all your art can make your project file size extremely large.
    
- **Linking** just makes a link between the art in the document and the file on the disk. If you update the linked art, it updates the document. This can keep your file sizes under control.
    

Not knowing how quickly I would accumulate [public domain art](https://www.skeletoncodemachine.com/p/public-domain-art-resources), I just made some folders and stored it on my main SSD. If and when I begin to run out of space, I’ll need to move everything to another drive. With everything linked, I now need to be really careful how that happens, or it will break all of the links in the Affinity documents. While Affinity will warn you and give you a chance to find and relink them, it can turn into a [giant mess](https://xkcd.com/349/) very quickly.

Consider if you want to link or embed your files. If you choose to link, make sure you have a long term plan if you move things around.

## 6. Check your fields panel

_Tip: Make your Author field what you want to show up in the PDF properties._

Hidden deep within Affinity Publisher under the View, Studio, and then Fields is the [Fields Panel](https://affinity.help/publisher/en-US.lproj/index.html?page=pages/Panels/fieldsPanel.html?title=Fields%20panel). This panel allows you to change your document information, including the Author, which probably defaults to your actual full name. Whatever is in the Author field will be put in the properties of the exported PDF. So if you want to use a name other than your real one when publishing, be sure to double check this before exporting.

The above works in Affinity Publisher V1 only. For V2 the Fields panel is under Window, References, Fields. (Go read [Your RPG Confuses Me](https://open.substack.com/pub/rpgconfusesme) because it’s awesome.)

## 7. Stay out of the gutter

_Tip: Stay far away from the center fold in bound books._

If you’ve ever had to really push down and break the spine of a book to read the text in the middle, that’s the gutter. It can be quite big/deep in perfect bound books, compared to staple bound.

If you choose a “Press Ready” preset in Affinity Publisher, the two inner 17 mm margins will give you a combined gutter of 34 mm (2 x 17 mm) which is probably safe in most cases. Many places recommend at least 0.5” of gutter margin on each side, but check with your printer for the actual requirements.

## 8. Check your PDF on multiple platforms

_Tip: Open your finished PDF in Acrobat, Chrome, and Edge to see how it looks._

While mostly related to layer blend modes above, there are all sorts of reasons your PDF might not looks the same in Chrome as it does in Adobe Acrobat Reader. The only way to know (that I’m aware of) is to open it in each target platform and look.

It doesn’t take long, and will ensure a consistent experience for everyone.

## 9. Check your fonts at actual size

_Tip: Your text is smaller than you think. Use Ctrl+8 to check it._

Chances are that you are zoomed in when working on your document. That’s great for most things, but when printed you might find the text is too small (or too big). This is particularly an issue when working with small formats like [MOSAIC Strict bridge cards](https://exeuntpress.itch.io/chthonic-metro-gods).

I’ve found that using Ctrl+8 to view Actual Size really does work! While not perfect, it allows you to view your document at very close to the actual, final printed size. You can do a quick check to make sure everything is readable.

Of course the only true test is to print it, but this is the next best thing!

## 10. Add some percent-based guides

_Tip: Give yourself some basic guides for each page._

Affinity’s “Press Ready” settings give you bleed and margins, but having some additional guides is always helpful. Under View, open the Guides Manager, and check the Percent box.

I like to set up horizontal and vertical guides at either 10%, 50%, 90% or 20%, 50%, 80% depending on the project. That gives me center lines as well as framework for aligning things.

You can also use the Grid Manager, but that could probably be a whole post by itself.

## See Also
[[Art and Design/Layout#Printed book colors\|Layout#Printed book colors]]