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
localization_priority: Normal
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
description: Découvrez Microsoft Defender pour Office 365 pour les fichiers dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 640867cb38dab650bca990fe36c0b7cea7f6a0d8
ms.sourcegitcommit: 3dc795ea862b180484f76b3eb5d046e74041252b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2021
ms.locfileid: "50175726"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Les pièces jointes fiables pour SharePoint, OneDrive et Microsoft Teams dans Microsoft Defender pour [Office 365](office-365-atp.md) fournissent une couche supplémentaire de protection pour les fichiers qui ont déjà été analysés au moment du chargement par le moteur de détection de virus courant dans [Microsoft 365.](virus-detection-in-spo.md) Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams permettent de détecter et de bloquer les fichiers existants identifiés comme malveillants dans les sites d’équipe et les bibliothèques de documents.

Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams ne sont pas activées par défaut. Pour l’activer, voir [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.](turn-on-atp-for-spo-odb-and-teams.md)

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>Fonctionnement des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

Lorsque les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams sont activées et identifient un fichier comme malveillant, le fichier est verrouillé à l’aide de l’intégration directe avec les magasins de fichiers. L’image suivante illustre un exemple de fichier malveillant détecté dans une bibliothèque.

![Fichiers dans OneDrive Entreprise avec un fichier détecté comme malveillant](../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png)

Bien que le fichier bloqué soit toujours répertorié dans la bibliothèque de documents et dans les applications web, mobiles ou de bureau, les utilisateurs ne peuvent pas ouvrir, copier, déplacer ou partager le fichier. Toutefois, ils peuvent supprimer le fichier bloqué.

Voici un exemple de ce à quoi ressemble un fichier bloqué sur un appareil mobile :

![Suppression d’un fichier bloqué de OneDrive Entreprise de l’application mobile OneDrive](../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png)

Par défaut, les personnes peuvent télécharger un fichier bloqué. Voici à quoi ressemble le téléchargement d’un fichier bloqué sur un appareil mobile :

![Téléchargement d’un fichier bloqué dans OneDrive Entreprise](../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png)

Les administrateurs SharePoint Online peuvent empêcher les utilisateurs de télécharger des fichiers malveillants. Pour obtenir des instructions, [voir Utiliser SharePoint Online PowerShell](turn-on-atp-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files)pour empêcher les utilisateurs de télécharger des fichiers malveillants.

Pour en savoir plus sur l’expérience utilisateur lorsqu’un fichier a été détecté comme malveillant, voir ce qu’il faut faire lorsqu’un fichier malveillant est trouvé dans [SharePoint Online, OneDrive](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)ou Microsoft Teams.

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Afficher des informations sur les fichiers malveillants détectés par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

Les fichiers identifiés comme malveillants par Microsoft Defender pour Office 365 s’afficheront dans les rapports de Microsoft Defender pour [Office 365](view-reports-for-atp.md) et dans l’Explorateur [(et détections](threat-explorer.md)en temps réel).

Depuis mai 2018, lorsqu’un fichier est identifié comme malveillant par Microsoft Defender pour Office 365, le fichier est également disponible en quarantaine. Pour plus d’informations, voir Le Centre de sécurité [& conformité pour gérer les fichiers mis en quarantaine.](manage-quarantined-messages-and-files.md#microsoft-defender-for-office-365-only-use-the-security--compliance-center-to-manage-quarantined-files)

## <a name="keep-these-points-in-mind"></a>Gardez ces points à l’esprit

- Defender pour Office 365 n’analyse pas tous les fichiers dans SharePoint Online, OneDrive Entreprise ou Microsoft Teams. Ce comportement est voulu par la conception même du produit. Les fichiers sont analysés de manière asynchrone. Le processus utilise les événements de partage et d’activité invité, ainsi que les signaux heuristiques intelligents et les signaux de menace pour identifier les fichiers malveillants.

- Assurez-vous que vos sites SharePoint sont configurés pour utiliser [l’expérience moderne.](https://docs.microsoft.com/sharepoint/guide-to-sharepoint-modern-experience) La protection Defender pour Office 365 s’applique que l’expérience moderne ou l’affichage classique soit utilisé . toutefois, les indicateurs visuels qui montrent qu’un fichier est bloqué sont disponibles uniquement dans l’expérience moderne.

- Les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams font partie de la stratégie globale de protection contre les menaces de votre organisation, qui inclut la protection contre le courrier indésirable et les programmes malveillants dans Exchange Online Protection (EOP), ainsi que les liens et pièces jointes sûrs dans Microsoft Defender pour Office 365. Pour en savoir plus, consultez La protection contre [les menaces dans Office 365.](protect-against-threats.md)
