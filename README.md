#  Geo-Catatan — Aplikasi Peta, Lokasi, dan Reverse Geocoding (Flutter)

**Geo-Catatan** adalah aplikasi Flutter sederhana yang memanfaatkan geolokasi, peta digital, dan reverse geocoding.  
Pengguna dapat menandai lokasi pada peta dengan long press, menyimpan catatan, serta melihat alamat otomatis dari titik yang dipilih.

Aplikasi ini dibuat sebagai bagian dari praktikum *Pemrograman Mobile* dengan topik **Geolokasi, Peta Digital, dan Geocoding**.

---

## Fitur Utama

- Menampilkan peta (OpenStreetMap via `flutter_map`)
- Menambahkan marker dengan long press
- Menyimpan catatan sederhana untuk setiap lokasi
- Menemukan lokasi pengguna dengan GPS
- Alamat otomatis dari koordinat (Reverse Geocoding)

---

## Dependensi

Tambahkan ke `pubspec.yaml`:

```yaml
dependencies:
  flutter:
    sdk: flutter

  geolocator: ^11.0.0
  geocoding: ^3.0.0
  flutter_map: ^6.1.0
  latlong2: ^0.9.0
