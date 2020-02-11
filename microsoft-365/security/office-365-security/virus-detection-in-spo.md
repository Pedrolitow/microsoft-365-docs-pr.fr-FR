---
title: Détection de virus dans SharePoint Online
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
description: Découvrez la protection antivirus dans SharePoint Online.
ms.openlocfilehash: f22c2a3280148eb23f4ba53ff467a533186ed791
ms.sourcegitcommit: 3d17c1d6b80672719b1878e2f321f0de39595226
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "41887271"
---
# <a name="virus-detection-in-sharepoint-online"></a>Détection de virus dans SharePoint Online

Office 365 peut aider à protéger votre environnement contre les programmes malveillants en détectant les virus dans les fichiers que les utilisateurs téléchargent sur SharePoint Online. Les fichiers peuvent être analysés pour détecter d’éventuels virus une fois qu’ils ont été téléchargés. Si un fichier est infecté, une propriété est définie de sorte que les utilisateurs ne puissent pas télécharger ou synchroniser le fichier.

> [!IMPORTANT]
> Ces fonctionnalités antivirus dans SharePoint Online sont un moyen de contenir des virus. Ils ne sont pas destinés à être utilisés comme point de défense unique contre les programmes malveillants pour votre environnement. Nous encourageons tous les clients à évaluer et à mettre en œuvre une protection contre les programmes malveillants à différentes couches et à appliquer les meilleures pratiques pour sécuriser votre infrastructure d’entreprise. Pour plus d’informations sur les stratégies et les meilleures pratiques, consultez la rubrique [Security Roadmap](security-roadmap.md).

## <a name="what-happens-when-an-infected-file-is-uploaded-to-sharepoint-online"></a>Que se passe-t-il lorsqu’un fichier infecté est téléchargé vers SharePoint Online ?

Office 365 utilise un moteur de détection de virus courant. Le moteur s’exécute de façon asynchrone au sein de SharePoint Online et analyse certains fichiers après leur chargement. Les heuristiques sont utilisées pour déterminer quels fichiers sont analysés. Lorsqu’un fichier contient un virus, il est signalé de sorte qu’il ne puisse pas être téléchargé à nouveau. En avril 2018, nous avons supprimé la limite de 25 Mo pour les fichiers analysés.

Voici ce qui se passe :

1. Un utilisateur télécharge un fichier vers SharePoint Online.

2. SharePoint Online détermine si le fichier répond aux critères d’une analyse.

3. Le moteur de détection de virus analyse le fichier.

4. Si un virus est détecté, le moteur antivirus définit une propriété sur le fichier qui indique qu’il est infecté.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Que se passe-t-il lorsqu’un utilisateur essaie de télécharger un fichier infecté à l’aide du navigateur ?

Si un fichier est infecté, les utilisateurs ne peuvent pas télécharger le fichier à partir de SharePoint Online à l’aide du navigateur.

Voici ce qui se passe :

1. Un utilisateur ouvre un navigateur Web et essaie de télécharger un fichier infecté à partir de SharePoint Online.

2. L’utilisateur reçoit un avertissement indiquant qu’un virus a été détecté. L’utilisateur a la possibilité de télécharger le fichier et d’essayer de le nettoyer à l’aide de son propre logiciel antivirus.

> [!NOTE]
> Vous pouvez utiliser le paramètre *DisallowInfectedFileDownload* sur la cmdlet [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant) dans SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger un fichier infecté, même dans la fenêtre d’avertissement antivirus.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>Que se passe-t-il lorsque le client de synchronisation OneDrive tente de synchroniser un fichier infecté ?

Que les utilisateurs synchronisent des fichiers avec le nouveau client de synchronisation OneDrive (OneDrive. exe) ou le client de synchronisation OneDrive entreprise précédent (Groove. exe), si un fichier contient un virus, le client de synchronisation ne le télécharge pas. Le client de synchronisation affiche une notification indiquant que le fichier ne peut pas être synchronisé.
