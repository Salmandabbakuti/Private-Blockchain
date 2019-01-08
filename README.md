# Private-net-with-Geth
## Pre-requisites
1.Geth
2.Code editor
## Steps
1. Create a new folder with a name of your choice. for this tutorial, lets say "chain" on your desktop.

2. Copy and paste "myGenesis.json" file(ceate file with this code and with same name) and put it in your folder directory(chain).

3. Go to command prompt. in your directory, run the following command
```
geth --datadir ./node1 init myGenesis.json
 ```
it will start a private blockchain with Genesis state.
 
4. Provide network id by running this command
```
geth --datadir ./node1 --networkid 2019 console
```
it will take you to jS console.

5. Create new account that holds mining reward in the console

```
> personal.newAccount("password Here")

```
6.Set it as default account for mining reward

```
miner.setEtherbase(web3.eth.accounts[0])
```
this command should return true.

7. Start mining activity

```
> miner.start()

```
8. Adding Peers and connecting them together

==> Open another cmd prompt, initialize same genesis file with new data directory like below

```
geth --datadir ./node2 init myGenesis.json

```
==> Connect 2nd node with same network id as first node and use different port.
```
geth --datadir ./node2 --networkid 2019 --port 8081 --ipcdisable --nodiscover console

```
Above command will instantiate chain with networkid 0f 2019 and port of 8081. but node2 is still not connected to node1. to connect, run following commands.

** Repeat step 5, 6 and 7 to add accounts to node 2. ** 

==> in the first node console run this command
```
>admin.nodeInfo

```
above command will return node info with different parameters. copy the enode value which is like this ```"enode://.....@" ```. it is an id of node1. this id is key to connect node2 with node1. we will do it in the next step.

 ==> in your node2 console,

```
>admin.addPeer("enode://.....@")
```
it will return true if, node succesfully conncted. make sure your ``` "enode://...@" ``` value is correct. to confirm if node is connected, run below command in the node1 console

```
>admin.peer()
```
it will show you conncted node with port id, network id.. etc.

Boom... you have succesfully initiated private blockchain with 2 nodes.
