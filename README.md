# Jarkom-Modul-1-2025-K-43

| Nama | NRP |
|------------|--------------|
| Mey Rosalina     | 5027241004    |
| Mochamad Fadhil Saifullah   | 5027231068       |


<img width="1206" height="747" alt="image" src="https://github.com/user-attachments/assets/dd2e27b7-f3af-4233-aa4f-e15dc6336b39" />

1. Membuat entitas seperti yang di gambar dan membuat keempat ainur menjadi client dengan:

   - Set IP statis sesuai switch/gateway

router/Eru
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
      address 10.85.1.1
      netmask 255.255.255.0

auto eth2
iface eth2 inet static
      address 10.85.2.1
      netmask 255.255.255.0
```

client

Melkor
```
auto eth0
iface eth0 inet static
    address 10.85.1.2
    netmask 255.255.255.0
    gateway 10.85.1.1
```
Manwe
```
auto eth0
iface eth0 inet static
    address 10.85.1.3
    netmask 255.255.255.0
    gateway 10.85.1.1
```

Varda
```
auto eth0
iface eth0 inet static
    address 10.85.2.2
    netmask 255.255.255.0
    gateway 10.85.2.1
```

Ulmo
```
auto eth0
iface eth0 inet static
    address 10.85.2.3
    netmask 255.255.255.0
    gateway 10.85.2.1
```

2. Buat agar Eru dapat tersambung ke internet.
   
configurasi
```
auto eth0
iface eth0 inet dhcp
```

menjalankan ```iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.85.0.0/16```
dan ```ping gogle.com -c 5```

<img width="650" height="416" alt="Screenshot 2025-09-30 193420" src="https://github.com/user-attachments/assets/4fc518df-84d0-448e-8d13-fd302e9243a5" />

3. Client dapat terhubung satu sama lain dengan mengatur IP-nya , lalu test dengan melakukan ```ping```
   
   contoh ```ping 10.85.2.2```  ->Dari Melkor ke Varda
   
<img width="672" height="376" alt="image" src="https://github.com/user-attachments/assets/ab881c6f-7c48-4dbc-a983-f77ac3937ee1" />

4. Eru ingin agar client tersambung ke internet
   1. jalankan ```iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.85.0.0/16``` di Eru
   2. ```echo "nameserver 192.168.122.1" > /etc/resolv.conf``` set namaserver di masing-masing client
   3. ```ping google.com -c 5``` Pengecekan koneksi internet dari masing-masing Client
  
<img width="648" height="506" alt="Screenshot 2025-09-30 193144" src="https://github.com/user-attachments/assets/411f5892-56eb-436e-a7f8-2853e599d3f1" />

5. Membuat konfigurasi tidak hilang saat semua node di restart dengan memasukkannya ke dalam file /root/.bashrc
<img width="894" height="542" alt="image" src="https://github.com/user-attachments/assets/219bd228-e225-42eb-8439-0da4081a7422" />







