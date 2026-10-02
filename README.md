# 👻 Ghost Biztonsági Modul
**PowerShell-alapú Windows és Azure Biztonsági Megerősítő Eszköz**

> **Proaktív biztonsági megerősítés Windows végpontokhoz és Azure környezetekhez.** A Ghost PowerShell-alapú megerősítő funkciókat biztosít, amelyek segíthetnek csökkenteni a gyakori támadási vektorokat a szükségtelen szolgáltatások és protokollok letiltásával.

## ⚠️ Fontos Jognyilatkozatok

**TESZTELÉS SZÜKSÉGES**: Mindig először nem-termelési környezetben tesztelje a Ghost-ot. A szolgáltatások letiltása hatással lehet a jogos üzleti funkciókra.

**NINCS GARANCIA**: Bár a Ghost a gyakori támadási vektorokat célozza meg, egyetlen biztonsági eszköz sem tud minden támadást megakadályozni. Ez egy átfogó biztonsági stratégia egyik összetevője.

**MŰKÖDÉSI HATÁS**: Egyes funkciók befolyásolhatják a rendszer működését. Telepítés előtt alaposan tekintse át minden beállítást.

**SZAKMAI ÉRTÉKELÉS**: Termelési környezetek esetében konzultáljon biztonsági szakemberekkel, hogy a beállítások megfeleljenek szervezete igényeinek.

## 📊 A Biztonsági Helyzet

A ransomware károk **2025-ben 57 milliárd dollárra** emelkedtek, a kutatások azt mutatják, hogy sok sikeres támadás az alapvető Windows szolgáltatások és helytelen konfigurációk kihasználásával történik. A gyakori támadási vektorok közé tartoznak:

- **A ransomware esetek 90%-a** RDP kihasználással jár
- **Az SMBv1 sebezhetőségek** lehetővé tették az olyan támadásokat, mint a WannaCry és NotPetya
- **A dokumentum makrók** továbbra is a malware szállítás elsődleges módja
- **USB-alapú támadások** továbbra is légmentesen elzárt hálózatokat céloznak
- **A PowerShell visszaélés** az elmúlt években jelentősen megnőtt

## 🛡️ Ghost Biztonsági Funkciók

A Ghost **16 Windows megerősítő funkciót** és **Azure biztonsági integrációt** biztosít:

### Windows Végpont Megerősítés

| Funkció | Cél | Megfontolások |
|----------|---------|----------------|
| `Set-RDP` | Távoli asztali hozzáférés kezelése | Hatással lehet a távoli adminisztrációra |
| `Set-SMBv1` | Örökölt SMB protokoll vezérlés | Nagyon régi rendszerekhez szükséges |
| `Set-AutoRun` | AutoPlay/AutoRun vezérlés | Hatással lehet a felhasználói kényelemre |
| `Set-USBStorage` | USB tárolóeszközök korlátozása | Hatással lehet a jogos USB használatra |
| `Set-Macros` | Office makró végrehajtás vezérlés | Hatással lehet a makróval rendelkező dokumentumokra |
| `Set-PSRemoting` | PowerShell távoli kapcsolat kezelése | Hatással lehet a távoli kezelésre |
| `Set-WinRM` | Windows Remote Management vezérlés | Hatással lehet a távoli adminisztrációra |
| `Set-LLMNR` | Névfeloldási protokoll kezelése | Általában biztonságos letiltani |
| `Set-NetBIOS` | NetBIOS TCP/IP feletti vezérlés | Hatással lehet az örökölt alkalmazásokra |
| `Set-AdminShares` | Adminisztratív megosztások kezelése | Hatással lehet a távoli fájl hozzáférésre |
| `Set-Telemetry` | Adatgyűjtés vezérlés | Hatással lehet a diagnosztikai képességekre |
| `Set-GuestAccount` | Vendég fiók kezelése | Általában biztonságos letiltani |
| `Set-ICMP` | Ping válaszok vezérlése | Hatással lehet a hálózati diagnosztikára |
| `Set-RemoteAssistance` | Távoli segítség kezelése | Hatással lehet a helpdesk működésre |
| `Set-NetworkDiscovery` | Hálózati felderítés vezérlése | Hatással lehet a hálózati böngészésre |
| `Set-Firewall` | Windows tűzfal kezelése | Kritikus a hálózati biztonsághoz |

### Azure Felhő Biztonság

| Funkció | Cél | Követelmények |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Alapvető Azure AD biztonság engedélyezése | Microsoft Graph engedélyek |
| `Set-AzureConditionalAccess` | Hozzáférési szabályzatok konfigurálása | Azure AD P1/P2 licencelés |
| `Set-AzurePrivilegedUsers` | Privilegizált fiókok auditálása | Globális adminisztrátori engedélyek |

### Vállalati Telepítési Lehetőségek

| Módszer | Használati Eset | Követelmények |
|--------|----------|--------------|
| **Közvetlen Végrehajtás** | Tesztelés, kis környezetek | Helyi adminisztrátori jogok |
| **Group Policy** | Domén környezetek | Domén adminisztrátor, GP kezelés |
| **Microsoft Intune** | Felhőben kezelt eszközök | Intune licencelés, Graph API |

## 🚀 Gyors Kezdés

### Biztonsági Értékelés
```powershell
# Ghost modul betöltése
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Jelenlegi biztonsági helyzet ellenőrzése
Get-Ghost
```

### Alapvető Megerősítés (Először Tesztelje)
```powershell
# Alapvető megerősítés - először laboratóriumi környezetben tesztelje
Set-Ghost -SMBv1 -AutoRun -Macros

# Változások áttekintése
Get-Ghost
```

### Vállalati Telepítés
```powershell
# Group Policy telepítés (domén környezetek)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune telepítés (felhőben kezelt eszközök)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Telepítési Módszerek

### 1. lehetőség: Közvetlen Letöltés (Tesztelés)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### 2. lehetőség: Modul Telepítés
```powershell
# Telepítés PowerShell Gallery-ből (amikor elérhető)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### 3. lehetőség: Vállalati Telepítés
```powershell
# Másolás hálózati helyre Group Policy telepítéshez
# Intune PowerShell szkriptek konfigurálása felhő telepítéshez
```

## 💼 Használati Eset Példák

### Kisvállalkozás
```powershell
# Alapvető védelem minimális hatással
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Egészségügyi Környezet
```powershell
# HIPAA-fókuszú megerősítés
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Pénzügyi Szolgáltatások
```powershell
# Magas biztonsági konfiguráció
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Felhő-Első Szervezet
```powershell
# Intune-kezelt telepítés
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Funkció Részletek

### Alapvető Megerősítő Funkciók

#### Hálózati Szolgáltatások
- **RDP**: Blokkolja a távoli asztali hozzáférést vagy randomizálja a portot
- **SMBv1**: Letiltja az örökölt fájlmegosztási protokollt
- **ICMP**: Megakadályozza a ping válaszokat a felderítéshez
- **LLMNR/NetBIOS**: Blokkolja az örökölt névfeloldási protokollokat

#### Alkalmazás Biztonság  
- **Makrók**: Letiltja a makró végrehajtást Office alkalmazásokban
- **AutoRun**: Megakadályozza az automatikus végrehajtást cserélhető adathordozókról

#### Távoli Kezelés
- **PSRemoting**: Letiltja a PowerShell távoli munkameneteket
- **WinRM**: Leállítja a Windows Remote Management-et
- **Remote Assistance**: Blokkolja a távoli segítség kapcsolatokat

#### Hozzáférés Vezérlés
- **Admin Shares**: Letiltja a C$, ADMIN$ megosztásokat
- **Guest Account**: Letiltja a vendég fiók hozzáférést
- **USB Storage**: Korlátozza az USB eszköz használatot

### Azure Integráció
```powershell
# Csatlakozás Azure bérlőhöz
Connect-AzureGhost -Interactive

# Biztonsági alapértelmezések engedélyezése
Set-AzureSecurityDefaults -Enable

# Feltételes hozzáférés konfigurálása
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Privilegizált felhasználók auditálása
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integráció (Új a v2-ben)
```powershell
# Csatlakozás Intune-hoz
Connect-IntuneGhost -Interactive

# Telepítés Intune szabályzatokon keresztül
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Fontos Megfontolások

### Tesztelési Követelmények
- **Laboratóriumi Környezet**: Először izolált környezetben tesztelje az összes beállítást
- **Szakaszos Telepítés**: Fokozatosan vezesse be a problémák azonosításához
- **Visszaállítási Terv**: Győződjön meg róla, hogy szükség esetén visszavonhatja a változásokat
- **Dokumentáció**: Rögzítse, mely beállítások működnek az Ön környezetében

### Potenciális Hatás
- **Felhasználói Produktivitás**: Egyes beállítások befolyásolhatják a napi munkafolyamatokat
- **Örökölt Alkalmazások**: A régebbi rendszerek bizonyos protokollokat igényelhetnek
- **Távoli Hozzáférés**: Vegye figyelembe a hatást a jogos távoli adminisztrációra
- **Üzleti Folyamatok**: Ellenőrizze, hogy a beállítások nem törnek-e kritikus funkciókat

### Biztonsági Korlátok
- **Védelem Mélységben**: A Ghost a biztonság egy rétege, nem teljes megoldás
- **Folyamatos Kezelés**: A biztonság folyamatos figyelést és frissítéseket igényel
- **Felhasználói Képzés**: A technikai vezérléseket biztonsági tudatossággal kell párosítani
- **Fenyegetés Evolúció**: Az új támadási módszerek megkerülhetik a jelenlegi védelmeket

## 🎯 Példa Támadási Forgatókönyvek

Míg a Ghost a gyakori támadási vektorokat célozza meg, a konkrét megelőzés a megfelelő implementációtól és teszteléstől függ:

### WannaCry-stílusú Támadások
- **Mérséklés**: `Set-Ghost -SMBv1` letiltja a sebezhető protokollt
- **Megfontolás**: Győződjön meg róla, hogy nincs örökölt rendszer, amelynek SMBv1-re van szüksége

### RDP-alapú Ransomware
- **Mérséklés**: `Set-Ghost -RDP` blokkolja a távoli asztali hozzáférést
- **Megfontolás**: Alternatív távoli hozzáférési módszereket igényelhet

### Dokumentum-alapú Malware
- **Mérséklés**: `Set-Ghost -Macros` letiltja a makró végrehajtást
- **Megfontolás**: Hatással lehet a jogos makróval rendelkező dokumentumokra

### USB-szállított Fenyegetések
- **Mérséklés**: `Set-Ghost -USBStorage -AutoRun` korlátozza az USB funkcionalitást
- **Megfontolás**: Hatással lehet a jogos USB eszköz használatra

## 🏢 Vállalati Funkciók

### Group Policy Támogatás
```powershell
# Beállítások alkalmazása Group Policy registry-n keresztül
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# A beállítások a GP frissítés után domén-szerte érvényesülnek
gpupdate /force
```

### Microsoft Intune Integráció
```powershell
# Intune szabályzatok létrehozása Ghost beállításokhoz
Set-IntuneGhost -Settings $GhostSettings -Interactive

# A szabályzatok automatikusan települnek a kezelt eszközökre
```

### Megfelelőségi Jelentések
```powershell
# Biztonsági értékelési jelentés generálása
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure biztonsági helyzet jelentés
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Legjobb Gyakorlatok

### Telepítés Előtt
1. **Jelenlegi Állapot Dokumentálása**: Futtassa a `Get-Ghost`-ot változások előtt
2. **Alapos Tesztelés**: Validáljon nem-termelési környezetben
3. **Visszaállítási Terv**: Tudja, hogyan fordítsa vissza minden beállítást
4. **Érdekelt Felek Áttekintése**: Győződjön meg róla, hogy az üzleti egységek jóváhagyják a változásokat

### Telepítés Alatt
1. **Szakaszos Megközelítés**: Először pilot csoportokba telepítsen
2. **Hatás Figyelése**: Figyelje a felhasználói panaszokat vagy rendszerproblémákat
3. **Problémák Dokumentálása**: Rögzítsen minden problémát jövőbeli referenciához
4. **Változások Kommunikálása**: Tájékoztassa a felhasználókat a biztonsági fejlesztésekről

### Telepítés Után
1. **Rendszeres Értékelés**: Időszakosan futtassa a `Get-Ghost`-ot a beállítások ellenőrzéséhez
2. **Dokumentáció Frissítése**: Tartsa naprakészen a biztonsági konfigurációkat
3. **Hatékonyság Áttekintése**: Figyelje a biztonsági incidenseket
4. **Folyamatos Fejlesztés**: Állítsa be a beállításokat a fenyegetési táj alapján

## 🔧 Hibaelhárítás

### Gyakori Problémák
- **Engedély Hibák**: Győződjön meg róla, hogy a PowerShell munkamenet emelt szintű
- **Szolgáltatás Függőségek**: Egyes szolgáltatások függőségekkel rendelkezhetnek
- **Alkalmazás Kompatibilitás**: Teszteljen üzleti alkalmazásokkal
- **Hálózati Kapcsolat**: Ellenőrizze, hogy a távoli hozzáférés még működik

### Helyreállítási Lehetőségek
```powershell
# Szükség esetén konkrét szolgáltatások újra engedélyezése
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 A Szerzőről

**Jim Tyler** - Microsoft MVP PowerShell-hez
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ feliratkozó)
- **Hírlevel**: [PowerShell.News](https://powershell.news) - Heti biztonsági intelligencia
- **Szerző**: "PowerShell for Systems Engineers"
- **Tapasztalat**: Évtizedek PowerShell automatizálás és Windows biztonság

## 📄 Licenc és Jogi Nyilatkozat

### MIT Licenc
A Ghost MIT licenc alatt van biztosítva ingyenes használatra, módosításra és terjesztésre.

### Biztonsági Jogi Nyilatkozat
- **Nincs Garancia**: A Ghost "ahogy van" alapon van biztosítva, mindenféle garancia nélkül
- **Tesztelés Szükséges**: Mindig először nem-termelési környezetben teszteljen
- **Szakmai Útmutatás**: Termelési telepítésekhez konzultáljon biztonsági szakemberekkel
- **Működési Hatás**: A szerzők nem felelősek semmilyen működési zavarokért
- **Átfogó Biztonság**: A Ghost egy teljes biztonsági stratégia egyik összetevője

### Támogatás
- **GitHub Issues**: [Hibák jelentése vagy funkciók kérése](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentáció**: Használja a `Get-Help <function> -Full`-t részletes segítségért
- **Közösség**: PowerShell és biztonsági közösségi fórumok

---

**🔒 Erősítse meg biztonsági helyzetét a Ghost-tal - de mindig először teszteljen.**

```powershell
# Kezdjen értékeléssel, ne feltételezésekkel
Get-Ghost
```

**⭐ Csillagozza meg ezt a repository-t, ha a Ghost segít javítani biztonsági helyzetét!**