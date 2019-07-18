---
title: Technologies de bureau géré Microsoft
description: Cette rubrique répertorie les technologies et les applications utilisées dans le bureau géré Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 914a90b4267132c9cb942740ceb974b084bcdf82
ms.sourcegitcommit: 2f4a61f02ea90102ded8e5d71c9b78a1f7f6b789
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2019
ms.locfileid: "35778089"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies de bureau géré Microsoft

Cette rubrique répertorie les technologies et les applications utilisées dans le bureau géré Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

La licence Microsoft 365 Enterprise est requise pour tous les utilisateurs du bureau géré Microsoft. Pour plus d’informations sur les exigences en matière de licences pour le service, reportez-vous à [Prerequisites for Microsoft Managed Desktop](../get-ready/prerequisites.md).

Vous trouverez ci-dessous tous les composants inclus dans les licences d’entreprise requises et la façon dont le service utilise chaque composant avec les appareils de bureau gérés Microsoft. Les rôles et responsabilités spécifiques de chaque domaine sont détaillés dans la rubrique Microsoft Managed Desktop. 

## <a name="office-365-e3"></a>Office 365 E3
 |
 --- | ---
Office 365 standard suite (64 bits) * | La suite d’applications Office standard sera livrée avec le périphérique: Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype entreprise, OneNote.<br><br>Le complément 64 bits Click to Run (C2R) versions complètes de Microsoft Project et Microsoft Visio ne sont pas inclus dans la suite Office 365 standard.  Toutefois, étant donné que l’installation de ces applications dépend de l’installation de la suite Office standard, le bureau géré Microsoft a créé des déploiements Intune et des groupes de sécurité par défaut que le client utilisera pour déployer ces applications sur utilisateurs finaux sous licence.  
Applications du Store |    Microsoft Sway, Power BI Desktop n’est pas fourni avec le périphérique. Ces applications peuvent être téléchargées à partir du Microsoft Store.
Applications Win32 |    Power BI Pro, Azure information protection client et le planificateur Microsoft ne sont pas fournis avec le périphérique et peuvent être empaquetés pour être déployés par le client. 
Applications Web |  Yammer, Office dans un navigateur, Delve, Flow, StaffHub, PowerApp ne sont pas livrés avec l’appareil. Les utilisateurs peuvent accéder à la version Web de ces applications à l’aide d’un navigateur.
PBX Cloud Skype entreprise Online | Cette fonctionnalité est disponible via Office 365. Microsoft Managed Desktop ne configure aucun aspect de ce service.

## <a name="windows-10-enterprise-e5"></a>Windows 10 entreprise E5

 |
 --- | ---
Credential Guard |  Microsoft fournira des conseils et gérera les aspects de Cloud de cette fonctionnalité.
Virtualisation d’application (App-V) |    Microsoft Managed Desktop ne prend pas en charge ce type de déploiement car il n’est pas pris en charge sur Intune.
Virtualisation de l’expérience utilisateur (UE-V) | Cela n’est pas utilisé avec les appareils gérés de bureau géré Microsoft.
Expérience utilisateur gérée  | Cela n’est pas utilisé avec les appareils gérés de bureau géré Microsoft. MDM est utilisé comme solution pour la gestion des appareils.
Protection avancée contre les menaces Microsoft Defender | Cette fonctionnalité est utilisée par le bureau géré Microsoft pour gérer les stratégies de sécurité des appareils. 

## <a name="enterprise-mobility--security-e5"></a>Enterprise Mobility + Security E5

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Tous les aspects de l’Enterprise Mobility + Security E3 et AADP peuvent être utilisés pour gérer les appareils MDM.
Microsoft Cloud App Security |  Il s’agit d’une fonctionnalité facultative que les clients peuvent utiliser avec le service Microsoft Managed Desktop.
Azure information protection P2  |Il s’agit d’une fonctionnalité facultative que les clients peuvent utiliser avec le service Microsoft Managed Desktop.
