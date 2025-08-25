# sed
metin üzerinde bul-değiştir, ekle, sil, dönüştürme işlemleri yapmak için kullanılan araçtır 
* satır satır çalışır dosyayı değiştirmeden çıktı üretebiliriz
* -i ile kalıcı olarak değiştirilebilir.
* 
# Sed Komutları ve Açıklamaları

| İşlem | Açıklama | Örnek Komut |
|-------|----------|-------------|
| Basit bul-değiştir |  eski kelimeyi yeni ile değiştirir | ```sed 's/eski/yeni/' file.txt``` |
| Tüm eşleşmeleri değiştirme | Satırdaki tüm “eski” kelimelerini “yeni” ile değiştirir | ```sed 's/eski/yeni/g' file.txt``` |
| Satır silme | Belirli desene uyan satırları siler | ```sed '/pattern/d' file.txt``` |
| Satır ekleme (üstüne) | Belirli satırın üstüne yeni satır ekler | ```sed '2i Bu satır 2. satırın üstüne eklendi' file.txt``` |
| Satır ekleme (altına) | Belirli satırın altına yeni satır ekler | ```sed '3a Bu satır 3. satırın altına eklendi' file.txt``` |
| Satırı değiştirme | Belirli satırı tamamen değiştirir | ```sed '3c Bu satır 3. satırı değiştirdi' file.txt``` |
| Dosyayı kalıcı değiştirme | `-i` ile değişiklikleri dosyaya uygular | ```sed -i 's/eski/yeni/g' file.txt``` |

# AWK ve SED Karşılaştırması

| Özellik / Araç | `awk` | `sed` |
|----------------|-------|-------|
| **Amaç** | Satır ve sütun bazlı veri işleme, filtreleme, sayma, toplama, hesaplama | Satır bazlı metin düzenleme: bul-değiştir, ekle, sil, değiştirme |
| **Veri yapısı** | Otomatik olarak satırları sütunlara ayırır (`$1`, `$2`, `$NF`) | Satırları bütün olarak işler; sütun bilgisi yoktur |
| **Matematik / hesaplama** | Evet, toplam, ortalama, sayaç gibi işlemler yapılabilir | Hayır, matematiksel hesaplama yok |
| **Filtreleme** | Sütun bazlı koşullarla filtreleme yapılabilir | Sadece satır içeriğine göre eşleşme (regex) ile filtreleme yapılır |
| **Değişiklik yapma** | Genellikle çıktı üretir, dosyayı değiştirmez | `-i` ile dosya üzerinde kalıcı değişiklik yapılabilir |
| **Kullanım örneği** | IP adreslerini saymak, log dosyasındaki HTTP durumlarını analiz etmek | Log dosyasında belirli satırları silmek, bir kelimeyi topluca değiştirmek |

**Özet:**  
- `awk` : Veri analizi ve sütun/satır bazlı hesaplamalar için idealdir.  
- `sed` :Metin düzenleme ve hızlı satır bazlı değişiklikler için idealdir.  

**Pratik Örnekler:**  
- Logdaki IP istek sayılarını saymak: `awk`  
- Logdaki tüm 401 hatalarını "HATA" ile değiştirmek :`sed`  
