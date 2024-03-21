
# CESS-MINER-NODE

<h1 align="center"> CESS | Storage Miner Testnet </h1>

<div align="center"
     
![image](https://github.com/0xSocrates/Testnet-Rehberler/assets/108215275/f52b6797-1e69-4d84-a5e3-8d84f9d0339e)
   
     
# [Website](https://www.cess.cloud/) | [Twitter](https://twitter.com/CESS_Storage) | [Discord](https://discord.gg/DyEzq6Js) | [Github](https://github.com/CESSProject) | [Docs](https://docs.cess.cloud/cess-build-book/)
     
 </div>

#

## Merhaba arkadaşlar bugün [Cess](https://www.cess.cloud/) projesinin teşvikli testentine katılacağız. Başlamadan önce projenin dökümanlarını ve sosyal medya hesaplarını inceleyip kendi araştırmanızı yapın.

## Cess açılımı Cumulus Encrypted Storage System. Kısacası merkezi olmayan bir yapıya sahip olan ve kullanıcıların verilerini güvenli bir şekilde depolamalarını sağlayan bir bulut depolama sistemidir.

## Testnetine iki farklı şekilde katılınabilir. Bu rehberde ***storage miner*** kurulumunu anlatıcam ***consensus miner*** kurmak isteyenler için [rehber](https://docs.cess.cloud/cess-build-book/consensus-miner)

## Mining, depolama alanı ile yapılıyor. Sunucu gereksinimleri 4Cpu 8Gb Ram Ssd miktarı ne kadar büyük olursa ***storage power*** da o kadar büyük olur dolayısıyla kazacağınız miktar da .


### Sistem Gereksinimleri

| Bileşenler | Minimum Gereksinimler | 
| ------------ | ------------ |
| ✔️CPU |	4+ vcpu|
| ✔️RAM	| 8+ GB |
| ✔️Storage	| 160+ GB SSD(nekadar-çok-okadar-ödül) |
| ✔️UBUNTU | 22or20 |
| ✔️Sunucu Seçimi storege vps secerseniz daha iyi olur coold vps nodede daha az ssd kartı algılıyor |                       |

# Kurulum
> Komutları sırayla girin. UNUTMAYIN HERHANGİ BİR POLKA TABANLI PROJE VARSA SIKINTI ÇIKAR.
```
ufw allow 4001
wget https://github.com/CESSProject/cess-nodeadm/archive/v0.5.4.tar.gz
tar -xvf v0.5.4.tar.gz
rm -rf v0.5.4.tar.gz
cd cess-nodeadm-0.5.4/
./install.sh
mkdir -p /opt/cess/storage/disk
```


# Cüzdan 
### Storage miner olmak için iki adet cüzdana ihtiyacınız var. Birisi gelen ödülelrin yatacağı hesap diğeri stake etmek ve işlemleri imzalamak için kullanılacak hesap.
### [Polkadot{.js}](https://polkadot.js.org/extension/) walletı açın ve iki tane yeni hesap oluşturun -ADRES CX İLE BAŞLAYACAK- ardından [explorera](https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Ftestnet-rpc0.cess.cloud%2Fws%2F#/accounts) gidin cüzdanı bağladıktan sonra ***accounts*** sekmesi altında adresleriniz görünecek. Farklı rpc [Explorer](https://testnet.cess.cloud/?rpc=wss%3A%2F%2Ftestnet-rpc2.cess.cloud%2Fws%2F#/accounts)
### [Faucetten](https://cess.cloud/faucet.html) test tokenları alın.



# Başlatma
```
cess config set
```


> ### Komutu girdikten sonra sırasıyla;
> 1. soru storage yazın
> 2. default port kullanmak istiyordanız enter değilse port numarası girin
> 3. ödüllerin geleceği cüzdanın adresini girin (burda sadece cüzdan adresi girilmeli)
> 4. stake için kullanacağınız cüzdanın mnemonic girin(yeni cüzdan bu sadece stake için-wallet ismine stake wallet olarak kaydedin karışmasın )
> 5. enter (zaten dosyasını olusturduk enter dıyoruz)-Dosya yolunda bazen hata çıkaibliyor ek ssd kart varsa lütfen yolu belirtin.
> 6. ne kadar depolama alını kullanmak istediğinizi girin (sadece sayı gb cinsinden 500gb sadece 500 yazıonuz) hata alıyorsanız 08 nolu çözüm önerisine  bakınız

 08nolu çözüm önerisi:eğer eklenti veya hatalı docker yolu bulamıyorsanız hata alacaksınız
 
 >1.çözüm:ssd diskin yolunu mutlaka bulun ve 5 numaralı soruda mutlaka belirtin

 >2.Çözüm reinstal yapın ve yeniden ilk kuruyormus gibi kurun ve 6. soruya geldiğinde size parantez içinde  önerdiği disk alanını girin
 
> 8. işlemci core sayısı 4 yazıyoruz
> 9. diğer stake hesabını soruyor enter dıyoruz buna
> 10. worker soruyor enter dıyoruz

> 10. > ### Başlat
>

```
cess start
```





# Kontrol
 ### Chain logları
 > `best` ulaştığınız blok yüksekliğiir [exploreri](https://cloudflare-ipfs.com/ipns/dotapps.io/?rpc=wss%3A%2F%2Ftestnet-rpc0.cess.cloud%2Fws%2F#/explorer) yakalayana kadar bekleyin farklı rpc [explorer](https://testnet.cess.cloud/?rpc=wss%3A%2F%2Ftestnet-rpc2.cess.cloud%2Fws%2F#/accounts)

```
docker logs -f chain
```
Önemli!!!Aşağıdaki gibi benzer çıktı almanız gerek expolererden block yüksekliklerini karşılaştırınız.

![image](https://github.com/Volkan081/CESS-MINER-NODE/assets/95221293/b1a4fe22-101a-4e97-998b-f0758c339683)



### Bucket logları
```


![image](https://github.com/Volkan081/CESS-MINER-NODE/assets/95221293/b1a4fe22-101a-4e97-998b-f0758c339683)




docker logs -f bucket
```
Önemli!!!Aşağıdaki gibi benzer bir çıktı almanız gerek.
![image](https://github.com/Volkan081/CESS-MINER-NODE/assets/95221293/ae43eaeb-1564-43f1-bf01-f6e248e0623c)


  



### Bucket durum

Önemli!!!loglar eşitlenince benzer bir görüntü almanız gerekiyor eğer loglar eşitlenmesse böyle bir node yok benzer bir uyarı alınır bu hata değildir sadece log eşitlenmsi beklkenir.

```
cess bucket stat
```


![image](https://github.com/Volkan081/CESS-MINER-NODE/assets/95221293/6bdb1ee2-ab2c-40e7-95d1-8a0e05d29ba8)



### [EXPLORERDA](https://substats.cess.cloud/) Miner kısmına gelip cüzdan adresinizi arayın.

## Yararlı komutlar

### Stake miktarını yükselt
```
cess bucket increase staking <miktar> 
```
Çıktı fotodaki gibi olmalı 

![image](https://github.com/Volkan081/CESS-MINER-NODE/assets/95221293/ca4f667d-c7e2-49d3-a330-216991e511b7)


### Withdraw
```
cess bucket withdraw
```
### Ödül bilgisi
```
cess bucket reward
```
### Claim
```
cess bucket claim
```
### Tüm servisleri güncelle
``` 
cess pullimg
```
### Tüm servisleri durdur ve sil
```
cess down
```
### Kazanç hesabını değiştir
```
cess bucket update earnings <cüzdan adresi>
```

<div align="center">

# Core Node  ekibine teşekkürü borç bilirim Türkiye kripto dünyasında iyi işler yapmaya devam ediyorlar 
# Ayrıca Herculesnode ve ekibine   teşekkür ediyorum.


