
# Hidroelectrica România - Integrare pentru Home Assistant 🏠🇷🇴

Această integrare pentru Home Assistant oferă **monitorizare completă** a datelor contractuale, facturilor curente, și istoricul plăților pentru utilizatorii Hidroelectrica România. Integrarea este configurabilă prin interfața UI și permite afișarea informațiilor utile în timp real. 🚀

## 🌟 Caracteristici

### Senzor `Date utilizator`:
  - **🔍 Monitorizare Generală**:
      - Afișează informații detaliate despre utilizator și cont.
  - **📊 Atribute disponibile**:
      - ID utilizator
      - Număr cont utilitate
      - Număr cont
      - Țară
      - Oraș
      - Tip client
      - Ultima actualizare de date
      - Tip contor

### Senzor `Factură restantă`:
  - **🔍 Detalii despre solduri restante**:
      - Afișează dacă există facturi restante și data scadenței.
  - **📊 Atribute disponibile**:
      - Plată restantă (ex. "259.12 lei, depășită cu 1 zi")
      - Total neachitat

### Senzor `Istoric facturi achitate`:
  - **📚 Monitorizare Istoric**:
      - Afișează informații despre plățile efectuate.
  - **📊 Atribute disponibile**:
      - Detalii plăți individuale (ex. "Emisă la data de 19 ianuarie 2024: 168.83 lei")
      - Total achitat
      - Număr total de plăți efectuate

---

## ⚙️ Configurare

### 🛠️ Interfața UI:
1. Adaugă integrarea din meniul **Setări > Dispozitive și Servicii > Adaugă Integrare**.
2. Introdu datele contului Hidroelectrica:
   - **Nume utilizator**: username-ul contului tău Hidroelectrica.
   - **Parolă**: parola asociată contului tău.
3. Specifică intervalul de actualizare (implicit: 3600 secunde).

---

## 🚀 Instalare

### 💡 Instalare prin HACS:
1. Adaugă [depozitul personalizat](https://github.com/cnecrea/hidroelectrica) în HACS. 🛠️
2. Caută integrarea **Hidroelectrica România** și instaleaz-o. ✅
3. Repornește Home Assistant și configurează integrarea. 🔄

### ✋ Instalare manuală:
1. Clonează sau descarcă [depozitul GitHub](https://github.com/cnecrea/hidroelectrica). 📂
2. Copiază folderul `custom_components/hidroelectrica` în directorul `custom_components` al Home Assistant. 🗂️
3. Repornește Home Assistant și configurează integrarea. 🔧

---

## ✨ Exemple de utilizare

### 🔔 Automatizare pentru Factură Restantă:
Creează o automatizare pentru a primi notificări când există o factură restantă.

```yaml
alias: Notificare Factură Restantă
description: Notificare dacă există facturi restante
trigger:
  - platform: state
    entity_id: sensor.hidroelectrica_factura_restanta
    to: "Da"
action:
  - service: notify.mobile_app_your_phone
    data:
      title: "Factură Restantă Detectată! ⚡"
      message: "Aveți o factură restantă în valoare de {{ states('sensor.factura_restanta') }}."
mode: single
```

### 🔍 Card pentru Dashboard:
Afișează datele despre utilizator, facturi restante și istoric plăți pe interfața Home Assistant.

```yaml
type: entities
title: Monitorizare Hidroelectrica România
entities:
  - entity: sensor.date_utilizator
    name: Date Utilizator
  - entity: sensor.hidroelectrica_factura_restanta
    name: Factură Restantă
  - entity: sensor.istoric_facturi_achitate
    name: Istoric Facturi Achitate
```

---

## ☕ Susține dezvoltatorul

Dacă ți-a plăcut această integrare și vrei să sprijini munca depusă, **invită-mă la o cafea**! 🫶  
Nu costă nimic, iar contribuția ta ajută la dezvoltarea viitoare a proiectului. 🙌  

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-Susține%20dezvoltatorul-orange?style=for-the-badge&logo=buy-me-a-coffee)](https://buymeacoffee.com/cnecrea)

Mulțumesc pentru sprijin și apreciez fiecare gest de susținere! 🤗

--- 

## 🧑‍💻 Contribuții

Contribuțiile sunt binevenite! Simte-te liber să trimiți un pull request sau să raportezi probleme [aici](https://github.com/cnecrea/hidroelectrica/issues).

---

## 🌟 Suport
Dacă îți place această integrare, oferă-i un ⭐ pe [GitHub](https://github.com/cnecrea/hidroelectrica/)! 😊
