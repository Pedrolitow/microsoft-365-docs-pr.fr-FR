---
title: Installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft
description: Informations sur l’installation de Microsoft Project ou de Microsoft Visio sur des appareils de bureau gérés Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, Microsoft Project, Microsoft Visio
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.date: 03/07/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: c04bcdf846bafaa7838ef5932c8de595f5035992
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950531"
---
# <a name="install-microsoft-project-or-microsoft-visio-on-microsoft-managed-desktop-devices"></a>Installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft

Microsoft Project et Microsoft Visio nécessitent l’installation de procédures spécifiques sur les appareils de bureau gérés par Microsoft. Cette rubrique décrit les conditions préalables et le processus d’installation de ces applications.

## <a name="prerequisites"></a>Conditions préalables

Les administrateurs doivent vérifier qu’ils satisfont aux conditions préalables suivantes :
- **Quantités de licences** : la quantité correcte de licences Microsoft Project et Microsoft Visio doit être disponible pour vos utilisateurs. Microsoft Managed Desktop ne prend actuellement en charge que les versions 64 bits de ces applications. 
- **Noms de licences** : les noms de licences appropriés pour ces applications sont les suivants :
    - **Microsoft Project** -Project Online professionnel ou Project Online Premium
    - **Microsoft Visio** -Visio Online-plan 2
- **Portail d’entreprise** : le portail de l’entreprise doit être disponible dans votre client pour permettre à vos utilisateurs d’installer ces applications. Si le portail d’entreprise n’est pas déployé dans votre client, reportez-vous à la rubrique [entreprise Portal](company-portal.md).

## <a name="deploy-project-and-visio-for-microsoft-managed-desktop-devices"></a>Déployer Project et Visio pour les appareils de bureau gérés Microsoft
Microsoft Managed Desktop ajoute Microsoft Project et Microsoft Visio sous la forme de deux applications Win32 dans Microsoft Intune. Nous allons également créer deux groupes dans Azure Active Directory qui seront affectés à l’application correspondante avec l’intention « disponible ». 

**Pour déployer Project et Visio** Ajoutez l’utilisateur au groupe approprié et l’application deviendra disponible dans le portail de l’entreprise. La synchronisation peut prendre quelques minutes, mais les utilisateurs peuvent alors installer les applications à partir du portail d’entreprise. 

Nom du groupe Azure AD | Quels utilisateurs affecter ?   
 --- | ---
Espace de travail moderne-Bureau-Project_Install | Utilisateurs ayant besoin d’un projet
Espace de travail moderne-Bureau-Visio_Install | Utilisateurs qui ont besoin de Visio

## <a name="communicate-changes"></a>Communication des modifications
Il est important que les administrateurs informatiques sachent comment installer Project et Visio. Cela inclut les opérations suivantes : 
- Avertir les utilisateurs lorsque ces applications sont disponibles. 
- Instructions sur l’installation de ces applications à partir du portail de l’entreprise.
