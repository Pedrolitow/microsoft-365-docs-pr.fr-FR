---
title: Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Découvrez comment SharePoint Online détecte les virus dans les fichiers que les utilisateurs téléchargent et empêche les utilisateurs de télécharger ou de synchroniser les fichiers.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 38d6111fe665e0af79cbd93f534b1058881ff76c
ms.sourcegitcommit: 04c4252457d9b976d31f53e0ba404e8f5b80d527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "48327986"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Microsoft 365 utilise un moteur de détection de virus courant pour analyser les fichiers que les utilisateurs téléchargent vers SharePoint Online, OneDrive et Microsoft Teams. Cette protection est incluse dans tous les abonnements qui incluent SharePoint Online, OneDrive et Microsoft Teams.

> [!IMPORTANT]
> Les fonctionnalités anti-virus intégrées permettent de mieux comprendre les virus. Ils ne sont pas destinés à être utilisés comme point de défense unique contre les programmes malveillants pour votre environnement. Nous encourageons tous les clients à examiner et à mettre en œuvre une protection contre les programmes malveillants à différentes couches et à appliquer les meilleures pratiques pour sécuriser leur infrastructure d’entreprise. Pour plus d’informations sur les stratégies et les meilleures pratiques, consultez la rubrique [Security Roadmap](security-roadmap.md).

## <a name="what-happens-when-an-infected-file-is-uploaded-to-sharepoint-online"></a>Que se passe-t-il lorsqu’un fichier infecté est téléchargé vers SharePoint Online ?

Le moteur de détection de virus Microsoft 365 s’exécute de façon asynchrone dans SharePoint Online. **Tous les fichiers ne sont pas analysés automatiquement lors du chargement**. Les heuristiques déterminent les fichiers à analyser. Lorsqu’un fichier contient un virus, le fichier est marqué de manière à ce qu’il ne puisse pas être téléchargé à nouveau. En avril 2018, nous avons supprimé la limite de 25 Mo pour les fichiers analysés.

Voici ce qui se passe :

1. Un utilisateur télécharge un fichier vers SharePoint Online.
2. SharePoint Online détermine si le fichier répond aux critères d’une analyse.
3. Le moteur de détection de virus analyse le fichier.
4. Si un virus est détecté, le moteur antivirus définit une propriété sur le fichier qui indique qu’il est infecté.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Que se passe-t-il lorsqu’un utilisateur essaie de télécharger un fichier infecté à l’aide du navigateur ?

Si un fichier est infecté, les utilisateurs ne peuvent pas télécharger le fichier à partir de SharePoint Online à l’aide d’un navigateur.

Voici ce qui se passe :

1. Un utilisateur ouvre un navigateur Web et essaie de télécharger un fichier infecté à partir de SharePoint Online.
2. L’utilisateur reçoit un avertissement indiquant qu’un virus a été détecté. Par défaut, l’utilisateur a la possibilité de télécharger le fichier et d’essayer de le nettoyer à l’aide du logiciel anti-virus sur son propre appareil.

> [!NOTE]
>
> Les administrateurs peuvent utiliser le paramètre *DisallowInfectedFileDownload* sur la cmdlet [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant) dans SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers infectés, même dans la fenêtre d’avertissement antivirus. Pour obtenir des instructions, consultez la rubrique [utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](turn-on-atp-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).
>
> Dès que vous activez le paramètre *DisallowInfectedFileDownload* , l’accès aux fichiers détectés/bloqués est totalement bloqué pour les utilisateurs et les administrateurs.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Que se passe-t-il lorsque le client de synchronisation OneDrive tente de synchroniser un fichier infecté ?

Les clients de synchronisation OneDrive ne téléchargent pas les fichiers contenant des virus. Le client de synchronisation affiche une notification indiquant que le fichier ne peut pas être synchronisé.

## <a name="extended-capabilities-with-office-365-advanced-threat-protection"></a>Fonctionnalités étendues avec Office 365 protection avancée contre les menaces

Les organisations Microsoft 365 qui disposent d' [Office 365 Advanced Threat Protection (ATP)](office-365-atp.md) incluses dans leur abonnement ou achetées en tant que complément peuvent activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams pour améliorer la création de rapports et la protection. Pour plus d’informations, reportez-vous à la rubrique [ATP pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md).

## <a name="more-information"></a>Plus d’informations

Pour plus d’informations sur les antivirus dans SharePoint Online, OneDrive et Microsoft Teams, consultez la rubrique se [protéger contre les menaces](protect-against-threats.md) et activer la protection avancée contre les menaces [pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md).
