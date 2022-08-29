---
title: Vue d’ensemble de l’utilisation de bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw, kywirpel
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment utiliser des bases de référence pour déployer des configurations de locataire standard.
ms.openlocfilehash: 40d146491b45203b9a643b81fa3677bb9ff53a0c
ms.sourcegitcommit: 9a4b0bc6a3ba076ecc392260efe7d2e1b655cde8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67419999"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>Vue d’ensemble de l’utilisation de bases de référence Microsoft 365 Lighthouse pour déployer des configurations de locataire standard 

Microsoft 365 Lighthouse lignes de base offrent un moyen reproductible et évolutif de gérer les paramètres de sécurité Microsoft 365 sur plusieurs locataires clients. Les bases de référence fournissent des configurations de locataire standard qui déploient des stratégies de sécurité de base et des normes de conformité qui sécurisent les utilisateurs, les appareils et les données de vos locataires.

Vous pouvez afficher la ligne de base par défaut et ses étapes de déploiement à partir de Lighthouse. Pour appliquer une ligne de base à un locataire, sélectionnez **Locataires** dans le volet de navigation gauche, puis sélectionnez un locataire. Ensuite, accédez à l’onglet **Plan de déploiement** pour commencer le déploiement.

## <a name="lighthouse-baseline"></a>Ligne de base du phare

Les configurations de référence lighthouse sont conçues pour garantir que tous les locataires gérés sont sécurisés et conformes. Sélectionnez **Lignes de base** dans le volet de navigation gauche pour afficher la ligne de base par défaut qui s’applique à tous les locataires. Pour afficher les étapes de déploiement incluses dans la ligne de base par défaut, sélectionnez **Afficher la ligne de base** pour ouvrir la page **De référence par défaut** . Sélectionnez l’une des étapes de déploiement pour afficher les détails du déploiement et l’impact sur l’utilisateur.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="Capture d’écran de la page De référence par défaut.":::

### <a name="default-lighthouse-configurations"></a>Configurations Lighthouse par défaut

| Configuration de référence | Description |
|--|--|
| Exiger l’authentification multifacteur pour les administrateurs | Stratégie d’accès conditionnel nécessitant une authentification multifacteur pour tous les administrateurs. Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger l’authentification multifacteur pour tous les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| Exiger l’authentification multifacteur pour les utilisateurs finaux | Stratégie d’accès conditionnel qui nécessite une authentification multifacteur pour tous les utilisateurs.  Elle est requise pour toutes les applications cloud. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| Bloquer l’authentification héritée | Stratégie d’accès conditionnel pour bloquer l’authentification du client hérité. Pour plus d’informations sur cette base de référence, consultez [Bloquer l’authentification héritée auprès d’Azure AD avec accès conditionnel](/azure/active-directory/conditional-access/block-legacy-authentication).|
| Configurer l’inscription des appareils | Inscription d’appareils pour permettre à vos appareils locataires de s’inscrire dans Microsoft Endpoint Manager. Pour ce faire, configurez l’inscription automatique entre Azure Active Directory et Microsoft Endpoint Manager. Pour plus d’informations sur cette base de référence, consultez [Configurer l’inscription pour les appareils Windows](/mem/intune/enrollment/windows-enroll). |
| Configurer Microsoft Defender pour entreprises | Provisionne le locataire pour Microsoft Defender pour entreprises et intègre les appareils déjà inscrits dans Microsoft Endpoint Manager à Microsoft Defender pour entreprises. Pour plus [d’informations, voir Qu’est-ce que Microsoft Defender pour entreprises ?](../security/defender-business/mdb-overview.md) |
| Configurer Exchange Online Protection et Microsoft Defender pour Office 365 | Stratégie permettant d’appliquer les stratégies recommandées anti-courrier indésirable, anti-programmes malveillants, anti-hameçonnage, liens sécurisés et stratégies de pièces jointes sécurisées à vos locataires Exchange Online boîtes aux lettres. |
| Configurer l’antivirus Microsoft Defender pour Windows 10 et versions ultérieures | Profil de configuration d’appareil pour les appareils Windows avec des paramètres antivirus Microsoft Defender préconfigurés. Pour plus d’informations sur cette base de référence, consultez [Configurer Microsoft Defender pour point de terminaison dans Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| Configurer le Pare-feu Microsoft Defender pour Windows 10 et versions ultérieures | Stratégie de pare-feu pour sécuriser les appareils en empêchant le trafic réseau indésirable et non autorisé. Pour plus d’informations sur cette base de référence, consultez [les meilleures pratiques de configuration de Windows Defender Pare-feu](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| Configurer une stratégie de conformité des appareils pour Windows 10 et versions ultérieures | Une stratégie d’appareil Windows avec des paramètres préconfigurés pour répondre aux exigences de conformité de base. Pour plus d’informations sur cette base de référence, consultez [Accès conditionnel : Exiger un appareil joint à Azure AD conforme ou hybride](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |
| Configurer Microsoft Edge  | Stratégie de navigateur Microsoft Edge pour Windows 10 ou version ultérieure avec des paramètres préconfigurés afin de rester protégé contre les escroqueries par hameçonnage et les logiciels malveillants. Cette stratégie permet également à Microsoft Edge d’enregistrer et de surveiller en toute sécurité les mots de passe et de suggérer des mots de passe forts si nécessaire. |

## <a name="deployment-plans"></a>Plans de déploiement

Chaque locataire actif dispose d’un plan de déploiement qui inclut les étapes de déploiement de la base de référence Microsoft 365 Lighthouse. Pour accéder au plan de déploiement d’un locataire, sélectionnez un locataire actif dans la liste de la page **Locataires** , puis sélectionnez l’onglet **Plan de déploiement** .

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="Capture d’écran de l’onglet Plan de déploiement.":::

L’onglet Plan de déploiement contient les informations suivantes :


|Colonne  |Description  |
|---------|---------|
|Étape de déploiement     |  Description de l’étape de déploiement.       |
|État     |État de l’étape de déploiement.         |
|Baseline     |Base de référence à partir de laquelle l’étape de déploiement est dérivée.         |
|Catégorie     | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données.        |
|Dernière mise à jour    | Date à laquelle l’étape de déploiement a été mise à jour pour la dernière fois.        |


L’onglet Plan de déploiement comprend également les options suivantes :

- **Exportation:** Sélectionnez cette option pour exporter les données d’étape de déploiement vers un fichier de valeurs séparées par des virgules Excel (.csv).
- **Actualiser:** Sélectionnez cette option pour récupérer les données d’étape de déploiement les plus actuelles.
- **Rechercher:** Entrez des mots clés pour localiser rapidement une étape de déploiement spécifique dans la liste.

## <a name="deployment-steps-and-processes"></a>Étapes et processus de déploiement

Le plan de déploiement de chaque locataire inclut les étapes de déploiement de la base de référence Microsoft 365 Lighthouse. Chaque étape de déploiement inclut un ou plusieurs processus qui doivent être terminés. Lorsqu’un nouveau locataire devient actif, vous devez effectuer les activités de déploiement associées aux étapes et processus de déploiement.

Pour chaque étape de déploiement, vous pouvez effectuer les actions suivantes :

|Opération  |Description  |
|---------|---------|
| Partager    |  Permet de partager le contenu de l’étape de déploiement par le biais d’un lien ou d’un e-mail.    |
| Examiner et déployer    |  Permet à l’utilisateur de : <ul><li>Une fois pris en charge, comparez les paramètres de configuration de l’étape de déploiement avec les paramètres de toutes les stratégies existantes sans déployer les paramètres sur le locataire.<br>Les étapes de déploiement suivantes prennent en charge la comparaison :</br><ul><li>Configurer une stratégie de conformité des appareils pour Windows 10 et versions ultérieures</li><li>Exiger l’authentification multifacteur pour les utilisateurs finaux</li><li>Exiger l’authentification multifacteur pour les administrateurs</li><li>Bloquer l’authentification héritée</li></ul></li> <li>Déployez les paramètres de configuration sur le locataire.</li></ul>**Note:** Les étapes qui ne prennent pas en charge la possibilité de comparer sans déployer les paramètres sur le locataire vous permettent de passer en revue les paramètres de configuration et de les déployer.|
| Mettre à jour l’état du plan d’action    |  Permet à l’utilisateur de signaler l’état de son plan d’action pour l’étape de déploiement.      |

## <a name="related-content"></a>Contenu associé

[Déployer Microsoft 365 Lighthouse lignes de base](m365-lighthouse-deploy-baselines.md) (article)\
[Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
