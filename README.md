<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Bagian dari kode situs web adalah sumber terbuka, selamat datang untuk membantu mengoptimalkan terjemahan.

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
