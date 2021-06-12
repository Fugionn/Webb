---
title: SetPlayerColor
description: Set warna nametag player dan marker (radar blip).
tags: ["player"]
---

## Deskripsi

Set warna nametag player dan marker (radar blip).

| Nama     | Deskripsi                                |
| -------- | ---------------------------------------- |
| playerid | ID pemain yang warnanya akan diatur.     |
| warna    | Warna untuk diatur. Mendukung nilai alfa.|

## Returns

Fungsi ini tidak mengembalikan nilai tertentu.

## Contoh

```c
// Merah, menggunakan hexadecimal:
SetPlayerColor(playerid, 0xFF0000FF);

//Merah, menggunakan desimal notasi:
SetPlayerColor(playerid, 4278190335);
```

## Catatan

Fungsi ini akan mengubah warna pemain untuk semua pemain, bahkan jika warna pemain diubah dengan SetPlayerMarkerForPlayer untuk pemain lain. Jika digunaka OnPlayerConnect, pemutar yang terpengaruh tidak akan melihat warna di menu TAB.

## Fungsi Terkait

- [SetPlayerMarkerForPlayer](SetPlayerMarkerForPlayer): Set marker pemain.
- [GetPlayerColor](GetPlayerColor): Cek warna player.
- [ChangeVehicleColor](ChangeVehicleColor): Mengubah warna kendaraan.
