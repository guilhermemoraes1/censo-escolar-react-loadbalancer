# censo-escolar-react-loadbalancer

Fiz o build da aplicação react gerando a pasta /dist

Criei os arquivos nginx.conf e default.conf para o balanceador de carga e também criei os arquivos nginx.conf e default.con para os nodes 

Digitei os comandos abaixo para criar 6 containers (1 balanceador de carga e 5 nodes)

'''
docker run -d --name loadBalancer \
  -p 80:80 \
  -v /home/journey/repos/censo-escolar-react-loadbalancer/loadbalancer/nginx.conf:/etc/nginx/nginx.conf \
  -v /home/journey/repos/censo-escolar-react-loadbalancer/loadbalancer/default.conf:/etc/nginx/conf.d/default.conf \
  nginx:latest

docker run -d --name node1 \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/nginx.conf:/etc/nginx/nginx.conf \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/default.conf:/etc/nginx/conf.d/default.conf \
	-v /home/journey/repos/censo-escolar-react-loadbalancer/dist:/usr/share/nginx/html \
	nginx:latest

docker run -d --name node2 \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/nginx.conf:/etc/nginx/nginx.conf \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/default.conf:/etc/nginx/conf.d/default.conf \
	-v /home/journey/repos/censo-escolar-react-loadbalancer/dist:/usr/share/nginx/html \
	nginx:latest

docker run -d --name node3 \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/nginx.conf:/etc/nginx/nginx.conf \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/default.conf:/etc/nginx/conf.d/default.conf \
	-v /home/journey/repos/censo-escolar-react-loadbalancer/dist:/usr/share/nginx/html \
	nginx:latest

docker run -d --name node4 \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/nginx.conf:/etc/nginx/nginx.conf \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/default.conf:/etc/nginx/conf.d/default.conf \
	-v /home/journey/repos/censo-escolar-react-loadbalancer/dist:/usr/share/nginx/html \
	nginx:latest

docker run -d --name node5 \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/nginx.conf:/etc/nginx/nginx.conf \
    -v /home/journey/repos/censo-escolar-react-loadbalancer/nodes/default.conf:/etc/nginx/conf.d/default.conf \
	-v /home/journey/repos/censo-escolar-react-loadbalancer/dist:/usr/share/nginx/html \
	nginx:latest
'''