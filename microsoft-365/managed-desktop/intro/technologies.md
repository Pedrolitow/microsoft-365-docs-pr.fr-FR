---
title: Technologies de bureau géré Microsoft
description: Cette rubrique répertorie les technologies et les applications utilisées dans le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 9f3094b1a1272b0c200271b8d5703fe7173683a6
ms.sourcegitcommit: 6b5370cded5d8259c9ed561eed324227f74c410b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "36171734"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies de bureau géré Microsoft

Cette rubrique répertorie les technologies et les applications utilisées dans le bureau géré Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

La licence Microsoft 365 Enterprise est requise pour tous les utilisateurs du bureau géré Microsoft. Pour plus d’informations sur les exigences en matière de licences pour le service, reportez-vous à [Prerequisites for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Cette rubrique résume les composants inclus dans les licences d’entreprise requises, ainsi qu’une description de la manière dont le service utilise chaque composant avec les appareils de bureau gérés Microsoft. Les rôles et responsabilités spécifiques de chaque domaine sont détaillés dans la documentation du bureau géré Microsoft. 

## <a name="office-365-e3"></a>Office 365 E3
 |
 --- | ---
Office 365 standard suite (64 bits) | La suite d’applications Office standard sera livrée avec le périphérique: Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype entreprise, OneNote.<br><br>Le 64-bit Click to Run (C2R) versions complètes de Microsoft Project et Microsoft Visio ne sont pas inclus dans Office 365. Toutefois, étant donné que l’installation de ces applications dépend de l’installation de la suite Office standard, le bureau géré Microsoft a créé des déploiements Microsoft Intune et des groupes de sécurité par défaut, que vous pouvez ensuite utiliser pour déployer ces applications sur utilisateurs finaux sous licence. Pour plus d’informations, consultez la rubrique [installer Microsoft Project ou Microsoft Visio sur des appareils de bureau gérés Microsoft](../get-started/project-visio.md)  
Applications du Store |    Microsoft Sway et Power BI ne sont pas fournis avec l’appareil. Ces applications peuvent être téléchargées à partir du Microsoft Store.
Applications Win32 |    Teams n’est pas fourni avec le périphérique, mais il est empaqueté et fourni par Microsoft pour les appareils de bureau gérés par Microsoft. Le client Azure information protection n’est pas livré avec l’appareil, mais vous pouvez en faire un package pour le déploiement. 
Applications Web |  Yammer, Office dans un navigateur, Delve, Flow, StaffHub, PowerApps et Planner ne sont pas fournis avec l’appareil. Les utilisateurs peuvent accéder à la version Web de ces applications à l’aide d’un navigateur.


## <a name="windows-10-enterprise-e5"></a>Windows 10 entreprise E5

 |
 --- | ---
Virtualisation d’application (App-V) |    Microsoft Managed Desktop ne prend pas en charge ce type de déploiement car il n’est pas pris en charge par Microsoft Intune.
Protection avancée contre les menaces Microsoft Defender |  Microsoft Managed Desktop utilise cette fonctionnalité pour surveiller la sécurité des appareils. 

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Vous pouvez utiliser toutes les fonctionnalités de Enterprise Mobility + Security E3 et Azure Active Directory Premium P2 pour gérer les appareils MDM.
Microsoft Cloud App Security |  Vous pouvez utiliser cette fonctionnalité facultative avec le bureau géré Microsoft.
Azure information protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec le bureau géré Microsoft.
