# Lab08

Nama  : Muhammad Arkhamullah Rifai Asshidiq

NIM   : 312410545

Kelas : TI.24.A.5

## kode program
```python
class DaftarNilaiMahasiswa:
    def __init__(self):
        self.daftar_mahasiswa = []

    def tambah(self, nama, tugas, uts, uas):
        self.daftar_mahasiswa.append({  'nama': nama, 'tugas': tugas,  'uts': uts, 'uas': uas,  'nilai_akhir': tugas * 0.3 + uts * 0.35 + uas * 0.35 })
        print(f"Data {nama} berhasil ditambahkan.")

    def tampilkan(self):
        if not self.daftar_mahasiswa:
            print("Tidak ada data mahasiswa.")
        else:
            for data in self.daftar_mahasiswa:
                print(f"Nama: {data['nama']}, Tugas: {data['tugas']}, UTS: {data['uts']}, "
                      f"UAS: {data['uas']}, Nilai Akhir: {data['nilai_akhir']:.2f}")

    def hapus(self, nama):
        for data in self.daftar_mahasiswa:
            if data['nama'] == nama:
                self.daftar_mahasiswa.remove(data)
                print(f"Data {nama} berhasil dihapus.")
                return
        print(f"Data {nama} tidak ditemukan.")

    def ubah(self, nama):
        for data in self.daftar_mahasiswa:
            if data['nama'] == nama:
                data['tugas'] = float(input("Masukkan nilai tugas baru: "))
                data['uts'] = float(input("Masukkan nilai UTS baru: "))
                data['uas'] = float(input("Masukkan nilai UAS baru: "))
                data['nilai_akhir'] = data['tugas'] * 0.3 + data['uts'] * 0.35 + data['uas'] * 0.35
                print("Data berhasil diubah.")
                return
        print(f"Data {nama} tidak ditemukan.")

def main():
    daftar = DaftarNilaiMahasiswa()

    while True:
        print("\nMenu:\n1. Tambah Data mahasiswa\n2. Tampilkan Data mahasiswa\n3. Hapus Data mahasiswa\n4. Ubah Data mahasiswa\n5. Keluar")
        pilihan = input("Pilih (1-5): ")

        if pilihan == '1':
            daftar.tambah(input("Nama: "), float(input("Tugas: ")), float(input("UTS: ")), float(input("UAS: ")))
        elif pilihan == '2':
            daftar.tampilkan()
        elif pilihan == '3':
            daftar.hapus(input("Nama yang akan dihapus: "))
        elif pilihan == '4':
            daftar.ubah(input("Nama yang akan diubah: "))
        elif pilihan == '5':
            print("selesai!")
            break
        else:
            print("Pilihan tidak valid.")

if __name__ == "__main__":
    main()
```
# Eksekusi program(output)
![Foto](https://github.com/MuhammadArkham/Lab08/blob/main/Screenshot%202024-12-10%20170943.png?raw=true)
![Foto](https://github.com/MuhammadArkham/Lab08/blob/main/Screenshot%202024-12-10%20171004.png?raw=true)

## Penjelasan Program Pengelola Nilai Mahasiswa

### 1. Class `DaftarNilaiMahasiswa`
  
Class ini adalah inti program yang berfungsi untuk menyimpan dan mengelola data mahasiswa. Di dalam class terdapat atribut dan metode (fungsi) untuk mempermudah pengelolaan data.

```python
class DaftarNilaiMahasiswa:
    def __init__(self):
        # Inisialisasi daftar untuk menyimpan data mahasiswa
        self.daftar_mahasiswa = []
```

---

### 2. Metode `tambah()`
 
Metode ini digunakan untuk menambahkan data mahasiswa. Data yang ditambahkan meliputi nama, nilai tugas, UTS, UAS, dan nilai akhir. Nilai akhir dihitung berdasarkan bobot tugas, UTS, dan UAS.

```python
    def tambah(self, nama, tugas, uts, uas):
        # Menambahkan data mahasiswa ke dalam daftar
        data = {
            'nama': nama,
            'tugas': tugas,
            'uts': uts,
            'uas': uas,
            'nilai_akhir': tugas * 0.3 + uts * 0.35 + uas * 0.35
        }
        self.daftar_mahasiswa.append(data)
        print(f"Data {nama} berhasil ditambahkan.")
```

---

### 3. Metode `tampilkan()`

Metode ini menampilkan semua data mahasiswa yang tersimpan. Jika tidak ada data, program akan memberi tahu pengguna bahwa daftar kosong.

```python
    def tampilkan(self):
        # Menampilkan semua data mahasiswa
        if not self.daftar_mahasiswa:
            print("Tidak ada data mahasiswa.")
        else:
            for data in self.daftar_mahasiswa:
                print(f"Nama: {data['nama']}, Tugas: {data['tugas']}, UTS: {data['uts']}, "
                      f"UAS: {data['uas']}, Nilai Akhir: {data['nilai_akhir']:.2f}")
```

---

### 4. Metode `hapus()`

Metode ini digunakan untuk menghapus data mahasiswa berdasarkan nama. Jika nama yang dimasukkan tidak ditemukan, program akan memberi tahu pengguna.


```python
    def hapus(self, nama):
        # Menghapus data mahasiswa berdasarkan nama
        for data in self.daftar_mahasiswa:
            if data['nama'] == nama:
                self.daftar_mahasiswa.remove(data)
                print(f"Data {nama} berhasil dihapus.")
                return
        print(f"Data {nama} tidak ditemukan.")
```

---
### 5. Metode `ubah()`
 
Metode ini memungkinkan pengguna untuk mengubah nilai tugas, UTS, dan UAS mahasiswa berdasarkan nama. Nilai akhir akan diperbarui secara otomatis setelah data diubah.

```python
    def ubah(self, nama):
        # Mengubah nilai tugas, UTS, dan UAS mahasiswa berdasarkan nama
        for data in self.daftar_mahasiswa:
            if data['nama'] == nama:
                try:
                    data['tugas'] = float(input("Masukkan nilai tugas baru: "))
                    data['uts'] = float(input("Masukkan nilai UTS baru: "))
                    data['uas'] = float(input("Masukkan nilai UAS baru: "))
                    data['nilai_akhir'] = data['tugas'] * 0.3 + data['uts'] * 0.35 + data['uas'] * 0.35
                    print(f"Data {nama} berhasil diubah.")
                    return
                except ValueError:
                    print("Input harus berupa angka!")
                    return
        print(f"Data {nama} tidak ditemukan.")
```
---
### 6. Fungsi `main()`
  
Fungsi ini menyediakan menu interaktif untuk pengguna. Pengguna dapat memilih salah satu dari lima opsi: tambah data, tampilkan data, hapus data, ubah data, atau keluar dari program.

```python
def main():
    daftar = DaftarNilaiMahasiswa()

    while True:
        print("\nMenu:\n1. Tambah Data mahasiswa\n2. Tampilkan Data mahasiswa\n3. Hapus Data mahasiswa\n4. Ubah Data mahasiswa\n5. Keluar")
        pilihan = input("Pilih (1-5): ")

        if pilihan == '1':
            try:
                nama = input("Nama: ")
                tugas = float(input("Tugas: "))
                uts = float(input("UTS: "))
                uas = float(input("UAS: "))
                daftar.tambah(nama, tugas, uts, uas)
            except ValueError:
                print("Input nilai harus berupa angka!")
        elif pilihan == '2':
            daftar.tampilkan()
        elif pilihan == '3':
            nama = input("Nama yang akan dihapus: ")
            daftar.hapus(nama)
        elif pilihan == '4':
            nama = input("Nama yang akan diubah: ")
            daftar.ubah(nama)
        elif pilihan == '5':
            print("Program selesai. Terima kasih!")
            break
        else:
            print("Pilihan tidak valid.")
```

# Flowchart dari program 
![Foto](https://github.com/MuhammadArkham/Lab08/blob/main/Flowchart.png?raw=true)

# Diagram class program
![Foto](https://github.com/MuhammadArkham/Lab08/blob/main/Diagram%20class%20(1).png?raw=true)
