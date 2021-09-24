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
localization_priority: Priority
description: En savoir plus sur les licences pour SharePoint Syntex
ms.openlocfilehash: 3c44545136a7ca67a63315a8378389212a160373
ms.sourcegitcommit: 0ed93816e2c1e6620e68bd1c0f00390062911606
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2021
ms.locfileid: "59484046"
---
# <a name="licensing-for-sharepoint-syntex"></a>Gestion des licences pour SharePoint Syntex

Pour utiliser SharePoint Syntex, votre organisation doit disposer d’un abonnement à SharePoint Syntex et chaque utilisateur Syntex doit disposer d’une licence. Si vous annulez votre abonnement SharePoint Syntex à une date ultérieure (ou si votre version d’évaluation expire), les utilisateurs ne pourront plus créer, publier ou exécuter des modèles de compréhension de document ou de traitement de formulaire. En outre, les rapports des magasins à terme, l'importation de la taxonomie SKOS et la poussée des types de contenu ne seront plus disponibles. Aucun modèle, contenu ou métadonnées ne sera supprimé et les autorisations de site ne seront pas modifiées.
 
> [!NOTE] 
> SharePoint Syntex est une licence d’extension et exige que les utilisateurs disposent également d’une licence pour Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>Tâches nécessitant une licence
 
Les tâches suivantes nécessitent une licence SharePoint Syntex pour l’utilisateur qui les exécute :
 
- Appliquer un modèle de compréhension de document à une bibliothèque. (Les utilisateurs sans licence peuvent se voir accorder l'accès à un centre de contenu et peuvent y créer des modèles de compréhension de documents, mais ne peuvent pas les appliquer à une bibliothèque de documents).
- Création d’un modèle de traitement de formulaire via le point d’entrée dans une bibliothèque
- Chargement de contenu dans une bibliothèque où un modèle de compréhension des documents ou de traitement des formulaires a été appliqué.
- Exécution d'un modèle de compréhension des documents à la demande
- Affichage des métadonnées extraites de fichiers à l’aide d’un modèle de compréhension de document ou de traitement de formulaires (Les utilisateurs doivent être titulaires d’une licence d’accès et d’utilisation des métadonnées associées aux fichiers traitées, quel que soit l’endroit où les fichiers sont déplacés.)
- Utilisez les services de taxonomie Premium. (Les services de taxonomie Premium comprennent l’importation d’ensembles de termes basés sur SKOS, l’envoi de types de contenu d’entreprise aux sites associés au hub et les rapports de magasin de termes.)

Les utilisateurs sans licence peuvent avoir accès à un centre de contenu et créer des modèles de compréhension de document, mais ne peuvent pas les appliquer à une bibliothèque de documents.
 
## <a name="cost-of-running-models"></a>Coût d’exécution des modèles
 
Le coût d’exécution des modèles de compréhension de document est inclus dans le coût d’une licence SharePoint Syntex. Toutefois, les modèles de traitement de formulaire utilisent AI Builder capacité, à la fois pour le traitement de l’entraînement et du runtime. La capacité doit être allouée à l’environnement Power Apps dans lequel vous utiliserez AI Builder.
 
Si vous possédez 300 licences SharePoint Syntex au sein de votre organisation, vous bénéficierez d’un million de crédits AI Builder. Cette capacité est renouvelée chaque mois si vous conservez le minimum de 300 licences. (Les crédits inutilisés ne se cumulent pas d’un mois à l’autre.) Si vous avez moins de 300 licences, vous devez acheter AI Builder crédits pour utiliser le traitement des formulaires.
 
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
