<h1 align="center">  Github Uzerindeki Bir Repoyu Gitopia Uzerine Aktarma  </h1>


![Fi0V8cBVUAETXeh](https://user-images.githubusercontent.com/108215275/211386256-ed4bb284-4f09-41ca-989f-39e3ab2685ab.jpg)

# Oncelikle bu rehberdeki tum islemleri Gitopianin kendi rehberinden de yapabilirsiniz. Bastan sona [Gitopia Docs](https://docs.gitopia.com/)

### Arkadaslar daha once Gitopia uzerinde bir repo olusturmustuk ve bu repoya `git` ile dosya yuklemistik.
### Simdi yapacagimiz islem ise Githubdaki bir repoyu Gitopia uzerinde tasimak.
### Tavsiyem eger yapmadiysaniz once repo olusturmayi yapin [Link](https://gitopia.com/Socrates/Repo-Olusturma/tree/master/README.md)
### Daha once olusturdugunuz repo ile bir iliskisi olmayacak yeni bir repo uzerinden islemleri yapacagiz
### Neler gerekli:
* Gitopiada kullandıgınız cuzdanın mnemonic
* Github hesabı ve icinde bir repo, forkladıgınız bir repo da olur

### Oncelikle Gitopia websitesine hangi cuzdan ile baglandiginizi kontrol edin.
### Eger gitopia wallet ile baglandiysaniz sag ustte profile tıkladıktan sonra `Download Wallet` secenegine tiklayip walletinizin .json uzantili dosyasini indirin.
![image](https://user-images.githubusercontent.com/108215275/211394826-d5177dd0-1ae8-48ea-9ac5-b0903516ae9c.png)

### Eger Keplr ile baglandiysaniz yine sag ustten profile tikladiktan sonra `Switch Wallet` secenegine
![image](https://user-images.githubusercontent.com/108215275/211395048-7301f9c8-58c3-4217-82e8-85da455f92cd.png)


### Ardından `Create New` butonuna
![image](https://user-images.githubusercontent.com/108215275/211395266-332d4079-ff65-485e-a0fb-1499cc00dcf8.png)

### Ardından acilan sayfada `Recover exiting wallet` secenegini sectikten sonra gitopia cuzdaninizin kelimelerini girin.

![image](https://user-images.githubusercontent.com/108215275/211394529-1dbadc65-b9e0-4b32-a3ff-9719fa53fc81.png)
### Ve `Download Wallet` tıklayarak wallet dosyasını indirin

### Indirdiginiz `cuzdanismi.json` dosyasini WinSCP ya da hangi SFTP araci kullaniyorsanıiz onunla sunucunuzun içine atin `/root` kasoru altina
### Ardindan
```
git config --global --unset gitopia.key
```
* Bu komutta dosya ismini degistirmeyi unutmayin (eger dosyayi root degil baska bir klasor icine attiysaniz, komutta dosya yolunu degistirebilirsiniz)
```
export GITOPIA_WALLET=/root/<dosyaismi.json>
```


### Sunucuda yapilacak islemler bu kadardi, simdi tekrar gitopia websitesine donun ve yeni bir repo olusturun.
### Daha onceki gibi acilan repo sayfasının en ustunde bir komut var bunu daha sonra kullanacagiz

![image](https://user-images.githubusercontent.com/108215275/211399446-22bd35ef-aaa7-46fc-8a1f-3c33c23e5877.png)

### Simdi github hesabiniza girip klonlamak istediginiz repoyu acin
### Ust satirin en sonunda `Settings`tiklayin.
![image](https://user-images.githubusercontent.com/108215275/211400092-f250f272-328f-4eb3-8af9-e960214a373c.png)
### Ardindan sol tarafta `Secrets` tikladiktan sonra altinda acilan `Actions` secenegine tiklayin.
![image](https://user-images.githubusercontent.com/108215275/211400563-9a6084da-5f66-4a28-ba65-cf5276b528ec.png)

### Ardindan `New repository secret` butonuna tiklayin.
![image](https://user-images.githubusercontent.com/108215275/211401076-82080a00-f03c-4914-bc7d-b50a961803d6.png)

### Acilan bolumde `Name*` kismina `GITOPIA_WALLET` `Value*` kismina ise indirdiginiz .json uzantili wallet dosyasinin icinde yazanlari oldugu gibi kopyalayip yapistirin. Ardindan `Add secret` butonuna tiklayin.

![image](https://user-images.githubusercontent.com/108215275/211402149-ad5ccc5b-0870-4ec9-b140-364b9f742d11.png)

### Karsiniza gelen sayfa bu sekilde altta Gitopia Wallet eklenmis oldugu gorunuyor. Ust satirda `Actions` bolumune tiklayin
![image](https://user-images.githubusercontent.com/108215275/211403225-dc188b37-ce36-4205-a653-bf0f0a1b9d4a.png)

### Mavi renkte `set up a workflow yourself` yazisina tiklayin.
![image](https://user-images.githubusercontent.com/108215275/211403470-b8bd519c-9ff0-43c2-945a-61e12570374e.png)

### Acilan sayfada isaretli kisimdaki `main.yml` dosya ismini `gitopia-mirror.yml` olarak degistirin. Klasor isimlerini degistirmeyin.

![image](https://user-images.githubusercontent.com/108215275/211404479-d3d34b5a-68b8-41b0-b9d2-9b6bba70a1dc.png)

### Kod kismina asagidakini komple kopyalayip yapistirin
### Degistirmeniz gereken kisim `remoteUrl:` bunun karsisina " " isaretleri icinde gitopia sitesinden aldiginiz komutu yazin.
```

name: Mirror to Gitopia

on:
  push:
    branches:
      - '**'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
        with:
          fetch-depth: 0
      - name: Push to Gitopia mirror
        uses: gitopia/gitopia-mirror-action@v0.5.0
        with:
          gitopiaWallet: "${{ secrets.GITOPIA_WALLET }}"
          remoteUrl: "gitopia://Gitopia-User/hello-world"
          force: false
```
### Son olarak bu sekilde gorunmesi gerekiyor

![image](https://user-images.githubusercontent.com/108215275/211408834-adccb362-bc8c-45c3-a446-d3e49d38abcb.png)

### Kontrol ettikten sonra; ilk olarak sag tarafta `Start commit` butonu ve ardından altinda acilan `Commit new file` butonuna tiklayin. Yukaridaki gorselde isaretli.

## Islemler bu kadardı Gitopiadaki reponuzu acip sayfayi yenileyin.















































![FUU_ffBUEAAvYjp](https://user-images.githubusercontent.com/108215275/211384853-c9bf68e4-297d-49e5-82c4-b665afc64492.jpg)


