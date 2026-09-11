<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>

# Infratuzilma runbooklari

[![CI](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml/badge.svg)](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml)


![Namoyish](screenshots/demo.svg)
Homelab va korporativ infratuzilma uchun productionda sinovdan oʻtgan operatsion runbooklar: Proxmox VE, UniFi tarmoq, Sophos fayrvol va AI agent ekspluatatsiyasi. Har bir runbookda aniq tartib, tipik tuzoqlar va tekshirish qadamlari bor — barchasi haqiqiy hodisalardan olingan saboqlar.

## Tamoyil

Har bir runbook bir xil tuzilishda yozilgan:
1. **Nima** — bajariladigan operatsiya
2. **Nega** — qachon kerak boʻladi
3. **Qadamlar** — aniq buyruqlar, tartib bilan
4. **Tekshirish** — muvaffaqiyatni qanday tasdiqlash
5. **Tuzoqlar** — bizda roʻy bergan xatolar, siz takrorlamasligingiz uchun

## Mundarija

### 🖥 Sysadmin
- [VM yaratish runbooki](sysadmin/vm-creation.md) — golden template bilan cloud-init provizioning
- [Diskni kattalashtirish runbooki](sysadmin/disk-resize.md) — onlayn, ikki bosqichda
- [SSH tiklash runbooki](sysadmin/ssh-recovery.md) — VM qayta yaratilgach cloudimg SSHsini tuzatish

### 🌐 Tarmoq
- [Wi-Fi diagnostika runbooki](network/wifi-diagnosis.md) — yuqoridan pastga metodika (avval DHCP)
- [DHCP poolini tekshirish](network/dhcp-pool.md) — "ulanmoqda..." muammosining 1-sababi
- [Port audit tartibi](network/port-audit.md) — anomaliyalarni aniqlash bilan kommutatorlarning toʻliq inventarizatsiyasi
- [Topologiya xaritalash](network/topology-mapping.md) — API asosida tarmoq daraxtini qurish

### 🔒 Xavfsizlik
- [Haftalik xavfsizlik auditi](security/weekly-audit.md) — avtomatlashtirilgan checklist
- [Syslog sozlash](security/syslog-setup.md) — barcha tarmoq qurilmalaridan markazlashgan log

## Stack
- Proxmox VE 9.x (3 ta alohida tugun)
- UniFi Controller (96 ta boshqariladigan qurilma)
- Sophos Firewall (2 ta gateway, XML API)
- Python + Bash (faqat standart kutubxona)
- Markazlashgan log uchun rsyslog

## Runbook nima uchun kerak?

Infratuzilma odatda oldindan koʻrinadigan tarzda buziladi: VM provizioningdagi ishdan chiqishlarning 80%i oʻsha 5 ta tuzoqdan, Wi-Fi shikoyatlarining koʻpi esa oʻsha 3 ta muammodan keladi. Bularni hujjatlashtirish:
- Yangi jamoa aʼzosi ishga tez kirishib ketadi
- Kechasi soat 3 dagi hodisa disk raskadrovka bilan emas, qadam-baqadam yurib hal boʻladi
- AI agent tartibga ishonch bilan amal qiladi

## Litsenziya
MIT

## 📬 Aloqa

Savol boʻlsa yozing: **[allumaxmail@gmail.com](mailto:allumaxmail@gmail.com)**

---

<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>
