---
title: Microsoft Teams
description: Comment Teams est installé sur les appareils et mis à jour par la suite
keywords: Microsoft Manged Desktop, Microsoft 365, service, documentation, applications, applications métier, applications métier
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: ITPro
ms.openlocfilehash: 21d69770fb16ac40b25cd9ff4fefd5ccf5b2f0fb
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62345938"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) [est une application](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) de messagerie qui fournit également un espace de travail pour la collaboration et la communication en temps réel, les réunions et le partage de fichiers et d’applications.

## <a name="initial-deployment"></a>Déploiement initial

La plupart des fournisseurs de matériel n’incluent pas encore Teams dans leurs images. Microsoft Manged Desktop déploie des Teams sur vos appareils à l’aide de Microsoft Intune. Tous les appareils gérés ont [le package Teams .msi installé](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works). Le package .msi garantit que tous les utilisateurs, qui se connectent à un appareil, Microsoft Teams prêt à l’emploi. Lorsque le package a terminé l’installation pour la première fois, Teams démarre automatiquement et ajoute un raccourci au Bureau.

### <a name="microsoft-intune-changes"></a>Microsoft Intune modifications

Microsoft Manged Desktop ajoute deux applications à votre organisation Azure AD pour Microsoft Teams. Ils sont déployés sur des clients 64 bits ou 32 bits selon les besoins de l’appareil :  

- Espace de travail moderne – Teams d’installation à l’échelle de l’ordinateur x64  
- Espace de travail moderne – Teams d’installation à l’échelle de l’ordinateur x32

## <a name="updates"></a>Mises à jour

Teams suit un chemin de mise à jour distinct de Applications Microsoft 365 pour les grandes entreprises. Le client de bureau se met à jour automatiquement. Teams recherche les mises à jour toutes les quelques heures, les télécharge, puis attend que l’ordinateur soit inactif avant d’installer silencieusement la mise à jour.  

Le Teams produit n’autorise pas les administrateurs à contrôler les mises à jour, Microsoft Manged Desktop utilise donc le canal de mise à jour [automatique standard](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>Mise à jour manuelle des Teams

Les utilisateurs individuels peuvent également télécharger les mises à jour. En haut à droite de l’application, dans la liste dropdown Profil, **sélectionnez Vérifier les mises à jour**. Si une mise à jour est disponible, elle est téléchargée et installée en mode silencieux lorsque l’ordinateur est inactif.

## <a name="delivery-optimization-of-updates"></a>Optimisation de la distribution des mises à jour

L’optimisation de la distribution Teams mises à jour est désactivée par défaut et ne nécessite aucune action de la part des administrateurs ou des utilisateurs.
