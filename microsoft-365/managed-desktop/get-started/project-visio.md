---
title: Installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft
description: Informations sur l'installation de Microsoft Project ou de Microsoft Visio sur des appareils de bureau gérés Microsoft
keywords: Microsoft maNaged Desktop, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5c820e36b7b397fe770216ee229e38a1da5b034d
ms.sourcegitcommit: aba6d1b81e4c579e82e6fad90daec65d775b450a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "30573418"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft

Microsoft Project et Microsoft Visio nécessitent l'installation de procédures spécifiques sur les appareils de bureau gérés par Microsoft. Cette rubrique décrit les conditions préalables et le processus d'installation de ces applications.

## <a name="prerequisites"></a>Conditions requises

Les administrateurs doivent vérifier qu'ils satisfont aux conditions préalables suivantes:
- **Quantités de licences** : la quantité correcte de licences Microsoft Project et Microsoft Visio doit être disponible pour vos utilisateurs. Microsoft maNaged Desktop ne prend actuellement en charge que les versions 64 bits de ces applications. 
- **Noms de licences** : les noms de licences appropriés pour ces applications sont les suivants:
    - **Microsoft Project** -Project Online professionnel ou Project Online Premium
    - **Microsoft Visio** -Visio Online-plan 2
- **Portail d'entreprise** : le portail de l'entreprise doit être disponible dans votre client pour permettre à vos utilisateurs d'installer ces applications. Si le portail d'entreprise n'est pas déployé dans votre client, reportez-vous à la rubrique [entreprise Portal](company-portal.md).

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Déployer Project et Visio pour les appareils de bureau gérés Microsoft
Une fois que vous avez soumis votre demande de support, le bureau géré Microsoft crée trois groupes Azure AD et trois déploiements d'application via Microsoft Intune pour déployer les applications sur votre client.  

**Pour déployer Project et Visio**
1. **Classer une demande de support** Les administrateurs informatiques doivent classer une demande de support pour mettre ces applications à disposition de leurs utilisateurs. Pour plus d'informations sur la façon de contacter le bureau géré Microsoft, consultez la rubrique [administrateur pris en charge pour Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).
2. **Affecter des utilisateurs à de nouveaux groupes Azure ad** Le bureau géré Microsoft créera 3 groupes Azure AD dans votre client et 3 déploiements d'applications correspondants. Les administrateurs informatiques doivent affecter les utilisateurs aux groupes appropriés.

>[!NOTE]
>Affectez des utilisateurs à un seul de ces groupes Azure AD. 

Nom du groupe Azure AD | Quels utilisateurs affecter?   
 --- | ---
Microsoft-Office-Project-installation | Les utilisateurs qui ont besoin d'un projet uniquement
Microsoft-Office-Visio-install | Les utilisateurs qui ont uniquement besoin de Visio
Microsoft-Office-Project et installation de Visio | Utilisateurs ayant besoin à la fois de Project et de Visio

Une fois affectées à ces groupes, les applications sont disponibles dans le portail de l'entreprise. La synchronisation peut prendre quelques minutes, mais les utilisateurs peuvent alors installer les applications à partir du portail d'entreprise. 

## <a name="communicate-changes"></a>Communication des modifications
Il est important que les administrateurs informatiques sachent comment installer Project et Visio. Celles-ci incluent les valeurs suivantes : 
- Avertir les utilisateurs lorsque ces applications sont disponibles. 
- Instructions sur l'installation de ces applications à partir du portail de l'entreprise.

>[!NOTE]
>Les utilisateurs doivent fermer toutes les applications Office avant d'installer Microsoft Project ou Microsoft Visio à partir du portail d'entreprise. 
