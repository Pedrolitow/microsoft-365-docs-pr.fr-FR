---
title: Microsoft Teams
description: Installation de Teams sur les appareils et mise à jour par la suite
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation, applications, applications métier, applications métier
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: ITPro
ms.openlocfilehash: ea2ef7637a8d360e3b598aec4852425d977ae4ec
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950917"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) est une application [de](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) messagerie pour votre organisation qui fournit également un espace de travail pour la collaboration et la communication en temps réel, les réunions et le partage de fichiers et d’applications.

## <a name="initial-deployment"></a>Déploiement initial

La plupart des fournisseurs de matériel n’incluent pas encore Teams dans le cadre de leurs images. Ainsi, Bureau géré Microsoft déploie Teams sur vos appareils à l’aide de Microsoft Intune. Sur tous les appareils gérés, le [package .msi Teams](https://docs.microsoft.com/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) est installé, ce qui garantit que Microsoft Teams est prêt à être utilisé par tous les utilisateurs qui se connectent à un appareil. Lorsque le package a terminé l’installation pour la première fois, Teams démarre automatiquement et ajoute un raccourci au Bureau.

### <a name="microsoft-intune-changes"></a>Modifications apportées à Microsoft Intune

Bureau géré Microsoft ajoute deux applications à votre organisation Azure AD pour Microsoft Teams. Ils sont déployés sur des clients 64 bits ou 32 bits selon les besoins de l’appareil :  

- Espace de travail moderne – Programme d’installation à l’échelle de l’ordinateur Teams x64  
- Espace de travail moderne – Programme d’installation à l’échelle de l’ordinateur Teams x32

## <a name="updates"></a>Mises à jour

Teams suit un chemin de mise à jour distinct de Microsoft 365 Apps for enterprise et le client de bureau se met à jour automatiquement. Teams recherche les mises à jour toutes les heures, les télécharge, puis attend que l’ordinateur soit inactif avant d’installer silencieusement la mise à jour.  

Le groupe de produits Teams n’autorise pas les administrateurs à contrôler les mises à jour, donc Bureau géré Microsoft utilise le canal de mise à jour [automatique standard.](https://docs.microsoft.com/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating)

### <a name="manually-updating-teams"></a>Mise à jour manuelle de Teams

Les utilisateurs individuels peuvent également télécharger les mises à jour en sélectionnant Vérifier les mises à jour dans le menu déroulant Profil en   haut à droite de ****   l’application. Si une mise à jour est disponible, elle est téléchargée et installée en mode silencieux lorsque l’ordinateur est inactif.

## <a name="delivery-optimization-of-updates"></a>Optimisation de la distribution des mises à jour

L’optimisation de la distribution pour les mises à jour Teams est désactivée par défaut et ne nécessite aucune action de la part des administrateurs ou des utilisateurs. 