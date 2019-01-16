---
title: Configuration du périphérique
description: Découvrez les stratégies par défaut appliqués aux périphériques de bureau Microsoft.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: e36c65bab3fa78fc27ee6228e78461b2e6b318dd
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867286"
---
# <a name="device-configuration"></a>Configuration du périphérique


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Lorsqu’un nouveau périphérique de bureau Microsoft est mise en service, nous assurer que la configuration, optimisée pour Microsoft de bureau, est en place. Cela inclut un ensemble de stratégies par défaut qui sont définies dans le cadre du processus d’intégration. Pour éviter les conflits de ces stratégies ne doivent pas être modifiés. 

Appareils seront arrivent avec une image de signature, puis rejoindre le domaine Azure Active Directory lorsque le premier utilisateur se connecte. Le périphérique installe automatiquement stratégies requises et les applications sans aucune intervention de l’informatique nécessaire.

## <a name="why-mdm-over-group-policy"></a>Pourquoi Mobile Device Manager sur la stratégie de groupe

Il existe quelques raisons d’utiliser la gestion des appareils mobiles (Mobile Device Manager) au lieu de la stratégie de groupe :

- Sécurité - Stratégies Mobile Device Manager sont plus sécurisés dans le monde moderne. Stratégie de groupe est conçue pour un fonctionnement optimal avec l’identité locale Mobile Device Manager est conçu pour un fonctionnement optimal avec la gestion des identités cloud (Azure Active Directory).
- Fiabilité - stratégies de Mobile Device Manager permettent de déploiement de stratégie plus fiable. En outre, Paramètres Mobile Device Manager écraser les stratégies de l’objet de stratégie de groupe (GPO). Démarrage avec Windows 10, version 1803, Paramètres Mobile Device Manager auront la priorité sur les valeurs de la stratégie de groupe, qui prend en charge les clients de passer à la gestion moderne. 
- Aligner avec vision de bureau Microsoft - fournit une analyse plus complète sur le déploiement de la stratégie et prend en charge approche basée sur le groupe progressivement les modifications de stratégie de déploiement avec la possibilité de suspendre / reprendre déploiement lorsque cela est nécessaire.

Pour plus d’informations, voir [Gestion des périphériques mobiles](https://docs.microsoft.com/windows/client-management/mdm/). 

## <a name="default-policies"></a>Stratégies par défaut

Ce tableau présente les stratégies par défaut qui sont appliqués à tous les périphériques de bureau Microsoft au cours de la configuration du périphérique. Tous les détectés reprend les modifications non approuvées par l’équipe Microsoft gérées bureau opérations aux objets gérés par Microsoft de bureau.

Stratégie | Description
--- | ---
Guide de sécurité | [Guide de sécurité Microsoft](https://docs.microsoft.com/windows/device-security/windows-security-baselines) pour Mobile Device Manager est configuré pour tous les périphériques de bureau Microsoft. Cette ligne de base est la configuration standard de l’industrie. Il sera diffusé commercialement, bien testé, a été révisé par des experts de sécurité de Microsoft pour que les périphériques de bureau Microsoft et sécuriser les applications dans l’espace de travail moderne.<br><br>Afin d’atténuer les menaces dans le paysage des menaces de sécurité en constante évolution, le Guide de sécurité Microsoft sera mis à jour et déployé sur les périphériques de bureau Microsoft à chaque mise à jour de la fonctionnalité Windows 10.<br><br>Pour plus d’informations, voir le [Guide de sécurité pour Windows 10](https://blogs.technet.microsoft.com/secguide/2017/10/18/security-baseline-for-windows-10-fall-creators-update-v1709-final/).
Ordinateur de bureau Microsoft recommandé de modèle de sécurité | Un ensemble de modifications recommandées pour la sécurité de base permettant d’optimiser l’expérience utilisateur.  Ces modifications sont documentées dans [L’Addendum de sécurité](#security-addendum). Mises à jour à l’addendum stratégie se produisent sur selon vos besoins.  
Conformité de périphérique | Ces stratégies sont configurés par défaut pour tous les périphériques de bureau Microsoft. Un périphérique est indiqué comme non conformes lors d’une des conditions de sécurité suivantes n’est pas remplie :<br>-Le chiffrement BitLocker périphérique activé, pour protéger les données sur les périphériques. Pour plus d’informations, voir [vue d’ensemble de périphérique chiffrement BitLocker dans Windows 10.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10)<br>-Initialisation sécurisée activée et appliquée, pour valider les images du microprogramme sur les périphériques avant qu’ils peuvent exécuter. Pour plus d’informations, voir [sécurisée présentation du chiffrement de démarrage et des périphériques.](https://docs.microsoft.com/windows-hardware/drivers/bringup/secure-boot-and-device-encryption-overview)<br>-Périphérique de bureau Microsoft requiert le mot de passe pour la connexion.
Déploiement de la mise à jour | Utilisez Windows Update pour les entreprises (WUfB) pour effectuer un déploiement progressif des mises à jour logicielles. Les administrateurs informatiques ne peuvent pas modifier les paramètres pour les stratégies de groupe de déploiement. Pour plus d’informations sur le déploiement basé sur un groupe, voir [la gestion des mises à jour](../working-with-managed-desktop/updates.md).
Télémétrie | Périphériques seront définis pour fournir des données de diagnostics améliorées à Microsoft sous un identificateur commercial connu. Dans le cadre de l’ordinateur de bureau Microsoft, les administrateurs informatiques ne peuvent pas modifier ces paramètres. Pour les clients en général régions règlement de Protection de données (PIBR), les utilisateurs finaux peuvent réduire le niveau de données de diagnostic qui sont fournis, mais il y aura une réduction de service. Par exemple, de bureau Microsoft ne pourront pas collecter les données nécessaires pour effectuer une itération sur les stratégies et paramètres pour mieux répondre aux besoins de performances et la sécurité. Pour plus d’informations, voir [des données de diagnostic configurer Windows dans votre organisation.](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

 ## <a name="security-addendum"></a>Addendum de sécurité

 Cette section présente les stratégies qui seront déployés comme supplémentaires aux stratégies de bureau Microsoft standards. Stratégies standards sont répertoriés dans [les stratégies par défaut](#default-policies). Cette configuration est conçue avec les Services financiers et hautement régulé secteurs d’activité à l’esprit : optimisation de la position la plus sécurisée, tout en maintenant la productivité des utilisateurs.

 ### <a name="additional-security-policies"></a>Stratégies de sécurité supplémentaires

 Ces stratégies sont ajoutées pour renforcer la sécurité pour les secteurs hautement régulé. 
 - **Application de liste verte**: applications doivent être approuvées par l’organisation à exécuter sur les périphériques de bureau Microsoft. Il fournit un environnement verrouillé. Les applications qui doivent être onboarded doivent être communiquées à l’équipe des opérations Microsoft géré du bureau. Pour plus d’informations, voir [Windows Defender périphérique Guard](https://docs.microsoft.com/windows/device-security/device-guard/device-guard-deployment-guide).
 - **Surveillance de la sécurité**: Microsoft surveillera périphériques à l’aide de [Windows Defender avancée protection contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Si une menace est détectée, Microsoft avertir le client, isoler le périphérique et corriger le problème à distance. 

