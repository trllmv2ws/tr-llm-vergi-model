Eğitim Süreci ve Karar Değişimleri
Eğitim yalnızca Wikipedia verisiyle başlatıldı; 12 partlık pretraining sonunda başarılı sonuçlar alındı.

Ardından opensubtitles + sözlük + Wikipedia verilerinin birlikte eğitilmesi planlandı ve bu yapı 120 part boyunca test edildi. Bu model kenara alındı.

Modelin ilk veri etkisi üzerine yeniden planlama yapıldı; wiki → sözlük → opensubtitles sıralaması tasarlandı ancak daha sonra sadece Wikipedia + sözlük yapısına karar verildi.

Veri kalitesinde başlık eksikliği, truncation ve karakter problemi fark edilince süreç temizlenerek sıfırdan yeniden başlatıldı. Tokenizer yeniden eğitildi.

Yeni eğitim linear scheduler, 5e-5 learning rate ve 3 epoch üzerinden yapılandırıldı. 120 part Wikipedia + 2 part sözlük verisi ile tamamlandı.

Preplexity ölçümleri ve otomatik scoring aracı ile 122 farklı model karşılaştırıldı.

Model çıktıları “doğruluk, bağlam takibi, dilbilgisi” gibi kriterlerle puanlanarak değerlendirildi. En iyi sonuç veren model part_114 olarak belirlendi.

Final modelde yalnızca Wikipedia verisi kullanıldı.

Diyalog ihtiyacı için 500 satırlık özel bir set hazırlandı ve fine-tune aşamasında kullanıldı.

Aritmetik, kanun hesaplamaları ve senaryolarla birlikte özel QA setleri ile fine-tune adımı tamamlandı.

Kanun verileri başlangıçta 13 farklı formata bölündü, sonrasında format sayısı azaltıldı ve sliding window yöntemi ile bağlam korunması sağlandı.
