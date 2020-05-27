# 6-gcp-CLOUD-STORAGE

#### Utworzenie Bucket za pomocą konsoli:
1. Storage
2. Create Bucket
3. Nazwa: gcp-bucket-nr1

### W konsoli CLI wgrywam pliki do folderu example.

```bash
cd example
ls
gsutil -m cp * gs://gcp-bucket-nr1
```
### Sprawdzam wielkość Bucketa.

```bash
gsutil du -s gs://gcp-bucket-nr1
```
### Zwraca metadane Bucketa.

```bash
gsutil ls -L -b gs://gcp-bucket-nr1
```

### Tworzę nowy Bucket.

```bash
gsutil mb -c standard -l us-east1 gs://gcp-bucket-nr2
```

### Kopiowanie całej zawartości z Bucket-nr1 do Bucket-nr2.

```bash
gsutil cp gs://gcp-bucket-nr1/** gs://gcp-bucket-nr2
```

### Wylistowanie wszystkich dostępnych plików Bucket-nr2.

```bash
gsutil ls -r gs://gcp-bucket-nr2/**
```

### Zmieniam domyślną klasę pamięci „gcp-bucket-nr2” na „nearline”. Opis [klas](https://cloud.google.com/storage/docs/storage-classes). 

```bash
gsutil defstorageclass set nearline gs://gcp-bucket-nr2
```
