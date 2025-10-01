# Jarkom-Modul-1-2025-K-43

| Nama | NRP |
|------------|--------------|
| Mey Rosalina     | 5027241004    |
| Mochamad Fadhil Saifullah   | 5027231068       |


<img width="1206" height="747" alt="image" src="https://github.com/user-attachments/assets/dd2e27b7-f3af-4233-aa4f-e15dc6336b39" />

1. Membuat entitas seperti yang di gambar dan membuat keempat ainur menjadi client dengan:

   - Set IP statis sesuai switch/gateway
  
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
lalu jalankan ```iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 10.85.0.0/16```



