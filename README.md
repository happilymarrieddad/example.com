## Other Notes
cryptogen generate --config crypto-config.yaml
configtxgen -profile SampleInsecureSolo -outputBlock ./orderer/genesis.block -channelID ordererchannel --configPath ${PWD}
configtxgen -profile SampleSingleMSPChannel -outputCreateChannelTx ./channels/mspchannel.tx -channelID mspchannel --configPath ${PWD}

docker exec -it $(docker ps -a | grep cli | awk '{print $1}') bash

peer channel create -c mspchannel -f ./channels/mspchannel.tx --outputBlock ./channels/mspchannel.block -o orderer:7050