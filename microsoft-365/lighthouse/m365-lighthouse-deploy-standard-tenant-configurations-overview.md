---
title: Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment utiliser les lignes de base pour déployer des configurations client standard.
ms.openlocfilehash: ff3fb21e71195f9614870b8e3c65c92ee11fdf69
ms.sourcegitcommit: 8c698d1a0c41baf5f35d07b0d765b4a5ead593d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2021
ms.locfileid: "53409178"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard 

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences.](m365-lighthouse-requirements.md) Si votre organisation n’a pas de Microsoft 365 Lighthouse, voir [S’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse de référence fournissent un moyen extensible et évolutif d’évaluer et de gérer Microsoft 365 de sécurité sur plusieurs clients. Les lignes de base permettent également de surveiller les stratégies de sécurité principales et les normes de conformité client avec des configurations qui sécurisationnt les utilisateurs, les appareils et les données.

Conçu pour aider les partenaires à favoriser l’adoption de la sécurité par les clients à leur propre rythme, Microsoft 365 Lighthouse fournit un ensemble standard de paramètres de référence et de configurations prédéfinëes pour Microsoft 365 services. Ces configurations de sécurité permettent de mesurer la progression de la sécurité Microsoft 365 conformité de vos locataires.

Vous pouvez afficher la ligne de base par défaut et ses étapes de déploiement à partir de Microsoft 365 Lighthouse. Pour appliquer des lignes de base à un client, sélectionnez **Les** locataires dans le volet de navigation de gauche, puis sélectionnez un client. Ensuite, allez dans l’onglet **Plans de** déploiement et implémentez la ligne de base souhaitée.

## <a name="standard-baseline-security-templates"></a>Modèles de sécurité standard de référence

Microsoft 365 Lighthouse configurations standard de référence pour les charges de travail de sécurité sont conçues pour aider tous les locataires gérés à atteindre un état acceptable de couverture de sécurité et de conformité.

Les configurations de référence dans le tableau suivant sont standard avec la Microsoft 365 Lighthouse par défaut.<br><br>

| Configuration de référence | Description |
|--|--|
| Exiger l’mf pour les administrateurs | Une stratégie d’accès conditionnel de rapport uniquement nécessitant une authentification multifacteur pour les administrateurs. Elle est requise pour toutes les applications cloud. |
| Exiger l’mf pour les utilisateurs finaux | Une stratégie d’accès conditionnel de rapport uniquement qui nécessite une authentification multifacteur pour les utilisateurs. Elle est requise pour toutes les applications cloud. |
| Bloquer l’authentification héritée | Une stratégie d’accès conditionnel de rapport uniquement pour bloquer l’authentification client héritée. |
| Inscrire des appareils dans Microsoft Endpoint Manager - Azure AD Join | Inscription d’appareils pour permettre à vos appareils locataires de s’inscrire dans Microsoft Endpoint Manager. Pour ce faire, vous avez la configuration de l’inscription automatique entre Azure Active Directory et Microsoft Endpoint Manager. |
| Configuration de la stratégie antivirus | Profil de configuration d’appareil Windows appareils avec des paramètres de Antivirus Microsoft Defender pré-configurés. |
| Stratégie de conformité de fenêtre 10 définie | Une stratégie Windows appareil avec des paramètres pré-configurés pour répondre aux exigences de conformité de base. |

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)