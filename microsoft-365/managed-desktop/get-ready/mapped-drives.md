---
title: Préparer les lecteurs mappés pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer que les utilisateurs peuvent accéder aux données sur des lecteurs mappés
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: d272c08287dd6198d4c33b4d1df3ff8662eda12781d676b75c93189d08409de7
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53819090"
---
#  <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Préparer les lecteurs mappés pour le Bureau géré Microsoft

De nombreux environnements d’entreprise ont des exigences héritées pour les lecteurs mappés pour permettre à leurs utilisateurs ou équipes de partager et stocker des fichiers, ou pour les applications sur site. Microsoft ne recommande pas l’utilisation de lecteurs mappés avec les Microsoft Manged Desktop. Au lieu de cela, nous vous recommandons de moderniser vos solutions d’accès aux fichiers comme suit :
  
- Migrez les lecteurs mappés utilisés par des utilisateurs individuels vers OneDrive Entreprise. 
- Migrez les lecteurs mappés utilisés par les équipes pour partager des fichiers vers SharePoint Online. 
- Moderniser ou remplacer les applications qui utilisent des partages de fichiers locaux pour supprimer cette exigence.
  
La modernisation de ces services permettra aux utilisateurs d’avoir la meilleure expérience Microsoft Manged Desktop. Les services Microsoft FastTrack peuvent vous aider à moderniser votre environnement à l’aide de Microsoft Cloud Services. Vous pouvez vérifier si vous êtes éligible aux services FastTrack auprès des plans et [services](/fasttrack/m365-eligible-services-and-plans) éligibles, puis les contacter directement pour préparer Microsoft Manged Desktop. Pour obtenir des informations sur FastTrack OneDrive Entreprise ou SharePoint migration en ligne, voir [Migration des données.](/fasttrack/o365-data-migration)

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Lecteurs mappés sur Microsoft Manged Desktop
 
Si vous ne pouvez pas supprimer ou remplacer des lecteurs mappés pour certains cas d’utilisation, vous devez envoyer une demande de support dans le portail d’administration Microsoft Manged Desktop pour les déployer vers Microsoft Manged Desktop utilisateurs.
    
Pour ce type de demande, vous devez fournir les détails suivants dans la demande de support : 

- Tous les chemins d’accès UNC aux emplacements de partage de fichiers qui devront être Microsoft Manged Desktop périphériques 
- Groupes d’utilisateurs qui nécessitent l’accès à ces emplacements de partage de fichiers 
- Toute lettre de lecteur spécifique à attribuer (si nécessaire)

Par exemple :

| Lettre du lecteur | Chemin UNC | Groupe d’utilisateurs |
|--------------|----------|------------|
| X:  | \\\server\share\Marketing | ContosoMarketing |

Il est entièrement de votre responsabilité de vous assurer que les utilisateurs et les groupes ont et conservent les autorisations d’accès aux emplacements de partage de fichiers et que les services de fichiers locaux restent accessibles. En outre, vous devez supprimer vos exigences pour ces partages de fichiers dès que possible.

### <a name="to-have-mapped-drives-deployed-in-microsoft-managed-desktop"></a>Pour déployer des lecteurs mappés dans Microsoft Manged Desktop
 
Assurez-vous que les lecteurs mappés ne peuvent pas être évités et que vous avez soigneusement examiné les conditions requises avant d’envoyer une demande de service. Ensuite, suivez les étapes suivantes :

1. Accédez [à Microsoft Endpoint Manager](https://endpoint.microsoft.com/) puis sélectionnez « Résolution des problèmes + prise en charge », puis recherchez « Demandes de service » dans la section Microsoft Manged Desktop.  
2. Envoyez une demande de support intitulée « Déploiement de lecteurs mappés » et fournissez tous les détails requis du partage de fichiers.  
3. Microsoft Manged Desktop Les opérations des services itaux vous conseillent, à l’aide des mises à jour des demandes de support, une fois la demande terminée. Initialement, cette configuration sera déployée uniquement sur les appareils du groupe de déploiement Test.  
4. Vous devez tester et vérifier si la configuration déployée par le Microsoft Manged Desktop opérations IT fonctionne comme prévu. Répondez à l’aide de l’onglet Discussion dans les détails de la même demande de support pour Microsoft Manged Desktop opérations it.une fois que vous avez terminé vos tests.  
5. Microsoft Manged Desktop L’équipe des opérations itaux déploiera ensuite la configuration sur les autres groupes de déploiement. 

## <a name="steps-to-get-ready"></a>Étapes pour vous préparer

1. Examiner [les conditions préalables pour Microsoft Manged Desktop](prerequisites.md).
2. [Utiliser les outils d’évaluation de la préparation.](readiness-assessment-tool.md)
3. [Conditions préalables pour les comptes invité](guest-accounts.md)
4. [Configuration du réseau pour Bureau géré Microsoft](network.md)
5. [Préparer les certificats et les profils réseau pour le Bureau géré Microsoft](certs-wifi-lan.md)
6. [Préparer l’accès aux ressources locales pour le Bureau géré Microsoft](authentication.md)
7. [Applications dans le Bureau géré Microsoft](apps.md)
8. [Préparer les lecteurs Microsoft Manged Desktop](mapped-drives.md) (Cet article)
9. [Préparer des ressources d’impression pour le Bureau géré Microsoft](printing.md)
