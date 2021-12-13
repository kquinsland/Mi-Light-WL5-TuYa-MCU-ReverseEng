
https://tasmota.github.io/docs/TuyaMCU/#anatomy-of-tuya-protocol


TX: The 4th byte is 6 which means "send commands"

55 AA 00 06 00 05 14 01 00 01 01 21

HEADER:
    55 AA 00

CMD:
    06 

DATA LEN:
    00 05


dpID
    14

(0x14 is 20 which according to this post is the 'traditional' binary on/off)
    https://github.com/arendst/Tasmota/issues/7385#issuecomment-701405902

dType
    01

Len:
    00 01

CMD:
    01

CHKSUM:
    21





RX: 

55 AA 03 07 00 05 14 01 00 01 01 25 
