# pBot

# Bot design, features, and systems

## **I. Core Modules/Cogs (Always On)**

   *   **Bot Management:**
        *   **Features:** Bot status, uptime, latency monitoring, resource usage stats, error logging, automatic restart on crash.
        *   **Commands:**
            *   `/status`: View bot status and server information.
            *   `/ping`: Check the bot's latency.
            *   `/info`: Get detailed information about the bot.
            *   `/help`: Access the help menu (dynamically generated based on loaded modules).
            *   `/invite`: Get an invite link to add the bot to other servers.
            *   `/support`: Get a link to the bot's support server.
            *   `/prefix <new_prefix>` (Admin): Change the bot's command prefix for the server.
   *   **User Management:**
        *   **Features:** User profile tracking (join/leave times, message count, roles, etc.), customizable welcome/goodbye messages (with embeds and variable support like `{user}`, `{server}`, `{memberCount}`), automatic role assignment on join.
        *   **Commands:**
            *   `/userinfo <@user>`: Get information about a user (or yourself if no user is specified).
            *   `/serverinfo`: Get information about the current server.
            *   `/whois <@user>`: Alias for `userinfo`
            *   `/avatar <@user>`: Display a user's avatar.

## **II. Customizable Modules/Cogs (Toggleable)**

   1.  **Moderation:**
        *   **Features:**
            *   **Automated Moderation (AutoMod):** Keyword filtering (with customizable sensitivity levels and whitelist/blacklist), spam detection (duplicate messages, rapid posting, excessive mentions), link filtering (with whitelist/blacklist), invite link detection and blocking, anti-raid protection (detect and react to sudden influx of users).
            *   **Manual Moderation Actions:** Kick, ban (with time limits), mute (with time limits), warn, purge messages.
            *   **Logging:** Detailed logging of all moderation actions, including who took the action, when, and why (with customizable channels for different log types).
            *   **Role-Based Permissions:** Fine-grained control over which roles can use which moderation commands.
            *   **Case System:**  Keep track of user infractions, building a history for better decision-making.
        *   **Commands:**
            *   `/kick <@user> <reason>`
            *   `/ban <@user> <duration> <reason>`
            *   `/mute <@user> <duration> <reason>`
            *   `/unmute <@user>`
            *   `/warn <@user> <reason>`
            *   `/purge <number> <@user>` (Purge messages from a user or channel)
            *   `/slowmode <seconds>`: Set the slowmode for a channel.
            *   `/lockdown <on/off>`:  Prevent users from sending messages in a channel (except specific roles).
            *   `/nuke`: Clones current channel and deletes the original, resetting it.
            *   `/case <case_id>`: View details of a specific moderation case.
            *   `/history <@user>`: View the moderation history of a user.
            *   `/modlogs <enable/disable/channel>`: Set up and configure moderation logging.
            *   `/automod`: Access AutoMod configuration settings.

   2.  **Leveling & Economy:**
        *   **Features:**
            *   **XP System:** Customizable XP gain per message or activity, role rewards based on level, leaderboards (daily, weekly, all-time), XP multipliers.
            *   **Currency System:** Customizable currency name, ability to earn currency through activity or commands, shop system to spend currency (on roles, items, etc.), ability to transfer currency between users.
            *   **Games:** Basic economy games (e.g., coin flip, slots, blackjack) to earn/gamble currency.
        *   **Commands:**
            *   `/rank <@user>`: Check a user's level and XP.
            *   `/leaderboard`: View the server leaderboard.
            *   `/balance <@user>`: Check a user's currency balance.
            *   `/daily`: Claim a daily currency reward.
            *   `/pay <@user> <amount>`: Transfer currency to another user.
            *   `/shop`: View the server shop.
            *   `/buy <item>`: Purchase an item from the shop.
            *   `/inventory <@user>`: Check user inventory
            *   `/give <@user> <amount>` (Admin): Grant currency to a user.
            *   `/setlevel <@user> <level>` (Admin): Set user level
            *   `/reset-economy` (Admin) - Resets the entire server economy

   3.  **Utility & Fun:**
        *   **Features:**
            *   **Reminders:** Set reminders for yourself or other users.
            *   **Polls:** Create polls with multiple options.
            *   **Giveaways:** Create and manage giveaways with customizable requirements and durations.
            *   **Custom Commands:** Create custom commands that output text, images, or execute other commands (with variable support).
            *   **Embed Builder:**  An interactive command to build and send custom embeds.
            *   **Role Reactions:** Assign roles to users based on their reactions to a message.
            *   **Suggestions:** Allow users to submit suggestions and vote on them.
            *   **Music:** Integrate basic music playback functionality using platforms like YouTube or Spotify.
            *   **Translate:** Integrate with translation APIs for language translation.
        *   **Commands:**
            *   `/remind <me/channel> <time> <message>`
            *   `/poll "Question" "Option 1" "Option 2" ...`
            *   `/giveaway <duration> <winners> <prize>`
            *   `/createcommand <name> <response>`
            *   `/editcommand <name> <response>`
            *   `/deletecommand <name>`
            *   `/embed`: Start the interactive embed builder.
            *   `/reactrole <message_id> <emoji> <@role>`
            *   `/suggest <suggestion>`
            *   `/play <song_url/search_query>`
            *   `/skip`
            *   `/queue`
            *   `/stop`
            *   `/translate <target_language> <text>`
            *   `/8ball <question>`
            *   `/coinflip`
            *   `/roll <number>`

   4.  **Logging:**
        *   **Features:**
            *   **Detailed Logging:** Log various server events to customizable channels.
                *   Message Edits/Deletions
                *   User Joins/Leaves
                *   Role Changes
                *   Channel Creations/Deletions/Updates
                *   Server Updates (name, icon, etc.)
                *   Voice Channel Activity
                *   Nickname Changes
                *   Avatar changes
        *   **Customizable:** Choose which events to log and where.
        *   **User Tracking:** Detailed logging on specific users, if needed for investigations.
        *   **Image Logging:** If an image is deleted, log the image to the log channel.
        *   **Ghost Ping Detection:** Detect and log when someone pings and then deletes the message.

        *   **Commands:**
            *   `/logging <enable/disable/channel> <event_type>`

   5.  **Ticketing:**
        *   **Features:**
            *   **Ticket Creation:** Allow users to create support tickets through reactions or commands.
            *   **Ticket Management:** Manage tickets in dedicated channels, with options to claim, close, and archive tickets.
            *   **Transcripts:** Generate transcripts of closed tickets for record-keeping.
            *   **Customizable:** Define ticket categories and assign them to specific roles or users.
            *   **Auto-close:** Automatically close tickets after a period of inactivity.
        *   **Commands:**
            *   `/new <reason>`: Create a new support ticket.
            *   `/close <reason>`: Close the current ticket.
            *   `/claim`: Claim the current ticket.
            *   `/add <@user>`: Add a user to the current ticket.
            *   `/remove <@user>`: Remove a user from the current ticket.
            *   `/rename <new_name>`: Rename the current ticket channel.
            *   `/transcript`: Generate a transcript of the current ticket.

## **III. Advanced Features**

    *   **Web Dashboard:** A comprehensive web dashboard for managing all aspects of the bot and server configuration. (Similar to Dyno or MEE6)
    *   **API Access:** Provide API access for server owners to integrate the bot with their own applications.
    *   **Plugin System:** Allow developers to create and load their own plugins to extend the bot's functionality.
    *   **Voice Channel Management:**
       *   Create temporary voice channels that are automatically deleted when empty.
       *   Commands to move users between voice channels.
       *   Commands to set user limits on voice channels.
    *   **Self-Assignable Roles:** Allow users to assign and remove their own roles via a panel
    *   **Starboard:** When a message reaches a certain threshold of star emoji reactions, it gets posted to a dedicated starboard channel.

## **IV.  Design Principles**

    *   **Modularity:**  Each feature set is a module that can be enabled/disabled.
    *   **Customizability:**  Every aspect of each module is configurable.
    *   **Ease of Use:** Intuitive commands and a user-friendly web dashboard.
    *   **Scalability:**  The bot is designed to handle large servers and high traffic.
    *   **Reliability:** Robust error handling and automatic recovery features.
    *   **Security:** Secure coding practices and protection against common vulnerabilities.
    *   **Documentation:** Extensive and well-written documentation.

# Order of development
## **Phase 1: Core Foundation**

1.  **Bot Setup & Basic Infrastructure:**
    *   Environment setup (Python version, dependencies)
    *   Discord API interaction (discord.py library)
    *   Basic command handling
    *   Database setup (e.g., SQLite, PostgreSQL)
    *   Configuration file handling

2.  **Core Modules:**
    *   **Bot Management:** `status`, `ping`, `info`, `help`, `invite`, `support`
    *   **User Management:** `userinfo`, `serverinfo`, `avatar`

3.  **Logging:**
    *   Basic logging (errors, command usage)

4.  **Testing and Error Handling:**
    *   Implement thorough testing (unit tests, integration tests)
    *   Robust error handling and recovery mechanisms

## **Phase 2: Essential Modules**

5.  **Moderation:**
    *   Manual Moderation: `kick`, `ban`, `mute`, `unmute`, `purge`
    *   Basic AutoMod (keyword filtering)
    *   Moderation logging
    *   Case System

6.  **Leveling & Economy:**
    *   XP System (`rank`, `leaderboard`)
    *   Basic Currency System (`balance`, `daily`)

7.  **Utility & Fun:**
    *   `remind`, `poll`, `8ball`, `coinflip`, `roll`

## **Phase 3: Expanding Functionality**

8.  **Moderation (Advanced):**
    *   Advanced AutoMod (spam, links, invites)
    *   `slowmode`, `lockdown`, `nuke`
    *   Role-based permissions for moderation commands
    *   `warn`, `history`, `case`

9.  **Leveling & Economy (Advanced):**
    *   `pay`, `shop`, `buy`, `inventory`
    *   Economy games (coin flip, slots)
    *   Administrative commands (give, setlevel)

10. **Utility & Fun (Advanced):**
    *   `giveaway`
    *   Custom Commands
    *   `embed` (Embed Builder)
    *   `reactrole`

## **Phase 4: Refinement and Advanced Features**

11. **Web Dashboard:**
    *   Basic dashboard functionality (server selection, module toggling)

12. **Logging (Advanced):**
    *   All detailed logging events
    *   Customizable logging channels
    *   Image logging
    *   Ghost ping detection

13. **Ticketing:**
    *   Full ticketing system (`new`, `close`, `claim`, `add`, `remove`, `rename`, `transcript`)

14. **Web Dashboard (Advanced):**
    *   Full control over all bot settings and modules
    *   Moderation action review and management

**Phase 5: Polish and Expansion**

15. **Voice Channel Management**
16. **Self-Assignable Roles**
17. **Starboard**
18. **API Access**
19. **Plugin System**
20. **Continuous Improvement:**
    *   Refactoring, optimization, and ongoing maintenance
    *   Community feedback and feature requests
    *   Security audits and updates
