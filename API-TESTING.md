# Game API Testing Examples

## 🎯 Quick Test Commands

### Health Check
```bash
curl http://localhost:3000/health
```

### Get All Users
```bash
curl http://localhost:3000/api/users
```

### Get Specific User
```bash
curl http://localhost:3000/api/users/1
```

### Get All Characters
```bash
curl http://localhost:3000/api/characters
```

### Get All Guilds
```bash
curl http://localhost:3000/api/guilds
```

### Get All Items
```bash
curl http://localhost:3000/api/items
```

### Get All Quests
```bash
curl http://localhost:3000/api/quests
```

### Get All Dungeons
```bash
curl http://localhost:3000/api/dungeons
```

### Get Server Stats
```bash
curl http://localhost:3000/api/stats
```

### Clear Cache
```bash
curl -X POST http://localhost:3000/api/proxy/clear-cache
```

### Get Next Load-Balanced Endpoint
```bash
curl http://localhost:3000/api/proxy/next-endpoint
```

---

## 📝 cURL Examples with JSON

### Create New User (POST)
```bash
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "username": "NewPlayer",
    "email": "newplayer@game.com"
  }'
```

### Get User Inventory
```bash
curl http://localhost:3000/api/inventory/1
```

---

## 🧪 Testing with PowerShell

```powershell
# Health Check
Invoke-WebRequest -Uri "http://localhost:3000/health" | ConvertTo-Json

# Get Users
Invoke-WebRequest -Uri "http://localhost:3000/api/users" | ConvertTo-Json

# Create User
$body = @{
    username = "PowerShellPlayer"
    email = "ps@game.com"
} | ConvertTo-Json

Invoke-WebRequest -Uri "http://localhost:3000/api/users" `
  -Method POST `
  -ContentType "application/json" `
  -Body $body
```

---

## 🌐 Testing with JavaScript/Fetch

```javascript
// Get all users
fetch('http://localhost:3000/api/users')
  .then(res => res.json())
  .then(data => console.log(data));

// Get stats
fetch('http://localhost:3000/api/stats')
  .then(res => res.json())
  .then(data => console.log('Server Stats:', data));

// Create new user
fetch('http://localhost:3000/api/users', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    username: 'JSPlayer',
    email: 'js@game.com'
  })
})
  .then(res => res.json())
  .then(data => console.log('New User:', data));

// Clear cache
fetch('http://localhost:3000/api/proxy/clear-cache', {
  method: 'POST'
})
  .then(res => res.json())
  .then(data => console.log(data));
```

---

## 🐍 Testing with Python

```python
import requests

# Get all users
response = requests.get('http://localhost:3000/api/users')
print(response.json())

# Get server stats
response = requests.get('http://localhost:3000/api/stats')
print('Stats:', response.json())

# Create new user
data = {
    'username': 'PythonPlayer',
    'email': 'python@game.com'
}
response = requests.post('http://localhost:3000/api/users', json=data)
print('New User:', response.json())

# Clear cache
response = requests.post('http://localhost:3000/api/proxy/clear-cache')
print(response.json())
```

---

## 📊 Expected Response Format

All successful responses follow this format:

```json
{
  "success": true,
  "count": 5,
  "data": [...]
}
```

Error responses:

```json
{
  "success": false,
  "error": "Error message here"
}
```

---

## 🎯 Common Test Scenarios

### Test 1: Check Server Health
1. Run: `curl http://localhost:3000/health`
2. Look for status: "online"

### Test 2: Cache Testing
1. First request: `curl http://localhost:3000/api/users`
2. Check logs for "Cache MISS"
3. Second request (same URL)
4. Check logs for "Cache HIT"

### Test 3: Load Balancer
1. Run multiple times: `curl http://localhost:3000/api/proxy/next-endpoint`
2. Notice the endpoint changes in round-robin pattern

### Test 4: Database Stats
1. Run: `curl http://localhost:3000/api/stats`
2. Check database query count and total records

---

## 🔧 Troubleshooting

**Server not starting?**
```bash
# Check if port 3000 is in use
netstat -ano | findstr :3000

# Kill the process (Windows)
taskkill /PID <PID> /F
```

**Cache not working?**
- Check config.json: `cache.enabled` should be true
- Clear cache: `curl -X POST http://localhost:3000/api/proxy/clear-cache`

**Database errors?**
- Make sure Node.js is installed
- Check server logs for errors
