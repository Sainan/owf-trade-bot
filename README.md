# 🤖 TradeBot for OpenWF

Улучшенный торговый бот для приватных серверов OpenWF. Добавляет поддержку чертежей, арканов, стаков предметов и автогенерацию цен.

Enhanced trade bot for OpenWF private servers. Adds support for blueprints, arcanes, item stacking and auto-price generation.

---

## 🇷🇺 Русская версия

### 📂 Структура файлов
Все файлы должны лежать в одной папке:
```
owf-trade-bot/
├── TradeBot.pluto          # Основной скрипт бота
├── item_data.lua           # Файл с предметами и ценами
├── config.json             # Настройки бота (создаётся автоматически)
├── data/
│   └── items.json          # Файл с предметами от OpenWF
```

### 🛠️ Установка

1. Установи Pluto:
   ```bash
   choco install plutolang
   ```
   Или скачай бинарники с [официального сайта Pluto](https://pluto-lang.org/).

2. Скачай файлы бота и положи их в одну папку.

3. Убедись, что `items.json` лежит в папке `data/`.

4. Запусти бота:
   ```bash
   pluto TradeBot.pluto
   ```

### ⚙️ Настройка `config.json`

При первом запуске бот создаст файл `config.json`:
```json
{
    "server_host": "127.0.0.1",
    "hub_level": "TRADE_EN_EN_WIN_0",
    "trades": {}
}
```

- `server_host` — IP сервера OpenWF.
- `hub_level` — локация для торговли (`TRADE_EN_EN_WIN_0` — английская, `TRADE_RU_WIN_0` — русская).
- `trades` — здесь можно переопределить цены для конкретных предметов.

### 💰 Управление ценами

Цены генерируются автоматически на основе `gameRef` предметов. Правила заданы в `item_data.lua`.

**Чтобы переопределить цену**, добавь предмет в `config.json`:
```json
"trades": {
    "Rifle Riven Mod (Veiled)": [100, 50],
    "Nekros Prime Neuroptics Blueprint": [20, 10]
}
```
Где `[100, 50]` — цена покупки (бот купит за 100) и цена продажи (бот продаст за 50).

### 💬 Как пользоваться

1. Найди бота на базаре Мару.
2. Открой окно торговли.
3. Напиши в чат команду:
   ```
   "Название предмета"
   ```
   Или для покупки нескольких штук:
   ```
   "Название предмета x5"
   ```
   Пример:
   ```
   "Arcane Aegis x5"
   ```
4. Бот подтвердит заказ в чате.
5. Положи платину в окно торговли.
6. Бот положит предметы и завершит сделку.

### 🛠️ Настройка цен по группам

Отредактируй `price_rules` в `item_data.lua`:
```lua
local price_rules = {
    { pattern = "/Lotus/Upgrades/Mods/Randomized/", buy = 50, sell = 25 },
    { pattern = "/Lotus/Powersuits/", buy = 30, sell = 15 },
    -- добавь свои правила
}
```

---

## 🇬🇧 English Version

### 📂 File Structure
All files must be in the same folder:
```
owf-trade-bot/
├── TradeBot.pluto          # Main bot script
├── item_data.lua           # Items and prices file
├── config.json             # Bot settings (auto-created)
├── data/
│   └── items.json          # Items file from OpenWF
```

### 🛠️ Installation

1. Install Pluto:
   ```bash
   choco install plutolang
   ```
   Or download binaries from [official Pluto website](https://pluto-lang.org/).

2. Download bot files and place them in one folder.

3. Make sure `items.json` is in the `data/` folder.

4. Run the bot:
   ```bash
   pluto TradeBot.pluto
   ```

### ⚙️ Configuring `config.json`

On first run, the bot will create `config.json`:
```json
{
    "server_host": "127.0.0.1",
    "hub_level": "TRADE_EN_EN_WIN_0",
    "trades": {}
}
```

- `server_host` — IP of your OpenWF server.
- `hub_level` — trading location (`TRADE_EN_EN_WIN_0` — English, `TRADE_RU_WIN_0` — Russian).
- `trades` — override prices for specific items.

### 💰 Price Management

Prices are auto-generated based on `gameRef`. Rules are defined in `item_data.lua`.

**To override a price**, add item to `config.json`:
```json
"trades": {
    "Rifle Riven Mod (Veiled)": [100, 50],
    "Nekros Prime Neuroptics Blueprint": [20, 10]
}
```
Where `[100, 50]` — buy price (bot buys for 100) and sell price (bot sells for 50).

### 💬 How to use

1. Find the bot at Maroo's Bazaar.
2. Open the trade window.
3. Type in chat:
   ```
   "Item Name"
   ```
   Or for multiple items:
   ```
   "Item Name x5"
   ```
   Example:
   ```
   "Arcane Aegis x5"
   ```
4. Bot will confirm the order in chat.
5. Put platinum in the trade window.
6. Bot will place items and complete the trade.

### 🛠️ Changing Category Prices

Edit `price_rules` in `item_data.lua`:
```lua
local price_rules = {
    { pattern = "/Lotus/Upgrades/Mods/Randomized/", buy = 50, sell = 25 },
    { pattern = "/Lotus/Powersuits/", buy = 30, sell = 15 },
    -- add your own rules
}
```

---

## 🐛 Отладка / Debugging

В консоли бота выводятся ошибки. Для детальной отладки в коде есть блок `print("=== DEBUG: Trade Window Content ===")`.

Error messages appear in the bot console. For detailed debugging, the code includes a `print("=== DEBUG: Trade Window Content ===")` block.

---

## 📜 Лицензия / License

MIT — используйте как хотите.

---

## 🙏 Благодарности / Credits

Оригинальный бот: [Sainan/owf-trade-bot](https://github.com/Sainan/owf-trade-bot)  
Дополнительная обработка категорий, автогенерация цен, поддержка стаков и IRC-фикс: сообщество.

---

*Если возникнут вопросы — создавайте Issue в репозитории.*
*If you have any questions — open an Issue in the repository.*
