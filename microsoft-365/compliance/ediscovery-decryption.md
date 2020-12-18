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
description: Découvrez comment les outils eDiscovery de Microsoft 365 gèrent les documents chiffrés joints aux messages électroniques et stockés dans SharePoint Online et OneDrive entreprise.
ms.openlocfilehash: df2ff218e5c62e103661889fc8c66950a4d25cab
ms.sourcegitcommit: 6759e619c45a5f8e775ad456a5dfb18c08f13f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "49713265"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils eDiscovery de Microsoft 365

Le chiffrement est une partie importante de votre stratégie de protection des informations et de protection des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et garantir que seules les personnes appropriées ont accès à ce contenu.

Pour exécuter des tâches eDiscovery communes sur du contenu chiffré, les gestionnaires eDiscovery ont été tenus de déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, de cas de découverte électronique principaux et de cas avancés de découverte électronique. Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible à des fins de révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail de découverte électronique, les outils eDiscovery de Microsoft 365 incorporent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. En outre, les documents chiffrés stockés dans SharePoint Online et OneDrive entreprise sont déchiffrés dans Advanced eDiscovery. 

Avant cette nouvelle capacité, seul le contenu d’un message électronique protégé par la gestion des droits (et non les fichiers attachés) a été déchiffré. Les documents chiffrés dans SharePoint et OneDrive n’ont pas pu être déchiffrés au cours du flux de travail de découverte électronique. À présent, si un fichier chiffré avec une technologie de chiffrement Microsoft est joint à un message électronique ou se trouvant sur un compte SharePoint ou OneDrive, ces éléments chiffrés sont déchiffrés lorsque les résultats de la recherche sont préparés pour l’aperçu, ajoutés à un ensemble de révision dans Advanced eDiscovery et exportés. Cela permet aux gestionnaires de découverte électronique d’afficher le contenu des pièces jointes et des documents de sites chiffrés lors de la prévisualisation des résultats de recherche, et de les examiner une fois qu’ils ont été ajoutés à un jeu de révisions dans Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prises en charge

Les outils de découverte électronique Microsoft prennent en charge les éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies incluent le chiffrement de messages Office, Azure Rights Management et Microsoft information protection (en particulier, les étiquettes de confidentialité). Pour plus d’informations sur les technologies de chiffrement Microsoft, consultez la rubrique [chiffrement](encryption.md). Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies non Microsoft ne sont pas pris en charge.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>activités eDiscovery qui prennent en charge les éléments chiffrés

Le tableau suivant identifie les tâches prises en charge pouvant être effectuées dans les outils eDiscovery de Microsoft 365 sur des fichiers chiffrés associés à des massages de messagerie et à des documents chiffrés dans SharePoint et OneDrive. Ces tâches prises en charge peuvent être exécutées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur « N/A » indique que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés dans des courriers électroniques et des sites     |Oui      |Oui      |Oui      |
|Afficher un aperçu des fichiers chiffrés joints au courrier électronique     |Oui      |Oui     |Oui       |
|Aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Examiner les fichiers chiffrés dans un jeu de révision    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés joints à un message électronique    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

## <a name="requirements-for-decryption-in-ediscovery"></a>Configuration requise pour le déchiffrement dans eDiscovery

Le rôle déchiffrement RMS doit vous être attribué pour prévisualiser, examiner et exporter les fichiers chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger des fichiers chiffrés ajoutés à un jeu de réexamen dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de rôles gestionnaire de découverte électronique sur la page **autorisations** dans le centre de conformité Office 365 Security &. Pour plus d’informations sur le rôle de déchiffrement RMS, consultez la rubrique [attribution d’autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).
