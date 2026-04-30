# 🧠 Optimasi Uang Jajan dengan Algoritma Genetika


Kita punya 5 item dengan biaya dan nilai kepuasan masing-masing. Program akan mencari kombinasi item (pilih/tidak pilih) yang menghasilkan **total kepuasan tertinggi** namun total biaya **≤ Rp50.000**.
Algoritma Genetika dipilih sebagai contoh penyelesaian masalah optimasi kombinatorial. Meskipun kasus ini sederhana (hanya 32 kemungkinan), algoritma ini cocok untuk masalah dengan banyak item (ratusan) yang tidak bisa dicoba satu per satu.

## Data Masukan

| Item        | Biaya (Rp) | Nilai Kepuasan |
|-------------|------------|----------------|
| Makan       | 20.000     | 80             |
| Kopi        | 15.000     | 60             |
| Jajan       | 10.000     | 50             |
| Transport   | 10.000     | 70             |
| Internet    | 5.000      | 40             |

**Budget** : Rp50.000

## Struktur Kode

```python
import random
import matplotlib.pyplot as plt

# Konstanta global
items = [...]          # daftar item
BUDGET = 50000
POP_SIZE = 30
GENERATIONS = 100
MUTATION_RATE = 0.2

# Fungsi-fungsi
create_individual()   # membuat satu kromosom acak
init_population()     # membuat populasi awal
fitness(ind)          # menghitung nilai kepuasan (dengan penalti overbudget)
selection(pop)        # seleksi turnamen ukuran 3
crossover(p1, p2)     # one-point crossover
mutate(ind)           # mutasi dengan probabilitas MUTATION_RATE
decode(ind)           # menerjemahkan gen ke nama item, biaya, kepuasan
GA()                  # eksekusi algoritma genetika utama

Cara Kerja Algoritma

    Inisialisasi – Buat 30 individu acak (setiap individu = larik 0/1 panjang 5).

    Evaluasi fitness – Hitung total biaya & kepuasan. Jika biaya > budget, fitness = 0.

    Seleksi (Turnamen) – Ambil 3 individu acak, pilih yang tertinggi fitness-nya. Lakukan dua kali untuk mendapat dua orang tua.

    Crossover – Potong kromosom pada satu titik acak lalu gabungkan bagian kiri dari induk1 dan bagian kanan dari induk2.

    Mutasi – Setiap gen memiliki 20% peluang berubah (0 ⇄ 1).

    Elitism – Dua individu terbaik dari generasi sebelumnya langsung disalin ke generasi baru (agar solusi bagus tidak hilang).

    Ulangi langkah 2–6 sebanyak 100 generasi.

    Output – Cetak kombinasi terbaik dan tampilkan grafik peningkatan fitness.

Cara Menjalankan
Prasyarat

    Python 3.x

    Library matplotlib

Install matplotlib jika belum:
bash

pip install matplotlib

Jalankan program
bash

python optimasi_jajan.py

(Misalkan file disimpan sebagai optimasi_jajan.py.)
Contoh Output
text

===== OPTIMASI UANG JAJAN =====

Gen   0 | Nilai kepuasan: 150
Gen   5 | Nilai kepuasan: 210
Gen  10 | Nilai kepuasan: 240
Gen  15 | Nilai kepuasan: 240
...
Gen  95 | Nilai kepuasan: 240

===== HASIL AKHIR =====
Pilihan: ['Makan', 'Jajan', 'Transport', 'Internet']
Total biaya: 45000
Total kepuasan: 240
Penjelasan: Pengeluaran optimal sesuai budget.
