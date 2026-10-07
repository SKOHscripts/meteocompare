Build de **test** de MeteoCompare 1.17.0 (version de [Pat0chat/meteocompare](https://github.com/Pat0chat/meteocompare) du 7 octobre 2026), avec en plus le modèle **WeatherNext 2**, pas encore intégré par l'auteur. Branche unique : `release/all-fixes`.

> APK **debug** « MeteoCompare test » (paquet `com.meteocompare.app.debug`) : il s'installe à côté de l'application officielle, sans y toucher.

## Mise à jour

Il s'installe **par-dessus** le build de test 1.14.5.3, sans désinstallation : même clé de signature, version 37 → 41. Villes, réglages et historique de fiabilité sont conservés, y compris les réglages de notifications (mêmes clés dans la version de l'auteur).

## Contenu

| Élément | Origine | État chez l'auteur |
|---|---|---|
| Base 1.17.0 : radar, unités impériales, 10 jours, JMA GSM, NOAA AIGFS… | Pat0chat | publié |
| #4 « Erreur inconnue » hors du domaine du premier modèle | PR #7 | ✅ fusionné |
| #3 Notifications locales, dans la version retravaillée par l'auteur | PR #6 | ✅ fusionné |
| #8 Bandeau de fiabilité locale par onglet | PR #9 | ✅ fusionné |
| #2 **WeatherNext 2** (membre de contrôle de l'ensemble) et sa fiabilité locale | PR #5 | en attente (interface des ensembles prévue par l'auteur) |

WeatherNext 2 a été porté sur le nouveau code : son lot part vers l'Ensemble API en parallèle de celui de la Forecast API, qui garde le nouveau mécanisme de l'auteur (nouvel essai avec les seuls modèles globaux quand une ville est hors du domaine d'un modèle régional).

## À tester

- [ ] L'APK s'installe par-dessus la 1.14.5.3 ; villes et réglages sont toujours là.
- [ ] WeatherNext 2 (opt-in dans les modèles) s'affiche à côté des 21 autres modèles, y compris pour une ville hors d'Europe.
- [ ] Son compteur de fiabilité continue de progresser.

## Vérifications

- 1098 tests unitaires JVM, 0 échec (voir aussi le run GitHub Actions de ce commit).
- Signature de l'APK contrôlée par le workflow avant publication.
