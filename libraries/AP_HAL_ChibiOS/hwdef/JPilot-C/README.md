# JPilot-C

Autopilot board for small UAV.

Developed and distributed by [Flyfocus](https://flyfocus.pl/avionics/)

![photo of the board](./JPilot-C_board_v1.0.jpg)

## Features

- dimensions: 32x32x8mm
- mass: 5g
- power: <1W
- interfaces: USB, GPIO, SPI, I2C, USART, PWM, CAN, analog
- onboard sensors: 2x IMU, 2x barometer
- overcurrent and ESD protection

## Pinout

Connector pinouts follow [DS-009 Pixhawk Connector Standard](https://github.com/pixhawk/Pixhawk-Standards/blob/master/DS-009%20Pixhawk%20Connector%20Standard.pdf)

|Connector|Pin 1|Pin 2|Pin 3|Pin 4|Pin 5|Pin 6|Pin 7|Pin 8|Pin 9|Pin 10|
|---------|-----|-----|-----|-----|-----|-----|-----|-----|-----|------|
|Telem1   |     |     |     |     |     |     |     |     |     |      |
|Telem2   |     |     |     |     |     |     |     |     |     |      |
|GPS1     |     |     |     |     |     |     |     |     |     |      |
|GPS2     |     |     |     |     |     |     |     |     |     |      |
|CAN1     |     |     |     |     |     |     |     |     |     |      |
|CAN2     |     |     |     |     |     |     |     |     |     |      |
|I2C      |     |     |     |     |     |     |     |     |     |      |
|Power1   |     |     |     |     |     |     |     |     |     |      |
|Power2   |     |     |     |     |     |     |     |     |     |      |

## UART Mapping

|Serial#|Protocol|Port  |Notes|
|-------|--------|------|-----|
|Serial0|OTG1    |USB   |     |
|Serial1|        |UART7 |     |
|Serial2|        |USART1|     |
|Serial3|        |USART2|     |
|Serial4|        |USART3|     |
|Serial5|        |UART8 |     |
|Serial6|        |UART4 |     |

## CAN Ports

There are 2 CAN buses available, each with a 120 Ohm termination resistor built-in.

## PWM Output

JPilot-C supports up to 14 PWM outputs with D-Shot.

The PWM outputs are in 5 groups:

- PWM 1 & 2 in group 1
- PWM 3 - 6 in group 2
- PWM 7 - 10 in group 3
- PWM 11 & 12 in group 4
- PWM 13 & 14 in group 5

Channels within the same group need to use the same output rate. If any channel in a group uses D-Shot then all channels in the group need to use D-Shot.

## RC Input

Using the RCin pin will support all unidirectional RC protocols.

## Battery Monitor

The board has internal voltage sensors and connection for external current sensor on the "Power1" and "Power2" ports.
The default battery parameters are:

- BATT_MONITOR 4
- BATT_VOLT_PIN 10
- BATT_CURR_PIN 11
- BATT_VOLT_MULT 11
- BATT2_VOLT_PIN 18
- BATT2_CURR_PIN 7
- BATT2_VOLT_MULT 11
- BATT_AMP_PERVLT 40

## Analog pins

These analog pins are used in addition to battery monitoring:

- Servo rail voltage (scale 1:3, pin PC5)
- VDD 5V supply voltage (scale 1:2, pin PA5)
- Pressure sensor (scale 1:2, pin PC4)

## Compass

JPilot-C does not have a builtin compass, but you can attach an external compass using the I2C port.

## Firmware

Firmware for JPilot-C can be found [here](https://firmware.ardupilot.org) in sub-folders labeled "JPilot-C".
