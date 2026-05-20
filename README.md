# PROTO2: Game Control System

A multi-platform game management and interactive event system that bridges Minecraft, Discord, Node-RED, and Digilab hardware (Raspberry Pi). The system introduces a strict hierarchical command structure, physical hardware overrides, live server events, and Discord-based gambling minigames that directly impact live gameplay.

---

## System Hierarchy

The system operates on three distinct authorization tiers to ensure controlled server management:

* **Digilab (Tier 1 - Emergency Override)**: Ignores all rules and permissions to execute immediate physical commands.
* **Discord (Tier 2 - Administrator)**: Reviews, confirms, or denies incoming user requests, and manages remote server controls.
* **Minecraft (Tier 3 - User)**: Submits command requests that remain pending until approved by a Discord administrator.

### Request Lifecycle Example
[Minecraft Player] ──(Sends Request)──> [Discord Bot] ──(Awaits Admin)──> [!confirm / !deny]
---

## Component Specifications

### Raspberry Pi & Node-RED
Node-RED acts as the central communication router connecting all software and hardware endpoints.
* **Routing Flows**: Handles bidirectional data mapping:
  * `Discord ➔ Node-RED ➔ Minecraft`
  * `Physical Buttons ➔ Node-RED ➔ Minecraft / Discord`
  * `Node-RED ➔ Hardware (LEDs / LCD / Dashboard)`
* **Alert System**: When a Minecraft request arrives, Node-RED blinks a physical LED and pushes the request details to the Digilab hardware display.
* **Ack Button**: Pressing a physical button turns off the alert LED and broadcasts an in-game message: *"Your request is currently being processed."*

### Digilab Hardware Interface
* **Inputs**: Physical buttons mapped directly to high-priority server commands for manual override execution.
* **Outputs**: An LCD screen showing the active request type and the username of the requesting player.

### Discord Bot
* **Gatekeeping**: Receives Node-RED payloads and prompts users with specific admin roles to approve or deny requests.
* **Feedback Loop**: Denied requests prompt the admin for a reason, which is sent directly back to the Minecraft in-game chat.
* **Remote Management**: Supports admin commands for remote player kicks, server restarts, item spawning, and entity distribution.

### System Dashboard
A web-based interface providing real-time telemetry and secondary controls:
* **Server Health**: Displays `playerCount`, `playerNames`, `isServerUp`, and error logs.
* **Queue Management**: Displays pending requests awaiting approval.
* **Fallback Controls**: Optional buttons to approve or deny requests if Discord or Digilab interfaces are offline.

---

## Dynamic Gameplay Features

### Live Events
Administrators can trigger or automate positive and negative environmental modifiers.

#### Malicious Events
* **Horde**: Spawns a dense cluster of hostile mobs at random coordinates around a randomly targeted player.
* **Big Loss**: Inflicts the target player with severe `Poison` and `Hunger` status effects.
* **Death**: An incredibly rare trigger that instantly kills the targeted player.

#### Beneficial Events
* **Make it Rain**: Drops a random quantity of random ores directly into the player's inventory.
* **Inspiration**: Grants the player a random assortment of high-tier positive status effects.
* **Another Chance**: Gifts the player a Totem of Undying.

### Discord Minigames
Players can gamble on Discord using classic casino games to alter their Minecraft reality. Winning triggers a **Beneficial Event**, while losing triggers a **Malicious Event**.
* **Supported Games**: Baccarat, Blackjack, Poker, and Dice.
