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
- m365-security
- SPO_Content
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Découvrez Microsoft Defender pour Office 365 pour les fichiers dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: e236fab4e3120e114f288e58ab3c7fe27aa1f6f4
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68087056"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams dans [Microsoft Defender pour Office 365](whats-new-in-defender-for-office-365.md) fournissent une couche supplémentaire de protection pour les fichiers qui ont déjà été analysés de manière asynchrone par le [moteur de détection de virus commun dans Microsoft 365](virus-detection-in-spo.md). Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams permettent de détecter et de bloquer les fichiers existants identifiés comme malveillants dans les sites d’équipe et les bibliothèques de documents.

Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams ne sont pas activées par défaut. Pour l’activer, consultez [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>Fonctionnement des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

Lorsque les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams sont activées et identifient un fichier comme malveillant, le fichier est verrouillé à l’aide de l’intégration directe avec les magasins de fichiers. L’image suivante illustre un exemple de fichier malveillant détecté dans une bibliothèque.

:::image type="content" source="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png" alt-text="Les fichiers dans OneDrive Entreprise avec un fichier détecté comme malveillant" lightbox="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png":::

Bien que le fichier bloqué soit toujours répertorié dans la bibliothèque de documents et dans les applications web, mobiles ou de bureau, les personnes ne peuvent pas ouvrir, copier, déplacer ou partager le fichier. Mais ils peuvent supprimer le fichier bloqué.

Voici un exemple de ce à quoi ressemble un fichier bloqué sur un appareil mobile :

:::image type="content" source="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png" alt-text="Option permettant de supprimer un fichier bloqué de OneDrive Entreprise de l’application mobile OneDrive" lightbox="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png":::

Par défaut, les personnes peuvent télécharger un fichier bloqué. Voici à quoi ressemble le téléchargement d’un fichier bloqué sur un appareil mobile :

:::image type="content" source="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png" alt-text="Option permettant de télécharger un fichier bloqué dans OneDrive Entreprise" lightbox="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png":::

Les administrateurs SharePoint Online peuvent empêcher les utilisateurs de télécharger des fichiers malveillants. Pour obtenir des instructions, consultez [Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

Pour en savoir plus sur l’expérience utilisateur lorsqu’un fichier a été détecté comme malveillant, voir [Que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Afficher des informations sur les fichiers malveillants détectés par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

Les fichiers identifiés comme malveillants par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams s’affichent dans [les rapports pour Microsoft Defender pour Office 365](view-reports-for-mdo.md) et dans [l’Explorateur (et les détections en temps réel).](threat-explorer.md)

Lorsqu’un fichier est identifié comme malveillant par des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams, le fichier est également disponible en quarantaine, mais uniquement pour les administrateurs. Pour plus d’informations, consultez [Gérer les fichiers en quarantaine dans Defender pour Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365).

## <a name="keep-these-points-in-mind"></a>Gardez ces points à l’esprit

- Defender pour Office 365 n’analyse pas tous les fichiers dans SharePoint Online, OneDrive Entreprise ou Microsoft Teams. Ce comportement est voulu par la conception même du produit. Les fichiers sont analysés de manière asynchrone. Le processus utilise des événements de partage et d’activité invité, ainsi que des heuristiques intelligentes et des signaux de menace pour identifier les fichiers malveillants.

- Assurez-vous que vos sites SharePoint sont configurés pour utiliser [l’expérience moderne](/sharepoint/guide-to-sharepoint-modern-experience). Defender pour Office 365 protection s’applique si l’expérience moderne ou la vue Classique est utilisée ; toutefois, les indicateurs visuels indiquant qu’un fichier est bloqué sont disponibles uniquement dans l’expérience moderne.

- Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams font partie de la stratégie globale de protection contre les menaces de votre organisation, qui inclut la protection anti-courrier indésirable et anti-programme malveillant dans Exchange Online Protection (EOP), ainsi que des liens sécurisés et des pièces jointes sécurisées dans Microsoft Defender pour Office 365. Pour en savoir plus, consultez [Protéger contre les menaces dans Office 365](protect-against-threats.md).
