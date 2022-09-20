---
title: Gérer la configuration de Pertinence dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
titleSuffix: Office 365
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: fd6be6d3-2e8d-449d-9851-03ab7546e6aa
ROBOTS: NOINDEX, NOFOLLOW
description: Lisez les recommandations pour configurer la formation de Pertinence dans eDiscovery (Premium) pour noter les fichiers par pertinence et générer des résultats analytiques.
ms.openlocfilehash: d66db4fc4a03aab2e63e093eb91a33267f66414e
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67820214"
---
# <a name="manage-relevance-setup-in-ediscovery-premium-classic"></a>Gérer la configuration de Pertinence dans eDiscovery (Premium) (classique)

> [!NOTE]
> Microsoft Purview eDiscovery (Premium) nécessite l’utilisation d’Office 365 E3 avec le module complémentaire Conformité avancée ou un abonnement E5 pour votre organisation. Si vous ne disposez pas de cette offre et que vous souhaitez essayer eDiscovery (Premium), vous pouvez [vous inscrire pour bénéficier d’un essai gratuit d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279). 
  
 La technologie de Pertinence eDiscovery (Premium) utilise des logiciels guidés par des experts pour la notation des fichiers en fonction de leur pertinence. Pertinence eDiscovery (Premium) peut être utilisée pour l’évaluation précoce des cas (ECA), l’élimination et l’examen des exemples de fichiers. 
  
 eDiscovery (Premium) inclut des composants pour la formation de Pertinence et le balisage des fichiers pertinents pour un cas. eDiscovery (Premium) apprend à partir des exemples formés de fichiers pertinents et non pertinents pour fournir des scores de pertinence pour chaque fichier, et génère des résultats analytiques qui peuvent être utilisés pendant et après le processus de révision de fichier. 
  
## <a name="guidelines-for-setting-up-relevance-training"></a>Conseils de configuration de l’entraînement Pertinence

 Dans Advanced eDiscovery, dans la fenêtre **Cas**, sélectionnez un cas et cliquez sur **Atteindre le cas**. Cliquez sur **Pertinence** \> **Installation de Pertinence**. Suivez ces conseils pour configurer Pertinence. 
  
- **Étiquetage** : l’efficacité du processus d’entraînement itératif Pertinence dépend de la capacité de l’expert à étiqueter les échantillons de fichier avec précision et cohérence.

- **Sujets des cas** :
  
  - Pour chaque sujet, faites appel au même expert tout au long de l’entraînement Pertinence. Plusieurs experts ne peuvent pas étiqueter le même sujet en même temps.
  
  - Déterminez si chaque groupe de fichiers est pertinent par rapport à un sujet spécifique.

  - Si un problème est défini trop généralement, eDiscovery (Premium) peut produire trop de fichiers qui ne sont pas pertinents. Si un problème est défini de façon trop étroite, le processus d’entraînement de Pertinence peut prendre plus de temps. 

  - Au cours de chaque cycle de formation de Pertinence, eDiscovery (Premium) se concentre sur un problème actif unique et les exemples de résultats intermédiaires sont affichés en conséquence.

  - Dans un scénario à sujets multiples, le mode Échantillonnage permet de sélectionner des sujets à inclure dans le processus. Les sujets marqués « Inactif » ne sont pas traités tant que le mode Échantillonnage n’est pas modifié. Un sujet peut apparaître « Inactif » ou « Actif » pour un seul expert.

  - eDiscovery (Premium) peut être utilisé pour générer des fichiers de privilèges candidats. Configurez un problème distinct pour les privilèges. Si possible, effectuez d’abord l’apprentissage et l’élimination en fonction de la pertinence, puis effectuez l’apprentissage pour obtenir des privilèges sur le jeu éliminé uniquement (rechargez l’ensemble éliminé en tant que cas distinct). 

  - Vous pouvez uniquement effectuer un traitement par lots si aucun échantillon n’est ouvert (quand vous cliquez sur Traitement par lots, une liste d’utilisateurs contenant des échantillons ouverts s’affiche). Un administrateur peut « fermer » les échantillons d’autres utilisateurs (seulement si ces utilisateurs ne sont pas en train d’étiqueter ces échantillons), en utilisant l’utilitaire « Modifier la pertinence » avec l’option « Tous les échantillons des utilisateurs ».

- **Métadonnées**: eDiscovery (Premium) se concentre sur le contenu. Il ne prend pas en compte les métadonnées dans le cadre des critères de pertinence.

- **Richesse** : si la richesse d’un sujet est inférieure à 3 % après évaluation, prévoyez d’alimenter l’entraînement Pertinence avec des fichiers pertinents et non pertinents connus.

- **Taille de fichier** : les fichiers volumineux (plus de 5 242 880 caractères de texte extrait) sont ignorés dans Pertinence. Ces fichiers ne participent pas au processus d’entraînement Pertinence et ne reçoivent pas de note de pertinence après le traitement par lots. Les fichiers de plus de 5 Mo peuvent être inclus dans le jeu d’évaluation.

## <a name="setting-up-case-issues"></a>Configuration des sujets des cas

Les paramètres décrits dans cette section sont disponibles dans eDiscovery (Premium) **Pertinence** \> **Configuration de Pertinence**.
  
- Les sujets doivent être affectés à un utilisateur qui entraînera les fichiers.

- Les fichiers importés doivent ensuite être ajoutés au chargement en cours de traitement.

- Définissez et organisez les sujets attentivement, car cela peut influer sur les résultats de l’entraînement Pertinence.

Une fois les paramètres définis, le réviseur-expert peut commencer à entraîner les fichiers dans l’onglet **Pertinence**.
