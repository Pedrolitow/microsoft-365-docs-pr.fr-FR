---
title: Configuration des périphériques
description: Découvrez les stratégies par défaut appliquées aux appareils de bureau gérés par Microsoft.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 479aa8888a3a8e67c51cb7edf14747c840295a4f
ms.sourcegitcommit: 6ae69c40bafa6aef633789c3df0fa20590bdcf40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "40823716"
---
# <a name="device-configuration"></a>Configuration des périphériques


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Lors de la configuration d’un nouveau périphérique de bureau géré Microsoft, nous nous assurons qu’il dispose de la bonne configuration optimisée pour Microsoft Managed Desktop. Cela inclut un ensemble de stratégies par défaut qui sont définies dans le cadre du processus d’intégration. Ces stratégies sont fournies à l’aide de la gestion des appareils mobiles (MDM) chaque fois que cela est possible. Pour plus d’informations, consultez la rubrique [gestion des appareils mobiles](https://docs.microsoft.com/windows/client-management/mdm/). 

>[!NOTE]
>Pour éviter les conflits, ne modifiez pas ces stratégies.

Les appareils arrivent avec une image de signature, puis rejoignent le domaine Azure Active Directory lorsque le premier utilisateur se connecte. L’appareil installe automatiquement les stratégies et applications requises sans aucune intervention de votre personnel informatique.

## <a name="default-policies"></a>Stratégies par défaut

Ce tableau met en évidence les stratégies par défaut appliquées à tous les appareils de bureau gérés par Microsoft lors de la mise en service des appareils. Toutes les modifications détectées qui ne sont pas approuvées par l’équipe des opérations de bureau géré Microsoft sur les objets gérés par Microsoft Managed Desktop seront rétablies.

Stratégie | Description
--- | ---
Base de sécurité | [Microsoft Security Baseline](https://docs.microsoft.com/windows/device-security/windows-security-baselines) pour MDM est configuré pour tous les appareils de bureau gérés par Microsoft. Il s’agit de la configuration standard. Elle est publiée, bien testée, et a été examinée par des experts en sécurité Microsoft afin de maintenir la sécurité des applications et des appareils de bureau gérés Microsoft dans l’espace de travail moderne. <br><br>Pour atténuer les menaces dans le contexte de sécurité en perpétuelle évolution, la base de sécurité Microsoft est mise à jour et déployée sur les appareils de bureau gérés Microsoft avec chaque mise à jour de la fonctionnalité Windows 10.<br><br>Pour plus d’informations, consultez la rubrique [Security Baseline for Windows 10](https://blogs.technet.microsoft.com/secguide/2017/10/18/security-baseline-for-windows-10-fall-creators-update-v1709-final/).
Modèle de sécurité Microsoft Managed Desktop recommandé | Un ensemble de modifications recommandées à la base de sécurité qui optimisent l’expérience utilisateur.  Ces modifications sont documentées dans [l’Addendum sur la sécurité](#security-addendum). Les mises à jour apportées à l’addenda de la stratégie ont lieu le cas échéant.  
Mettre à jour le déploiement | Utilisez Windows Update pour effectuer un déploiement graduel des mises à jour logicielles. Les administrateurs informatiques ne peuvent pas modifier les paramètres des stratégies de groupe de déploiement. Pour plus d’informations sur le déploiement basé sur un groupe, voir [How updates is Handled in Microsoft Managed Desktop](updates.md).
Données de diagnostic | Les appareils seront configurés pour fournir des données de diagnostic améliorées à Microsoft sous un identificateur commercial connu. Dans le cadre du bureau géré Microsoft, les administrateurs informatiques ne peuvent pas modifier ces paramètres. Pour les clients qui utilisent des régions générales de protection des données (RGPD), les utilisateurs finaux peuvent réduire le niveau de données de diagnostic fourni, mais une réduction du service est possible. Par exemple, le bureau géré Microsoft ne pourra pas collecter les données nécessaires pour effectuer une itération sur les paramètres et les stratégies afin de mieux répondre aux exigences de performances et de sécurité. Pour plus d’informations, reportez-vous à [la rubrique Configurer les données de diagnostic Windows dans votre organisation.](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)
Connexions limitées | Par défaut, les mises à jour sur les connexions limitées (telles que les réseaux LTE) sont désactivées, bien que chaque utilisateur puisse activer cette fonctionnalité de manière indépendante dans **paramètres > mises à jour > options avancées**. Si vous souhaitez autoriser tous les utilisateurs à activer les mises à jour sur les connexions limitées, [envoyez une demande de modification](https://docs.microsoft.com/microsoft-365/managed-desktop/working-with-managed-desktop/admin-support), qui activera ce paramètre pour tous les appareils.

 ## <a name="security-addendum"></a>Addendum sur la sécurité

 Cette section décrit les stratégies qui seront déployées en plus des stratégies de bureau géré Microsoft standard indiquées dans [stratégies par défaut](#default-policies). Cette configuration est conçue avec des services financiers et des secteurs hautement réglementés, ce qui optimise la sécurité la plus élevée tout en conservant la productivité des utilisateurs.

 ### <a name="additional-security-policies"></a>Stratégies de sécurité supplémentaires

 Ces stratégies sont ajoutées pour renforcer la sécurité des industries hautement réglementées. 
 - **Surveillance**de la sécurité : Microsoft surveille les appareils à l’aide de [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). Si une menace est détectée, Microsoft avertit le client, isole l’appareil et corrige le problème à distance. 
 - **Désactiver PowerShell v2**: Microsoft a supprimé PowerShell V2 en août 2017. Cette fonctionnalité a été désactivée sur tous les appareils de bureau gérés par Microsoft. Pour plus d’informations sur ce changement, voir [Windows PowerShell 2,0 Deconseilléion](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/).
