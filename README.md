# OptimAi BOT - Enhanced Version

An automated bot for OptimAi Network that handles account registration, daily check-ins, and node registration with advanced payload generation.

## More tools here: https://amautomarket.com/

## Features

- ✅ **Automated Login**: OAuth-based authentication with CAPTCHA support
- ✅ **Daily Check-ins**: Automatic daily reward claiming
- ✅ **Node Registration**: Smart node registration with real API data
- ✅ **Advanced Payload Generation**: Hybrid Python + JavaScript payload creation
- ✅ **Duplicate Prevention**: Smart account management prevents duplicates
- ✅ **Real API Integration**: Fetches actual user and device data from OptimAi API
- ✅ **Proxy Support**: Rotating proxy support for multiple accounts
- ✅ **Rate Limiting**: Built-in delays to avoid API rate limits

## Requirements

- Python 3.7+
- Node.js (for JavaScript payload generation)
- 2captcha API key (for CAPTCHA solving)
- Proxy list (recommended for multiple accounts)

## Installation

1. **Clone the repository**:

   ```bash
   git clone <repository-url>
   cd <repo_name>
   ```

2. **Install Python dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

3. **Install Node.js** (required for payload generation):
   - Download from [nodejs.org](https://nodejs.org/)
   - Verify installation: `node --version`

## Configuration

### 1. Account Setup

Edit `login_accounts.json` with your OptimAi accounts:

```json
[
  {
    "email": "your_email@example.com",
    "password": "your_password"
  }
]
```

### 2. 2captcha API Key

Add your 2captcha API key to `2captcha_key.txt`:

- Get API key here: [2captcha](https://2captcha.com/?from=24402314)

```
your_2captcha_api_key_here
```

### 3. Proxy Configuration (Optional but Recommended)

Add your proxies to `proxy.txt` (one per line):

```
http://username:password@proxy_server:port
socks5://user:pass@proxy.example.com:1080
```

## Usage

### Initial Setup

Run the setup script to register accounts and generate necessary data:

```bash
python setup.py
```

This will:

- Authenticate all accounts via OAuth
- Fetch real user IDs and device IDs from OptimAi API
- Generate secure payloads using hybrid JavaScript generation
- Save account data to `accounts.json`

### Daily Bot Execution

Run the main bot for daily operations:

```bash
python bot.py
```

This will:

- Refresh access tokens
- Perform daily check-ins
- Register nodes for mining
- Handle uptime reporting

## Technical Details

### Hybrid Payload Generation

This enhanced version uses a hybrid approach for maximum compatibility:

1. **Python handles**: Authentication, API calls, account management
2. **JavaScript handles**: Payload generation (ensures 100% compatibility with OptimAi's frontend)

The bot creates temporary JavaScript files to generate payloads using the exact same transformation functions as the OptimAi web interface.

### Advanced Features

- **Smart Duplicate Prevention**: Uses JWT user IDs to prevent account duplicates
- **Real API Data**: Fetches actual user and device information from OptimAi endpoints
- **Rate Limiting**: Intelligent delays prevent 429 "Too Many Requests" errors
- **Error Handling**: Comprehensive error handling with detailed logging

### API Endpoints Used

- `/auth/login` - OAuth authentication
- `/auth/token` - Token exchange
- `/auth/me` - User information retrieval
- `/devices` - Device information retrieval
- `/devices/register-v2` - Node registration
- `/checkin` - Daily check-in

## File Structure

```
OptimAi-BOT-Public/
├── bot.py                 # Main bot execution script
├── setup.py               # Initial account setup and registration
├── requirements.txt       # Python dependencies
├── accounts.json          # Generated account data (auto-created)
├── login_accounts.json    # Your login credentials (configure this)
├── proxy.txt             # Proxy list (configure this)
├── 2captcha_key.txt      # 2captcha API key (configure this)
├── .gitignore            # Git ignore file (protects sensitive data)
└── README.md             # This file
```

## Safety and Security

- ✅ **No sensitive data in repository**: All personal data goes in local config files
- ✅ **Proxy support**: Reduces risk of IP-based rate limiting or bans
- ✅ **CAPTCHA solving**: Handles anti-bot measures automatically
- ✅ **Rate limiting**: Respects API limits to avoid temporary bans

## Troubleshooting

### Common Issues

1. **429 "Too Many Requests" errors**:

   - Solution: Use more proxies, add delays between accounts
   - The bot includes automatic rate limiting

2. **JavaScript payload generation fails**:

   - Ensure Node.js is installed: `node --version`
   - Check that temporary files can be created in the bot directory

3. **CAPTCHA solving fails**:

   - Verify your 2captcha API key is correct
   - Check your 2captcha account balance

4. **Login fails**:
   - Verify email/password combinations in `login_accounts.json`
   - Check if accounts are already registered on OptimAi
