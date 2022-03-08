---
title: Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment utiliser les lignes de base pour déployer des configurations client standard.
ms.openlocfilehash: f59ca686892e0b20ce5e9ffb6d62859ce8079896
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323148"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard 

Microsoft 365 Lighthouse de référence fournissent un moyen extensible et évolutif de gérer les paramètres de sécurité Microsoft 365 plusieurs clients. Les lignes de base permettent également de surveiller les stratégies de sécurité principales et les normes de conformité des clients avec des configurations qui sécurisationnt les utilisateurs, les appareils et les données.

Conçu pour aider les fournisseurs de services gérés (MSP) à favoriser l’adoption de la sécurité par les clients, Le Général fournit un ensemble standard de paramètres de référence et de configurations prédéfinie pour Microsoft 365 services. Ces configurations de sécurité permettent de mesurer la progression de la sécurité Microsoft 365 conformité de vos locataires.

Vous pouvez afficher la ligne de base par défaut et ses étapes de déploiement à partir de La station d’évaluation. Pour appliquer une ligne de base à un client, **sélectionnez Les locataires** dans le volet de navigation de gauche, puis sélectionnez un client. Ensuite, allez dans l’onglet **Plans de** déploiement et implémentez la ligne de base.

## <a name="default-baseline-security-templates"></a>Modèles de sécurité de référence par défaut

Les configurations de base par défaut des charges de travail de sécurité sont conçues pour s’assurer que tous les locataires gérés sont sécurisés et conformes.

Les configurations de référence dans le tableau suivant sont standard avec la ligne de base par défaut du point de départ.<br><br>

| Configuration de référence | Description |
|--|--|
| Exiger l’mf pour les administrateurs | Une stratégie d’accès conditionnel nécessitant une authentification multifacteur pour tous les administrateurs. Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette ligne de base, voir [Accès conditionnel : exiger l’mbam pour tous les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Exiger l’mf pour les utilisateurs finaux | Une stratégie d’accès conditionnel qui nécessite une authentification multifacteur pour tous les utilisateurs.  Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette ligne de base, voir [Accès conditionnel : exiger l’mbam pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloquer l’authentification héritée | Une stratégie d’accès conditionnel pour bloquer l’authentification client héritée. Pour plus d’informations sur cette ligne de base, voir Bloquer l’authentification [héritée Azure AD avec l’accès conditionnel](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Configurer l’inscription des appareils | Inscription d’appareils pour permettre à vos appareils locataires de s’inscrire Microsoft Endpoint Manager. Pour ce faire, vous avez la configuration de l’inscription automatique entre Azure Active Directory et Microsoft Endpoint Manager. Pour plus d’informations sur cette ligne de base, voir Configurer l’inscription [Windows appareils mobiles](/mem/intune/enrollment/windows-enroll). |
| Configurer Antivirus Microsoft Defender pour Windows 10 et ultérieures | Profil de configuration d’Windows appareils avec des paramètres de Antivirus Microsoft Defender pré-configurés. Pour plus d’informations sur cette ligne de base, voir [Configurer Microsoft Defender pour endpoint dans Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Configurer le Pare-feu Microsoft Defender pour les Windows 10 et ultérieures | Une stratégie de pare-feu pour sécuriser les appareils en empêchant le trafic réseau indésirable et non autorisé. Pour plus d’informations sur cette ligne de base, voir [Best practices for configuring Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Configurer une stratégie de conformité des appareils pour Windows 10 et ultérieures | Une stratégie Windows appareil avec des paramètres pré-configurés pour répondre aux exigences de conformité de base. Pour plus d’informations sur cette ligne de base, voir Accès conditionnel : exiger la conformité ou [l’Azure AD appareil joint](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |


## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
