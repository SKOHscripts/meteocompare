Build de **test** de MeteoCompare 1.14.5, avec l'ensemble des corrections proposées à [Pat0chat/meteocompare](https://github.com/Pat0chat/meteocompare). Branche : `release/all-fixes`.

> APK **debug** (paquet `com.meteocompare.app.debug`) : il s'installe **à côté** de l'application officielle, sans la remplacer ni toucher à ses données. Les villes favorites sont donc à rajouter.

## Contenu

| Issue | Changement | État chez l'auteur |
|---|---|---|
| #4 | « Erreur inconnue » corrigée pour les villes hors du domaine du premier modèle (Asie, Afrique…) | ✅ fusionné (PR #7) |
| #2 | Nouveau modèle **Google WeatherNext 2** (membre de contrôle de l'ensemble, opt-in dans Réglages → Modèles) | PR #5 ouverte |
| #3 | **Notifications locales** : résumé quotidien, divergence des modèles, changement de prévision (Réglages → Notifications) | PR #6 ouverte |
| #8 | Bandeau de **fiabilité locale** par onglet, avec l'avancement « N/14 » et un bouton « Récupérer l'historique maintenant » | branche prête, PR à ouvrir |

## À tester

- [ ] **#4** : ajouter Tokyo ou Nairobi. Les prévisions s'affichent (plus d'« Erreur inconnue »).
- [ ] **#2** : activer WeatherNext 2 dans les modèles. Il apparaît dans les tableaux ; sa pastille de fiabilité affiche « — » (pas d'archive disponible pour ce modèle).
- [ ] **#3** : activer le résumé quotidien pour une ville, régler l'heure 2 à 3 minutes plus tard et accepter la permission. La notification arrive (Android peut la décaler de quelques minutes). Divergence et changement sont vérifiés toutes les 3 h.
- [ ] **#8** : ouvrir une ville, onglet Pluie ou Température. Le bandeau explique J+1 et le compteur N/14, et reste affiché tant que des modèles se complètent. Le bouton « Récupérer l'historique maintenant » fait progresser les compteurs après quelques minutes (réseau requis).

## Vérifications

- 912 tests unitaires JVM, 0 échec ; chaque commit des branches de PR passe aussi la suite.
- Pas de test sur appareil ni émulateur avant cette release : c'est l'objet de ce build.
