---
title: Déchiffrement dans eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment les outils microsoft 365 eDiscovery gèrent les documents chiffrés attachés aux e-mails et stockés dans SharePoint Online et OneDrive Entreprise.
ms.openlocfilehash: 689ac5420c3d9110a51586d8f008416363aafeec
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626312"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>Déchiffrement dans les outils microsoft 365 eDiscovery

Le chiffrement est une partie importante de votre stratégie de protection des fichiers et d’informations. Les organisations de tous types utilisent la technologie de chiffrement pour protéger le contenu sensible au sein de leur organisation et s’assurer que seules les bonnes personnes ont accès à ce contenu.

Pour exécuter des tâches eDiscovery courantes sur du contenu chiffré, les responsables eDiscovery devaient déchiffrer le contenu des messages électroniques, car il était exporté à partir de recherches de contenu, de cas Microsoft Purview eDiscovery (Standard) et de cas Microsoft Purview eDiscovery (Premium). Le contenu chiffré avec les technologies de chiffrement Microsoft n’était pas disponible pour révision avant son exportation.

Pour faciliter la gestion du contenu chiffré dans le flux de travail eDiscovery, les outils eDiscovery de Microsoft 365 intègrent désormais le déchiffrement des fichiers chiffrés joints aux messages électroniques et envoyés dans Exchange Online.<sup> 1</sup> En outre, les documents chiffrés stockés dans SharePoint Online et les OneDrive Entreprise sont déchiffrés dans eDiscovery (Premium).

Avant cette nouvelle fonctionnalité, seul le contenu d’un e-mail protégé par la gestion des droits (et non les fichiers attachés) était déchiffré. Les documents chiffrés dans SharePoint et OneDrive n’ont pas pu être déchiffrés pendant le flux de travail eDiscovery. À présent, les fichiers chiffrés à l’aide d’une technologie de chiffrement Microsoft se trouvent sur un compte SharePoint ou OneDrive sont consultables et déchiffrés lorsque les résultats de la recherche sont préparés pour la préversion, ajoutés à un ensemble de révisions dans eDiscovery (Premium) et exportés. En outre, les documents chiffrés dans SharePoint et OneDrive qui sont joints à un e-mail peuvent faire l’objet d’une recherche. Cette fonctionnalité de déchiffrement permet aux responsables eDiscovery d’afficher le contenu des pièces jointes et des documents de site chiffrés lors de l’aperçu des résultats de la recherche, et de les examiner après qu’ils ont été ajoutés à un ensemble de révisions dans eDiscovery (Premium).

## <a name="supported-encryption-technologies"></a>Technologies de chiffrement prises en charge

Les outils Microsoft eDiscovery prennent en charge les éléments chiffrés avec les technologies de chiffrement Microsoft. Ces technologies sont Azure Rights Management et Protection des données Microsoft Purview (en particulier les étiquettes de confidentialité). Pour plus d’informations sur les technologies de chiffrement Microsoft, consultez [Chiffrement](encryption.md). Le contenu chiffré par des technologies de chiffrement tierces n’est pas pris en charge. Par exemple, l’aperçu ou l’exportation de contenu chiffré avec des technologies non Microsoft n’est pas pris en charge.

> [!NOTE]
> Le déchiffrement des messages électroniques envoyés avec un [modèle de personnalisation Chiffrement de messages Microsoft Purview personnalisé](add-your-organization-brand-to-encrypted-messages.md) n’est pas pris en charge par les outils Microsoft eDiscovery. Lorsque vous utilisez un modèle de personnalisation OME, les messages électroniques sont remis au portail OME au lieu de la boîte aux lettres du destinataire. Par conséquent, vous ne pourrez pas utiliser les outils eDiscovery pour rechercher des messages chiffrés, car ces messages ne sont jamais reçus par la boîte aux lettres du destinataire.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Activités eDiscovery qui prennent en charge les éléments chiffrés

Le tableau suivant identifie les tâches prises en charge qui peuvent être effectuées dans les outils microsoft 365 eDiscovery sur les fichiers chiffrés joints aux messages électroniques et aux documents chiffrés dans SharePoint et OneDrive. Ces tâches prises en charge peuvent être effectuées sur des fichiers chiffrés qui correspondent aux critères d’une recherche. La valeur indique `N/A` que la fonctionnalité n’est pas disponible dans l’outil eDiscovery correspondant.

|Tâche eDiscovery  |Recherche de contenu  |eDiscovery (Standard)  |eDiscovery (Premium)  |
|:---------|:---------|:---------|:---------|
|Rechercher du contenu dans des fichiers chiffrés dans des sites et des pièces jointes<sup>de courrier 1</sup>     |Non      |Non      |Oui      |
|Aperçu des fichiers chiffrés attachés à un e-mail     |Oui      |Oui     |Oui       |
|Aperçu des documents chiffrés dans SharePoint et OneDrive|Non      |Non    |Oui       |
|Passer en revue les fichiers chiffrés dans un ensemble de révisions    |N/A      |N/A        | Oui        |
|Exporter les fichiers chiffrés attachés à l’e-mail    |Oui       |Oui  |Oui    |
|Exporter des documents chiffrés dans SharePoint et OneDrive    |Non       |Non  |Oui    |
|||||

> [!NOTE]
> <sup>1 Les</sup> fichiers chiffrés situés sur un ordinateur local et les pièces jointes cloud copiées dans un e-mail ne sont pas déchiffrés et indexés pour eDiscovery. Pour plus d’informations et une solution de contournement pour ces scénarios, consultez la section [Sur les limitations de déchiffrement avec les pièces jointes](#decryption-limitations-with-email-attachments) dans cet article.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>Limitations de déchiffrement avec les étiquettes de confidentialité dans SharePoint et OneDrive

eDiscovery ne prend pas en charge les fichiers chiffrés dans SharePoint et OneDrive lorsqu’une étiquette de confidentialité qui a appliqué le chiffrement est configurée avec l’un des paramètres suivants :

- Les utilisateurs peuvent attribuer des autorisations lorsqu’ils appliquent manuellement l’étiquette à un document. Il s’agit parfois *d’autorisations définies par l’utilisateur*.

- L’accès utilisateur au document a un paramètre d’expiration défini sur une valeur autre que **Jamais**.

Pour plus d’informations sur ces paramètres, consultez la section « Configurer les paramètres de chiffrement » dans [Restreindre l’accès au contenu à l’aide d’étiquettes de confidentialité pour appliquer le chiffrement](encryption-sensitivity-labels.md#configure-encryption-settings).

Les documents chiffrés avec les paramètres précédents peuvent toujours être retournés par une recherche eDiscovery. Cela peut se produire lorsqu’une propriété de document (par exemple, le titre, l’auteur ou la date de modification) correspond aux critères de recherche. Bien que ces documents puissent être inclus dans les résultats de la recherche, ils ne peuvent pas être prévisualisés ou révisés. Ces documents restent également chiffrés lorsqu’ils sont exportés dans eDiscovery (Premium).

> [!IMPORTANT]
> Le déchiffrement n’est pas pris en charge pour les fichiers chiffrés localement, puis chargés sur SharePoint ou OneDrive. Par exemple, les fichiers locaux chiffrés par le client Azure Information Protection (AIP), puis chargés vers Microsoft 365 ne sont pas pris en charge. Seuls les fichiers chiffrés dans le service SharePoint ou OneDrive sont pris en charge pour le déchiffrement.

## <a name="decryption-limitations-with-email-attachments"></a>Limitations de déchiffrement avec les pièces jointes d’e-mail

Les scénarios suivants décrivent les limitations du déchiffrement des fichiers joints aux messages électroniques. Ces descriptions de scénario incluent également des solutions de contournement pour atténuer ces limitations.

- Si un fichier situé sur un ordinateur local (et non stocké dans un site SharePoint ou un compte OneDrive) est joint à un message électronique et qu’une étiquette de confidentialité qui applique le chiffrement est appliquée au message électronique, le fichier joint ne peut pas être déchiffré par eDiscovery. Cela signifie que si vous exécutez une requête de recherche par mot clé de la boîte aux lettres du destinataire, la pièce jointe chiffrée ne sera pas retournée par une requête de recherche par mot clé.

  La solution de contournement de cette limitation consiste à rechercher la même pièce jointe dans la boîte aux lettres de l’expéditeur. Cela est dû au fait que le chiffrement appliqué par l’étiquette de confidentialité est appliqué pendant le transport du message électronique. Cela signifie que la pièce jointe est chiffrée lors de l’envoi du message électronique. Le résultat est que l’instance du fichier attaché dans la boîte aux lettres de l’expéditeur n’est pas chiffrée, même si le même fichier dans la boîte aux lettres du destinataire est chiffré.

- De même, les pièces jointes cloud (fichiers stockés dans un site SharePoint ou un compte OneDrive) copiées dans un e-mail (à l’aide de l’option **Attacher en tant qu’option de copie** dans Outlook) ne peuvent pas être déchiffrées par eDiscovery. En outre, le chiffrement appliqué par une étiquette de confidentialité est appliqué lors de l’envoi du message électronique. La recherche de l’instance non chiffrée de la copie de la pièce jointe cloud dans la boîte aux lettres de l’expéditeur constitue également la solution de contournement pour cette limitation.

Dans ces deux scénarios, les messages électroniques avec des pièces jointes chiffrées peuvent être retournés par une recherche eDiscovery si une propriété de messagerie (telle que la date d’envoi, l’expéditeur, le destinataire ou l’objet) correspond à la requête de recherche.

## <a name="requirements-for-decryption-in-ediscovery"></a>Configuration requise pour le déchiffrement dans eDiscovery

Le rôle de déchiffrement RMS doit vous être attribué pour afficher un aperçu, examiner et exporter des fichiers chiffrés avec les technologies de chiffrement Microsoft. Ce rôle doit également vous être attribué pour passer en revue et interroger les fichiers chiffrés ajoutés à un jeu de révisions dans eDiscovery (Premium).

Ce rôle est attribué par défaut au groupe de rôles eDiscovery Manager sur la page **Autorisations** du portail de conformité Microsoft Purview. Pour plus d’informations sur le rôle de déchiffrement RMS, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-ediscovery-standard"></a>Déchiffrement des e-mails protégés par RMS et des pièces jointes chiffrées à l’aide de la recherche de contenu ou d’eDiscovery (Standard)

Tous les messages électroniques protégés par des droits (protégés par RMS) inclus dans les résultats d’une recherche de contenu sont déchiffrés lorsque vous les exportez. En outre, tout fichier chiffré à l’aide d’une [technologie de chiffrement Microsoft](encryption.md) et attaché à un e-mail inclus dans les résultats de la recherche sera déchiffré lors de son exportation. Cette fonctionnalité de déchiffrement est activée par défaut pour les membres du groupe de rôles eDiscovery Manager. Cela est dû au fait que le rôle de gestion de déchiffrement RMS est attribué à ce groupe de rôles par défaut. Gardez à l’esprit les éléments suivants lors de l’exportation de courriers électroniques chiffrés et de pièces jointes :
  
- Comme expliqué précédemment, si vous activez le déchiffrement des messages protégés par RMS lorsque vous les exportez, vous devez exporter les résultats de la recherche en tant que messages individuels. Si vous exportez les résultats de la recherche dans un fichier PST, les messages protégés par RMS sont exportés en tant que messages électroniques individuels.

- Les messages déchiffrés sont identifiés dans le rapport **ResultsLog** . Ce rapport contient une colonne nommée **État de décodage**, et une valeur **de Décodage** identifie les messages qui ont été déchiffrés.

- Outre le déchiffrement des pièces jointes de fichier lors de l’exportation des résultats de recherche, vous pouvez également afficher un aperçu du fichier déchiffré lors de l’aperçu des résultats de la recherche. Vous pouvez uniquement afficher le message électronique protégé par des droits après l’avoir exporté.

- Si vous devez empêcher quelqu’un de déchiffrer les messages de protection RMS et les pièces jointes de fichiers chiffrés, vous devez créer un groupe de rôles personnalisé (en copiant le groupe de rôles eDiscovery Manager intégré), puis supprimer le rôle de gestion de déchiffrement RMS du groupe de rôles personnalisé. Ajoutez ensuite la personne dont vous ne souhaitez pas déchiffrer les messages en tant que membre du groupe de rôles personnalisé.
