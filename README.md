<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Disarankan untuk menginstal nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) terlebih dahulu, lalu `direnv allow` setelah memasuki direktori ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) akan dijalankan secara otomatis setelah memasuki direktori).

Artinya adalah: terjemahan bahasa Mandarin ke bahasa Jepang, Korea, Inggris, Inggris terjemahan ke semua bahasa lainnya. Jika Anda hanya ingin mendukung bahasa Cina dan Inggris, Anda dapat menulis `zh: en` .

## kode ujung depan

* [kode ujung depan](https://github.com/xxai-art/web)
* [Paket bahasa untuk situs secara keseluruhan](https://github.com/xxai-art/web/tree/main/i18n)
* [Paket bahasa untuk modul login](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Dokumentasi Multibahasa Situs Web](https://github.com/xxai-doc)

Bahasa pemrograman front-end adalah [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , yang menambahkan beberapa fitur berdasarkan sintaks coffeescript, lihat [./coffee_plus.md](./coffee_plus.md) .

## Internasionalisasi situs web dan dokumen

Membangun pada 3 proyek berikut

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Akhirannya adalah `.mdt` , Anda dapat menggunakan sintaks yang mirip dengan `<+ ./coffee_plus/import.js>` untuk merujuk ke file eksternal, dan menghasilkan penurunan harga dengan akhiran `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Terjemahan penurunan harga tidak akan menerjemahkan kode dan tautan, dan akan meng-cache kalimat yang diterjemahkan. Jika terjemahan diubah tetapi teks asli tidak diubah, mengeksekusinya lagi tidak akan menimpa perubahan terjemahan.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  File bahasa untuk menerjemahkan situs web yang dihasilkan `yaml` .

### Petunjuk Otomasi Terjemahan Dokumen

Lihat repositori kode [xxai-art/doc](https://github.com/xxai-art/doc)

Disarankan untuk menginstal nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) terlebih dahulu, lalu `direnv allow` setelah memasuki direktori ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) akan dijalankan secara otomatis setelah memasuki direktori).

Untuk menghindari basis kode besar yang diterjemahkan ke dalam ratusan bahasa, saya membuat basis kode terpisah untuk setiap bahasa dan membuat organisasi untuk menyimpan basis kode

Mengatur variabel lingkungan `GITHUB_ACCESS_TOKEN` lalu menjalankan [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) akan secara otomatis membuat repositori kode.

Tentu saja, Anda juga bisa memasukkannya ke dalam basis kode.

Referensi skrip terjemahan [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Kode skrip ditafsirkan sebagai berikut:

[bunx](https://bun.sh/docs/cli/bunx) adalah pengganti npx, yang lebih cepat. Tentu saja, jika Anda belum menginstal bun, Anda dapat menggunakan `npx` sebagai gantinya.

`bunx mdt zh` merender `.mdt` di direktori zh sebagai `.md` , lihat 2 file tertaut di bawah

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` adalah kode inti untuk terjemahan (jika Anda hanya menginstal `nodejs` , tetapi `bun` dan `direnv` tidak diinstal, Anda juga dapat menjalankan `npx i18n` untuk menerjemahkan).

Ini akan menguraikan [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfigurasi `i18n.yml` dalam dokumen ini adalah sebagai berikut:

```
en:
zh: ja ko en
```

Artinya adalah: terjemahan bahasa Mandarin ke bahasa Jepang, Korea, Inggris, Inggris terjemahan ke semua bahasa lainnya. Jika Anda hanya ingin mendukung bahasa Cina dan Inggris, Anda dapat menulis `zh: en` .

Yang terakhir adalah [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , yang mengekstrak konten antara judul utama dan subjudul pertama dari `README.md` setiap bahasa untuk menghasilkan entri `README.md` . Kodenya sangat sederhana, Anda bisa melihatnya sendiri.

Google API digunakan untuk terjemahan gratis. Jika Anda tidak dapat mengakses Google, harap konfigurasikan dan atur proxy, seperti:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Skrip terjemahan akan menghasilkan cache terjemahan di direktori `.i18n` , harap periksa dengan `git status` dan tambahkan ke repositori kode untuk menghindari terjemahan berulang.

Jalankan `bunx i18n` setiap kali Anda memodifikasi terjemahan untuk memperbarui cache.

Jika teks asli dan terjemahannya diubah pada saat yang sama, cache akan bingung, jadi jika Anda ingin memodifikasi, Anda hanya dapat memodifikasi satu, lalu jalankan `bunx i18n` untuk memperbarui cache.
