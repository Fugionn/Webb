---
title: GetPlayerName
description: Mendapatkan nama pemain.
tags: ["player"]
---

## Deskripsi

Mendapatkan nama pemain

| Nama     | Deskripsi                                                                                                                                     |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| playerid | Pemain yang terkoneksi.                                                                                                        |
| nama[]   | Array tempat menyimpan nama, dilanjutkan dengan referensi.                                                                                     |
| len      | Panjang string yang harus disimpan. Direkomendasikan untuk menjadi MAX_PLAYER_NAME + 1. +1 diperlukan untuk memperhitungkan terminator nol. |

## Returns

Nama pemain disimpan dalam array yang ditentukan.

## Examples

```c
public OnPlayerConnect(playerid)
{
    // Mendapatkan nama pemain yang terhubung dan tampilkan pesan bergabung ke pemain lain
    new nama[MAX_PLAYER_NAME + 1];
    GetPlayerName(playerid, nama, sizeof(nama));

    new string[MAX_PLAYER_NAME + 23 + 1];
    format(string, sizeof(string), "%s Telah bergabung kedalam server.", nama);
    SendClientMessageToAll(0xC4C4C4FF, string);
    return 1;
}
```

## Catatan

Nama pemain bisa sampai 24 karakter (0.3d R2) dengan menggunakan SetPlayerName. Ini didefinisikan di a_samp.inc sebagai MAX_PLAYER_NAME. Namun, klient hanya dapat bergabung dengan nama panggilan antara 3 dan 20 karakter, jika tidak, koneksi akan ditolak dan pemain harus keluar untuk memilih nama yang valid.

## Fungsi Terkait

- [SetPlayerName](SetPlayerName): Fungsi untuk set nama player.
- [GetPlayerIp](GetPlayerIp): Mendapatkan IP Pemain
- [GetPlayerPing](GetPlayerPing): Mendapatkan Ping Pemain
- [GetPlayerScore](GetPlayerScore): Mendapatkan score pemain.
- [GetPlayerVersion](GetPlayerVersion): Mendapatkan versi client pemain.
