# 📦 Distributed CAS File Server

A peer-to-peer **Content Addressable Storage (CAS)** file server written in Go. Each node runs a secure file server with built-in file sharing, synchronization, and AES encryption over TCP.

---

## 📁 Project Structure

```
cas/
├── main.go             # Application entrypoint
├── store.go            # CAS logic (Put/Get)
├── fileserver.go       # File server handling peer sync
├── crypto.go           # AES-CTR encryption
├── Makefile            # Build/run tool
└── p2p/                # P2P TCP communication
    ├── transport.go
    ├── tcp_transport.go
    ├── message.go
    ├── encoding.go
    └── handshake.go
```

---

## 🚀 Getting Started

### ⚙️ Prerequisites

- Go 1.20+
- Git

### 🔨 Build

```bash
make build
```

Or:

```bash
go build -o cas
```

### ▶️ Run

```bash
make run
```

This will start 3 nodes:
- `:3000`
- `:7000`
- `:5000` (this node uploads, deletes, and fetches from others)

---

## 🧪 Example Output

```bash
[:5000] don't have file (picture_1.png), fetching from peers...
[:3000] serving file (c5fbc5...) over network
[:5000] received (25) bytes from (:3000)
my big data file here!
```

---

## 🧠 Features

- ✅ **Content Addressable Storage**: Files stored by SHA-1 hash
- 🔐 **Encrypted Transport**: AES-CTR encryption
- 🌐 **P2P Communication**: TCP-based peer messaging
- ♻️ **Sync Support**: File automatically downloaded from peer if not found locally
- 🧹 **Lightweight**: No database, no external dependencies

---

## 🧰 Components

### 🔐 Crypto

- Uses `AES-CTR` encryption
- `crypto.go` handles encryption/decryption helpers

### 🧠 Storage

- Files are stored by SHA-1 hash key
- File structure is flat, no nested folders

### 🔗 P2P Protocol

- Custom TCP transport layer
- JSON-based message exchange
- Supports handshake, file request/response

### 🖥 File Server

- Uploads files
- Deletes local files to simulate cache eviction
- Automatically fetches missing files from other peers

---

## 📦 How It Works

1. Node `:5000` uploads file and deletes it locally
2. File hash is stored (SHA-1)
3. When file is requested again, node fetches it from other peers (`:3000`, `:7000`)
4. File is decrypted and stored again locally

---

## 🛡 Security

- AES-CTR encryption ensures secure file transfers
- Encrypted content at rest and over the wire
- Random IV per encryption

---

## 🧹 Future Improvements

- Gossip protocol for peer discovery
- gRPC-based transport option
- Automatic re-replication
- Persistent metadata store

---

## 🧑‍💻 Author

**Nguyễn Văn Hưng**

---

## 📝 License

MIT License
