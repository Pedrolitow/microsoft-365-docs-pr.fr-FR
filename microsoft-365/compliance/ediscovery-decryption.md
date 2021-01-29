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
description: Découvrez comment les outils eDiscovery de Microsoft 365 gèrent les documents chiffrés joints aux messages électroniques et stockés dans SharePoint Online et OneDrive Entreprise.
ms.openlocfilehash: aeb1d927a5da24c55838fe3379451956949d8b4f
ms.sourcegitcommit: 1b30ac6e05906c8a014b1fed33fc71e1821f6ad2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "50044766"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils eDiscovery de Microsoft 365

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les bonnes personnes ont accès à ce contenu.

Pour exécuter des tâches eDiscovery courantes sur du contenu chiffré, les gestionnaires eDiscovery devait déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, de cas eDiscovery principaux et de cas Advanced eDiscovery. Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible pour révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, les outils de découverte électronique Microsoft 365 intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. En outre, les documents chiffrés stockés dans SharePoint Online et OneDrive Entreprise sont déchiffrés dans Advanced eDiscovery. 

Avant cette nouvelle fonctionnalité, seul le contenu d’un message électronique protégé par la gestion des droits (et les fichiers non joints) était déchiffré. Les documents chiffrés dans SharePoint et OneDrive n’ont pas pu être déchiffrés pendant le flux de travail eDiscovery. Maintenant, si un fichier chiffré avec une technologie de chiffrement Microsoft est joint à un message électronique ou situé sur un compte SharePoint ou OneDrive, ces éléments chiffrés sont déchiffrés lorsque les résultats de la recherche sont préparés pour la prévisualisation, ajoutés à un groupe de révision dans Advanced eDiscovery et exportés. Cela permet aux gestionnaires eDiscovery d’afficher le contenu des pièces jointes et des documents de site chiffrés lors de l’aperçu des résultats de la recherche, et de les examiner une fois qu’ils ont été ajoutés à un groupe de révision dans Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prise en charge

Les outils eDiscovery de Microsoft permettent la prise en charge des éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies incluent le chiffrement de messages Office, Azure Rights Management et Microsoft Information Protection (en particulier les étiquettes de sensibilité). Pour plus d’informations sur les technologies de chiffrement Microsoft, voir [Chiffrement.](encryption.md) Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies autres que Microsoft n’est pas prise en charge.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Activités eDiscovery qui la prise en charge des éléments chiffrés

Le tableau suivant identifie les tâches prise en charge qui peuvent être effectuées dans les outils eDiscovery Microsoft 365 sur les fichiers chiffrés joints à des courriers électroniques et des documents chiffrés dans SharePoint et OneDrive. Ces tâches peuvent être effectuées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur `N/A` indique que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|Tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés dans les e-mails et les sites     |Oui      |Oui      |Oui      |
|Afficher un aperçu des fichiers chiffrés joints à la messagerie     |Oui      |Oui     |Oui       |
|Afficher un aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Passer en revue les fichiers chiffrés dans un jeu à réviser    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés joints à un e-mail    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

**Remarque :** eDiscovery ne prend pas en charge les fichiers chiffrés dans SharePoint et OneDrive lorsqu’une étiquette de sensibilité qui a appliqué le chiffrement est configurée avec l’un des paramètres suivants :

- Les utilisateurs peuvent attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à un document. Cela est parfois appelé autorisations *définies par l’utilisateur.*<br/>

- L’accès utilisateur au document a un paramètre d’expiration qui est définie sur une valeur autre que **Jamais**.

Pour plus d’informations sur ces paramètres, voir la section « Configurer les paramètres de chiffrement » dans Restreindre l’accès au contenu à l’aide d’étiquettes de niveau de sensibilité pour appliquer le [chiffrement.](encryption-sensitivity-labels.md#configure-encryption-settings)

Les documents chiffrés avec les paramètres précédents peuvent toujours être renvoyés par une recherche de découverte électronique. Cela peut se produire lorsqu’une propriété de document (telle que le titre, l’auteur ou la date de modification) correspond aux critères de recherche. Bien que ces documents soient inclus dans les résultats de la recherche, ils ne peuvent pas être prévisualiser ou révisés. Ces documents restent également chiffrés lorsqu’ils sont exportés dans Advanced eDiscovery.

## <a name="requirements-for-decryption-in-ediscovery"></a>Conditions requises pour le déchiffrement dans eDiscovery

Le rôle de déchiffrement RMS doit vous être attribué pour prévisualiser, examiner et exporter des fichiers chiffrés avec les technologies de chiffrement Microsoft. Vous devez également avoir ce rôle pour examiner et interroger les fichiers chiffrés qui sont ajoutés à un jeu à réviser dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de **rôles** Gestionnaire eDiscovery dans la page Autorisations du Centre de sécurité et conformité Office 365 &. Pour plus d’informations sur le rôle de déchiffrement RMS, voir [Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).
