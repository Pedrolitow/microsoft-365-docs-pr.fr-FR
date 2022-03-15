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
ms.openlocfilehash: 643bb962277d30caf8ea067b9276a5986af8914f
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504531"
---
# <a name="overview-of-using-baselines-to-deploy-standard-tenant-configurations"></a>Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard 

Microsoft 365 Lighthouse de référence fournissent un moyen extensible et évolutif de gérer les paramètres de sécurité Microsoft 365 plusieurs clients. Les lignes de base fournissent des configurations client standard qui déploient des stratégies de sécurité principales et des normes de conformité qui assurent la sécurité des utilisateurs, des appareils et des données de vos clients.

Vous pouvez afficher la ligne de base par défaut et ses étapes de déploiement à partir de La station d’évaluation. Pour appliquer une ligne de base à un client, **sélectionnez Les locataires** dans le volet de navigation de gauche, puis sélectionnez un client. Ensuite, allez dans l’onglet **Plans de** déploiement pour commencer le déploiement.

## <a name="lighthouse-baseline"></a>Ligne de base de référence de référence

Les configurations de base de référence de référence sont conçues pour s’assurer que tous les locataires gérés sont sécurisés et conformes. **Sélectionnez Lignes de base** dans le volet de navigation de gauche pour afficher la ligne de base par défaut qui s’applique à tous les locataires.  Pour afficher les étapes de déploiement incluses dans la ligne de base par défaut, sélectionnez **Afficher** la ligne de base pour ouvrir la page de référence par défaut. Sélectionnez l’une des étapes de déploiement pour afficher les détails du déploiement et l’impact sur l’utilisateur.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Capture d’écran de la page de référence par défaut.":::

### <a name="default-lighthouse-configurations"></a>Configurations par défaut

| Configuration de référence | Description |
|--|--|
| Exiger l’mf pour les administrateurs | Une stratégie d’accès conditionnel nécessitant une authentification multifacteur pour tous les administrateurs. Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette ligne de base, voir [Accès conditionnel : exiger l’mbam pour tous les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Exiger l’mf pour les utilisateurs finaux | Une stratégie d’accès conditionnel qui nécessite une authentification multifacteur pour tous les utilisateurs.  Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette ligne de base, voir [Accès conditionnel : exiger l’mbam pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloquer l’authentification héritée | Une stratégie d’accès conditionnel pour bloquer l’authentification client héritée. Pour plus d’informations sur cette ligne de base, voir Bloquer l’authentification [héritée Azure AD avec l’accès conditionnel](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Configurer l’inscription des appareils | Inscription d’appareils pour permettre à vos appareils locataires de s’inscrire Microsoft Endpoint Manager. Pour ce faire, vous avez la configuration de l’inscription automatique entre Azure Active Directory et Microsoft Endpoint Manager. Pour plus d’informations sur cette ligne de base, voir Configurer l’inscription [Windows appareils mobiles](/mem/intune/enrollment/windows-enroll). |
| Configurer Antivirus Microsoft Defender pour Windows 10 et ultérieures | Profil de configuration d’Windows appareils avec des paramètres de Antivirus Microsoft Defender pré-configurés. Pour plus d’informations sur cette ligne de base, voir [Configurer Microsoft Defender pour endpoint dans Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Configurer le Pare-feu Microsoft Defender pour les Windows 10 et ultérieures | Une stratégie de pare-feu pour sécuriser les appareils en empêchant le trafic réseau indésirable et non autorisé. Pour plus d’informations sur cette ligne de base, voir [Best practices for configuring Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Configurer une stratégie de conformité des appareils pour Windows 10 et ultérieures | Une stratégie Windows appareil avec des paramètres pré-configurés pour répondre aux exigences de conformité de base. Pour plus d’informations sur cette ligne de base, voir Accès conditionnel : exiger la conformité ou [l’Azure AD appareil joint](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>Plans de déploiement

Chaque client actif possède un plan de déploiement qui inclut les étapes de déploiement de la Microsoft 365 Lighthouse base de référence. Pour accéder au plan de déploiement d’un client, sélectionnez un client actif dans la liste de **la page Locataires** , puis sélectionnez l’onglet **Plan de** déploiement.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Capture d’écran de l’onglet Plan de déploiement.":::

L’onglet Plan de déploiement inclut les informations suivantes :


|Colonne  |Description  |
|---------|---------|
|Étape de déploiement     |  Description de l’étape de déploiement.       |
|État     |État de l’étape de déploiement.         |
|Baseline     |Base de référence à partir de laquelle l’étape de déploiement est dérivée.         |
|Catégorie     | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données.        |
|Dernière mise à jour    | Date à laquelle l’étape de déploiement a été mise à jour pour la dernière fois.        |


L’onglet Plan de déploiement inclut également les options suivantes :

- **Exporter :** Choisissez d’exporter les données de l’étape de déploiement vers Excel fichier de valeurs séparées par des virgules (.csv).
- **Actualiser :** Sélectionnez pour récupérer les données d’étape de déploiement les plus récentes.
- **Recherche :** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="deployment-steps-and-processes"></a>Étapes et processus de déploiement

Le plan de déploiement de chaque client inclut les étapes de déploiement de la Microsoft 365 Lighthouse base de référence. Chaque étape de déploiement se compose d’un ou de plusieurs processus qui doivent être effectués pour satisfaire aux exigences de l’étape de déploiement. Lorsqu’un nouveau client devient actif, vous devez effectuer les activités de déploiement associées aux étapes et processus de déploiement.

Pour chaque étape de déploiement, vous pouvez prendre les mesures suivantes :

|Opération  |Description  |
|---------|---------|
| Partager    |  Permet de partager le contenu de l’étape de déploiement par le biais d’un lien ou par courrier électronique.    |
| Examiner et déployer    |  Permet à l’utilisateur de : <ul><li>Lorsqu’il est pris en charge, comparez les paramètres de configuration de l’étape de déploiement avec les paramètres des stratégies existantes sans déployer les paramètres sur le client.<br>La comparaison des étapes de déploiement suivantes est prise en charge :</br><ul><li>Configurer une stratégie de conformité des appareils pour Windows 10 et ultérieures</li><li>Exiger l’mf pour les utilisateurs finaux</li><li>Exiger l’mf pour les administrateurs</li><li>Bloquer l’authentification héritée</li></ul></li> <li>Déployez les paramètres de configuration sur le client.</li></ul>**Remarque :** Les étapes qui ne permettent pas de comparer sans déployer les paramètres sur le client vous permettront de passer en revue les paramètres de configuration et de les déployer.|
| Mettre à jour l’état du plan d’action    |  Permet à l’utilisateur de signaler l’état de son plan d’action pour l’étape de déploiement.      |

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
