# consul-dockercompose
Learn Consul with a local sandbox using docker-compose

# Step 1
/step1
Create a simple Consul Server.
We using client 0.0.0.0

consul agent \
  -server \
  -bootstrap-expect=1 \
  -node=agent-one \
  -client=0.0.0.0 \
  -data-dir=/tmp/consul \
  -config-dir=/etc/consul.d
  
  
  # Step 2
  
  Add an agent to the Cluster via docker network.

  Now, i will share a folder with the consul server, so we can add some changes to the config file.
   Run docker compose and only 1 node will appaer in the consul. Get the ip (172.28.0.2). 
  Sign in to the new consul_agent node:
  consul members
  
  Node          Address          Status  Type    Build  Protocol  DC   Segment
626bb4c548db  172.28.0.3:8301  alive   client  1.8.5  2         dc1  <default>
  
  now we can join this node to the cluster
   consul join 172.28.0.2
Successfully joined cluster by contacting 1 nodes.
  
  And now we will have 2 nodes connected.
  
  #Step 3
  Now that we now how to add more nodes, we will try to join them automatically.
  
