# Build-Docker-Image
Catatan Cara Membangun Image Docker

Untuk membuild Dockerfile Anda ke dalam arsitektur ARM v7, Anda bisa menggunakan docker buildx yang mendukung arsitektur multi-platform. Berikut adalah perintah build dan run:

Langkah 1: Aktifkan docker buildx
Pastikan docker buildx sudah diaktifkan di mesin Anda. Anda bisa memeriksanya dengan:

```
docker buildx create --use
```

Langkah 2: Build Image untuk ARM v7
Gunakan perintah berikut untuk membuild image untuk arsitektur ARM v7:
```
docker buildx build --platform linux/arm/v7 -t mikhmonv3:latest --load .
```

Langkah 3: Menjalankan Container
Setelah image dibuild, jalankan container dengan perintah:

```
docker run -d --name mikhmonv3 -p 8080:8080 mikhmonv3:latest
```
