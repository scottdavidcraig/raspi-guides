# Raspberry Pi temperature

It's important to keep the Raspberry Pi from getting too hot (or too cold!). To keep our Pi running smoothly, we should keep an eye on its temperature.

This guide shows you how to;

1. Show the temperature using the command-line.
2. Create a command-line temperature shortcut
3. Display the temperature in the GUI

Let's get started!

## Viewing the computer's temperature

The Raspberry Pi has a thermometer on the circuit board that we can use to measure the temperature of the processor.

### Show the temperature using the command-line.

To access the thermometer's temperature open the terminal and type;

```
vcgencmd measure_temp

```
This command returns the temperature of the SoC. in degrees celsius.

If we need a more precise reading, we can type;

```
cat /sys/class/thermal/thermal_zone0/subsystem/thermal_zone0/temp
```
This command returns the temperature in millicelsius.

### Create a command-line temperature shortcut

Typing long commands like this can become very tedious.

To access the temperature quicker let's create a shortcut, or alias, for each of our two commands.

1. Navigate to your home folder
```
cd ~
```
2. Open a the `.bash_aliases` file in a text editor.
```
sudo nano .bash_aliases
```
3. Add the following lines to the `.bash_aliases` file
```
alias celsius='vcgencmd measure_temp'
alias millicelsius=' cat /sys/class/thermal/thermal_zone0/subsystem/thermal_zone0/temp'
```
4. Save the file and exit the text editor.
5. You're done!

Open terminal and type in `celsius` or `millicelsius` to see the results.

Oh no! it doesn't work! But why?

The `.bash_aliases` file is only read by the terminal program (called bash) when it loads up. For our new shortcuts to work, we have to close the current terminal window and start up a new one. Try it now.


### Show the temperature in the GUI

To display the temperature in the Raspbian task bar;

1. Right-click on the task bar
2. Click on 'Add / Remove panel items'
3. In the 'Panel Applets' tab, click 'add'
4. Scroll through the list until you find temperature and click 'add'

You should now see a real-time indicator of the computers temperature in the task bar!

Notice that the task bar temperature indicator is colour coded. See if you can find out at what temperature it changes colour!


## Learn more!

[Formatting output from RPI temperature sensors](http://kernelreloaded.com/formatting-output-from-raspberry-pi-temperature-sensors/)

[The vcgencmd command](http://elinux.org/RPI_vcgencmd_usage)


## Attribution.

Credit to eXsoR on the Raspberry Pi forums for explaining [how to create a bash alias.](https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=34994)
