Build de **test** de MeteoCompare 1.14.5 avec l'ensemble des corrections proposées à [Pat0chat/meteocompare](https://github.com/Pat0chat/meteocompare). Branche unique : `release/all-fixes`.

> APK **debug** (paquet `com.meteocompare.app.debug`) : il s'installe à côté de l'application officielle et remplace les builds de test précédents en conservant leurs données.

## Nouveau dans ce build

- **WeatherNext 2 entre dans la fiabilité locale.** Faute d'archive Previous Runs chez Open-Meteo, sa fiabilité se construit à partir des prévisions J+1 que l'application enregistre à chaque actualisation. Son compteur « N/14 » progresse au fil de l'usage, et le modèle rejoint les « meilleurs modèles locaux » une fois 14 jours comparés atteints.
  - Le bouton « Récupérer l'historique maintenant » reprend aussi jusqu'à 5 jours d'actualisations passées pour ce modèle.
  - Un jour sans actualisation de la ville la veille ne compte pas.
- Si WeatherNext 2 était le seul modèle actif, le suivi de biais ne passe plus en échec.

## Contenu cumulé

| Issue | Changement | État chez l'auteur |
|---|---|---|
| #4 | « Erreur inconnue » corrigée pour les villes hors du domaine du premier modèle | ✅ fusionné (PR #7) |
| #2 | Modèle **Google WeatherNext 2** (membre de contrôle de l'ensemble), avec sa fiabilité locale | PR #5 ouverte |
| #3 | **Notifications locales** : résumé quotidien, divergence, changement de prévision | PR #6 ouverte |
| #8 | Bandeau de **fiabilité locale** par onglet (avancement N/14) et bouton de récupération | branche prête, PR à ouvrir |

## À tester

- [ ] **WeatherNext 2** : il faut au moins une actualisation de la ville la veille, puis le cycle quotidien ou le bouton « Récupérer l'historique maintenant ». Son compteur passe alors de 0 à 1/14 ou plus. Les autres modèles ne régressent pas.
- [ ] **#8** : sur Pluie et Température, le bandeau reste affiché tant que WeatherNext 2 se complète, et affiche le nombre de modèles prêts.
- [ ] **#4, #3** : comme pour le build précédent.

## Vérifications

- Tests unitaires JVM, 0 échec (voir le run GitHub Actions de ce commit).
- Pas de test sur appareil avant cette release : c'est l'objet de ce build.
