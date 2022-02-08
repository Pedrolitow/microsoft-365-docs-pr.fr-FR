---
title: Préparer les lecteurs mappés pour le Bureau géré Microsoft
description: Étapes importantes pour s’assurer que les utilisateurs peuvent accéder aux données sur des lecteurs mappés
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d8100323350b11cb2329d752892cd64b1bc764a0
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62444556"
---
# <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Préparer les lecteurs mappés pour le Bureau géré Microsoft

De nombreux environnements d’entreprise ont des exigences héritées pour les lecteurs mappés pour permettre à leurs utilisateurs ou équipes de partager et stocker des fichiers, ou pour les applications sur site.

Microsoft ne recommande pas l’utilisation de lecteurs mappés avec les Microsoft Manged Desktop. Au lieu de cela, nous vous recommandons de moderniser vos solutions d’accès aux fichiers comme suit :
  
- Migrez les lecteurs mappés utilisés par des utilisateurs individuels vers OneDrive Entreprise.
- Migrez les lecteurs mappés utilisés par les équipes pour partager des fichiers vers SharePoint Online.
- Moderniser ou remplacer les applications qui utilisent des partages de fichiers locaux pour supprimer cette exigence.
  
La modernisation de ces services permettra aux utilisateurs d’avoir la meilleure expérience Microsoft Manged Desktop. Microsoft FastTrack Services cloud peut vous aider à moderniser votre environnement à l’aide de Microsoft Cloud Services. Vous pouvez vérifier si vous êtes éligible aux services FastTrack services et plans [éligibles](/fasttrack/m365-eligible-services-and-plans). Ensuite, contactez-les directement pour vous préparer au Microsoft Manged Desktop. Pour plus d’informations sur FastTrack OneDrive Entreprise migration SharePoint online, voir [Migration des données](/fasttrack/o365-data-migration).

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Lecteurs mappés sur Microsoft Manged Desktop

Si vous ne pouvez pas supprimer ou remplacer des lecteurs mappés dans certains cas d’utilisation, vous devez envoyer une demande de support dans le portail d’administration Microsoft Manged Desktop pour les déployer vers Microsoft Manged Desktop utilisateurs.

Pour ce type de demande, vous devez fournir les détails suivants dans la demande de support :

- Tous les chemins d’accès UNC aux emplacements de partage de fichiers qui devront être Microsoft Manged Desktop périphériques.
- Groupes d’utilisateurs qui nécessitent l’accès à ces emplacements de partage de fichiers.
- Toute lettre de lecteur spécifique à attribuer (si nécessaire).

Par exemple :

| Lettre du lecteur | Chemin UNC | Groupe d’utilisateurs |
|--------------|----------|------------|
| X:  | \\\server\share\Marketing | ContosoMarketing |

Il est entièrement de votre responsabilité de :

- S’assurer que les utilisateurs et les groupes ont et conservent les autorisations d’accès aux emplacements de partage de fichiers
- Rendre les services de fichiers locaux accessibles.

Vous devez supprimer les conditions requises pour ces partages de fichiers dès que possible.

**Pour déployer des lecteurs mappés dans Microsoft Manged Desktop :**

Assurez-vous que les lecteurs mappés ne peuvent pas être évités et que vous avez attentivement examiné les conditions requises avant d’envoyer une demande de support.

1. Accédez à [Microsoft Endpoint Manager](https://endpoint.microsoft.com/), puis sélectionnez **Résolution des problèmes + prise en charge**.
1. Dans la **section Microsoft Manged Desktop**, sélectionnez **Demandes de service**.
1. Envoyez une demande de support intitulée « Déploiement de lecteurs mappés » et fournissez tous les détails requis du partage de fichiers.  
1. Microsoft Manged Desktop opérations de l’équipe technique vous conseillera, à l’aide des mises à jour des demandes de support, une fois la demande terminée. Initialement, cette configuration sera déployée uniquement sur les appareils du groupe de déploiement Test.  
1. Vous devez tester et vérifier si la configuration déployée par le Microsoft Manged Desktop opérations IT fonctionne comme prévu.
1. Dans la même demande de support, répondez à l’aide de l’onglet **Discussion** pour Microsoft Manged Desktop opérations it. Une fois que vous avez terminé vos tests.  
1. Microsoft Manged Desktop’équipe des opérations IT déploiera ensuite la configuration sur les autres groupes de déploiement.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Étapes pour vous préparer à la Microsoft Manged Desktop

1. Examinez [Configuration requise pour le Bureau géré Microsoft](prerequisites.md).
1. Exécutez les [outils d’évaluation de la préparation](readiness-assessment-tool.md).
1. Achetez [Portail d’entreprise](../get-started/company-portal.md).
1. Passez en revue les [prérequis pour les comptes invités](guest-accounts.md).
1. Vérifiez la[configuration réseau](network.md).
1. [Préparer les certificats et les profils réseau](certs-wifi-lan.md).
1. [Préparer l’accès utilisateur aux données](authentication.md).
1. [Préparer les applications](apps.md).
1. Préparer les lecteurs mappés (cet article).
1. [Préparer les ressources d’impression](printing.md).
1. [noms d’appareil](address-device-names.md) d’une adresse.
