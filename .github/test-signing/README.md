# Signature des builds de test du fork

`meteocompare-test.jks` signe les APK **debug** (paquet `com.meteocompare.app.debug`)
produits par les workflows du fork :

- `APK de test (manuel)` (`build-apk.yml`, sur `release/all-fixes`) : bouton « Run workflow »,
  n'importe quelle branche du fork, APK en artefact. La clé est injectée au build
  (`android.injected.signing.*`), sans modifier la branche compilée.
- `Release de test (fork)` (`release-apk.yml`, sur `release/all-fixes`) :
  pré-release publiée à chaque nouvelle version de test.

Sans cette clé commune, chaque runner CI génère sa propre clé de debug et Android
refuse d'installer un nouveau build de test par-dessus le précédent.

- Alias et mots de passe : `meteocompare-test` (publics par construction).
- Empreinte SHA-256 du certificat : voir `certificate-sha256.txt`. Les workflows
  refusent de livrer un APK signé avec une autre clé.
- Cette clé ne signe **jamais** l'application officielle (`com.meteocompare.app`) et
  ne figure dans aucune PR vers le dépôt de l'auteur.

Vérifier un APK téléchargé :

```bash
apksigner verify --print-certs meteocompare-*.apk | grep SHA-256
```
