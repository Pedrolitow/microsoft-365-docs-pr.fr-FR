---
title: Technologies associées de Bureau géré Microsoft
description: Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: cb368939e87ddbbfc8f5386c6fc5d6bff110a7ec
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49840900"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies associées de Bureau géré Microsoft

Cet article répertorie les technologies et applications utilisées dans bureau géré Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

La gestion des licences Microsoft 365 Entreprise est requise pour tous les utilisateurs du Bureau géré Microsoft. Pour plus d’informations sur les conditions requises en matière de licences pour le service, voir [Prerequisites for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Cet article récapitule les composants inclus dans les licences d’entreprise requises, avec une description de la façon dont le service utilise chaque composant avec les appareils bureau géré Microsoft. Les rôles et responsabilités spécifiques pour chaque domaine sont détaillés dans la documentation du Bureau géré Microsoft. 

## <a name="office-365-e3-or-e5"></a>Office 365 E3 ou E5
 |
 --- | ---
Applications Microsoft 365 pour les entreprises (64 bits) | Ces applications Office seront livrées avec l’appareil : Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype Entreprise, OneNote.<br><br>Les versions complètes 64 bits de Microsoft Project et Microsoft Visio ne sont pas incluses. Toutefois, étant donné que l’installation de ces applications dépend de l’installation des applications Microsoft 365 pour les entreprises, Bureau géré Microsoft a créé des déploiements et des groupes de sécurité Microsoft Intune par défaut que vous pouvez ensuite utiliser pour déployer ces applications pour les utilisateurs sous licence. Pour plus d’informations, voir [Installer Microsoft Project ou Microsoft Visio sur les appareils de bureau géré Microsoft.](../get-started/project-visio.md)
OneDrive |L’ion unique Azure Active Directory est activée pour les utilisateurs lorsqu’ils se connectent pour la première fois à OneDrive.<br><br>La redirection de dossiers connue pour les dossiers « Bureau », « Document » et « Images » est incluse ; activé et configuré par Bureau géré Microsoft.
Store Apps |    Microsoft Sway et Power BI ne sont pas livrés avec l’appareil. Ces applications sont disponibles en téléchargement à partir du Microsoft Store.
Win32 Applications |    Teams n’est pas fourni avec l’appareil, mais il est empaqueté et fourni par Microsoft pour les appareils bureau géré Microsoft. Le client Azure Information Protection n’est pas livré avec l’appareil, mais vous pouvez le faire empaqueté pour le déploiement.
Applications Web |  Yammer, Office dans un navigateur, Delve, Flow, StaffHub, PowerApps et planner ne sont pas livrés avec l’appareil. Les utilisateurs peuvent accéder à la version web de ces applications avec un navigateur.


## <a name="windows-10-enterprise-e5-or-e3-with-microsoft-defender-for-endpoint"></a>Windows 10 Entreprise E5 ou E3 avec Microsoft Defender pour Point de terminaison

 |
 --- | ---
Application Virtualization (App-V) |    Les clients peuvent déployer des packages App-V à l’aide du client de gestion des applications Intune Win32.
Microsoft Defender pour point de terminaison |    Bureau géré Microsoft utilise ce produit pour surveiller la sécurité des appareils. 

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Vous pouvez utiliser toutes les fonctionnalités d’Enterprise Mobility + Security E3 et Azure Active Directory Premium P2 pour gérer les appareils GDM.
Microsoft Cloud App Security |  Vous pouvez utiliser cette fonctionnalité facultative avec Bureau géré Microsoft.
Azure Information Protection P2  | Vous pouvez utiliser cette fonctionnalité facultative avec Bureau géré Microsoft.
