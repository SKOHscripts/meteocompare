# Signature des builds de test du fork

`meteocompare-test.jks` signe l'APK **debug** (paquet `com.meteocompare.app.debug`)
produit par la branche `release/all-fixes`. Sans ce fichier, chaque runner CI
génère sa propre clé de debug et Android refuse d'installer un nouveau build de
test par-dessus le précédent.

- Alias et mots de passe : `meteocompare-test` (publics par construction).
- Empreinte SHA-256 du certificat : voir `certificate-sha256.txt`. Le workflow
  `release-apk.yml` refuse de publier un APK signé avec une autre clé.
- Cette clé ne signe **jamais** l'application officielle (`com.meteocompare.app`) :
  elle n'a de valeur que pour les builds de test, et ne doit pas quitter cette
  branche (aucune PR vers le dépôt de l'auteur ne la contient).

Vérifier un APK téléchargé :

```bash
apksigner verify --print-certs meteocompare-skoh-v*.apk | grep SHA-256
```
