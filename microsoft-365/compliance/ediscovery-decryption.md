---
title: Déchiffrement dans eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment les outils eDiscovery de Microsoft 365 gèrent les documents chiffrés joints aux messages électroniques.
ms.openlocfilehash: 91d5689bfb64d272c896c0e92422ce1f45fd5f72
ms.sourcegitcommit: 89f56c3e0b619a4700a75a21927d9ffc90658632
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "48984898"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils eDiscovery de Microsoft 365

Le chiffrement est une partie importante de votre stratégie de protection des informations et de protection des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et garantir que seules les personnes appropriées ont accès à ce contenu.

Pour exécuter des tâches eDiscovery communes sur du contenu chiffré, les gestionnaires eDiscovery ont été tenus de déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, de cas de découverte électronique principaux et de cas avancés de découverte électronique. Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible à des fins de révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail de découverte électronique, les outils eDiscovery de Microsoft 365 incorporent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. Avant cette nouvelle capacité, seul le contenu d’un message électronique protégé par la gestion des droits (et non les fichiers attachés) a été déchiffré. À présent, si un fichier chiffré avec une technologie de chiffrement Microsoft est joint à un message électronique correspondant aux critères de recherche, le fichier chiffré est déchiffré lors de la préparation des résultats de la recherche. Cela permet aux gestionnaires de découverte électronique d’afficher le contenu des pièces jointes chiffrées lors de l’aperçu des résultats de la recherche et de les examiner une fois qu’ils ont été ajoutés à un jeu de révisions dans Advanced eDiscovery.

> [!NOTE]
> À partir de bientôt, les outils eDiscovery de Microsoft 365 prennent en charge les documents chiffrés stockés dans SharePoint Online et OneDrive entreprise. Cela inclut les documents chiffrés à la suite d’étiquettes de sensibilité appliquées.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prises en charge

Les outils de découverte électronique Microsoft prennent en charge les éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies incluent le chiffrement de messages Office et Azure Rights Management. Pour plus d’informations sur les technologies de chiffrement Microsoft, consultez la rubrique [chiffrement](encryption.md). Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Il n’y a pas de prise en charge lors de l’aperçu ou de l’exportation de contenu chiffré avec des technologies non Microsoft.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>activités eDiscovery qui prennent en charge les éléments chiffrés

Le tableau suivant identifie les tâches effectuées dans les outils eDiscovery de Microsoft 365 qui prennent en charge le déchiffrement des fichiers chiffrés joints aux massages de messagerie. Les tâches de prise en charge peuvent être effectuées sur un fichier chiffré joint à un message électronique qui correspond aux critères d’une recherche. La valeur « N/A » indique que la fonction n’est pas disponible dans l’outil eDiscovery correspondant.

|tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés     |Oui      |Oui      |Oui      |
|Afficher un aperçu des fichiers chiffrés     |Oui      |Oui     |Oui       |
|Examiner les fichiers chiffrés dans un jeu de révision    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés    |Oui       |Oui  |Oui    |

## <a name="requirements-for-decryption-in-ediscovery"></a>Configuration requise pour le déchiffrement dans eDiscovery

Vous devez disposer du rôle déchiffrement RMS pour prévisualiser, examiner et exporter les fichiers joints chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger les pièces jointes chiffrées ajoutées à un jeu de réviseur dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de rôles gestionnaire de découverte électronique dans le centre de conformité Office 365 Security &. Pour plus d’informations sur le rôle de déchiffrement RMS, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).
