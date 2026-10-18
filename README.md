# 🏗️ SD Proje Araçları (SD Tools) v2.6

Statik Dizayn Mühendislik için özel olarak geliştirilmiş **SD Proje Araçları (SD Tools)**; ETABS, SAP2000, SAFE, ideCAD ve STA4CAD gibi yapısal analiz yazılımları ile mimari/CAD projelerinin bakımını, temizliğini ve yedeklenmesini tek merkezden yöneten **hepsi-bir-arada (All-in-One)** mühendislik çalışma süitidir.

Gelecekte eklenecek yeni modüllere ve sekmelere (pafta düzenleme, metraj, model kontrolü vb.) uygun, genişletilebilir modern bir sekme mimarisine sahiptir.

> 📋 **Sürüm geçmişi ve yapılan tüm yenilikler için:** [**Sürüm Notları (CHANGELOG.md)**](CHANGELOG.md)

---

## 📦 Kurulum ve Dağıtım (v2.6)

- **🚀 Kurulum Sihirbazı (`SDTools_Setup.exe` - Önerilen):**
  Tek dosyalık **`SDTools_Setup.exe`** (~402 KB) kurulum paketini çalıştırarak yazılımı bilgisayarınıza (`%LocalAppData%\Programs\SDTools` veya `C:\Program Files\SDTools` altına) kurabilirsiniz. Kurulum sihirbazı:
  - Masaüstü ve Başlat Menüsü kısayollarını otomatik oluşturur,
  - `config.json` ayar dosyasını kurulum klasörü içinde atomik olarak tutar (**Masaüstünde asla `config.json` görünmez**),
  - Windows *Program Ekle veya Kaldır* listesine güvenli kaldırıcı (Uninstaller) kaydı ekler.
- **🔄 GitHub Üzerinden SHA-256 Doğrulamalı Online Güncelleme (Auto-Update):**
  Uygulama açılışında veya **Hakkında -> `🔄 Güncelleme Kontrolü`** butonuna tıklandığında GitHub (`version.json`) üzerinden yeni sürüm kontrolü yapılır. Yeni bir sürüm yayınlandığında SHA-256 bütünlük doğrulamasıyla indirilir ve yerleşik `--apply-update` mekanizmasıyla kendi kendini güvenle günceller.
- **⚡ Taşınabilir (Portable) Tek `.exe` Kullanımı:**
  Kurulum yapmadan doğrudan **`SDTools.exe`** (~303 KB) dosyasını da çalıştırabilirsiniz. Doğrudan Masaüstü'nden çalıştırılsa bile ayar dosyasını otomatik olarak `%LocalAppData%\Programs\SDTools\config.json` altında saklar.

---

## 🌟 Mevcut Modüller & Özellikler

1. **🧹 Proje Temizleme Modülü:**
   - ETABS, SAP2000, SAFE, ideCAD ve STA4CAD gibi yazılımların analiz sırasında ürettiği yüzlerce dinamik geçici dosya uzantısını (`.LOG`, `.OUT`, `.F06`, `.K01`, `.Y01`, `.$et`, `.$2k`, `.val` vb.) **"Korunan Uzantılar ve Kategoriler Dışındakileri Temizle"** prensibiyle güvenle temizler.
   - **📁 Modern Windows Gezgini Klasör Seçici:** Klasör seçme pencereleri adres çubuklu, arama kutulu ve *Hızlı Erişim* destekli standart **Windows Gezgini (Explorer)** görünümünde açılır.
   - **🛡️ Korunacak Dosyaları Belirle & Bağımsız Yedek Dosyaları Kontrolü:** İki kolonlu modern seçim penceresi ile ana mühendislik modellerini (`ETABS: .edb, .e2k`, `SAP2000: .sdb, .s2k`, `SAFE: .fdb, .f2k`, `ideCAD: .ide*`, `CAD: .dwg, .dxf, .dwt, .ctb`, `STA4CAD: .st4, .stl`), sıkıştırılmış arşiv paketlerini (`.zip`, `.rar`, `.7z`, `.tar`, `.gz`) ve ofis/medya formatlarını kategori bazında korur. **`Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)`** ayrı bir satır olarak sunulur ve varsayılan olarak silinir (işaretsizdir); istenildiğinde işaretlenerek korunabilir.
   - **🔒 Sistem Yedekleri ve Log Koruması:** Programın kendi ürettiği otomatik yedek arşivleri (`_Modeller_Otomatik_Yedek_*.zip`), yedek klasörleri (`SD_Backup_*`) ve işlem raporları (`_yedekleme_logu_*`) her koşulda koruma altındadır.
   - **📁 Akıllı Alt Klasör Seçimi (Genişletilebilir Klasör Ağacı):** Hedef proje klasörü altındaki analiz klasörlerini (`ETABS, SAP2000, ideCAD, SAFE, CAD, STA4CAD`) tek tıkla varsayılanlardan veya derin ağaç yapısından seçer. Doğrudan hedef klasörün kendisi seçildiğinde de (`C:\Proje\ETABS` gibi) yalnız seçilen kök klasörün adını kontrol ederek akıllı eşleşme sağlar.
   - **🔄 Otomatik Tarama Kilidi Güvenliği:** Tarama yapıldıktan sonra klasör yolu, gün sınırı veya koruma filtreleri değiştirilirse **"Temizle" butonu otomatik kilitlenir** ve güncel ayarlarla yeniden tarama yapılması istenir.
   - **🔢 Sayısal Gün Filtresi Koruması:** Dosya yaşı (gün sınırı) kutusuna yalnızca rakam (`0-9`) girilebilir; harf ve geçersiz metin girişi/yapıştırması engellenmiştir.
   - **📦 Yalnızca Modelleri Sıkıştıran Ön Yedekleme:** *"Temizlik Öncesi ZIP Yedek Al"* seçeneği açıldığında geçici analiz artıkları ve mevcut arşivler hariç tutularak **yalnızca korunan model ve proje belgeleri** `_Modeller_Otomatik_Yedek_YYYYMMDD_HHMMSS.zip` arşivine sıkıştırılır.
   - Dosya listesinde her satırın yanındaki **`📂` butonu** (veya çift tıklama) ile dosyayı doğrudan Windows Gezgini'nde seçili olarak açar.

2. **💾 Proje Yedekleme Modülü (SD Backup Entegre):**
   - Proje klasörlerini harici disklere, SSD'lere veya ağ sürücülerine hızla yedekler.
   - Çift kolonlu akıllı filtreleme (`ideCAD`, `CAD`, `ETABS`, `SAP2000`, `SAFE`, `STA4CAD`, `Fischer`, `idea Statika`, `SketchUp`, `Excel`, `Word`, `PDF`, `Arşiv`, `Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)`, `Resim`, `Video`, `IFC`).
   - **⚡ Artımlı (Incremental) ve Atomik Yedekleme:** Değişmemiş dosyaları saniyeler içinde atlar; kopyalanan dosyaları önce geçici (`.tmp`) dosyaya yazıp işlem tamamlandığında atomik olarak hedefe yerleştirir. Böylece kesinti veya iptal durumunda hedefteki eski sağlam yedek asla bozulmaz.
   - Tarih ve dosya boyutu (MB) filtreleme desteği.
   - Her işlem sonunda hedef klasörde tarihçeli detaylı denetim raporu (`_yedekleme_logu_*.txt`) üretir.

3. **🛡️ Sistem Klasörü ve Sembolik Bağ Koruması:**
   - `C:\`, `C:\Windows`, `Program Files`, `$RECYCLE.BIN` gibi işletim sistemi dizinlerinin kazara taranmasını/temizlenmesini engeller ve sembolik bağlardan (ReparsePoint / Junction) kaynaklı sonsuz döngüleri önler.

4. **☀️ Canlı Açık / Koyu Tema, Online Güncelleme & Sürüm Notları:**
   - Sağ üstteki toggle butonu ile tek tıkla canlı olarak tema değiştirilebilir.
   - **`🔄 Güncelle`** ve **Hakkında -> 📋 Sürüm Notları** pencereleri ile uygulama içinden sürüm geçmişi incelenebilir ve yeni sürümler tek tıkla yüklenebilir.

---

## 📖 Nasıl Kullanılır? (Adım Adım Kullanım Rehberi)

### 1️⃣ Proje Temizleme Rehberi (Sekme 1)
1. **Klasör Seçimi:** **Klasör Seç...** butonu ile standart Windows Gezgini penceresinden temizlemek istediğiniz ana proje klasörünü (veya doğrudan `ETABS`, `ideCAD` gibi analiz klasörünü) seçin.
2. **Hedef Alt Klasör Filtresi:** *"Sadece bu klasörleri tara"* kutusu işaretliyken **Klasör Seç...** butonuna tıklayarak proje içindeki alt klasörleri ağaç yapısından seçebilir veya **Varsayılanlar** (`ETABS, SAP2000, ideCAD, SAFE, CAD, STA4CAD`) butonunu kullanabilirsiniz.
3. **Korunacak Dosyaları Belirle:** **Korunacak Dosyaları Belirle...** butonuna tıklayarak hangi yazılım modellerinin, arşivlerin (`.zip`, `.rar`, `.7z`) ve belgelerin korunacağını seçin.
   - **Yedek Dosyaları (`.bak, .ebk, .sbk, .fbk`):** `Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)` satırı varsayılan olarak **işaretsizdir** (böylece bu yedek dosyaları temizlikte silinir). Eğer silinmemesini istiyorsanız bu satırı işaretlemeniz yeterlidir.
4. **Gün Sınırı:** Örneğin `7` girerseniz son 7 gün içinde değiştirilmiş hiçbir geçici analiz dosyasına dokunulmaz (`⏳ Korunacak (Güncel)` olarak işaretlenir); yalnızca 7 günden eski analiz artıkları temizlenir.
5. **Güvenlik Seçenekleri:**
   - **Geri Dönüşüm Kutusu'na Gönder:** Silinen dosyaların Windows Geri Dönüşüm Kutusu'na taşınmasını sağlar (Önerilir).
   - **Temizlik Öncesi ZIP Yedek Al:** Temizlik başlamadan önce korunan model dosyalarını otomatik olarak `_Modeller_Otomatik_Yedek_*.zip` arşivine yedekler.
6. **Tara ve Analiz Et & Temizliği Başlat:** Önce **Tara ve Analiz Et** butonuna basarak listeyi ve durum rozetlerini (`🛡️ Korunacak (Model)`, `📦 Korunacak (Yedek/Arşiv)`, `📄 Korunacak (Belge/Medya)`, `🗑️ Temizlenecek`) inceleyin, ardından **Temizliği Başlat** butonu ile işlemi tamamlayın.

### 2️⃣ Proje Yedekleme Rehberi (Sekme 2)
1. **Kaynak ve Hedef Seçimi:** Windows Gezgini penceresi ile yedeklenecek ana proje dizinini (**Kaynak**) ve yedeklerin aktarılacağı diski/klasörü (**Hedef**) seçin.
2. **Kategori Seçimi:** Sol ve sağ kolonlardan yedeklenmesini istediğiniz proje, ofis, medya veya arşiv kategorilerini işaretleyin (`Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)` satırı isteğe bağlı olarak işaretlenebilir).
3. **Artımlı Yedekleme ve Filtreler:**
   - **Artımlı Yedekleme:** Hedefte zaten aynı boyutta ve güncellikte bulunan dosyaları atlayarak yedekleme süresini büyük ölçüde kısaltır.
   - **Tarih ve Boyut Filtresi:** Belirli bir tarihten sonra değişen veya belirli bir MB sınırının altındaki dosyaları filtreleyebilirsiniz.
4. **Yedeklemeyi Başlat:** İşlem sonunda hedef klasörde detaylı `_yedekleme_logu_YYYYMMDD_HHMMSS.txt` raporu oluşturulur.

---

## 🛡️ Korunan Dosya Uzantıları ve Kategoriler (v2.6)

| Kategori | Uzantılar | Varsayılan Durum |
| :--- | :--- | :--- |
| **ETABS Modelleri** | `.edb`, `.e2k` | 🛡️ **KORUNUR (Model)** |
| **SAP2000 Modelleri** | `.sdb`, `.s2k` | 🛡️ **KORUNUR (Model)** |
| **SAFE Modelleri** | `.fdb`, `.f2k` | 🛡️ **KORUNUR (Model)** |
| **ideCAD Modelleri** | `.ide*` (`.ide7`..`.ide11`, `.ide85`, `.ide`) | 🛡️ **KORUNUR (Model)** |
| **STA4CAD Modelleri** | `.st4`, `.stl` | 🛡️ **KORUNUR (Model)** |
| **CAD & Çizim & 3D** | `.dwg`, `.dxf`, `.dwt`, `.ctb`, `.shx`, `.lsp`, `.skp`, `.ifc`, `.ideaCon`, `.cfix` | 🛡️ **KORUNUR (Model)** |
| **Arşiv Paketleri** | `.zip`, `.rar`, `.7z`, `.tar`, `.gz` | 📦 **KORUNUR (Yedek/Arşiv)** |
| **Yedek Dosyaları** | `.bak`, `.ebk`, `.sbk`, `.fbk` | ⚙️ **VARSAYILAN SİLİNİR (İsteğe Bağlı Korunur)** |
| **Sistem Otomatik Yedek & Logları** | `_Modeller_Otomatik_Yedek_*.zip`, `SD_Backup_*`, `_yedekleme_logu_*` | 🔒 **KOŞULSUZ KORUNUR** |
| **Raporlar, Ofis & Medya** | `.pdf`, `.xlsx`, `.xls`, `.xlsm`, `.csv`, `.docx`, `.doc`, `.pptx`, `.ppt`, `.txt`, `.mp4`, `.avi`, `.mov`, `.mkv`, `.png`, `.jpg`, `.jpeg`, `.bmp`, `.tif`, `.tiff` | 📄 **KORUNUR (Belge/Medya)** |
| **Güncel Geçici Dosyalar** | Tüm uzantılar (< Gün Sınırı, varsayılan 7 gün) | ⏳ **KORUNUR (Güncel)** |
| **Eski Analiz Artıkları** | `.LOG`, `.OUT`, `.F06`, `.K01`, `.M01`, `.E01`, `.Y01`, `.$et`, `.$2k`, `.$sf`, `.val`, `.tmp` vb. (≥ Gün Sınırı) | 🗑️ **TEMİZLENİR** |

> 💡 **Önemli Not:** Temizleme modülü *"Beyaz Liste (Korunanlar Dışındakileri Sil)"* prensibiyle çalışır. Yukarıdaki korunan kategorilerde yer almayan ve belirlenen gün sınırından daha eski olan dosya uzantıları temizlenir. Özel bir dosya uzantısını korumak isterseniz **Korunacak Dosyaları Belirle -> İlave / Özel Uzantılar** kutusuna ekleyebilirsiniz.

---

## ⚙️ Yapılandırma (`config.json`) ve Derleme (`build.ps1`)

- Tüm kullanıcı tercihleri (klasör yolları, gün sınırı, temizleme ve yedekleme kategori seçimleri, özel uzantılar, hariç tutulan klasörler ve tema) kurulum klasöründeki `config.json` dosyasında otomatik olarak saklanır.
- Kaynak kodlardan (`SDTools_App.cs` ve `SDTools_Setup.cs`) hem `SDTools.exe` hem de `SDTools_Setup.exe` paketini tek tıkla derlemek için PowerShell üzerinden `.\build.ps1` betiğini çalıştırabilirsiniz.

---

*Geliştirici: Statik Dizayn Mühendislik • Web: https://statikdizayn.com • Sürüm: v2.6 • Powered by Google Gemini*
