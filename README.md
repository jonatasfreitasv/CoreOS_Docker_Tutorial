Este reposítorio pode não fazer sentido se você não assistir os videos no link: http://xxxx.com

#user-data
<pre><code>
#cloud-config
coreos:
  etcd: key here
    # generate a new token for each unique cluster from https://discovery.etcd.io/new
    discovery: https://discovery.etcd.io/<token>
    # multi-region and multi-cloud deployments need to use $public_ipv4
    addr: $private_ipv4:4001
    peer-addr: $private_ipv4:7001
  units:
    - name: etcd.service
      command: start
    - name: fleet.service
      command: start
  </code></pre>

#build command
<pre><code>docker build -t nome_da_imagem .  </code></pre>

#run command
<pre><code>docker run -d -p 80:80 --name="nome_do_docker" -t nome_da_imagem  </code></pre>
