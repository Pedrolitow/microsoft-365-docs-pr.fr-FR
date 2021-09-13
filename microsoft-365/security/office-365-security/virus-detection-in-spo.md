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
ms.openlocfilehash: 2ab11d4c1e2a064ad0717e6619f72a38b0cbc831
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202679"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>Protection antivirus intégrée dans SharePoint Online, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Microsoft 365 utilise un moteur de détection de virus courant pour analyser les fichiers que les utilisateurs téléchargent sur SharePoint Online, OneDrive et Microsoft Teams. Cette protection est incluse dans tous les abonnements qui incluent SharePoint Online, OneDrive et Microsoft Teams.

> [!IMPORTANT]
> Les fonctionnalités anti-virus intégrées permettent de contenir des virus. Elles ne sont pas conçues comme un seul point de défense contre les programmes malveillants pour votre environnement. Nous encourageons tous les clients à examiner et à implémenter la protection contre les programmes malveillants à différents niveaux et à appliquer les meilleures pratiques pour sécuriser leur infrastructure d’entreprise. Pour plus d’informations sur les stratégies et les meilleures pratiques, consultez [la feuille de route de sécurité.](security-roadmap.md)

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Que se passe-t-il si un fichier infecté est téléchargé vers SharePoint Online ?

Le moteur Microsoft 365 détection de virus s’exécute de manière asynchrone (indépendamment des chargements de fichiers) dans SharePoint Online. **Tous les fichiers ne sont pas analysés automatiquement.** Les heuristiques déterminent les fichiers à analyser. Lorsqu’un fichier contient un virus, le fichier est signalé. En avril 2018, nous avons supprimé la limite de 25 Mo pour les fichiers analysés.

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
> Les administrateurs peuvent utiliser le paramètre *DisallowInfectedFileDownload* sur la cmdlet [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant) dans SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers infectés, même dans la fenêtre d’avertissement antivirus. Pour obtenir des instructions, voir Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de [télécharger des fichiers malveillants.](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files)
>
> Dès que vous activez le paramètre *DisallowInfectedFileDownload,* l’accès aux fichiers détectés/bloqués est complètement bloqué pour les utilisateurs et les administrateurs.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Que se passe-t-il lorsque le client Synchronisation OneDrive tente de synchroniser un fichier infecté ?

Lorsqu’un fichier malveillant est téléchargé vers OneDrive, il est synchronisé avec l’ordinateur local avant d’être marqué comme programme malveillant. Une fois qu’il a été marqué comme programme malveillant, l’utilisateur ne peut plus ouvrir le fichier synchronisé à partir de son ordinateur local.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Fonctionnalités étendues avec Microsoft Defender pour Office 365

Microsoft 365 organisations dont [Microsoft Defender pour Office 365](defender-for-office-365.md) est inclus dans leur abonnement ou acheté en tant que module supplémentaire peuvent activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams pour améliorer la fonctionnalité de rapports et de protection. Pour plus d’informations, [voir Coffre attachments for SharePoint, OneDrive, and Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>Articles connexes

[Protection contre les programmes malveillants et les ransomware dans Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

Pour plus d’informations sur l’antivirus dans SharePoint Online, OneDrive et [](protect-against-threats.md) Microsoft Teams, voir Se protéger contre les menaces et activer les pièces jointes Coffre pour [SharePoint, OneDrive](turn-on-mdo-for-spo-odb-and-teams.md)et Microsoft Teams .
