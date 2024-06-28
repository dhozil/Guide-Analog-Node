# Guide Analog Timechain Node

### Install Docker
```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

### Download the latest Timechain image
```
docker pull analoglabs/timechain
```

### Running Node
```
docker run -d -p 9944:9944 -p 30303:30303 analoglabs/timechain --base-path /data --rpc-external --name "yourvalidatorname" --rpc-methods Unsafe --unsafe-rpc-external --rpc-max-connections 15000 --rpc-cors all &
```

### Check your node on telemetry
Go to [Analog Telemetry](https://telemetry.analog.one/#/0x0614f7b74a2e47f7c8d8e2a5335be84bdde9402a43f5decdec03200a87c8b943)
### Generate and Register your Session Keys For Staking
```
echo '{"id":1,"jsonrpc":"2.0","method":"author_rotateKeys","params":[]}' | websocat -n1 -B 99999999 ws://127.0.0.1:9944
```

### Install websocat
```
sudo wget -qO /usr/local/bin/websocat https://github.com/vi/websocat/releases/latest/download/websocat.x86_64-unknown-linux-musl
```

### Verify Websocat Instalation
```
sudo chmod a+x /usr/local/bin/websocat && websocat --version
```

### Bond to Run Validator
Go to PolkadotJS

Create new stash account

Choose Stash account, then fill the amount to bond (Minimum 0.9 TANLOG)

### You can see the result, it is the rotate keys used for bond and start validating
