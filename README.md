# Computer Vision Labs : détection, OCR et visual retrieval

Trois notebooks pédagogiques en français pour Abdessamad Abouchraa, INPT. Le projet montre comment utiliser des modèles préentraînés sur de petits tests, sans entraînement lourd. La détection remplace le tracking de la première série ; génération et captioning sont hors périmètre.

## Contenu

| Notebook | Modèle / bibliothèque | Expérience |
|---|---|---|
| [01_object_detection.ipynb](01_object_detection.ipynb) | YOLO11n / Ultralytics | Une photo de bus, boîtes/classes/confiances, effet du seuil |
| [02_ocr.ipynb](02_ocr.ipynb) | Tesseract / pytesseract | Document contrôlé, transcription, CER/WER et flou ; option photo personnelle |
| [03_visual_retrieval.ipynb](03_visual_retrieval.ipynb) | CLIP ViT-B/32 / Transformers | Trois photos réelles, texte-image et image-image, cosinus et top-k |

Chaque notebook contient définition, installation, données, fonctionnement, visualisation, limites, quatre questions et bibliographie. Aucun média n’est créé par un générateur d’images. Le document OCR par défaut est un test typographique, clairement identifié.

## Démarrage local

Python 3.10–3.12 recommandé. Créer un environnement :

```bash
python -m venv .venv
# Linux/macOS
source .venv/bin/activate
# Windows PowerShell : .venv\Scripts\Activate.ps1
pip install -r requirements.txt
jupyter lab
```

Pour économiser les ressources, on peut installer uniquement les bibliothèques du sujet via la première cellule `%pip`. Sous Linux installer aussi `sudo apt-get install tesseract-ocr fonts-dejavu-core`. Sous Windows installer le moteur Tesseract et ajouter son dossier au PATH. La bibliothèque Python seule ne suffit pas. Les données anglaises `eng` sont utilisées pour le test ; installer `fra` pour le français.

## Google Colab

Importer un notebook ou ouvrir depuis GitHub dans Colab, puis exécuter de haut en bas. Le notebook OCR installe Tesseract automatiquement dans Colab si absent. CPU par défaut possible, GPU facultatif pour YOLO/CLIP. Connexion Internet nécessaire pour les photos et les poids au premier lancement. Aucun token ou clé API requis pour ces modèles publics.

## Travail effectué et statut de validation

Code des trois expériences préparé et contrôlé syntaxiquement. Les cellules Python standard sont analysées, les notebooks sont vérifiés comme JSON et les installations `%pip` restent des commandes IPython. **Les inférences YOLO, Tesseract via pytesseract et CLIP de cette nouvelle série n’ont pas été exécutées dans l’environnement de préparation.** Les poids et dépendances n’y sont pas téléchargeables. Les sorties sont donc vides : aucun score, résultat ou temps d’inférence n’est inventé. Cette série n’est pas annoncée comme préexécutée. Les plages de versions expriment les dépendances visées, pas un environnement intégralement testé ou verrouillé.

## Évaluation et interprétation

- Détection : visualisation et seuils uniquement. La mAP nécessite des annotations, donc elle n’est pas calculée sur cette photo non annotée.
- OCR : CER et WER via distance de Levenshtein. Sans transcription de référence sur une image personnelle, les métriques sont désactivées.
- Retrieval : trois requêtes à une seule cible chacune. Hit@k et mAP illustrent le calcul, sans constituer un benchmark. Le cosinus ne représente pas une probabilité.
- Les temps dépendent du matériel et excluent le téléchargement des poids. Aucune comparaison universelle de performances.

Les téléchargements vont dans `data/`, les résultats dans `outputs/`. Ils sont ignorés par Git. Pour aller plus loin : photos variées, annotations, plusieurs requêtes et séparation des données d’évaluation.

## Sources et licences

- [YOLO11](https://docs.ultralytics.com/models/yolo11/) et [inférence](https://docs.ultralytics.com/modes/predict/).
- [Tesseract](https://tesseract-ocr.github.io/tessdoc/) et [pytesseract](https://pypi.org/project/pytesseract/).
- [CLIP, Radford et al. 2021](https://arxiv.org/abs/2103.00020) et [fiche des poids](https://huggingface.co/openai/clip-vit-base-patch32).
- Photos : démonstrations publiques Ultralytics (bus, Zidane) et PyTorch Hub (chien), URLs dans les cellules. Images téléchargées à l’exécution, non redistribuées ici. Leurs droits restent ceux des sources.

Les bibliothèques, modèles et poids conservent leurs propres licences. Ultralytics propose notamment AGPL-3.0 et une licence commerciale selon l’usage. Consulter les conditions de chaque dépendance avant réutilisation.
