# STP-2 Task

## Gotham Hustle
### Flag Part 1 – Command History
I used cmdscan to check the command history of the system. One of the commands contained a Base64-encoded string. After decoding it, I got the first part of the flag:
- bi0sctf{w3lc0m3_

### Flag Part 3 – Notepad Memory & Web Link
While extracting strings from Notepad memory, I found a suspicious web link. Opening that link revealed another Base64-encoded string, which decoded to:
- h0p3_th15_

### Flag Part 4 – Notepad Process Dump
I dumped the Notepad process using procdump and ran strings on it. Inside the output, I found another Base64 string, which decoded to:
- b3n3f175_y0u_

### Flag Part 5 – Password-Protected RAR File
From filescan, I found a file called flag5.rar on the Desktop.
Using hashdump, I extracted the user password hash and cracked it to get:
- batman
Using this password, I extracted the RAR file and decoded the final Base64 string:
- m0r3_13337431}

*Was not able to find the part 2 of the flag*

## Cryptography
### LWE Maze – Path Discovery
- The maze structure was provided as a graph in graph.json.
- Each node represented a maze state and each edge represented a valid move.
- A graph traversal algorithm (BFS/DFS) was used to find the valid path.
- This ensured the shortest and correct route to the final node.``
- The final path obtained was: 
```
[0, 15, 1, 16, 2, 17, 3, 18, 4, 19, 5, 20, 6, 21, 7, 22, 8, 23, 9, 24,
 10, 25, 11, 26, 12, 27, 13, 28, 14, 29]
```
### LWE Error Magnitude Extraction
- Each correct maze move returned a numeric value from the server.
- These values represented the absolute magnitude of the LWE error.
- By traversing the full correct path, all error values were collected.
- The complete list of extracted LWE error magnitudes is:
```
[265, 622, 38, 716, 722, 308, 996, 799, 742, 337,
 927, 698, 626, 969, 330, 126, 321, 20, 271, 839,
 175, 399, 752, 989, 666, 629, 271, 400, 311, 840,
 821, 821, 17, 978, 488, 781, 74, 818, 849, 903,
 776, 142, 505, 951, 582, 638, 222, 872, 427, 165,
 307, 209, 475, 970, 748, 814, 69, 213, 27, 742,
 744, 566, 262, 852, 740, 309, 997, 502, 995, 434,
 405, 193, 257, 953, 924, 678, 232, 226, 560, 414,
 584, 579, 767, 810, 51, 894, 446, 281, 761, 908,
 715, 787, 722, 270, 94, 169, 474, 431, 292, 346]

```

*I was only able to reach till here was nto able to find the required s vector to get the flag*