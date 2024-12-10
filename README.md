# **Tugas-KPPL-Week-13**

Kelompok 13:

1.  Adyuta Prajahita Murdianto - 5025221186

2.  Mirza Zaki Rafii - 5025221018

## **Problems**

1. Berdasarkan SRS dan Use Case Smart Home pada minggu lalu buatlah Analysis Modelnya.
2. Analysis Model, Use Case Diagram, Activity Diagram, dan Class Diagram.
3. Lengkapi Analysis Model yang dibuat dengan Behavioral Element.
4. Pengerjaan bisa secara kelompok, maksimal 2

## **Class Diagram**

![alt text](Resource/Class.png)

## **Use Case Diagram**

![alt text](Resource/useCaseDiagram.png)

## **Activity Diagram**

## **Analisis Class Diagram**

 ### **User** ###

 **Atribut**

- id

   Pengidentifikasi unik untuk setiap pengguna. Memastikan identifikasi yang jelas dari setiap individu dalam sistem.

- email
   Digunakan untuk komunikasi dan notifikasi, juga berfungsi sebagai pengidentifikasi saat pendaftaran dan masuk.

- username

   Menyediakan nama pengguna yang ramah untuk login dan tampilan.

- password

   Kredensial aman untuk autentikasi pengguna.

- device

   Array yang menyimpan semua perangkat yang dikelola oleh pengguna. Ini memungkinkan sistem mengelola beberapa perangkat per pengguna.

**Metode**

- register(email: String, password: String): void

  Memungkinkan pengguna baru membuat akun dengan menyediakan kredensial yang diperlukan.

- login(username: String, password: String): Boolean 

  Mengautentikasi pengguna dengan memverifikasi kredensial yang diberikan.

- manage_device(device: Device, addDevice: Boolean, removeDevice: Boolean): void

   Memfasilitasi penambahan atau penghapusan perangkat dari akun pengguna. Ini meningkatkan kontrol pengguna atas perangkat mereka.

- readLog(Log_id: Integer): Log

   Mengambil entri log tertentu, memungkinkan pengguna memantau aktivitas perangkat mereka di masa lalu.

- receiveNotification(Notification_id: Integer): Notification

   Memberikan pengguna notifikasi tentang status perangkat atau peristiwa penting dalam sistem.

### **Device** ###
**Atribut**

- name

   Pengidentifikasi perangkat yang mudah dibaca, memudahkan pengguna mengenali dan mengelola perangkat yang berbeda.

- status

   Menunjukkan apakah perangkat saat ini aktif atau tidak. Nilai boolean menyederhanakan pemeriksaan status.

- user_id

   Menghubungkan perangkat ke pengguna tertentu, memastikan perangkat terkait dengan pemiliknya dengan benar.

- timestamp

  Merekam waktu interaksi terakhir, berguna untuk otomasi dan tujuan log.

- id 

  Pengidentifikasi unik untuk setiap perangkat dalam sistem.

**Metode**

- isOn(): void

   Mengaktifkan perangkat, mengubah statusnya menjadi true.

- isOff(): void

   Menonaktifkan perangkat, mengubah statusnya menjadi false.

- automate(name: String, status: Boolean, timestamp: DateTime): void

   Mengatur aturan otomatisasi untuk perangkat, memungkinkan perangkat beroperasi secara otomatis berdasarkan kondisi yang ditentukan pengguna.

### **Log** ###
**Atribut**

- id

   Pengidentifikasi unik untuk setiap entri log, memastikan perbedaan yang jelas antara log yang berbeda.

- activity

   Mendeskripsikan tindakan yang dilakukan (misalnya, perangkat dinyalakan, dimatikan, dll.), memberikan konteks pada entri log.

- timestamp

   Menangkap waktu tepat saat aktivitas terjadi, penting untuk pelacakan dan analisis historis.

- device_name

   Mengidentifikasi perangkat mana yang terkait dengan entri log, menambah kejelasan pada log.

**Metode**

- createLog(device_name: String, activity: String, timestamp: DateTime): void


   Membuat entri log baru, mencatat aktivitas perangkat.

- showLog(): String

   Menampilkan entri log, memungkinkan pengguna meninjau aktivitas masa lalu perangkat mereka.

### **Kelas Notifikasi** ###
**Atribut**

- id

   Pengidentifikasi unik untuk setiap notifikasi, memastikan entri notifikasi yang jelas.

- message

   Konten notifikasi, menginformasikan pengguna tentang peristiwa atau status.

- timestamp

   Merekam waktu notifikasi dihasilkan, memberikan konteks dan relevansi.

**Metode**

- sendNotification(): void

   Mengirimkan notifikasi kepada pengguna, memastikan peringatan tepat waktu tentang peristiwa atau status penting.

## **Analisis Use Case Diagram**

### **Use Case: Registrasi**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna melakukan pendaftaran untuk membuat akun pada sistem.
- **Prekondisi**: Pengguna belum memiliki akun di sistem.
- **Postkondisi**: Akun pengguna berhasil dibuat dan tersimpan di sistem.
- **Alur**:
  1. Pengguna membuka halaman registrasi.
  2. Pengguna memasukkan informasi seperti nama, email, dan kata sandi.
  3. Sistem memvalidasi data yang dimasukkan.
  4. Sistem menyimpan data pengguna ke dalam basis data.
  5. Sistem menampilkan pesan bahwa pendaftaran berhasil.

### **Use Case: Tambah Perangkat**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna menambahkan perangkat baru ke sistem Smart Home.
- **Prekondisi**: Pengguna telah masuk ke sistem dan perangkat yang akan ditambahkan tersedia.
- **Postkondisi**: Perangkat berhasil ditambahkan ke daftar perangkat pengguna.
- **Alur**:
  1. Pengguna membuka halaman tambah perangkat.
  2. Pengguna memasukkan informasi perangkat, seperti nama dan ID perangkat.
  3. Sistem memvalidasi informasi perangkat.
  4. Sistem menambahkan perangkat ke akun pengguna.
  5. Sistem menampilkan pesan bahwa perangkat berhasil ditambahkan.

### **Use Case: Hapus Perangkat**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna menghapus perangkat dari sistem Smart Home.
- **Prekondisi**: Pengguna telah masuk ke sistem dan memiliki perangkat yang terhubung.
- **Postkondisi**: Perangkat berhasil dihapus dari daftar perangkat pengguna.
- **Alur**:
  1. Pengguna membuka halaman daftar perangkat.
  2. Pengguna memilih perangkat yang ingin dihapus.
  3. Pengguna mengonfirmasi penghapusan perangkat.
  4. Sistem memverifikasi perangkat yang dipilih.
  5. Sistem menghapus perangkat dari daftar pengguna.
  6. Sistem menampilkan pesan bahwa perangkat berhasil dihapus.

### **Use Case: Kontrol Perangkat**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna mengontrol perangkat yang sudah terhubung dengan sistem.
- **Prekondisi**: Pengguna telah masuk ke sistem dan memiliki perangkat yang terhubung.
- **Postkondisi**: Perangkat berhasil dikontrol sesuai perintah pengguna.
- **Alur**:
  1. Pengguna membuka halaman kontrol perangkat.
  2. Pengguna memilih perangkat yang ingin dikontrol.
  3. Pengguna memberikan perintah (misalnya, hidupkan atau matikan).
  4. Sistem mengirim perintah ke perangkat yang dipilih.
  5. Sistem menampilkan status perangkat setelah perintah dieksekusi.

### **Use Case: Automasi**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna membuat aturan atau jadwal untuk mengotomatiskan tindakan perangkat.
- **Prekondisi**: Pengguna telah masuk ke sistem dan memiliki perangkat yang terhubung.
- **Postkondisi**: Aturan atau jadwal automasi berhasil dibuat dan disimpan di sistem.
- **Alur**:
  1. Pengguna membuka halaman pengaturan automasi.
  2. Pengguna memilih perangkat yang akan diotomasi.
  3. Pengguna menentukan aturan atau jadwal automasi (misalnya, hidupkan perangkat pada waktu tertentu).
  4. Sistem memvalidasi aturan atau jadwal yang dibuat.
  5. Sistem menyimpan pengaturan automasi.
  6. Sistem menampilkan pesan bahwa automasi berhasil dibuat.


### **Use Case: Notifikasi**

- **Aktor**: Pengguna.
- **Deskripsi**: Sistem mengirimkan notifikasi kepada pengguna terkait status perangkat.
- **Prekondisi**: Sistem mendeteksi suatu kondisi yang memerlukan notifikasi.
- **Postkondisi**: Notifikasi berhasil dikirimkan dan diterima oleh pengguna.
- **Alur**:
  1. Sistem memantau perangkat pengguna.
  2. Sistem mendeteksi perubahan status perangkat atau kondisi tertentu.
  3. Sistem memproses informasi dan membuat notifikasi.
  4. Sistem mengirimkan notifikasi ke perangkat pengguna (aplikasi atau email).
  5. Pengguna menerima notifikasi.

### **Use Case: Pemantauan Perangkat**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna memantau status perangkat yang terhubung dengan sistem Smart Home.
- **Prekondisi**: Pengguna telah masuk ke sistem dan memiliki perangkat yang terhubung.
- **Postkondisi**: Pengguna berhasil melihat status perangkat secara real-time.
- **Alur**:
  1. Pengguna membuka halaman pemantauan perangkat.
  2. Sistem menampilkan daftar perangkat yang terhubung.
  3. Pengguna memilih perangkat yang ingin dipantau.
  4. Sistem menampilkan status perangkat secara real-time (misalnya, suhu, status aktif/tidak aktif).
  6. Pengguna melihat informasi status perangkat.

### **Use Case: Log Aktivitas**

- **Aktor**: Pengguna.
- **Deskripsi**: Pengguna dapat melihat log aktivitas untuk memantau tindakan yang dilakukan pada perangkat.
- **Prekondisi**: Pengguna telah masuk ke sistem dan log aktivitas telah disimpan.
- **Postkondisi**: Pengguna berhasil melihat log aktivitas.
- **Alur**:
  1. Pengguna membuka halaman log aktivitas.
  2. Sistem menampilkan daftar log aktivitas yang relevan untuk pengguna.
  3. Pengguna melihat detail aktivitas tertentu jika diperlukan.

## **Analisis Activity Diagram**
