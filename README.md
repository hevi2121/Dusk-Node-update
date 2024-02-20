# dusk-node-güncel

ÖDÜL DURUMU

Dusk teşvikli Node kurulum işlemi. Ödül alabilmeniz için;
20 Şubat itibarıyla düğümlerin çalışır durumda olması gerekiyor. Bu, "sayıldığı" ve çalışma süresinin kaydedileceği zamandır
21 Şubat - 15 Mart 2024 arası çalışması gerekiyor.
Ödüller :
250K DUSK tüm düğümlere eşit olarak dağıtılacak
250K DUSK, stake edilen tutara göre POAP airdrop'uyla dağıtılacak


## Linkler

 [volkanberra twitter](https://twitter.com/BerraVolkan)

 [volkanberra github](https://github.com/Volkan081)
 
 


##Gereksinimler
| 2-4 Gb Ram  | Ubuntu 22.04 |  50-100 Gb SSD | 
| ----------------- | ----------------- | ----------------- |


## Sistem Güncelleme ve kütüphaneler
```shell
sudo apt update && sudo apt upgrade -y
```


## Rust kurulumu yapın  

Kurulumu yapın

```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.0/itn-installer.sh | sudo sh
```



## Cüzdan oluşturma ve Faucet işlemi 
Discord gidin duyuru kanalına giderek sağ üst tarafta insan logosuna tıklayın
Botu bulun ve !Dusk komutunu yazın ve sizden cüzdan adresi isteyecek cüzdan adresinizi yazın
1100 adet tDusk gelecek cüzdanınızı kontrol edin(yogunluktan dolayı 4-12 saat arasında gelebiliyor tokenler)
- Aşağıdaki komutu girin ve cüzdan kelimelerinizi yazarak giriş yapın.
- Not:Cüzdan kelimeleri ingilizce karakter ve hepsi küçük harfle olmalı.
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

## Port Ayarı İşlemleri

## 1.Sunucu Port Ayarı

-sanal makinenizden vpc network-firewall kısmını tıklayın(google could) 
(Not:Diğer farklı şirket sunucuları olanlar güvenlik duvarı ayarlarına girecek)

-Create firewal Rule(güvenlik duvarı kuralı olustur) tıklayın

-Giriş(Ingress) ve çıkış(Egress) her iki trafik yönü için 0.0.0.0/0 filtreli  tcp:8080 udp:9000 olacak şekilde güvenlik duvarı kuralı olsuturun.

-tags kesinlikle vermelisiniz!!! örnek olarak girişe dusk1, çıkışa dusk2 ismini verin.
-verilen tagsları sanal sunucunuzda network tags bölümüne dusk1 ve dusk2  olusturuduğunuz tagsları yazın
-
## 2.Terminal Port Ayarı

komutu girin ufw nin aktif olup olmadığını kontrol edin 

```shell
ufw status
```

'ufw incantive' çıktısı aldıysanız 08 nolu koddan devam devam edin,eğer ufw active çıktısı aldıysanız aşağıdaki kodu girin

```shell
ufw disable
```
08 nolu kod:aşağıdaki komutu girin 

```shell
nano /opt/dusk/services/rusk.conf.user
```


screen açılacak 

screende açılan ip ayarlarında 

-kodların başındaki # (tag)  işretlerini silin 

-public-ip silin ve yerine harici ip(External IP) yazın 

-private-ip silip yerine dahili ip(Internal IP) yazın

#KADCAST_PUBLIC_ADDRESS=public-ip:9000

#KADCAST_LISTEN_ADDRESS=private-ip:9000

Örnek
KADCAST_PUBLIC_ADDRESS=34.168.241.213:9000

KADCAST_LISTEN_ADDRESS=10.138.0.6:9000

## Servisi Çalıştırın

```shell
service rusk start
```

## Update İşlemi Yapın


-Günceleme 
```shell
curl --proto '=https' --tlsv1.2 -sSfL https://github.com/dusk-network/itn-installer/releases/download/v0.1.1/itn-installer.sh | sudo sh

```

2-Çalıştırma

```shell
service rusk start

```

-Log kontrol

```shell
tail -F /var/log/rusk.log

```




## Senkronizasyon Kontrol

Aşağıdaki kodu direk sunucuya yapıştırın bloklar yükseliyormu kontrol edin.Expolrerden karşılaştırma yapın

```shell
curl --location --request POST 'http://127.0.0.1:8080/02/Chain' --header 'Rusk-Version: 0.7.0-rc' --header 'Content-Type: application/json' --data-raw '{
    "topic": "gql",
    "data": "query { block(height: -1) { header { height } } }"
}' | jq '.block.header.height'
```

*https://explorer.dusk.network/



## Stake işlemleri

- Cüzdanınıza Faucet üzerinden 1000 tDusk aldıysanız aşağıdaki komutu girerek stake işlemini başlatın

```shell
rusk-wallet stake --amt 1000 # Or however much you want to stake
```

- Stake sonrası aşağıdaki gibi bir ekran gelecek 30 block onayı verecek


