1, In order to mine from a developer's perspective, we need to have at least two MWC instances. The best way of handling this is to 
create a whyusers directory, under which two separate directories for user1 and user2 are created. Then cd to the directories  
for user1 and user2, do: 
> why server config

The above will set up the environment so that running more than 1 instance on the same machine won't hit the locking issue. After 
this run 
> why 

to start two MWC instances. 

2, Get another terminal, then set up the wallet by doing: 
> why wallet init -h
> why wallet listen

3, Again get another terminal, go to the directory for user1, update in file why-server.toml: 
change enable_stratum_server from false to true

4, Build grin-miner, and then run it (more updates later)

5, To verify if mining is going on, look for grin-miner.log.
