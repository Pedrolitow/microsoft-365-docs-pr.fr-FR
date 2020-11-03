---
title: Protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.service: O365-seccomp
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
description: Découvrez Microsoft Defender pour Office 365 pour les fichiers dans SharePoint Online, OneDrive entreprise et Microsoft Teams.
ms.openlocfilehash: 7b007671a7fecb3ae074fd07ce38d17fb025f6b4
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844331"
---
# <a name="atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

La protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams dans [Microsoft Defender pour Office 365](office-365-atp.md) fournit une couche supplémentaire de protection pour les fichiers qui ont déjà été analysés au moment du chargement par le [moteur de détection de virus courant dans Microsoft 365](virus-detection-in-spo.md). La protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams permet de détecter et de bloquer les fichiers existants identifiés comme étant malveillants dans les sites d’équipe et les bibliothèques de documents.

La protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams n’est pas activée par défaut. Pour l’activer, voir Activer la protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md).

## <a name="how-atp-for-sharepoint-onedrive-and-microsoft-teams-works"></a>Fonctionnement de la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams

Lorsque la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams est activée et identifie un fichier comme malveillant, le fichier est verrouillé à l’aide de l’intégration directe aux magasins de fichiers. L’image suivante montre un exemple de fichier malveillant détecté dans une bibliothèque.

![Fichiers dans OneDrive entreprise avec un fichier détecté comme malveillant](../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png)

Bien que le fichier bloqué figure toujours dans la bibliothèque de documents et dans les applications Web, mobiles ou de bureau, les utilisateurs ne peuvent pas ouvrir, copier, déplacer ou partager le fichier. Mais ils peuvent supprimer le fichier bloqué.

Voici un exemple de ce à quoi ressemble un fichier bloqué sur un appareil mobile :

![Suppression d’un fichier bloqué de OneDrive entreprise à partir de l’application mobile OneDrive](../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png)

Par défaut, les utilisateurs peuvent télécharger un fichier bloqué. Voici ce à quoi ressemble un fichier bloqué sur un appareil mobile :

![Téléchargement d’un fichier bloqué dans OneDrive entreprise](../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png)

Les administrateurs SharePoint Online peuvent empêcher les utilisateurs de télécharger des fichiers malveillants. Pour obtenir des instructions, consultez la rubrique [utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](turn-on-atp-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

Pour en savoir plus sur l’expérience utilisateur lorsqu’un fichier a été détecté comme malveillant, consultez la rubrique [que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="view-information-about-malicious-files-detected-by-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Afficher des informations sur les fichiers malveillants détectés par la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams

Les fichiers identifiés comme étant malveillants par Microsoft Defender pour Office 365 s’afficheront dans des [rapports pour Microsoft Defender pour office 365](view-reports-for-atp.md) et dans l' [Explorateur (et les détections en temps réel)](threat-explorer.md).

En ce qui concerne le 2018 mai, lorsqu’un fichier est identifié comme malveillant par Microsoft Defender pour Office 365, le fichier est également disponible en quarantaine. Pour plus d’informations, consultez [la rubrique utiliser le centre de sécurité & conformité pour gérer les fichiers mis en quarantaine](manage-quarantined-messages-and-files.md#microsoft-defender-for-office-365-only-use-the-security--compliance-center-to-manage-quarantined-files).

## <a name="keep-these-points-in-mind"></a>Gardez les points suivants à l’esprit

- Defender pour Office 365 n’analyse pas tous les fichiers dans SharePoint Online, OneDrive entreprise ou Microsoft Teams. Ce comportement est voulu par la conception même du produit. Les fichiers sont analysés de manière asynchrone. Le processus utilise les événements d’activité de partage et d’invité, ainsi que les heuristiques intelligentes et les signaux de menace pour identifier les fichiers malveillants.

- Assurez-vous que vos sites SharePoint sont configurés pour utiliser l' [expérience moderne](https://docs.microsoft.com/sharepoint/guide-to-sharepoint-modern-experience). La protection Defender pour Office 365 s’applique si l’expérience moderne ou l’affichage classique est utilisé ; Toutefois, les indicateurs visuels signalant qu’un fichier est bloqué sont disponibles uniquement dans l’expérience moderne.

- La protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams fait partie de la stratégie globale de protection contre les menaces de votre organisation, qui inclut la protection contre le courrier indésirable et les programmes malveillants dans Exchange Online Protection (EOP), ainsi que les liens fiables et les pièces jointes fiables dans Microsoft Defender pour Office 365. Pour en savoir plus, consultez la rubrique [Protégez-vous contre les menaces dans Office 365](protect-against-threats.md).
