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