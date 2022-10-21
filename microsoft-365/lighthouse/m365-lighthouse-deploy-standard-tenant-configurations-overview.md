---
title: Vue d’ensemble de l’utilisation des bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: shcallaw, kywirpel
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment utiliser des bases de référence pour déployer des configurations de locataire standard.
ms.openlocfilehash: dd55963142abf35c6ee689980116817632110b18
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660178"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>Vue d’ensemble de l’utilisation des bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard 

Microsoft 365 Lighthouse bases de référence fournissent un moyen reproductible et évolutif de gérer les paramètres de sécurité Microsoft 365 sur plusieurs locataires clients. Les bases de référence fournissent des configurations de locataire standard qui déploient des stratégies de sécurité de base et des normes de conformité qui protègent les utilisateurs, les appareils et les données de vos locataires.

Vous pouvez afficher la base de référence par défaut et ses étapes de déploiement à partir de Lighthouse. Pour appliquer une base de référence à un locataire, sélectionnez **Locataires** dans le volet de navigation gauche, puis sélectionnez un locataire. Ensuite, accédez à l’onglet **Plan de déploiement** pour commencer le déploiement.

## <a name="lighthouse-baseline"></a>Base de référence du phare

Les configurations de base lighthouse sont conçues pour garantir que tous les locataires gérés sont sécurisés et conformes. Sélectionnez **Lignes de base** dans le volet de navigation gauche pour afficher la ligne de base par défaut qui s’applique à tous les locataires. Pour afficher les étapes de déploiement incluses dans la base de référence par défaut, sélectionnez **Afficher la base de référence** pour ouvrir la page **Base de référence par défaut** . Sélectionnez l’une des étapes de déploiement pour afficher les détails du déploiement et l’impact sur l’utilisateur.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Capture d’écran de la page Base de référence par défaut.":::

### <a name="default-lighthouse-configurations"></a>Configurations lighthouse par défaut

| Configuration de référence | Description |
|--|--|
| Exiger l’authentification multifacteur pour les administrateurs | Stratégie d’accès conditionnel nécessitant une authentification multifacteur pour tous les administrateurs. Elle est obligatoire pour toutes les applications cloud. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger l’authentification multifacteur pour tous les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Exiger l’authentification multifacteur pour les utilisateurs finaux | Stratégie d’accès conditionnel qui nécessite une authentification multifacteur pour tous les utilisateurs.  Elle est obligatoire pour toutes les applications cloud. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloquer l’authentification héritée | Une stratégie d’accès conditionnel pour bloquer l’authentification du client hérité. Pour plus d’informations sur cette base de référence, consultez [Bloquer l’authentification héritée sur Azure AD avec l’accès conditionnel](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Configurer l’inscription des appareils | Inscription d’appareil pour permettre aux appareils de vos locataires de s’inscrire dans Microsoft Endpoint Manager. Pour ce faire, vous configurez l’inscription automatique entre Azure Active Directory et Microsoft Endpoint Manager. Pour plus d’informations sur cette base de référence, consultez [Configurer l’inscription pour les appareils Windows](/mem/intune/enrollment/windows-enroll). |
| Configurer Microsoft Defender pour entreprises | Approvisionne le locataire pour Microsoft Defender pour entreprises et intègre les appareils déjà inscrits dans Microsoft Endpoint Manager à Microsoft Defender pour entreprises. Pour plus d’informations, consultez [Qu’est-ce que Microsoft Defender pour entreprises ?](../security/defender-business/mdb-overview.md) |
| Configurer Exchange Online Protection et Microsoft Defender pour Office 365 | Une stratégie pour appliquer les stratégies recommandées contre le courrier indésirable, les programmes malveillants, l’anti-hameçonnage, les liens sécurisés et les pièces jointes sécurisées à vos locataires Exchange Online boîtes aux lettres. |
| Configurer Microsoft Defender Antivirus pour Windows 10 et versions ultérieures | Profil de configuration d’appareil pour les appareils Windows avec des paramètres d’antivirus Microsoft Defender préconfigurés. Pour plus d’informations sur cette base de référence, consultez [Configurer Microsoft Defender pour point de terminaison dans Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Configurer Microsoft Defender Pare-feu pour Windows 10 et versions ultérieures | Une stratégie de pare-feu pour sécuriser les appareils en empêchant le trafic réseau indésirable et non autorisé. Pour plus d’informations sur cette base de référence, consultez [Bonnes pratiques pour configurer Windows Defender Pare-feu](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Configurer une stratégie de conformité des appareils pour Windows 10 et versions ultérieures | Une stratégie d’appareil Windows avec des paramètres préconfigurés pour répondre aux exigences de conformité de base. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger un appareil joint à Azure AD conforme ou hybride](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |
| Configurer Microsoft Edge  | Une stratégie de navigateur Microsoft Edge pour Windows 10 ou une version ultérieure avec des paramètres préconfigurés pour rester protégé contre les escroqueries par hameçonnage et les logiciels malveillants. Cette stratégie permet également à Microsoft Edge d’enregistrer et de surveiller les mots de passe en toute sécurité et de suggérer des mots de passe forts si nécessaire. |

## <a name="deployment-plans"></a>Plans de déploiement

Chaque locataire actif dispose d’un plan de déploiement qui inclut les étapes de déploiement de la base de référence Microsoft 365 Lighthouse. Pour accéder au plan de déploiement d’un locataire, sélectionnez un locataire actif dans la liste de la page **Locataires** , puis sélectionnez l’onglet **Plan de déploiement** .

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Capture d’écran de l’onglet Plan de déploiement.":::

L’onglet Plan de déploiement comprend les informations suivantes :


|Colonne  |Description  |
|---------|---------|
|Étape de déploiement     |  Description de l’étape de déploiement.       |
|État     |État de l’étape de déploiement.         |
|Baseline     |Base de référence à partir de laquelle l’étape de déploiement est dérivée.         |
|Catégorie     | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données.        |
|Dernière mise à jour    | Date à laquelle l’étape de déploiement a été mise à jour pour la dernière fois.        |


L’onglet Plan de déploiement inclut également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données de l’étape de déploiement vers un fichier de valeurs séparées par des virgules (.csv) Excel.
- **Actualiser:** Sélectionnez cette option pour récupérer les données d’étape de déploiement les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="deployment-steps-and-processes"></a>Étapes et processus de déploiement

Le plan de déploiement de chaque locataire inclut les étapes de déploiement de la base de référence Microsoft 365 Lighthouse. Chaque étape de déploiement comprend un ou plusieurs processus qui doivent être effectués. Lorsqu’un nouveau locataire devient actif, vous devez effectuer les activités de déploiement associées aux étapes et processus de déploiement.

Pour chaque étape de déploiement, vous pouvez effectuer les actions suivantes :

|Opération  |Description  |
|---------|---------|
| Partager    |  Permet de partager le contenu de l’étape de déploiement via un lien ou par e-mail.    |
| Passer en revue et déployer    |  Permet à l’utilisateur de : <ul><li>Lorsqu’il est pris en charge, comparez les paramètres de configuration de l’étape de déploiement avec les paramètres des stratégies existantes sans déployer les paramètres sur le locataire.<br>Les étapes de déploiement suivantes prennent en charge la comparaison :</br><ul><li>Configurer une stratégie de conformité des appareils pour Windows 10 et versions ultérieures</li><li>Exiger l’authentification multifacteur pour les utilisateurs finaux</li><li>Exiger l’authentification multifacteur pour les administrateurs</li><li>Bloquer l’authentification héritée</li></ul></li> <li>Déployez les paramètres de configuration sur le locataire.</li></ul>**Note:** Les étapes qui ne prennent pas en charge la possibilité de comparer sans déployer les paramètres sur le locataire vous permettent d’examiner les paramètres de configuration et de les déployer.|
| Mettre à jour l’état du plan d’action    |  Permet à l’utilisateur de signaler l’état de son plan d’action pour l’étape de déploiement.      |

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse bases de référence](m365-lighthouse-deploy-baselines.md) (article)\
[Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (article)\
[FAQ Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (article)
