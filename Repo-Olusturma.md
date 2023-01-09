<h1 align="center">  Gitopia Testnet Uzerinde Repo Olusturma  </h1>

![Fi0V8cBVUAETXeh](https://user-images.githubusercontent.com/108215275/211196512-59543d30-4ede-446c-87d0-fccbbcc182b0.jpg)

## Gitopianin kendi rehberi uzerinden de bu islemleri yapabilirsiniz, bastan sona [Gitopia Docs](https://docs.gitopia.com/)

## Oncelikle [gitopia.com](https://gitopia.com/) websitesine girip cüzdani bagladiktan sonra `Create A Repository` sekmesinden bir repo oluşturmaniz gerekiyor. Bir repo ismi beliredikten ve istege bagli aciklama yazdiktan sonra `Create Repository` butonuna tiklamanız yeterli

## Reponun icine girdiginizde isaretli kutucuktaki komutu daha sonra kullanacagiz.
![image](https://user-images.githubusercontent.com/108215275/211202603-fe40fa68-3f09-4159-9357-6156e73350d2.png)


## Sonraki adimlar sunucuda yapilacak.

### guncellenmis oldugundan emin olun.
```
sudo apt-get update -y && sudo apt-get upgrade -y
```
### Git Remote Helper'i indirin.
```
curl https://get.gitopia.com | bash
```
### Git-Remote icin wallet tanimlama
```
gpg --full-generate-key
```
* Yukaridaki komutu girdikten sonra sirasiyla;
* 1..  ve 2.. sorulari enter basarak gecin
* 3..  soru `y` ardindan enter
* 4.. kisimda isim ve email girmenizi isteyecek, isterseniz gercek isim ve emailinizi girin isterseniz bir seyler sallayin ama bos birakmamak gerekiyor.
* 5.. kisimda okay anlamında `o` sonra enter
* Sonraki kisimda passphrase olusturmanizi isteyecek bu kismi bos birakip `<OK>` secenegini isaretleyip enter
![image](https://user-images.githubusercontent.com/108215275/211200661-5d025e39-bf55-4b99-ae06-19242161a478.png)
* Son olarak emin misiniz sorusu `<Yes, protection is not needed>` secenegini isaretleyip enter
![image](https://user-images.githubusercontent.com/108215275/211200616-4e7944ef-b9b2-4ef0-ad81-fd7137ffa1c1.png)

### pass keyring init
```
apt install pass
```
* `<isim>` kismina yukarida belirlediginiz ismi yazın
```
pass init <isim>
```
### Gitopia cuzdanini ekleme
* `<cuzdanismi>` kismini degistirmeyi unutmayin
* Mnenonic girmenizi isteyecek siteye baglandiginiz cuzdanin mnemoniclerini girin
```
git gitopia keys add <cuzdanismi> --recover --keyring-backend pass 
```
```
git config --global --unset gitopia.key
```
```
git config --global gitopia.key <cuzdanismi>
```

```
git config --global gitopia.backend pass
```

### Olusturacaginiz repo icin bir klasor olusturun
```
mkdir <repoismi>
```
```
cd <repoismi>
```
### Simdi repoya bir seyler ekleme zamani
```
nano README.md
```
* README.md dosyasinin icine  herhangi bir sey yazabilirsiniz, ya da githubdaki bir reponuzun README.md dosyasinin icerigini koypalayip yapistirabilirsiniz.
* `CTRL+X`  `Y` ardindan enter basarak dosyadan cıkın

```
git init
```
```
git add README.md
```
```
git commit -m "initial commit"
```
## Ardından siteden aldiginiz komutu girin. Yukarida gorselde isaretli kisim
```
git push -u origin master
```
## Siteye geri donup oluşturdugunuz repo icine girin ve sayfayi yenileyin









































