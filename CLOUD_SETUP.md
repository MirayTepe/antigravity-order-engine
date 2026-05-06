# ☁️ Google Cloud Bağlantı ve Kredi Kurulumu

Bu doküman, projeyi belirttiğiniz **TryGCP - Instrumentless credit** ($5.00) ile Google Cloud'a bağlamak ve kullanmak için gereken adımları içerir.

## 💳 Kredi Bilgileri
- **Kredi Adı:** TryGCP - Instrumentless credit
- **Promosyon Kodu:** `KH35L1PY2387EFL0`
- **Durum:** 84% Kullanılabilir ($4.22 kalan)
- **Son Kullanma:** 6 Ekim 2026

## 🚀 Bağlantı Adımları

### 1. Billing Account ID'nizi Bulun
Kredinin bağlı olduğu Faturalandırma Hesabı ID'sini (Format: `XXXXXX-XXXXXX-XXXXXX`) öğrenmek için:
1. [GCP Billing Console](https://console.cloud.google.com/billing)'a gidin.
2. "TryGCP - Instrumentless credit"in yanındaki Faturalandırma Hesabı ID'sini kopyalayın.

### 2. Projeyi Cloud'a Bağlayın (CLI üzerinden)
Terminalinizde aşağıdaki komutları sırasıyla çalıştırarak projeyi oluşturun ve krediye bağlayın:

```powershell
# 1. Yeni bir GCP projesi oluşturun
gcloud projects create antigravity-order-engine --name="Antigravity Order Engine"

# 2. Projeyi faturalandırma hesabına bağlayın
# [BILLING_ACCOUNT_ID] kısmını yukarıda bulduğunuz ID ile değiştirin
gcloud billing projects link antigravity-order-engine --billing-account=[BILLING_ACCOUNT_ID]

# 3. Gerekli servisleri etkinleştirin (Örn: Cloud Run)
gcloud services enable run.googleapis.com cloudbuild.googleapis.com --project=antigravity-order-engine
```

### 3. Dağıtım (Deployment) Seçenekleri

#### Seçenek A: Google App Engine (Kolay)
Proje kök dizinindeki `app.yaml` dosyasını kullanarak:
```powershell
gcloud app deploy --project=antigravity-order-engine
```

#### Seçenek B: Cloud Run (Modern)
Docker kullanarak dağıtmak isterseniz:
```powershell
gcloud run deploy order-engine --source . --project=antigravity-order-engine --region=us-central1
```

## ⚠️ Önemli Notlar
- Bu kredi **"Instrumentless"** olduğu için kredi kartı gerektirmez, ancak $5.00 limitine ulaştığınızda servisleriniz duracaktır.
- `order_service.py` şu an bir kütüphane/script mantığında çalışmaktadır. Cloud üzerinde bir HTTP endpoint olarak sunmak isterseniz bir web framework (Flask/FastAPI) eklemeniz önerilir.

---
*Proje otomatik olarak `antigravity-order-engine` GitHub reposuna da push edilmiştir.*
