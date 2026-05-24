# Analisis Data COVID-19 Global menggunakan Python & Pandas

![Python](https://img.shields.io/badge/-Python-085041?style=flat&labelColor=E1F5EE&color=085041) ![Pandas](https://img.shields.io/badge/-Pandas-085041?style=flat&labelColor=E1F5EE&color=085041) ![Jupyter Notebook](https://img.shields.io/badge/-Jupyter%20Notebook-085041?style=flat&labelColor=E1F5EE&color=085041) ![Data Cleaning](https://img.shields.io/badge/-Data%20Cleaning-085041?style=flat&labelColor=E1F5EE&color=085041) ![EDA](https://img.shields.io/badge/-EDA-085041?style=flat&labelColor=E1F5EE&color=085041) 

---


## Tentang proyek

Proyek ini menganalisis penyebaran COVID-19 di berbagai negara menggunakan dataset publik. Fokus utama pada proses data cleaning, eksplorasi data, dan perbandingan kasus antar negara.


## Tujuan analisis

- Memahami distribusi kasus COVID-19 per negara dan per tanggal
- Mengidentifikasi dan menangani missing values pada dataset besar
- Membandingkan total kasus dan kematian antar negara (UK, US, Guam)

## Dataset

Sumber: datacovid19.csv — 1.000 baris × 13 kolom

- Kolom utama: country_region, date, confirmed, deaths, recovered, active
- Terdapat missing values pada kolom province_state, latitude, longitude, dan lainnya

## Tahapan analisis


### 1. Load & eksplorasi data

```
import pandas as pd
df = pd.read_csv("datacovid19.csv")
print(df.shape)  # 1000 rows x 13 columns
```


### 2. Filtering & grouping

```
# Filter kasus di atas 100
filtered_df = df[df["Cases"] > 100]

# Total kasus per negara
grouped_df = df.groupby("Country").sum()
```


### 3. Data cleaning — menangani missing values

```
# Isi kolom numerik dengan rata-rata
df["Cases"] = df["Cases"].fillna(df["Cases"].mean())

# Isi kolom kategori dengan modus
df["Country"] = df["Country"].fillna(df["Country"].mode()[0])
```

> Hasil: Semua kolom berhasil dibersihkan dari 0 missing values setelah proses cleaning.


## Insight utama

- UK memiliki total kasus lebih tinggi dibanding US pada periode Januari–Februari 2020
- Kolom combined_key memiliki missing values terbanyak (1.000 dari 1.000 baris)
- Setelah cleaning, dataset siap untuk analisis lanjutan seperti visualisasi tren harian

## Cara menjalankan

```
git clone https://github.com/weaslyrx/covid19-analysis
cd covid19-analysis
pip install pandas jupyter
jupyter notebook
```


## Tools

![Python 3.x](https://img.shields.io/badge/-Python%203.x-085041?style=flat&labelColor=E1F5EE&color=085041) ![Pandas](https://img.shields.io/badge/-Pandas-085041?style=flat&labelColor=E1F5EE&color=085041) ![Jupyter Notebook](https://img.shields.io/badge/-Jupyter%20Notebook-085041?style=flat&labelColor=E1F5EE&color=085041) 

