# Arduino Animation
<h3>Displaying gifs and text using u8g2 library and XBM to animate multiple frames.</h3>

<br>
In this repository I have provided 2 examples, one being an animation of a cat looping through the screen and another one being general Kenobi from Star Wars emerging on the screen from the bottom
<br>

<br>This program was made for the Arudino 0.96" OLED screen. It is possible to use other sizes but the code will need to be adapted to do so.<br><br>
Here is the wiring for the OLED screen in case anyone needs it:<br>
![image](https://user-images.githubusercontent.com/72141834/156676674-1703edc1-cb8d-41d7-a66a-e45a1b7f1e24.png)<br><br>

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
in the drawAnimation() function, you will need to set the location in the OLED screen where the frame will be displayed as well as the position in the array where to get the frame from. To do so we use a pointer which increments after every loop moving the cat frame on the x axis. Once it reaches the end of the screen, the cat will automatically be displayed on the other side of the screen as the position will become negative. To change the frame we simply increase the frame pointer which will display a different frame in our u8g2.drawXBMP().

<br><br>
To change the text displayed, you can change the string inside the functions writeI() and writeP().
<br>
It is also possible to change the font of the text, and to find all possible options I recommend checking the repo of u8g2 font "fntlistallplain": https://github.com/olikraus/u8g2/wiki/fntlistallplain

<br><br>
The final product will look like this! 
<br>Cat example:

![ezgif-2-963c31d317](https://user-images.githubusercontent.com/72141834/158070043-18a5c818-cb94-4999-aff8-2ea4f1c89a8e.gif)
<br><br>
Kenobi example:<br>
![AnimatedKenobiGif](https://user-images.githubusercontent.com/72141834/158070069-f1519df1-2327-4870-adc6-66100e11f81f.gif)


<br><br><br>
Have fun messing around with this code! :)
