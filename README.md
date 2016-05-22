# esp8266-freedom
I put back the Wifi packet freedom that was taken away after "esp_iot_sdk_v1.3.0" 
__You can't take the sky from me..__

I've been reading the [Espressif Non-OS IoT SDK Guide](http://bbs.espressif.com/download/file.php?id=1366) and realised there's quite a lot of functionality in there that's not exposed to the world. 

Furthermore, after a bit of digging around in the 802.11 stack I realised they've literally reduced the functionality offered by wifi_send_pkt_freedom()! 

The reason I was looking to do this is because I'm building an ESP8266 mesh networking framework, and I was hoping to be able to implement 802.11s MAC frames (which requires a slightly different packet structure to the normal 802.11a/b/g standards). Ultimately the conclusion of that endeavour was that it's probably possible to send 802.11s MAC frames with wifi_send_pkt_freedom(), but the underlying hardware doesn't understand the differing packet format, which would probably cause it to ignore them all. I thought I might be able to circumvent this using the (vaguely hidden) promiscuous mode, but it turns out that only returns the paacket header information and is limited to 1

I don't like it when people take away freedoms, so I've put them back. I used the binary tools in [esp-open-sdk](https://github.com/pfalcon/esp-open-sdk) to pick out the original version of the wifi_send_pkt_freedom(), plus I've exposed some of the features that aren't normally available in the ESP8266Wifi driver for Arduino. 

In fact, I'm going to expose most of the Non-OS SDK, Espressif have released it, these files are straight out of version 1.3.0 of their IoT SDK. 
 
