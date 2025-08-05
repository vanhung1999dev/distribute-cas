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
[[:3000] starting fileserver...
2025/08/05 19:19:58 TCP transport listening on port: :3000
[:7777] starting fileserver...
2025/08/05 19:19:58 TCP transport listening on port: :7777
[:5000] starting fileserver...
[:5000] stored file (picture_0.png) and shared with peers
2025/08/05 19:20:02 deleted [d44bbd0bbda685d5db90f419568b531ab9afa97b] from disk
[:5000] dont have file (picture_0.png) locally, fetching from network...
2025/08/05 19:20:07 file (picture_0.png) could not be fetched from network
make: *** [run] Error 1
➜ distribute-cas (main) ✗ make run 
[:3000] starting fileserver...
2025/08/05 19:25:37 TCP transport listening on port: :3000
[:7777] starting fileserver...
2025/08/05 19:25:37 TCP transport listening on port: :7777
[:5000] starting fileserver...
[:5000] stored file (picture_0.png) and shared with peers
2025/08/05 19:25:41 deleted [d44bbd0bbda685d5db90f419568b531ab9afa97b] from disk
[:5000] serving file (picture_0.png) from local disk
my big data file here!
[:5000] stored file (picture_1.png) and shared with peers
2025/08/05 19:25:41 deleted [69ad3ac500e651c476117fe45b7f3335ae264b4a] from disk
[:5000] serving file (picture_1.png) from local disk
my big data file here!
[:5000] stored file (picture_2.png) and shared with peers
2025/08/05 19:25:41 deleted [9a492a63d12540113813344ae1cd6f3df2859a01] from disk
[:5000] serving file (picture_2.png) from local disk
my big data file here!
[:5000] stored file (picture_3.png) and shared with peers
2025/08/05 19:25:41 deleted [1e85e446c078d81bbc7a535f41167531e131b464] from disk
[:5000] serving file (picture_3.png) from local disk
my big data file here!
[:5000] stored file (picture_4.png) and shared with peers
2025/08/05 19:25:41 deleted [d0631a82f788eedaab32cc88f48593ff421fb229] from disk
[:5000] serving file (picture_4.png) from local disk
my big data file here!
[:5000] stored file (picture_5.png) and shared with peers
2025/08/05 19:25:41 deleted [2784657e08429f15f1d16a616e84baa0d38c2dc8] from disk
[:5000] serving file (picture_5.png) from local disk
my big data file here!
[:5000] stored file (picture_6.png) and shared with peers
2025/08/05 19:25:41 deleted [755d434bae2c76b6e44531ce8aeac35de152a5dd] from disk
[:5000] serving file (picture_6.png) from local disk
my big data file here!
[:5000] stored file (picture_7.png) and shared with peers
2025/08/05 19:25:41 deleted [1fa7d7419af18fe51c0d517b8f1df9f9f2b0fa31] from disk
[:5000] serving file (picture_7.png) from local disk
my big data file here!
[:5000] stored file (picture_8.png) and shared with peers
2025/08/05 19:25:41 deleted [94867d2198870a27828ccf3d5da178ae0ffd02d3] from disk
[:5000] serving file (picture_8.png) from local disk
my big data file here!
[:5000] stored file (picture_9.png) and shared with peers
2025/08/05 19:25:41 deleted [1f3eb716dbdedb78ccbc063f731d215eae500bcc] from disk
[:5000] serving file (picture_9.png) from local disk
my big data file here!
[:5000] stored file (picture_10.png) and shared with peers
2025/08/05 19:25:41 deleted [7f31e3243362bfabfd463c5c7a554fb4b9847741] from disk
[:5000] serving file (picture_10.png) from local disk
my big data file here!
[:5000] stored file (picture_11.png) and shared with peers
2025/08/05 19:25:41 deleted [cd3e591445832fd329cc449612a721394a4b1fec] from disk
[:5000] serving file (picture_11.png) from local disk
my big data file here!
[:5000] stored file (picture_12.png) and shared with peers
2025/08/05 19:25:41 deleted [5fff2dd941423a6dc27d054ffcffb18912c93721] from disk
[:5000] serving file (picture_12.png) from local disk
my big data file here!
[:5000] stored file (picture_13.png) and shared with peers
2025/08/05 19:25:41 deleted [309fdb56d613490d2854579197098b504ff82b8a] from disk
[:5000] serving file (picture_13.png) from local disk
my big data file here!
[:5000] stored file (picture_14.png) and shared with peers
2025/08/05 19:25:41 deleted [82510cd450281de103f769f6ce1ac5f3328303fd] from disk
[:5000] serving file (picture_14.png) from local disk
my big data file here!
[:5000] stored file (picture_15.png) and shared with peers
2025/08/05 19:25:41 deleted [b1f78d726eced960bbee6faca1d3694a20eedfc7] from disk
[:5000] serving file (picture_15.png) from local disk
my big data file here!
[:5000] stored file (picture_16.png) and shared with peers
2025/08/05 19:25:41 deleted [72c1d81159dcc898c10bc7cd16f032c5bfd87f01] from disk
[:5000] serving file (picture_16.png) from local disk
my big data file here!
[:5000] stored file (picture_17.png) and shared with peers
2025/08/05 19:25:41 deleted [170a59718ed2ef498f3bc5828b5f17a8b53a7a27] from disk
[:5000] serving file (picture_17.png) from local disk
my big data file here!
[:5000] stored file (picture_18.png) and shared with peers
2025/08/05 19:25:41 deleted [23a77e81b4e82c2ddd07323d11fc4e01b011e6d8] from disk
[:5000] serving file (picture_18.png) from local disk
my big data file here!
[:5000] stored file (picture_19.png) and shared with peers
2025/08/05 19:25:41 deleted [dceee50f1ea67596dc67a1be4e10975451f8af2a] from disk
[:5000] serving file (picture_19.png) from local disk
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
