# 🚀 GitHub Automation Tool 

A comprehensive, professional-grade Python tool for GitHub automation with multiple operation modes, intelligent rate limiting, multi-threading support, and robust error handling.

## ✨ Features

### Core Capabilities
- ✅ **Token Validation** - Secure authentication with GitHub API
- 👥 **Follow Users** - Manual or automatic user following
- ⭐ **Star Repositories** - Manual or automatic repository starring
- 🎯 **Follow Stargazers** - Follow all users who starred a specific repository
- 🔄 **Multi-threading** - Concurrent operations for optimal performance
- ⏳ **Smart Rate Limiting** - Automatic detection and handling with countdown
- 📊 **Real-time Statistics** - Live progress tracking and final summaries
- 📝 **Comprehensive Logging** - Optional file logging for audit trails
- 🎨 **Color-coded CLI** - Beautiful, informative terminal interface
- 🛡️ **Graceful Shutdown** - Clean exit on Ctrl+C with summary
- 🔁 **Retry Mechanisms** - Exponential backoff for network errors
- 🌐 **Cross-platform** - Works on Windows, Linux, macOS, Termux

### Operation Modes

#### 1. **Manual Mode**
- Follow specific users by username
- Star specific repositories by owner/repo

#### 2. **Auto Follow Users**
- Automatically follow random GitHub users
- Configurable count and threading

#### 3. **Auto Star Repos**
- Automatically star trending repositories
- Filter by programming language
- Configurable parameters

#### 4. **Follow Repo Stargazers**
- Follow all users who starred a repository
- Pagination support for large lists
- Batch processing with configurable parameters

#### 5. **Rate Limit Check**
- View current API rate limit status
- See when limits reset

## 📋 Requirements

### System Requirements
- Python 3.6 or higher
- Internet connection
- GitHub Personal Access Token

### Python Dependencies
```bash
requests
```

## 🔧 Installation

### Standard Installation (Linux/macOS/Windows)

1. **Clone or download the script:**
```bash
# Download the script
git clone https://github.com/mrwhite4939/GitForce
# or
git clone https://github.com/mrwhite4939/GitForce
```

2. **Install dependencies:**
```bash
pip install requests
# or on some systems:
pip3 install requests
```

3. **Make executable (Linux/macOS):**
```bash
chmod +x GitForce
```

### Termux Installation (Android)

```bash
# Update packages
pkg update && pkg upgrade

# Install Python
pkg install python

# Install pip
pkg install python-pip

# Install requests
pip install requests

# Download the script
git clone https://github.com/mrwhite4939/GitForce

# Run the script
python GitForce
```

### Kali Linux Installation

```bash
# Update system
sudo apt update

# Install Python and pip
sudo apt install python3 python3-pip

# Install requests
pip3 install requests

# Download and run
git clone https://github.com/mrwhite4939/GitForce
python3 GitForce
```

### Windows Installation

1. **Install Python:**
   - Download from [python.org](https://www.python.org/downloads/)
   - Check "Add Python to PATH" during installation

2. **Install dependencies:**
```cmd
pip install requests
```

3. **Run the script:**
```cmd
python GitForce
```

## 🔑 Creating a GitHub Personal Access Token

The tool requires a GitHub Personal Access Token for authentication:

1. Go to **GitHub Settings** → **Developer settings** → **Personal access tokens**
2. Click **"Generate new token"** → **"Generate new token (classic)"**
3. Give it a descriptive name (e.g., "Automation Tool")
4. Select the following scopes:
   - ✅ `user:follow` - To follow/unfollow users
   - ✅ `public_repo` - To star repositories
5. Click **"Generate token"**
6. **Copy the token immediately** (you won't see it again!)

### Token Permissions Required

| Permission | Purpose | Required For |
|------------|---------|--------------|
| `user:follow` | Follow/unfollow users | Following users |
| `public_repo` | Star repositories | Starring repos |

## 🎮 Usage

### Basic Usage

```bash
python GitForce
# or
python3 GitForce
# or (if made executable)
./GitForce
```

### Step-by-Step Workflow

1. **Launch the tool**
2. **Enter your GitHub Personal Access Token** (input is hidden for security)
3. **Token validation** - Confirms authentication
4. **Choose operation mode** from the menu:
   - Manual Mode
   - Auto Follow Users
   - Auto Star Repos
   - Follow Repo Stargazers
   - Check Rate Limit
   - Exit

### Example Sessions

#### Example 1: Manual Mode - Follow a User
```
SELECT MODE
1. Manual Mode
...
Enter your choice (1-6): 1

Choose action:
  1. Follow a user
  2. Star a repository

Enter choice (1-2): 1
Enter GitHub username to follow: torvalds
✓ Followed: torvalds
```

#### Example 2: Auto Follow Random Users
```
SELECT MODE
...
Enter your choice (1-6): 2
How many users to follow? (default=50): 100
Number of workers (default=10): 15
Rest time between batches in seconds (default=5): 3

🚀 Following up to 100 random users...
✓ Followed: user1
✓ Followed: user2
...
```

#### Example 3: Follow Repository Stargazers
```
SELECT MODE
...
Enter your choice (1-6): 4
Enter repository (owner/repo): microsoft/vscode
Number of workers (default=10): 20
Rest time between batches (default=5): 5
Batch size (default=50): 100

🚀 Following stargazers of microsoft/vscode...
📄 Processing page 1...
✓ Followed: user1
✓ Followed: user2
...
```

#### Example 4: Auto Star Trending Repos
```
SELECT MODE
...
Enter your choice (1-6): 3
How many repos to star? (default=30): 50
Filter by language? (optional, e.g., Python): Python
Number of workers (default=10): 10
Rest time between batches in seconds (default=5): 5

🚀 Starring up to 50 trending repositories (Python)...
⭐ Starred: django/django
⭐ Starred: pallets/flask
...
```

## ⚙️ Configuration Options

### Threading & Performance

| Parameter | Description | Default | Recommended Range |
|-----------|-------------|---------|-------------------|
| `workers` | Number of concurrent threads | 10 | 5-20 |
| `rest_time` | Seconds to rest between batches | 5 | 3-10 |
| `batch_size` | Items per batch before rest | 50 | 30-100 |

### Performance Tips

- **Small tasks (< 100 items):** workers=10, rest_time=3
- **Medium tasks (100-500 items):** workers=15, rest_time=5
- **Large tasks (> 500 items):** workers=20, rest_time=10
- **Conservative (avoid rate limits):** workers=5, rest_time=10

## 📊 Statistics Tracking

The tool tracks and displays:

- ✅ **Users Followed** - Successfully followed users
- ⭐ **Repos Starred** - Successfully starred repositories
- ⊘ **Items Skipped** - Already followed/starred
- ✗ **Actions Failed** - Failed operations
- ⏳ **Rate Limits** - Number of times rate limit was hit
- 📄 **Pages Processed** - Total pages processed
- 🎯 **Total Actions** - Total operations attempted

### Sample Output
```
FINAL SUMMARY
=====================================
✓ Users Followed:      150
⭐ Repos Starred:      30
⊘ Items Skipped:       25
✗ Actions Failed:      5
⏳ Rate Limits:        2
📄 Pages Processed:    10
🎯 Total Actions:      180
```

## 🛡️ Security & Best Practices

### Security Measures
- ✅ Token input is hidden (using `getpass`)
- ✅ Token is never logged or printed
- ✅ Secure HTTPS communication with GitHub API
- ✅ No token storage - enter each session

### Best Practices
1. **Use dedicated tokens** for automation
2. **Set minimum required scopes** only
3. **Regenerate tokens** periodically
4. **Never share** your token
5. **Revoke tokens** if compromised
6. **Monitor** your account activity

### Rate Limiting
- GitHub allows **5,000 API requests/hour** for authenticated users
- Tool automatically detects and waits when limits are hit
- Countdown timer shows remaining wait time
- Operations resume automatically after reset

## 🐛 Troubleshooting

### Common Issues

#### "Module 'requests' not found"
```bash
pip install requests
# or
pip3 install requests
```

#### "Invalid token" error
- Check token has correct permissions (`user:follow`, `public_repo`)
- Ensure token hasn't expired
- Verify no extra spaces when pasting

#### Rate limit exceeded frequently
- Reduce number of `workers`
- Increase `rest_time`
- Reduce `batch_size`

#### Network timeout errors
- Check internet connection
- GitHub API may be temporarily unavailable
- Tool will retry automatically

#### Script not running on Windows
- Ensure Python is in PATH
- Use `python` instead of `python3`
- Run as administrator if needed

### Error Codes

| Code | Meaning | Solution |
|------|---------|----------|
| 401 | Unauthorized | Check token validity |
| 403 | Rate limited or forbidden | Wait for rate limit reset |
| 404 | User/repo not found | Verify username/repo exists |
| 500+ | GitHub server error | Retry later |

## 📝 Logging

### Enable Logging
When prompted at startup:
```
Enable logging to file? (y/n, default=n): y
```

### Log File Format
```
github_automation_YYYYMMDD_HHMMSS.log
```

### Log Contents
- Timestamp for each operation
- Successful follows/stars
- Errors and failures
- Rate limit events
- Network issues

### Example Log Entries
```
2025-01-15 14:23:45 - INFO - Token validated for user: username
2025-01-15 14:24:12 - INFO - Successfully followed user: torvalds
2025-01-15 14:24:15 - WARNING - Rate limit hit. Waiting 10m 5s
2025-01-15 14:24:20 - ERROR - Failed to follow octocat: HTTP 404
```

## 🎨 Color Coding

| Color | Meaning | Example |
|-------|---------|---------|
| 🟢 Green | Success | "✓ Followed: username" |
| 🔴 Red | Error/Failure | "✗ Failed: username" |
| 🟡 Yellow | Warning | "⏳ Rate limit hit" |
| 🔵 Blue | Information | "📄 Processing page 1" |
| 🟣 Magenta | Special action | "⭐ Starred: repo" |
| ⚪ Cyan | Prompts/Headers | Menu selections |

## 🔄 Graceful Shutdown

Press **Ctrl+C** at any time to:
- Stop current operations cleanly
- Complete in-progress requests
- Display final statistics
- Save logs (if enabled)
- Exit gracefully

## 📚 API Reference

### GitHub API Endpoints Used

- `GET /user` - Validate token
- `GET /rate_limit` - Check rate limits
- `PUT /user/following/{username}` - Follow users
- `PUT /user/starred/{owner}/{repo}` - Star repos
- `GET /repos/{owner}/{repo}/stargazers` - Get stargazers
- `GET /users` - Get random users
- `GET /search/repositories` - Search trending repos

## 📄 License

This tool is provided as-is for educational and automation purposes. Use responsibly and in accordance with GitHub's Terms of Service and API rate limits.

## ⚠️ Disclaimer

- Use this tool responsibly
- Respect GitHub's Terms of Service
- Don't spam or abuse the automation features
- Be mindful of rate limits
- The author is not responsible for account suspensions due to misuse

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📞 Support

For issues or questions:
1. Check the troubleshooting section
2. Review GitHub API documentation
3. Check your token permissions
4. Review the log files (if enabled)

## 🎯 Future Enhancements

Potential features for future versions:
- Unfollow users functionality
- Unstar repositories
- Export followed users list
- Import user lists from file
- Follow users by location/language
- Statistics export to JSON/CSV
- GUI version
- Webhook integration

---

**Made with ❤️ for GitHub automation**
