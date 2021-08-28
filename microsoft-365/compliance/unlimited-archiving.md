---
title: Vue d’ensemble de l’archivage illimité
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 37cdbb02-a24a-4093-8bdb-2a7f0b3a19ee
description: Découvrez l’archivage à extension automatique, qui fournit un stockage d’archivage illimité pour Exchange Online boîtes aux lettres.
ms.openlocfilehash: be6fc33879a43d01dfde1312d7144994ff18fd18
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58561181"
---
# <a name="overview-of-unlimited-archiving"></a>Vue d’ensemble de l’archivage illimité

Dans Office 365, les boîtes aux lettres d’archivage fournissent aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire. Une fois la boîte aux lettres d’archivage d’un utilisateur activée, jusqu’à 100 Go de stockage supplémentaire sont disponibles. Dans le passé, lorsque le quota de stockage de 100 Go était atteint, les organisations deviez contacter Microsoft pour demander de l’espace de stockage supplémentaire pour une boîte aux lettres d’archivage. Ce n’est plus le cas.

La fonctionnalité d’archivage illimité Microsoft 365 (appelée archivage à extension *automatique)* offre un stockage supplémentaire dans les boîtes aux lettres d’archivage. Lorsque le quota de stockage dans la boîte aux lettres d’archivage est atteint, Microsoft 365 augmente automatiquement la taille de l’archive, ce qui signifie que les utilisateurs ne manqueront pas d’espace de stockage de boîte aux lettres et que les administrateurs n’auront pas à demander de stockage supplémentaire pour les boîtes aux lettres d’archivage.

Pour obtenir des instructions pas à pas pour activer l’archivage à extension automatique, voir [Activer l’archivage illimité.](enable-unlimited-archiving.md)

> [!NOTE]
> L’archivage à extension automatique prend aussi en charge les boîtes aux lettres partagées. Pour activer l’archive d’une boîte aux lettres partagée, une licence Exchange Online Plan 2 ou une licence Exchange Online Plan 1 avec une licence Archivage Exchange Online est requise.

## <a name="how-auto-expanding-archiving-works"></a>Fonctionnement de l’archivage à extension automatique

Comme indiqué précédemment, un espace de stockage de boîte aux lettres supplémentaire est créé lorsque la boîte aux lettres d’archivage d’un utilisateur est activée. Lorsque l’archivage à extension automatique est activé, Microsoft 365 vérifie régulièrement la taille de la boîte aux lettres d’archivage. Lorsqu’une boîte aux lettres d’archivage approche de sa limite de stockage, Microsoft 365 crée automatiquement un espace de stockage supplémentaire pour l’archive. Si l’utilisateur n’a plus cet espace de stockage supplémentaire, Microsoft 365'espace de stockage est ajouté à l’archive de l’utilisateur. Ce processus se produit automatiquement, ce qui signifie que les administrateurs n’ont pas besoin de demander un stockage d’archivage supplémentaire ou de gérer l’archivage à extension automatique.

Voici une vue d’ensemble rapide du processus.

![Vue d’ensemble du processus d’archivage à extension automatique.](../media/74355385-d990-44fe-8a87-6c3639d1f63f.png)

1. L’archivage est activé pour une boîte aux lettres utilisateur ou une boîte aux lettres partagée. Une boîte aux lettres d’archivage avec 100 Go d’espace de stockage est créée et le quota d’avertissement pour la boîte aux lettres d’archivage est fixé à 90 Go.

2. Un administrateur active l’archivage à extension automatique pour la boîte aux lettres. Lorsque la boîte aux lettres d’archivage (y compris le dossier Éléments récupérables) atteint 90 Go, elle est convertie en archive à extension automatique et Microsoft 365 ajoute de l’espace de stockage à l’archive. La mise en service de l’espace de stockage supplémentaire peut prendre jusqu’à 30 jours.

   > [!NOTE]
   > Si une boîte aux lettres est placée en conservation ou affectée à une stratégie de rétention, le quota de stockage de la boîte aux lettres d’archivage est augmenté jusqu’à 110 Go lorsque l’archivage à extension automatique est activé. De même, le quota d’avertissement d’archivage est augmenté jusqu’à 100 Go.

3. Microsoft 365 ajoute automatiquement plus d’espace de stockage si nécessaire.

> [!IMPORTANT]
> L’archivage à extension automatique est uniquement pris en charge pour les boîtes aux lettres utilisées pour des utilisateurs individuels (ou des boîtes aux lettres partagées) avec un taux de croissance qui ne dépasse pas 1 Go par jour. La boîte aux lettres d'archivage d'un utilisateur est destinée uniquement à cet utilisateur. L’utilisation de la journalation, des règles de transport ou des règles de transport automatique pour copier des messages dans une boîte aux lettres d’archivage n’est pas autorisée. Microsoft se réserve le droit de refuser l’archivage illimité dans les cas où la boîte aux lettres d’archivage d’un utilisateur est utilisée pour stocker des données d’archivage pour d’autres utilisateurs ou dans d’autres cas d’utilisation inappropriée.

## <a name="what-gets-moved-to-the-additional-archive-storage-space"></a>Qu’est-ce qui est déplacé vers l’espace de stockage d’archivage supplémentaire ?

Pour utiliser efficacement le stockage d’archives à extension automatique, les dossiers peuvent être déplacés. Microsoft 365 détermine quels dossiers sont déplacés lorsque du stockage supplémentaire est ajouté à l’archive. Parfois, lorsqu’un dossier est déplacé, un ou plusieurs sous-dossiers sont automatiquement créés et les éléments du dossier d’origine sont distribués dans ces dossiers pour faciliter le processus de déplacement. Lorsque vous affichez la partie archive de la liste des dossiers Outlook, ces sous-dossiers sont affichés sous le dossier d’origine.  La convention d’attribution de noms Microsoft 365 utilise pour nommer ces sous-_yyyy (créé sur **\<folder name\> mmm dd, aaa h_mm)**, où :

- **yyyy est l’année** de réception des messages dans le dossier.

- **mmm dd, yyyy h_m** est la date et l’heure de création du sous-fichier par Office 365, au format UTC, en fonction du fuseau horaire et des paramètres régionaux de l’utilisateur dans Outlook.

Les captures d’écran suivantes montrent une liste de dossiers avant et après le déplacer vers une archive à extension automatique.

 **Avant l’ajout d’un espace de stockage supplémentaire**

![Liste de dossiers de boîte aux lettres d’archivage avant la mise en service de l’archive à extension automatique.](../media/5d6d6420-e562-4912-aaab-1c111762b3f6.png)

 **Une fois le stockage supplémentaire ajouté**

![Liste de dossiers de boîte aux lettres d’archivage après la mise en service de l’archive à extension automatique.](../media/c03c5f51-23fa-4fc2-b887-7e7e5cce30da.png)

> [!NOTE]
> Comme décrit précédemment, Microsoft 365 déplace les éléments vers des sous-documents (et les nomme à l’aide de la convention d’attribution de noms décrite ci-dessus) pour aider à distribuer le contenu vers une archive auxiliaire. Toutefois, le déplacement d’éléments vers des sous-dossiers peut ne pas toujours être le cas. Parfois, un dossier entier peut être déplacé vers une archive auxiliaire. Dans ce cas, le dossier conserve son nom d’origine.  Il n’apparaît pas dans la liste des dossiers Outlook que le dossier a été déplacé vers une archive auxiliaire.

## <a name="outlook-requirements-for-accessing-items-in-an-auto-expanded-archive"></a>Outlook’accès aux éléments dans une archive à extension automatique

Pour accéder aux messages stockés dans une archive à extension automatique, les utilisateurs doivent utiliser l’un des clients Outlook suivants :

- Outlook 2016 ou Outlook 2019 pour Windows

- Outlook sur le web

- Outlook 2016 ou Outlook 2019 pour Mac

Voici quelques éléments à prendre en compte lorsque vous utilisez Outlook ou Outlook sur le web pour accéder aux messages stockés dans une archive à extension automatique.

- Vous pouvez accéder à n’importe quel dossier de votre boîte aux lettres d’archivage, y compris ceux qui ont été déplacés vers la zone de stockage à extension automatique.

- Si une boîte aux lettres d’archivage possède au moins une zone de stockage à extension automatique, vous ne pouvez pas supprimer un dossier de la boîte aux lettres d’archivage ou de l’archive auxiliaire. En d’autres termes, une fois qu’une zone de stockage à extension automatique a été mise en service, vous ne pouvez supprimer aucun dossier dans l’archive.

- Vous pouvez supprimer des éléments dans une zone de stockage à extension automatique. Toutefois, vous ne pouvez pas utiliser la fonctionnalité Récupérer les éléments supprimés pour récupérer un élément supprimé d’une zone de stockage à extension automatique.

- La recherche d’archivage à extension automatique est disponible dans Outlook pour le web (OWA). À l’exemple de l’archive en ligne, vous pouvez rechercher des éléments qui ont été déplacés vers une zone de stockage supplémentaire. Lorsque l’archive est sélectionnée en tant qu’étendue de recherche dans OWA, toutes les archives (y compris les archives à extension automatique) et leurs sous-documents correspondants sont recherchés.

- La recherche d’archives à extension automatique est disponible dans Outlook bureau dans le canal actuel (prévisualisation). Dans cet aperçu, l’étendue Boîte aux lettres actuelle est disponible, ce qui vous permet d’effectuer des recherches dans l’archive à extension automatique. Pour plus d’informations sur cette fonctionnalité et d’autres [fonctionnalités](https://techcommunity.microsoft.com/t5/outlook-global-customer-service/how-outlook-for-windows-connected-to-exchange-online-utilizes/ba-p/1715045)Recherche Microsoft prise en charge, voir Comment Outlook pour Windows connecté à Exchange Online utilise Recherche Microsoft . 

- Le nombre d’éléments Outlook et le nombre de lecture/non lus (en Outlook et Outlook sur le web) dans une archive à extension automatique peuvent ne pas être exacts.

## <a name="auto-expanding-archiving-and-other-compliance-features"></a>Archivage à extension automatique et autres fonctionnalités de conformité

Cette section explique la fonctionnalité entre l’archivage à extension automatique et d’autres fonctionnalités de conformité et de gouvernance des données.

- **eDiscovery :** Lorsque vous utilisez un outil eDiscovery, tel que la recherche de contenu ou In-Place eDiscovery, les zones de stockage supplémentaires dans une archive à extension automatique sont également recherchés.

- **Rétention :** Lorsque vous placez une boîte aux lettres en conservation à l’aide d’outils tels que la conservation pour litige dans Exchange Online ou les conservations de cas eDiscovery et les stratégies de rétention dans le centre de sécurité et de conformité, le contenu situé dans une archive à extension automatique est également mis en attente.

- **Gestion des enregistrements de messagerie (MRM) :** Si vous utilisez des stratégies de suppression de la mrm dans Exchange Online pour supprimer définitivement les éléments de boîte aux lettres expirés, les éléments expirés situés dans l’archive à extension automatique sont également supprimés.

- **Service d’importation :** Vous pouvez utiliser le service d Office 365 pour importer des fichiers PST dans l’archive à extension automatique d’un utilisateur. Vous pouvez importer jusqu’à 100 Go de données à partir de fichiers PST dans la boîte aux lettres d’archivage de l’utilisateur.

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations techniques sur l’archivage à extension automatique, voir [Microsoft 365: Auto-Expanding Archives FAQ](https://techcommunity.microsoft.com/t5/exchange-team-blog/office-365-auto-expanding-archives-faq/ba-p/607784).
