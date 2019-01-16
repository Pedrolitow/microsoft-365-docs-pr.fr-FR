---
title: Technologies de bureau Microsoft
description: Cette rubrique répertorie les technologies et les applications utilisées dans l’ordinateur de bureau Microsoft.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 4b26ec88e1f4ca95fee6f7c4c927fc06cab32135
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867044"
---
# <a name="microsoft-managed-desktop-technologies"></a>Technologies de bureau Microsoft

Cette rubrique répertorie les technologies et les applications utilisées dans l’ordinateur de bureau Microsoft.

<!-- Microsoft 365 E5; Device as a Service -->
<!-- in O365 table, standard suite, removed this sentence "Please see the Installation of Project/Visio 64bit Click to Run Addendum for important deployment instructions. -->

Microsoft 365 E5 licence (ou équivalent) est requis pour le service de l’ordinateur de bureau Microsoft. Tous les composants qui sont inclus dans cette licence et l’utilisation de bureau Microsoft chaque composant avec les périphériques de bureau Microsoft sont présentées ci-dessous.  Des rôles et responsabilités de chaque zone sont détaillées dans les rubriques de bureau Microsoft. 

Microsoft 365 E5 est composé de 3 composants : Office 365 E5, Windows 10 Enterprise et E5, mobilité d’entreprise + E5 de la sécurité.  

## <a name="office-365-e5"></a>E5 Office 365
 |
 --- | ---
Office 365 Standard Suite (64 bits) * | La Suite d’applications Office standard sont fournie avec le périphérique : Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype pour les entreprises, OneNote.<br><br>64 bits, cliquez sur Exécuter les versions complètes (C2R) de Microsoft Project et Microsoft Visio ne sont pas incluses dans la Suite Standard de Office 365.  Toutefois, étant donné que l’installation de ces applications dépendent de l’installation standard de la Suite Office, de bureau Microsoft a créé des déploiements Intune par défaut et les groupes de sécurité du client utilisé pour le déploiement de ces applications utilisateurs finaux sous licence.  
Stocker des applications |    Microsoft Sway, Microsoft Teams, Power BI bureau (pas Pro) ne sont pas fournis avec appareil. Ces applications sont disponibles en téléchargement à partir de Microsoft Store.
Applications Win32 |    Power BI Pro, Client de Protection d’informations Azure et Microsoft Planner ne sont pas fournis avec le périphérique et peuvent être empaquetée pour le déploiement par le client. 
Applications Web |  Yammer, Office Online, Delve, flux, StaffHub, PowerApps ne sont pas fournis avec le périphérique. Les utilisateurs peuvent accéder à la version de ces applications avec un navigateur web.
Skype pour Business Cloud Online PBX | Cette fonctionnalité est disponible via Office 365 E5. Ordinateur de bureau Microsoft ne configure pas tous les aspects de ce service

## <a name="windows-10-enterprise-e5"></a>E5 d’entreprise Windows 10

 |
 --- | ---
Protection des informations d’identification |  Ordinateur de bureau Microsoft sera fournissent des instructions et gérer les aspects du nuage de cette fonctionnalité
Module de protection du périphérique (contrôle d’Application Windows Defender) | Ordinateur de bureau Microsoft créera la stratégie. Client gérer les signatures
Gestion AppLocker |  Ordinateur de bureau Microsoft créera la stratégie. Client gérer les signatures
Application Virtualization (App-V) |    Ordinateur de bureau Microsoft ne gère pas ce type de déploiement tel qu’il n’est pas pris en charge sur Intune.
Virtualisation d’expérience utilisateur (UE-V) | Il n’est pas utilisé avec les appareils Microsoft de bureau géré
Expérience utilisateur géré  | Il n’est pas utilisé avec les appareils Microsoft de bureau gérés. Mobile Device Manager est utilisée en tant que solution de gestion des périphériques
Windows Defender Advanced Threat Protection |   Cela est utilisée par l’ordinateur de bureau Microsoft pour gérer les stratégies de sécurité des périphériques. 

## <a name="enterprise-mobility--security"></a>Enterprise Mobility + Security 

 |
 --- | ---
Enterprise Mobility + Security E3<br>Azure Active Directory Premium P2 |    Tous les aspects de la mobilité d’entreprise + E3 de sécurité et de AADP peuvent être utilisées pour gérer les périphériques Mobile Device Manager
Microsoft Cloud App Security |  Il s’agit d’une fonctionnalité facultative qui permet aux clients avec le service de bureau Microsoft.
Informations Azure Protection P2  |Il s’agit d’une fonctionnalité facultative qui permet aux clients avec le service de bureau Microsoft.
