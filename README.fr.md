# Automatisation IA, pipelines GPU & inférence conteneurisée

Dépôt vitrine public consacré aux workflows IA conteneurisés développés et maintenus par **Unicorn Who Dev**.

Ce dépôt documente des travaux concrets autour de l'inférence GPU reproductible, des environnements de serving de modèles, des pipelines IA automatisés, du pré/post-traitement et du déploiement via Docker.

> Il s'agit d'un **dépôt portfolio et documentation technique**. Il n'expose ni identifiants de production, ni endpoints privés, ni secrets de modèles, ni datasets propriétaires, ni services GPU payants ouverts sans contrôle.

## Ce que le dépôt démontre

- Déploiement IA avec Docker
- Environnements d'inférence GPU reproductibles
- Workloads CUDA / PyTorch
- Pipelines IA headless
- Services de modèles orientés API
- Séparation des modèles et des artefacts persistants
- Prétraitement et post-traitement conteneurisés
- Dépendances runtime versionnées
- Déploiement GPU local et distant
- Intégration de services IA dans des applications et automatisations plus larges

## Docker Hub public

**Docker Hub :** https://hub.docker.com/u/charlibillabert

Les images publiques servent de preuves techniques de workflows IA conteneurisés. Chaque conteneur peut appartenir à un projet R&D actif et posséder ses propres contraintes de runtime, modèles, licences et matériel.

## Conteneur mis en avant

### `charlibillabert/mmg-pose-sheet-pipeline`

Pipeline GPU headless créé pour un workflow de génération de personnages.

Les métadonnées publiques de l'image montrent notamment :

- Linux/amd64
- CUDA 13.0
- PyTorch 2.11
- ComfyUI
- Diffusers
- composants runtime épinglés par version
- volumes dédiés `/models` et `/data/artifacts`
- exécution orientée API
- port de service `8788`
- outils de preflight GPU et d'acceptance

Le conteneur encapsule l'environnement d'exécution d'un pipeline sketch-to-pose-sheet plutôt que de dépendre d'un poste de travail configuré manuellement.

Voir [`docs/mmg-pose-sheet-pipeline.md`](docs/mmg-pose-sheet-pipeline.md).

## Architecture type

```text
Client / Application
    |
    v
API ou requête de job
    |
    v
Service IA conteneurisé
    |
    +--> validation / prétraitement
    |
    +--> pipeline GPU
    |
    +--> post-traitement / validation
    |
    v
Artefacts versionnés / sortie structurée
```

Lorsque c'est pertinent, les poids de modèles et les artefacts générés restent séparés de l'image Docker. Cela permet de mettre à jour le runtime indépendamment des assets lourds et des sorties persistantes.

## Pourquoi Docker

Pour ces workloads IA, Docker fait partie de l'architecture de déploiement et ne sert pas uniquement à empaqueter du code.

L'objectif est de rendre un pipeline d'inférence :

- reproductible entre différentes machines,
- explicite sur ses dépendances,
- plus simple à déployer sur des fournisseurs GPU distants,
- validable avant l'acceptation de jobs,
- versionnable et réversible,
- et facilement intégrable derrière une API ou un workflow automatisé.

## Travaux associés

Ces conteneurs s'inscrivent dans un portfolio plus large couvrant :

- automatisation IA et workflows agentiques,
- IA générative,
- computer vision,
- datasets et fine-tuning,
- applications web,
- WebAudio et logiciels audio,
- systèmes géospatiaux et 3D.

Portfolio : https://unicornwhodev.com

GitHub : https://github.com/unicornwhodev

Hugging Face : https://huggingface.co/Charlbi

FireViewer : https://github.com/fireviewer

## Périmètre public

La documentation publique n'expose volontairement pas :

- les credentials et secrets API,
- les URLs internes de production,
- les endpoints GPU ouverts sans contrôle,
- les datasets privés,
- les poids propriétaires,
- les informations de facturation des fournisseurs,
- ni les détails opérationnels permettant d'abuser d'une infrastructure payante.
