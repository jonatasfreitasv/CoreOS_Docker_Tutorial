Este reposítorio pode não fazer sentido se você não assistir os videos.

#Step 1
(CoreOS + Docker + Amazon Web Services + Apache/PHP + Linux Dash)

https://www.youtube.com/audio?video_referrer=watch&v=-m_FiDCR4uE

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


#Docker Commands
<pre><code>
//Listar containers
docker ps (em execução) ou ps -l (para listar todos as imagens)

//Listar imagens baixadas
docker images

//Utilizado para criar uma imagem do Docker com as instruções do Dockerfile
docker build -t nome_da_imagem .

//Executar um container
docker run -d -p porta_srv:porta_docker --name="nome_do_docker" -t nome_da_imagem

//Acessar Docker em execução
PID=$(docker inspect --f '{{.State.Pid}}' CONTAINER_ID)
sudo nsenter --target $PID --mount --uts --ipc --net --pid
</code></pre>

