# Mirror_Maker_2

Este projeto tem a finalidade de realizar a replicação de clusters Kafka.

Utiliza um docker compose que provisiona:

- Mirror Maker
- Prometheus
- Kafka Exporter
- Grafana
- Kafka UI

---

Para iniciar a utilização edit o arquivo .env preenchendo com os endereços corretos dos brokers.

> Por default este projeto executa uma replicação ativo-passivo em um cluster sem autenticação e sem ssl, para um cenário diferente será necessário ajustar os parametros do arquivo "properties" em ./configs/

Após a edição do arquivo .env execute o setup.sh para garantir a instalação do docker e do docker-compose:

'''
sudo chmod +x setup.sh && \
sudo ./setup.sh
'''

Feito isso basta executar o docker-compose para provisionar o ambiente e iniciar a replicação:

'''
docker-compose up -d
'''

> Para visualizar o status de cada cluster com a UI antes de iniciar a replicação, você pode iniciar apenas o service kafka-ui e após o termino da verificação utilize o comando acima para subir o restante dos serviços.
> Para iniciar apenas 1 service, por exemplo do UI, utilize o comando abaixo:

'''
docker-compose up -d kafka-ui
'''

---

Para acompanhar o status da replicação temos o Prometheus e o Grafana:

- Prometheus: http://localhost:9090
- Grafana: http://localhost:3000
- Kafka UI: http://localhost:8080