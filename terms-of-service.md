# Terms of Service

**Last updated: October 6, 2026**

Welcome to **Dymo** ("the Bot", "we", "us"). By adding Dymo to your Discord server or interacting with it, you agree to the following Terms of Service. If you do not agree, please remove the bot from your server immediately.

---

## 1. Acceptance of Terms

By inviting Dymo to your Discord server, you confirm that you are at least 13 years of age (or the minimum age required in your country) and that you accept these Terms in full. Server administrators who invite the bot take responsibility for ensuring compliance with these Terms within their communities.

---

## 2. Description of Service

Dymo is a multi-purpose Discord bot providing the following features:

- **Moderation** – Commands for muting, kicking, banning, purging messages, and managing members.
- **Anti-Nuke** – Automated real-time protection detecting and reverting destructive server actions (mass bans, role deletions, channel deletions, webhook creation, permission changes). Violations trigger immediate automated penalties and Audit Log–based recovery.
- **Auto-Moderation** – Automatic detection of spam, scam/phishing links, and logging of deleted/edited messages for server transparency.
- **Seal System** – A role-based restriction mechanism ("seal" and "super-seal") that removes all roles from a member to prevent interaction across all channels. The system self-heals: it re-applies punishments if someone leaves and rejoins, and re-creates enforcement roles if they are deleted.
- **Admin Management** – A hierarchical permission system allowing server owners to delegate moderation responsibilities safely.
- **Web Dashboard** – A companion web application allowing server administrators to configure all features through a graphical interface.

---

## 3. User Conduct

You agree **not** to use Dymo to:

- Violate Discord's [Terms of Service](https://discord.com/terms) or [Community Guidelines](https://discord.com/guidelines).
- Harass, threaten, defame, or harm any individual or group.
- Distribute spam, phishing links, malware, or any other malicious content.
- Attempt to reverse-engineer, exploit, or abuse the bot's systems.
- Use the bot for any illegal activity under applicable laws.

We reserve the right to deny service to any server or user at our discretion.

---

## 4. Data Collection and Usage

Dymo collects and processes the minimum data necessary to operate its features. Specifically:

- **Guild (Server) information**: Server ID, name, owner ID — used to maintain per-server configuration.
- **Member information**: User IDs, role lists, join/leave events — used strictly to enforce moderation rules (e.g., anti-nuke exemptions, seal punishments, anti-escape re-application).
- **Message content**: Message text is cached temporarily in-memory (max 20 minutes, up to 800 messages per server) for the purpose of displaying deleted/edited message logs to server moderators. Message content is **never written to disk or stored in a database**.
- **Punishment records**: Active seal/sseal records (user ID + server ID + timestamp + reason) are stored in MongoDB to ensure persistence across bot restarts and to prevent punishment evasion.
- **Audit Log data**: Read-only access to Discord's Audit Log is used to identify the actor behind destructive actions. No Audit Log data is stored.

We do **not** sell, share, or monetize any user data. Data is used solely for bot functionality.

---

## 5. Data Retention

- **Message content cache**: Purged automatically after 20 minutes or upon server capacity being reached. Never persisted to storage.
- **Punishment records**: Retained until the punishment is lifted (manually or via expiry). Deleted immediately upon bot removal from a server.
- **Server configuration**: Retained for 30 days after bot removal to allow easy re-invitation, then permanently deleted.

---

## 6. Privileged Intents

Dymo requires the following Discord Privileged Gateway Intents:

- **Server Members Intent**: Required to detect member join/leave events for anti-escape enforcement (re-applying seal on rejoin), syncing the member list for moderation commands, and maintaining the anti-nuke exemption list.
- **Message Content Intent**: Required to read message content for deleted/edited message logging, scam/phishing link detection, and spam analysis.

These intents are used exclusively for the stated purposes and in compliance with Discord's Developer Policy.

---

## 7. Disclaimer of Warranties

Dymo is provided "as is" without any warranty of any kind, express or implied. We do not guarantee uninterrupted uptime, error-free operation, or that the bot will meet your specific requirements. Automated moderation actions (anti-nuke, auto-mod) are best-effort and may occasionally produce false positives.

---

## 8. Limitation of Liability

To the maximum extent permitted by law, Dymo and its developers shall not be liable for any indirect, incidental, special, or consequential damages arising from your use of or inability to use the bot, including but not limited to data loss, server disruption, or unauthorized access.

---

## 9. Modifications to Terms

We reserve the right to update these Terms at any time. Continued use of Dymo after changes are posted constitutes acceptance of the revised Terms. We will attempt to notify server administrators of significant changes.

---

## 10. Termination

We may suspend or terminate access to Dymo for any server or user that violates these Terms without prior notice. You may also remove the bot from your server at any time, which will terminate your use of the service.

---

## 11. Governing Law

These Terms are governed by applicable laws. Disputes shall be resolved through good-faith negotiation. If a dispute cannot be resolved informally, it shall be subject to binding arbitration.

---

## 12. Contact

For questions, reports, or takedown requests regarding these Terms, please contact the Dymo development team through our official Discord support server or GitHub repository.
