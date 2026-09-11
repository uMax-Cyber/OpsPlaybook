<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>

# Infratuzilma runbook lari

[![CI](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml/badge.svg)](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml)


![Namoyish](screenshots/demo.svg)
Homelab/korporativ infratuzilma uchun ishlab chiqarishda sinovdan oʻtgan operatsion runbook lar: Proxmox VE, UniFi tarmoqlari, Sophos fayrvollari va AI agentlar ekspluatatsiyasi. Har bir runbook aniq tartibni, tipik tuzoqlarni va tekshirish qadamlarini hujjatlashtiradi — barchasi haqiqiy hodisalardan olingan.

## Falsafa

Har bir runbook bir xil tuzilishga amal qiladi:
1. **Nima** — bajarilayotgan operatsiya
2. **Nega** — bu qachon kerak boʻladi
3. **Qadamlar** — aniq buyruqlar, tartib bilan
4. **Tekshirish** — muvaffaqiyatni qanday tasdiqlash
5. **Tuzoqlar** — sodir boʻlgan haqiqiy muvaffaqiyatsizliklar, siz takrorlamasligingiz uchun

## Mundarija

### 🖥 Sysadmin
- [VM yaratish runbook i](sysadmin/vm-creation.md) — golden template bilan cloud-init provizioning
- [Disk kattalashtirish runbook i](sysadmin/disk-resize.md) — ikki bosqichli onlayn kattalashtirish
- [SSH tiklash runbook i](sysadmin/ssh-recovery.md) — VM qayta yaratilgandan keyin cloudimg SSH ni tuzatish

### 🌐 Tarmoq
- [Wi-Fi diagnostikasi runbook i](network/wifi-diagnosis.md) — yuqoridan pastga metodologiya (avval DHCP)
- [DHCP pulini tekshirish](network/dhcp-pool.md) — «ulanmoqda...» muammolarining 1-sababi
- [Port auditi tartibi](network/port-audit.md) — anomaliyalarni aniqlash bilan toʻliq kommutator inventarizatsiyasi
- [Topologiya xaritalash](network/topology-mapping.md) — API dan tarmoq daraxtini qurish

### 🔒 Xavfsizlik
- [Haftalik xavfsizlik auditi](security/weekly-audit.md) — avtomatlashtirilgan tekshiruv roʻyxati
- [Syslog sozlash](security/syslog-setup.md) — barcha tarmoq qurilmalaridan markazlashtirilgan jurnallov

## Stack
- Proxmox VE 9.x (3 ta mustaqil tugun)
- UniFi Controller (96 ta boshqariladigan qurilma)
- Sophos Firewall (2 ta shlyuz, XML API)
- Python + Bash (faqat stdlib)
- Markazlashtirilgan jurnallov uchun rsyslog

## Nega runbook lar?

Infratuzilma oldindan aytiladigan usullarda buziladi. Bir xil 5 ta tuzoq VM provizioning muvaffaqiyatsizliklarining 80% ini keltirib chiqaradi. Bir xil 3 ta muammo Wi-Fi shikoyatlarining katta qismini tashkil qiladi. Bularni hujjatlashtirish shuni anglatadi:
- Yangi jamoa aʼzolari tezroq kirishadi
- Tunda soat 3 dagi hodisalar disk raskadrovkasi emas, qadamlarga amal qilish bilan hal qilinadi
- AI agentlar tartiblarga ishonchli amal qilishi mumkin

## Litsenziya
MIT

## 📬 Aloqa

Savollaringiz bormi? Yozing: **[allumaxmail@gmail.com](mailto:allumaxmail@gmail.com)**

---

<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>
