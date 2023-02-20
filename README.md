




# Laravel & Symfony Netgsm Sabit Telefon Entegrasyonu

Netgsm ses paket aboneliği bulunan kullanıcılarımız için composer paketidir.  
## İçindekiler
- [İletişim & Destek](#i̇letişim--destek)
- [Supported](#Supported-Laravel-Versions)
- [Kurulum](#kurulum)
- [Görüşme Detayı](#görüşme-detayı)
- [Telesekreter Mesajları](#telesekreter-mesajları)
# İletişim & Destek

 Netgsm API Servisi ile alakalı tüm sorularınızı ve önerilerinizi teknikdestek@netgsm.com.tr adresine iletebilirsiniz.


# Döküman 
https://www.netgsm.com.tr/dokuman/
 API Servisi için hazırlanmış kapsamlı dokümana ve farklı yazılım dillerinde örnek amaçlı hazırlanmış örnek kodlamalara 
 [https://www.netgsm.com.tr/dokuman](https://www.netgsm.com.tr/dokuman) adresinden ulaşabilirsiniz.


### Supported Laravel Versions

Laravel 6.x, Laravel 7.x, Laravel 8.x, Laravel 9.x, 

### Supported Lumen Versions

Lumen 6.x, Lumen 7.x, Lumen 8.x, Lumen 9.x, 

### Supported Symfony Versions

Symfony 4.x, Symfony 5.x, Symfony 6.x

### Supported Php Versions

PHP 7.2.5 ve üzeri

### Kurulum

<b>composer require netgsm/voipphone</b>

.env  dosyası içerisinde NETGSM ABONELİK bilgileriniz tanımlanması zorunludur.  

<b>NETGSM_USERCODE=""</b>  
<b>NETGSM_PASSWORD=""</b>  

### Görüşme Detayı

Gelen ve giden aramalarınızı bu servisi kullanarak sorgulayabilirsiniz.

<table>
<thead>
<tr>
<th>Değişken</th>
<th>Anlamı</th>
</tr>
</thead>
<tbody>

<tr>
<td><code>date</code></td>
<td>Aramanın yapıldığı tarih formatı ddMMyyyyHHmm şeklinde olmalıdır.  <em>(Boş bırakılırsa sorgulama yapılan günün kayıtları listelenir.)</em></td>
</tr>
<tr>
<td><code>direction</code></td>
<td>Arama yönünü belirlemek için kullanılır. Gönderebileceğiniz değerleri aşağıdaki <strong>Direction (Arama Yönü) Açıklamaları</strong> listeden bulabilirsiniz.</td>
</tr>
</tbody>
</table>




```php    
        use Netgsm\Voipphone\voip;
        $sabittelefon=new voip;
        $data=array(
            'date'=>'160220230900',
            'direction'=>2
        );     
        $sonuc=$sabittelefon->gorusmedetayi($data);
        dd($sonuc);
        die;
```

#### Başarılı Sonuç Örneği

```php
Array
(
    [0] => Array
        (
            [number] => 549xxxxxxx
            [date] => 03.02.2023 21:18:54
            [sure] => 00:00:08
            [yoncode] => 1
            [yonanlam] => Gelen Aramalar
        )

    [1] => Array
        (
            [number] => 549xxxxxxx
            [date] => 03.02.2023 21:13:45
            [sure] => 00:00:00
            [yoncode] => 3
            [yonanlam] => Cevapsız Aramalar
        )

   

)
```
<table>
<thead>
<tr>
<th>Kod</th>
<th>Anlamı</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>1</code></td>
<td>Gelen Aramalar</td>
</tr>
<tr>
<td><code>2</code></td>
<td>Giden Aramalar</td>
</tr>
<tr>
<td><code>3</code></td>
<td>Cevapsız Aramalar</td>
</tr>
<tr>
<td><code>4</code></td>
<td>Bütün Aramalar</td>
</tr>
</tbody>
</table>

#### Başarısız Sonuç Örneği

```php
Array
(
    [code] => 100
    [durum] => Sistem hatası, sınır aşımı. (dakikada en fazla 2 kez sorgulanabilir.)
)
```




### Telesekreter Mesajları

Abone numaranıza gelen sesli mesajları sorguyabilirsiniz.

```php     
        use Netgsm\Voipphone\voip;
        $telesekreter=new voip;
        $sonuc=$telesekreter->telesekretermesaj();
        dd($sonuc);
        die;
        
```

####  Başarılı istek örnek sonuç
```php
Array
(
    [0] => Array
        (
            [number] =>  
            [tarih] =>  08.08.2022 11:57 
            [dosya] =>  http://sesdosya.netgsm.com.tr/upload.php?tip=7&a=24f4431869f3d493271eb8s212vs....... 
        )

    [1] => Array
        (
            [number] =>  
            [tarih] =>  08.08.2022 11:29 
            [dosya] =>  http://sesdosya.netgsm.com.tr/upload.php?tip=7&a=24f44318xasavs3.....
        )
 )
```
####  Başarısız istek örnek sonuç

```php
Array
(
    [durum] => Geçersiz kullanıcı adı , şifre veya kullanıcınızın API erişim izninin olmadığını gösterir.  
    Ayrıca eğer API erişiminizde IP sınırlaması yaptıysanız ve sınırladığınız ip dışında gönderim  
    sağlıyorsanız 30 hata kodunu alırsınız. API erişim izninizi veya IP sınırlamanızı , web arayüzümüzden;  
    sağ üst köşede bulunan ayarlar> API işlemleri menüsunden kontrol edebilirsiniz.
    [code] => 30
)

```
