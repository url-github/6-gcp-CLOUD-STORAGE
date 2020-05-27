# 6-4-Regulating Storage Access + Hands On

### Tworzę Bucketa.
```bash
gsutil mb gs://gcp-bucket-nr1
gsutil 
```

### Kopiuję pliki do Bucketa.
```bash
gsutil -m cp * gs://gcp-bucket-nr1
```

### Ustawiam politykę retencji na 60 sekund w wiadrze. Próbuje usunąć plik z wiadra.
```bash
gsutil retention set 100s gs://gcp-bucket-nr1
gsutil rm gs://gcp-bucket-nr1/plik1.jpg
```

### Następujące polecenie wykonuje zmianę (acl ch), przyznając użytkownikowi AllUsers (-u) uprawnienia do odczytu (R).

```bash
gsutil acl ch -u AllUsers:R gs://gcp-bucket-nr1/plik2.jpg
```
