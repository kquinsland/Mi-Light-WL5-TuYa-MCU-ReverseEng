I have found the blue/gold colors to be useful in testing and reverse engineering work.
I pulled the packets directly from pulseview.
They can be sent directly to the MCU via the `SerialSend5` command.
The payloads do not _always_ work as the mode setting button on the controller seems to iterate through some pre-defined colors / modes.
There appear to be somewhere between 4 and 6 different modes.
I have not yet been able to figure out _exactly_ what each mode is... all I know is that sometimes the `serialsend5` command does not work. Press the mode button a few times and then it does.


BLUE: 
55 AA 00 06 00 19 1C 03 00 15 31 30 31 30 66 30 33 65 38 30 33 65 38 30 30 30 30 30 30 30 30 FA
SerialSend5 55 AA 00 06 00 19 1C 03 00 15 31 30 31 30 66 30 33 65 38 30 33 65 38 30 30 30 30 30 30 30 30 FA


GOLD:
55 AA 00 06 00 19 1C 03 00 15 31 30 30 35 32 30 33 65 38 30 33 65 38 30 30 30 30 30 30 30 30 CA

SerialSend5 55 AA 00 06 00 19 1C 03 00 15 31 30 30 35 32 30 33 65 38 30 33 65 38 30 30 30 30 30 30 30 30 CA



Tasmota docs seem to indicate that previously reverse engineered TuYa things use one of two methods of encoding color:"

- `0HUE0SAT0BRI0` (type1) 
- `RRGGBBFFFF6464` (type2)

See: https://tasmota.github.io/docs/TuyaMCU/#rgb-light

I don't see any `6464` sequences so likely dealing with the first type.
Aka [`TuyaRGB 0`](https://tasmota.github.io/docs/Commands/#tuyamcu)

DPid 24
    BLUE:  01 0f 03 e8 03 e8
    GOLD: 00 52 03 e8 03 e8

    0HUE0SAT0BRI0
