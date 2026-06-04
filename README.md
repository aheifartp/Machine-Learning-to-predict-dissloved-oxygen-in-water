# Machine-Learning-to-predict-dissloved-oxygen-in-water
# Project Siscer: Prediksi Dissolved Oxygen (Oksigen Terlarut) dalam Air

## Deskripsi Proyek
**Project Siscer** adalah proyek Machine Learning yang dirancang untuk memprediksi tingkat **Dissolved Oxygen (mg/L)** dalam air menggunakan berbagai parameter kualitas air. Proyek ini dibangun menggunakan Python dan menerapkan model *Multiple Linear Regression* untuk memahami hubungan antara sifat fisik/kimia air dan konsentrasi oksigen.

## Dataset
Model ini dilatih menggunakan dataset (`Dataset_water.csv`) yang berisi 500 sampel air.

**Fitur (Input):**
* **pH:** Tingkat keasaman atau kebasaan air.
* **Temperature (°C):** Suhu air.
* **Turbidity (NTU):** Kekeruhan cairan.
* **Conductivity (µS/cm):** Kemampuan air untuk menghantarkan arus listrik.

**Variabel Target (Output):**
* **Dissolved Oxygen (mg/L):** Jumlah oksigen yang terlarut dalam air.

*(Catatan: Kolom `Sample ID` dihapus selama proses persiapan data karena tidak memiliki nilai prediktif).*

## Tech Stack
* **Bahasa:** Python 3
* **Library:** 
  * `pandas` untuk manipulasi dan analisis data.
  * `scikit-learn` untuk pemisahan data, pembuatan model, dan evaluasi matriks.
  * `matplotlib` untuk visualisasi data.

## Alur Kerja (Workflow)
1. **Load Data:** Mengimpor dataset menggunakan Pandas.
2. **Data Preparation:** Memisahkan variabel independen (X) dari variabel dependen (y) dan menghapus kolom yang tidak relevan.
3. **Data Splitting:** Membagi dataset menjadi data latih (80%) dan data uji (20%) menggunakan `train_test_split` dengan *random state* 100 untuk reproduktibilitas.
4. **Model Building:** Melatih model `LinearRegression` pada data latih.
5. **Evaluation:** Mengukur performa model menggunakan *Mean Squared Error* (MSE) dan skor *R-squared* (R2).
6. **Visualization:** Membuat plot sebaran (scatter plot) nilai Aktual vs. Prediksi untuk menilai secara visual seberapa baik model menyesuaikan dengan data latih.

## Evaluasi Model
Model Linear Regression menghasilkan metrik performa berikut:

* **Data Latih (Training):**
  * Mean Squared Error (MSE): **0.212**
  * R-squared (R2) Score: **0.679**
* **Data Uji (Testing):**
  * Mean Squared Error (MSE): **0.205**
  * R-squared (R2) Score: **0.714**

Skor R2 sebesar ~0.71 pada data uji menunjukkan bahwa model ini mampu menjelaskan sekitar 71% varians tingkat oksigen terlarut berdasarkan parameter kualitas air yang diberikan.

## Contoh Penggunaan
Anda dapat memasukkan array fitur baru ke dalam model yang telah dilatih untuk memprediksi tingkat oksigen terlarut. Format input harus sesuai dengan urutan fitur model: `[pH, Temperature, Turbidity, Conductivity]`.

```python
# Contoh Input: pH=7.25, Temp=23.1°C, Turbidity=4.5 NTU, Conductivity=342 µS/cm
x_input = [[7.25, 23.1, 4.5, 342]]

# Melakukan Prediksi
y_pred = lr.predict(x_input)

print("Hasil prediksi:", y_pred)
# Output yang diharapkan: [8.38011947] mg/L
