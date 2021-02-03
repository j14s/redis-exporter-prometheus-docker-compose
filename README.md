# redis prometheus && exporter 

## Deploy:

  1) Clone this repo to a docker server
  2) From within the cloned repo run

    docker-compose up

  3) Log into grafana(default user/pass is admin/admin. It will ask you to change the pass on first login.)

    http://your-server-name:3000/

  4) Create the Prometheus datasource
    a) Settings->Data Sources->Add Datasource->Prometheus
    b) http://your-server-name:9090
    c) Save and Test
  5) On left side bar, "+"->import
    a) Copy/Paste the contents of the file: redis-dashboard-for-prometheus-redis-exporter-1-x_rev3.json
    b) Datasource: Prometheus
  6) Test Redis:
    a) Install redis-tools
    b) Run benchmark

    redis-benchmark -h your-server-name -p 6379 -r 1000000 -n 200000000 -t get,set,lpush,lpop -P 16

  7) Watch pretty graphs run.