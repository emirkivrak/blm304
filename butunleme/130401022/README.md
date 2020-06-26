## Nasıl çalışır ?

  Kullanıcının girdiği makina adına paket göndermek için `UDP` paketi oluşturur. `UDP` paketini oluşturduktan sonra `zaman_asimi = struct.pack("ll", 999, 0)` kodu yaklaşık 1 sn bekleme süresi ile paketleri oluşturup ilgini makinanın ip'sine gönderir ve gelen cevapları `İCMP` paketi olarak alır.
Aynı zamanda gelen cevabı almak için `İCMP` paketi oluşturur. `mesaj , adres = aliciPaket.recvfrom(BUFFER_SIZE)` kodu ile `İCMP` paketine gelen mesajın adresini kaydeder. Eğer `İCMP` paketine cevap gelmemiş ise yönlendiricinin ip'sini gizlenmiş varsayılır ve adres değerine `tll + *` yazılır.
Bu adres, ilgili time to live(ttl) değerine karşılık gelen yönlendirici adresidir. 
Daha sonra ilgili ttl numarasını ve yönlendirici adresini `rota.txt` adlı metin
belgesine yazar. Bu işlemler, son yönlendirici adresine ya da `ttl = 30` değerine ulaşana kadar devam eder. Bütün sonuçlar `rota.txt` dosyasına yazdırılmış olur.

## Nasıl kullanılır ?

  Örnek kullanım olarak ubuntu işletim sisteminde :   `sudo python3 rota.py makinaAdi` şeklinde çalıştırılır. Makina adının eksik yada yanlış girilmesi durumunda kod çalışmayıp kendi kendini imha edecektir. Bu durumda doğru makina adı ile tekrar deneyiniz.
