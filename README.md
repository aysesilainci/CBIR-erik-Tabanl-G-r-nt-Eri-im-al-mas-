# CIFAR-10 Content-Based Image Retrieval (CBIR) System

Bu proje, **CIFAR-10** veri seti üzerinde **ResNet-50** derin öğrenme modelini özellik çıkarıcı olarak kullanarak geliştirilmiş uçtan uca bir İçerik Tabanlı Görüntü Erişim (CBIR) sistemidir. Proje kapsamında özellik çıkarma, mesafe metrikleri ile benzeşim arama, performans değerlendirme (Precision, Recall, F1, mAP) ve sonuç görselleştirme adımları gerçekleştirilmiştir.

## 🚀 Projenin Amacı ve Öne Çıkan Özellikler
*   **Derin Özellik Çıkarımı:** ImageNet ağırlıklarıyla önceden eğitilmiş ResNet-50 modelinin sınıflandırma katmanı devre dışı bırakılarak görsellerden 2048 boyutlu öznitelik vektörleri elde edilmiştir.
*   **Çoklu Mesafe Metriği:** Sorgu ve veritabanı görselleri arasındaki benzerlikler **Öklid (Euclidean)**, **Kosinüs (Cosine)** ve **Manhattan** mesafeleri ile karşılaştırılmıştır.
*   **Performans Metrikleri:** Sistem; $Precision@K$, $Recall@K$, $F1@K$ ve Ortalama Hassasiyet ($mAP@K$) metrikleriyle değerlendirilmiştir.
*   **Görselleştirme:** En yakın eşleşen (Top-K) görselleri ve arama sürelerini kıyaslayan otomatik grafik/tablo modülleri içerir.

## 📊 Veri Seti
Projede kullanılan **CIFAR-10** veri setinin dağılımı:
*   **Eğitim (Veritabanı) Görüntüsü:** 50.000 adet (10 sınıftan 5000'er adet)
*   **Test (Sorgu) Görüntüsü:** 10.000 adet (10 sınıftan 1000'er adet)
*   **Sınıflar:** `airplane`, `automobile`, `bird`, `cat`, `deer`, `dog`, `frog`, `horse`, `ship`, `truck`

## 🛠️ Metodoloji ve İş Akışı
1.  **Özellik Çıkarma:** Görüntüler ResNet-50 transformasyonlarına uygun hale getirilerek 2048 boyutlu vektörlere dönüştürülmüştür.
2.  **İndeksleme:** Elde edilen veritabanı ve sorgu matrisleri `.npy` formatında kaydedilmiştir.
3.  **Arama:** Belirlenen mesafe metrikleri üzerinden en yakın komşular taranmıştır.
4.  **Değerlendirme:** Farklı veritabanı boyutları ve metrikler için sorgu süreleri (ms) ile başarı skorları raporlanmıştır.

## 📈 Deneysel Sonuçlar
*   **En İyi Doğruluk:** Kosinüs (Cosine) mesafesi, en yüksek $Precision@K$ (%73.23) ve $mAP@K$ (%67.62) skorlarını sağlamıştır.
*   **En Hızlı Sorgu:** Öklid (Euclidean) mesafesi ortalama ~15.5 ms sorgu süresi sunmuştur.

## 💻 Kurulum ve Çalıştırma
Projeyi çalıştırmak için gerekli kütüphaneler:

```bash
pip install torch torchvision scikit-learn scikit-image pandas matplotlib pillow
