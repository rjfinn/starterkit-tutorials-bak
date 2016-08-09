
# Cellular IoT Button

|   Author   | Created At  |
| ---------- | ----------- |
| rjfinn     | 2016-08-09  |

------

### Intro

A simple use case to demonstrate using the built-in buttons on the Freedom K64F board which comes with the AT&T IoT Starter Kit.  Both SW buttons on the board result in calls to AT&T Flow which then sends a message.  The default case uses Twillio to send an SMS.

### Steps

1. If you haven't already, set up an account on the [Starter Kit `Portal`](https://starterkit.att.com/app) and register your SIM card.
2. Log into [AT&T Flow](https://flow.att.io/).
3. Fork the [Buttons reference project](https://flow.att.io/starter-kit-core/starter-kit-buttons/home) using the ![alt text](../images/Fork.jpg "Fork") button.  (Optional: Create a Twillio account to receive SMS messages and configure the Twillio node in this flow)
4. Deploy it to set the endpoints using the ![alt text](../images/Deploy.jpg "Deploy") button.
5. Open the Endpoints tab and you'll see something like this:
<br/>![alt text](../images/ButtonsFlow.jpg "Buttons Flow")
6. If you haven't already, assemble the hardware for for your AT&T IoT Starter Kit.  The shield goes on top with the micro USB ports all facing the same direction.  The SIM card is inserted with the metal leads facing down.  Only the power USB cable is required once the device is operational.  That requires 5V-2.4A provided by the USB plug in your kit.  The USB serial cable plugs into your computer for transferring the program and monitoring the serial output.
<br/>You may need to update the firmware.  Check the DETAILS.TXT file in the MBED drive for the firmware version.  You want at least 0226.  If not, [get the latest here](https://developer.mbed.org/handbook/Firmware-FRDM-K64F).
<br/>![alt text](../images/KitCables.jpg "Kit Cables")
7. Log into the [ARM mbed online IDE](https://developer.mbed.org/compiler/) (create an account if you don't have one).
8. Select the [FRDM-K64F platform](https://developer.mbed.org/platforms/FRDM-K64F/) and import the [ATT_Cellular_IoT_Button](https://developer.mbed.org/users/rfinn/code/ATT_Cellular_IOT_Button/) template program.
9. Alter the config_me.h file and modify MY_SERVER_NAME, MY_PORT_STR, and FLOW_BASE_URL.  By default, the program only uses the TCP version so you don't need FLOW_BASE_URL unless you change your code to use an HTTP GET.
<br/>![alt text](../images/ButtonsMbed.jpg "Buttons m-bed")
10. Compile the binary file.  It will create an ATT_Cellular_IoT_Button_K64F.bin file and download it to your Downloads folder.
11. Drag and drop this over to the MBED drive which appeared when you plugged in the Starter Kit.
12. The code will load and then automatically reboot the device, but I like to manually use the Reset button anyway.
![alt text](../images/KitButtons.jpg "Kit Buttons")
13. Once its up and talking you can click on the SW2 or SW3 buttons (they come through to Flow as Button 1 and Button 2, respectively).  You'll see this in the Debug panel of the Flow.

Now you're up and running!  You can modify the flow to add functionality like calling out to other web services.

### Troubleshooting

If you're having trouble it may help you to connec to the serial output.  Use a terminal program to connect to the newly created serial port (typically something like usbmodem1412 for the Mac or COM14 for the PC) with a 115200 baud rate.
* [PC USB serial driver](https://developer.mbed.org/handbook/Windows-serial-configuration)

Make sure to check your flow endpoints for the correct server name and port.  Most people forget to change the server name.

The modem module requires a lot of power.  The USB plub included with the kit provides ***5V-2.4A*** and you need at least that much.
