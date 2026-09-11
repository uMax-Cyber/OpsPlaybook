<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>

# Инфраструктурные runbook'и

[![CI](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml/badge.svg)](https://github.com/uMax-Cyber/OpsPlaybook/actions/workflows/ci.yml)


![Демонстрация](screenshots/demo.svg)
Проверенные в продакшене операционные runbook'и для homelab/корпоративной инфраструктуры: Proxmox VE, сети UniFi, файрволы Sophos и эксплуатация ИИ-агентов. Каждый runbook документирует точную процедуру, типовые ловушки и шаги проверки — всё вынесено из реальных инцидентов.

## Философия

Каждый runbook следует единой структуре:
1. **Что** — выполняемая операция
2. **Зачем** — когда это может понадобиться
3. **Шаги** — точные команды, по порядку
4. **Проверка** — как подтвердить успех
5. **Ловушки** — реальные сбои, произошедшие у нас, чтобы вы их не повторяли

## Содержание

### 🖥 Сисадминство
- [Runbook создания VM](sysadmin/vm-creation.md) — провижининг через cloud-init с золотым шаблоном
- [Runbook расширения диска](sysadmin/disk-resize.md) — онлайн-расширение в два этапа
- [Runbook восстановления SSH](sysadmin/ssh-recovery.md) — починка SSH на cloudimg после пересоздания VM

### 🌐 Сети
- [Runbook диагностики Wi-Fi](network/wifi-diagnosis.md) — методология сверху вниз (сначала DHCP)
- [Проверка DHCP-пула](network/dhcp-pool.md) — причина №1 проблем «подключение...»
- [Процедура аудита портов](network/port-audit.md) — полная инвентаризация коммутаторов с обнаружением аномалий
- [Построение топологии](network/topology-mapping.md) — сборка дерева сети из API

### 🔒 Безопасность
- [Еженедельный аудит безопасности](security/weekly-audit.md) — автоматизированный чек-лист
- [Настройка syslog](security/syslog-setup.md) — централизованные логи со всех сетевых устройств

## Стек
- Proxmox VE 9.x (3 автономных узла)
- UniFi Controller (96 управляемых устройств)
- Sophos Firewall (2 шлюза, XML API)
- Python + Bash (только stdlib)
- rsyslog для централизованного логирования

## Зачем runbook'и?

Инфраструктура ломается предсказуемыми способами. Одни и те же 5 ловушек вызывают 80% отказов при провижининге VM. Одни и те же 3 проблемы — большинство жалоб на Wi-Fi. Их документирование означает:
- Новые члены команды входят в курс дела быстрее
- Инциденты в 3 часа ночи решаются следованием шагам, а не отладкой
- ИИ-агенты могут надёжно следовать процедурам

## Лицензия
MIT

## 📬 Контакты

Вопросы? Пишите: **[allumaxmail@gmail.com](mailto:allumaxmail@gmail.com)**

---

<div align="center">

[![English](https://img.shields.io/badge/README-English-blue)](README.md)
[![Русский](https://img.shields.io/badge/README-Русский-red)](README.ru.md)
[![Oʻzbekcha](https://img.shields.io/badge/README-Oʻzbekcha-green)](README.uz.md)

</div>
