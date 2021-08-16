---
title: Configuration des appareils
description: Découvrez les stratégies par défaut appliquées Microsoft Manged Desktop appareils.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 0e763e78513426e187ab4f3df87438ac750d6f4a77d8a0b5791276685c221a89
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53854434"
---
# <a name="device-configuration"></a>Configuration des appareils


<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

Lorsqu’un nouvel Microsoft Manged Desktop est en cours de configuration, nous nous assurons qu’il dispose de la bonne configuration optimisée pour Microsoft Manged Desktop. Cette configuration inclut un ensemble de stratégies par défaut définies dans le cadre du processus d’intégration. Ces stratégies sont livrées à l’aide de la Gestion des périphériques mobiles (MDM) chaque fois que possible. Pour plus d’informations, voir [Gestion des périphériques mobiles.](/windows/client-management/mdm/) 

>[!NOTE]
>Pour éviter les conflits, ne modifiez pas ces stratégies.

Les appareils arrivent avec une image de signature, puis rejoignent le Azure Active Directory lorsque le premier utilisateur se connecté. L’appareil installe automatiquement les stratégies et applications requises sans intervention de votre personnel technique.

## <a name="default-policies"></a>Stratégies par défaut

Ce tableau met en évidence les stratégies par défaut qui sont appliquées à tous les Microsoft Manged Desktop lors de la mise en service des appareils. Toutes les modifications détectées non approuvées par Microsoft Manged Desktop Operations Team sur les objets gérés par Microsoft Manged Desktop seront de retour.

Stratégie | Description
--- | ---
Base de référence de sécurité | [La ligne de base](/windows/device-security/windows-security-baselines) de sécurité Microsoft pour la gestion des périphériques mobiles est configurée pour tous les Microsoft Manged Desktop mobiles. Cette ligne de base est la configuration standard du secteur. Il est publié publiquement, bien testé et a été examiné par des experts en sécurité Microsoft pour garantir la sécurité Microsoft Manged Desktop et des applications dans l’espace de travail moderne. <br><br>Pour atténuer les menaces dans le paysage des menaces de sécurité en constante évolution, la ligne de base de sécurité Microsoft sera mise à jour et déployée sur les appareils Microsoft Manged Desktop avec chaque mise à jour Windows 10 fonctionnalités.<br><br>Pour plus d’informations, [voir Windows de sécurité.](/windows/security/threat-protection/windows-security-baselines)
Microsoft Manged Desktop de sécurité recommandé | Ensemble de modifications recommandées apportées à la ligne de base de sécurité qui optimisent l’expérience utilisateur.  Ces modifications sont documentées dans [le addendum de sécurité.](#security-addendum) Les mises à jour du addendum de stratégie se produisent selon les besoins.  
Mettre à jour le déploiement | Utilisez Windows Update for Business pour effectuer un déploiement progressif des mises à jour logicielles. Les administrateurs informatiques ne peuvent pas modifier les paramètres des stratégies de groupe de déploiement. Pour plus d’informations sur le déploiement basé sur un groupe, voir Comment les mises à jour sont [gérées dans Microsoft Manged Desktop](updates.md).
Connexions avec des compteurs | Par défaut, les mises à jour sur les connexions avec compteurs (telles que les réseaux LTE) sont désactivées, même si chaque utilisateur peut activer indépendamment cette fonctionnalité dans **Paramètres > Updates > Options** avancées . Si vous souhaitez autoriser tous les utilisateurs à activer les mises à jour sur des connexions avec des connexions, envoyez une demande de [modification,](../working-with-managed-desktop/admin-support.md)qui activera ce paramètre pour tous les appareils.
| Conformité des appareils | Ces stratégies sont configurées pour tous Microsoft Manged Desktop appareils. Un appareil est signalé comme non conforme lorsqu’il dérive de notre configuration de sécurité requise.

## <a name="windows-diagnostic-data"></a>Données de diagnostic Windows

 Les appareils seront définies pour fournir des données de diagnostic améliorées à Microsoft sous un identificateur commercial connu. Dans le cadre de Microsoft Manged Desktop, les administrateurs informatiques ne peuvent pas modifier ces paramètres. Pour les clients dans les régions du Règlement général sur la protection des données (R GDPR), les utilisateurs peuvent réduire le niveau des données de diagnostic fournies, mais il y aura une réduction du service. Par exemple, Microsoft Manged Desktop ne sera pas en mesure de collecter les données nécessaires pour itérer sur les paramètres et les stratégies afin de mieux répondre aux besoins en matière de performances et de sécurité. Pour plus d’informations, [voir Configure Windows diagnostic data in your organization.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="security-addendum"></a>Addendum de sécurité

 Cette section décrit les stratégies qui seront déployées en plus des stratégies Microsoft Manged Desktop standard répertoriées dans les [stratégies par défaut.](#default-policies) Cette configuration est conçue avec les services financiers et les secteurs hautement réglementés à l’esprit, en optimisant la sécurité la plus élevée tout en conservant la productivité des utilisateurs.

 ### <a name="additional-security-policies"></a>Stratégies de sécurité supplémentaires

 Ces stratégies sont ajoutées pour renforcer la sécurité des secteurs hautement réglementés. 
 - **Surveillance de la** sécurité : Microsoft surveillera les appareils à l’aide [de Microsoft Defender pour le point de terminaison.](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) Si une menace est détectée, Microsoft avertit le client, isole l’appareil et rectifie le problème à distance. 
 - **Désactiver PowerShell V2 :** Microsoft a supprimé PowerShell V2 en août 2017. Cette fonctionnalité a été désactivée sur tous Microsoft Manged Desktop appareils. Pour plus d’informations sur cette [modification, voir Windows PowerShell 2.0 Deprecation](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/).