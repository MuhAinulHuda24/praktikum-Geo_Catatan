###  Geo-Catatan — Aplikasi Peta, Lokasi, dan Reverse Geocoding (Flutter)

## Deskripsi 

Praktikum ini membahas penerapan layanan lokasi (GPS), peta digital, dan geocoding pada aplikasi Flutter melalui proyek “Geo-Catatan”. Aplikasi ini menampilkan peta OpenStreetMap, menandai lokasi melalui long press, serta menyimpan catatan dan alamat hasil reverse geocoding.

## Tujuan

Menampilkan peta menggunakan flutter_map

Mengambil lokasi GPS dengan geolocator

Mengubah koordinat menjadi alamat (reverse geocoding)

Menambahkan marker melalui gesture long pres

# Konfigurasi Proyek
# pubspec.yaml
dependencies:
  flutter:
    sdk: flutter
  geolocator: ^11.0.0
  geocoding: ^3.0.0
  flutter_map: ^6.1.0
  latlong2: ^0.9.0

AndroidManifest.xml
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.INTERNET" />

# Model Data
class CatatanModel {
  final LatLng position;
  final String note;
  final String address;

  CatatanModel({
    required this.position,
    required this.note,
    required this.address,
  });
}

# Implementasi Utama
## Menampilkan Peta

FlutterMap(
  options: MapOptions(
    initialCenter: latlong.LatLng(-6.2, 106.8),
    initialZoom: 13,
    onLongPress: _handleLongPress,
  ),
  children: [
    TileLayer(urlTemplate: 'https://tile.openstreetmap.org/{z}/{x}/{y}.png'),```

## Mendapatkan Lokasi Pengguna

Position position = await Geolocator.getCurrentPosition();
_mapController.move(
  latlong.LatLng(position.latitude, position.longitude), 15.0);

## Long Press → Tambah Marker + Reverse Geocoding

void _handleLongPress(_, latlong.LatLng point) async {
  List<Placemark> p = await placemarkFromCoordinates(point.latitude, point.longitude);
  setState(() {
    _savedNotes.add(CatatanModel(
      position: point,
      note: "Catatan Baru",
      address: p.first.street ?? "Alamat tidak dikenal",
    ));
  });
}


## Menampilkan Marker
MarkerLayer(
  markers: _savedNotes.map((n) => Marker(
    point: n.position,
    child: Icon(Icons.location_on, color: Colors.red),
  )).toList(),
)

# Hasil

Aplikasi berhasil:
![hasil flutter ](https://github.com/user-attachments/assets/9cab0a03-bc78-4329-a344-fda614e3f853)

Menampilkan peta


Mengambil lokasi perangkat

Menambahkan marker lewat long press

Mendapatkan alamat dengan reverse geocoding

# Kesimpulan

Praktikum ini memberikan pemahaman dasar integrasi layanan lokasi dan penggunaan peta digital dalam Flutter. Aplikasi “Geo-Catatan” berhasil menunjukkan cara kerja GPS, peta, marker, serta konversi koordinat menjadi alamat.
