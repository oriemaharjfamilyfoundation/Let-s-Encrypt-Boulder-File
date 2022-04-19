git clone https://github.com/letsencrypt/boulder/
cd boulder

docker-compose up

docker-compose run --use-aliases boulder ./test.sh

docker-compose run --use-aliases boulder ./test.sh --unit

docker-compose run --use-aliases boulder ./test.sh --unit --filter=./va

docker-compose run --use-aliases boulder ./test.sh --integration

docker-compose run --use-aliases boulder ./test.sh --filter TestAkamaiPurgerDrainQueueFails/TestWFECORS

docker-compose run --use-aliases boulder ./test.sh --list-integration-tests 

ifconfig docker0 | grep "inet addr:" | cut -d: -f2 | awk '{ print $1}'

docker-compose run --use-aliases -e FAKE_DNS=172.17.0.1 --service-ports boulder ./start.py

docker-compose run --use-aliases boulder go test -p 1 ./...

docker-compose run --use-aliases boulder go test <DIRECTORY>

docker-compose run --use-aliases boulder python3 test/integration-test.py --chisel --gotest --filter <REGEX>


SERVER=http://localhost:4001/directory certbot_test certonly --standalone -d oriemaharaj.org
