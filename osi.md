<img width="1914" height="1118" alt="image" src="https://github.com/user-attachments/assets/9ddfc2c5-eacd-4ddb-96c9-914b1a3045bc" />
A simple way to remember it:

**"All People Seem To Need Data Processing"**

| Layer | Name         |
| ----- | ------------ |
| 7     | Application  |
| 6     | Presentation |
| 5     | Session      |
| 4     | Transport    |
| 3     | Network      |
| 2     | Data Link    |
| 1     | Physical     |

---

# Layer 7 – Application
<img width="1895" height="1211" alt="image" src="https://github.com/user-attachments/assets/bc7f4beb-abc9-48ac-ad5a-c19fdeb3dfa7" />
This is the layer closest to the user.

It provides network services to applications like:

* Web browsers
* Email clients
* File transfer software

### Examples

* HTTP/HTTPS
* FTP
* SMTP
* DNS

### Example

When you open Google in Chrome, the request starts here.

---

# Layer 6 – Presentation
<img width="1924" height="593" alt="image" src="https://github.com/user-attachments/assets/c3b99450-6ad6-40cb-8175-e7f7d1944283" />
Responsible for:

* Data formatting
* Encryption
* Compression

### Examples

* SSL/TLS encryption
* JPEG images
* MP3 audio

### Example

When you visit an HTTPS website, encryption happens here.

Think:

> "How should the data be presented?"

---

# Layer 5 – Session
<img width="1932" height="936" alt="image" src="https://github.com/user-attachments/assets/c4ad0b8a-607c-459c-852a-dd5c4db8329b" />
Responsible for:

* Starting communication
* Maintaining communication
* Ending communication

### Example

When you're in a Zoom meeting, this layer keeps the session active.

Think:

> "Who is talking and for how long?"

---

# Layer 4 – Transport
<img width="1926" height="1217" alt="image" src="https://github.com/user-attachments/assets/f5fb5a8f-1960-44e6-9cbc-b20b66f7651c" />
<img width="1803" height="722" alt="image" src="https://github.com/user-attachments/assets/2e8a6e64-f965-4708-8f37-b87c73d15728" />
<img width="1858" height="1192" alt="image" src="https://github.com/user-attachments/assets/d58aa31d-73f9-4538-a5fc-56e8137b6bb4" />

Responsible for:

* Reliable delivery
* Error checking
* Flow control

### Protocols

* TCP
* UDP

### Example

#### TCP

* Reliable
* Used for websites, emails

#### UDP

* Faster
* Used for gaming and streaming

Think:

> "Did all the data arrive correctly?"

---

# Layer 3 – Network
<img width="1900" height="774" alt="image" src="https://github.com/user-attachments/assets/319573fe-e4a4-43b8-9bc0-56c5f27a95be" />
Responsible for:

* Routing
* Logical addressing

### Protocol

* IP (Internet Protocol)

### Device

* Router

### Example

Your packet travels from Missouri to California using routers.

Think:

> "Where should this packet go?"

---

# Layer 2 – Data Link
<img width="1880" height="725" alt="image" src="https://github.com/user-attachments/assets/08e92fc5-ed08-4838-89e5-c529d78fe20f" />
Responsible for:

* MAC Addresses
* Error detection
* Communication within the same network

### Device

* Switch

### Example

A switch decides which computer on your local network should receive the frame.

Think:

> "Which device on this local network gets the data?"

---

# Layer 1 – Physical
<img width="1868" height="1063" alt="image" src="https://github.com/user-attachments/assets/7aba0f10-bdce-4163-bc41-5d04d35db709" />
Responsible for transmitting actual bits.

### Examples

* Ethernet cables
* Fiber optic cables
* Wi-Fi radio signals

### Data

Only:

```
0s and 1s
```

### Example

Electrical signals travel through a cable.

Think:

> "How do the bits physically travel?"

---

# Real Example: Opening Google

When you type **[www.google.com](http://www.google.com)**:

### Layer 7 (Application)

Browser creates HTTP request.

⬇

### Layer 6 (Presentation)

Data gets encrypted using HTTPS/TLS.

⬇

### Layer 5 (Session)

Session established with Google.

⬇

### Layer 4 (Transport)

TCP breaks data into segments.

⬇

### Layer 3 (Network)

IP address added.

⬇

### Layer 2 (Data Link)

MAC address added.

⬇

### Layer 1 (Physical)

Bits sent through Wi-Fi or cable.

---

# Encapsulation (Very Important)

As data moves **down** the OSI model:

Each layer adds its own information (header).

```
Application Data
      ↓
Transport Header + Data
      ↓
Network Header + Data
      ↓
Data Link Header + Data
      ↓
Physical Transmission
```

This process is called:

✅ **Encapsulation**

At the receiving computer, the headers are removed layer by layer.

This is called:

✅ **Decapsulation**

---

# Devices at Each Layer

| Layer          | Device              |
| -------------- | ------------------- |
| 7 Application  | Browser/Application |
| 6 Presentation | SSL/TLS             |
| 5 Session      | Session Manager     |
| 4 Transport    | Firewall (L4)       |
| 3 Network      | Router              |
| 2 Data Link    | Switch              |
| 1 Physical     | Cable, Hub, Wi-Fi   |

---

### Cybersecurity Interview Tip

Interviewers often ask:

**"Which OSI layer does a router work on?"**
➡️ Layer 3 (Network)

**"Which OSI layer does a switch work on?"**
➡️ Layer 2 (Data Link)

**"HTTPS belongs to which layer?"**
➡️ Layer 7 (Application) using Layer 6 encryption concepts.

For TryHackMe and Security+, the most tested layers are **1, 2, 3, 4, and 7**, so focus extra attention on those.
