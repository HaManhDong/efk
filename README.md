### EFK Stack

- Deploy stack
```
cd aio
docker compose up -d
```

- Service port:
    - Fluentd: 24224
    - Elasticsearch: 9200
    - Kibana: 5601
    - Web: 80

- Command to generate logs:
```
for i in {1..10}; do curl http://localhost:80/; done

for i in {1..10}; do curl http://localhost:80/abc; done
```

### Elastalert2

Link download elastalert2 plugin cho kibana: https://github.com/Karql/elastalert-kibana-plugin/releases

Link elastalert2 server: https://github.com/Karql/elastalert2-server/blob/master/README.md

Triển khai cài elastalert plugin cho kibana:
```
# docker cp elastalertKibanaPlugin-1.7.2-8.17.0.zip multinode-kibana-1:/home/
# docker exec -it -u0 multinode-kibana-1 bash
# ls -la /home/elastalertKibanaPlugin-1.7.2-8.17.0.zip
# which kibana-plugin
/usr/share/kibana/bin/kibana-plugin

# /usr/share/kibana/bin/kibana-plugin install file:///home/elastalertKibanaPlugin-1.7.2-8.17.0.zip

// nếu gặp lỗi như dưới thì cần hạ version của kibana từ 8.17.2 về 8.17.0 thông qua edit file docker-compose.yaml
// Plugin installation was unsuccessful due to error "Plugin elastalertKibanaPlugin [8.17.0] is incompatible with Kibana [8.17.2]

# docker restart multinode-kibana-1

# docker commit multinode-kibana-1 kibana:8.17.0_elastalert2
```