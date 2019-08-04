---
title: Préparer les lecteurs mappés pour le bureau géré Microsoft
description: Étapes importantes pour vous assurer
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: e4c2dbe8f1cae12aa1b10c6cd43f295a9a6062d0
ms.sourcegitcommit: 8102751ae20c93439e19afded396c4e6ee5ea5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "34100710"
---
#  <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Préparer les lecteurs mappés pour le bureau géré Microsoft

De nombreux environnements d’entreprise ont des exigences héritées pour les lecteurs mappés pour permettre à leurs utilisateurs ou équipes de partager et de stocker des fichiers, ou pour des applications locales. Microsoft ne recommande pas l’utilisation de lecteurs mappés avec le bureau géré Microsoft. Au lieu de cela, nous vous recommandons de moderniser les solutions d’accès aux fichiers yor comme suit:
  
- Migrer les lecteurs mappés utilisés par des utilisateurs individuels vers OneDrive entreprise. 
- Migrer des lecteurs mappés utilisés par teams pour partager des fichiers avec SharePoint Online. 
- Moderniser ou remplacer les applications qui utilisent des partages de fichiers locaux pour supprimer cette exigence.
  
La modernisation de ces services permettra aux utilisateurs finaux les plus performants avec le bureau géré Microsoft. Microsoft FastTrack services peut vous aider à moderniser votre environnement à l’aide des services de Cloud Computing Microsoft. Vous pouvez vérifier si vous êtes éligible aux services FastTrack dans les [offres et les services éligibles](https://docs.microsoft.com/fasttrack/m365-eligible-services-and-plans) , puis les contacter directement pour préparer le bureau géré Microsoft. Pour en savoir plus sur la migration de FastTrack OneDrive entreprise ou SharePoint Online, consultez la rubrique [migration de données](https://docs.microsoft.com/fasttrack/o365-data-migration).

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Lecteurs mappés sur le bureau géré Microsoft
 
Si vous ne pouvez pas supprimer ou remplacer des lecteurs mappés dans certains cas d’utilisation, vous devez soumettre une demande de support dans le portail d’administration de bureau géré Microsoft pour les déployer sur les utilisateurs de bureau géré Microsoft.
    
Pour une demande de ce type, vous devez fournir les informations suivantes dans la demande de support: 

- Tous les chemins d’accès UNC aux emplacements de partage de fichiers qui devront être mappés pour les appareils de bureau gérés par Microsoft 
- Groupes d’utilisateurs qui requièrent l’accès à ces emplacements de partage de fichiers 
- Une lettre de lecteur spécifique qui doit être attribuée (le cas échéant);

Par exemple :

| Lettre du lecteur | Chemin d’accès UNC | Groupe d’utilisateurs |
|--------------|----------|------------|
| ActiveX  | \\\server\share\Marketing | ContosoMarketing |

Il est de votre responsabilité de s’assurer que les utilisateurs et les groupes disposent des autorisations appropriées pour accéder aux emplacements de partage de fichiers et que les services de fichiers locaux restent accessibles. Par ailleurs, vous devez supprimer vos besoins pour ces partages de fichiers dès que possible.

### <a name="to-have-mapped-drives-deployed-in-microsoft-managed-desktop"></a>Pour déployer des lecteurs mappés dans le bureau géré Microsoft
 
Assurez-vous que les lecteurs mappés ne peuvent pas être évités et que vous avez soigneusement examiné les exigences avant d’envoyer une demande de service. Ensuite, procédez comme suit:

1. Accédez au [portail de bureau géré Microsoft](https://aka.ms/mmdportal).  
2. Soumettez une demande de support intitulée «déploiement de lecteurs mappés» via la section prise en charge des **demandes de support >** et fournissez tous les détails de partage de fichiers requis.  
3. Les opérations informatiques de bureau gérées par Microsoft conseilleront, à l’aide de mises à jour de demande de support, une fois la demande terminée. Cette configuration sera initialement déployée sur les appareils dans le groupe de déploiement de test.  
4. Vous devez tester et confirmer que la configuration déployée par le service informatique de bureau géré Microsoft fonctionne comme prévu. Répondez à l’aide de l’onglet discussion de la demande de support pour informer les opérations informatiques gérées par Microsoft une fois que vous avez terminé vos tests.  
5. L’équipe des opérations de bureau géré par Microsoft déploiera la configuration sur les autres groupes de déploiement. 
