---
title: Installer Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils
description: Informations sur l’installation Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils
keywords: Microsoft Manged Desktop, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: medium
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: af5470d0993c54c1593526a7e0e3ae0b6e239065
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60199788"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Installer Microsoft Project ou Microsoft Visio sur Microsoft Manged Desktop appareils

Microsoft Project et Microsoft Visio des étapes spécifiques doivent être installées sur Microsoft Manged Desktop appareils. Cette rubrique documente les conditions préalables et le processus d’installation de ces applications.

## <a name="prerequisites"></a>Configuration requise

Les administrateurs doivent vérifier qu’ils répondent aux conditions préalables ci-après :
- **Quantités de licences** : le nombre correct de licences Microsoft Project et microsoft Visio licences doit être disponible pour vos utilisateurs. Microsoft Manged Desktop ne prend actuellement en charge que les versions 64 bits de ces applications. 
- **Noms de licence** : les noms de licence appropriés pour ces applications sont les éléments ci-après :
    - **Microsoft Project** - Project Online Professionnel ou Project Online Premium
    - **Microsoft Visio** - Visio Online Plan 2
- **Portail d'entreprise** - Le Portail d'entreprise doit être disponible dans votre client pour que vos utilisateurs installent ces applications. Si le Portail d'entreprise n’est pas déployé dans votre client, voir [Portail d'entreprise](company-portal.md).

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Déployer des Project et des Visio pour Microsoft Manged Desktop appareils
Microsoft Manged Desktop ajoutera Microsoft Project et Microsoft Visio en tant que deux applications Win32 dans Microsoft Intune. Nous allons également créer deux groupes dans Azure Active Directory qui seront affectés à l’application correspondante avec l’intention « Disponible ». 

**Pour déployer Project et Visio** Ajoutez l’utilisateur au groupe approprié et l’application sera disponible dans le Portail d'entreprise. La synchronisation peut prendre quelques minutes, mais vos utilisateurs peuvent ensuite installer les applications à partir Portail d'entreprise. 

Nom du groupe Azure AD | Quels utilisateurs attribuer ?   
 --- | ---
Espace de travail moderne Office-Project_Install | Utilisateurs qui ont besoin de Project
Espace de travail moderne Office-Visio_Install | Utilisateurs qui ont besoin de Visio

## <a name="communicate-changes"></a>Communiquer les modifications
Il est important pour les administrateurs informatiques de faire savoir à leurs utilisateurs comment installer Project et Visio. Cela inclut les opérations suivantes : 
- Avertir les utilisateurs lorsque ces applications sont à leur disposition. 
- Instructions sur l’installation de ces applications à partir du Portail d'entreprise.
