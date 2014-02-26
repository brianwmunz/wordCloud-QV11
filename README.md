wordCloud-QV11
==============

Repository for storing the code for the D3 world cloud extension for QlikView 11.

I don't use all of the options available in this library and keep it pretty bare bones, but I imagine this extension should satisfy most use cases. 
The properties are fairly straightforward:
![alt tag](http://community.qlik.com/servlet/JiveServlet/showImage/2-265261-22843/cloudprops.png)
The Words dimension is simply the list of words that will be displayed in the cloud
 
Measurement is an expression which controls the sizes of the words.  This could be anything you'd like to measure the words against.
 
Color Expression is the expression which controls the color of the words.  If you simply want one color, you could hardcode it to a hex or RGB color, or you could use an expression and mix two colors (using the ColorMix1 function from QlikView), or use the expression like a gauge and present any number of colors based on some range.
 
The Maximum Font Size and Minimum Font Size properties are simply the maximum and minimum sizes of the words.
 
SOME THINGS TO NOTE:
The cloud can be a bit unwieldly (or maybe crash) if you pass too many words into it, so I've set a maximum data set of 700 for this extension.  To change this, edit the Definition.xml file in the extension's folder and change 700 to whatever you want in this line:
```
<ExtensionObject Label="wordCloud" Description="wordCloud" PageHeight="700">
```
The only issue this might cause is if you have 1000 words in the dimension, a random selection of 700 will be passed in, in no particular order.  I've tried and tried to get the extension to sort based on the expression rather than the dimension and I think it's not possible (which may be a bug), so instead returning the top x number of words based on an expression might need to be done using set analysis, firstsortvalue, or ranking function.