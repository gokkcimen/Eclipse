# Eclipse

> Details were available in the tweet.

> It doesn't matter if we do the operations on any of our servers.


## Contrat Deploy:

```console
# After entering the command starting with curl below, let's select 1:

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"

# solana cli installation - let's use the commands one by one.

sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
PATH="/root/.local/share/solana/install/active_release/bin:$PATH"
solana config set --url https://staging-rpc.dev.eclipsenetwork.xyz

# after this command => key will be created, We set a password and save the mnemonics and wallet address.

solana-keygen new

# In this command we get tokens to the wallet.

solana airdrop 10

# for this command to work 8 ram required

solana-test-validator

# Once the command runs, you can stop it with ctrl c.

# nodejs installation - let's use the commands one by one

sudo apt-get install -y ca-certificates curl gnupg
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg

NODE_MAJOR=20
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list
sudo apt-get update
sudo apt-get install nodejs -y

# Let's perform the contract deployment process

git clone https://github.com/solana-labs/example-helloworld
cd example-helloworld
npm install

# There will be a bit of a wait here due to rust - it may take a long time.

npm run build:program-rust

# note the program id - YOU WILL USE THIS ID LATER IN THE FORM

solana program deploy dist/program/helloworld.so
npm run start

# It will give success output at the end.

```

## Bridge operation:

```console
sudo apt update -y && sudo apt upgrade -y
sudo apt install git

git clone https://github.com/Eclipse-Laboratories-Inc/testnet-deposit.git
cd testnet-deposit

yarn install
yarn add ethers

# Altta ki komutu düzenleyelim (tırnakları kaldırın):

node deposit.js <solanaAdresi> 0x7C9e161ebe55000a3220F972058Fb83273653a6e 500000 100 <MetamaskPrivateKeyi> https://rpc.sepolia.org

# solana cüzdanı yukarıda oluşturduk onu import edin yeni profilde.
```

> If successful, it will give success and tx output.

> https://explorer.dev.eclipsenetwork.xyz/?cluster=testnet From here we check the wallet and see if there is eth or not. ok if there is.

> Fill out the form: https://docs.google.com/forms/d/e/1FAIpQLSfJQCFBKHpiy2HVw9lTjCj7k0BqNKnP6G1cd0YdKhaPLWD-AA/viewform
