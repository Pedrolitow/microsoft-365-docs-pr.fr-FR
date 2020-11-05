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
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment les outils eDiscovery de Microsoft 365 gèrent les documents chiffrés joints aux messages électroniques.
ms.openlocfilehash: 89e6457015289055c56278f5f8650ce022ecf081
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920705"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils eDiscovery de Microsoft 365

Les organisations utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les personnes appropriées ont accès à ce contenu. Les organisations utilisent différents types de chiffrement, les technologies de chiffrement Microsoft et les technologies tierces pour répondre à leurs besoins en matière de sécurité et protéger leurs informations sensibles.

À ce jour, la gestion du contenu chiffré dans le flux de travail de découverte électronique dans Microsoft 365 nécessite un traitement spécial des éléments chiffrés en fonction du type de chiffrement utilisé et de l’étape spécifique dans le flux de travail. Ceci était principalement réalisé en déchiffrant le contenu des messages électroniques lorsqu’il a été exporté à partir de recherches de contenu, de cas de découverte électronique principaux et de cas de découverte électronique avancée. Le contenu chiffré avec les technologies de chiffrement Microsoft n’a pas pu être prévisualisé tant qu’il n’a pas été exporté. Dans Advanced eDiscovery, le contenu chiffré a été signalé par une erreur de traitement, qui a nécessité de télécharger l’élément chiffré, de le déchiffrer, puis de télécharger le fichier déchiffré dans un jeu de révision.

Pour faciliter la gestion du contenu chiffré dans le flux de travail de découverte électronique, les outils eDiscovery de Microsoft 365 peuvent déchiffrer les fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. Avant cette nouvelle capacité, seul le contenu d’un message électronique protégé par la gestion des droits (et non les fichiers joints) a été déchiffré. À présent, si un fichier chiffré avec une technologie de chiffrement Microsoft est joint à un message électronique qui correspond aux critères de recherche, le fichier chiffré est déchiffré lorsque les résultats de la recherche sont préparés pour l’aperçu. Cela permet aux gestionnaires eDiscovery d’afficher le contenu des pièces jointes chiffrées lors de l’aperçu des résultats de la recherche.

> [!NOTE]
> À partir du 1er janvier 2021, les outils eDiscovery de Microsoft 365 prennent en charge les documents chiffrés stockés dans SharePoint Online et OneDrive entreprise.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prises en charge

Les outils de découverte électronique Microsoft prennent en charge les éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies incluent le chiffrement de messages Office, la protection des informations Microsoft (étiquettes de confidentialité) et Azure Rights Management. Pour plus d’informations sur les technologies de chiffrement Microsoft, consultez la rubrique [chiffrement](encryption.md). Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Il n’y a pas de prise en charge lors de l’aperçu ou de l’exportation de contenu chiffré avec des technologies non Microsoft.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>activités eDiscovery qui prennent en charge les éléments chiffrés

Le tableau suivant identifie les tâches effectuées dans les outils eDiscovery de Microsoft 365 qui prennent en charge le déchiffrement des fichiers chiffrés joints aux massages de messagerie. Les tâches de prise en charge peuvent être effectuées sur un fichier chiffré joint à un message électronique qui correspond aux critères d’une recherche. La valeur « N/A » indique que la fonction n’est pas disponible dans l’outil eDiscovery correspondant.

|tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés     |Non      |Non      |Non      |
|Afficher un aperçu des fichiers chiffrés     |Oui      |Oui     |Oui       |
|Examiner les fichiers chiffrés dans un jeu de révision    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés    |Oui       |Oui  |Oui    |

## <a name="requirements-for-decryption-in-ediscovery"></a>Configuration requise pour le déchiffrement dans eDiscovery

Vous devez disposer du rôle déchiffrement RMS pour prévisualiser, examiner et exporter les fichiers joints chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger les pièces jointes chiffrées ajoutées à un jeu de réviseur dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de rôles gestionnaire de découverte électronique dans le centre de conformité Office 365 Security &. Pour plus d’informations sur le rôle de déchiffrement RMS, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).
