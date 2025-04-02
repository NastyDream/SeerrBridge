# 🌉 SeerrBridge - Automate Your Media Fetching with DMM 🎬

![seerrbridge-cover](https://github.com/user-attachments/assets/653eae72-538a-4648-b132-04faae3fb82e)

![GitHub last commit](https://img.shields.io/github/last-commit/Woahai321/SeerrBridge?style=for-the-badge&logo=github)
![GitHub issues](https://img.shields.io/github/issues/Woahai321/SeerrBridge?style=for-the-badge&logo=github)
![GitHub stars](https://img.shields.io/github/stars/Woahai321/SeerrBridge?style=for-the-badge&logo=github)
![GitHub release](https://img.shields.io/github/v/release/Woahai321/SeerrBridge?style=for-the-badge&logo=github)
![Python](https://img.shields.io/badge/Python-3.10.11+-blue?style=for-the-badge&logo=python)
[![Website](https://img.shields.io/badge/Website-soluify.com-blue?style=for-the-badge&logo=web)](https://soluify.com/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-connect-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/company/soluify/)
<!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-2-orange.svg?style=flat-square)](#contributors-)
<!-- ALL-CONTRIBUTORS-BADGE:END -->

---

## 🚀 What is SeerrBridge?

🌉 **SeerrBridge** is a browser automation tool that integrates [Jellyseer](https://github.com/Fallenbagel/jellyseerr)/[Overseerr](https://overseerr.dev/) with [Debrid Media Manager](https://github.com/debridmediamanager/debrid-media-manager). It listens to movie requests via Overseerr webhook. It automates the torrent search and download process using Debrid Media Manager via browser automation, which in turn, gets sent to Real-Debrid. This streamlines your media management, making it fast and efficient.

<details>
<summary>🛠️ Why SeerrBridge?</summary>

**SeerrBridge** eliminates the need to set up multiple applications like [Radarr](https://radarr.video/), [Sonarr](https://sonarr.tv/), [Jackett](https://github.com/Jackett/Jackett), [FlareSolverr](https://github.com/FlareSolverr/FlareSolverr), and other download clients. With SeerrBridge, you streamline your media management into one simple, automated process. No more juggling multiple tools—just request and download!

Simply put, I was too lazy to set up all of these other applications (arrs) and thought.... I want this instead.

Example:

![sb](https://github.com/user-attachments/assets/f4a9f1c9-5fa9-4fa5-b1e8-3ddc6a156a91)
</details>

---
## ✨ Run SeerrBridge with ElfHosted 🚀

Want to turbocharge your SeerrBridge setup without the DIY hassle? 🎉 Check out [ElfHosted](https://store.elfhosted.com/seerrbridge/elf/6929/)! They’ve got a slick, fully-managed option to run SeerrBridge standalone—perfect for auto-grabbing TV episodes 📺 with Overseerr and RealDebrid, no server wizardry needed! 🧙‍♂️

Or, go big with their [Hobbit bundle](https://store.elfhosted.com/hobbit-jellyfin-realdebrid-seerrbridge/elf/6929/) 🎁: Jellyfin + RealDebrid + SeerrBridge, all pre-wired for you. Stream infinite episodes (yep, auto-grabs included! ⏰) with up to 2 HD or 1 4K stream 🌟—a turn-key media dream. Join the 100+ ⭐ stargazers loving SeerrBridge, hassle-free!

---

<details>
<summary>📊 Flowchart (Rectangle of Life)</summary>

![image](https://github.com/user-attachments/assets/e6b1a4f2-8c69-40f9-92a8-e6e76e8e34e7)
</details>


<details>
<summary>🔑 Key Features</summary>

- **Automated Movie Requests**: Automatically processes movie requests from Overseerr and fetches torrents from Debrid Media Manager.
  
- **TV Show Subscriptions**: Subscribes to ongoing/currently airing TV shows and automatically tracks individual episode releases.
  - Automatically fetches individual episodes when **complete season packs** are unavailable.
  - Tracks previously missed or failed episodes and retries processing them.
  - Continuously polls on a defined interval to automatically detect and fetch new episodes as they are released.
  - Fully integrated with **Debrid Media Manager** and **Real-Debrid**.

- **Debrid Media Manager Integration**: Uses DMM to automate (via browser) torrent search & downloads.
  
- **Persistent Browser Session**: Keeps a browser session alive using Selenium, ensuring faster and more seamless automation.
  
- **Queue Management**: Handles multiple requests with an asynchronous queue, ensuring smooth processing.
  
- **Error Handling & Logging**: Provides comprehensive logging and error handling to ensure smooth operation.
  
- **Setting Custom Regex / Filter in Settings**: Upon launch, the script automates the addition of a regex filter which can be updated in code.
</details>

<details>
<summary>📊 Compatibility</summary>

| Service        | Status | Notes                                |
|----------------|--------|--------------------------------------|
| **[List Sync](https://github.com/Woahai321/list-sync)**| ✅      | Our other Seerr app for importing lists   |
| **Jellyseerr**  | ✅      | Main integration. Supports movie requests via webhook  |
| **Overseerr**   | ✅      | Base application Jellyseerr is based on  |
| **Debrid Media Manager**| ✅      | Torrent fetching automation          |
| **Real-Debrid**| ✅      | Unrestricted (torrent) downloader       |
| **AllDebrid**| ❌      | Not Supported      |
| **TorBox**| ❌      | Not Supported     |
| **SuggestArr**| ✅      | Automatically grab related content and send to Jellyseerr/Overseerr      |
| **Windows & Linux x86-64**| ✅      | Tested and working in both Windows & Linux environments      |
</details>

<details>
### (THIS SCRIPT IS STILL IN BETA)
<summary>⚙ Requirements</summary>

Before you can run this script, ensure that you have the following prerequisites:

### 1. **Jellyseerr / Overseerr API & Notifications**
  - SeerrBridge should be running on the same machine that Jellyseerr / Overseerr is running on.
  - You will need the API key for your .env file.
  - For notifications, navigate to Settings > Notifications > Webhook > Turn it on, and configure as shown below

     ```bash
     http://localhost:8777/jellyseer-webhook/
     ```

![image](https://github.com/user-attachments/assets/170a2eb2-274a-4fc1-b288-5ada91a9fc47)

Ensure your JSON payload is the following 

```
{
    "notification_type": "{{notification_type}}",
    "event": "{{event}}",
    "subject": "{{subject}}",
    "message": "{{message}}",
    "image": "{{image}}",
    "{{media}}": {
        "media_type": "{{media_type}}",
        "tmdbId": "{{media_tmdbid}}",
        "tvdbId": "{{media_tvdbid}}",
        "status": "{{media_status}}",
        "status4k": "{{media_status4k}}"
    },
    "{{request}}": {
        "request_id": "{{request_id}}",
        "requestedBy_email": "{{requestedBy_email}}",
        "requestedBy_username": "{{requestedBy_username}}",
        "requestedBy_avatar": "{{requestedBy_avatar}}",
        "requestedBy_settings_discordId": "{{requestedBy_settings_discordId}}",
        "requestedBy_settings_telegramChatId": "{{requestedBy_settings_telegramChatId}}"
    },
    "{{issue}}": {
        "issue_id": "{{issue_id}}",
        "issue_type": "{{issue_type}}",
        "issue_status": "{{issue_status}}",
        "reportedBy_email": "{{reportedBy_email}}",
        "reportedBy_username": "{{reportedBy_username}}",
        "reportedBy_avatar": "{{reportedBy_avatar}}",
        "reportedBy_settings_discordId": "{{reportedBy_settings_discordId}}",
        "reportedBy_settings_telegramChatId": "{{reportedBy_settings_telegramChatId}}"
    },
    "{{comment}}": {
        "comment_message": "{{comment_message}}",
        "commentedBy_email": "{{commentedBy_email}}",
        "commentedBy_username": "{{commentedBy_username}}",
        "commentedBy_avatar": "{{commentedBy_avatar}}",
        "commentedBy_settings_discordId": "{{commentedBy_settings_discordId}}",
        "commentedBy_settings_telegramChatId": "{{commentedBy_settings_telegramChatId}}"
    },
    "{{extra}}": []
}
```

### 2. **Real-Debrid Account**
   - You will need a valid [Real-Debrid](https://real-debrid.com/) account to authenticate and interact with the Debrid Media Manager.
     - The Debrid Media Manager Access token, Client ID, Client Secret, & Refresh Tokens are used and should be set within your .env file. Grab this from your browser via Inspect > 

![image](https://github.com/user-attachments/assets/c718851c-60d4-4750-b020-a3edb990b53b)

This is what you want to copy from your local storage and set in your .env:

    RD_ACCESS_TOKEN={"value":"your_token","expiry":123}
    RD_CLIENT_ID=YOUR_CLIENT_ID
    RD_CLIENT_SECRET=YOUR_CLIENT_SECRET
    RD_REFRESH_TOKEN=YOUR_REFRESH_TOKEN

### 3. **Trakt API / Client ID**
   - Create a [Trakt.tv](https://Trakt.tv) account. Navigate to Settings > Your API Apps > New Application
     - You can use https://google.com as the redirect URI
     - Save the Client ID for your .env file.
    
![image](https://github.com/user-attachments/assets/c5eb7dbf-7785-45ca-99fa-7e6341744c9d)
![image](https://github.com/user-attachments/assets/3bb77fd5-2c8f-4675-a1da-59f0cb9cb178)


### 4. **Python 3.10.11+**
   - The bot requires **Python 3.10.11** or higher. You can download Python from [here](https://www.python.org/downloads/).

### 5. **Required Python Libraries**
   - You can install the required libraries by running:
     ```bash
     pip install -r requirements.txt
     ```

---

### Example `.env` File

Create a `.env` (or rename the example .env) file in the root directory of the project and add the following environment variables:

```bash
RD_ACCESS_TOKEN={"value":"YOUR_TOKEN","expiry":123456789}
RD_REFRESH_TOKEN=YOUR_REFRESH_TOKEN
RD_CLIENT_ID=YOUR_CLIENT_ID
RD_CLIENT_SECRET=YOUR_CLIENT_SECRET
TRAKT_API_KEY=YOUR_TRAKT_TOKEN
OVERSEERR_API_KEY=YOUR_OVERSEERR_TOKEN
OVERSEERR_BASE=https://YOUR_OVERSEERR_URL.COM
HEADLESS_MODE=true
ENABLE_AUTOMATIC_BACKGROUND_TASK=false
REFRESH_INTERVAL_MINUTES=120
TORRENT_FILTER_REGEX=^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
MAX_MOVIE_SIZE=0
MAX_EPISODE_SIZE=0
```
</details>

<details>
<summary>🛠️ Getting Started</summary>

### Sending Notifications to SeerrBridge from Jellyseerr / Overseerr

Configure your webhook as mentioned above so SeerrBridge can ingest and process approval requests.


### Python Environment

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Woahai321/SeerrBridge.git
   cd SeerrBridge
   ```
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
3. **Run the application**:
   ```bash
   python seerrbridge.py
   ```

---

### 🐳 Docker Support

#### Option 1: Using Docker Compose

1. Clone the repository:
    ```bash
    git clone https://github.com/Woahai321/SeerrBridge.git
    cd SeerrBridge
    ```

2. Copy the example `.env` file and update it with your specific configuration:
    ```bash
    cp .env.example .env
    ```

    Example `.env`:
    ```bash
    RD_ACCESS_TOKEN={"value":"YOUR_TOKEN","expiry":123456789}
    RD_REFRESH_TOKEN=YOUR_REFRESH_TOKEN
    RD_CLIENT_ID=YOUR_CLIENT_ID
    RD_CLIENT_SECRET=YOUR_CLIENT_SECRET
    TRAKT_API_KEY=YOUR_TRAKT_TOKEN
    OVERSEERR_API_KEY=YOUR_OVERSEERR_TOKEN
    OVERSEERR_BASE=https://YOUR_OVERSEERR_URL.COM
    HEADLESS_MODE=true
    ENABLE_AUTOMATIC_BACKGROUND_TASK=true
    REFRESH_INTERVAL_MINUTES=120
    TORRENT_FILTER_REGEX=^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
    MAX_MOVIE_SIZE=5
    MAX_EPISODE_SIZE=1
    ```

3. Start the container:
    ```bash
    docker compose build
    docker compose up -d
    ```

4. Access the app at: [http://localhost:8777](http://localhost:8777).

---

#### Option 2: Using Docker Run

Skip Compose and run the container directly:

```bash
docker run -d \
  --name seerrbridge \
  -p 8777:8777 \
  -v $(pwd)/config:/app/config \
  -e RD_ACCESS_TOKEN={"value":"YOUR_TOKEN","expiry":123456789} \
  -e RD_REFRESH_TOKEN=YOUR_REFRESH_TOKEN \
  -e RD_CLIENT_ID=YOUR_CLIENT_ID \
  -e RD_CLIENT_SECRET=YOUR_CLIENT_SECRET \
  -e TRAKT_API_KEY=YOUR_TRAKT_TOKEN \
  -e OVERSEERR_API_KEY=YOUR_OVERSEERR_TOKEN \
  -e OVERSEERR_BASE=https://YOUR_OVERSEERR_URL.COM \
  -e HEADLESS_MODE=true \
  -e ENABLE_AUTOMATIC_BACKGROUND_TASK=true \
  -e REFRESH_INTERVAL_MINUTES=120 \
  -e TORRENT_FILTER_REGEX=^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).* \
  -e REFRESH_INTERVAL_MINUTES=120 \
  -e MAX_MOVIE_SIZE=5 \
  -e MAX_EPISODE_SIZE=1 \
  ghcr.io/woahai321/seerrbridge:main
```
---

***IF YOU ARE USING OVERSEERR IN DOCKER AND SEERRBRIDGE IN DOCKER, YOUR WEBHOOK IN OVERSEERR NEEDS TO BE THE DOCKER CONTAINER IP***

To find the IP of the SeerrBridge Docker container do the following:

```bash
docker ps
```

You will see the container and ID

![image](https://github.com/user-attachments/assets/dac5fb21-89a7-42ff-8e73-911a6b8ee149)

Grab the ID and do

```bash
docker inspect YOUR-ID
```

You will see the ID in the response:

![image](https://github.com/user-attachments/assets/b9a67170-748b-4c44-b37c-86a820e8d09a)

This will determine your Overseerr Webhook URL i.e. HTTP://DOCKER-CONTAINER-IP:8077/jellyseer-webhook/

---



## Docker Network Configuration

### Steps to Align Containers on the Same Network

1. **Check Container Networks:**
   Run the following command to list the containers and their associated networks:
   ```bash
   docker ps --format '{{ .ID }} {{ .Names }} {{ json .Networks }}'
   ```
   This will display the container IDs, names, and the networks they are connected to.

2. **Disconnect the Container from Its Current Network:**
   Use the following command to disconnect a container from its current network:
   ```bash
   docker network disconnect NETWORK_NAME CONTAINER_ID
   ```
   Replace `NETWORK_NAME` with the name of the network the container is currently on, and `CONTAINER_ID` with the ID of the container.

3. **Connect the Container to the Desired Network:**
   Use the following command to connect the container to the target network:
   ```bash
   docker network connect TARGET_NETWORK_NAME CONTAINER_ID
   ```
   Replace `TARGET_NETWORK_NAME` with the name of the network you want the container to join (e.g., `overseerr`), and `CONTAINER_ID` with the ID of the container.

4. **Verify the Changes:**
   Run the `docker ps --format '{{ .ID }} {{ .Names }} {{ json .Networks }}'` command again to confirm that both containers are now on the same network.

### Example
To move a container with ID `abc123` from its current network to the `overseerr` network:
```bash
docker network disconnect current_network abc123
docker network connect overseerr abc123
```

### Notes
- Ensure both containers are connected to the same network after completing the steps.
- If the containers are still not communicating, double-check the network configuration and ensure no firewall rules are blocking the connection.

---

That's it! Your **SeerrBridge** container should now be up and running. 🚀
</details>

<details>
<summary>🛤️ Roadmap</summary>

- [ ] **Faster Processing**: Implement concurrency to handle multiple requests simultaneously.
- [x] **TV Show Support**: Extend functionality to handle TV series and episodes.
- [x] **DMM Token**: Ensure access token permanence/refresh
- [x] **Jellyseer/Overseer API Integration**: Direct integration with Jellyseer/Overseer API for smoother automation and control.
- [x] **Title Parsing**: Ensure torrent titles/names are properly matched and handle different languages.
- [x] **Docker Support**: Allow for Docker / Compose container.
</details>

<details>
<summary>🔍 How It Works</summary>

1. **Seerr Webhook**: SeerrBridge listens for movie requests via the configured webhook.
2. **Automated Search**: It uses Selenium to automate the search for movies on Debrid Media Manager site.
3. **Torrent Fetching**: Once a matching torrent is found, SeerrBridge automates the Real-Debrid download process.
4. **Queue Management**: Requests are added to a queue and processed one by one, ensuring smooth and efficient operation.

If you want to see the automation working in real-time, you can edit the .env and set it to false

![image](https://github.com/user-attachments/assets/dc1e9cdb-ff59-41fa-8a71-ccbff0f3c210)

This will launch a visible Chrome browser. Be sure not to mess with it while it's operating or else you will break the current action/script and need a re-run.

Example:

![sb](https://github.com/user-attachments/assets/c6a0ee1e-db07-430c-93cd-f282c8f0888f)
</details>

<details>
<summary>📺 TV Show Subscription Feature</summary>

SeerrBridge now includes an exciting **TV Show Subscription** feature that enhances its functionality for ongoing and currently airing TV shows! With this new addition, SeerrBridge takes automated media fetching to the next level:

### 🔧 How It Works:
- **Episode-Level Automation**: Automatically tracks and fetches **individual episodes** for ongoing TV shows, especially when a **complete season pack** is unavailable.
- **Smart Subscription System**:
    - Tracks currently airing episodes and **checks for new releases on a defined interval**.
    - Handles previously **missed or failed episode downloads**, ensuring nothing gets left behind.
- **Seamless Integration**: Works flawlessly with **Debrid Media Manager** and **Real-Debrid**, providing uninterrupted automation and caching requested episodes instantly when available.
- **Fully Automated**: Once subscribed to a show, SeerrBridge manages all episodes for you. No need to manually check for new episodes!

### 🌟 Key Benefits:
- **Never Miss an Episode**: Perfect for keeping up with currently airing shows where season packs are rare or unavailable during release cycles.
- **Optimized for Real-Debrid**: Ensures episodes are downloaded as soon as torrents are cached and accessible in your debrid account.
- **Retry Mechanism**: Any failed episode attempts are logged and automatically retried during the next interval check.

🎉 **This feature ensures you stay up to date on your favorite series—all fully automated!**
</details>

<details>
<summary>📁 Movie and Show File Sizes</summary>

For movies, possible values are: 
| Value | Description |
| :-----------: | :-----------: |
| 0| Biggest Size Possible |
|1|1 GB|
|3|3 GB|
|5|5 GB **(Default)**|
|15|15 GB|
|30|30 GB|
|60|60 GB|

For episodes, possible values are: 
| Value | Description |
| :-----------: | :-----------: |
| 0| Biggest Size Possible |
|0.1|100 MB|
|0.3|300 MB|
|0.5|500 MB|
|1|1 GB **(Default)**|
|3|3 GB|
|5|5 GB|
</details>

<details>
<summary>🎯 Custom Regex Filtering</summary>

This script includes support for **custom regex filtering**, allowing you to filter out unwanted items and refine the results based on specific patterns. The regex is automatically added when the script runs, and you can customize it directly in the code.

### Default Regex

The currently used regex is:

```python
^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

#### What It Does:
- **Exclude Items with `【...】`**: `(?!.*【.*?】)` removes items with formatted text in this style.
- **Exclude Cyrillic Characters**: `(?!.*[\u0400-\u04FF])` removes items containing characters from Cyrillic scripts (e.g., Russian text).
- **Exclude Items with `[esp]`**: `(?!.*\[esp\])` removes items explicitly marked as `[esp]` (often denoting Spanish content).
- **Match All Other Content**: `.*` ensures the filter applies to the rest of the string.

This is a broad exclusion-based filter that removes unwanted patterns without requiring specific inclusions.

---

### Optional Regex (Filtering by Resolution)

If you'd like to refine the filter further to only match items containing **1080p** or **2160p**, you can use the following optional regex:

```python
^(?=.*(1080p|2160p))(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

#### What It Does:
- **Include Only Items with `1080p` or `2160p`**: `(?=.*(1080p|2160p))` ensures that only items with these resolutions are processed.
- The rest of the filter (**exclude `【...】`, Cyrillic characters, or `[esp]`**) works the same as in the default regex.

---

### How to Use

To switch between the default and optional regex, simply update the `.env` file:

- **Default Regex**:
    ```python
    ^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
    ```

- **Optional Regex**:
    ```python
    ^(?=.*(1080p|2160p))(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
    ```

This gives you flexibility to define what gets filtered, based on your preferred criteria.


## 📜 List of Regex Examples

Below is a categorized list of regex patterns for different filtering possibilities.

---

### 1. **Current Filter**
```regex
^(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

---

### 2. **Current Filter with Resolutions**
```regex
^(?=.*(1080p|2160p))(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

---

### 3. **Current Filter with Torrent Types**
```regex
^(?=.*(Remux|BluRay|BDRip|BRRip))(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

---

### 4. **Filter with Both Types and Resolutions**
```regex
^(?=.*(1080p|2160p))(?=.*(Remux|BluRay|BDRip|BRRip))(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

---

### 5. **Filter for Specific Resolution Only**
```regex
^(?=.*(1080p|2160p)).*
```

---

### 6. **Filter for Specific Torrent Types Only**
```regex
^(?=.*(Remux|BluRay|BDRip|BRRip)).*
```

---

### 7. **Customizable Regex Template**
```regex
^(?=.*(1080p|2160p))?(?=.*(Remux|BluRay|BDRip|BRRip))?(?!.*【.*?】)(?!.*[\u0400-\u04FF])(?!.*\[esp\]).*
```

---

By selecting one of these patterns, you can tailor the regex filter to fit your exact needs.
</details>


## 📞 Contact

Have any questions or need help? Feel free to [open an issue](https://github.com/Woahai321/SeerrBridge/issues) or connect with us on [LinkedIn](https://www.linkedin.com/company/soluify/).

---

## 🤝 Contributing

We welcome contributions! Here’s how you can help:

1. **Fork the repository** on GitHub.
2. **Create a new branch** for your feature or bug fix.
3. **Commit your changes**.
4. **Submit a pull request** for review.

---

## 💰 Support SeerrBridge's Development

If you find SeerrBridge useful and would like to support its development, consider becoming a sponsor:

➡️ [Sponsor us on GitHub](https://github.com/sponsors/Woahai321)

Thank you for your support!

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=Woahai321/SeerrBridge&type=Date)](https://star-history.com/#Woahai321/SeerrBridge&Date)

---

## Contributors 🌟

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/KRadd1221"><img src="https://avatars.githubusercontent.com/u/5341534?v=4?s=100" width="100px;" alt="Kevin"/><br /><sub><b>Kevin</b></sub></a><br /><a href="https://github.com/Woahai321/SeerrBridge/commits?author=KRadd1221" title="Code">💻</a> <a href="https://github.com/Woahai321/SeerrBridge/issues?q=author%3AKRadd1221" title="Bug reports">🐛</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/shivamsnaik"><img src="https://avatars.githubusercontent.com/u/16705944?v=4?s=100" width="100px;" alt="Shivam Naik"/><br /><sub><b>Shivam Naik</b></sub></a><br /><a href="https://github.com/Woahai321/SeerrBridge/commits?author=shivamsnaik" title="Code">💻</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

---

## 📄 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

---

<details>
<summary>📜 Legal Disclaimer</summary>

This repository and the accompanying software are intended **for educational purposes only**. The creators and contributors of this project do not condone or encourage the use of this tool for any illegal activities, including but not limited to copyright infringement, illegal downloading, or torrenting copyrighted content without proper authorization.

### Usage of the Software:
- **SeerrBridge** is designed to demonstrate and automate media management workflows. It is the user's responsibility to ensure that their usage of the software complies with all applicable laws and regulations in their country.
- The tool integrates with third-party services which may have their own terms of service. Users must adhere to the terms of service of any external platforms or services they interact with.

### No Liability:
- The authors and contributors of this project are not liable for any misuse or claims that arise from the improper use of this software. **You are solely responsible** for ensuring that your use of this software complies with applicable copyright laws and other legal restrictions.
- **We do not provide support or assistance for any illegal activities** or for bypassing any security measures or protections.

### Educational Purpose:
This tool is provided as-is, for **educational purposes**, and to help users automate the management of their own legally obtained media. It is **not intended** to be used for pirating or distributing copyrighted material without permission.

If you are unsure about the legality of your actions, you should consult with a legal professional before using this software.
</details>
