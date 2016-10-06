# F1r3d&H4ck3d - Egypt

So we got a Folder with a bunch of files inside.
Some word documents, PCAP files and other stuff.

We noticed this suspicious Screenshot in the folder:

![found screen](work.png)

There were 2 Hotspots:

**Network: BSSID**

**FLAGPART1: 5C:4C:A9:AE:2D:A1**

**FLAGPART2: 20:7C:8F:9A:1E:A3**

So the idea was, that the flagname is the combination of the network passwords.

There were 2 Network Types: WEP and WPA2 PSK

####The PCAP Files
So the first thing we needed, was to get all the pcap files in the folders.
We put them alltogther into one folder. Therefore it was easier to work with it.
The files were in the PCAPng format present. aircrack-ng can't handle this format.
Therefore we needed to convert it into old PCAP file format via `editcap`:

`editcap <infile> <outfile>`

After the conversion they were usable with aircrack-ng tool.


##### WEP
WEP is easily crackable with captured IV. We had enough captured traffic to crack them via aircrack-ng.
But there were not enough in a single PCAP File. You need minimum of 5000 IVs to crack it.
Therefore we combined all the PCAP files with the following tool which is integrated of aircrack: `mergecap` (check manpage for usage)

After we merged the files we had enough data to crack the password easily with the following command:

`aircrack-ng -b BSSID <merged PCAP File>`

##### WPA2/PSK
In the captured traffic was also a handshake between a Client and the FLAGPART2 Network.
It is possible to bruteforce the password of a WPA2/PSK Network if you have captured a handshake.

We tried the password.lst file in the test folder, and the rockyou wordlist with [hashcat](https://hashcat.net/hashcat/) to crack the password, but the password wasn't there.
Then cluosh found a link to a password list in one of the word documents.
This was the key for the solution. We cracked the password via [hashcat](https://hashcat.net/hashcat/)

<br />
#####The Flag
The Flag was the combination of the Passwords from FLAGPART1 and FLAGPART2 Networks.

**h4ck1t{FLAGPART1pw+FLAGPART2pw}**  (sorry no clue what real flag was)

