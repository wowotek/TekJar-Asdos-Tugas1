> Tugas Ini di rilis oleh 
> **Erlangga Ibrahim** secara terbuka (*Open Source*)
> Dibawah Lisensi **GNU GPLv3**
> untuk keterangan dan informasi lebih lanjut dapat dibuka di : https://www.gnu.org/licenses/gpl-3.0.en.html
> atau dengan membaca file `LICENSE`

> Semua sumber yang digunakan pada tugas ini, dapat dilihat pada :
> https://github.com/wowotek/TekJar-Tugas1

> **PERINGATAN** : *Tugas ini dirilis setelah tenggat waktu pengumpulan tugas, dan tidak akan berlaku untuk kolega dengan tenggat waktu pengumpulan yang sama*

> **PERINGATAN** : *Tugas ini dirilis tanpa garansi, termasuk nilai yang di-nihilkan oleh sebab mencontek dan/atau menyalin dan/atau meniru yang bersumber dari tugas ini*
# Teknik Jaringan - Tugas1

## Deskripsi Tugas

### Ide Awal : 
Install dan meng-integrasikan software Virtual Machine kedalam GNS3
### Pembakuan :
1. Install ~~VMWare~~
> **PERINGATAN** : Menggunakan software bajakan sangat merugikan developer software tersebut
> dan melanggar hukum. pilih alternatif *Open Source* atau software Gratis/*Libre* Lainnya untuk mengihindari hal tersebut. Contoh : [**_VirtualBox_**](https://www.virtualbox.org/wiki/Downloads)
2. Install GNS3
3. Install Qemu VM didalam GNS3
4. Install

## Hasil Pengerjaan
> **PERINGATAN**: Tugas ini dibuat di Sistem Operasi **_GNU/Linux_** Distribusi **Ubuntu v18.04**, Tidak ada jaminan dapat bekerja di Sistem Operasi Lain

### _(Opsional)_ Setup `AMD-V` Di Bios Anda
> **PERINGATAN**: Tahap ini dibuat menggunakan `BIOS` _Motherboard_ **Gigabyte**, tidak ada jaminan tahap akan sama dengan _Motherboard_ lain.
1. Masuk kedalam bios anda (Tekan Tombol _Delete_ saat `Booting`)
2. Pilih _Tab_ `M.I.T`
3. Lalu pilih menu `Advanced Frequency Settings`
4. Lalu pastikan menu `SVM Mode` pada posisi `Enabled`
5. Arahkan ke _Tab_ `Save & Exit`
6. Lalu tekan `Save Changes & Reboot`

### VMware
#### Installasi VMware
1. Download `VMware` dari Link berikut : [VMware.com](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)
    1. Dengan browser
    2. Dengan terminal
    ```bash
    $ wget -P ~/Downloads \
        https://download3.vmware.com/software/wkst/file/VMware-Workstation-Full-15.1.0-13591040.x86_64.bundle
    ```
2. Pindah Direktori, ke tempat dimana `VMware` di download.
    ```bash
    # dengan asumsi `VMware` di download pada folder `~/Downloads/`
    $ cd ~/Downloads/
    ```
3. _(Opsional)_ Ubah nama installasi `VMware` ke nama yang lebih mudah
    ```bash
    $ mv VMware* vmware.bundle
    ```
4. Jalankan installasi dengan perintah
    ```bash
    $ sudo sh ./vmware.bundle
    ```
5. Masukkan password jika diperlukan
6. Baca Dokumen **_`VMwate Workstation - End User License Agreement`_** dengan seksama
7. Klik **_`I accept the terms in the license agreement`_** lalu tekan tombol `Next`
    > **PERHATIAN !** : Tutorial installasi ini hanya dapat dilakukan jika anda menyetujui perjanjian lisensi yang diberikan oleh developer `VMware Workstation`. **HANYA LAKUKAN TAHAP INI JIKA ANDA MENYETUJUI PERJANJIAN LISENSI TERSEBUT.** Jika anda tidak menyetujui perjanjian lisensi tersebut, silahkan melihat alternatif tutorial menggunakan `VirtualBox`.
8. Baca Dokument **_`VMware OVF Tool component for Linux - End User License Agreement`_** dengan seksama
9. Klik **_`I accept the terms in the license agreement`_** lalu tekan tombol `Next`
    > **PERHATIAN !** : Tutorial installasi ini hanya dapat dilakukan jika anda menyetujui perjanjian lisensi yang diberikan oleh developer `VMware OVF Tool component for Linux`. **HANYA LAKUKAN TAHAP INI JIKA ANDA MENYETUJUI PERJANJIAN LISENSI TERSEBUT.**
10. Tekan `yes` atau `no` sesuai dengan keinginan anda untuk `VMware` dapat cek dan upgrade. Lalu tekan tombol `next`
11. Jendela berikut menanyakan anda untuk bergabung dengan program mereka, silahkan baca lalu putuskan dengan menekan tombol `yes` atau `no`. Lalu tekan tombol `Next`
12. masukkan username yang akan digunakan untuk koneksi ke `Workstation Server`. lalu tekan tombol `next`
13. masukkan direktori untuk penyimpanan data _Virtual Machine_ anda. silahkan gunakan yang sudah di sediakan jika anda kurang yakin. lalu tekan tombol `next`
14. masukkan `Port HTTPS` yang digunakan oleh `Workstation Server`. silahkan gunakan isi yang sudah di sediakan jika anda kurang yakin. lalu tekan tombol `next`
15. _(Opsional)_ masukkan kode lisensi jika anda sudah membeli produk `VMware Workstation Pro 15.0`
16. Pastikan konfigurasi anda telah benar, jika belum, anda dapat kembali dengan menekan tombol `Back`. jika sudah, silahkan lanjutkan installasi dengan menekan tombol `Install`
17. Tunggu proses installasi sampai selesai
18. Proses installasi telah selesai. klik tombol `Close`

#### Installasi GNS3-VM Pada VMware
1. Download GNS3-VM 
    1. Dengan Browser
        1. Download melalui link berikut : [GNS3-VM Downloads](https://www.gns3.com/software/download-vm)
        2. Klik Tombol Download dibawah kolom **_`VMWARE WORKSTATION AND FUSION`_**
    2. Dengan Terminal
    ```bash
    $ wget -P ~/Downloads \
        https://github-production-release-asset-2e65be.s3.amazonaws.com/13111393/ac245300-7896-11e9-85a0-7f143b48505a?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20190518%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20190518T132535Z&X-Amz-Expires=300&X-Amz-Signature=3f02041c5abc0e2fa7d9d98e6d0e6d50dcf082d177f0dff1093c16f57e240939&X-Amz-SignedHeaders=host&actor_id=25195739&response-content-disposition=attachment%3B%20filename%3DGNS3.VM.VMware.Workstation.2.1.17.zip&response-content-type=application%2Foctet-stream
    ```
2. Unzip file yang sudah di download:
    ```bash
    $ unzip GNS3*
    ```
3. Buka `VMware Workstation`
4. Tekan Tombol `Open a Virtual Machine`
5. Arahkan ke File `GNS3*`**`.ova`** yang baru anda Unzip, lalu tekan Open
6. _(Opsional)_ Ubah Nama VM dan Lokasi penyimpanannya.
7. Tekan Import

#### Installasi GNS3-GUI
1. tambahkan Repository `GNS3` kedalam Sistem `APT`
    ```bash
    $ sudo add-apt-repository ppa:gns3/ppa
    ```
2. Update _Listing_ Repository anda
    ```bash
    $ sudo apt-get update
    ```
3. Download dan install `GNS3-GUI`
    ```bash
    $ sudo apt-get install -f -y gns3-gui
    ```
4. Tekan tombol no, jika anda di peringati oleh dialog berikut
5. Tekan tombol yes, jika anda di peringati oleh dialog berikut

#### Setup GNS3
1. Buka GNS3, Lalu anda akan temui jendela Setup Wizard
2. Pilih `Run the topologies in an isolated and standard VM` lalu tekan `Next`
3. Gunakan konfigurasi default untuk `Server path`, `Host binding`, dan `Port` lalu tekan Next
4. Pilih `VMware` pada _Virtualization Software_
5. _(Opsional)_ Ubah nama Virtual Machine, jumlah virtual CPU cores, besar RAM sesuai keinginan anda
6. Tekan tombol Next
7. jendela VMware Workstation secara otomatis akan terbuka. lalu di dalam GNS3-VM silahkan tekan tombol `OK`

#### Installasi Qemu
1. Buka GNS3
2. Di jendela Project, silahkan beri nama dan lokasi penyimpanan
3. 
### Vbox
> TODO : Create VirtualBox Version of this tutorial