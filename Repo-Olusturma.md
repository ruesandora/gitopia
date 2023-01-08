<h1 align="center">  Gitopia Testnet Uzerinde Repo Olusturma  </h1>

![Fi0V8cBVUAETXeh](https://user-images.githubusercontent.com/108215275/211196512-59543d30-4ede-446c-87d0-fccbbcc182b0.jpg)

## Gitopianin kendi rehberi üzerinden de bu islemleri yapabilirsiniz, bastan sona [Gitopia Docs](https://docs.gitopia.com/)

## Oncelikle [gitopia.com](https://gitopia.com/) websitesine girip cüzdanı bağladıktan sonra `Create A Repository` sekmesinden bir repo oluşturmanız gerekiyor. Bir repo ismi beliredikten ve istege baglı acıklama yazdıktan sonra `Create Repository` butonuna tıklamanız yeterli

## Reponun icine girdiginizde isaretli kutucuktaki komutu daha sonra kullanacagız.
![image](https://user-images.githubusercontent.com/108215275/211202603-fe40fa68-3f09-4159-9357-6156e73350d2.png)


## Sonraki adımlar sunucuda yapılacak.

### guncellenmis olduğundan emin olun.
```
sudo apt-get update -y && sudo apt-get upgrade -y
```
### Git Remote Helper'i indirin.
```
curl https://get.gitopia.com | bash
```
### Git-Remote icin wallet tanımlama
```
gpg --full-generate-key
```
* Yukarıdaki komutu girdikten sonra sırasıyala;
* 1..  ve 2.. soruları enter basarak gecin
* 3..  soru `y` ardından enter
* 4.. kısımda isim ve email girmenizi isteyecek, isterseniz gercek isim ve emailinizi girin isterseniz bir seyler sallayın ama bos birakmamak gerekiyor.
* 5.. kısımda okay anlamında `o` sonra enter
* Sonraki kısımda passphrase olusturmanızı isteyecek bu kısmı bos birakip `<OK>` secenegini isaretleyip enter
![image](https://user-images.githubusercontent.com/108215275/211200661-5d025e39-bf55-4b99-ae06-19242161a478.png)
* Son olarak emin misiniz sorusu `<Yes, protection is not needed>` secenegini isaretleyip enter
![image](https://user-images.githubusercontent.com/108215275/211200616-4e7944ef-b9b2-4ef0-ad81-fd7137ffa1c1.png)

### pass keyring init
```
apt install pass
```
* `<isim>` kısmına yukarıda belirlediginiz ismi yazın
```
pass init <isim>
```
### Gitopia cuzdanını ekleme
* `<cuzdanismi>` kısmını degistirmeyi unutmayın
* Mnenonic girmenizi isteyecek siteye bağlandıgınız cuzdanın mnemoniclerini girin
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

### Olusturacagınız repo icin bir klasor olusturun
```
mkdir <repoismi>
```
```
cd <repoismi>
```
### Simdi repoya bir seyler ekleme zamanı
```
nano README.md
```
* README.md dosyasının icine  herhangi bir sey yazabilirsiniz, ya da githubdaki bir reponuzun README.md dosyasının icerigini koypalayıp yapıstırabılırsınız.
* `CTRL+X`  `Y` ardından enter basarak dosyadan cıkın

```
git init
```
```
git add README.md
```
```
git commit -m "initial commit"
```
## Ardından siteden aldıgınız komutu girin. Yukarıda gorselde isaretli kısım
```
git push -u origin master
```
## Siteye geri donup oluşturdugunuz repo icine girin ve sayfayı yenileyin









































