---
title: SetTimer
deskripsi: Menyetel 'timer' untuk memanggil fungsi setelah beberapa waktu.
tags: ["timer"]
---

## Deskripsi

Menyetel 'pengatur waktu' untuk memanggil fungsi setelah beberapa waktu. Bisa di atur untuk mengulang.

| Nama       | Deskripisi                                                                                                                     |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| funcname[] | Nama fungsi yang akan dipanggil sebagai string. Ini harus menjadi fungsi publik (diteruskan). String nol di sini akan membuat server crash. |
| interval   |Interval dalam milisecond                                                                                                       |
| repeating  | Boolean (true/false) tentang apakah timer harus diulang atau tidak.                                                                 |

## Returns

ID timer yang dimulai. ID timer mulai dari 1.

## Contoh

```c
forward pesan();

public OnGameModeInit()
{
    print(" timer...");
    SetTimer("pesan", 1000, false); // Atur timer 1000 milisecond (1 detik)
}

public message()
{
    print("1 detik.");
}
```

## Catatan



Interval pengatur waktu tidak akurat (kurang lebih 25%). Ada perbaikan yang tersedia di sini dan di sini. ID Timer tidak pernah digunakan dua kali. Anda dapat menggunakan KillTimer() pada ID timer dan tidak masalah apakah itu berjalan atau tidak. Fungsi yang seharusnya dipanggil, harus publik, artinya harus diteruskan. Penggunaan banyak timer akan mengakibatkan peningkatan penggunaan memori/cpu.

## Fungsi Terkait

- [SetTimerEx](SetTimerEx): Mengatur sebuah timer menggunakan parameters.
- [KillTimer](KillTimer): Menghentikan a timer.