




# Laravel Netgsm Sabit Telefon Entegrasyonu

Netgsm ses paket aboneliği bulunan kullanıcılarımız için laravel paketidir.  

# İletişim & Destek

 Netgsm API Servisi ile alakalı tüm sorularınızı ve önerilerinizi teknikdestek@netgsm.com.tr adresine iletebilirsiniz.


# Doküman 
https://www.netgsm.com.tr/dokuman/
 API Servisi için hazırlanmış kapsamlı dokümana ve farklı yazılım dillerinde örnek amaçlı hazırlanmış örnek kodlamalara 
 [https://www.netgsm.com.tr/dokuman](https://www.netgsm.com.tr/dokuman) adresinden ulaşabilirsiniz.


### Supported Laravel Versions

Laravel 6.x, Laravel 7.x, Laravel 8.x, Laravel 9.x, 

### Supported Php Versions

PHP 7.2.5 ve üzeri

### Kurulum

composer require netgsm/voicesms 

.env  dosyası içerisinde NETGSM ABONELİK bilgileriniz tanımlanması zorunludur.  

<b>NETGSM_USERCODE=""</b>  
<b>NETGSM_PASSWORD=""</b>  

### Görüşme Detayı

Gelen ve giden aramalarınızı bu servisi kullanarak sorgulayabilirsiniz.

```    
        use Netgsm\Voipphone\voip;
        $sabittelefon=new voip;
        $data["date"]="260120230900";
        $data["direction"]=4;
        $sonuc=$sabittelefon->gorusmedetayi($data);
        
        echo '<pre>';
            print_r($sonuc);
        echo '<pre>';
```

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

### Telesekreter Mesajları

Abone numaranıza gelen sesli mesajları sorguyabilirsiniz.

```     
        use Netgsm\Voipphone\voip;
        $telesekreter=new voip;
        $sonuc=$telesekreter->telesekretermesaj();
        echo '<pre>';
            print_r($sonuc);
        echo '<pre>';
        
```





<table>
<thead>
<tr>
<th>Hata Kodu</th>
<th>Anlamı</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>30</code></td>
<td>Geçersiz kullanıcı adı , şifre veya kullanıcınızın API erişim izninin olmadığını gösterir.Ayrıca eğer API erişiminizde IP sınırlaması yaptıysanız ve sınırladığınız ip dışında gönderim sağlıyorsanız 30 hata kodunu alırsınız. API erişim izninizi veya IP sınırlamanızı , web arayüzümüzden; sağ üst köşede bulunan ayarlar&gt; API işlemleri menüsunden kontrol edebilirsiniz.</td>
</tr>
<tr>
<td><code>40</code></td>
<td>Arama kriterlerinize göre listelenecek kayıt olmadığını ifade eder.</td>
</tr>
<tr>
<td><code>50</code></td>
<td>Arama kriterlerindeki tarih formatının hatalı olduğunu ifade eder. (ddMMyyyyHHmm)</td>
</tr>
<tr>
<td><code>60</code></td>
<td>Arama kiterlerindeki startdate ve stopdate zaman farkının 30 günden fazla olduğunu ifade eder.</td>
</tr>
<tr>
<td><code>70</code></td>
<td>Hatalı sorgulama. Gönderdiğiniz parametrelerden birisi hatalı veya zorunlu alanlardan birinin eksik olduğunu ifade eder.</td>
</tr>
</tbody>
</table>
