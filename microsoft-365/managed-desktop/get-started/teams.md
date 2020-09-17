---
title: Microsoft Teams
description: Comment teams est-il installé sur les appareils et mis à jour par la suite ?
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation, applications, applications métiers, applications métier
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
# <a name="microsoft-teams"></a>Microsoft Teams

[Teams](https://www.microsoft.com/microsoft-365/microsoft-teams/group-chat-software) est une [application de messagerie](https://support.microsoft.com/office/microsoft-teams-basics-6d5f52e6-5306-4096-ac24-c3082b79eaf0) pour votre organisation qui fournit également un espace de travail pour la collaboration et la communication en temps réel, les réunions et le partage de fichiers et d’applications.

## <a name="initial-deployment"></a>Déploiement initial

La plupart des fournisseurs de matériel n’incluent pas encore teams dans leurs images, de sorte que Microsoft Managed Desktop déploie teams sur vos appareils à l’aide de Microsoft Intune. Le [package Teams. msi](https://docs.microsoft.com/MicrosoftTeams/msi-deployment#how-the-microsoft-teams-msi-package-works) est installé sur tous les appareils gérés afin de s’assurer que Microsoft teams est prêt à utiliser tous les utilisateurs qui se connectent à un appareil. Une fois l’installation du package terminée, teams démarre automatiquement et ajoute un raccourci vers le bureau.

### <a name="microsoft-intune-changes"></a>Modifications apportées à Microsoft Intune

Microsoft Managed Desktop ajoute deux applications à votre organisation Azure AD pour Microsoft Teams. Elles sont déployées sur les clients 64 bits ou 32 bits en fonction du périphérique :  

- Espace de travail moderne – programme d’installation x64 à l’échelle de l’ordinateur teams  
- Espace de travail moderne – programme d’installation de l’ordinateur teams x32

## <a name="updates"></a>Mises à jour

Teams suit un chemin de mise à jour distinct de Microsoft 365 Apps for Enterprise et le client de bureau lui-même est automatiquement mis à jour. Teams vérifie les mises à jour toutes les quelques heures, les télécharge, puis attend que l’ordinateur soit inactif avant d’installer la mise à jour en silence.  

Le groupe de produits Teams ne permet pas aux administrateurs de contrôler les mises à jour, de sorte que Microsoft Managed Desktop utilise le [canal de mise à jour automatique standard](https://docs.microsoft.com/microsoftteams/teams-client-update#can-admins-deploy-updates-instead-of-teams-auto-updating).

### <a name="manually-updating-teams"></a>Mise à jour manuelle de teams

Les utilisateurs individuels peuvent également télécharger des mises à jour en sélectionnant **vérifier les mises à jour**   dans le **Profile**   menu déroulant Profil dans le coin supérieur droit de l’application. Si une mise à jour est disponible, elle est téléchargée et installée silencieusement lorsque l’ordinateur est inactif.

## <a name="delivery-optimization-of-updates"></a>Optimisation de la distribution des mises à jour

L’optimisation de la remise des mises à jour de teams est activée par défaut et ne nécessite aucune action de la part des administrateurs ou des utilisateurs. 