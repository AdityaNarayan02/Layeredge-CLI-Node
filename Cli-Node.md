# CLI Node Run Full Guide (PC and VPS for Both)

### Offical Docs Guide - https://docs.layeredge.io/introduction/developer-guide/run-a-node/light-node-setup-guide

## Dependencies for WINDOWS & LINUX & VPS
```
sudo apt update && sudo apt upgrade -y
```

- For VPS Only
```
apt install screen -y
```
```
screen -S edge
```

## Install Go 
```
wget https://go.dev/dl/go1.21.5.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.21.5.linux-amd64.tar.gz
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
source ~/.bashrc
go version
```
## Install Rust
```
curl — proto ‘=https’ — tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
rustup install 1.81.0
rustup default 1.81.0
rustc --version
```
## Install Risc0
```
curl -L https://risczero.com/install | bash && rzup install
```

# Download Node Files
```
git clone https://github.com/Layer-Edge/light-node.git
cd light-node
```

## Configure Environment Variables
```
touch .env
```
```
nano .env
```
```
export GRPC_URL=34.31.74.109:9090
export CONTRACT_ADDR=cosmos1ufs3tlq4umljk0qfe8k5ya0x6hpavn897u2cnf9k0en9jr7qarqqt56709
export ZK_PROVER_URL=http://127.0.0.1:3001
export API_REQUEST_TIMEOUT=100
export POINTS_API=http://127.0.0.1:8080
export PRIVATE_KEY='cli-node-private-key'
```
Press CTRL+X, then Y, then Enter
- Replace 'cli-node-private-key' with your actual private key. (Use New Metamask Wallet)

## Start the Merkle Service
```
cd risc0-merkle-service
cargo build && cargo run
```
Keep this terminal open and running. Do not close this as you need it up and running for the node

## Open Another Window for WSL or VPS (do not close the previous one)

### Start Node
```
cd light-node
go build
./light-node
```
- Then Go to Dashboard: https://dashboard.layeredge.io/tasks
- Click "+" icon in CLI-Based Node and put ur Public Key & Verify it
  
## 🔵For Next Day Run This Command

- Open WSL and Put this Command 
```
cd light-node
cd risc0-merkle-service
cargo build && cargo run
```
- Open Another Window for WSL
```
cd light-node
go build
./light-node
```

## Thank you for Visiting if there's any issue feel free to drop your comments here or on telegram
