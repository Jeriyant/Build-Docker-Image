# Build-Docker-Image
Catatan Cara Membangun Image Docker

Untuk membuild Dockerfile Anda ke dalam arsitektur ARM v7, Anda bisa menggunakan docker buildx yang mendukung arsitektur multi-platform. Berikut adalah perintah build dan run:

## Langkah 1: Aktifkan docker buildx
Pastikan docker buildx sudah diaktifkan di mesin Anda. Anda bisa memeriksanya dengan:

```
docker buildx create --use
```

## Langkah 2: Build Image untuk ARM v7
Gunakan perintah berikut untuk membuild image untuk arsitektur ARM v7:
```
docker buildx build --platform linux/arm/v7 -t mikhmonv3:latest --load .
```

## Langkah 3: Menjalankan Container
Setelah image dibuild, jalankan container dengan perintah:

```
docker run -d --name mikhmonv3 -p 8080:8080 mikhmonv3:latest
```

# Upload Image Docker Ke Repository
<details>
  <summary>Lihat Disini</summary>

# Cara Upload Docker Image ke Docker Hub

Untuk meng-upload Docker image yang telah Anda build ke repository di Docker Hub, ikuti langkah-langkah berikut. Asumsinya Anda sudah memiliki akun Docker Hub dan sudah membuat repository `jeriyant/mikhmonv3`.

## Langkah-Langkah Upload Docker Image

1. **Login ke Docker Hub**  
   Pertama, Anda perlu login ke Docker Hub menggunakan command berikut:
   
   ```bash
   docker login
   ```
   
   Anda akan diminta memasukkan username dan password Docker Hub.

2. **Tag Docker Image**  
   Setelah login, tag Docker image yang sudah Anda buat (`mikhmonv3`) ke dalam format yang sesuai untuk Docker Hub. Formatnya adalah: `username/repository:tag`. Untuk contoh ini, gunakan repository `jeriyant/mikhmonv3`:
   
   ```bash
   docker tag mikhmonv3 jeriyant/mikhmonv3:latest
   ```
   
   Di sini `latest` adalah tag versi image Anda. Anda bisa menggantinya dengan tag lain, misalnya `v1.0` atau `stable`.

3. **Push Docker Image ke Docker Hub**  
   Setelah menambahkan tag, push Docker image ke Docker Hub menggunakan command berikut:
   
   ```bash
   docker push jeriyant/mikhmonv3:latest
   ```
   
   Ini akan meng-upload image yang telah Anda tag (`jeriyant/mikhmonv3:latest`) ke Docker Hub. Pastikan untuk menunggu hingga proses upload selesai.

4. **Verifikasi Upload**  
   Setelah proses push selesai, Anda dapat memverifikasi apakah image tersebut sudah berhasil di-upload dengan cara login ke Docker Hub di [link berikut](https://hub.docker.com/r/jeriyant/mikhmonv3) dan melihat daftar tag yang tersedia.

## Ringkasan

Berikut adalah command lengkapnya:

```bash
docker login
docker tag mikhmonv3 jeriyant/mikhmonv3:latest
docker push jeriyant/mikhmonv3:latest
```

### Pastikan Hal-Hal Berikut:
- Anda menggunakan nama repository yang benar (`jeriyant/mikhmonv3`).
- Anda telah melakukan login ke Docker Hub sebelum melakukan push.

Jika semuanya sudah benar, maka Docker image `mikhmonv3` yang Anda build akan berhasil ter-upload ke Docker Hub repository `jeriyant/mikhmonv3`.

</details>
