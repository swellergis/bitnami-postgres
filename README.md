# confirm vertx-mid:atarc-apisrv image exists

docker images

## build vertx-mid:atarc-apisrv image if it doesn't already exist

cd ~/checkout/vertx-mid/
docker build -t vertx-mid:dev .

# restarting postgresql and vertx containers

## clear existing images and containers

cd ~/checkout/bitnami-postgresql/
docker compose down

## run postgres and vertx containers
docker compose up -d

## confirm 5432 (postgres) and 8080 are both listening
ss -nltp

## test the customers endpoint
curl -k https://localhost:8080/customers
