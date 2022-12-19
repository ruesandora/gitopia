<h1 align="center"> Github-Gitopia </h1>

- Github'ta oluşturduğunuz bir repoyu Gitopia'ya aktarabileceğiniz bir rehber ile karşınızdayım. O halde haydi başlayalım.

- Bu işlemi gerçekleştirmek için önce Gitopia üzerinde bir repo oluşturmalıyız. Bunun için Gitopia sitesinde profilimize girdiğimizde 'Create a repository' seçeneğine tıklayın.

<img width="1418" alt="1" src="https://user-images.githubusercontent.com/98269269/208249327-e36f37f0-9aff-4094-a546-72f9433a4b97.png">

- Açılan ekranda 'Repository name' ve 'description' kısımlarını dolduralım. Ardından 'Create repository' kısmına tıklayalım.

<img width="1418" alt="2" src="https://user-images.githubusercontent.com/98269269/208249375-83d1b5e1-143b-4056-ba03-dbdcec2e8a31.png">


- Şimdi yapacağımız adımları çok dikkatli yapmalısınız. Öncelikle git remote helper yükleyeceğiz. Bu işlemleri yapabilmek için Gİtopia sunucunuzu açın ve ana terminalde işlem yapın.

- Önce aşağıdaki komut ile kurulumu yapıyoruz.

```
curl https://get.gitopia.com | bash
```
- Yukarıdaki kodu girdiğinizde aşağıdaki hatayı alırsanız, bir sonraki kodu girmelisiniz. Aşağıdaki hatayı almazsanız bir sonraki komutu girmenize gerek yoktur.

![4](https://user-images.githubusercontent.com/98269269/208249557-ae6ee762-5fc0-4e8b-9ab1-0a14f946fbd6.png)

- Yukarı hatayı aldıysanız bu kodu girmelisiniz.
```
sudo mv /tmp/tmpinstalldir/git-remote-gitopia /usr/local/bin/
```


- Şimdi anahtarımızı OS anahtarına ekleyeceğiz. Aşağıdaki komutta yer alan <YOUR_KEY_NAME> kısmına kendiniz için bir isim belirleyip yazıyorsunuz. Ve bu kodu giriyorsunuz.
  
```
git gitopia keys add <YOUR-KEY-NAME> --recover
```
- Yukarıdaki komutu girdiğinizde, cüzdan anımsatıcınızı girmeniz istenecektir. Cüzdanınızın 24 kelimelik kurtarma ifadesini yazın ve ENTER'a basın.

- Kelimeleri girip ENTER tuşuna bastığınızda karşınıza böyle bir çıktı çıkmalı.

![5](https://user-images.githubusercontent.com/98269269/208249849-88c90335-cf64-45dc-b303-0b80b3c800d6.png)

- Şimdi Gitopia anahtar adımızı git config'de yapılandıralım. <YOUR_KEY_NAME> yazan yere biraz önce yukarıda belirlediğiniz adı yazmalısınız.

```
git config --global gitopia.key <YOUR-GITOPIA-KEY-NAME>
```



- Ana adımlara geçmeden önce Keplr cüzdan Mnemonic Seed Phrase'inizi bulmanız gerekiyor. Bunun için öncelikle araç çubuğunuzdaki Keplr uzantı ikonuna tıklayarak hesabınıza giriş yapın ve ardından görseldeki gibi hesap ikonuna tıklayın.

<img width="1420" alt="az" src="https://user-images.githubusercontent.com/98269269/208250010-db70ff75-1925-4258-af8b-67976aee8511.png">

- Şimdi, gösterildiği gibi hesap adınızın yanındaki üç noktayı tıklayın.

<img width="1420" alt="azz" src="https://user-images.githubusercontent.com/98269269/208250050-7d46f096-7e1e-4cdb-8194-5ff8f7e84c42.png">

- Ortaya çıkan seçim menüsünde, View Mnemonic Seed'e tıklayın

<img width="1420" alt="azz" src="https://user-images.githubusercontent.com/98269269/208250170-8bf86f0a-c71c-4942-98bb-501b97902708.png">

- Cüzdan şifrenizi yazmanız istenecektir. Doldurulduktan sonra Confirm tuşuna tıklayın.

<img width="1420" alt="azz" src="https://user-images.githubusercontent.com/98269269/208250231-5c087cf4-0ccf-47e1-8112-c87760a0ee99.png">

- Keplr cüzdanınız Mnemonic Seed Phrase şimdi görüntülenecektir. Anahtarınızı işletim sistemi anahtarlığında ayarlamak için bu anımsatıcıya ihtiyacınız olacak. Bu nedenle bu ifadeleri güvende tuttuğunuzdan emin olmalısınız.

<img width="1420" alt="az" src="https://user-images.githubusercontent.com/98269269/208250281-069b87c5-6eaf-4274-a4fc-6cc9fc49a410.png">

- Oluşturduğunuz anahtarlarınızın isimlerini görmek için aşağıdaki kodu kullanabilirsiniz.

```
git gitopia keys list
```
- Yukarı komutu kullandığınızda aşağıdaki gibi bir çıktı alacaksınız. Bu çıktıda key isimlerinizi görebilirsiniz.

![7](https://user-images.githubusercontent.com/98269269/208250409-ac4822cd-7763-4aba-aa2d-cf9dab8ed79b.png)


- Oluşturduğunuz bir keyi silmek isterseniz bu komutu kullanabilirsiniz.

```
git gitopia keys delete <key_name>
```

- Bu kodu yazdığınızda karşınıza çıkan seçeneğe 'y' diyin ve ENTER tuşuna basın. İşleminiz gerçekleşmiş olacaktır.

## Şimdi Asıl İşlemlere Başlıyoruz. Üst Düzey Dikkat Lazım!

- Öncelikle terminalimizde yukarıdaki cüzdan işlemlerini tamamladık. Artık repomuzu sisteme tanıtarak Github-Gitopia bağlantısını kuracağız. Değişik geldiğini tahmin edebiliyorum :) Haydi başlayalım.

- Komutları tek tek ve sırasıyla girelim.
```
mkdir <REPO_ADINIZ>
```
```
cd <REPO_ADINIZ>
```
```
echo "# <REPO_ADINIZ>" >> README.md
```
```
git init
```
```
git add README.md
```
```
git commit -m "initial commit"
```

- Şimdi Gitopia sayfamıza gidiyoruz ve repomuzun adına tıklıyoruz. Karşımıza çıkan ekranda 'Download Wallet' seçeneğine tıklıyoruz.

<img width="1422" alt="sd" src="https://user-images.githubusercontent.com/98269269/208251096-5fc29723-3be2-476d-8532-b3d2fff0571a.png">

- Sıradaki işlem ile devam ediyoruz. Aşağıdaki kodda <GITOPIA_HESABINIZDAKI_REMOTE_YAZAN_YER> kısmına ilgili yerdeki kodu kopyalayıp yapıştırın.

![8](https://user-images.githubusercontent.com/98269269/208252172-6ab88ea2-e708-44d1-8f6e-0749b05731b8.png)

```
git remote add origin <GITOPIA_HESABINIZDAKI_REMOTE_YAZAN_YER>
```
```
git push origin master
```
## Şimdi Tekrar Gitopia Sayfamıza Gidelim

- Issues kısmına tıklayalım.

![9](https://user-images.githubusercontent.com/98269269/208252285-2f9cef8a-99aa-4079-bee2-9ea6d4596440.png)

- Ardından 'New issue' diyelim.

![10](https://user-images.githubusercontent.com/98269269/208252308-a2d1cd46-8c7a-41f8-9c59-6610f12f6847.png)

- Şimdi ilgili yerleri dolduralım. Bir başlık belirleyelim ve 'Create issue' diyelim.

![11](https://user-images.githubusercontent.com/98269269/208252391-5a9a022d-8e65-4c56-8617-abe7af477699.png)

- Repomuzun içine girelim ve 'forks' seçeneğini seçelim.

![12](https://user-images.githubusercontent.com/98269269/208252458-b35acfc3-c2ac-45a3-a551-f8400a4e8e32.png)

- Şimdi de 'clone' yapalım.

![qqqq](https://user-images.githubusercontent.com/98269269/208424377-374ed9b9-4a6a-498e-a01a-d8047cdf454c.png)

- Şimdi işaretli yerdeki kodu kopyalayalım.

![qqqqq](https://user-images.githubusercontent.com/98269269/208425182-fd481f67-f946-4da0-aeb0-2a283a7fc752.png)

- Yukarıda kopyaladığımız kodu terminalimize yapıştırıyoruz.

![qqqqqq](https://user-images.githubusercontent.com/98269269/208425447-aa137a06-ebcc-4e40-ba06-c34910689641.png)

- Aşağıdaki kodu terminalimize yapıştırıyoruz.
```
cd <REPO_ADINIZ>
```

- Aşağıdaki kodlarla devam ediyoruz.

```
git checkout -b dev
```

```
vim README.md
```

- Yukarıdaki kodu yazınca işaretlediğim yerdeki yazım yanlışını düzeltiyoruz.

![zzzz](https://user-images.githubusercontent.com/98269269/208426476-5ef7ea5f-7fc6-44e8-9c18-61bed490692c.png)

- Devam ediyoruz.

```
git add README.md
```

```
git commit -m "fix typo"
```

```
git push origin dev
```

- Bu işlemlerden sonra Gitopia sayfamıza gidiyoruz ve repomuza tıklıyoruz. Açılan sayfada işaretlediğim yere tıklayarak 'dev' seçeneğini seçiyoruz.

![za](https://user-images.githubusercontent.com/98269269/208427022-7fe43b2e-1a59-4f7a-87d4-e46e0a51b9a6.png)

- Son olarak 'pull requests' yapalım. İşaretlediğim yerlere sırasıyla tıklıyoruz.

![zaa](https://user-images.githubusercontent.com/98269269/208427332-b6007ec6-162f-4808-be78-69ae14eac6cb.png)

- Ardından işaretli yere tıklıyoruz.

![qw](https://user-images.githubusercontent.com/98269269/208427817-ec3419b0-c572-467e-a1e1-34abee8aa778.png)

- Sonra aşağıdaki işaretli yeri seçiyoruz.

![qwe](https://user-images.githubusercontent.com/98269269/208428009-7eba88cf-ecb7-4e8f-9bf7-be1eb86b08f4.png)

- 'Create pull request' yazısına tıklıyoruz.

![q](https://user-images.githubusercontent.com/98269269/208428207-8f5ea5f7-a21c-4fc4-87c0-1341aed02d61.png)

- Sırasıyla aşağıdaki işlemleri yapıyoruz. 1 numaralı yere bir başlık belirliyoruz ve sonuna README yazmayı unutmuyoruz.

![qa](https://user-images.githubusercontent.com/98269269/208428517-1ecb66f0-5fd4-44da-a83a-f66cb0705787.png)

- Son olarak 'Merge Pull Request' yapıyoruz ve işlemi sonlandırıyoruz.

![qas](https://user-images.githubusercontent.com/98269269/208428881-1144e8d6-6fda-406f-bbd1-b3ccaade39fb.png)

- Umarım anlaşılır olmuştur. Cüzdan oluşturmadan tutun da tüm adımları tane tane anlatmaya çalıştım. Uzun bir süredir Gitopia testneti için node çalıştırıyoruz ve bu işlemin de faydası olacağını düşündüm. Herkese kolay gelsin.
- Aynı zamanda profilimde detaylı bir şekilde 'Gitopia-Cuzdan' adlı repoma da ulaşabilirsiniz.
