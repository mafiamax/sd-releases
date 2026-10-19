# 📋 SD Proje Araçları (SD Tools) - Sürüm Notları (Changelog)

Bu sayfada **SD Proje Araçları (SD Tools)** yazılımının sürümlerinde yapılan tüm yenilikler, iyileştirmeler ve hata düzeltmeleri listelenmektedir.

---

## 📦 Sürüm 2.6.1 (19 Ekim 2026) - *Güncel Sürüm*

- **📦 Dosya Türü Ayrımı Yapmadan Tüm Dosyaları Yedekle (`*.*`) Modu:**
  - Proje Yedekleme modülündeki *"3. Yedeklenecek Dosya Türleri"* başlığının sağ tarafına **`📦 Dosya Türü Ayrımı Yapmadan Tüm Dosyaları Yedekle (*.*)`** seçeneği eklendi.
  - Bu seçenek işaretlendiğinde kategori listesi hafızadaki seçimlerinizi kaybetmeden görsel olarak devre dışı (pasif) bırakılır ve kaynak klasördeki **tüm dosya türleri (`*.*`)** hiçbir uzantı kısıtlamasına takılmadan birebir yedeklenir (Hariç tutulan klasörler, tarih, boyut ve artımlı yedekleme filtreleri yine çalışmaya devam eder).
- **➕ Proje Yedekleme İçin Özel Uzantı Kutusu:**
  - Proje Yedekleme modülünün alt kısmına **`➕ Özel Uzantılar`** metin kutusu eklendi. Standart kategorilerde yer almayan özel uzantıları (`.dwf, .lumion, .max, .fbx` vb.) virgülle ayırarak doğrudan yedeklemeye dahil edebilirsiniz.
- **🏗️ Revit (`.rvt, .rfa, .rte`) BIM Desteği:**
  - Hem Proje Temizleme hem Proje Yedekleme modüllerindeki **Mühendislik & CAD / BIM** kolonuna varsayılan olarak **`Revit (.rvt, .rfa, .rte)`** kategorisi eklendi ve kritik model koruması kapsamına alındı.

---

## 🛡️ Sürüm 2.6 (18 Ekim 2026)

- **🔄 SHA-256 Doğrulamalı Online Güncelleme (`--apply-update`):**
  - İndirme adresini yalnızca resmi dağıtım deposuna (`mafiamax/sd-releases`) kilitler, indirilen paketin **SHA-256 kriptografik özetini** ve PE (`MZ`) başlığını doğrular.
  - Harici `.bat` betiği yerine yerleşik `--apply-update` mekanizmasıyla çalışan süreci bekler, mevcut `.exe` dosyasını `.old` olarak yedekler, hata durumunda otomatik geri yükler (rollback) ve yeni sürüm açıldığında Windows *Program Ekle / Kaldır* sürüm bilgisini günceller.
- **📦 Kurulum Sihirbazı ve Güvenli Kaldırıcı İyileştirmeleri (`SDTools_Setup.exe`):**
  - Dolu kullanıcı klasörlerine doğrudan kurulum yapılmasını engelleyerek otomatik `\SDTools` alt dizini koruması uygular.
  - Yönetici yetkisiyle yapılan kurulumlar sonrasında uygulamayı normal kullanıcı yetkisiyle (`explorer.exe` üzerinden) başlatarak Google Drive (`G:\`) ve ağ sürücülerinin görünürlüğünü korur.
  - Kaldırma sırasında yalnızca kendi kurulum dosyalarını siler ve klasör yalnızca tamamen boşsa temizler.
- **🛡️ Ekstra Temizleme, Yedekleme ve `config.json` Güvenliği:**
  - Çalıştırılabilir sistem ve uygulama dosyaları (`.exe, .dll, .sys, .msi, .bat, .cmd, .ps1, .lnk, .cs, .py, .json, .config, .ico`) her koşulda silinmeye karşı koruma altına alındı (`NeverDeleteExtensions`).
  - Temizlik onay penceresine **"En Çok Silinecek İlk 5 Uzantı ve Adetleri"** özeti eklendi; silme anında dosyanın tarama sonrasındaki boyut ve değiştirilme tarihi tekrar kontrol edilir.
  - Gelecekteki tüm **ideCAD** sürümleri (`.ide12`, `.ide15` vb.) `.ide*` önek eşleşmesiyle otomatik olarak desteklenir.
  - `config.json` yazma işlemleri `.tmp` + `File.Replace` ile atomik hale getirildi.

---

## 🚀 Sürüm 2.5 (17 Ekim 2026)

- **📦 Kurulum Sihirbazı (`SDTools_Setup.exe`):**
  - İçinde `SDTools.exe` ve `app.ico` gömülü olan, internet gerektirmeyen tek dosyalık modern **WPF Kurulum Sihirbazı (`SDTools_Setup.exe`)** eklendi.
  - Masaüstü kısayolu, Başlat Menüsü kısayolu ve Windows *Program Ekle / Kaldır (Uninstall)* kaydını otomatik oluşturur.
- **🔄 GitHub Üzerinden Online Güncelleme (Auto-Update):**
  - Uygulama açılışında arka planda sessizce ve *Hakkında -> Güncelleme Kontrolü* butonuyla GitHub (`version.json`) üzerinden yeni sürüm kontrolü yapar.
- **🛡️ Masaüstünde Gizli / Akıllı `config.json` Yönetimi:**
  - Yazılım kurulum klasöründen çalıştığında `config.json` dosyasını kendi kurulum klasöründe tutar; böylece Masaüstünde sadece kısayol yer alır ve hiçbir JSON dosyası görünmez.

---

## 📁 Sürüm 2.4 (17 Ekim 2026)

- **📁 Modern Windows Gezgini (Explorer) Klasör Seçici:**
  - Proje Temizleme ve Proje Yedekleme modüllerindeki klasör seçme pencereleri (`IFileDialog` / `FOS_PICKFOLDERS` mimarisi ile) standart büyük **Windows Gezgini** görünümüne yükseltildi.
  - Artık klasör seçerken üstteki adres çubuğuna doğrudan yol yapıştırabilir, arama yapabilir ve sol menüdeki *Hızlı Erişim / Masaüstü / Bu Bilgisayar* kısayollarını kullanabilirsiniz.
- **📦 Bağımsız `Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)` Satırı (Varsayılan Silinir):**
  - `.bak`, `.ebk`, `.sbk` ve `.fbk` yedek uzantıları diğer kategorilerden ayrılarak hem Temizleme hem Yedekleme modüllerine **`Yedek Dosyaları (.bak, .ebk, .sbk, .fbk)`** adıyla bağımsız bir satır olarak eklendi.
  - Çoğunlukla yedek dosyalarının temizlenmesi tercih edildiği için bu satır **varsayılan olarak işaretsiz (`false`)** gelir; istenildiğinde işaretlenerek korunabilir veya yedeklenebilir.
- **🏗️ Kategori ve Uzantı Sadeleştirmeleri:**
  - Tüm çizim yazılımlarını (ZWCAD, BricsCAD, GstarCAD, AutoCAD vb.) kapsaması için `AutoCAD` kategorisinin adı **`CAD (.dwg, .dxf, .dwt, .ctb)`** olarak değiştirildi.
  - **ETABS** satırı yalnızca **`.edb, .e2k`**; **SAP2000** satırı yalnızca **`.sdb, .s2k`**; **SAFE** satırı yalnızca **`.fdb, .f2k`** ana model dosyalarını koruyacak şekilde sadeleştirildi.
- **🔢 Sayısal Giriş Koruması & Arayüz Güvenliği:**
  - Proje Temizleme modülündeki **Gün Sınırı (Dosya Yaşı)** kutusuna klavyeden veya kopyala-yapıştır (`Ctrl+V`) yoluyla harf/sembol girilmesi tamamen engellendi (yalnızca `0-9` rakam girişi yapılabilir).
  - Üst klasör yolunda hedef klasör adı geçtiğinde (`D:\CAD\ProjeX` gibi) alt klasör filtrelemesinin devre dışı kalması önlendi; yalnızca seçilen kök klasörün kendi adı kontrol edilir.
  - Tarama ve temizleme esnasında tüm onay kutuları kilitlenir; silinemeyen (açık/kilitli) dosyaların isimleri işlem sonu özetinde gösterilir.
- **📋 Sürüm Notları Penceresi ve Tek `.exe` İkon Desteği:**
  - **Hakkında** penceresine **Sürüm Notları** butonu ve GitHub sürüm geçmişi bağlantısı eklendi.
  - Sadece `SDTools.exe` dosyasının tek başına dağıtıldığı bilgisayarlarda pencere sol üst simgesinin doğrudan `.exe` içinden otomatik okunması sağlandı.

---

## 🛡️ Sürüm 2.3 (17 Ekim 2026)

- **Seçenek B Koruma Mimarisi & Arşiv Koruması:**
  - Analiz programlarının ürettiği yüzlerce dinamik geçici dosya uzantısını yakalamak için *"Korunan kategoriler dışındakileri temizle"* yapısı güçlendirildi; sıkıştırılmış paketler için **`Arşiv (.zip, .rar, .7z)`** kategorisi eklendi.
  - Yazılımın kendi ürettiği `_Modeller_Otomatik_Yedek_*.zip` arşivleri, `SD_Backup_*` klasörleri ve `_yedekleme_logu_*` raporları her koşulda silinmeye karşı koruma altına alındı.
- **Otomatik Tarama Kilidi & Doğrudan Klasör Eşleşmesi:**
  - Tarama yapıldıktan sonra klasör yolu, gün sınırı veya koruma filtreleri değiştirilirse **"Temizle" butonu otomatik kilitlenir** ve yeniden tarama yapılması istenir.
  - Kullanıcının ana klasör olarak doğrudan `C:\Proje\ETABS` gibi bir hedef klasörü seçtiğinde alt klasör filtresine takılmaması sağlandı.
- **Atomik Yedekleme ve Sistem Klasörü Koruması:**
  - Yedekleme sırasında dosyalar önce `.tmp` olarak yazılıp tamamlandığında `File.Replace` ile atomik olarak hedefe alınır; kesinti veya iptal durumunda yarım `.tmp` dosyaları otomatik temizlenir.
  - `Windows`, `Program Files`, `$RECYCLE.BIN` sistem dizinleri ve sembolik bağ (`ReparsePoint`) döngü koruması eklendi.

---

## 🌳 Sürüm 2.2 (16 Ekim 2026)

- **Genişletilebilir Klasör Ağacı (`TreeView`):**
  - Taranacak Hedef Alt Klasörler penceresine proje klasörlerinin derin alt dizinlerini gösteren çift tıklamalı ağaç görünümü eklendi.
- **STA4CAD Desteği & Kritik Model Onay Bariyeri:**
  - Mühendislik kategorilerine ve varsayılan hedef klasörlere **`STA4CAD (.st4)`** ve **`CAD`** eklendi.
  - Kritik model kategorilerinin koruması kapatıldığında kullanıcıdan açık onay isteyen güvenlik uyarısı eklendi.

---

## ✨ Sürüm 2.0 & 2.1 (Ekim 2026)

- **Hepsi-Bir-Arada (All-in-One) Mimari:**
  - Proje Temizleme ve SD Backup Proje Yedekleme araçları tek bir bağımsız C# / WPF (`.exe`) masaüstü süitinde birleştirildi.
  - Canlı Açık / Koyu tema geçişi, iki kolonlu kategori yönetimi, Windows Gezgini'nde dosyaya gitme (`📂`) ve Geri Dönüşüm Kutusu kalıcı silme onay bariyeri eklendi.
