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
ms.openlocfilehash: 3ea75323b56941b47e8bf9826c0bfeeb7d8983f9
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62034796"
---
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) est une [](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) application de messagerie pour votre organisation qui fournit également un espace de travail pour la collaboration et la communication en temps réel, les réunions et le partage de fichiers et d’applications.

## <a name="initial-deployment"></a>Déploiement initial

La plupart des fournisseurs de matériel n’incluent pas encore Teams dans leurs images. Par Microsoft Manged Desktop déploie Teams sur vos appareils à l’aide de Microsoft Intune. Tous les appareils gérés ont [le package Teams .msi](/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) installé, ce qui garantit que tous les utilisateurs qui se connectent à un appareil Microsoft Teams prêt à l’emploi. Lorsque le package a terminé l’installation pour la première fois, Teams démarre automatiquement et ajoute un raccourci au Bureau.

### <a name="microsoft-intune-changes"></a>Microsoft Intune modifications

Microsoft Manged Desktop ajoute deux applications à votre organisation Azure AD pour Microsoft Teams. Ils sont déployés sur des clients 64 bits ou 32 bits selon les besoins de l’appareil :  

- Espace de travail moderne – Teams d’installation à l’échelle de l’ordinateur x64  
- Espace de travail moderne – Teams d’installation à l’échelle de l’ordinateur x32

## <a name="updates"></a>Mises à jour

Teams suit un chemin de mise à jour distinct de Applications Microsoft 365 pour les grandes entreprises et le client de bureau se met à jour automatiquement. Teams recherche les mises à jour toutes les quelques heures, les télécharge, puis attend que l’ordinateur soit inactif avant d’installer silencieusement la mise à jour.  

Le groupe Teams produit n’autorise pas les administrateurs à contrôler les mises à jour. Par Microsoft Manged Desktop utilise le canal de mise à jour automatique [standard.](/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating)

### <a name="manually-updating-teams"></a>Mise à jour manuelle des Teams

Les utilisateurs individuels peuvent également télécharger les mises à jour en sélectionnant Vérifier les mises à jour dans le menu déroulant Profil en   haut à droite de ****   l’application. Si une mise à jour est disponible, elle est téléchargée et installée en mode silencieux lorsque l’ordinateur est inactif.

## <a name="delivery-optimization-of-updates"></a>Optimisation de la distribution des mises à jour

L’optimisation de la distribution Teams mises à jour est désactivée par défaut et ne nécessite aucune action de la part des administrateurs ou des utilisateurs.