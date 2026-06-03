# 🎮 Game Proxy Database System

Un sistema completo di **finto database** con **proxy server** per un gioco RPG fantasy. Perfetto per testing, mockup e imparare come funzionano i sistemi di backend!

## 📋 Struttura del Progetto

```
Proxy/
├── config.json          # Configurazione con parametri finti
├── package.json         # Dipendenze Node.js
└── src/
    ├── index.js        # Server Express principale
    ├── database.js     # Mock Database (simula un vero DB)
    └── proxy.js        # Proxy Server con cache e load balancing
```

## 🚀 Come Iniziare

### 1. Installare le dipendenze
```bash
npm install
```

### 2. Avviare il server
```bash
npm start
```

O in modalità development (con auto-reload):
```bash
npm run dev
```

### 3. Testare gli endpoint

**Health Check:**
```bash
curl http://localhost:3000/health
```

**Ottenere tutti gli utenti:**
```bash
curl http://localhost:3000/api/users
```

**Ottenere un utente specifico:**
```bash
curl http://localhost:3000/api/users/1
```

## 🎯 Caratteristiche Principali

### 📊 Mock Database
- **8 tabelle** simulate: users, characters, inventory, guilds, items, quests, dungeons, world_events
- **Dati finti realistici** per il gioco RPG
- Query veloci con ritardo simulato
- Statistiche di esecuzione

### 🔄 Proxy Server
- **Cache intelligente** (Redis-style con TTL)
- **Load Balancer** round-robin tra 3 endpoint
- **Retry automatico** per richieste fallite
- Statistiche di hit/miss della cache

### ⚙️ Configurazione
Nel file `config.json` troverai:
- Parametri del server (port, host)
- Credenziali database (finte)
- Impostazioni cache
- Configurazione proxy
- Parametri del gioco
- Features abilitate/disabilitate
- Rate limiting
- Logging

## 📡 Endpoint Disponibili

### Users
- `GET /api/users` - Lista tutti gli utenti
- `GET /api/users/:id` - Dettagli di un utente
- `POST /api/users` - Crea un nuovo utente

### Characters
- `GET /api/characters` - Lista tutti i personaggi
- `GET /api/characters/:id` - Dettagli di un personaggio

### Inventory
- `GET /api/inventory/:userId` - Inventario di un utente

### Guilds
- `GET /api/guilds` - Lista tutte le gilde
- `GET /api/guilds/:id` - Dettagli di una gilda

### Items
- `GET /api/items` - Lista tutti gli oggetti
- `GET /api/items/:id` - Dettagli di un oggetto

### Quests
- `GET /api/quests` - Lista tutte le quest
- `GET /api/quests/:id` - Dettagli di una quest

### Dungeons
- `GET /api/dungeons` - Lista tutti i dungeon

### World Events
- `GET /api/world-events` - Eventi mondiali attivi

### System
- `GET /health` - Status del server
- `GET /api/stats` - Statistiche server, proxy e database
- `POST /api/proxy/clear-cache` - Pulisci la cache
- `GET /api/proxy/next-endpoint` - Prossimo endpoint load-balanced

## 📊 Dati di Esempio

### Utenti
- **Dragon_Slayer** (Livello 45)
- **MysticWizard** (Livello 38)
- **ShadowAssassin** (Livello 42)
- **HolyKnight** (Livello 50)
- **EchoHunter** (Livello 35)

### Classi Disponibili
- Warrior (Guerriero)
- Mage (Mago)
- Rogue (Ladro)
- Paladin (Paladino)
- Ranger (Ranger)

### Oggetti Leggendari
- **Excalibur** - Spada leggendaria con 150 DMG
- **Staff of Eternal Wisdom** - Staff epico con 200 MATK
- **Adamantite Plate Armor** - Armatura rara con 100 DEF

### Dungeon
- **Tomb of the Forgotten** - Livello 30+
- **Cursed Forest** - Livello 20+
- **Dragon Lair** - Livello 50+ (LEGGENDARIO)

## 🛠️ Features del Sistema

### Game Features
- 🏰 Dungeons
- 🤝 Guilds (Gilde)
- 💳 Marketplace (Mercato)
- 🎮 Battle Pass
- 🎉 Seasonal Events (Eventi Stagionali)
- 🔨 Crafting
- 🐾 Pets
- 🐴 Mount System

### Server Features
- ⚡ Cache con TTL configurabile
- 🔄 Load Balancing round-robin
- 🛡️ Rate Limiting
- 📝 Logging strutturato
- 🔐 API Key Security
- 🌐 CORS configurato

## 📝 Configurazione Personalizzata

Modifica `config.json` per:
- Cambiare porta e host
- Configurare il nome del gioco
- Abilitare/disabilitare features
- Regolare TTL della cache
- Settare rate limits
- Cambiare endpoint del proxy

## 🎮 Esempio di Risposta

```json
{
  "success": true,
  "count": 5,
  "data": [
    {
      "id": 1,
      "username": "Dragon_Slayer",
      "email": "player1@game.com",
      "level": 45,
      "experience": 150000,
      "created_at": "2024-01-15"
    }
  ]
}
```

## 🔍 Debug & Logging

Quando richiedi un endpoint:
- Vedrai i log nel terminale
- Cache hit/miss tracciati
- Endpoint load-balanced mostrati
- Statistiche database disponibili

## 📚 Cosa Imparare

Questo progetto dimostra:
- ✅ Architettura Proxy/Database
- ✅ Caching strategies (TTL, invalidation)
- ✅ Load Balancing
- ✅ RESTful API design
- ✅ Mock data generation
- ✅ Error handling
- ✅ Config management

## 🚀 Prossimi Passi

Puoi espandere il progetto con:
- Autenticazione JWT
- WebSocket per real-time updates
- Persistenza reale (PostgreSQL)
- Rate limiting più sofisticato
- Database replication
- Monitoring e alerting
- Docker containerization

---

**Divertiti!** 🎉
