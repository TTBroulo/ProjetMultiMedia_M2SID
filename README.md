# **Projet MultiMédia M2SID**

---
**Projet MultiMédia, M2 SID, UT3 Paul Sabatier**  

Réalisé par : **Léa Fabriol**, **Valentin Lafargue** & **Théotime Dmitrašinović**.  
Date : 23/10/2023 -> 10/11/2023  

Il est conseillé de cloner ce dossier dans google colab car le projet a été réalisé à l'aide de google drive.

---

# **Arborescence du répertoire GitHub avec Résumés des fichiers**


`README`
- `README.ipynb` : NoteBook d'édition du README markdown
- `README.md` : Le fichier README en markdown affiché par GitHub

## **`DOC\`**  

- `Rapport_Projet_NA_DM_M2_2023_2024.pdf` : Rapport de Projet  

- `Diapo_Projet_NA_DM_M2_2023_2024.pdf` : Diapo Soutenance  
  

---

## **`Media_Extract\`**  

- `Equilibrage_des_classes_Premiers_Tests.ipynb` : Premiers tests d'équilibrage de la distribution des catégories  
  
- `Pre-traitement.ipynb` : analyse des données du github, parcours des différentes données dont les fameux fichiers json à utilitée doutable, fichier permettant de récupérer et stocker
l'audio des vidéos en mp3 (format qui prend moins de place). (-> parallélisation sur création fichier mp3)  
  
- `Speech2Text.ipynb` : Fichier utilisant ces fichiers mp3 pour obtenir la transcription de l'audio original avec Whisper Small (-> parallélisation sur transcription)  
  
- `Video32Frames.ipynb` : Clustering sur les images pour sélectionner les 32 images les plus importantes d'une vidéo : Kmeans avec distance classique et k=32, on prend l'image la plus proche de chaque cluster.  
  
- `ZeroShot.ipynb` : Unsupervised deep learning sur des données textuelles: essayer de relabéliser les données avec les labels présents dans le papier, approche classification directe intéressante mais pas exploitée.  
  
---

## **`Embeddings_Extract\`**  

- **`Audio\`** :  
  - `Exploration_AudioDetection.ipynb` : Notebook de recherche de modèles pré-entrainés pour la detection audio  
    
  - `ExtractAudioEmbeddings_VGGish.ipynb` : Récupération des embeddings Audio avec le modèle pré-entrainé VGGish   
    
  - `ExtractAudioEmbeddings_YAMNet.ipynb` :  Récupération des embeddings Audio avec le modèle pré-entrainé YAMNet  
     
  - `inferenceALL.py` : Script python utilisé pour la récupération des embeddings avec YAMNet, récupère le vecteur entier (521) et pas seulement les 10 sons environnants les mieux prédits  
    

- **`Video\`** :  
  - `Embeddings_res_yolo.ipynb` : Transforme en embeddings les résultats de yolo et applique un classifieur aux embeddings  
    
  - `use_yolo.ipynb` : Fait tourner l’algo yolo et enregistre les résultats dans un fichier   
    
  - `detect.py` : Fichier du package yolo modifier pour obtenir les sortie voulues à savoir la proba de l’objet et l’objet détecté pour chaque frame  
    
  - `ViViT2210.ipynb` : Utilisation du model sur nos 32 images sélectionné avec la méthode développé dans `Video32Frames.ipynb`, on récupère l'embedding qui est la dernière couche du model de classification original, on supprime toute la sortie (sauf ce qui nous intéresse) pour la ram et on recommence
   

- **`Texte\`** :  
  - `mpnet.ipynb` : Fichier avec embeddings de MPnet et prediction Deep + ML  
   


  
- `..\Classification\Text.ipynb` : Extraction des embeddings **et** Classification. Prédictions avec DistilBERT ainsi qu'un Model de ML sur un sentenceBERT classique ; des approches classiques de ML (SVC) sur ces embeddings  

   
---

## **`Classification\`**  


- `ClassifAudio_Premiers_Tests.ipynb` :  Premiers tests de classification audio  
  
- `Classification_Audio.ipynb` : Classification de toutes les combinaisons de labelisation, Embeddings audio et méthode d'équilibrage  
  
- `ClassifViViT.ipynb` : Deep learning et ML sur les embeddings de ViViT (qui ont du être aggrée par manque de RAM)  
  
- `Text.ipynb` : Fichier sur lequel on a les prédictions avec DistilBERT ainsi qu'un Model de ML sur un sentenceBERT classique ; des approches classiques de ML (SVC) sur ces embeddings  
  
- `TranscriptionClassificationML.ipynb` : ML sur des approches d'embeddings simples : countvectorizer, tf-idf
  
`..\Embeddings_Extract\Video\Embeddings_res_yolo.ipynb` : Extraction des embeddings **et** Classification. Transforme en embeddings les résultats de yolo et applique un classifieur aux embeddings.    

---

## **`Multi&Cross_Modal\`**  

- `CrossModal_et_MultiModalntermediaire.ipynb` : Embeddings vers Embeddings (audio(VGG-ish)/texte(MPnet)/video(yolo)) ; prédiction intermédiaire avec Réseau de Neurone plsu complexe (tf.split + tf.concat) qui permet de réduire la dimension des embeddings et de les uniformiser en ayant déjkà pour but la classification.  
  
- `MultiModalPrécoce.ipynb` : Réunion des embeddings des trois modalités (avant classification)
  
- `MultiModalTardivet.ipynb` : Réunion des probabilités de prédictions des trois modalités (après classification)
  
- `DALLE_mini.ipynb` :  Transformation de la description écrite en image, but étant de comparer ensuite ces images au images les plus représentatives de la vidéo  
  
- `Texte_to_image.ipynb` : Test dans le but d'évaluer la correspondance entre les images et la description écrite d’une vidéo avec le modèle CLIP  
   
---

Les Notebooks suivants comprennent à la fois l'extraction des caractéristiques et la classification.  
- `Classification\Text.ipynb`  
- `Embeddings_Extract\Video\Embeddings_res_yolo.ipynb`
