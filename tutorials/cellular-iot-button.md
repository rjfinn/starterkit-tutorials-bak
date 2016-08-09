
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
3. Fork the [Buttons reference project](https://flow.att.io/starter-kit-core/starter-kit-buttons/home) using the ![alt text](../images/Fork.jpg "Fork") button.
4. Deploy it to set the endpoints using the ![alt text](../images/Deploy.jpg "Deploy") button.
5. Open the Endpoints tab and you'll see something like this:
![alt text](../images/ButtonsFlow.jpg "Buttons Flow")
6. If you haven't already, assemble the hardware for for your AT&T IoT Starter Kit.
 ⋅⋅*The shield goes on top with the micro USB ports all facing the same direction.  The SIM card is inserted with the metal leads facing down.
- ⋅⋅*
Only the power USB cable is required once the device is operational.  That requires 5V-2.4A provided by the USB plug in your kit.
 ⋅⋅*The USB serial cable plugs into your computer for transferring the program and monitoring the serial output.

![alt text](../images/KitCables.jpg "Kit Cables")
7. Log into the [ARM mbed online IDE](https://developer.mbed.org/compiler/) (create an account if you don't have one).
8. Import the [ATT_Cellular_IoT_Button](https://developer.mbed.org/users/rfinn/code/ATT_Cellular_IOT_Button/) template program.
9. Alter the config_me.h file and modify MY_SERVER_NAME, MY_PORT_STR, and FLOW_BASE_URL.
⋅⋅*By default, the program only uses the TCP version so you don't need FLOW_BASE_URL unless you change your code to use an HTTP GET.