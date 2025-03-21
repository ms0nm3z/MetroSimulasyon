# Metro Ağı Simülasyonu

Bu proje, Python kullanılarak geliştirilen bir "metro ağı simülasyonudur". 
Metro istasyonları arasında en kısa ve en hızlı rotayı hesaplamak için 
"Graph veri yapısı" , "BFS algoritması" ve "A* algoritması" kullanılmaktadır.

- BFS algoritması : 
 graf (graph) veya ağaç (tree) yapılarında en kısa yolu bulmak veya veriyi keşfetmek
 için kullanılan arama algoritmalarından biridir.

 📌 BFS Algoritmasının Çalışma Prensibi
    Bir başlangıç düğümü (node) seçilir.
    Bir kuyruk (queue) kullanılarak keşfedilecek düğümler saklanır.
    İlk düğüm kuyruktan çıkarılır ve işlenir.
    İşlenen düğümün komşuları keşfedilir ve daha önce ziyaret edilmemişlerse kuyruğa eklenir.
    Tüm düğümler işlenene kadar adımlar devam eder.

- A* algoritması : En kısa ve en hızlı yolu bulmak için kullanılan 
bilgi güdümlü (heuristic-based) bir arama algoritmasıdır.
Her adımda toplam maliyeti (g) ve tahmini maliyeti (h) göz önünde bulundurur.


## Yapı
1. Istasyon (Class)
Metro İstasyonuna ait bilgilerin bulunduğu sınıftır. 
    Özellikler:
    idx: İstasyon eşsiz Id (örneğin "K1")
    ad: İstasyon adı (örneğin "Kızılay")
    hat: Hangi metro hattında olduğu (örneğin "Kırmızı Hat")
    komsular: Bağlantılı istasyonlar ve aralarındaki süre bilgisi (örn. [(istasyon, süre)])

    Metod:
    - komsu_ekle(self, istasyon: 'Istasyon', sure: int):
    İstasyona komşu istasyon bilgilerini eklemek için kullanılır.
    Örnek:

           istasyon1.komsu_ekle(istasyon2, sure)


 2.Metro Ağı  ( Class )
Bu sınıf, bütün metro istasyonlarını ve hatları saklar.
Metro hattı üzerinde istasyonlar arasında bağlantılar (yollar) tanımlanabilir.
 
  Özellikler
    istasyonlar (Dictionary): İstasyonların bilgisi tutulur
    hatlar (Dictionary): Metro hatlarının bilgisi tutulur

  Metod:
    - istasyon_ekle(self, idx: str, ad: str, hat: str) -> None:
    Metro ağına yeni bir istasyon ekler
    Örnek: 
    
        metro.istasyon_ekle("K1", "Kızılay", "Kırmızı Hat")

  - baglanti_ekle(self, istasyon1_id: str, istasyon2_id: str, sure: int) : 
    İki komşu istasyon arasındaki bağlantıyı oluşturmak
    ve istasyonlar arası süre bilgisini eklemek için kullanılır
      Örnek :


        metro.baglanti_ekle("T1", "T2", 7)

 -en_az_aktarma_bul(self, baslangic_id: str, hedef_id: str) -> Optional[List[Istasyon]]
     istenen iki istasyon arasındaki en az aktarmalı rotayı 
     BFS algoritması kullanılarak hesaplar.
        Örnek : 
        
        rota = metro.en_az_aktarma_bul("M1", "K4")

  - en_hizli_rota_bul(self, baslangic_id: str, hedef_id: str) -> Optional[Tuple[List[Istasyon], int]]:
    istenen iki istasyon arasındaki en hızlı rotayı
    "A* algoritması" kullanılarak hesaplar .
         Örnek:

        sonuc = metro.en_hizli_rota_bul("T4", "M1")



## Sonuç  
 - Metro ağları ve toplu taşıma sistemleri için kullanılabilir.
 - Farklı şehirler, yeni hatlar ve istasyonlar kolayca eklenebilir.
 
## Öneriler
- Hatların istayondan kalkış saatleri yapıya eklenebilir, 
en hızlı rota fonksiyonu varış ve kalkış zamanlarını dikkkate alacak
şekilde düzenlenebilir

