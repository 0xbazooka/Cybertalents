# Wireshark bflag Challenge

### Introduction

> hello every one today we are going to solve one of **Cyber Talents** challenges about **Wireshark**.

### lets see challenge

- challenge click [here](https://cybertalents.com/learn/introduction-to-cybersecurity/20-wireshark/challenges/bflag)

- this is the description for the challenge ![bflagDescription](https://user-images.githubusercontent.com/83983701/231558165-76167a81-5e36-4c6e-a353-71d029861232.png)


### Solution

- first we need to download pcap file
- lets open it using wireshark ![pcapFile](https://user-images.githubusercontent.com/83983701/231558294-5d3d4915-63f0-4eec-9522-5ba39b247200.png)
- so we have this captured traffic
- we need to find the flag so can search about ```flag``` word as a string ![flagSearch](https://user-images.githubusercontent.com/83983701/231558378-f7fa53b2-1f67-480e-be81-4a8c924ddf48.png)
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

- lets try it now we can search for the **flag**  as `f14g`![flagSearch1](https://user-images.githubusercontent.com/83983701/231558443-c6ce6abe-3ed2-45a5-be97-2db649875abc.png)
- lets follow **TCP  Stream** for this package ![flag](https://user-images.githubusercontent.com/83983701/231558488-1cf701a0-0954-4d68-84a6-44731354f1a1.png)
- Now we find the flag

### Thanks
