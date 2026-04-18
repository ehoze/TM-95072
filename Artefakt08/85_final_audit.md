# 🏦 RAPORT Z AUDYTU BEZPIECZEŃSTWA: APIDEMOS  
**Data:** [18.04.2026]  
**Audytor:** [Eryk 95072]  
**Projekt:** Mobilny System Demonstracyjny (Android)

---

## 📊 1. OCENA KOŃCOWA (SECURITY SCORE)  
**Wynik:** 0 / 100  
**Status:** 🔴 *REJECTED / NEEDS FIX*

---

## 🛡️ 2. KLUCZOWE OBSZARY RYZYKA

### A. Konfiguracja Systemowa (Zadanie 8.1)  
- **Problem:** W pliku Manifest ustawiono `debuggable="true"`.  
- **Ryzyko:** Umożliwia podłączenie debuggera i pozyskanie danych z pamięci operacyjnej.

### B. Wycieki Danych (Zadanie 8.2)  
- **Problem:** W zasobach znajdują się twardo zakodowane wrażliwe frazy (np. `password`).  
- **Ryzyko:** Możliwość przejęcia kont testowych lub dostępu do niepublicznych endpointów.

### C. Biblioteki Zewnętrzne (Zadanie 8.3)  
- **Problem:** Użycie `org.apache.commons` w wersji 1.0.0.  
- **Ryzyko:** Podatność **CVE‑2015‑7501 (CRITICAL)** umożliwiająca zdalne wykonanie kodu na urządzeniu użytkownika.

---

## 📝 3. REKOMENDACJE NAPRAWCZE

1. **[Priorytet 1]** Zaktualizować bibliotekę `org.apache.commons` do najnowszej stabilnej wersji.  
2. **[Priorytet 1]** Wyłączyć tryb debugowania w buildzie produkcyjnym (Release).  
3. **[Priorytet 2]** Usunąć wrażliwe dane ze `strings.xml` i przenieść je do Android Keystore lub innego bezpiecznego magazynu.

---

## 🎓 4. WNIOSKI KOŃCOWE  
Aplikacja w obecnym stanie **nie spełnia wymogów bezpieczeństwa** i nie powinna zostać udostępniona użytkownikom. Krytyczne podatności w bibliotekach oraz błędna konfiguracja manifestu stanowią poważne zagrożenie dla poufności i integralności danych.
