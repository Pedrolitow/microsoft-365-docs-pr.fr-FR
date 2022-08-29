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
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: Découvrez comment SharePoint Online détecte les virus dans les fichiers que les utilisateurs chargent et empêche les utilisateurs de télécharger ou de synchroniser les fichiers.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e57865d0c8ec3993080c822438b7c4037ccab765
ms.sourcegitcommit: e6595be36bbaba244439bd59dbae935e2b258ded
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2022
ms.locfileid: "67450056"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Microsoft 365 utilise un moteur de détection de virus commun pour analyser les fichiers que les utilisateurs chargent sur SharePoint Online, OneDrive et Microsoft Teams. Cette protection est incluse avec tous les abonnements qui incluent SharePoint Online, OneDrive et Microsoft Teams.

> [!IMPORTANT]
> Les fonctionnalités antivirus intégrées sont un moyen d’aider à contenir des virus. Ils ne sont pas conçus comme un seul point de défense contre les programmes malveillants pour votre environnement. Nous encourageons tous les clients à examiner et à implémenter la protection contre les programmes malveillants à différentes couches et à appliquer les meilleures pratiques pour sécuriser leur infrastructure d’entreprise. Pour plus d’informations sur les stratégies et les meilleures pratiques, consultez la [feuille de route de sécurité](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Que se passe-t-il si un fichier infecté est chargé sur SharePoint Online ?

Le moteur de détection de virus Microsoft 365 analyse les fichiers de façon asynchrone (à un moment donné après le chargement). Si un fichier n’a pas encore été analysé par le processus de détection de virus asynchrone et qu’un utilisateur tente de télécharger le fichier à partir du navigateur ou de Teams, une analyse lors du téléchargement est déclenchée par SharePoint avant l’autorisation du téléchargement. **Tous les types de fichiers ne sont pas analysés automatiquement**. Les heuristiques déterminent les fichiers à analyser. Lorsqu’un fichier contient un virus, le fichier est marqué. 

Voici ce qui se passe :

1. Un utilisateur charge un fichier dans SharePoint Online.
2. SharePoint Online, dans le cadre de ses processus d’analyse antivirus, détermine ultérieurement si le fichier répond aux critères d’une analyse.
3. Si le fichier répond aux critères d’une analyse, le moteur de détection de virus analyse le fichier.
4. Si un virus se trouve dans le fichier analysé, le moteur de virus définit une propriété sur le fichier qui indique que le fichier est infecté.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Que se passe-t-il lorsqu’un utilisateur tente de télécharger un fichier infecté à l’aide du navigateur ?

Par défaut, les utilisateurs peuvent télécharger des fichiers infectés à partir de SharePoint Online. Voici ce qui se passe :

1. Dans un navigateur web, un utilisateur tente de télécharger un fichier à partir de SharePoint Online qui est infecté.
2. L’utilisateur reçoit un avertissement indiquant qu’un virus a été détecté dans le fichier. L’utilisateur a la possibilité de poursuivre le téléchargement et de tenter de le nettoyer à l’aide d’un logiciel antivirus sur son appareil.

Pour modifier ce comportement afin que les utilisateurs ne puissent pas télécharger les fichiers infectés, même à partir de la fenêtre d’avertissement antivirus, les administrateurs peuvent utiliser le paramètre *DisallowInfectedFileDownload* sur l’applet de commande **[Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant)** dans SharePoint Online PowerShell. La valeur $true pour le paramètre *DisallowInfectedFileDownload* bloque complètement l’accès aux fichiers détectés/bocked pour les utilisateurs.

Pour obtenir des instructions, consultez [Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

## <a name="can-admins-bypass-disallowinfectedfiledownload-and-extract-infected-files"></a>Les administrateurs peuvent-ils contourner *DisallowInfectedFileDownload* et extraire des fichiers infectés ?

Les administrateurs SharePoint et les administrateurs généraux sont autorisés à effectuer des extractions de fichiers d’investigation de fichiers infectés par des programmes malveillants dans SharePoint Online PowerShell avec l’applet de commande [Get-SPOMalwareFileContent](/powershell/module/sharepoint-online/get-spomalwarefilecontent) . Les administrateurs n’ont pas besoin d’accéder au site qui héberge le contenu infecté. Tant que le fichier a été marqué comme programme malveillant, les administrateurs peuvent utiliser **Get-SPOMalwareFileContent** pour extraire le fichier. 

Pour plus d’informations sur le fichier infecté, les administrateurs peuvent utiliser l’applet de commande **[Get-SPOMalwareFile](/powershell/module/sharepoint-online/get-spomalwarefile)** pour voir le type de programme malveillant détecté et l’état de l’infection. 

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Que se passe-t-il lorsque le client Synchronisation OneDrive tente de synchroniser un fichier infecté ?

Lorsqu’un fichier malveillant est chargé sur OneDrive, il est synchronisé avec l’ordinateur local avant d’être marqué comme programme malveillant. Une fois qu’il est marqué comme programme malveillant, l’utilisateur ne peut plus ouvrir le fichier synchronisé à partir de son ordinateur local.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Fonctionnalités étendues avec Microsoft Defender pour Office 365

Les organisations Microsoft 365 qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md) incluses dans leur abonnement ou achetées en tant que module complémentaire peuvent activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams pour améliorer la création de rapports et la protection. Pour plus d’informations, consultez [Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>Articles connexes

[Protection contre les programmes malveillants et les ransomware dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

Pour plus d’informations sur les antivirus dans SharePoint Online, OneDrive et Microsoft Teams, consultez [Protéger contre les menaces](protect-against-threats.md) et [activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).
