---
sidebar_position: 3
title: Build Guide
---

# Ergonaut One Build Guide

## Assemble your PCB

| PCB                                 |
| ----------------------------------- |
| ![](/img/one_build_guide/pcb/0.jpg) |

### Case compatibility

You can assemble PCB in two different configurations - either with Xiao on "top", or on the "bottom".
Pick a configuration based on the variant of the case you would want to use.

:::note

All the images in this guide are using the configuration with the Xiao on the "bottom".

:::

| Case    | Xiao position |
| ------- | ------------- |
| Modern  | Bottom        |
| Classic | Top           |

### Soldering

#### Xiao

Before soldering the Xiao, please, apply a **small** amount of solder on the battery pins on the bottom of Xiao.
If you applied too much - you can collect the solder to the iron tip with some flux.

:::tip

The Xiao should sit flush on the PCB without being skewed or angled! If it's not
laying flat on the PCB, there is too much solder on the pins.

:::

![](/img/one_build_guide/pcb/bat_pins.jpg)

1. Position Xiao in its designated place
2. Start by soldering two opposite pins to keep it in place
3. Solder the rest of the pins
4. Flip the board
5. Put some flux in the holes (marked by the red circle in the photo), and fill them with solder (you might want to heat those pins a little longer than usual)

| Left                                  | Right                                 |
| ------------------------------------- | ------------------------------------- |
| ![](/img/one_build_guide/pcb/1_l.jpg) | ![](/img/one_build_guide/pcb/1_r.jpg) |
| ![](/img/one_build_guide/pcb/2_l.jpg) | ![](/img/one_build_guide/pcb/2_r.jpg) |

#### Diodes

"Bottom Xiao" configuration: diodes should be on the **SAME** side as Xiao.  
"Top Xiao" configuration: diodes should be on the **OPPOSITE** side from Xiao.

Please take note that diodes have polarity that are shown on the PCB and on the
diodes with a line.

![](/img/one_build_guide/pcb/diode.png)

![](/img/one_build_guide/pcb/diode_2.jpg)

1. Add a small amount of solder to one pad
2. Place the diode on the pads with tweezers, making sure they are in the
   correct orientation
3. Melt the solder already on the pad and ensure the diode aligned properly
4. Solder the other pad

| Left                                  | Right                                 |
| ------------------------------------- | ------------------------------------- |
| ![](/img/one_build_guide/pcb/3_l.jpg) | ![](/img/one_build_guide/pcb/3_r.jpg) |

#### Hotswap Sockets

"Bottom Xiao" configuration: sockets should be on the **SAME** side as Xiao.  
"Top Xiao" configuration: sockets should be on the **OPPOSITE** side from Xiao.

The orientation of the sockets does **not** matter.

1. Insert the sockets into the PCB
2. Solder one pin of each socket to keep them in place, ensuring the socket is
   flat against the PCB
3. Check if the sockets are flat, if there are any that are not, reheat the
   solder and adjust the socket
4. Solder the other side of the sockets

| Left                                  | Right                                 |
| ------------------------------------- | ------------------------------------- |
| ![](/img/one_build_guide/pcb/4_l.jpg) | ![](/img/one_build_guide/pcb/4_r.jpg) |

#### Power Switches

Power switches are always on the opposite side of Xiao.

1. Add a small amount of solder to one pad
2. Place the switch on the pad with the mounting pins in the holes
3. Melt the solder already on the pad and ensure the switch is aligned properly
4. Solder the other pads

![](/img/one_build_guide/pcb/5.jpg)

#### Test for shorts

If you have a multimeter, test for shorts before connecting the battery.

1. Between "-" and "+";
2. Between GND and 5V on the Xiao;
3. Between GND and 3V3 on the Xiao.

![](/img/one_build_guide/pcb/pins.jpg)

#### JST Connector (Optional)

The JST connector is optional and is used to connect the battery to the PCB.
If your battery doesn't have a JST connector or if you prefer to do so, you can
solder the battery wires directly to the PCB in the next step.

JST connector should be on the same side as the battery.

1. Apply solder to the larger solder pad closest to the Xiao as it is the most
   difficult to solder with the connector in place
2. Align the JST connector on the pad, making sure the small leads on the
   connector are aligned with the pad labeled "+" and "-"
3. Heat the solder pad with the previously applied solder and push the connector
   down onto the pad, ensuring it is flush with the PCB and the leads are aligned
4. Solder the other pads

#### Batteries

If you are added a JST connector and have a compatible battery, you just connect
the battery and move on to the next step.

:::warning

Please take note of battery polarity. Positive wire (red) should go to "+",
negative wire (black) to "-".

:::

You can choose any side for battery wires soldering, but using the same side as
the Xiao is suggested.

Even though the battery is protected, it's recommended to solder on 1 wire at a
time to prevent two loose exposed wires from touching and causing a short.

1. Strip the end of the ONE battery wire. The amount of bare wire should be
   enough to pass through the hole with a little extra to fold over.
2. Pass the wire through the hole in the PCB such that the wire comes from the
   side opposite of the other connection, parallel to both solder pads (refer to
   the image)
3. Fold the wire on the backside such that it folds away from the other
   connection
4. Solder the wire to the through hole pad
5. Trim the excess wire on the backside
6. Repeat for the other wire

![](/img/one_build_guide/pcb/6.jpg)

#### Test the battery connection

If you do not have a multimeter, skip this step.

Turn on the power switch and verify the voltage between GND and 3V3 is 3.3 volts.
If the voltage is not there, you probably need to re-solder the underside pads.

### Clean up

Clean your PCB from flux residues. IPA (isopropyl alcohol) with Q-tips should do the trick.

### Flash firmware

Now it's a good time to flash firmware to a keyboard.

1. Download [firmware](https://github.com/ergonautkb/one-zmk-config/releases/latest/download/ergonaut_one_firmware.zip) and unzip it.
2. Repeat for each half:
   1. Connect the PCB to the PC via USB-C cable;
   2. Press the **RST** button twice - you should see a new USB device;
   3. Copy `ergonaut_one_left-seeeduino_xiao_ble-zmk.uf2` for left half or `ergonaut_one_right-seeeduino_xiao_ble-zmk.uf2` for right half to the new USB device. The device will disconnect automatically;
3. Turn ON both halves;
4. Press the **RST** button of both halves SIMULTANEOUSLY to pair them;
5. Try to connect it to the PC via Bluetooth and test that everything works;
6. Turn OFF both halves.

![](/img/one_build_guide/pcb/7.jpg)

### Test the PCB

If you do not have a multimeter, connect the battery on the left half and turn it on.
Verify it shows up as a Bluetooth keyboard.
If it does not and only shows up when connected to USB power, you probably need to re-solder the underside pads.
That is also the likely cause for the right half not connecting on battery and only working when connected to USB power.

After that, you can optionally verify the matrix.
Connect both halves to your PC and either use tweezers to short each socket or insert and press switches.
Please brace the sockets (with your fingers) when inserting the switches!

![](/img/one_build_guide/pcb/tweezers.jpg)

Keep in mind that some positions in the matrix are modifiers and will not do anything when pressed on their own.
A [keyboard tester website](https://www.keyboardtester.com) will work for modifiers, but it will not detect layers.

Matrix verification can be performed after inserting all the switches into the top case, but it is best done before mounting the bottom.

## Assemble your case

Start by inserting the PCB inside the top part of the case.

![](/img/one_build_guide/case/1.jpg)

Flip the keyboard, and insert some switches while holding the PCB against the top case. This will fix the PCB in place for further build.

![](/img/one_build_guide/case/2.jpg)

Flip the keyboard again, and insert the bottom part of the case.

![](/img/one_build_guide/case/3.jpg)

Now the tricky part - you should place hex nuts in the hex slots on the bottom side of the case, and insert screws from the top side of the case.

:::warning

Please do not overtighten the screws! You can easily damage the case.

:::

| Top                                  | Bottom                               |
| ------------------------------------ | ------------------------------------ |
| ![](/img/one_build_guide/case/4.jpg) | ![](/img/one_build_guide/case/5.jpg) |

Install rubber bump-ons on the bottom side of the case.

![](/img/one_build_guide/case/7.jpg)

Now insert the rest of the switches into the case.

![](/img/one_build_guide/case/6.jpg)

Now put your favorite keycaps, repeat the steps for the second half of the keyboard, turn it on, and enjoy your freshly assembled Ergonaut One!

![](/img/one_build_guide/case/8.jpg)
![](/img/one_build_guide/case/9.jpg)
