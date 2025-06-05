# Şirketler Arası LAN ve Routing Projesi

Bu proje, iki farklı şirkete ait LAN ağlarının routerlar aracılığıyla birbirine bağlandığı küçük ölçekli bir senaryoyu simüle eder.

## 🎯 Amaçlar
- İki LAN segmenti oluşturmak
- Router’lar arası bağlantı kurmak
- Statik routing ile yönlendirme sağlamak
- Tüm cihazların birbirine erişimini test etmek

## 🗺️ Topoloji

![Image](https://github.com/user-attachments/assets/0003fd23-08ba-4693-9a0d-c028073b79fa)

## 🌐 IP Dağılımı

### A Şirketi (LAN Ağı: `216.34.56.0/29`)
| Cihaz  | IP Adresi       | Gateway            |
|--------|------------------|---------------------|
| PC1    | 216.34.56.1      | 216.34.56.6         |
| PC2    | 216.34.56.2      | 216.34.56.6         |
| PC3    | 216.34.56.3      | 216.34.56.6         |
| PC4    | 216.34.56.4      | 216.34.56.6         |
| R1     | 216.34.56.6      | -                   |

### B Şirketi (LAN Ağı: `192.168.1.0/29`)
| Cihaz  | IP Adresi       | Gateway            |
|--------|------------------|---------------------|
| PC5    | 192.168.1.1      | 192.168.1.6         |
| PC6    | 192.168.1.2      | 192.168.1.6         |
| PC7    | 192.168.1.3      | 192.168.1.6         |
| PC8    | 192.168.1.4      | 192.168.1.6         |
| R2     | 192.168.1.6      | -                   |

### Routerlar Arası Bağlantı (Ağ: `192.168.13.0/30`)
- R1: `192.168.13.1`
- R2: `192.168.13.2`

## ⚙️ Statik Yönlendirme

### R1:

ip route 192.168.1.0 255.255.255.248 192.168.13.2

### R2:

ip route 216.34.56.0 255.255.255.248 192.168.13.1

## ✅ Testler
- Her iki LAN'daki tüm PC'ler birbiriyle haberleşebiliyor.
- Statik yönlendirme ile router’lar arası trafik doğru şekilde yönlendiriliyor.
- Başarılı ping testleri gerçekleştirildi.
