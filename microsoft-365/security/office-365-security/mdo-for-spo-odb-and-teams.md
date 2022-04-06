---
title: Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 26261670-db33-4c53-b125-af0662c34607
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Découvrez Microsoft Defender pour Office 365 fichiers dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 220bb976ebe701e5db5f03370a1a7c188f197cb1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475760"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Coffre attachments for SharePoint, OneDrive, and Microsoft Teams in [Microsoft Defender for Office 365](whats-new-in-defender-for-office-365.md) provides an additional layer of protection for files that have already been scanned asynchronously by the [common virus detection engine in Microsoft 365](virus-detection-in-spo.md). Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams permet de détecter et de bloquer les fichiers existants identifiés comme malveillants dans les sites d’équipe et les bibliothèques de documents.

Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams ne sont pas activées par défaut. Pour l’activer, voir [Activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>Fonctionnement Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams pièces jointes

Lorsque Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams est activée et identifie un fichier comme malveillant, le fichier est verrouillé à l’aide de l’intégration directe avec les magasins de fichiers. L’image suivante illustre un exemple de fichier malveillant détecté dans une bibliothèque.

:::image type="content" source="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png" alt-text="Fichiers dans OneDrive Entreprise avec un détecté comme malveillant" lightbox="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png":::

Bien que le fichier bloqué soit toujours répertorié dans la bibliothèque de documents et dans les applications web, mobiles ou de bureau, les personnes ne peuvent pas ouvrir, copier, déplacer ou partager le fichier. Mais ils peuvent supprimer le fichier bloqué.

Voici un exemple de ce à quoi ressemble un fichier bloqué sur un appareil mobile :

:::image type="content" source="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png" alt-text="Option de suppression d’un fichier bloqué de l OneDrive Entreprise de l’application OneDrive mobile" lightbox="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png":::

Par défaut, les personnes peuvent télécharger un fichier bloqué. Voici à quoi ressemble le téléchargement d’un fichier bloqué sur un appareil mobile :

:::image type="content" source="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png" alt-text="Option de téléchargement d’un fichier bloqué dans OneDrive Entreprise" lightbox="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png":::

SharePoint en ligne peuvent empêcher les utilisateurs de télécharger des fichiers malveillants. Pour obtenir des instructions, voir Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de [télécharger des fichiers malveillants](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

Pour en savoir plus sur l’expérience utilisateur lorsqu’un fichier a été détecté comme malveillant, voir comment faire lorsqu’un fichier malveillant est trouvé dans [SharePoint Online, OneDrive ou Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Afficher des informations sur les fichiers malveillants détectés par Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams

Les fichiers identifiés comme malveillants par les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams s’afficheront dans les rapports de [Microsoft Defender pour Office 365](view-reports-for-mdo.md) et dans l’Explorateur (et les [détections](threat-explorer.md) en temps réel).

Lorsqu’un fichier est identifié comme malveillant par des pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams, le fichier est également disponible en quarantaine, mais uniquement pour les administrateurs. Pour plus d’informations, voir [Gérer les fichiers mis en quarantaine dans Defender pour Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365).

## <a name="keep-these-points-in-mind"></a>Gardez ces points à l’esprit

- Defender for Office 365 n’analyse pas chaque fichier dans SharePoint Online, OneDrive Entreprise ou Microsoft Teams. Ce comportement est voulu par la conception même du produit. Les fichiers sont analysés de manière asynchrone. Le processus utilise les événements de partage et d’activité invité, ainsi que les signaux heuristiques intelligents et les signaux de menace pour identifier les fichiers malveillants.

- Assurez-vous que SharePoint sites sont configurés pour utiliser [l’expérience moderne](/sharepoint/guide-to-sharepoint-modern-experience). Defender pour Office 365 protection s’applique que l’expérience moderne ou l’affichage classique soit utilisé ; toutefois, les indicateurs visuels qui montrent qu’un fichier est bloqué sont disponibles uniquement dans l’expérience moderne.

- Coffre attachments for SharePoint, OneDrive, and Microsoft Teams is part of your organization’s overall threat protection strategy, which includes anti-spam and anti-malware protection in Exchange Online Protection (EOP), as well as Coffre liens et Coffre pièces jointes dans Microsoft Defender pour Office 365. Pour plus d’informations, voir [Protéger contre les menaces dans Office 365](protect-against-threats.md).
