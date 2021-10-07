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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Microsoft 365 eDiscovery gèrent les documents chiffrés joints aux messages électroniques et stockés dans SharePoint Online et OneDrive Entreprise.
ms.openlocfilehash: 351a6c77d1fc0956c83661132f1111897896a724
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60159907"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils Microsoft 365 eDiscovery

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et des informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les bonnes personnes ont accès à ce contenu.

Pour exécuter des tâches eDiscovery courantes sur du contenu chiffré, les gestionnaires eDiscovery devait déchiffrer le contenu des messages électroniques lors de son exportation à partir de recherches de contenu, de cas eDiscovery principaux et de Advanced eDiscovery cas. Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible pour révision tant qu’il n’a pas été exporté.

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, les outils eDiscovery Microsoft 365 intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online. <sup>1</sup> En outre, les documents chiffrés stockés dans SharePoint Online et OneDrive Entreprise sont déchiffrés dans Advanced eDiscovery.

Avant cette nouvelle fonctionnalité, seul le contenu d’un message électronique protégé par la gestion des droits (et les fichiers non joints) était déchiffré. Les documents chiffrés SharePoint et OneDrive n’ont pas pu être déchiffrés pendant le flux de travail eDiscovery. À présent, les fichiers chiffrés à l’aide d’une technologie de chiffrement Microsoft se trouvent sur un compte SharePoint ou OneDrive et peuvent être recherchés et déchiffrés lorsque les résultats de la recherche sont préparés pour la prévisualisation, ajoutés à un groupe de révision dans Advanced eDiscovery et exportés. En outre, les documents chiffrés dans SharePoint et OneDrive joints à un message électronique peuvent faire l’être. Cette fonctionnalité de déchiffrement permet aux gestionnaires eDiscovery d’afficher le contenu des pièces jointes et des documents de site chiffrés lors de l’aperçu des résultats de la recherche, et de les examiner une fois qu’ils ont été ajoutés à un groupe de révision dans Advanced eDiscovery.

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prise en charge

Les outils eDiscovery de Microsoft permettent la prise en charge des éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies sont Azure Rights Management et Protection des données Microsoft (en particulier les étiquettes de sensibilité). Pour plus d’informations sur les technologies de chiffrement Microsoft, voir [Chiffrement.](encryption.md) Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies autres que Microsoft n’est pas prise en charge.

> [!NOTE]
> Le déchiffrement des messages électroniques envoyés avec un modèle de personnalisation [chiffrement de messages Office 365 (OME)](add-your-organization-brand-to-encrypted-messages.md) n’est pas pris en charge par les outils eDiscovery de Microsoft. Lorsque vous utilisez un modèle de personnalisation OME, les messages électroniques sont remis au portail OME au lieu de la boîte aux lettres du destinataire. Par conséquent, vous ne pourrez pas utiliser les outils eDiscovery pour rechercher des messages chiffrés par OME, car ces messages ne sont jamais reçus par la boîte aux lettres du destinataire.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Activités eDiscovery qui la prise en charge des éléments chiffrés

Le tableau suivant identifie les tâches prise en charge qui peuvent être effectuées dans les outils eDiscovery Microsoft 365 sur les fichiers chiffrés joints aux messages électroniques et aux documents chiffrés dans SharePoint et OneDrive. Ces tâches peuvent être effectuées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur `N/A` indique que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|Tâche eDiscovery  |Recherche de contenu  |Core eDiscovery  |Advanced eDiscovery  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés dans des sites et des pièces jointes de courrier<sup>électronique 1</sup>     |Non      |Non      |Oui      |
|Afficher un aperçu des fichiers chiffrés joints à la messagerie     |Oui      |Oui     |Oui       |
|Afficher un aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Passer en revue les fichiers chiffrés dans un jeu à réviser    |N/A      |N/A        | Oui        |
|Exporter des fichiers chiffrés joints à la messagerie électronique    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

> [!NOTE]
> <sup>1 Les</sup> fichiers chiffrés situés sur un ordinateur local et les pièces jointes cloud copiées dans un message électronique ne sont pas déchiffrées et indexées pour eDiscovery. Pour plus d’informations et une solution de contournement pour ces scénarios, voir la section Limitations de déchiffrement avec pièces [jointes](#decryption-limitations-with-email-attachments) dans cet article.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Limites de déchiffrement avec les étiquettes de niveau de SharePoint et OneDrive

eDiscovery ne prend pas en charge les fichiers chiffrés dans SharePoint et OneDrive lorsqu’une étiquette de sensibilité qui a appliqué le chiffrement est configurée avec l’un des paramètres suivants :

- Les utilisateurs peuvent attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à un document. Cela est parfois appelé autorisations *définies par l’utilisateur.*

- L’accès utilisateur au document a un paramètre d’expiration qui est définie sur une valeur autre que **Jamais**.

Pour plus d’informations sur ces paramètres, voir la section « Configurer les paramètres de chiffrement » dans Restreindre l’accès au contenu à l’aide d’étiquettes de niveau de sensibilité pour appliquer le [chiffrement.](encryption-sensitivity-labels.md#configure-encryption-settings)

Les documents chiffrés avec les paramètres précédents peuvent toujours être renvoyés par une recherche de découverte électronique. Cela peut se produire lorsqu’une propriété de document (telle que le titre, l’auteur ou la date de modification) correspond aux critères de recherche. Bien que ces documents soient inclus dans les résultats de la recherche, ils ne peuvent pas être prévisualiser ou révisés. Ces documents restent également chiffrés lorsqu’ils sont exportés Advanced eDiscovery.

## <a name="decryption-limitations-with-email-attachments"></a>Limites de déchiffrement avec pièces jointes de courrier électronique

Les scénarios suivants décrivent les limitations dans le déchiffrement des fichiers joints aux messages électroniques. Ces descriptions de scénario incluent également des solutions de contournement pour atténuer ces limitations.

- Si un fichier situé sur un ordinateur local (et non stocké dans un site SharePoint ou un compte OneDrive) est joint à un message électronique et qu’une étiquette de niveau de sensibilité qui applique le chiffrement est appliquée au message électronique, le fichier joint ne peut pas être déchiffré par eDiscovery. Cela signifie que si vous exécutez une requête de recherche par mot clé de la boîte aux lettres du destinataire, la pièce jointe chiffrée ne sera pas renvoyée par une requête de recherche par mot clé.

  La solution de contournement de cette limitation consiste à rechercher la même pièce jointe dans la boîte aux lettres de l’expéditeur. Cela est dû au fait que le chiffrement appliqué par l’étiquette de sensibilité est appliqué lors du transport du message électronique. Cela signifie que la pièce jointe est chiffrée lors de l’envoi du message électronique. Le résultat est que l’instance du fichier joint dans la boîte aux lettres de l’expéditeur n’est pas chiffrée, même si le même fichier dans la boîte aux lettres du destinataire est chiffré.

- De même, les pièces jointes cloud (fichiers stockés dans un site SharePoint ou un compte OneDrive)  qui sont copiées dans un message électronique (à l’aide de l’option Joindre en tant que copie dans Outlook) ne peuvent pas être déchiffrées par eDiscovery. Cela est également dû au fait que le chiffrement appliqué par une étiquette de niveau de sensibilité est appliqué lors de l’envoi du message électronique. La recherche de l’instance non chiffrée de la copie de la pièce jointe cloud dans la boîte aux lettres de l’expéditeur constitue également la solution de contournement de cette limitation.

Dans ces deux scénarios, les messages électroniques avec des pièces jointes chiffrées peuvent être renvoyés par une recherche de découverte électronique si une propriété de messagerie (telle qu’une date d’envoi, un expéditeur, un destinataire ou un objet) correspond à la requête de recherche.

## <a name="requirements-for-decryption-in-ediscovery"></a>Conditions requises pour le déchiffrement dans eDiscovery

Le rôle de déchiffrement RMS doit vous être attribué pour prévisualiser, examiner et exporter des fichiers chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour examiner et interroger les fichiers chiffrés qui sont ajoutés à un jeu à réviser dans Advanced eDiscovery.

Ce rôle est attribué par défaut au groupe de rôles Gestionnaire eDiscovery dans la page **Autorisations** du Centre de conformité Microsoft 365. Pour plus d’informations sur le rôle de déchiffrement RMS, voir [Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-core-ediscovery"></a>Déchiffrement des messages électroniques protégés par RMS et des pièces jointes chiffrées à l’aide de la recherche de contenu ou de la découverte électronique principale

Tous les messages électroniques protégés par des droits (protégés par RMS) inclus dans les résultats d’une recherche de contenu sont déchiffrés lorsque vous les exportez. En outre, tout fichier chiffré avec une technologie de chiffrement [Microsoft](encryption.md) et joint à un message électronique inclus dans les résultats de la recherche est déchiffré lorsqu’il est exporté. Cette fonctionnalité de déchiffrement est activée par défaut pour les membres du groupe de rôles Gestionnaire eDiscovery. Cela est dû au fait que le rôle de gestion déchiffrement RMS est attribué par défaut à ce groupe de rôles. Gardez les points suivants à l’esprit lors de l’exportation de pièces jointes et de messages électroniques chiffrés :
  
- Comme indiqué précédemment, pour déchiffrer les messages protégés par RMS lorsque vous les exportez, vous devez exporter les résultats de la recherche en tant que messages individuels. Si vous exportez des résultats de recherche dans un fichier PST, les messages protégés par RMS restent chiffrés.

- Les messages déchiffrés sont identifiés dans le **rapport ResultsLog.** Ce rapport contient une colonne nommée **État** de décodage et une valeur décodée **identifie** les messages qui ont été déchiffrés.

- Outre le déchiffrement des pièces jointes lors de l’exportation des résultats de recherche, vous pouvez afficher un aperçu du fichier déchiffré lors de l’aperçu des résultats de recherche. Vous pouvez uniquement afficher le message électronique protégé par des droits après l’avoir exporté.

- Si vous devez empêcher quelqu’un de déchiffrer les messages protégés par RMS et les pièces jointes chiffrées, vous devez créer un groupe de rôles personnalisé (en copiant le groupe de rôles gestionnaire eDiscovery intégré), puis supprimer le rôle de gestion déchiffrement RMS du groupe de rôles personnalisé. Ajoutez ensuite la personne qui ne doit pas déchiffrer les messages en tant que membre du groupe de rôles personnalisé.
