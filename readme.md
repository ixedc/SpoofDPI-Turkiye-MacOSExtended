# [SpoofDPI-Turkiye](https://github.com/renardev/SpoofDPI-Turkiye "SpoofDPI-Turkiye GitHub sayfası") MacOS Extended

[SpoofDPI-Turkiye](https://github.com/renardev/SpoofDPI-Turkiye "SpoofDPI-Turkiye GitHub sayfası") forkunun MacOS'da bir servis gibi çalışması için geliştirilmiştir. Otomatik olarak Google DNS (8.8.8.8:53) kullanmaktadır.
<br>
## <ins>KURULUM</ins>

<details><summary>Kolay Kurulum</summary>

- [Bu link](https://github.com/ixedc/SpoofDPI-Turkiye-MacOSExtended/releases "İndirme Linki") üzerinden "Assets" kısmına tıklayıp spoofdpi.app.zip dosyasını indirin
- Finder > İndirilenler'e gidin ve spoofdpi uygulamasını (eğer hala zip şeklindeyse çift tıklayıp zipten çıkartın) Finder > Uygulamalar klasörüne sürükle bırak yapın.
- spoofdpi uygulamasını açın, çıkan uyarı mesajına bitti diyin ve Sistem Ayarları > Gizlilik ve Güvenlik kısmında aşağıya inip uygulamaya izin verin.
- Sol üstteki Apple logosu > Sistem Ayarları... > Genel > Oturum Açma Ögeleri ve Genişletmeler kısmına gelin ve +(artı) butonuna tıklayıp Uygulamalar klasöründeki spoofdpi uygulamasını seçin.
- Artık [SpoofDPI-Turkiye](https://github.com/renardev/SpoofDPI-Turkiye "SpoofDPI-Turkiye GitHub sayfası") sistem açılınca otomatik olarak arka planda çalışmaya başlayacaktır.
</details>
<details><summary>Manuel Kurulum</summary>

- Mac'inizde kurulu olan Betik Düzenleyici uygulamasını açın.
- Sol taraftaki menüden Uygulamalar klasörünü seçin.
- Yeni Belge'yi seçin.
```
repeat
	try
		-- İnternet bağlantısını kontrol etmek için bir test (Google DNS'e ping atılır)
		do shell script "ping -c 1 8.8.8.8 > /dev/null 2>&1"
		
		-- Eğer ping başarılı olursa komut çalıştırılır ve döngüden çıkılır
		do shell script "/Applications/spoofdpi.app/Contents/MacOS/spoofdpi -dns-addr 8.8.8.8 --dns-port 53 -silent"
		exit repeat
	on error
		-- Ping başarısız olursa 1 saniye bekle
		delay 1
	end try
end repeat
```
- Yukarıda verilen kodu beyaz alana yapıştırın.
- Command + S tuş kombinasyonu veya Dosya > Kaydet ile betiği istediğiniz bir isimde örn: spoofdpi-tr Uygulamalar klasörüne Uygulama olarak kaydedin. (Betik yerine Uygulama'yı seçin)
- Finder > Uygulamalar klasörüne gelin ve kaydettiğiniz dosyayı sağ tık > Paket İçeriğini Göster ile açıp Contents klasöründeki info.plist dosyasını sağ tık > Şununla Aç > Uygulamalar klasöründe en aşağıkaydıralım TextEdit'i bulana kadar ve bulunca TextEdit ile açalım.
- Dosyanın son 2 satırı aşağıdaki gibi olacaktır.
```
</dict>
</plist>  
```
- Bu 2 satırın üstüne aşağıdaki kodu yapıştırın. Bu kod sayesinde uygulama size gözükmeden arka planda çalışacaktır.
```
<key>LSUIElement</key>
<true/>
```
- Sol üstteki Apple logosu > Sistem Ayarları... > Genel > Oturum Açma Ögeleri ve Genişletmeler kısmına gelin ve +(artı) butonuna tıklayıp Uygulamalar klasöründeki spoofdpi uygulamasını seçin.
- Artık [SpoofDPI-Turkiye](https://github.com/renardev/SpoofDPI-Turkiye "SpoofDPI-Turkiye GitHub sayfası") sistem açılınca otomatik olarak arka planda çalışmaya başlayacaktır.
</details>

## <ins>KALDIRMA</ins>

- Finder > Uygulamalar klasöründeki spoofdpi veya kendi isimlendirdiğiniz dosyayı çöpe atın ve Sistem Ayarları > Genel > Oturum Açma Ögeleri ve Genişletmeler'e eklediğiniz spoofdpi veya kendi isimlendirdiğiniz uygulamaya tıklayıp - butonuna basın.

## <ins>GÜNCELLEME</ins>
- [SpoofDPI-Turkiye](https://github.com/renardev/SpoofDPI-Turkiye "SpoofDPI-Turkiye GitHub sayfası") sayfasından güncel versiyonu indirin.
- Finder > Uygulamalar klasörüne gidip önceden oluşturulan spoofdpi uygulamasını sağ tık > Paket İçeriğini Göster > Contents > MacOS klasörüne gidip spoofdpi dosyasını silin ve yenisini buraya taşıyın. (Aynı isimde olmasına dikkat edin.)

## <ins>PARAMETRE DEĞİŞTİRME</ins>
- MacOS'da bulunan Betik Düzenleyici uygulamasını açın.
- Uygulamalar klasöründeki spoofdpi uygulamasını açın.
```
do shell script "/Applications/spoofdpi.app/Contents/MacOS/spoofdpi -dns-addr 8.8.8.8 --dns-port 53 -silent"
```
- Üstteki kodun bulunduğu yerdeki parametreleri dilediğiniz gibi değiştirin.
- Command + S ile dosyayı kaydedin.
- Bilgisayarınız her açıldığında yeni parametreler ile çalışacaktır. Bilgisayarı kapatıp açmadan yeni parametrelerle çalıştırmak için Etkinlik Monitörü uygulamasından spoofdpi ile aratıp işlemleri seçin ve durdur butonuna tıklayın.