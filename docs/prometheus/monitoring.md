# Prometheus监控

#### 启动prometheus
```
docker run -dit --restart=always --name prometheus -p 9090:9090 -v /opt/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml prom/prometheus:v2.18.1
```

#### 启动grafana
```
docker run -dit --restart always --name=grafana -p 3000:3000 -v /data/devops/grafana_storage:/var/lib/grafana grafana/grafana:6.7.4
```
#### 启动node-exporter
```
docker pull prom/node-exporter:v0.18.1
docker pull prom/node-exporter:v1.0.1

docker run -dit \
    --restart=always \
    --name node-exporter \
    --net="host" \
    -p 9100:9100 \
    -v "/proc:/host/proc:ro" \
    -v "/sys:/host/sys:ro" \
    -v "/:/rootfs:ro" \
    prom/node-exporter:v1.0.1
```

#### 监控nvidia GPU
```
docker run -dit \
    -p 9400:9400 \
    --gpus all \
    --restart always \
    --name dcgm-exporter \
    nvidia/dcgm-exporter:1.7.2
```

