<h1 align="center"> Hatırladınız mı? Evet.. ben.. Gitopia </h1>


![image](https://user-images.githubusercontent.com/101149671/201470278-31aa9701-c0be-404c-9b39-a6b481727728.png)


<h1 align="center"> Selamlar, Nisan ayında beklediğimiz malum proje başladı.. </h1>

### Notlar:

 * Nisan ayında ki olayları unutun, neden? - Testnet 2 gün önce başladı.
 * Ee hocam 2 gün önceyse neden şimdi paylaşıyorsun? Elektiriklerim yoktu ve dün ki yoğunluk + Zeeka'yı biliyorsunuz. ([Exorde](https://github.com/ruesandora/ExordeLabs)'de 3 gün önce başlamıştı)
 * Biz daha önce test tokenleri alıp repolar oluşturmuştuk, o tokenler hala geçerli.
 * Floodu detaylı okumanızı rica ediyorum.
 * Gitopia için nerede sohbet edeceğiz? Sadece bu iki kanalda: [burada](https://t.me/GitopiaTurkish) ve [burada](https://discord.gg/JUtJ6b9F)
 * Gitopia için nerede sohbet edeceğiz? Sadece bu iki kanalda: [burada](https://t.me/GitopiaTurkish) ve [burada](https://discord.gg/JUtJ6b9F)
 * Gitopia için nerede sohbet edeceğiz? Sadece bu iki kanalda: [burada](https://t.me/GitopiaTurkish) ve [burada](https://discord.gg/JUtJ6b9F) 

<h1 align="center"> Hoş geldin sevgili dostum, hoş geldin.. </h1>

![image](https://user-images.githubusercontent.com/101149671/201470246-0f7a1ee8-eda2-47c1-99f3-8708764fba4a.png)

## Sistem gereksinimleri:

 * Ekip sistem gereksinimleri yüksek yazmış, o kadara gerek yok bence.
 * Neden? Pruning'i kapatıp, index'i açacağız.
 * Hocam  benim diskim vs. dolduğunda taşıyabilir miyim başka sunucuya? - ```Evet ```
 * Ben ikisinide yazayım:

* Ekibin söylediği:

```
4 CPU Cores
32GB RAM
1TB of storage
```

* Bence:

```
4 CPU
8 RAM
200 SSD (contabo ise, 400 yapın diski, bedava şu an)
```

## Eğer sunucunuz yüksekse ve farklı bir node varsa içinde, yanına gitopia kurmak istiyorsanız şu şekilde başlayın:

 * Değilse, sıfır sunucuysa buna gerek yok.

```
apt install screen
screen -S gitopia
```

## Sistem güncellemesi yapıyoruz
```
sudo apt update && sudo apt upgrade -y
```
## Gerekli kütüphanelerin kurulumunu yapıyoruz.
```
sudo apt install curl build-essential git wget jq make gcc tmux chrony -y
```

## Validator adınızı " " içinde yazın
```
MONIKER="RuesValidator"
GITOPIA_CHAIN_ID="gitopia-janus-testnet-2"
```

## Go kurulumu:
```
cd $HOME
wget -O go1.18.4.linux-amd64.tar.gz https://golang.org/dl/go1.18.4.linux-amd64.tar.gz
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.4.linux-amd64.tar.gz && rm go1.18.4.linux-amd64.tar.gz
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile
echo 'export GO111MODULE=on' >> $HOME/.bash_profile
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile
go version
```

## Gitopia portunu açalım:
```
PORT=15
echo "export NODENAME=$NODENAME" >> $HOME/.bash_profile
echo "export WALLET=wallet" >> $HOME/.bash_profile
echo "export GCHAIN_ID=gitopia-janus-testnet-2" >> $HOME/.bash_profile
echo "export GPORT=${GPORT}" >> $HOME/.bash_profile
source $HOME/.bash_profile
```
## Binary dosyamızı yapılandırıyoruz ve kurulum yapıyoruz.
```
cd $HOME 
rm -rf gitopia
curl https://get.gitopia.com | bash
git clone -b v1.2.0 gitopia://gitopia/gitopia
cd gitopia 
make install
```
## Gitopia Versiyon kontrol ediyoruz

* version: 1.2.0
```
gitopiad version --long
```

## Başlatıyoruz:

* Bir şey değiştirmenize gerek yok burada:

```
gitopiad init --chain-id "$GITOPIA_CHAIN_ID" "$MONIKER"
```
## Genesis ve addrbook'u indiriyoruz:
```
wget -O $HOME/.gitopia/config/addrbook.json "http://65.108.6.45:8000/gitopia/addrbook.json"
wget https://server.gitopia.com/raw/gitopia/testnets/master/gitopia-janus-testnet-2/genesis.json.gz
gunzip genesis.json.gz
mv genesis.json $HOME/.gitopia/config/genesis.json
```

## Seed ve Peers ayarlıyoruz:
```
SEEDS="399d4e19186577b04c23296c4f7ecc53e61080cb@seed.gitopia.com:26656"
PEERS=""
sed -i -e "s/^seeds *=.*/seeds = \"$SEEDS\"/; s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" $HOME/.gitopia/config/config.toml
```
## Disk yerimizi azaltmak için Pruning yapıyoruz
```
pruning="custom"
pruning_keep_recent="100"
pruning_keep_every="0"
pruning_interval="50"
sed -i -e "s/^pruning *=.*/pruning = \"$pruning\"/" $HOME/.gitopia/config/app.toml
sed -i -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"$pruning_keep_recent\"/" $HOME/.gitopia/config/app.toml
sed -i -e "s/^pruning-keep-every *=.*/pruning-keep-every = \"$pruning_keep_every\"/" $HOME/.gitopia/config/app.toml
sed -i -e "s/^pruning-interval *=.*/pruning-interval = \"$pruning_interval\"/" $HOME/.gitopia/config/app.toml
```

## İndexer kapatmak için:
```
indexer="null"
sed -i -e "s/^indexer *=.*/indexer = \"$indexer\"/" $HOME/.gitopia/config/config.toml
```

## Gaz ve ücretleri ayarlıyoruz:
```
sed -i -e "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0utlore\"/" $HOME/.gitopia/config/app.toml
```

## Prometheus etkinleştiriyoruz
```
sed -i -e "s/prometheus = false/prometheus = true/" $HOME/.gitopia/config/config.toml
```

## SErvis dosyası oluşturuyoruz:
```
sudo tee /etc/systemd/system/gitopiad.service > /dev/null <<EOF
[Unit]
Description=gitopia
After=network-online.target

[Service]
User=$USER
ExecStart=$(which gitopiad) start --home $HOME/.gitopia
Restart=on-failure
RestartSec=3
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```

## Servis dosyamızı yetkilendirip nodu başlatıyoruz

 * Yeni başlayan arkadaşlara not:
 * journalctl'li olan son komutu girdiğinizde loglar akacaktır
 * ctrl + c ile logları durduğunuzda height kısmında bir sayı yazacaktır, örneğin: 205
 * Şu an güncel blok [explorerdan](https://gitopia.explorers.guru/) baktığımızda 201233
 * Buraya kadar eşleşmesini beklemeliyiz, burası uzun (belki bir kaç saat) sürebilir.
 * Az önce ctrl + c ile durdurduk, tekrar `sudo journalctl -u gitopiad -f -o cat` komutunu girerek bakabiliriz.
 * Ee.. hocam bu işlemi snapshot ve statesync ile hızlandıramaz mıyız? - Tonla hata veriyor, gerek yok bekleriz..
 

```
apt install screen
screen -S gitopia

sudo systemctl daemon-reload
sudo systemctl enable gitopiad
sudo systemctl restart gitopiad 
sudo journalctl -u gitopiad -f -o cat
```

## Yukarıda anlattığım eşleşme olduktan aşağıdaki komutu girdiğiniz `false` çıktısı vermeli

 * Eşleşmeden komutu girerseniz `true` yazar.
 * Node eşleşene kadar biz diğer işlemleri yapalım, cüzdan oluşturma kısmına geçin:

```
gitopiad status 2>&1 | jq .SyncInfo
```

## Cüzdan oluşturma: 

* Rues yazan kısmı kendınız belirleyin
* Cüzdan oluşturmadan önce isterseniz altta ki 2 komutu okuyun!!!

```
gitopiad keys add Rues
```

## NOTU OKU! Cüzdan varsa mnomaniclerle kur:

 * Hocam benim cüzdanım var, onu kullanmak istiyorum:
 * Ana cüzdan kullanmayın sakın..

```
gitopiad keys add Rues --recover
```

## Şimdi test tokeni alacağız

 * Bunun için faucet botu değil, Nisan ayında yaptığımız gibi platformdan alacağız:
 * [Platform linki](https://gitopia.com/home)
 * Burada yeni bir profil oluşturun keplr indirin, yukarıda kurduğunuz cüzdanın 12 kelimesini girin.

## Cüzdan bakiyenizi kontrol etmek için:

* Cüzdan adrsinizi girin
* Eğer nodunuz eşleşmediyse bu komutu girince balance 0 gözükür
* Neden 0 gözükür? Çünkü nodunuz örneğin 500. bloktaysa, 500. bloğa kadar olan veriyi gösterir, blockchain'e hoş geldiniz.
* Ama keplrda tokenler gözükür, çünkü o güncel bloktadır.

```
gitopiad query bank balances CÜZDANADRESİ
```

## Eee hocam nodumuz eşleşti, şimdi.. Validator oluşturmak için aşağıdaki komudu düzenle

* From yazan yere cüzdan adınız
* Moniker yazan yere Validatör isminiz. (değişmesenizde yukarıda belirlediğimiz ismi koyar, ama test etmedim)

```
gitopiad tx staking create-validator \
  --amount 1000000utlore \
  --from RuesWallet \
  --commission-max-change-rate "0.01" \
  --commission-max-rate "0.2" \
  --commission-rate "0.07" \
  --min-self-delegation "1" \
  --pubkey  $(gitopiad tendermint show-validator) \
  --moniker $MONIKER \
  --chain-id gitopia-janus-testnet-2
```

## Validatore stake etmek için:

* Komutu düzenleyin
* Validatör adresi (valoper adresi)
* Cüzdan adresi
* Validatör adresi nerede bulunur? Operator veya valoper yazar.

![image](https://user-images.githubusercontent.com/101149671/201474759-5924472c-5740-47c3-b80f-c11b9bf9a22a.png)

```
gitopiad tx staking delegate <validatöradresi> 10000000utlore --from=RuesWalletAddress --chain-id=gitopia-janus-testnet-2 --gas=auto
```

# Faydalı komutlar:


### Node'u silme
```
sudo systemctl stop gitopiad
sudo systemctl disable gitopiad
sudo rm /etc/systemd/system/gitopia* -rf
sudo rm $(which gitopiad) -rf
sudo rm $HOME/.gitopia* -rf
sudo rm $HOME/gitopia -rf
sed -i '/GITOPIA_/d' ~/.bash_profile
```

### Jailden çıkma:
```
gitopiad tx slashing unjail --from Cüzdanİsmi --chain-id $GCHAIN_ID
```

### Aklıma komut geldikçe güncellerim..



## Ödül mü?

Okuyabilirsin: [Link](https://blog.gitopia.com/post/2022/11/the-janus-testnet-upgrade/index.html)





