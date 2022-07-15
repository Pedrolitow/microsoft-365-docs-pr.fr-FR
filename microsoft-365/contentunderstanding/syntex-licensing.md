---
title: Gestion des licences pour SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: high
description: En savoir plus sur les licences pour SharePoint Syntex
ms.openlocfilehash: 31b10c0107bf871f827244889ac7ec77f7958e1f
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787493"
---
# <a name="licensing-for-sharepoint-syntex"></a>Gestion des licences pour SharePoint Syntex

Pour utiliser SharePoint Syntex, chaque utilisateur Syntex doit disposer d’une licence. Si vous annulez vos licences SharePoint Syntex à une date ultérieure (ou si votre version d’évaluation expire), les utilisateurs ne pourront plus créer, publier ou exécuter des modèles de compréhension de document ou de traitement de formulaire. En outre, les rapports des magasins à terme, l'importation de la taxonomie SKOS et la poussée des types de contenu ne seront plus disponibles. Aucun modèle, contenu ou métadonnées ne sera supprimé et les autorisations de site ne seront pas modifiées.
 
> [!NOTE] 
> SharePoint Syntex est une licence d’extension et exige que les utilisateurs disposent également d’une licence pour Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Tâches nécessitant une licence
 
Les tâches suivantes nécessitent une [licence SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) pour l’utilisateur qui les exécute :
 
- Appliquer un modèle de compréhension de document à une bibliothèque. (Les utilisateurs sans licence peuvent se voir accorder l'accès à un centre de contenu et peuvent y créer des modèles de compréhension de documents, mais ne peuvent pas les appliquer à une bibliothèque de documents).
- Création d’un modèle de traitement de formulaire via le point d’entrée dans une bibliothèque
- Chargement de contenu dans une bibliothèque où un modèle de compréhension des documents ou de traitement des formulaires a été appliqué.
- Exécution d'un modèle de compréhension des documents à la demande
- Utilisez les services de taxonomie Premium. (Les services de taxonomie Premium comprennent l’importation d’ensembles de termes basés sur SKOS, l’envoi de types de contenu d’entreprise aux sites associés au hub et les rapports de magasin de termes.)

Les utilisateurs sans licence peuvent avoir accès à un centre de contenu et créer des modèles de compréhension de document, mais ne peuvent pas les appliquer à une bibliothèque de documents.
 
## <a name="cost-of-training-and-running-models"></a>Coût de l’entraînement et de l’exécution des modèles
 
Le coût de l’entraînement et d’exécution des modèles de compréhension de document est inclus dans le coût d’une licence SharePoint Syntex. Toutefois, les modèles de traitement de formulaire utilisent AI Builder capacité, à la fois pour le traitement de l’entraînement et du runtime. La capacité doit être allouée à l’environnement Power Apps dans lequel vous utiliserez AI Builder.

Pour chaque licence SharePoint Syntex, vous disposez de 3 500 crédits de générateur d’IA par licence, par mois regroupés au niveau du locataire, avec une allocation maximale de 1 million de crédits par mois. Cette allocation est renouvelée chaque mois pour chaque licence SharePoint Syntex active. (Les crédits inutilisés ne se cumulent pas d’un mois à l’autre.) 

Vous pouvez estimer la capacité d’AI Builder qui vous convient, grâce à la calculatrice [AI Builder](https://powerapps.microsoft.com/ai-builder-calculator).

Si vous planifiez d’utiliser un environnement Power Platform personnalisé, vous devez [attribuer des crédit à cet environnement](/power-platform/admin/capacity-add-on).

Accédez au [Centre d’administration Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) pour vérifier vos crédits et leur utilisation.
  
## <a name="additional-term-store-features"></a>Fonctionnalités supplémentaires du magasin de termes
 
Un abonnement à SharePoint Syntex propose les fonctionnalités de magasin de termes supplémentaires suivantes :
 
- Importation de l’ensemble de termes basé sur SKOS
- Envoi de types de contenu d’entreprise à un site hub, qui les ajoute également aux sites associés et aux listes ou bibliothèques nouvellement créées
- Rapports de magasin de termes fournissant des insights sur les ensembles de termes publiés et leur utilisation dans votre locataire


## <a name="see-also"></a>Voir aussi

Vue d’ensemble des licences [pour Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[FAQ sur les licences Power Apps et Power Automate](/power-platform/admin/powerapps-flow-licensing-faq)
