# Pristupni rad iz Osnova ekonometrije

Ovaj repozitorij sadrži studentski pristupni rad iz kolegija **Osnove ekonometrije**.  
Projekt je pisan na hrvatskom jeziku i dokumentiran tako da bude razumljiv i korisnicima koji nisu primarno programeri.

## Komu je projekt namijenjen

- studentima ekonomije i ekonometrije
- statističarima
- ekonomistima koji žele reproducirati analizu u Pythonu
- svima koji žele vidjeti cjelovit primjer ekonometrijskog workflowa u Jupyter notebooku

## Što projekt radi (I/II/III dio)

Projekt je organiziran kroz tri cjeline:

- **I dio:** priprema varijabli i osnovna deskriptivna analiza
- **II dio:** višestruka regresija i standardni dijagnostički testovi (autokorelacija, heteroskedastičnost, multikolinearnost, OVB)
- **III dio:** stacionarnost i vremenske serije (ADF, diferenciranje, adekvatniji model, VAR, Granger, IRF, FEVD)

Fokus je na metodologiji i pravilnoj interpretaciji testova, bez fokusiranja na implementacijske detalje koda.

## Struktura repozitorija

- `analysis.ipynb` - glavni notebook s kompletnom analizom
- `demand.XLSX` - ulazni skup podataka
- `Pristupni rad-2025-26.docx` - tekst zadatka / specifikacija rada
- `analysis_submission.pdf` - finalni PDF za predaju (bez prikaza code ćelija)
- `requirements.txt` - reproducibilni popis Python paketa (`pip freeze`)
- `requirements-colab.txt` - minimalni popis paketa za pokretanje u Google Colabu

## Kako pokrenuti projekt (detaljan walkthrough)

### 1) Preduvjeti

- Python 3
- `pip`
- preporuka: rad u virtualnom okruženju (`venv`)

### 2) Kreiranje i aktivacija virtualnog okruženja

Windows (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

macOS/Linux (bash/zsh):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3) Instalacija ovisnosti

```bash
pip install -r requirements.txt
```

### 4) Pokretanje notebooka

Opcija A (Jupyter):

```bash
jupyter notebook
```

ili

```bash
jupyter lab
```

Zatim otvori `analysis.ipynb` i pokreni **Run All**.

Opcija B (VS Code):

- otvori projektni folder u VS Code
- otvori `analysis.ipynb`
- odaberi Python kernel iz aktivnog virtualnog okruženja (`.venv`)
- pokreni **Run All**

## Pokretanje u Google Colabu

Google Colab je dobra opcija ako želiš pokretati projekt bez lokalne instalacije Pythona i Jupytera.

### 1) Otvaranje notebooka

- otvori [Google Colab](https://colab.research.google.com/)
- odaberi **Upload notebook**
- učitaj datoteku `analysis.ipynb`

### 2) Instalacija paketa u Colabu

U prvoj ćeliji pokreni:

```python
!pip install -q -r requirements-colab.txt
```

### 3) Učitavanje podataka

- u Colabu učitaj datoteku `demand.XLSX` (panel Files -> Upload)
- zatim pokreni ovu ćeliju da se uskladi naziv koji koristi notebook:

```python
import os
import shutil

if os.path.exists("demand.XLSX") and not os.path.exists("demand.xlsx"):
    shutil.copy("demand.XLSX", "demand.xlsx")
```

### 4) Pokretanje analize

- u Colabu odaberi **Runtime -> Run all**

## Praktične napomene i poznata ograničenja

- U repozitoriju je dataset nazvan `demand.XLSX`, dok kod učitava `demand.xlsx`.
- Na Windowsu to najčešće radi zbog case-insensitive datotečnog sustava.
- Na Linux/macOS (case-sensitive sustavi) potrebno je uskladiti naziv datoteke i putanju u kodu.
- `analysis.ipynb` je izvor istine; PDF je izlazni deliverable.
- `requirements.txt` je puni reproducibilni freeze lokalnog (Windows) okruženja; za Colab koristi `requirements-colab.txt`.

## Kratki sažetak na engleskom

This repository contains a Croatian student project for an introductory econometrics course.  
The main work is in a Jupyter notebook that covers regression analysis, diagnostics, stationarity checks, and VAR-based time-series analysis.  
The project is documented for economists, statisticians, and students, not only developers.  
The final deliverable is `analysis_submission.pdf`, while `analysis.ipynb` remains the primary source file.
