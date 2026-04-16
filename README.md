# 🔐 Steganografi: Görsele Görsel Saklama

Shamir's Secret Sharing (SSS) algoritması kullanarak bir görsel içine başka bir görseli gizleyen ve geri çıkaran React tabanlı bir web uygulaması.

## 📖 Proje Hakkında

Bu proje, **LSB (Least Significant Bit) steganografi** tekniği ile **Shamir's Secret Sharing** algoritmasını birleştirerek güvenli bir görsel gizleme sistemi sunar. Gizlenecek görsel önce SSS ile 6 farklı parçaya (share) bölünür, ardından bu parçalar bir taşıyıcı görselin en düşük anlamlı bitlerine gömülür. Geri çıkarma işlemi için herhangi 3 parça yeterlidir.

### ✨ Temel Özellikler

- **Encode (Gizleme):** Bir görseli SSS ile parçalara ayırıp taşıyıcı görsele gömme
- **Decode (Çıkarma):** 3 adet encode edilmiş görselden orijinal gizli görseli kurtarma
- **PSNR Hesaplama:** Orijinal ve stegano görsel arasındaki kalite farkını ölçme
- **Ayarlanabilir Bit Derinliği:** Piksellerde kaç bit kullanılacağını seçebilme
- **İndirme:** İşlenmiş görselleri PNG formatında indirme

## 🛠️ Teknoloji Yığını

| Teknoloji | Kullanım |
|-----------|----------|
| **React** | Kullanıcı arayüzü |
| **JavaScript (ES6+)** | Uygulama mantığı |
| **UPNG.js** | PNG kodlama/çözme |
| **Create React App** | Proje altyapısı |

## 📂 Proje Yapısı

```
steganografi-gorsele-gorsel-saklama/
├── public/
│   ├── index.html
│   ├── favicon.ico
│   └── manifest.json
├── src/
│   ├── components/
│   │   ├── EncodeForm.js        # Encode (gizleme) formu
│   │   ├── EncodeForm.css
│   │   ├── DecodeForm.js        # Decode (çıkarma) formu
│   │   ├── DecodeForm.css
│   │   ├── PsnrForm.js          # PSNR hesaplama formu
│   │   ├── PsnrForm.css
│   │   ├── ImageUploadBox.js    # Görsel yükleme bileşeni
│   │   ├── ImageUploadBox.css
│   │   ├── ImageDisplayBox.js   # Görsel gösterim bileşeni
│   │   └── ImageDisplayBox.css
│   ├── encodeWithSSS.js         # SSS encode/decode algoritması
│   ├── App.js                   # Ana uygulama bileşeni
│   ├── App.css
│   ├── index.js                 # Uygulama giriş noktası
│   └── index.css
├── package.json
└── README.md
```

## 🚀 Kurulum ve Çalıştırma

### Gereksinimler

- **Node.js** (v16 veya üzeri)
- **npm** (v8 veya üzeri)

### Kurulum

```bash
# Depoyu klonlayın
git clone https://github.com/AkerimC/steganografi-gorsele-gorsel-saklama.git

# Proje dizinine gidin
cd steganografi-gorsele-gorsel-saklama

# Bağımlılıkları yükleyin
npm install
```

### Çalıştırma

```bash
# Geliştirme sunucusunu başlatın
npm start
```

Uygulama varsayılan olarak `http://localhost:3000` adresinde açılacaktır.

### Derleme (Production)

```bash
npm run build
```

## 📋 Kullanım

### 1. Encode (Görsele Görsel Gizleme)

1. **Encode** sekmesine gidin.
2. Bit derinliğini ayarlayın (varsayılan: 2 bit).
3. **Ana Resim** alanına gizlenecek görseli yükleyin — SSS ile 6 parçaya ayrılır.
4. **Gizlenecek Resim** alanına taşıyıcı görseli yükleyin — parçalar bu görselin içine gömülür.
5. İşlenmiş 6 görseli **İndir** butonuyla kaydedin.

### 2. Decode (Gizli Görseli Çıkarma)

1. **Decode** sekmesine gidin.
2. Encode edilmiş 6 görselden **herhangi 3 tanesini** yükleyin.
3. **Decode Et** butonuna tıklayın.
4. Kurtarılan görseli indirin.

### 3. PSNR Hesaplama

1. **PSNR Hesaplama** sekmesine gidin.
2. Orijinal ve stegano görseli yükleyin.
3. **Hesapla** butonuna tıklayarak kalite farkını (dB cinsinden) görüntüleyin.

## 🔬 Algoritma Detayları

### Shamir's Secret Sharing (SSS)

- **Polinom Derecesi:** 2 (kuadratik)
- **Modüler Aritmetik:** mod 251 (en büyük 8-bit asal sayı)
- **Parça Sayısı:** 6 (toplam)
- **Eşik Değeri:** 3 (geri çıkarma için gerekli minimum parça)
- **Sabit Katsayılar:** `f(x) = (secret + 166x + 94x²) mod 251`

### LSB Gömme

- Taşıyıcı görsel 2x çözünürlüğe yükseltilir (kapasite artırımı).
- Her renk kanalının (R, G, B, A) en düşük anlamlı bitlerine veri gömülür.
- Kullanıcı tarafından seçilebilen bit derinliği ile kalite-kapasite dengesi sağlanır.

## 📄 Lisans

Bu proje eğitim amaçlı geliştirilmiştir.
