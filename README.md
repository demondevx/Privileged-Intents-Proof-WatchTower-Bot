# 📜 Privileged Intents Proof – WatchTower Security Bot

Hello Discord Team,

This document provides detailed proof of why WatchTower requires the Server Members Intent and Message Content Intent. WatchTower is a security-focused Discord bot designed to protect servers from raids, nukes, and abuse. WatchTower does NOT use AutoMod and does NOT require Presence Intent.

Each section below explains the features that rely on the intent and lists the exact proof videos/screenshots that will be provided.

────────────────────────
SERVER MEMBERS INTENT (GUILD_MEMBERS)
────────────────────────

WatchTower requires the Server Members Intent for its core security systems. Without this intent, the bot cannot safely identify users, enforce punishments, or protect servers from malicious actions.

Required for the following features:

🛡️ Anti-Raid System
- Detects members joining the server in real time
- Tracks join bursts and thresholds
- Automatically kicks members when raid conditions are met
- Logs anti-raid actions to the configured logging channel

This requires detecting member join events, identifying the joining user, and executing moderation actions.

🧨 Anti-Nuke Protection System
WatchTower actively monitors destructive actions using audit logs combined with guild member data.

Protected actions include:
- Role permission updates
- Dangerous role assignment
- Role rename / delete / create
- Channel rename / delete / create
- Emoji rename / delete
- Invite deletion
- Bot additions
- Server rename
- Server icon change
- Prune actions
- Ban & kick abuse

Server Members Intent is required to:
- Identify the executor of each action from audit logs
- Check whether the executor is the server owner
- Check whether the executor is whitelisted
- Respect Discord role hierarchy
- Apply punishments (ban, kick, clear roles)
- Skip punishment and reverts if the executor is the server owner or whitelisted
- Send accurate logs and security alerts

Without member objects, WatchTower cannot safely determine who performed an action or whether punishment should be applied.

👤 Verification System
- Assigns verification roles to members
- Controls access to channels after verification
- Tracks verified users

This requires fetching members and managing roles.

🧾 Whitelist System
- Allows server owners to whitelist trusted users, roles, and channels
- Prevents anti-nuke punishment for whitelisted entities

Requires member and role identification.

🔨 Moderation Commands
- Ban
- Kick
- Clear roles

These commands require fetching members, checking permissions, and respecting role hierarchy.

Summary for Server Members Intent:
WatchTower uses GUILD_MEMBERS to detect joins, identify action executors, enforce punishments, respect owner/whitelist immunity, manage verification roles, apply moderation actions, and protect servers from raids and nukes. Without this intent, WatchTower’s core security systems cannot function.

Proofs to be provided:
- [🎥 Video 1 - Anti-Raid locking channels on mass join Admin POV](https://youtube.com/shorts/V4cAa6rrGx8?feature=share)
-   [🎥 Video 2 - Anti-Raid locking channels on mass join](https://youtu.be/zEgEEfxERpw)
-   [📷 Screenshot 1 - Anti-raid Dm notification to server Owner](https://i.postimg.cc/8ckT7B08/antiraiddmnotification.png)
- [🎥 Video 3 Anti-Nuke detecting renaming emojis and punishing executor if the user isnt admin/whitelisted](https://youtube.com/shorts/RKNRm-iAvDM)
-   [📷 Screenshot 2 - Anti-Nuke detecting renaming emojis and punishing executor if the user isnt admin/whitelisted](https://i.postimg.cc/T1Phz6Gb/emojirename.png)
-   [🎥 Video 4 Anti-Nuke detecting deleting emojis and punishing executor if the user isnt admin](https://youtube.com/shorts/v8vRLjcCYmY)
-   [📷 Screenshot 3 - Anti-Nuke detecting deleting emojis and punishing executor if the user isnt admin/whitelisted](https://i.postimg.cc/vmQyqvGH/emojidelete.png)
-   [🎥 Video 5 Anti-Nuke detecting role creation and permission update and punishing executor if the user isnt admin](https://youtube.com/shorts/oKq4b0Hgxvk)
-   [📷 Screenshot 4 - Anti-Nuke detecting role creation and permission update and punishing executor if the user isnt admin/whitelisted](https://i.postimg.cc/fyxZqqSD/newrole.png)
- [🎥 Video 7 Anti-Nuke detecting bot add and punishing executor if the user isnt admin](https://youtube.com/shorts/rQQBQNDQt6o)
- [📷 Screenshot 6 - Whitelisted user bypassing punishment]([https://i.postimg.cc/x8dyth46/massmention.png](https://i.postimg.cc/vBCftTfX/Whitelisted-user-bypassing-punishment.png))
- [🎥 Video 8 -  Verification System Admin](https://youtube.com/shorts/kyYSA46rmog)
-   [🎥 Video 9 - Verification System Member](https://youtube.com/shorts/4Jsz4pfyhII)
- [🎥 Video 10 -  Moderation kick mute](https://youtube.com/shorts/UFpKBW0VZ3E)
-   [🎥 Video 11 - Moderation ban](https://youtube.com/shorts/O-MiNNTx_jI)

────────────────────────
MESSAGE CONTENT INTENT
────────────────────────

WatchTower requires Message Content Intent only for security detection and command handling.

📢 Anti-Mass Mention Protection
- Detects excessive mentions in a single message
- Counts only unique mentions
- Ignores reply mentions
- Triggers punishment only when the configured limit is exceeded

This requires reading message content and mention data.

🧠 Prefix Command Support
WatchTower supports prefix-based moderation commands, which require reading message content to parse commands.

Privacy & Safety:
- WatchTower does NOT read or store general user messages
- Message content is processed only to detect security violations
- No messages are logged, saved, or analyzed beyond the event trigger

Proofs to be provided:
- [🎥 Video 6 Anti-Nuke detecting mass mention and punishing executor if the user isnt admin](https://youtu.be/KxsQBRGztsM)
-   [📷 Screenshot 5 - Anti-Nuke detecting mass mention and punishing executor if the user isnt admin](https://i.postimg.cc/x8dyth46/massmention.png)
-  [📷 Screenshot 7 - Logging System](https://i.postimg.cc/7LmN0qKd/Logging.png)
-  [📷 Screenshot 8 - Owner/Whitelist Bypass](https://i.postimg.cc/QtzkY0ZD/owner-admin-whitelist.png)
-  [📷 Screenshot 9 - DM Aleart's](https://i.postimg.cc/xjkWfZCj/dm.png)

────────────────────────
PRESENCE INTENT
────────────────────────

WatchTower does NOT use presence data.
- No activity tracking
- No online/offline status usage
- No game or status detection

Presence Intent is NOT requested.

────────────────────────
DATA STORAGE & PRIVACY
────────────────────────

- WatchTower stores only minimal, non-sensitive data required for security features
- Stored data includes:
  - Guild IDs
  - User IDs
  - Role IDs
  - Channel IDs
  - Whitelist entries
  - Anti-Nuke configuration
  - Anti-Raid configuration
- No message content is stored
- No personal user data is sold or shared
- Data is stored securely using MongoDB
- Server owners can delete all data using the /factory-reset command
- Data exists only while the bot is present in the server

────────────────────────
CONTACT & TRANSPARENCY
────────────────────────

- Developer Contact: [Discord ID](https://discord.com/users/555652788592443392)
- Support Server: [Support Server](https://discord.gg/puBgWvnmjU)
- Privacy Policy: [PRIVACY_POLICY_LINK](https://github.com/demondevx/WatchTower/blob/main/PRIVACY_POLICY.md)
- Email us : [support@demondev.org](mailto:support@demondev.org)

────────────────────────
FINAL INTENT REQUEST SUMMARY
────────────────────────

✔ Server Members Intent — REQUIRED
✔ Message Content Intent — REQUIRED (minimal usage)
❌ Presence Intent — NOT REQUIRED
❌ Discord AutoMod — NOT USED

WatchTower is a security-only bot. These intents are strictly required to protect Discord servers from raids, abuse, and destructive actions.
