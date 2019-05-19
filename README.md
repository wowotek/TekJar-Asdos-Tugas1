> Tugas Ini di rilis oleh  **Erlangga Ibrahim** secara terbuka (*Open Source*)
> Dibawah Lisensi **GNU GPLv3**. untuk keterangan dan informasi lebih lanjut mengenai
> Lisensi, dapat dibuka di : https://www.gnu.org/licenses/gpl-3.0.en.html
> atau dengan membaca file `LICENSE`

> Semua sumber yang digunakan pada tugas ini, dapat dilihat pada :
> https://github.com/wowotek/TekJar-Tugas1

> **PERINGATAN** : *Tugas ini dirilis setelah tenggat waktu pengumpulan tugas, dan tidak akan berlaku untuk kolega dengan tenggat waktu pengumpulan yang sama*

> **PERINGATAN** : *Tugas ini dirilis tanpa garansi, termasuk nilai yang di-nihilkan oleh sebab mencontek dan/atau menyalin dan/atau meniru yang bersumber dari tugas ini*
# Teknik Jaringan - Tugas1
## Penulis
* Nama : **Erlangga Ibrahim**
* NIM : **672017282**
## Deskripsi Tugas

### Ide Awal : 
Install dan meng-integrasikan software Virtual Machine kedalam GNS3
### Pembakuan :
1. Install ~~VMWare~~
> **PERINGATAN** : Menggunakan software bajakan sangat merugikan developer software tersebut
> dan melanggar hukum. pilih alternatif *Open Source* atau software Gratis/*Libre* Lainnya untuk mengihindari hal tersebut. Contoh : [**_VirtualBox_**](https://www.virtualbox.org/wiki/Downloads)
2. Install GNS3
3. Install Qemu VM didalam GNS3
4. Install Ubuntu Server dalam QemuVM

## Hasil Pengerjaan
> **PERINGATAN**: Tugas ini dibuat di Sistem Operasi **_GNU/Linux_** Distribusi **Ubuntu v18.04**, Tidak ada jaminan dapat bekerja di Sistem Operasi Lain

### _(Opsional)_ Setup `AMD-V` Di Bios Anda
> **PERINGATAN**: Tahap ini dibuat menggunakan `BIOS` _Motherboard_ **Gigabyte**, tidak ada jaminan tahap akan sama dengan _Motherboard_ lain.
1. Masuk kedalam bios anda (Tekan Tombol _Delete_ saat `Booting`)
2. Pilih _Tab_ `M.I.T`, Lalu pilih menu `Advanced Frequency Settings`
    ![amdv1]
3. Pilih Menu `Advanced CPU Core Settings`
    ![amdv2]
4. Lalu pastikan menu `SVM Mode` pada posisi `Enabled`
    ![amdv3]
5. Arahkan ke _Tab_ `Save & Exit`
6. Lalu tekan `Save Changes & Reboot`

### VMware
#### Installasi VMware
1. Download `VMware` dari Link berikut : [VMware.com](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)
    1. Dengan browser
        ![vmware1]
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
    ![vmware2]
7. Klik **_`I accept the terms in the license agreement`_** lalu tekan tombol `Next`
    > **PERHATIAN !** : Tutorial installasi ini hanya dapat dilakukan jika anda menyetujui perjanjian lisensi yang diberikan oleh developer `VMware Workstation`. **HANYA LAKUKAN TAHAP INI JIKA ANDA MENYETUJUI PERJANJIAN LISENSI TERSEBUT.** Jika anda tidak menyetujui perjanjian lisensi tersebut, silahkan melihat alternatif tutorial menggunakan `VirtualBox`.
8. Baca Dokument **_`VMware OVF Tool component for Linux - End User License Agreement`_** dengan seksama
    ![vmware3]
9. Klik **_`I accept the terms in the license agreement`_** lalu tekan tombol `Next`
    > **PERHATIAN !** : Tutorial installasi ini hanya dapat dilakukan jika anda menyetujui perjanjian lisensi yang diberikan oleh developer `VMware OVF Tool component for Linux`. **HANYA LAKUKAN TAHAP INI JIKA ANDA MENYETUJUI PERJANJIAN LISENSI TERSEBUT.**
10. Tekan `yes` atau `no` sesuai dengan keinginan anda untuk `VMware` dapat cek dan upgrade. Lalu tekan tombol `next`
    ![vmware4]
11. Jendela berikut menanyakan anda untuk bergabung dengan program mereka, silahkan baca lalu putuskan dengan menekan tombol `yes` atau `no`. Lalu tekan tombol `Next`
    ![vmware5]
12. masukkan username yang akan digunakan untuk koneksi ke `Workstation Server`. lalu tekan tombol `next`
    ![vmware6]
13. masukkan direktori untuk penyimpanan data _Virtual Machine_ anda. silahkan gunakan yang sudah di sediakan jika anda kurang yakin. lalu tekan tombol `next`
    ![vmware7]
14. masukkan `Port HTTPS` yang digunakan oleh `Workstation Server`. silahkan gunakan isi yang sudah di sediakan jika anda kurang yakin. lalu tekan tombol `next`
    ![vmware8]
15. _(Opsional)_ masukkan kode lisensi jika anda sudah membeli produk `VMware Workstation Pro 15.0`
    ![vmware9]
16. Pastikan konfigurasi anda telah benar, jika belum, anda dapat kembali dengan menekan tombol `Back`. jika sudah, silahkan lanjutkan installasi dengan menekan tombol `Install`
    ![vmware10]
17. Tunggu proses installasi sampai selesai
    ![vmware11]
18. Proses installasi telah selesai. klik tombol `Close`
    ![vmware12]

#### Installasi GNS3-VM Pada VMware
1. Download GNS3-VM 
    1. Dengan Browser
        1. Download melalui link berikut : [GNS3-VM Downloads](https://www.gns3.com/software/download-vm)
        2. Klik Tombol Download dibawah kolom **_`VMWARE WORKSTATION AND FUSION`_**
        ![ins-gns3-vm1]
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
    ![ins-gns3-vm2]
5. Arahkan ke File `GNS3*`**`.ova`** yang baru anda Unzip, lalu tekan Open
    ![ins-gns3-vm3]
6. _(Opsional)_ Ubah Nama VM dan Lokasi penyimpanannya.
    ![ins-gns3-vm4]
7. Tekan Import

#### Installasi GNS3-GUI
1. tambahkan Repository `GNS3` kedalam Sistem `APT`
    ```bash
    $ sudo add-apt-repository ppa:gns3/ppa
    ```
    ![ins-gns3-gui1]
2. Update _Listing_ Repository anda
    ```bash
    $ sudo apt-get update
    ```
3. Download dan install `GNS3-GUI`
    ```bash
    $ sudo apt-get install -f -y gns3-gui
    ```
    ![ins-gns3-gui2]
4. Tekan tombol no, jika anda di peringati oleh dialog berikut
    ![ins-gns3-gui3]
5. Tekan tombol yes, jika anda di peringati oleh dialog berikut
    ![ins-gns3-gui4]

#### Setup GNS3
1. Buka GNS3, Lalu anda akan temui jendela Setup Wizard
2. Pilih `Run the topologies in an isolated and standard VM` lalu tekan `Next`
    ![set-gns3-1]
3. Gunakan konfigurasi default untuk `Server path`, `Host binding`, dan `Port` lalu tekan Next
    ![set-gns3-2]
    ![set-gns3-3]
4. Pilih `VMware` pada _Virtualization Software_
5. _(Opsional)_ Ubah nama Virtual Machine, jumlah virtual CPU cores, besar RAM sesuai keinginan anda
6. Tekan tombol Next
    ![set-gns3-4]
    ![set-gns3-5]
7. jendela VMware Workstation secara otomatis akan terbuka. lalu di dalam GNS3-VM silahkan tekan tombol `OK`
    ![set-gns3-6]
    ![set-gns3-7]
    ![set-gns3-8]

#### Installasi Ubuntu Server dengan QemuVM
1. Buka GNS3
2. Di jendela Project, silahkan beri nama dan lokasi penyimpanan
    ![qemu1]
3. Tekan `EDIT` > `Preferences` > `QEMU` > `Qemu VMs`
    ![qemu2]
4. Tekan Tombol `New`, lalu pastikan pilih `Run this Qemu VM on the GNS3 VM`, Lalu tekan `Next`
    ![qemu3]
5. Beri Nama `Linux Server` Lalu tekan `Next`
    ![qemu4]
6. Gunakan pilihan bawaan untuk `Qemu binary`, lalu beri RAM minimal `512 MB`, lalu tekan `Next`
    ![qemu5]
7. Gunakan Console `Telnet` lalu tekan `Next`
    ![qemu6]
8. Pilih `New Image`, lalu tekan tombol `Browser` arahkan ke file `Ubuntu-Server` `*.vmdk`
    ![qemu8]
9. Tunggu hingga Upload selesai, lalu tekan `Finish`


### Vbox
> TODO : Create VirtualBox Version of this tutorial
---

[amdv1]: img/AMD_V/1.jpeg
[amdv2]: img/AMD_V/2.jpeg
[amdv3]: img/AMD_V/3.jpeg

[vmware1]: img/vm/vmware/1.png
[vmware2]: img/vm/vmware/2.png
[vmware3]: img/vm/vmware/3.png
[vmware4]: img/vm/vmware/4.png
[vmware5]: img/vm/vmware/5.png
[vmware6]: img/vm/vmware/6.png
[vmware7]: img/vm/vmware/7.png
[vmware8]: img/vm/vmware/8.png
[vmware9]: img/vm/vmware/9.png
[vmware10]: img/vm/vmware/10.png
[vmware11]: img/vm/vmware/11.png
[vmware12]: img/vm/vmware/12.png

[ins-gns3-vm1]: img/gns3/vmware/instalasi/1.png
[ins-gns3-vm2]: img/gns3/vmware/instalasi/2.png
[ins-gns3-vm3]: img/gns3/vmware/instalasi/3.png
[ins-gns3-vm4]: img/gns3/vmware/instalasi/4.png

[ins-gns3-gui1]: img/gns3/gui/1.png
[ins-gns3-gui2]: img/gns3/gui/2.png
[ins-gns3-gui3]: img/gns3/gui/3.png
[ins-gns3-gui4]: img/gns3/gui/4.png

[set-gns3-1]: img/gns3/vmware/setup/1.png
[set-gns3-2]: img/gns3/vmware/setup/2.png
[set-gns3-3]: img/gns3/vmware/setup/3.png
[set-gns3-4]: img/gns3/vmware/setup/4.png
[set-gns3-5]: img/gns3/vmware/setup/5.png
[set-gns3-6]: img/gns3/vmware/setup/6.png
[set-gns3-7]: img/gns3/vmware/setup/7.png
[set-gns3-8]: img/gns3/vmware/setup/8.png

[qemu1]: img/qemu/1.png
[qemu2]: img/qemu/2.png
[qemu3]: img/qemu/3.png
[qemu4]: img/qemu/4.png
[qemu5]: img/qemu/5.png
[qemu6]: img/qemu/6.png
[qemu7]: img/qemu/7.png
[qemu8]: img/qemu/8.png
