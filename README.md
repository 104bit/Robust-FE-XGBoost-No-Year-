# Formula 1 Pit Stop Prediction
[English README](README_EN.md)

Bu proje, Formula 1 yarış verileri kullanılarak bir aracın bir sonraki turda pit stop yapıp yapmayacağını tahmin etmeyi amaçlar. Modelleme sürecinde XGBoost algoritması kullanılmıştır.

## Amaç

Hedef değişken `PitNextLap` olarak belirlenmiştir. Model; tur bilgisi, lastik ömrü, stint durumu, yarış ve sürücü bilgileri gibi değişkenlerden yararlanarak pit stop olasılığı üretir.

## Kullanılan Yöntem

Proje kapsamında aşağıdaki adımlar uygulanmıştır:

- Eğitim verisinin yüklenmesi
- Kategorik değişkenlerin modele uygun hale getirilmesi
- Sınıf dengesizliği için `scale_pos_weight` kullanılması
- XGBoost modeli ile sınıflandırma yapılması
- `Year` değişkeninin çıkarılarak zamansal aşırı öğrenmenin azaltılması
- Ek özellikler oluşturularak modelin güçlendirilmesi
- Test verisi için tahmin dosyası hazırlanması

## Özellik Mühendisliği

Modelde kullanılan ek özellikler şunlardır:

- `Rolling_3Lap_Time`: Son 3 turun ortalama tur zamanı
- `Stint_Position_Change`: Stint içindeki kümülatif pozisyon değişimi
- `Tyre_Stress_Ratio`: Lastik yaşının ilgili hamurun ortalama ömrüne oranı

## Kullanılan Teknolojiler

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib

## Çalıştırma

Gerekli kütüphaneleri yüklemek için:

```bash
pip install pandas numpy scikit-learn xgboost matplotlib
```

Notebook dosyasını çalıştırmak için:

```bash
jupyter notebook robust-fe-xgboost-no-year.ipynb
```

## Çıktı

Notebook çalıştırıldıktan sonra test verisi için tahmin sonuçlarını içeren aşağıdaki dosya oluşturulur:

```text
f1_pitstop_submission.csv
```

## Not

Bu çalışmada `Year` değişkeni modelden çıkarılmıştır. Böylece modelin belirli sezonları ezberlemesi yerine yarış stratejisi, lastik kullanımı ve tur performansı gibi daha genellenebilir bilgilerden öğrenmesi amaçlanmıştır.
