Build de **test** de MeteoCompare 1.14.5 avec l'ensemble des corrections proposées à [Pat0chat/meteocompare](https://github.com/Pat0chat/meteocompare). Branche unique : `release/all-fixes`.

> APK **debug** (paquet `com.meteocompare.app.debug`) : il s'installe à côté de l'application officielle, sans la remplacer ni toucher à ses données.

## ⚠️ Une seule fois : désinstaller le build de test actuel

Les builds précédents (1.14.5.1, 1.14.5.2) étaient signés avec une clé de debug différente à chaque compilation. Android refuse donc d'installer celui-ci par-dessus (« Application non installée » ou « conflit de paquet »), et les notes de la 1.14.5.2 étaient fausses sur ce point.

1. Désinstaller l'ancien build de test. Il porte aussi le nom « MeteoCompare » : c'est celui dont les Réglages contiennent la section **Notifications**. L'application officielle ne bouge pas.
2. Installer cet APK, puis rajouter les villes du build de test.

Le build de test s'appelle désormais **MeteoCompare test** sur l'écran d'accueil, pour ne plus le confondre avec l'application officielle.

## Ensuite : mises à jour sans désinstallation

À partir de ce build, tous les APK de test sont signés avec la même clé, dédiée aux builds de test du fork. Chaque nouvelle release s'installe **par-dessus** la précédente et conserve villes, réglages et historique de fiabilité. Le workflow refuse de publier un APK signé avec une autre clé.

- Version affichée dans Réglages → À propos : `1.14.5-test.<n° du build>`.
- Empreinte SHA-256 du certificat : `39:79:E3:BB:3F:62:90:B1:C1:25:5B:49:09:67:9B:E8:07:41:03:E3:32:66:B6:F2:5A:5D:A0:79:AC:C6:3B:49`.

## Contenu cumulé (inchangé depuis 1.14.5.2)

| Issue | Changement | État chez l'auteur |
|---|---|---|
| #4 | « Erreur inconnue » corrigée pour les villes hors du domaine du premier modèle | ✅ fusionné (PR #7) |
| #2 | Modèle **Google WeatherNext 2** (membre de contrôle de l'ensemble), avec sa fiabilité locale | PR #5 ouverte |
| #3 | **Notifications locales** : résumé quotidien, divergence, changement de prévision | PR #6 ouverte |
| #8 | Bandeau de **fiabilité locale** par onglet (avancement N/14) et bouton de récupération | branche prête, PR à ouvrir |

## À tester

- [ ] Après désinstallation, cet APK s'installe sous le nom « MeteoCompare test » et l'application officielle reste intacte.
- [ ] Au prochain build de test, l'APK s'installe par-dessus celui-ci sans désinstallation, avec les villes conservées.
- [ ] Les points de la 1.14.5.2 : WeatherNext 2 dans la fiabilité locale, bandeau #8, #4 et #3.

## Vérifications

- Tests unitaires JVM, 0 échec (voir le run GitHub Actions de ce commit).
- Signature de l'APK contrôlée par le workflow avant publication.
