# 📋 SD Proje Araçları (SD Tools) - Sürüm Notları (Changelog)

Bu sayfada **SD Proje Araçları (SD Tools)** yazılımının sürümlerinde yapılan tüm yenilikler, iyileştirmeler ve hata düzeltmeleri listelenmektedir.

---

## 🚀 Sürüm 2.5 (17 Ekim 2026) - *Güncel Sürüm*

- **📦 Kurulum Sihirbazı (`SDTools_Setup.exe`):**
  - İçinde `SDTools.exe` ve `app.ico` gömülü olan, internet gerektirmeyen tek dosyalık modern **WPF Kurulum Sihirbazı (`SDTools_Setup.exe`)** eklendi.
  - Varsayılan olarak `%LocalAppData%\Programs\SDTools` klasörüne (veya isteğe bağlı olarak `C:\Program Files\SDTools` ya da özel bir klasöre) kurulum yapar.
  - Masaüstü kısayolu, Başlat Menüsü kısayolu ve Windows *Program Ekle / Kaldır (Uninstall)* kaydını otomatik oluşturur.
- **🔄 GitHub Üzerinden Tek Tıkla Online Güncelleme (Auto-Update):**
  - Uygulama açılışında arka planda sessizce ve üst bardaki **`🔄 Güncelle`** (veya *Hakkında -> Güncelleme Kontrolü*) butonuyla GitHub (`version.json`) üzerinden yeni sürüm kontrolü yapar.
  - Yeni bir sürüm bulunduğunda kullanıcı onayıyla yeni `SDTools.exe` dosyasını indirir, PE (`MZ`) bütünlük doğrulamasını yapar, mevcut sürümün üzerine yazar ve saniyeler içinde yeni sürümle yeniden başlatır.
- **🛡️ Masaüstünde Gizli / Akıllı `config.json` Yönetimi:**
  - Yazılım kurulum klasöründen çalıştığında `config.json` dosyasını kendi kurulum klasöründe tutar; böylece Masaüstünde sadece kısayol yer alır ve hiçbir JSON dosyası görünmez.
  - Eğer kullanıcı tekil `SDTools.exe` dosyasını doğrudan Masaüstü üzerinde çalıştırırsa bile, masaüstünü kirletmemek için `config.json` dosyasını otomatik olarak `%LocalAppData%\Programs\SDTools\config.json` konumuna taşır ve orada yönetir.

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
