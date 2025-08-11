# Session 3 Detailed Plan - AI Sprint Program

## Session Overview
**Format:** Interactive workshop with gaming demonstration and ZeroTier network setup  
**Objective:** Focus on ZeroTier virtual networking with teacher-hosted game demonstration

---

## Pre-Session Setup (30 mins prior)

### Installation/Technical Support
**Format:** Individual assistance and troubleshooting

#### Activities:
- **ZeroTier Installation Help**
  - Confirm ZeroTier client is installed on all devices
  - Help participants with installation issues
  - Verify account creation completion
  - Test basic ZeroTier functionality

#### Preparation Checklist:
- [ ] Verify ZeroTier installation on all participant devices
- [ ] Create ZeroTier networks for group activities
- [ ] Test TOSIOS online instance accessibility
- [ ] Prepare teacher-hosted TOSIOS server
- [ ] Test ZeroTier network configurations

---

## Detailed Agenda

### 1. Brief Review of Session 2 Topics

#### Activities:
- **Session 2 Recap**
  - Quick review of NotebookLM vs PKC comparison
  - Recall local-first principles discussion
  - Connect previous concepts to today's focus on virtual networking with ZeroTier

#### Interactive Element:
- Brief discussion: "What do you remember about local-first principles from last session?"

---

### 2. Demonstration of Online TOSIOS

#### Activities:
- **Game Introduction:**
  - TOSIOS: The Open-Source IO Shooter
  - Browser-based multiplayer battle royale game
  - Simple mechanics, perfect for networking demonstration

- **Online Gaming Experience:**
  - Guide participants to join the online instance
  - Ask them to join the same game room
  - Play a few rounds together

#### Interactive Element:
- **Group Discussion:**
  - "How easy was it to join and play?"
  - "What happens when your internet is slow?"
  - "Where do you think the game server is located?"
  - Highlight that this is an online, server-based game

---

### 3. Introducing Teacher-Hosted Game Server

#### Activities:
- **Introducing Teacher-Hosted Game:**
  - "Now we'll play the same game but on a server hosted by me"
  - "This server is running on my machine, not on a public cloud"

- **Server Demonstration:**
  - Show TOSIOS instance running on teacher's machine
  - Explain it's running on the local network, not a remote server
  - Ask participants to try joining the game directly
  - **Expected result:** They cannot connect

#### Interactive Element:
- **Group Problem-Solving:**
  - "Why can't we connect to the teacher's game?"
  - Discuss network isolation between different networks
  - "This is where ZeroTier comes in!"

---

### 4. Brief Explanation of ZeroTier

#### Activities:
- **What is ZeroTier?**
  - Virtual networking solution
  - Creates secure connections between devices
  - Works across different physical networks
  - Enables peer-to-peer connections when possible

- **How ZeroTier Enables Connected Gaming:**
  - Creates a virtual LAN for devices to connect
  - Devices can communicate as if on the same network
  - Connects participants across different physical networks
  - Secures communications between devices

---

### 5. Demonstration of Joining ZeroTier Network

#### Activities:
- **Group Network Setup:**
  - Add all participants to a single ZeroTier network
  - Provide network ID and join instructions
  - Explain how joining the network works

- **ZeroTier Network Joining:**
  - Guide participants to join the ZeroTier network
  - Teacher authorizes participants in the network
  - Verify successful network connections
  
#### Interactive Element:
- Group collaboration for successful ZeroTier connection
- Experiencing the power of virtual networking

---

### 6. Further Explanation of Local-First Principles

#### Activities:
- **What Just Happened:**
  - "You just connected to a teacher-hosted game server"
  - "The game server is running on the teacher's machine, not in the cloud"
  - "This is virtual networking in action"

- **ZeroTier Benefits in Practice:**
  - **Control:** Administrator decides who joins the network
  - **Privacy:** Network traffic stays within your virtual network
  - **Connectivity:** Works across different physical networks
  - **Simplicity:** No need for complex network configuration
  - **Security:** Encrypted connections between all devices

- **Real-World Applications:**
  - File sharing within teams
  - Local development environments
  - Private communication networks
  - Self-hosted applications and services

---

### 7. Deeper Dive into ZeroTier Technology

#### Activities:
- **ZeroTier Technical Overview:**
  - How ZeroTier creates virtual networks
  - Peer-to-peer vs. relayed connections
  - Network controllers and authorization

- **ZeroTier Configuration:**
  - Managing networks and devices
  - Setting up routes and rules
  - Security considerations

- **ZeroTier Use Cases:**
  - Remote team collaboration
  - Connecting IoT devices
  - Gaming and entertainment
  - Enterprise networking

---

### 8. Summary and Next Steps

#### Activities:
- **Key Takeaways:**
  - ZeroTier creates secure virtual networks across locations
  - Virtual networking enables connections without public servers
  - ZeroTier offers both convenience and control
  - These networking skills apply to many other applications

- **Tools Needed for Session 4:**
  - **Windsurf IDE Installation**
    - Download from windsurf.codeium.com
    - Install appropriate version for your operating system
  
  - **Docker Installation**
    - Download Docker Desktop for your platform
    - Complete installation and setup

#### Interactive Element:
- Quick feedback: "What surprised you most about local networking?"

---

## Materials Needed:
- ZeroTier network for group activity
- TOSIOS online instance URL
- Teacher-hosted TOSIOS server
- ZeroTier administration dashboard
- ZeroTier network ID and join instructions
- Installation guides for Windsurf and Docker (for next session)

---

## Success Metrics:
- Participants understand the basics of virtual networking
- Participants successfully join the ZeroTier network
- Participants connect to the teacher-hosted game server through ZeroTier
- Participants grasp basic networking concepts
- Participants understand how virtual networks enable direct connections
- Participants are prepared for Windsurf and Docker installation for Session 4
