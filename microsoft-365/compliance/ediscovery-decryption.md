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
description: Découvrez comment Microsoft 365 eDiscovery gèrent les documents chiffrés joints aux messages électroniques et stockés dans SharePoint Online et OneDrive Entreprise.
ms.openlocfilehash: e03f5813fcd5f232119f3586cd173c40ca846cc7a7cb6908b5b71fab8e26361c
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53842290"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils Microsoft 365 eDiscovery

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les bonnes personnes ont accès à ce contenu.

Pour exécuter des tâches eDiscovery courantes sur du contenu chiffré, les gestionnaires eDiscovery devait déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, de cas eDiscovery principaux et de Advanced eDiscovery cas. Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible pour révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, les outils eDiscovery Microsoft 365 intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. <sup>1</sup> En outre, les documents chiffrés stockés dans SharePoint Online et OneDrive Entreprise sont déchiffrés dans Advanced eDiscovery.

Avant cette nouvelle fonctionnalité, seul le contenu d’un message électronique protégé par la gestion des droits (et les fichiers non joints) était déchiffré. Les documents chiffrés SharePoint et OneDrive n’ont pas pu être déchiffrés pendant le flux de travail eDiscovery. À présent, les fichiers chiffrés à l’aide d’une technologie de chiffrement Microsoft se trouvent sur un compte SharePoint ou OneDrive et peuvent être recherchés et déchiffrés lorsque les résultats de la recherche sont préparés pour la prévisualisation, ajoutés à un jeu à réviser dans Advanced eDiscovery et exportés. En outre, les documents chiffrés dans SharePoint et OneDrive joints à un message électronique peuvent faire l’être. Cette fonctionnalité de déchiffrement permet aux gestionnaires eDiscovery d’afficher le contenu des pièces jointes et des documents de site chiffrés lors de l’aperçu des résultats de la recherche, et de les examiner après leur ajout à un groupe de révision dans Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prise en charge

Les outils eDiscovery de Microsoft permettent la prise en charge des éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies sont Azure Rights Management et Protection des données Microsoft (en particulier les étiquettes de sensibilité). Pour plus d’informations sur les technologies de chiffrement Microsoft, voir [Chiffrement.](encryption.md) Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies autres que Microsoft n’est pas prise en charge.

> [!NOTE]
> Le déchiffrement des messages électroniques chiffrés avec chiffrement de messages Office 365 (OME) n’est pas pris en charge par les outils eDiscovery de Microsoft.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Activités eDiscovery qui la prise en charge des éléments chiffrés

Le tableau suivant identifie les tâches prise en charge qui peuvent être effectuées dans les outils eDiscovery Microsoft 365 sur les fichiers chiffrés joints aux messages électroniques et aux documents chiffrés dans SharePoint et OneDrive. Ces tâches prise en charge peuvent être effectuées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur `N/A` indique que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|Tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans les fichiers chiffrés dans le courrier électronique et les sites<sup>1</sup>     |Oui      |Oui      |Oui      |
|Afficher un aperçu des fichiers chiffrés joints à la messagerie     |Oui      |Oui     |Oui       |
|Afficher un aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Passer en revue les fichiers chiffrés dans un jeu à réviser    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés joints à la messagerie électronique    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

> [!NOTE]
> <sup>1</sup> Les fichiers chiffrés qui se trouvent sur un ordinateur local (et qui ne sont pas stockés sur un site SharePoint ou OneDrive) ne sont pas indexés pour eDiscovery. Cela signifie que si un fichier local chiffré est joint à un message électronique, le fichier ne sera pas renvoyé par une requête de recherche par mot clé, même si le fichier contient des mots clés qui correspondent à la requête de recherche. Toutefois, les messages électroniques avec un fichier chiffré local peuvent être renvoyés par une recherche de découverte électronique si une propriété de messagerie (telle qu’une date d’envoi, un expéditeur, un destinataire ou un objet) correspond à la requête de recherche.

### <a name="decryption-limitations-with-sensitivity-labels"></a>Limites de déchiffrement avec les étiquettes de sensibilité

eDiscovery ne prend pas en charge les fichiers chiffrés dans SharePoint et OneDrive lorsqu’une étiquette de sensibilité qui a appliqué le chiffrement est configurée avec l’un des paramètres suivants :

- Les utilisateurs peuvent attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à un document. Cela est parfois appelé autorisations *définies par l’utilisateur.*

- L’accès utilisateur au document a un paramètre d’expiration qui est définie sur une valeur autre que **Jamais**.

Pour plus d’informations sur ces paramètres, voir la section « Configurer les paramètres de chiffrement » dans Restreindre l’accès au contenu à l’aide d’étiquettes de niveau de sensibilité pour appliquer le [chiffrement.](encryption-sensitivity-labels.md#configure-encryption-settings)

Les documents chiffrés avec les paramètres précédents peuvent toujours être renvoyés par une recherche de découverte électronique. Cela peut se produire lorsqu’une propriété de document (telle que le titre, l’auteur ou la date de modification) correspond aux critères de recherche. Bien que ces documents soient inclus dans les résultats de la recherche, ils ne peuvent pas être prévisualiser ou révisés. Ces documents restent également chiffrés lorsqu’ils sont exportés Advanced eDiscovery.

## <a name="requirements-for-decryption-in-ediscovery"></a>Conditions requises pour le déchiffrement dans eDiscovery

Le rôle de déchiffrement RMS doit vous être attribué pour prévisualiser, examiner et exporter des fichiers chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger les fichiers chiffrés qui sont ajoutés à un jeu à réviser dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de **rôles** Gestionnaire eDiscovery dans la page Autorisations du Centre de sécurité & conformité Office 365. Pour plus d’informations sur le rôle de déchiffrement RMS, voir [Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).
