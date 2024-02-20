# dusk-node-güncel

ÖDÜL DURUMU

Dusk teşvikli Node kurulum işlemi. Ödül alabilmeniz için;
20 Şubat itibarıyla düğümlerin çalışır durumda olması gerekiyor. Bu, "sayıldığı" ve çalışma süresinin kaydedileceği zamandır
21 Şubat - 15 Mart 2024 arası çalışması gerekiyor.
Ödüller :
250K DUSK tüm düğümlere eşit olarak dağıtılacak
250K DUSK, stake edilen tutara göre POAP airdrop'uyla dağıtılacak


##Gereksinimler
| 2-4 Gb Ram  | Ubuntu 22.04 |  50-100 Gb SSD | 
| ----------------- | ----------------- | ----------------- |


## Sistem Güncelleme ve kütüphaneler
```shell
sudo apt update && sudo apt upgrade -y
```azılacak


## Rust kurulumu yapın
Kurulumu yapın
```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.0/itn-installer.sh | sudo sh
```
## Cüzdan oluşturma ve Faucet işlemi 
Discord gidin duyuru kanalına giderek sağ üst tarafta insan logosuna tıklayın
Botu bulun ve !Dusk komutunu yazın ve sizden cüzdan adresi isteyecek cüzdan adresinizi yazın
1100 adet tDsuk gelecek cüzdanınızı kontrol edin(yogunluktan dolayı 4-12 saat arasında gelebiliyor tokenler)
- Aşağıdaki komutu girin ve cüzdan kelimelerinizi yazarak giriş yapın.
- Şifrenizi belirleyin
  
- Şifre tekrar girin

```shell
rusk-wallet restore
```
- konsensüs anahtarını dışarı aktarmak için aşaıdaki komutu girin
- Cüzdanınızın şifresini girin
- Tekrar Şifrenizi girin

```shell
rusk-wallet export -d /opt/dusk/conf -n consensus.keys
```

- Şifrenizi girin

```shell
sh /opt/dusk/bin/setup_consensus_pwd.sh
```

##Port Ayarı İşlemleri

#Sanal Sunucuda Yapılacak Port Ayarları 
sanal makinenizden vpc network-firewall kısmını tıklayın(google could) 
(Not:Diğer farklı şirket sunucuları olanlar güvenlik duvarı ayarlarına girecek)
Create firewal Rule(güvenlik duvarı kuralı olustur) tıklayın
Giriş(Ingress) ve çıkış(Egress) her iki trafik yönü için 0.0.0.0/0 filtreli  tcp:8080 udp:9000 olacak şekilde güvenlik duvarı kuralı olsuturun tags kesinlikle vermelisiniz örnek girişe dusk1 çıkışa dusk2 ismini verin 
verilen tagsları sanal sunucunuzda network tags bölümüne dusk1 ve dusk2  olusturuduğunuz tagsları yazın

##Terminalde Yapılacak Port Ayarları



