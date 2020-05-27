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

### Do utworzenia podpisanego adresu URL wymagany jest moduł pyopenssl. Można go zainstalować za pomocą polecenia.

```bash
sudo pip install pyopenssl
```

### Do utworzenia podpisanego adresu URL wymagany jest moduł pyopenssl. Można go zainstalować za pomocą polecenia.

```bash
gcloud iam service-accounts list

bigdata_pw_2020@cloudshell:~ (affable-doodad-259911)$ gcloud iam service-accounts list
NAME                                    EMAIL                                               DISABLED
Compute Engine default service account  929521083857-compute@developer.gserviceaccount.com  False
```

### Tworzenie klucza prywatnego za pomocą wskazanego konta usługi.
```bash
gcloud iam service-accounts keys create key.json --iam-account 929521083857-compute@developer.gserviceaccount.com

ls
```
### Użycie utworzonego klucza prywatnego do utworzenia podpisanego adresu URL, który będzie trwał 10 minut (-d 10m) w pliku plik3.jgp

Coś z biblioteką pyopenssl nie hula. 

```bash
gsutil signurl -d 10m key.json gs://gcp-bucket-nr1/plik3.jgp

bigdata_pw_2020@cloudshell:~ (affable-doodad-259911)$ gsutil signurl -d 10m key.json gs://gcp-bucket-nr1/plik3.jgp
CommandException: The signurl command requires the pyopenssl library (try pip install pyopenssl or easy_install pyopenssl)
```

7. Using created private key to create signed URL, which will last for 10 minutes (-d 10m) on file img1.jgp.
```
gsutil signurl -d 10m key.json gs://gcp-bucket-nr1/img1.jgp
