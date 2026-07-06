# Uç Birim Yapay Zeka (Edge AI) Destekli Proaktif Akıllı Yük Yönetim Sistemi

[![Language](https://img.shields.io/badge/Dil-T%C3%BCrk%C3%A7e-red.svg)](#) [![Language: EN](https://img.shields.io/badge/Language-English-blue.svg)](README.md)
[![Donanım](https://img.shields.io/badge/Donan%C4%B1m-STM32F446RE-green.svg)](#) [![Mimari](https://img.shields.io/badge/Mimari-Edge_AI-orange.svg)](#)

> **Not:** Bu depo, mühendislik bitirme projemizin mimari bir vitrini ve akademik bir incelemesi olarak hazırlanmıştır. Projenin kaynak kodları kapalı (closed-source) tutulmaktadır ve burada paylaşılmamaktadır.

## 📌 Özet
Bu çalışma, sınırlı güç kapasitesine sahip dağıtım sistemlerinde elektriksel yüklerin güvenli, önceliklendirilmiş ve karar destekli biçimde yönetilmesine yönelik mikrodenetleyici tabanlı akıllı bir sistemdir. Geleneksel koruma rölelerinin arıza sonrasında (reaktif) devreye girmesi yerine, sistem **Uç Birim Yapay Zekası (Edge AI)** kullanarak krizleri saniyeler önceden öngörür ve proaktif "Kademeli Yük Atma" senaryoları üretir.

## ⚙️ Sistem Mimarisi

### Donanım Katmanı
Fiziksel prototip endüstriyel standartlara uygun olarak optimize edilmiştir:
* **Merkezi İşlemci:** STM32F446RE Nucleo
* **Gerçek Zamanlı SCADA Ölçümü:** 5 adet INA219 Akım Sensörü (I2C) ile bağımsız gerçek zamanlı ölçüm.
* **Yüksek Verimli Güç Anahtarlama:** Fan ve su pompası kontrolünde voltaj düşümünü önlemek için D4184 MOSFET modülleri.
* **Yükler:** Su Pompası (L1), DC Fan (L2), LED & Lazer Grubu (L3), Hat Ayırıcı Servo Motorlar.

### Yazılım ve Yapay Zeka Katmanı
* **HMI / SCADA:** UART haberleşmesi üzerinden parametrelerin gerçek zamanlı izlendiği Python tabanlı endüstriyel arayüz.
* **AI Karar Motoru:** INA219'dan akan verileri saniyelik olarak işleyen **Lineer Regresyon** tabanlı trend analizi ($y = mx + b$). Gelecek zaman dilimindeki güç tüketimini kestirir.
* **Histerezis (Hysteresis) Kontrolü:** Sınırda dalgalanan yüklerin röleleri sürekli açıp kapatmasını engellemek için sisteme kararlılık marjı eklenmiştir.

## 🏭 Endüstriyel Dijital İkiz (Digital Twin) Senaryosu
Geliştirilen sistemin ölçeklenebilirliğini göstermek amacıyla tesis yükleri aşağıdaki gibi senaryolaştırılmıştır:
* **L1 - Kritik Yük (Su Pompası):** Kesintiye uğramaması gereken hayati proses pompası.
* **L2 - Esnek Yük (DC Fan):** İklimlendirme ve soğutma sistemi (Geçici olarak durdurulabilir).
* **L3 - Düşük Öncelikli Yük (LED/Lazer):** Çevre aydınlatması (Kapasite aşımı öngörüldüğünde ilk atılacak yük).

## 📊 Akış Şeması ve Bağlantı Diyagramı
*(Afişinizdeki donanım blok diyagramını ve akış şemasını sürükle-bırak yöntemiyle buraya ekleyebilirsiniz)*
<img width="2670" height="6990" alt="AI Load Forecasting Pipeline-2026-06-19-161543" src="https://github.com/user-attachments/assets/83c94686-6e6b-437d-825a-8e41c39ab56a" />


## 🎓 Proje Ekibi ve Kurum
* **Duru Çalışkan** - Elektrik-Elektronik Mühendisi
* **Mehmet Emir Çebi** - Elektrik-Elektronik Mühendisi
* **Kurum:** Ondokuz Mayıs Üniversitesi (OMÜ)
