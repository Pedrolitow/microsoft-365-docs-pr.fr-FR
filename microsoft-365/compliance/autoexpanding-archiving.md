---
title: En savoir plus sur l’archivage à extension automatique
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 37cdbb02-a24a-4093-8bdb-2a7f0b3a19ee
description: Découvrez l'archivage en auto-expansion, qui fournit un stockage d’archivage supplémentaire pour Exchange Online boîtes aux lettres.
ms.openlocfilehash: 1eb2aaf2593e9b5d2c1e254f7fa8e207cbc848d4
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359972"
---
# <a name="learn-about-auto-expanding-archiving"></a>En savoir plus sur l’archivage à extension automatique

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Les boîtes aux lettres d’archivage dans Microsoft Purview fournissent aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire. Une fois la boîte aux lettres d’archivage d’un utilisateur activée, jusqu’à 100 Go de stockage supplémentaire sont disponibles.

Cette fonctionnalité d’archivage dans Microsoft Purview (appelée *archivage à extension automatique*) fournit jusqu’à 1,5 To de stockage supplémentaire dans les boîtes aux lettres d’archivage. Lorsque le quota de stockage dans la boîte aux lettres d’archivage est atteint, Microsoft Purview augmente automatiquement (et incrémentiellement) la taille de l’archive jusqu’à ce que la boîte aux lettres d’archivage atteigne 1,5 To.

Pour obtenir des instructions détaillées sur l’activation de l’archivage à extension automatique, consultez [Activer l’archivage en auto-expansion](enable-autoexpanding-archiving.md).

> [!NOTE]
> L’archivage à extension automatique prend aussi en charge les boîtes aux lettres partagées.

## <a name="how-auto-expanding-archiving-works"></a>Fonctionnement de l’archivage en auto-expansion

Comme expliqué dans l’introduction, un espace de stockage de boîte aux lettres supplémentaire est créé lorsque la boîte aux lettres d’archivage d’un utilisateur est activée. Lorsque l’archivage de développement automatique est activé, Microsoft Purview vérifie régulièrement la taille de la boîte aux lettres d’archivage. Lorsqu’une boîte aux lettres d’archivage est proche de sa limite de stockage, un espace de stockage supplémentaire est automatiquement créé pour l’archive. Si l’utilisateur manque de cet espace de stockage supplémentaire, un espace de stockage supplémentaire est automatiquement ajouté à l’archive de l’utilisateur. Ce processus se poursuit jusqu’à ce que l’archive de l’utilisateur atteigne une taille de 1,5 To. Ce processus se produit automatiquement, ce qui signifie que les administrateurs n’ont pas besoin de demander un stockage d’archivage supplémentaire ou de gérer l’archivage en auto-expansion.

Voici une vue d’ensemble rapide du processus.

![Vue d’ensemble du processus d’archivage en auto-expansion.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. L’archivage est activé pour une boîte aux lettres utilisateur ou une boîte aux lettres partagée. Une boîte aux lettres d’archivage avec 100 Go d’espace de stockage est créée et le quota d’avertissement pour la boîte aux lettres d’archivage est défini sur 90 Go.

2. Un administrateur active l’archivage en auto-expansion pour la boîte aux lettres. Si une stratégie de conservation ou de rétention est appliquée à la boîte aux lettres, le quota de stockage de la boîte aux lettres d’archivage est augmenté à 110 Go et le quota d’avertissement d’archivage est augmenté à 100 Go.
    
    Ensuite, lorsque la boîte aux lettres d’archivage (y compris le dossier Éléments récupérables) atteint son quota de stockage, la boîte aux lettres d’archivage est convertie en archive à extension automatique. Un espace de stockage supplémentaire est ajouté jusqu’à ce qu’il atteigne une taille maximale de 1,5 To. La mise en service de l’espace de stockage supplémentaire peut prendre jusqu’à 30 jours.

3. Microsoft Purview ajoute automatiquement plus d’espace de stockage si nécessaire.

> [!IMPORTANT]
> L’archivage en auto-expansion est pris en charge uniquement pour les boîtes aux lettres utilisées pour des utilisateurs individuels (ou des boîtes aux lettres partagées) avec un taux de croissance qui ne dépasse pas 1 Go par jour. La boîte aux lettres d'archivage d'un utilisateur est destinée uniquement à cet utilisateur. L'utilisation de la fonction de journalisation, des règles de transport ou des règles de transfert automatique pour copier des messages vers une boîte aux lettres Exchange Online à des fins d'archivage n'est pas autorisée. Microsoft se réserve le droit de refuser l’archivage illimité dans les cas où la boîte aux lettres d’archivage d’un utilisateur sert à stocker les données d’archivage d’autres utilisateurs ou dans d’autres cas d’utilisation inappropriée.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Qu’est-ce qui est déplacé vers l’espace de stockage d’archivage supplémentaire ?

Pour utiliser efficacement le stockage d’archivage en auto-expansion, les dossiers peuvent être déplacés. Microsoft Purview détermine les dossiers déplacés quand un stockage supplémentaire est ajouté à l’archive. Parfois, lorsqu’un dossier est déplacé, un ou plusieurs sous-dossiers sont automatiquement créés et les éléments du dossier d’origine sont distribués dans ces dossiers pour faciliter le processus de déplacement. Lorsque vous affichez la partie archive de la liste des dossiers dans Outlook, ces sous-dossiers sont affichés sous le dossier d’origine. La convention d’affectation de noms utilisée par Microsoft 365 pour nommer ces sous-dossiers est **\<folder name\>_aaaa (créée sur mmm jj, aaaa h_mm)**, où :

- **aaaa est l’année** de réception des messages dans le dossier.

- **mmm jj, aaaa h_m** est la date et l’heure auxquelles le sous-dossier a été créé par Office 365, au format UTC, en fonction du fuseau horaire et des paramètres régionaux de l’utilisateur dans Outlook.

Les captures d’écran suivantes montrent une liste de dossiers avant et après le déplacer vers une archive en auto-expansion.

 **Avant l’ajout d’un espace de stockage supplémentaire**

![Liste de dossiers de boîte aux lettres d’archivage avant la mise en service de l’archivage en auto-expansion.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Une fois le stockage supplémentaire ajouté**

![Liste de dossiers de boîte aux lettres d’archivage après la mise en service de l’archivage en auto-expansion.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Comme décrit précédemment, Microsoft Purview déplace les éléments vers des sous-dossiers (et les nomme à l’aide de la convention d’affectation de noms décrite ci-dessus) pour aider à distribuer du contenu dans une archive auxiliaire. Toutefois, le déplacement d’éléments vers des sous-dossiers peut ne pas toujours être le cas. Parfois, un dossier entier peut être déplacé vers une archive auxiliaire. Dans ce cas, le dossier conserve son nom d’origine. Il n’apparaît pas dans la liste des dossiers Outlook que le dossier a été déplacé vers une archive auxiliaire.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Conditions requises d’Outlook pour accéder aux éléments dans une archive en auto-expansion

Pour accéder aux messages stockés dans une archive en auto-expansion, les utilisateurs doivent utiliser l’un des clients Outlook suivants :

- Outlook dans le cadre de Microsoft 365 Apps for enterprise (anciennement Office 365 ProPlus)

- Outlook dans le cadre de Microsoft 365 Apps for business (anciennement Office 365 Business)

- Outlook 2016 ou Outlook 2019 pour Windows

- Outlook sur le web lorsque la boîte aux lettres principale est en Exchange Online plutôt qu’en local

- Outlook 2016 ou Outlook 2019 pour Mac

Voici quelques éléments à prendre en compte lorsque vous utilisez Outlook ou Outlook sur le web pour accéder aux messages stockés dans une archive en auto-expansion.

- Vous pouvez accéder à n’importe quel dossier de votre boîte aux lettres d’archivage, y compris ceux qui ont été déplacés vers la zone de stockage en auto-expansion.

- Si une boîte aux lettres d’archivage possède au moins une zone de stockage en auto-expansion, vous ne pouvez pas supprimer un dossier de la boîte aux lettres d’archivage ou de l’archive auxiliaire. En d’autres termes, une fois qu’une zone de stockage en auto-expansion a été mise en service, vous ne pouvez supprimer aucun dossier dans l’archive.

- Vous pouvez supprimer des éléments dans une zone de stockage développée automatiquement. Toutefois, vous ne pouvez pas utiliser la fonctionnalité Récupérer les éléments supprimés pour récupérer un élément après l’activation de l’archivage à extension automatique pour une boîte aux lettres.

- La recherche d’archivage en auto-expansion est disponible dans Outlook pour le web (OWA). Comme pour les archives en ligne, vous pouvez rechercher des éléments qui ont été déplacés vers une zone de stockage supplémentaire. Lorsque l’archive est sélectionnée en tant qu’étendue de recherche dans OWA, toutes les archives (y compris les archivage en auto-expansion) et leurs sous-documents correspondants sont recherchés.

- La recherche d’archives développée automatiquement est disponible dans Outlook pour Windows dans le canal d’entreprise mensuel. Avec cette mise à jour, l’étendue de la boîte aux lettres actuelle est disponible, ce qui vous permet de rechercher dans l’archive développée automatiquement. Notez que la recherche n’est pas prise en charge pour la fonctionnalité d’archivage à extension automatique dans une situation d’archivage cloud uniquement (boîte aux lettres principale toujours locale). Pour plus d’informations à ce sujet et d’autres fonctionnalités de support Microsoft Search, consultez [Comment Outlook pour Windows connecté à Exchange Online utilise Microsoft Search](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045). 

- Le nombre d’éléments Outlook et le nombre de lecture/non lus (en Outlook et Outlook sur le web) dans une archive en auto-expansion peuvent ne pas être exacts.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Archivage en auto-expansion et autres fonctionnalités de conformité

Cette section explique la fonctionnalité entre l’archivage en auto-expansion et d’autres fonctionnalités de conformité et de gouvernance des données.

- **eDiscovery :** Lorsque vous utilisez un outil eDiscovery, tel que la recherche de contenu ou In-Place eDiscovery, les zones de stockage supplémentaires dans une archive en auto-expansion sont également recherchés.

- **Rétention:** Lorsque vous mettez une boîte aux lettres en attente à l’aide d’outils tels que la conservation pour litige dans Exchange Online ou les stratégies de conservation et de rétention de cas eDiscovery dans le portail de conformité Microsoft Purview, le contenu situé dans une archive développée automatiquement est également mis en attente.

- **Gestion des enregistrements de messagerie (MRM) :** Si vous utilisez des stratégies de suppression de la MRM dans Exchange Online pour supprimer définitivement les éléments de boîte aux lettres expirés, les éléments expirés situés dans l’archive en auto-expansion sont également supprimés.

- **Service d’importation :** Vous pouvez utiliser le service d Office 365 pour importer des fichiers PST dans l’archive en auto-expansion d’un utilisateur. Vous pouvez importer jusqu’à 100 Go de données à partir de fichiers PST vers la boîte aux lettres d’archivage de l’utilisateur.

## <a name="next-steps"></a>Prochaines étapes

Pour plus d’informations techniques sur l’archivage en auto-expansion, consultez [Microsoft 365 : FAQ sur l’archivage en auto-expansion](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).

Si vous êtes prêt à activer l’archivage à extension automatique, consultez [Activer l’archivage à extension automatique](enable-autoexpanding-archiving.md).
