# Privacy Policy

**Last updated: October 6, 2026**

This Privacy Policy describes how **Dymo** ("the Bot", "we", "us") collects, uses, stores, and protects information when you use our Discord bot and web dashboard. We are committed to protecting your privacy and handling all data with transparency and care.

---

## 1. Information We Collect

### 1.1 Data Collected Automatically

When Dymo is active in your Discord server, we may collect the following through the Discord Gateway and API:

| Data Type | Purpose | Stored? |
|---|---|---|
| Server (Guild) ID, name, owner ID | Server identification and configuration | ✅ Yes – MongoDB |
| User IDs (members) | Moderation records, exemption lists | ✅ Yes – MongoDB |
| Role information | Anti-nuke protection, seal enforcement | ✅ Yes – MongoDB |
| Member join/leave events | Anti-escape enforcement for active punishments | ❌ No – processed in-memory only |
| Message content | Deleted/edited log display, scam detection, spam analysis | ❌ No – RAM cache only (≤20 min) |
| Audit Log entries | Identifying actors in anti-nuke events | ❌ No – read-only, not stored |
| Punishment records | Active seal/sseal enforcement | ✅ Yes – MongoDB |

### 1.2 Dashboard Authentication

Our web dashboard uses **Discord OAuth2** for authentication. During login, we receive your Discord user ID, username, avatar, and guild list. This data is stored only in an encrypted server-side session and is discarded upon logout or session expiry. We do not store OAuth2 tokens beyond the active session.

### 1.3 Data We Do NOT Collect

We explicitly do **not** collect:

- Email addresses
- Passwords or credentials of any kind
- Payment information
- Private/direct message (DM) content — the bot only operates within servers
- Voice channel audio or metadata
- Any data from servers the bot is not a member of

---

## 2. How We Use Your Data

Data collected by Dymo is used **exclusively** for bot operation:

- **Server configuration** – Storing your chosen settings (auto-mod rules, anti-nuke thresholds, log channels, etc.) so they persist across bot restarts.
- **Moderation enforcement** – Maintaining active punishment records, exemption lists, and admin hierarchies.
- **Security features** – Detecting destructive server actions (mass bans, role deletions, webhook spam) and automatically reverting them in real time.
- **Message logging** – Temporarily caching message content in RAM to provide deleted/edited message logs to your server moderators. This cache is never written to disk.
- **Anti-escape enforcement** – Detecting when a punished member leaves and rejoins your server, and automatically re-applying their punishment.

We do **not** use your data for advertising, user profiling, analytics sales, or any commercial purpose.

---

## 3. Message Content Intent

Dymo uses Discord's **Message Content Privileged Intent** solely to:

1. Cache message content in-memory (maximum 800 messages per server, purged after 20 minutes) so that moderators can see what was written in deleted or edited messages.
2. Scan message text against a list of known scam/phishing domains to protect server members from malicious links.
3. Analyze message frequency and patterns for spam detection.

Message content is processed exclusively in RAM and is **never written to a database, log file, or any external service**. Messages from bot accounts, users with the `Manage Messages` or `Administrator` permission, and channels manually excluded by administrators are **excluded** from all processing.

---

## 4. Server Members Intent

Dymo uses Discord's **Server Members Intent** solely to:

1. Receive `on_member_join` events to re-apply active punishments when a previously punished member rejoins (anti-escape).
2. Receive `on_member_update` events to detect and revert unauthorized removal of enforcement roles (seal/sseal).
3. Accurately resolve member information for moderation commands that require looking up a member by name or ID.
4. Maintain an up-to-date member list for anti-nuke threat detection.

Member data processed via this intent is used **only** for the moderation and security purposes described above.

---

## 5. Data Storage and Security

All persistent data is stored in a **MongoDB** database with the following security measures:

- **Encryption at rest**: The database volume is encrypted using AES-256.
- **Encryption in transit**: All connections between the bot, dashboard, and database use TLS 1.3.
- **Access control**: Database credentials are stored as environment variables and are never committed to version control. Access is restricted to bot and dashboard services only.
- **Session security**: Dashboard sessions are encrypted with a secret key and transmitted over HTTPS only.
- **Minimal surface**: The bot does not expose any public API endpoint that reads or writes user data without authentication. The internal dashboard API requires a shared secret for every write operation.
- **Secret management**: All credentials (Discord token, MongoDB URI, OAuth2 secrets) are managed via environment variables with no hard-coded values in source code.

We are committed to industry-standard security practices and will notify affected users promptly in the event of a data breach.

---

## 6. Data Retention

| Data | Retention Period |
|---|---|
| Message content cache | ≤20 minutes in RAM; immediately evicted on bot restart |
| Active punishment records | Until punishment is lifted (manually or by expiry) |
| Server configuration | Deleted within 30 days of bot removal from server |
| Guild membership record | Deleted immediately when bot leaves/is removed from server |
| Dashboard session | Deleted on logout or after session expiry (default 24 hours) |

---

## 7. Data Sharing

We **do not** sell, rent, trade, or share your personal data with third parties, except:

- **Discord Inc.**: Interaction with the Discord API is necessary for the bot to function. Data shared with Discord is governed by [Discord's Privacy Policy](https://discord.com/privacy).
- **Hosting and infrastructure providers**: Our database and bot hosting infrastructure providers process data on our behalf under appropriate data processing agreements. These providers do not have access to data for their own purposes.
- **Legal requirements**: We may disclose data if required by applicable law or a valid legal order.

---

## 8. Your Rights

You have the right to:

- **Access**: Request a copy of the data we hold about you.
- **Deletion**: Request deletion of your data. For server-level data (configuration, punishment records), the server owner may also request deletion.
- **Correction**: Request correction of inaccurate data.
- **Objection**: Object to data processing where we rely on legitimate interests.
- **Removal**: You may remove Dymo from your server at any time. All server-level data will be deleted within 30 days of removal.

To exercise these rights, contact us via our official Discord support server or GitHub repository.

---

## 9. Children's Privacy

Dymo is not directed to children under the age of 13 (or higher where required by local law). We do not knowingly collect data from children. If you believe a child under 13 has used the bot in violation of Discord's Terms, please contact us.

---

## 10. Changes to This Policy

We may update this Privacy Policy at any time. Changes will be reflected by updating the "Last updated" date at the top. We will make reasonable efforts to notify server administrators of material changes. Continued use of Dymo after changes are posted constitutes acceptance.

---

## 11. Contact

If you have any questions, concerns, or requests regarding this Privacy Policy or your data, please reach out to the Dymo development team through our official Discord support server or GitHub repository.
