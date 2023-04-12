# Wireshark bflag Challenge

### Introduction

> hello every one today we are going to solve one of **Cyber Talents** challenges about **Wireshark**.

### lets see challenge

- challenge click [here](https://cybertalents.com/learn/introduction-to-cybersecurity/20-wireshark/challenges/bflag)

- this is the description for the challenge![bflagDescription](D:\Cyberus\bflagDescription.png)

### Solution

- first we need to download pcap file
- lets open it using wireshark ![pcapFile](D:\Cyberus\pcapFile.png)
- so we have this captured traffic
- we need to find the flag so can search about ```flag``` word as a string
- so we have this ![flagSearch](D:\Cyberus\flagSearch.png)

- some times there are characters represent as number as follow:

  ```
  Number : character
  0 : O 
  1 : L
  2 : Z
  3 : E
  4 : A
  5 : S
  ```

- lets try it now we can search for the **flag**  as `f14g`![flagSearch1](D:\Cyberus\flagSearch1.png)

- lets follow **TCP  Stream** for this package ![flag](D:\Cyberus\flag.png)

- Now we find the flag

### Thanks