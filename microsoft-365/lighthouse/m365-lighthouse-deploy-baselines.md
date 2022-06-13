---
title: Déployer Microsoft 365 Lighthouse lignes de base
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment déployer Microsoft 365 Lighthouse lignes de base.
ms.openlocfilehash: 17eda86e80b928fb8b4f56b0e5c719574e4741f5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012591"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Déployer Microsoft 365 Lighthouse lignes de base

Microsoft 365 Lighthouse vous permet de déployer des configurations de locataire managé standard pour sécuriser les utilisateurs, les appareils et les données au sein des locataires clients. Il existe sept [configurations de base de référence par défaut](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) qui sont standard avec Lighthouse. À l’aide de la fonctionnalité de plan de déploiement Lighthouse, vous pouvez afficher, tester et déployer des configurations de sécurité sur tous vos locataires. Un plan de déploiement est uniquement disponible pour les locataires actifs. Une fois qu’un locataire est intégré, vous pouvez comparer la configuration actuelle de vos clients à la configuration de référence par défaut et effectuer les actions appropriées.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que vous et vos locataires clients répondez aux exigences indiquées dans [Requirements for Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Afficher un plan de déploiement

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez le locataire que vous souhaitez afficher.

3. Sélectionnez l’onglet **Plan de déploiement** .

    L’onglet Plan de déploiement fournit une liste pouvant faire l’objet d’une recherche et exportable de chaque étape de déploiement incluse dans le plan de déploiement du locataire, qui inclut les informations suivantes pour chaque étape de déploiement :

    | Colonne            | Description |
    |-----------------|-------------------------------------------------------------------------------------|
    | Étape de déploiement | Description de l’étape de déploiement.                                                     |
    | État          | État de l’étape de déploiement.                                                  |
    | Baseline        | Base de référence à partir de laquelle l’étape de déploiement est dérivée.                             |
    | Catégorie        | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données. |
    | Dernière mise à jour    | Date à laquelle l’étape de déploiement a été mise à jour pour la dernière fois.                             |

4. Dans la liste, sélectionnez une étape de déploiement à examiner.

    La page Étape de déploiement fournit les informations suivantes :

    | Colonne            | Description |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Résumé        | Récapitulatif de l’objectif de l’étape de déploiement.                                         |
    | Baseline       | Base de référence à partir de laquelle l’étape de déploiement est dérivée.                             |
    | Catégorie       | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données. |
    | Référence SKU requise   | Références SKU requises pour effectuer l’étape de déploiement.                                      |
    | Impact sur les utilisateurs    | Impact du déploiement de l’étape sur les utilisateurs du locataire.                             |
    | Pour vos utilisateurs | Les liens vers les ressources que les utilisateurs du locataire peuvent trouver utiles.                             |
    | Étapes suivantes     | Liens et conseils concernant les étapes suivantes applicables.                                |

    Les étapes de déploiement incluent un ou plusieurs processus qui doivent être terminés. La page Étape de déploiement comprend un tableau qui répertorie chaque processus inclus dans l’étape de déploiement et fournit les informations suivantes :

    | Colonne            | Description |
    |-------------------|-------------------------------------------------------------|
    | Nom du processus      | Nom du processus, qui, lorsqu’il est sélectionné, ouvre l’onglet Processus applicable.          |
    | État            | État détecté de ces configurations de paramètre incluses dans le processus de déploiement.           |
    | Portail de gestion | Portail par le biais duquel les paramètres de configuration associés au processus sont gérés. |

## <a name="deploy-a-deployment-step"></a>Déployer une étape de déploiement

1. Dans la page de navigation de gauche, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez le locataire que vous souhaitez afficher.

3. Sélectionnez l’onglet **Plan de déploiement** .

4. Dans la liste des étapes de déploiement, sélectionnez une étape de déploiement que vous souhaitez déployer.

5. Sélectionnez **Vérifier et déployer**.

6. Dans le volet **Confirmer les configurations** , sélectionnez **Déployer**.

## <a name="test-a-deployment-step"></a>Tester une étape de déploiement

Pour les étapes de déploiement déployées via des stratégies d’accès conditionnel, vous pouvez comparer les paramètres de configuration de l’étape de déploiement avec les paramètres de toutes les stratégies existantes sans déployer les paramètres sur le locataire.

1. Dans la page de navigation de gauche, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez le locataire que vous souhaitez afficher.

3. Sélectionnez l’onglet **Plan de déploiement** .

4. Dans la liste des étapes de déploiement, sélectionnez une étape de déploiement que vous souhaitez déployer.

5. Sélectionnez **Vérifier et déployer**.

6. Dans le volet **Confirmer les configurations** , sélectionnez **Tester ces paramètres sans déploiement**.

7. Sélectionnez **Tester**.

Le volet Confirmer les configurations se ferme et affiche la comparaison de stratégie. Chaque stratégie au sein du locataire existant est répertoriée dans la table des paramètres détectés.

La table paramètres détectés répertorie chaque stratégie existante et résume le nombre de paramètres et, entre parenthèses, le nombre d’utilisateurs qui se trouvent dans l’un des états suivants :

| État         | Description
|-------------|------------------------------------------------------------|
| Paramètres égaux       | Nombre total de paramètres de configuration dans le plan de déploiement avec une valeur équivalente dans le locataire.      |
| Paramètres manquants     | Nombre total de paramètres de configuration dans le plan de déploiement qui manquent une valeur dans le locataire.      |
| Paramètres en conflit | Nombre total de paramètres de configuration dans le plan de déploiement qui ont une valeur conflictuelle dans le locataire. |

Les paramètres détectés peuvent également être affichés dans une table modulaire qui fournit les détails des paramètres de configuration pour chaque stratégie au niveau du paramètre et de l’utilisateur et qui peut être triée selon chacun des états de paramètres suivants :

| État         | Description
|-------------|------------------------------------------------------------|
| Paramètres totaux       | Nombre total de paramètres de configuration inclus dans le processus de déploiement.                        |
| Paramètres égaux       | Nombre total de paramètres de configuration dans le plan de déploiement avec une valeur équivalente dans le locataire.      |
| Paramètres manquants     | Nombre total de paramètres de configuration dans le plan de déploiement qui manquent une valeur dans le locataire.      |
| Paramètres en conflit | Nombre total de paramètres de configuration dans le plan de déploiement qui ont une valeur conflictuelle dans le locataire. |
| Paramètres supplémentaires       | Nombre total de paramètres de configuration avec une valeur dans le locataire, mais aucune valeur dans le plan de déploiement.     |

Une fois cette comparaison effectuée, Lighthouse met automatiquement à jour l’état détecté, l’état du déploiement et l’état de l’étape de déploiement.

S’il n’existe aucune stratégie à comparer, sélectionnez Vérifier et déployer pour rouvrir le volet Confirmer les configurations, puis sélectionnez Déployer.

S’il existe des stratégies existantes à comparer, vous pouvez :

- Modifiez les paramètres de configuration du plan de déploiement et retestez-les par rapport aux stratégies existantes, **sélectionnez Vérifier et déployer** pour rouvrir le volet Confirmer les configurations, ajustez les paramètres de configuration souhaités, cochez la case, puis sélectionnez **Tester** en bas du volet.

- Modifiez les stratégies existantes dans le portail de gestion applicable pour rapprocher les différences par :
  - Application des paramètres manquants
  - Modification de paramètres en conflit
  - Suppression de stratégies existantes

Pour chaque processus de déploiement qui peut être automatisé via Lighthouse, il existe à la fois un état de déploiement et un état détecté.

- L’état détecté indique dans quelle mesure les paramètres de ce processus sont actuellement déployés.
- L’état du déploiement correspond à l’état du dernier déploiement sur le locataire.

Les étapes de déploiement peuvent être déployées indépendamment des stratégies existantes, mais ne seront pas considérées comme terminées tant qu’il n’y a pas de paramètres en conflit. L’échec de la résolution de ces paramètres conflictuels peut avoir un impact sur l’expérience utilisateur. 

Le déploiement de l’étape de déploiement dans des instances où il existe des paramètres égaux dans le locataire à partir d’une stratégie existante entraîne la duplication des paramètres existants au sein du locataire, mais n’affecte pas l’expérience utilisateur. 

Des paramètres supplémentaires sont fournis pour votre prise de conscience, mais ne vous obligent pas à prendre des mesures.

Pour plus d’informations sur la gestion des conflits de stratégie, consultez la [documentation sur l’accès conditionnel Azure AD](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Mettre à jour l’état de l’étape de déploiement

1. Dans la page de navigation de gauche, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez le locataire que vous souhaitez afficher.

3. Sélectionnez l’onglet **Plan de déploiement** .

4. Dans la liste des étapes de déploiement, sélectionnez une étape de déploiement à mettre à jour.

5. Dans la liste déroulante **Adresse à** , sélectionnez un état d’action.

    | État de l’action                        | Description      |
    |---------------------------------------|----------------------------------------|
    | Pour résoudre le problème                        | État par défaut de toutes les étapes de déploiement qui n’incluent PAS plusieurs processus d’étape de déploiement.      |
    | Planifié                           | L’étape de déploiement a été planifiée, mais n’a pas encore été effectuée.                                      |
    | Risque accepté                     | L’utilisateur a accepté le risque qui aurait autrement été évité en appliquant l’étape de déploiement. |
    | Risque résolu par le biais d’un tiers | Le risque a été résolu par l’implémentation d’une application ou d’un logiciel tiers.             |
    | Résolu par d’autres moyens  | Le risque a été résolu par d’autres moyens, tels que l’implémentation d’un outil interne.    |
    | Configuration manuelle appliquée      | La configuration prescrite dans le plan de déploiement a été appliquée manuellement.                         |

## <a name="share-deployment-step"></a>Étape de déploiement de partage

1. Dans la page de navigation de gauche, sélectionnez **Locataires**.

2. Dans la liste des locataires, sélectionnez le locataire que vous souhaitez afficher.

3. Sélectionnez l’onglet **Plan de déploiement** .

4. Dans la liste des étapes de déploiement, sélectionnez une étape de déploiement que vous souhaitez partager.

5. Dans la liste déroulante **Partager** , sélectionnez l’une des options suivantes.

    | Option  | Description |
    |-----------|-------------------------------------------------------------------------|
    | Copy  | Copie un lien vers l’étape de déploiement dans votre Presse-papiers.                                     |
    | E-mail | Ouvre votre nouveau message électronique sur votre ordinateur local et insère un lien vers l’étape de déploiement. |

    Le lien permet à toute personne disposant d’autorisations dans votre organisation d’afficher le plan de déploiement du locataire.


## <a name="related-content"></a>Contenu connexe

[Vue d’ensemble de l’utilisation de Microsoft 365 Lighthouse lignes de base pour déployer des configurations de locataire standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)\
[Vue d’ensemble de la page Windows 365 (PC cloud) dans Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md) (article)\
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)\
[Configurer Microsoft 365 Lighthouse sécurité du portail](m365-lighthouse-configure-portal-security.md) (article) 