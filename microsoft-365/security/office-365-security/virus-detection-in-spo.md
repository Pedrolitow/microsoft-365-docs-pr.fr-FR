---
title: Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
localization_priority: Normal
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Découvrez comment SharePoint Online détecte des virus dans les fichiers que les utilisateurs téléchargent et empêche les utilisateurs de télécharger ou de synchroniser les fichiers.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9ba3d19c6b04b93d9b1089540b7483d8b2e7246c
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727498"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)

Microsoft 365 utilise un moteur de détection de virus courant pour analyser les fichiers que les utilisateurs téléchargent sur SharePoint Online, OneDrive et Microsoft Teams. Cette protection est incluse dans tous les abonnements qui incluent SharePoint Online, OneDrive et Microsoft Teams.

> [!IMPORTANT]
> Les fonctionnalités anti-virus intégrées permettent de contenir des virus. Elles ne sont pas destinées à être un point de défense unique contre les programmes malveillants pour votre environnement. Nous encourageons tous les clients à examiner et à implémenter la protection contre les programmes malveillants à différents niveaux et à appliquer les meilleures pratiques pour sécuriser leur infrastructure d’entreprise. Pour plus d’informations sur les stratégies et les meilleures pratiques, consultez [la feuille de route de sécurité.](security-roadmap.md)

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Que se passe-t-il si un fichier infecté est téléchargé vers SharePoint Online ?

Le moteur de détection de virus Microsoft 365 s’exécute de manière asynchrone (indépendamment des téléchargements de fichiers) dans SharePoint Online. **Tous les fichiers ne sont pas analysés automatiquement.** Les heuristiques déterminent les fichiers à analyser. Lorsqu’un fichier contient un virus, le fichier est signalé. En avril 2018, nous avons supprimé la limite de 25 Mo pour les fichiers analysés.

Voici ce qui se produit :

1. Un utilisateur télécharge un fichier vers SharePoint Online.
2. SharePoint Online, dans le cadre de ses processus d’analyse antivirus, détermine ultérieurement si le fichier répond aux critères d’une analyse.
3. Si le fichier répond aux critères d’une analyse, le moteur de détection de virus analyse le fichier.
4. Si un virus est trouvé dans le fichier analysé, le moteur de virus définit une propriété sur le fichier indiquant qu’il est infecté.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Que se passe-t-il lorsqu’un utilisateur tente de télécharger un fichier infecté à l’aide du navigateur ?

Si un fichier est infecté, les utilisateurs ne peuvent pas télécharger le fichier à partir de SharePoint Online à l’aide d’un navigateur.

Voici ce qui se produit :

1. Un utilisateur ouvre un navigateur web et tente de télécharger un fichier infecté à partir de SharePoint Online.
2. L’utilisateur est averti qu’un virus a été détecté. Par défaut, l’utilisateur a la possibilité de télécharger le fichier et de tenter de le nettoyer à l’aide du logiciel antivirus sur son propre appareil.

> [!NOTE]
>
> Les administrateurs peuvent utiliser le paramètre *DisallowInfectedFileDownload* sur la cmdlet [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant) dans SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers infectés, même dans la fenêtre d’avertissement antivirus. Pour obtenir des instructions, [voir Utiliser SharePoint Online PowerShell](turn-on-atp-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files)pour empêcher les utilisateurs de télécharger des fichiers malveillants.
>
> Dès que vous activez le paramètre *DisallowInfectedFileDownload,* l’accès aux fichiers détectés/bloqués est complètement bloqué pour les utilisateurs et les administrateurs.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Que se passe-t-il lorsque le client de synchronisation OneDrive tente de synchroniser un fichier infecté ?

Les clients de synchronisation OneDrive ne téléchargeront pas les fichiers contenant des virus. Le client de synchronisation affiche une notification vous avertissant que le fichier ne peut pas être synchronisé.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Fonctionnalités étendues avec Microsoft Defender pour Office 365

Les organisations Microsoft 365 dont Microsoft Defender pour [Office 365](office-365-atp.md) est inclus dans leur abonnement ou qui ont été achetés en tant que modules peuvent activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams pour améliorer la fonctionnalité de rapports et de protection. Pour plus d’informations, [voir Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.](atp-for-spo-odb-and-teams.md)

## <a name="related-articles"></a>Articles connexes

[Protection contre les programmes malveillants et les ransomware dans Microsoft 365](https://docs.microsoft.com/compliance/assurance/assurance-malware-and-ransomware-protection)

Pour plus d’informations sur l’antivirus dans SharePoint Online, OneDrive et Microsoft Teams, voir Se protéger contre les menaces et activer les pièces [jointes sécurisées pour SharePoint, OneDrive](turn-on-atp-for-spo-odb-and-teams.md)et Microsoft Teams. [](protect-against-threats.md)
