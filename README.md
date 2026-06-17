# 🚢 Segmentation par Instance d'Objets Maritimes par Apprentissage Profond

> Projet de Préparation Métier (P2M) — École Supérieure des Communications de Tunis (SUP'COM) — Année Universitaire 2025/2026

## 📋 Description

Ce projet propose une chaîne de traitement complète pour la **surveillance maritime par apprentissage profond**, depuis la collecte automatisée d'images satellitaires jusqu'au déploiement de modèles de détection et de segmentation au sein d'une application web temps réel (**Surveillini**).

Le pipeline couvre :
- 🛰️ **Collecte automatisée** d'images satellitaires via l'API OpenAerialMap
- 🏷️ **Annotation semi-automatique** avec SAM 3 (prompts textuels) + filtres post-traitement
- ✏️ **Correction manuelle** des annotations via CVAT
- 🧠 **Fine-tuning** de SAM 3 et YOLO11 (nano & large) sur 8 classes d'objets maritimes
- 📊 **Évaluation comparative** (précision, rappel, mIoU, mAP50, mAP50-95)
- 🌐 **Intégration** dans l'application web Surveillini

## 👥 Auteurs

- **Abbes Amir**
- **Harrabi Ines**

## 🎓 Encadrants

- Mme. Abdelkefi Fatma
- Mme. Trabelsi Rim
- M. Cabani Adnane 
- M. Lucas Justin Yirepoa Kinda

## 🏗️ Architecture du pipeline

```
OpenAerialMap (collecte) 
        ↓
SAM 3 (pré-annotation par prompts textuels)
        ↓
Filtres post-traitement (NMS, taille, forme, HSV)
        ↓
CVAT (correction manuelle)
        ↓
Dataset final (840/200/220)
        ↓
Fine-tuning SAM 3 & YOLO11 (n/l)
        ↓
Application Surveillini (temps réel)
```

## 🗂️ Classes d'objets maritimes

| Classe 
|---
| `voilier` 
| `yacht` 
| `jet_ski` 
| `bateau_peche` 
| `navire_croisiere` 
| `navire_militaire` 
| `remorqueur` 
| `cargo` 

## 📊 Dataset

- **1260 images** collectées (zones portuaires, multi-échelle, via OpenAerialMap)
- Annotation semi-automatique (SAM 3) + correction manuelle (CVAT)
- Répartition : **Train (840) / Validation (200) / Test (220)**
- Format : images PNG + annotations XML CVAT (polygones de segmentation)

📦 **Le dataset complet est disponible via ce lien** : [lien à compléter]

## 🧠 Modèles entraînés

| Modèle | Tâche | mAP50-95 (Test) |
|---|---|---|
| SAM 3 (fine-tuné) | Segmentation par instance | 0.809 (mIoU seg) |
| YOLO11n (sans augmentation) | Détection | 0.246 |
| YOLO11n (avec augmentation) | Détection | 0.326 |
| YOLO11l (avec augmentation) | Détection | **0.389** |

> 📈 Amélioration totale du mAP50-95 entre la 1ère et la dernière expérience YOLO : **+58.1%**

## Résultats et nouveaux paramètres :
Ce lien vous ramène à un fichier contenant les nouveaux poids obtenus à la fin de la phase de finetuning : 
 https://drive.google.com/file/d/1w3XW2gtmdcLUH3TAXct9jDZY0pvY4-Uw/view?usp=sharing


### 🔭 Perspectives

- Enrichissement du dataset pour les classes sous-représentées (jet-ski, voilier, bateau de pêche)
- Exploration de modèles plus récents (YOLO26)
- Pipeline hybride SAM 3 + YOLO11 (précision de segmentation + rapidité de détection)


*SUP'COM — Université de Carthage — Année Universitaire 2025/2026*
