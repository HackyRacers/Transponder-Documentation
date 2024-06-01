I found this online and it seems to have been copied and pasted from a bunch of sources so no idea who to credit.

For the I-Lap hardware there are two known response packets
To start the lap counter you must send the following command:   
`01 25 0D 0A`  

This initializes the lap counter into 7 digit mode
This will respond with a packet that looks like the following:  
`01 25 09 32 30 34 09 30 09 30 0D 0A`

The breakdown is the following:  
- Byte 1 is the header, `01`  
- Byte 2 is the packet type, `25` (%) for an initialization packet  
- Byte 3 is a seperator character, `09` seperates fields  
- Bytes 4-6 are the decoder id in ascii, `204` in this case  
- Byte 7 is a seperator, `09`  
- Byte 8 is not used set to `0` in ascii  
- Byte 9 is a seperator, `09`  
- Byte 10 is not used set to `0` in ascii  
- Bytes 11 and 12 are the ending delimiter, `0D 0A` is a new line character sequence  

After the lap counter is initialized it will send a packet each time a car is detected. An example packet would look like this:  
`01 40 09 32 30 34 09 33 34 35 36 37 38 39 09 33 32 34 2E 36 32 30 0D 0A`  

The breakdown is the following:
- Byte 1 is the header, `01`
- Byte 2 is the packet type, `40` (@) for a transponder packet
- Byte 3 is a seperator character, `09` seperates fields
- Bytes 4-6 are the decoder id in ascii, 204 (`32 30 34`) in this case
- Byte 7 is a seperator character, `09`
- Bytes 8-14 are the transponder id in ascii characters, 3456789 (`33 34 35 36 37 38 39`)
- Byte 15 is a seperator character, `09`
- Bytes 16 - 22 are the time, it starts counting up when initalized, this field can vary in size, time is in the format SECS.MSS, 324.620 in this case
- Bytes 23 and 24 are the ending delimiter, `0D 0A` is a new line character

A second example would look like this:  
`01 40 09 32 30 34 09 33 31 37 34 39 36 36 09 31 32 2E 32 32 36 0D 0A`  

This has a transponder 3174966 and a time of 12.226

Third example:  
`01 40 09 32 30 34 09 37 32 35 31 33 31 38 09 34 2E 34 34 38 0D 0A`  

This has transponder 7251318 and a time of 4.448
