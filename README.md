# Türkçe Vergi LLM Projesi (GPT-2 Tabanlı)

Bu proje, Türkçe dilinde vergi, mali mevzuat ve sayısal içerikler üzerine uzmanlaşmış küçük boyutlu bir dil modeli (LLM) geliştirmeyi hedefler. GPT-2 mimarisi temel alınmış ve model sıfırdan Türkçe verilerle eğitilmiştir.

## Proje Özeti

- Model: GPT-2 Small (Türkçe tokenizer ile, sıfırdan eğitildi)
- Eğitim Yaklaşımı:
  - Pretraining: Türkçe Wikipedia, sözlük ve diyalog verileriyle sıfırdan genel dil eğitimi
  - Fine-tuning: Vergi, mali mevzuat, sayısal ve senaryo tabanlı verilerle özel alan uyarlaması
- Veri:
  - 2.000+ vergi QA çifti  
  - 36.000 sayısal/senaryo tabanlı örnek  
  - Diyalog ve kavram odaklı içerikler
- Eğitim Özellikleri:
  - Chain (zincirleme) fine-tune sistemi
  - Schedule tabanlı part bazlı otomasyon
  - Sliding window ve bağlam koruma stratejisi
- Başarı Oranı: QA setinde yaklaşık %80 doğruluk
- Sistem: Pop!_OS 22.04, 24GB RAM, GTX 1050 GPU

## Proje Amacı ve Motivasyon

Bu proje, yalnızca hazır bir model üzerine veri vermekten öteye geçerek, Türkçe bir dil modeli oluşturma sürecini en alt katmandan ele alma amacını taşır. Vergi, mevzuat, muhasebe ve hesaplama gibi kurallı ve bağlamsal alanlarda çalışan modellerin daha güvenilir yanıtlar vermesi için özel olarak yapılandırılmıştır.

Modelin tasarımı, sadece doğal dil üretimi değil, aynı zamanda analitik ve işlem tabanlı düşünme yetkinliği kazandırmayı hedefler.

## Dosya ve Klasör Yapısı

- `train_one_part.py` – Tek part eğitimi başlatan script
- `train_schedule_loop.py` – Zincirleme eğitim sürecini yöneten script
- `schedule.json` – Eğitim sıralaması ve ayarları
- `tokenizer/` – Eğitilmiş tokenizer dosyaları (paylaşılmadı)
- `data/` – Veri seti klasör yapısı (örnek yapılar paylaşılacak)
- `checkpoints/` – Model checkpoint dizinleri (private)
- `logs_chain/` – Eğitim logları

## Eğitim Komutları

```bash
# Tek part eğitimi
python train_one_part.py

# Zincirleme eğitim
python train_schedule_loop.py
