# Arduino Animation
<h3>Displaying gifs and text using u8g2 library and XBM to animate multiple frames.</h3>

<br>This program was made for the Arudino 0.96" OLED screen. It is possible to use other sizes but the code will need to be adapted to do so.<br><br>

In order to do so we first have to select what gif we want to use.
In arduino it is not possible to display gifs as they are, therefore we will split the gif in different frames, map each pixel in them to be stored in an array of char and then display the gif in sequence using the u8g2 library.
<br><br><br>
It is possible to split the gif into frames on many websites, such as: https://ezgif.com/split
<br>
With the frames splitted, we have to do one final step before being able to animate the gif in arduino.
We need to map each pixel in the frame and obtain the XBM files!
<br>To do so we can use an online converter that automatically maps it for us:<br>
https://www.online-utility.org/image/convert/to/XBM
<br><br><br>

Inside the code we can see that I have made an array of chars that will store the XBM of each frame.<br>
You can replace the number of frames and the content of each array location easily by changing the values that I have set when declaring the array.
<br>![image](https://user-images.githubusercontent.com/72141834/156674686-1726fa42-98fe-4ad3-afce-89cdba408606.png)
<br>
For example, if you were to have 15 frames you would set the first value of the array to be 15 and the second would be the n. of values that each XBM will have.
To calculate that, multiply the n. of columns by the number of rows. E.g.: in our repo the XBM files have 12 columns and 48 rows, therefore we will need 576 locations.<br>
Once done that, don't forget to define the height and width of the frames that you're trying to display.
<br><br><br>
in the drawAnimation() function, you will need to set the location in the OLED screen where the frame will be displayed as well as the position in the array where to get the frame from. To do so we use a pointer which increments after every loop, and a switch which depending on the pointer, will display a different case of our u8g2.drawXBMP().

<br><br>
To change the text displayed, you can change the string inside the functions writeI() and writeP().
<br>
It is also possible to change the font of the text, and to find all possible options I recommend checking the repo of u8g2 font "fntlistallplain": https://github.com/olikraus/u8g2/wiki/fntlistallplain

<br><br>
The final product will look like this!

![cat-animation](https://user-images.githubusercontent.com/72141834/156673473-46ed7ef7-0bf0-4ac2-a08b-87c6d529ce1d.gif)
<br><br><br>
Have fun messing around with this code!
