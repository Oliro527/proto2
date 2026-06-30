# 🎮 Minecraft Automation System

This project connects Minecraft, Discord, and Node-RED to create an interactive game control system. It also supports Raspberry Pi hardware like buttons, LEDs, and an LCD screen. The goal is to control the Minecraft server, add fun features, and interact with the game from outside (Discord or hardware).

## 🚀 Features

### 🎲 Dice Game (Discord + Minecraft)
Play a dice game and get rewards or punishments in Minecraft.

### 💎 Daily Reward System
Players can collect diamonds once every 24 hours.

### 📊 Server Status Check
See if the server is online and how many players are connected.

### ⚙️ Admin Commands from Discord
Send Minecraft commands directly from Discord (admin only).

### 🆘 Emergency Button
Instantly kick all players using a physical button.

### 🔛 Server Start / Stop (Hardware Control)
Control the server using Raspberry Pi buttons.

### 🌦️ Weather Integration
Real-world weather changes the Minecraft weather.

### 🖥️ LCD Display Output
Shows information like game results, server status, or weather.

### 💡 LED Effects
LEDs react to events like games or alerts.

## 💬 Commands

### Player Commands
* `$dice` → Play the dice game
* `$daily <name>` → Get daily reward
* `$status` → Check server status
* `$help` → List all commands

### Admin Commands
* `!<command>` → Send Minecraft commands
* *Example:* `!gamemode creative`

## 🎲 Dice Game

You roll against a dealer. 

**Possible results:**
* **✅ Win:** Rewards (items, effects)
* **❌ Lose:** Penalties (poison, mobs, etc.)
* **🤝 Draw:** No effect

## ⚡ Hardware (Raspberry Pi)

### Buttons
* Start / stop server
* Emergency kick
* Trigger actions

### LCD
* Displays messages and info

### LEDs
* Show activity and alerts

## 🌍 Weather System

Uses an online weather API.

**Example locations included:**
* Luxembourg
* Japan

**Effects:**
* Updates Minecraft weather (clear, rain, thunder)
* Shows temperature on dashboard
* Displays data on LCD

## 🛠️ Setup

### Requirements
* Node-RED
* Minecraft server with RCON enabled
* Discord bot
* Raspberry Pi (optional)

### Required Node-RED Modules
Install the following nodes:
* `node-red-contrib-discord-advanced`
* `@tomsith/node-red-contrib-minecraft`
* `node-red-node-pi-gpio`
* `node-red-contrib-raspi5-lcd-16x2`
* `@flowfuse/node-red-dashboard`
* `node-red-node-tail`

## ▶️ How to Run

1. Import the project JSON into Node-RED.
2. Configure your credentials:
   * Discord bot token
   * RCON server IP and password
3. Deploy the flow.
4. Start the Minecraft server.

## 🔐 Notes
* Admin commands are restricted to authorized users.
* Daily rewards have a 24-hour cooldown.
* Hardware features only work when hosted on a Raspberry Pi.

## 📌 Overview
This system connects everything together:
* **Discord** → User interaction
* **Node-RED** → Logic and automation
* **Minecraft** → Game actions
* **Raspberry Pi** → Physical control
Authors: Tiago & Ronny
