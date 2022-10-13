---
title: Gestion des licences pour Microsoft Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: high
description: Découvrez les licences pour Microsoft Syntex.
ms.openlocfilehash: c3c78d407aacb260d6b9d6edb9597d9fc3a4c38c
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68565045"
---
# <a name="licensing-for-microsoft-syntex"></a>Gestion des licences pour Microsoft Syntex

Pour utiliser SharePoint Syntex, vous devez disposer d’une licence pour chaque utilisateur Syntex. Si vous supprimez toutes les licences SharePoint Syntex de votre locataire à une date ultérieure (ou si votre version d’évaluation expire), les utilisateurs ne pourront plus créer, publier ou exécuter des modèles de compréhension de document ou de traitement de formulaire. En outre, les rapports des magasins à terme, l'importation de la taxonomie SKOS et la poussée des types de contenu ne seront plus disponibles. Aucun modèle, contenu ou métadonnées ne sera supprimé et les autorisations de site ne seront pas modifiées.
 
> [!NOTE] 
> Syntex est une licence de module complémentaire qui exige que les utilisateurs disposent également d’une licence pour Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Tâches nécessitant une licence
 
Les tâches suivantes nécessitent une [licence Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) pour l’utilisateur qui les exécute :
 
- Applying a document understanding model to a library. (Unlicensed users can be granted access to a content center and can create document understanding models there but can't apply them to a document library.)
- Création d’un modèle de traitement de formulaire via le point d’entrée dans une bibliothèque
- Chargement de contenu dans une bibliothèque où un modèle de compréhension des documents ou de traitement des formulaires a été appliqué.
- Exécution d'un modèle de compréhension des documents à la demande
- Création d’un modèle moderne avec un assembly de contenu
- Génération d’un document à partir d’un modèle moderne
- Utilisation de la recherche avancée de métadonnées
- Utilisation des services de taxonomie Premium. (Premium services de taxonomie comprennent l’importation d’ensembles de termes basés sur SKOS, qui poussent les types de contenu d’entreprise vers les sites associés au hub et les rapports du magasin de termes.)

Les utilisateurs sans licence peuvent avoir accès à un centre de contenu et créer des modèles de compréhension de document, mais ne peuvent pas les appliquer à une bibliothèque de documents.
 
## <a name="cost-of-training-and-running-models"></a>Coût de l’entraînement et de l’exécution des modèles
 
Le coût de l’entraînement et de l’exécution des modèles de compréhension des documents est inclus dans le coût d’une licence Syntex. Toutefois, les modèles de traitement de formulaire utilisent AI Builder capacité, à la fois pour le traitement de l’entraînement et du runtime. La capacité doit être allouée à l’environnement Power Apps dans lequel vous utiliserez AI Builder.

Pour chaque licence Syntex, vous disposez de 3 500 crédits AI Builder par licence, par mois regroupés au niveau du locataire, avec une allocation maximale de 1 million de crédits par mois. Cette allocation est renouvelée chaque mois pour chaque licence Syntex active. (Les crédits inutilisés ne se cumulent pas d’un mois à l’autre.) 

Vous pouvez estimer la capacité d’AI Builder qui vous convient, grâce à la calculatrice [AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Si vous planifiez d’utiliser un environnement Power Platform personnalisé, vous devez [attribuer des crédit à cet environnement](/power-platform/admin/capacity-add-on).

Accédez au [Centre d’administration Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) pour vérifier vos crédits et leur utilisation.
  
## <a name="additional-term-store-features"></a>Fonctionnalités supplémentaires du magasin de termes

Le fait d’avoir une ou plusieurs licences Syntex dans votre organisation permet aux administrateurs SharePoint d’utiliser les fonctionnalités de magasin de termes supplémentaires suivantes :
 
- Importation de l’ensemble de termes basé sur SKOS
- Envoi de types de contenu d’entreprise à un site hub, qui les ajoute également aux sites associés et aux listes ou bibliothèques nouvellement créées
- Rapports de magasin de termes fournissant des insights sur les ensembles de termes publiés et leur utilisation dans votre locataire


## <a name="see-also"></a>Voir aussi

Vue d’ensemble des licences [pour Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[FAQ sur les licences Power Apps et Power Automate](/power-platform/admin/powerapps-flow-licensing-faq)
