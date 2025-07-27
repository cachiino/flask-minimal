
# flask-minimal
Sebelum memulai, temen-temen harus tau dulu nih apasih flask itu?? terus apasih kegunaannya?
Flask adalah framework web berbasis Python yang digunakan untuk membangun aplikasi web. Flask bersifat ringan (minimalis) dan fleksibel, sehingga sangat cocok untuk pemula maupun pengembang profesional yang ingin membuat aplikasi web dengan cepat dan efisien.
Kali ini kita bakal buat flask sesimpel mungkin, namun juga punya beberapa fitur yang berguna!! 
---

## ✨ Fitur Utama

* ✅ Aplikasi Flask hanya dalam satu file (`app.py`) — praktis dan cepat!
* 🎨 Template HTML sederhana dengan styling dan JavaScript minimal.
* 🚀 Setup super gampang, cocok buat pemula atau prototipe cepat.
* 🔧 Mudah diubah sesuai kebutuhan aplikasi web kamu.
* ✔ Tidak akan hilang walaupun mesin direboot

---

## 🔧 Persiapan Awal
### 1. Fork github ini ke repository kalian
<pre>a. buka halaman github yang akan di fork
b. pilih fork di bagian kanan atas 
c. buka halaman github yang sudah di fork ke akun kalian
  </pre>
### 2. Buat instance di AWS 
<pre>a. Beri nama instance pada bagian "Name"
b. Pilih OS Ubuntu
c. Instance type : t2.nano
d. Key pair : vockey
e. Security group :
   Allow SSH (port 22)
f. Jika sudah klik "Launch Instance"
g. Jika instance tidak muncul, refresh halaman instance
</pre>
### 3. Tambahkan port 5000
<pre>a. klik ID Instance
b. scroll ke bawah lalu pilih security
c. klik bagian "Security Groups" 
d. pilih "Edit inbound rules"
e. "Add rule" 
   Type : Custom TCP 
   Port range : 5000
   Source : Anywhere-IPv4
f. jika sudah sesuai klik "Save rules"
</pre>
### 4. Masuk ke terminal ec2
a. klik ID Instance
b. klik "connect" di bagian kanan atas
c. scroll sedikit ke bawah kemudian pilih "Connect"

Nah persiapan awal sudah selesai teman-teman semua~. 
Untuk selanjutnya ayo kita mulai menuliskan script nya🎉🎉

## Cara Instalasi
### 1. Pastikan Python sudah terinstall dengan cara :

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
```

### 2. Clone repositorimu:

   ```bash
   git clone https://github.com/yourusername/flask-minimal.git
   cd flask-minimal
   ```

### 3. Buat virtual environment:

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

### 4. Install semua kebutuhan proyek:

   ```bash
   pip install -r requirements.txt
   ```

### 5. Jalankan aplikasinya:

   ```bash
   python app.py
   ```

Jika sudah sampai sini web temen-temen udah bisa diakses loh! pake public ip dan tambahkan ":5000" di belakangnya. Namun sayangnya kalo cuma sampe sini, web kita gabisa diakes kalo terminalnya di close ataupun mesinnya direboot :(.
Maka dari itu aku udah siapin nih caranya supaya web kita tetap bisa diakses walaupun terminalnya kita tutup atau mesinnya kita reboot! 

### 6. Tekan CTRL+C untuk keluar dari server flask

### 7. Buat File Service untuk Systemd
```bash
sudo nano /etc/systemd/system/flaskapp.service
```
### 8. Isi dengan :
```bash
[Unit]
Description=Flask Minimal App
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python app.py
Restart=always

[Install]
WantedBy=multi-user.target
```

### 9. Reload dan Jalankan Servicenya
```bash
sudo systemctl daemon-reexec
sudo systemctl daemon-reload
sudo systemctl enable flaskapp
sudo systemctl start flaskapp
```

Sekarang buka browser dan kunjungi Public ip kamu dan tambahkan ":5000" di belakangnya!
contoh :
```bash
54.162.37.27:5000
```
---

## 💡 Cara Menggunakan
Kamu bisa mulai modifikasi bagian-bagian berikut:

* 🖼 HTML → `templates/index.html`
* 🎨 CSS → `static/style.css`
* ⚙️ JavaScript → `static/script.js`
* 🔄 Rute & logika Flask → `app.py`
---
Nah sekarang kamu sudah tau dan sudah bisa flask!
Semoga membantu yaaa💞💞
