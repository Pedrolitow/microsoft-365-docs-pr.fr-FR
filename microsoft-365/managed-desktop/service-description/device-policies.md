---
title: Configuration des périphériques
description: Découvrez les stratégies par défaut appliquées aux appareils de bureau gérés par Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 9a7d2130775c9c5d99bba711254fc0f0ce540947
ms.sourcegitcommit: 3294b97a20ae0e5eb8ce6187310cc96b5050a215
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "34422210"
---
# <a name="device-configuration"></a>Configuration des périphériques


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Lors de la mise en service d’un nouveau périphérique de bureau géré Microsoft, nous nous assurons que la bonne configuration, optimisée pour Microsoft Managed Desktop, est en place. Cela inclut un ensemble de stratégies par défaut qui sont définies dans le cadre du processus d’intégration. Pour éviter les conflits, ces stratégies ne doivent pas être modifiées. 

Les appareils arrivent avec une image de signature, puis rejoignent le domaine Azure Active Directory lorsque le premier utilisateur se connecte. L’appareil installe automatiquement les stratégies et applications requises sans intervention informatique requise.

## <a name="why-mdm-over-group-policy"></a>Pourquoi MDM via la stratégie de groupe

Il existe quelques raisons d’utiliser MDM (Mobile Device Management) au lieu de la stratégie de groupe:

- Sécurité: les stratégies MDM sont plus sécurisées dans le monde moderne. La stratégie de groupe est conçue pour fonctionner de façon optimale avec l’identité locale, tandis que MDM est conçu pour fonctionner de manière optimale avec le Cloud Identity Management (Azure Active Directory).
- Fiabilité: les stratégies MDM fournissent un déploiement de stratégie plus fiable. En outre, les paramètres MDM remplacent les stratégies d’objets de stratégie de groupe (GPO). À partir de Windows 10, version 1803, les paramètres MDM seront classés par ordre de priorité sur les valeurs de stratégie de groupe, qui prend en charge les clients qui migrent vers une gestion moderne. 
- Aligner avec Microsoft Managed Desktop vision: fournit une surveillance plus complète sur le déploiement de stratégie et prend en charge l’approche basée sur les groupes pour déployer progressivement des modifications de stratégie avec la possibilité de suspendre/reprendre le déploiement si nécessaire.

Pour plus d’informations, consultez la rubrique [gestion des appareils mobiles](https://docs.microsoft.com/windows/client-management/mdm/). 

## <a name="default-policies"></a>Stratégies par défaut

Ce tableau met en évidence les stratégies par défaut appliquées à tous les appareils de bureau gérés par Microsoft lors de la mise en service des appareils. Toutes les modifications détectées qui ne sont pas approuvées par l’équipe des opérations de bureau géré Microsoft sur les objets gérés par Microsoft Managed Desktop seront rétablies.

Stratégie | Description
--- | ---
Base de sécurité | [Microsoft Security Baseline](https://docs.microsoft.com/windows/device-security/windows-security-baselines) pour MDM est configuré pour tous les appareils de bureau gérés par Microsoft. Il s’agit de la configuration standard. Elle est publiée, bien testée, et a été examinée par des experts en sécurité Microsoft afin de maintenir la sécurité des applications et des appareils de bureau gérés Microsoft dans l’espace de travail moderne. <br><br>Pour atténuer les menaces dans le contexte de sécurité en perpétuelle évolution, la base de sécurité Microsoft est mise à jour et déployée sur les appareils de bureau gérés Microsoft avec chaque mise à jour de la fonctionnalité Windows 10.<br><br>Pour plus d’informations, consultez la rubrique [Security Baseline for Windows 10](https://blogs.technet.microsoft.com/secguide/2017/10/18/security-baseline-for-windows-10-fall-creators-update-v1709-final/).
Modèle de sécurité Microsoft Managed Desktop recommandé | Un ensemble de modifications recommandées à la base de sécurité qui optimisent l’expérience utilisateur.  Ces modifications sont documentées dans [l’Addendum sur la sécurité](#security-addendum). Les mises à jour apportées à l’addenda de la stratégie ont lieu le cas échéant.  
Mettre à jour le déploiement | Utilisez Windows Update for Business (WUfB) pour effectuer un déploiement progressif des mises à jour logicielles. Les administrateurs informatiques ne peuvent pas modifier les paramètres des stratégies de groupe de déploiement. Pour plus d’informations sur le déploiement basé sur un groupe, consultez [la rubrique How updates handle](../working-with-managed-desktop/updates.md).
Données de diagnostic | Les appareils seront configurés pour fournir des données de diagnostic améliorées à Microsoft sous un identificateur commercial connu. Dans le cadre du bureau géré Microsoft, les administrateurs informatiques ne peuvent pas modifier ces paramètres. Pour les clients qui utilisent des régions générales de protection des données (RGPD), les utilisateurs finaux peuvent réduire le niveau de données de diagnostic fourni, mais une réduction du service est possible. Par exemple, le bureau géré Microsoft ne pourra pas collecter les données nécessaires pour effectuer une itération sur les paramètres et les stratégies afin de mieux répondre aux exigences de performances et de sécurité. Pour plus d’informations, reportez-vous à [la rubrique Configurer les données de diagnostic Windows dans votre organisation.](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

 ## <a name="security-addendum"></a>Addendum sur la sécurité

 Cette section décrit les stratégies qui seront déployées comme complément aux stratégies de bureau géré standard de Microsoft. Les stratégies standard sont répertoriées dans [stratégies par défaut](#default-policies). Cette configuration est conçue avec des services financiers et des secteurs hautement réglementés à l’esprit: optimisation de l’attitude la plus sécurisée, tout en maintenant la productivité des utilisateurs.

 ### <a name="additional-security-policies"></a>Stratégies de sécurité supplémentaires

 Ces stratégies sont ajoutées pour renforcer la sécurité des industries hautement réglementées. 
 - **Liste**d’applications autorisées: les applications doivent être approuvées par l’Organisation pour s’exécuter sur des appareils de bureau gérés par Microsoft. Cela fournit un environnement verrouillé. Toutes les applications qui doivent être intégrées doivent être communiquées à l’équipe des opérations de bureau géré Microsoft. Pour plus d’informations, consultez la rubrique [Windows Defender Device Guard](https://docs.microsoft.com/windows/device-security/device-guard/device-guard-deployment-guide).
 - **Surveillance**de la sécurité: Microsoft surveille les appareils à l’aide de la [protection avancée contre les menaces Windows Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Si une menace est détectée, Microsoft avertit le client, isole l’appareil et corrige le problème à distance. 
 - **Désactiver PowerShell v2**: Microsoft a supprimé PowerShell version 2 en août 2017. Cette fonctionnalité a été désactivée sur tous les appareils de bureau gérés par Microsoft. Pour plus d’informations sur ce changement, voir [Windows PowerShell 2,0](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/)deconseilléion.
