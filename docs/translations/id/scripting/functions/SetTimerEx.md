---
title: SetTimerEx
description: Mengatur timer untuk memanggil fungsi setelah interval yang ditentukan.
tags: ["timer"]
---

## Deskripsi

Mengatur timer untuk memanggil fungsi setelah interval yang ditentukan. Varian ini ('Ex') dapat meneruskan parameter (seperti ID pemain) ke fungsi.

| Name           | Deskripsi                                                                                                                               |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| funcname[]     | Nama fungsi publik yang akan dipanggil saat waktu timer habis.                                                                              |
| interval       | Interval dalam milisecond (1 detik = 1000 MS).                                                                                             |
| repeating      | Boolean (true/false (atau 1/0)) yang menyatakan apakah timer harus dipanggil berulang kali (hanya dapat dihentikan dengan "KillTimer") atau hanya sekali. |
| format[]       | Format khusus yang menunjukkan jenis nilai yang akan dilewatkan oleh timer.                                                                         |
| {Float,\_}:... | Jumlah argumen yang tidak terbatas untuk diteruskan (harus mengikuti format yang ditentukan dalam parameter sebelumnya).                                               |

## Returns

ID timer yang dimulai. ID Timer dimulai dari 1 dan tidak pernah digunakan kembali. Tidak ada pemeriksaan internal untuk memverifikasi bahwa parameter yang diteruskan valid (misalnya durasi bukan nilai minus). Plugin 'fixes2' Y_Less mengimplementasikan pemeriksaan ini dan juga sangat meningkatkan akurasi pengatur waktu, dan juga menambahkan dukungan untuk passing array/string.

## Contoh

```c
SetTimerEx("EndAntiSpawnKill", 5000, false, "i", playerid);
// EndAntiSpawnKill - Fungsi yang akan di panggil
// 5000 - 5000 MS (5 detik). Ini adalah intervalnya. Timer akan dipanggil setelah 5 detik.
// false - Tidak mengulangi. Hanya akan dipanggil sekali.
// "i" - I singkatan dari integer (bilangan bulat). Kami meneruskan bilangan bulat (ID pemain) ke fungsi.
// playerid - Nilai. Ini adalah bilangan bulat yang ditentukan dalam parameter sebelumnya.
// fungsi callback (OnPlayerSpawn) - kita akan memulai sebuah timer disini
public OnPlayerSpawn(playerid)
{
    // Anti-Spawnkill (5 seconds)

    // Set darah sangat tinggi mereka akan mati
    SetPlayerHealth(playerid, 999999);

    // Memberitahukan pemain
    SendClientMessage(playerid, -1, "Anda terlindungi dari spawn-killing selama 5 detik.");

    // Memulai sebuah timer dalam waktu 5 detik untuk mematikan anti-spawnkill
    SetTimerEx("EndAntiSpawnKill", 5000, false, "i", playerid);
}

// Meneruskan (membuat publik) fungsinya sehingga server dapat 'melihatnya'
forward EndAntiSpawnKill(playerid);
// Fungsi pengatur waktu - kode yang akan dieksekusi ketika pengatur waktu dipanggil ada di sini
public EndAntiSpawnKill(playerid)
{
    // 5 detik telah berlalu, jadi mari kita kembalikan HP mereka ke 100
    SetPlayerHealth(playerid, 100);

    // Memberi tahu pemain
    SendClientMessage(playerid, -1, "Anda tidak lagi terlindungi dari spawn-killing.");
    return 1;
}
```

## Catatan


Variabel ID Timer harus diinisialisasi ke -1 jika memungkinkan untuk meminimalkan kemungkinan tidak sengaja membunuh ID timer 0 karena kesalahan (atau gunakan ID timer 0 di awal OnGameModeInit). Interval pengatur waktu tidak akurat (kurang lebih 25%). Ada perbaikan yang tersedia di sini dan di sini. Fungsi yang akan dipanggil harus publik. Artinya harus diteruskan.

## Fungsi Terkait

- [SetTimer](SetTimer): Set timer.
- [KillTimer](KillTimer): Mematikan timer.
- [CallLocalFunction](CallLocalFunction): Panggil fungsi dalam skript.
- [CallRemoteFunction](CallRemoteFunction): Panggil fungsi dalam skrip apa pun yang dimuat.
