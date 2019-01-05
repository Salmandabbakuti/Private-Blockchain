# Private-net-with-Geth
## Pre-requisites
1.Geth
2.Code editor
## Steps in Creating PrivateNet
1.Create a new folder with a name of your choice. for this tutorial, lets say "chain" on your desktop.
2.Copy and paste "myGenesis.json" file(ceate file with this code and with same name) and put it in your folder directory(chain).
3.Go to command prompt. in your directory, run the following command
 geth --datadir ./node1 init myGenesis.json
 it will start a private blockchain with Genesis state.
4.Provide network id by running this command
geth --datadir ./node1 --networkid 2018 console
it will take you to jS console
Rest is coming soon..........................
