## Dzień 1
Te repozytorium ma na celu dokumentowanie mojej wiedzy uzyskanej z nauki Hyperledger-Farbic. Aktualnie zakres jaki będzie się tu zawierał to proste zadania np dodawanie organizacji
do istniejacej sieci, aby zrozumieć działanie architektury tej technologii i wstępnie przygotować się do pisania pracy dyplomowej. <br/>
Postępy będą dokumentowane w formie "dziennkika", niekoniecznie każdego dnia bo bardziej chodzi o zachowanie formatu przyjmując że każdy dzień to jakiś krok dalej.<br/>
### Postęp 
Udało mi się uruchomić pierwszą sieć po wielu napotkanych problemach. Generalnie zacząłem od instalacji linuxa 20.4 LTS na maszynie wirtualnej, poniżej zestawiam listę komend instalacyjnych
które poprawnie przygotowały mój system na instalację binarek(Może komuś się przyda te zestawienie)
```
# instalacja git
sudo apt install  git -y

# instalacja  curl
sudo apt install curl -y

# instalacja  docker i docker compose
sudo apt install build-essential -y

sudo apt install apt-transport-https ca-certificates gnupg-agent software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y
```
Teraz bardzo istotna kwestia ponieważ powinniśmy sprawdzić czy mamy dostęp do komendy docker ps jeśli nie to  dodajemy użytkownika do grupy 
```
sudo usermod -aG docker $USER
newgrp docker
sudo service docker start
docker version 
sudo systemctl enable docker.service //Uruchamianie dockera przy starcie systemu.
```





```
# instalacja go
curl -o "go.tar.gz" https://storage.googleapis.com/golang/go1.16.3.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf "go.tar.gz"

export PATH=$PATH:/usr/local/go/bin   
source ~/.bashrc

# install node
sudo apt install nodejs -y

#instalacja pythona 
sudo apt install python
```
Następnie stworzyłem folder hlf do którego pobrałem binarkę za pomocą komendy 
``
curl -sSL https://bit.ly/2ysbOFE | bash -s -- 2.2.3 1.5.0
``
Po czym w końcu bez problemów mogłem uruchomić 
```
./network.sh up 
```
Oto rezultat
![image](https://user-images.githubusercontent.com/45511879/116892418-1b381500-ac30-11eb-9fbc-426c8d299c39.png)

