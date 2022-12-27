# Protocol
The protocol is string based. Every packet must and will end with a newline (`\n`).  
Every argument in a packet is pipe seperated.  
E.g: `pos|5|3|0|1|1|1`

## Packet structure
The general packet structure looks like this:  
`<packetType>|<...arguments>`  
E.g: `game|15|10|7|9`  
Where `game` is the packetType, `15` the first argument, `10` the second, `7` the third and `9` the fourth.

## Packet types

### modt
The motd packet is sent by the server when you connect to it. motd means "Message of the day".

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `string: message of the day`                           |
| **example**   | `motd|Hello how are you? :)`                           |

### join
The join packet is the first packet the client has to send to the server when connecting. Remember the password otherwise you cant use the username again!

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | client                                                 |
| **arguments** | `string: username`<br />`string: password`             |
| **example**   | `join|Cool Guy|mysupersecret`                          |

### error
The error packet is sent by the server if something went wrong.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `string: error message`                                |
| **example**   | `error|INVALID_USERNAME`                               |

### game
The game packet is sent by the server to inform the client about the current running game.<br />It contains information about the map size and the goal position.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `number: map width`<br />`number: map height`<br />`number: x postition of the goal`<br />`number: y position of the goal` |
| **example**   | `game|10|10|7|9`                                       |

### pos
The pos packet is sent by the server to inform the client about its position and walls.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `number: x position of the client`<br />`number: y position of the client`<br />`0 or 1, depending on whether there is a wall above`<br />`0 or 1, depending on whether there is a wall to the right`<br />`0 or 1, depending on whether there is a wall below`<br />`0 or 1, depending on whether there is a wall to the left` |
| **example**   | `pos|5|3|0|1|1|1`                                      |

### move
The move packet is sent by the client to decide where to walk.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | client                                                 |
| **arguments** | `string: up, right, down or left`                              |
| **example**   | `move|up`                                              |

### chat
The chat packet is sent by the client to send a cool chat message :>.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | client                                                 |
| **arguments** | `string: chat message`                                         |
| **example**   | `chat|I am so cool B)`                                 |

### win
The win packet is sent by the server to inform the client they won.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `number: total wins`<br />`number: total loses`        |
| **example**   | `win|1|20`                                             |

### lose
The lose packet is sent by the server to inform the client they lost.

|               |                                                        |
|---------------|--------------------------------------------------------|
| **sender**    | server                                                 |
| **arguments** | `number: total wins`<br />`number: total loses`        |
| **example**   | `lose|1|20`                                            |