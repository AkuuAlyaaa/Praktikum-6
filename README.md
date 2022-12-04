NAMA      : ALYA SEFHIA EKA PUTRI

NIM       : 312210108

KELAS     : TI.22.B1

# Latihan Menggunakan Function dan Lambda pada python dan membuat program crud sederhana

1. Pertama kita buat buat folder 11-function-lambda dan didalam kita buat file bernama Latihan.py dan Praktikum6.py.

    ![Latihan 6](https://user-images.githubusercontent.com/115520278/205452342-c2032512-e8b8-42f1-8cb5-49cda3f6f54e.PNG)
  
2. Lalu buka Latihan.py dan masukan coding sebagai berikut lalu run dengan mengetikan perintah berikut diterminal python Latihan.py:

    ![Latihan 6](https://user-images.githubusercontent.com/115520278/205452579-f635eba2-fa75-41f1-b0ff-9fb506523c4f.PNG)

dan ini hasil run nya:

   ![hasil](https://user-images.githubusercontent.com/115520278/205452629-fe4d24d6-cb7d-414a-a68d-f147ab7fdd64.PNG)

3. Selanjutnya kita akan buat program crud sederhana dan berikut flowchart program yang akan dibuat.

    ![flowchart](https://user-images.githubusercontent.com/115520278/205452713-d08047bc-6cbf-458f-9617-fa1076002024.png)

4. Lalu buka file Praktikum6.py dan masukan codingan sebagai berikut lalu run dengan mengetikan perintah berikut diterminal python Praktikum6.py:

                # import tabulate
            from tabulate import tabulate

            # Alya Sefhia Eka Putri
            # TI22B1

            dataMahasiswa = {
                'No' : [],
                'NIM' : [],
                'Nama' :[],
                'Tugas' : [],
                'UTS' : [],
                'UAS' : [],
                'Nilai Akhir' : []

            }
            no = 0
            # fungsi untuk menampilkan data

            def tampilkan():
                print("Berikut data yang ada")
                print(tabulate(dataMahasiswa, headers=[
                    'No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

            # fungsi untuk menambahkan data


            def tambah(no):
                # menginput data
                nim = int(input("Masukkan NIM : "))
                nama = input("Masukkan Nama : ")
                tugas = int(input("Masukkan Nilai Tugas : "))
                uts = int(input("Masukkan Nilai UTS : "))
                uas = int(input("Masukkan Nilai UAS : "))
                nilai_akhir = (tugas * 30 / 100) + (uts * 35 / 100) + (uas * 35 / 100)
                # menambahkan data
                dataMahasiswa['No'].append(no)
                dataMahasiswa['NIM'].append(nim)
                dataMahasiswa['Nama'].append(nama)
                dataMahasiswa['UTS'].append(uts)
                dataMahasiswa['Tugas'].append(tugas)
                dataMahasiswa['UAS'].append(uas)
                dataMahasiswa['Nilai Akhir'].append(nilai_akhir)
                print("Data berhasil di tambahkan.")
                # print(tabulate(dataMahasiswa, headers=[
                #       'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))

            # fungsi untuk mengedit data


            def ubah(nama):
                # cek jika ada nama ersebut di dataMahasiswa
                if nama in dataMahasiswa['Nama']:
                    # cari posisi indexnya lalu di simpan di nimIndex
                    namaindex = dataMahasiswa['Nama'].index(nama)
                    print("Pilih data yang mau di edit")
                    # perulangan mengedit data dalam bentuk pilihan
                    while True:
                        editApa = int(input(
                            "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai UTS, \n (5) Nilai UAS, \n (0) Save Perubahan & exit \n :"))
                        print("")

                        if editApa == 1:
                            # mengubah nim
                            newNim = int(input("Masukkan NIM :"))
                            dataMahasiswa['NIM'][namaindex] = newNim
                        elif editApa == 2:
                            # mengubah nama
                            newNama = input("Masukkan Nama :")
                            dataMahasiswa['Nama'][namaindex] = newNama
                        elif editApa == 3:
                            # mengubah nilai tugas dan nilai akhir
                            newTugas = int(input("Masukkan Nilai Tugas :"))
                            nilai_akhir = (newTugas * 30 / 100) * (dataMahasiswa['UTS'][namaindex] * 35 / 100) * (
                                dataMahasiswa['UAS'][namaindex] * 35 / 100)
                            dataMahasiswa['Tugas'][namaindex] = newTugas
                            dataMahasiswa['Nilai Akhir'][namaindex] = nilai_akhir
                        elif editApa == 4:
                            # mengubah nilai uts dan nilai akhir
                            newUTS = int(input("Masukkan Nilai UTS :"))
                            nilai_akhir = (dataMahasiswa['Tugas'][namaindex] * 30 / 100) * (newUTS * 35 / 100) + (
                               dataMahasiswa['UAS'][namaindex] * 35 / 100)
                            dataMahasiswa['UTS'][namaindex] = newUTS
                            dataMahasiswa['Nilai Akhir'][namaindex] = nilai_akhir
                        elif editApa == 5:
                            # mengubah nilai uas dan nilai akhir
                            newUAS = int(input("Masukkan Nilai UAS :"))
                            nilai_akhir = (dataMahasiswa['Tugas'][namaindex] * 30 / 100) + (dataMahasiswa['UTS'][namaindex] * 35 / 100) * (
                                newUAS * 35 / 100)
                            dataMahasiswa['UAS'][namaindex] = nilai_akhir

                        elif editApa == 0:
                            print('Perubahan data berhasil di simpan,')
                            break
                else:
                    print("Data tidak di temukan")

            # fungsi untuk menghapus data

            def hapus(nama):
                if nama in dataMahasiswa['Nama']:
                    namaIndex = dataMahasiswa['Nama'].index(nama)
                    # menghapus data berdasarkan position index pada nama
                    del dataMahasiswa['No'][namaIndex]
                    del dataMahasiswa['NIM'][namaIndex]
                    del dataMahasiswa['Nama'][namaIndex]
                    del dataMahasiswa['Tugas'][namaIndex]
                    del dataMahasiswa['UTS'][namaIndex]
                    del dataMahasiswa['UAS'][namaIndex]
                    del dataMahasiswa['Nilai Akhir'][namaIndex]
                    print("Data berhasil di hapus. ")
                else:
                    print("Data tidak di temukan")
            # fungsi untuk mencari data

            # melakukan perulangan menggunakan while sampai user menekan huruf Q perulangan akan berhenti
            while True:
                # opsi input pilihan C,R,U,D,F,Q
                tanya = input (
                    "(C) Menambahkan data, \n (R) Melihat semua data, (U) Update data, \n (D) Menghapus data, \n (Q) Keluar Program :") 
                if tanya == "C":
                    while True:
                        no += 1
                        # memanggil fungsi tambah data dan memparsing data no
                        tambah(no)
                        tambahDataLagi = int(input("Tamba data lagi ? (y/n) :"))
                        if tambahDataLagi == 'n':
                            break
                elif tanya == "R":
                    # menampilkan data dalam bentuk table menggunakan package tabulate
                    tampilkan()
                    print("")
                elif tanya == "U":
                    print(tabulate(dataMahasiswa, headers=[
                        'No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
                    nama = input("Masukkan nama yang mau di edit : ")
                    print("")
                    ubah(nama)
                elif tanya == "D":
                    print(tabulate(dataMahasiswa, headers=[
                        'No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_gird"))
                    nama = input("Masukkan nama yang mau di di hapus : ")
                    print("")
                    hapus(nama)
                elif tanya == 'Q':
                    print("")
                    print("Anda telah keluar dari program")
                    break
                    
dan Berikut hasilnya :

Jika memilih opsi C = menambah data maka akan tampil sebagai berikut :

  ![1](https://user-images.githubusercontent.com/115520278/205454793-7739301b-b9d1-4cec-9cb2-848d1819d71d.PNG)
    
Jika memilih opsi R = Melihat semua data maka akan tampil sebagai berikut :

  ![2](https://user-images.githubusercontent.com/115520278/205454835-e012bca4-41b1-40c2-9c31-b5d23dfa52c4.PNG)

Jika memilih opsi U = mengupdate data maka akan tampil sebagai berikut :

  ![3](https://user-images.githubusercontent.com/115520278/205454850-e960ee8e-8621-4c79-a2a5-ae4cb3969d05.PNG)
    
Jika memilih opsi D = Menghapus data maka akan tampil sebagai berikut :

  ![6](https://user-images.githubusercontent.com/115520278/205474725-e53709b8-85cb-4620-aa75-6cb2a2e558c6.PNG)

Jika memilih opsi Q = Keluar Program maka akan tampil sebagai berikut :

  ![5](https://user-images.githubusercontent.com/115520278/205454912-ddea04bf-7664-4fd9-8c27-d11a79457f6c.PNG)
    
Selesai. seperti itulah program crud sederhana yang kita buat,

Terimakasih...........







