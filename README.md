# Ollama OpenWebUI Telegram Bot 🚀

This project integrates three powerful tools—[Ollama](https://github.com/jmorganca/ollama), [OpenWebUI](https://github.com/mlc-ai/web-llm), and [Ollama Telegram Bot](https://github.com/ruecat/ollama-telegram)—to enable AI interaction through a web UI and Telegram bot. It supports both CPU and GPU configurations. 🖥️🤖

---

## Features ✨
- **[Ollama](https://github.com/jmorganca/ollama)**: Backend for advanced AI language models.
- **[OpenWebUI](https://github.com/mlc-ai/web-llm)**: A web-based interface for interacting with AI.
- **[Ollama Telegram Bot](https://github.com/ruecat/ollama-telegram)**: Seamlessly integrates AI models with Telegram.

---

## Requirements ✅
- **Docker** and **Docker Compose** installed on your system.
- Optional: A GPU-compatible system with NVIDIA drivers for accelerated performance. ⚡

---

## Setup Instructions 🛠️

### 1. Clone the Repository 📂
```bash
git clone https://github.com/samsesh/ollama-openwebui-tg.git
cd ollama-openwebui-tg
```

### 2. Edit the `docker-compose.yml` File 📝
- Uncomment the following lines in the `docker-compose.yml` file to expose the services outside the Docker network:
  - For Ollama:
    ```yaml
    ports:
      - "11434:11434" # Uncomment this line for external access to Ollama
    ```
- Adjust the ports if necessary to avoid conflicts.

### 3. Configure the Telegram Bot 🤖
1. Create a bot on Telegram via [BotFather](https://core.telegram.org/bots#botfather).
2. Obtain the bot token and set it as an environment variable in `docker-compose.yml` under the `OLLAMA_TELEGRAM` service:
   ```yaml
   environment:
     TELEGRAM_BOT_TOKEN=YOUR_BOT_TOKEN
   ```

3. Add your Telegram `userids` and `adminids`:
   ```yaml
     ADMIN_IDS=12345678
     USER_IDS=12345678,87654321
   ```
   Use the instructions below to find your Telegram `userid`.

### How to Get Your Telegram UserID 🔎
1. Search for the bot [@userinfobot](https://t.me/userinfobot) on Telegram.
2. Start a conversation with the bot.
3. The bot will reply with your `userid` (e.g., `12345678`).

You can add this `userid` to the `USER_IDS` or `ADMIN_IDS` environment variables in `docker-compose.yml`.


### 4. Start the Services 🚀
```bash
docker-compose up -d
```

---

## GPU Support 💻
For GPU acceleration, ensure you have:
1. **NVIDIA Drivers** installed on your host system.
2. **nvidia-container-toolkit** installed.

Uncomment the following section in `docker-compose.yml` for GPU support:
```yaml
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]
```


## Customization 🎨
### WebUI Access 🌐
- OpenWebUI is accessible on port `8080`. Visit `http://localhost:8080` (or replace `localhost` with your server's IP) to interact with the web interface.

### Ollama Service Access 🔗
- Ollama is accessible on port `11434`. Use this port to connect external applications or tools.

### Telegram Bot Integration 🤖
- Use the bot token to interact via Telegram. Add the bot to your chat to start using it.

### Editing Configurations 🔧
You can edit `docker-compose.yml` to:
- Change ports.
- Add GPU support.
- Update Telegram bot configurations.

---

## Donations ❤️
Support this project by donating:
[donate.samsesh.net](https://donate.samsesh.net) 💖

---

For questions or contributions, feel free to create an issue or pull request. 🙌
