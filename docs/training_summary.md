# Eğitim Süreci ve Karar Değişimleri

Model eğitimi ilk olarak yalnızca Wikipedia verisi ile başlatıldı. 12 partlık ön eğitim sonunda başarılı çıktılar elde edildi. Süreç, aşağıdaki aşamalardan geçti:

### Erken Aşama
- Wikipedia + sözlük + opensubtitles şeklinde karma bir yapı denendi.
- Zincirleme part yapısından schedule tabanlı otomasyon sistemine geçildi.
- 120 part opensubtitles verisiyle eğitim yapıldı ancak bu model kenara alındı.

### Strateji Değişimi
- Modelin ilk veri ile etkileşiminin güçlü olması sebebiyle, veri sıralaması yeniden düzenlendi.
- Sözlük → opensubtitles → Wikipedia gibi sıralamalar denendi, ancak en sağlıklı sonucun yalnızca Wikipedia verisiyle alındığı gözlemlendi.

### Veri Kalitesi Tespiti
- Verilerde başlık eksikliği, truncation kaynaklı bilgi kaybı, Türkçe dışı karakter sorunları tespit edildi.
- Clean ve normalize işlemleri yapılarak veri yapısı sıfırdan yeniden kuruldu.
- Yeni tokenizer eğitildi, veri yeniden partlandırıldı.

### Yeniden Eğitim Aşaması
- Cosine scheduler (2e-5) yerine linear (5e-5) scheduler kullanıldı.
- 3 epoch üzerinden planlanan eğitimde ilk 12 partta kalite artışı gözlemlendi ve devam kararı alındı.

### Eğitim Doygunluğu ve Final Seçimi
- Part 67–80 arasında eğitimin durağanlaştığı gözlemlendi.
- Kalan partlar veri içeriği açısından incelendi, yeterince farklı içerik bulunduğu için eğitim tamamlandı.
- Toplam: 120 part Wikipedia + 2 part sözlük verisi ile eğitim sonlandırıldı.

### Değerlendirme ve Model Seçimi
- 122 modeli karşılaştıran otomatik bir puanlama aracı geliştirildi.
- Doğruluk, bağlam takibi, Türkçe akıcılığı gibi kriterlerle en iyi model `part_114` olarak belirlendi.
- Final model yalnızca Wikipedia verisiyle eğitilmiştir.

### Fine-Tune Aşaması
- El yapımı 500 satırlık diyalog verisi ile desteklenen özel QA, aritmetik ve yasa formatlı verilerle fine-tune yapıldı.
- Kanun verisi ilk olarak 13 farklı formatta parçalandı, sonrasında bağlam korunarak sliding window yapısıyla düzenlendi.
