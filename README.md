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

### Generate and Register your Session Keys For Staking
```
echo '{"id":1,"jsonrpc":"2.0","method":"author_rotateKeys","params":[]}' | websocat -n1 -B 99999999 ws://127.0.0.1:9944
```

### You can see the result, it is the rotate keys used for bond and start validating
