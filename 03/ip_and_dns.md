# ip and dns

## ip and dns in a nutshell


    An IP address in the IPV4 standard has four numbers separated by three decimals, as in: 70.74.251.42
    An IP address in the IPV6 standard has eight hexadecimal numbers (base-16) separated by colons, as in 2001:0cb8:85a3:0000:0000:8a2e:0370:7334. Because IPV6 is still a very new standard, we'll concentrate on the more common IPV4 for this article.
    Each number in an IPV4 number is called an "octet" because it's a base-10 equivalent of an 8-digit base-2 (binary) number used in routing network traffic. For example, the octet written as 42 stands for 00101010. Each digit in the binary number is the placeholder for a certain power of two from 2 to 27, reading from right to left. That means that in 00101010, you have one each of 21, 23 and 25. So, to get the base-10 equivalent, just add 21 + 23 + 25 = 2 + 8 + 32 = 42.
    There are only 256 possibilities for the value of each octect: the numbers 0 through 255.
    Certain addresses and ranges are designated by the IANA as reserved IP addresses, which means they have a specific job in IP. For example, the IP address 127.0.0.1 is reserved to identify the computer you're currently using. So, talking to 127.0.0.1 is just talking to yourself [sources: Cisco, Lammele].
`<source>:`[](https://computer.howstuffworks.com/dns1.htm)
`<cli>:` inpconfig, nslookup
