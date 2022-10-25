---
title: Déchiffrement dans les outils Microsoft Purview eDiscovery
description: Découvrez comment les outils eDiscovery microsoft 365 gèrent les documents chiffrés joints aux messages électroniques et stockés dans SharePoint Online et OneDrive Entreprise.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
ms.openlocfilehash: 4e4405290f4fbd4965ac3c37afa98390272cd7c2
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688617"
---
# <a name="decryption-in-microsoft-purview-ediscovery-tools"></a>Déchiffrement dans les outils Microsoft Purview eDiscovery

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et de protection des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les personnes appropriées ont accès à ce contenu.

Pour exécuter des tâches eDiscovery courantes sur du contenu chiffré, les responsables eDiscovery devaient déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, Microsoft Purview eDiscovery cas (Standard) et Microsoft Purview eDiscovery cas (Premium). Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible pour révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, Microsoft Purview eDiscovery outils intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online.<sup> 1</sup> En outre, les documents chiffrés stockés dans SharePoint Online et OneDrive Entreprise sont déchiffrés dans eDiscovery (Premium)<sup>2</sup>.

Avant cette nouvelle fonctionnalité, seul le contenu d’un e-mail protégé par la gestion des droits (et non les fichiers joints) était déchiffré. Les documents chiffrés dans SharePoint et OneDrive n’ont pas pu être déchiffrés pendant le flux de travail eDiscovery. Désormais, les fichiers chiffrés avec une technologie de chiffrement Microsoft se trouvent sur un compte SharePoint ou OneDrive sont consultables et déchiffrés lorsque les résultats de la recherche sont préparés pour la préversion, ajoutés à un jeu de révision dans eDiscovery (Premium) et exportés. En outre, les documents chiffrés dans SharePoint et OneDrive qui sont joints à un e-mail (sous forme de copie) peuvent faire l’objet d’une recherche. Cette fonctionnalité de déchiffrement permet aux gestionnaires eDiscovery d’afficher le contenu des pièces jointes et des documents de site chiffrés lors de l’aperçu des résultats de la recherche, et de les examiner une fois qu’ils ont été ajoutés à un jeu de révision dans eDiscovery (Premium).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prises en charge

Pour Exchange, les outils Microsoft Purview eDiscovery prennent en charge les éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies sont Azure Rights Management (Azure RMS)<sup>3</sup> et Protection des données Microsoft Purview (en particulier les étiquettes de confidentialité). Pour plus d’informations sur les technologies de chiffrement Microsoft, consultez [Chiffrement](encryption.md) et les différentes options de [chiffrement de courrier](email-encryption.md#comparing-email-encryption-options-available-in-office-365) électronique disponibles. Le contenu chiffré par S/MIME ou des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies non-Microsoft n’est pas pris en charge.

> [!NOTE]
> Le déchiffrement des messages électroniques envoyés avec un [modèle de personnalisation Chiffrement de messages Microsoft Purview personnalisé](add-your-organization-brand-to-encrypted-messages.md) n’est pas pris en charge par les outils Microsoft eDiscovery. Lorsque vous utilisez un modèle de personnalisation OME, les messages électroniques sont remis au portail OME au lieu de la boîte aux lettres du destinataire. Par conséquent, vous ne pourrez pas utiliser les outils eDiscovery pour rechercher des messages chiffrés, car ces messages ne sont jamais reçus par la boîte aux lettres du destinataire.

Pour SharePoint, le contenu étiqueté avec le service En ligne SharePoint sera déchiffré. Les éléments étiquetés ou chiffrés dans le client avant le chargement sur SharePoint, les modèles ou paramètres RMS hérités de la bibliothèque de documents et S/MIME ou d’autres normes ne sont pas pris en charge<sup>2</sup>.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Activités eDiscovery qui prennent en charge les éléments chiffrés

Le tableau suivant identifie les tâches prises en charge qui peuvent être effectuées dans les outils eDiscovery Microsoft 365 sur les fichiers chiffrés joints à des messages électroniques et des documents chiffrés dans SharePoint et OneDrive. Ces tâches prises en charge peuvent être effectuées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur indique `N/A` que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|Tâche eDiscovery  |Recherche de contenu  |eDiscovery (Standard)  |eDiscovery (Premium)  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés dans des sites et des pièces jointes d’e-mail<sup>1</sup>     |Non      |Non      |Oui      |
|Afficher un aperçu des fichiers chiffrés joints à un e-mail     |Oui      |Oui     |Oui       |
|Afficher un aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Examiner les fichiers chiffrés dans un jeu de révision    |S/O      |N/A        | Oui        |
|Exporter des fichiers chiffrés joints à un e-mail    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Limitations du déchiffrement avec des étiquettes de confidentialité dans SharePoint et OneDrive

eDiscovery ne prend pas en charge les fichiers chiffrés dans SharePoint et OneDrive lorsqu’une étiquette de confidentialité qui a appliqué le chiffrement est configurée avec l’un des paramètres suivants :

- Les utilisateurs peuvent attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à un document. Il s’agit parfois *d’autorisations définies par l’utilisateur*.
- L’accès utilisateur au document a un paramètre d’expiration défini sur une valeur autre que **Jamais**.

Pour plus d’informations sur ces paramètres, consultez la section « Configurer les paramètres de chiffrement » dans [Restreindre l’accès au contenu à l’aide d’étiquettes de confidentialité pour appliquer le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings).

Les documents chiffrés avec les paramètres précédents peuvent toujours être retournés par une recherche eDiscovery. Cela peut se produire lorsqu’une propriété de document (telle que le titre, l’auteur ou la date de modification) correspond aux critères de recherche. Bien que ces documents puissent être inclus dans les résultats de recherche, ils ne peuvent pas être prévisualisés ou révisés. Ces documents restent également chiffrés lorsqu’ils sont exportés dans eDiscovery (Premium).

> [!IMPORTANT]
> Le déchiffrement n’est pas pris en charge pour les fichiers qui sont chiffrés localement, puis chargés sur SharePoint ou OneDrive. Par exemple, les fichiers locaux chiffrés par le client Azure Information Protection (AIP) puis chargés sur Microsoft 365 ne sont pas pris en charge. Seuls les fichiers chiffrés dans le service SharePoint ou OneDrive sont pris en charge pour le déchiffrement.

## <a name="requirements-for-decryption-in-ediscovery"></a>Conditions requises pour le déchiffrement dans eDiscovery

Le rôle Decrypt RMS doit vous être attribué pour afficher un aperçu, examiner et exporter des fichiers chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger les fichiers chiffrés qui sont ajoutés à un jeu de révision dans eDiscovery (Premium).

Ce rôle est attribué par défaut au groupe de rôles Gestionnaire eDiscovery dans la page **Autorisations** du portail de conformité Microsoft Purview. Pour plus d’informations sur le rôle Decrypt RMS, consultez [Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées à l’aide de la recherche de contenu ou d’eDiscovery (Standard)

Tous les messages électroniques protégés par des droits (protégés par RMS) inclus dans les résultats d’une recherche de contenu seront déchiffrés lorsque vous les exporterez. En outre, tout fichier chiffré avec une [technologie de chiffrement Microsoft](encryption.md) et joint à un message électronique inclus dans les résultats de la recherche sera déchiffré lors de son exportation. Cette fonctionnalité de déchiffrement est activée par défaut pour les membres du groupe de rôles Gestionnaire eDiscovery. Cela est dû au fait que le rôle de gestion de déchiffrement RMS est attribué à ce groupe de rôles par défaut. Gardez les éléments suivants à l’esprit lors de l’exportation de messages électroniques et de pièces jointes chiffrés :
  
- Comme expliqué précédemment, si vous activez le déchiffrement des messages protégés par RMS lorsque vous les exportez, vous devez exporter les résultats de la recherche en tant que messages individuels. Si vous exportez les résultats de la recherche vers un fichier PST, les messages protégés par RMS sont exportés en tant que messages électroniques individuels.
- Les messages déchiffrés sont identifiés dans le rapport **ResultsLog** . Ce rapport contient une colonne nommée **État du décodage**, et une valeur **Décodé** identifie les messages qui ont été déchiffrés.
- Outre le déchiffrement des pièces jointes lors de l’exportation des résultats de recherche, vous pouvez également afficher un aperçu du fichier déchiffré lors de l’aperçu des résultats de la recherche. Vous ne pouvez afficher le message électronique protégé par des droits qu’après l’avoir exporté.
- Si vous devez empêcher une personne de déchiffrer les messages rms-protect et les pièces jointes chiffrées, vous devez créer un groupe de rôles personnalisé (en copiant le groupe de rôles eDiscovery Manager intégré), puis supprimer le rôle de gestion de déchiffrement RMS du groupe de rôles personnalisé. Ajoutez ensuite la personne que vous ne souhaitez pas déchiffrer les messages en tant que membre du groupe de rôles personnalisé.

## <a name="notes"></a>Remarques

<sup>1</sup> Les fichiers chiffrés situés sur un ordinateur local et copiés dans un e-mail ne sont pas déchiffrés et indexés pour eDiscovery. Pour eDiscovery (Premium), les e-mails chiffrés et les pièces jointes dans la boîte aux lettres du destinataire doivent être indexés pour être déchiffrés. Pour plus d’informations sur l’indexation avancée, consultez [Indexation avancée des données du consignataire](indexing-custodian-data.md).

<sup>2</sup> Seuls les éléments étiquetés dans le service SharePoint Online seront déchiffrés, tout le reste n’est pas pris en charge, y compris l’étiquetage ou le chiffrement dans le client avant le chargement, les modèles ou paramètres RMS hérités de la bibliothèque de documents, SMIME ou toute autre norme, etc. Voir [Activer les étiquettes de confidentialité pour les fichiers Office](sensitivity-labels-sharepoint-onedrive-files.md).

<sup>3</sup> Les clés RMS doivent être entièrement gérées dans le service cloud M365/O365, ce qui signifie que DKE, BYOK, RMS local, etc. ne sont pas pris en charge. Consultez [Votre clé de locataire Azure Information Protection](/azure/information-protection/plan-implement-tenant-key#tenant-root-keys-generated-by-microsoft).
