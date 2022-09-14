---
title: Utiliser Microsoft Defender pour Office 365 dans SharePoint Online
description: Les étapes pour vous assurer que vous pouvez utiliser et obtenir la valeur à partir de Microsoft Defender pour Office 365 dans SharePoint Online et OneDrive Entreprise
search.product: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTBen
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
search.appverid: met150
ms.openlocfilehash: b2785d0f8f5fed637121ca77af9abb6ef933b3ab
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687300"
---
# <a name="use-microsoft-defender-for-office-365-with-sharepoint-online"></a>Utiliser Microsoft Defender pour Office 365 avec SharePoint Online

Microsoft Office SharePoint Online est un outil de collaboration utilisateur et de stockage de fichiers largement utilisé. Les étapes suivantes permettent de réduire la surface d’attaque dans SharePoint Online et de sécuriser cet outil de collaboration dans votre organisation. Toutefois, il est important de noter qu’il existe un équilibre entre la sécurité et la productivité, et toutes ces étapes ne peuvent pas être pertinentes pour votre profil de risque organisationnel. Examinez, testez et conservez cet équilibre.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 Plan 1
- Autorisations suffisantes (administrateur SharePoint/administrateur de sécurité).
- Microsoft Office SharePoint Online (partie de Microsoft 365).
- Cinq à dix minutes pour effectuer ces étapes.

## <a name="turn-on-microsoft-defender-for-office-365-in-sharepoint-online"></a>Activer Microsoft Defender pour Office 365 dans SharePoint Online
Si vous disposez d’une licence pour Microsoft Defender pour Office 365 **(évaluation gratuite de 90 jours disponible à aka.ms/trymdo),** vous pouvez garantir une protection transparente contre les programmes malveillants zero day et la protection contre les clics dans Microsoft Teams.

Pour plus d’informations, consultez [l’étape 1 : Utilisez le portail Microsoft 365 Defender pour activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](/microsoft-365/security/office-365-security/turn-on-mdo-for-spo-odb-and-teams#step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams).

1.  Connectez-vous à la [page de configuration des pièces jointes sécurisées du centre de sécurité](https://security.microsoft.com/safeattachmentv2).
1.  Sélectionnez **Paramètres généraux**.
1.  Vérifiez que **l’option Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams** est **activée**.
1.  Accédez à la [page de configuration des liens sécurisés du centre de sécurité](https://security.microsoft.com/safelinksv2).
1.  Sélectionnez **Enregistrer**.

## <a name="stop-infected-file-downloads-from-sharepoint-online"></a>Arrêter les téléchargements de fichiers infectés à partir de SharePoint Online

Par défaut, les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers malveillants détectés par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams. Toutefois, l’option *Télécharger* est toujours disponible et doit être *désactivée*. 

Pour plus d’informations, consultez [l’étape 2 : (*recommandé*) Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](/microsoft-365/security/office-365-security/turn-on-mdo-for-spo-odb-and-teams#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

1.  Ouvrez [et connectez-vous à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
1.  Exécutez la commande suivante : **Set-SPOTenant -DisallowInfectedFileDownload $true**.

### <a name="further-reading"></a>Lire plus en détail
[Recommandations de stratégie pour la sécurisation des sites et fichiers SharePoint](/microsoft-365/security/office-365-security/sharepoint-file-access-policies)
