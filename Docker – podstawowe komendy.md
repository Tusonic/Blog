Docker
Instalacja
Instalujemy potrzebne pakiety
apt-get install -y curl apt-transport-https ca-certificates software-properties-common
Instrukcja na stronie: https://get.docker.com/

Skrócona wersja instalacji
curl -fsSL https://get.docker.com -o install-docker.sh
 sudo sh install-docker.sh
Wyświetlanie kontenerów
Lista wszystkich aktywnych (uruchomionych) kontenerów
docker ps

Lista pełna również kontenerów zatrzymanych (nieaktywne)
docker ps -a

Szczegółowe informacje w formie listy
docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}"
Działania na kontenerach
Uruchamianie zatrzymanego kontenera
docker start {id_kontener}

Zatrzymanie działającego kontenera
docker stop {id_kontener}

Usunięcie konteneru (wcześniej musi być zatrzymany)
docker rm {id_kontener}
lub kilku

docker rm {id_kontener} {id_kontener} {id_kontener}
Uruchomienie docker-compose.yml
Start docker-compose.yml (foreground)
docker compose up
Start docker-compose.yml (detached)
docker compose up -d
Usługi docker
Zatrzymanie usługi Docker
systemctl stop docker
Sprawdzenie statusu usługi Docker
systemctl status docker
Uruchomienie ponownie usługi Docker
systemctl start docker