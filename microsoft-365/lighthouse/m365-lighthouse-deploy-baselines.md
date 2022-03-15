---
title: Déployer les Microsoft 365 Lighthouse base de référence
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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment déployer des Microsoft 365 Lighthouse de référence.
ms.openlocfilehash: 0e19843ee6cfebaf9b37e10929884d0671608451
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504491"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Déployer les Microsoft 365 Lighthouse base de référence

Microsoft 365 Lighthouse vous permet de déployer des configurations de client géré standard pour sécuriser les utilisateurs, les appareils et les données au sein des clients. Il existe sept [configurations de référence par défaut qui](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) sont standard avec Le Caserr. À l’aide de la fonctionnalité plan de déploiement de l’entreprise, vous pouvez afficher, tester et déployer des configurations de sécurité sur tous vos locataires. Un plan de déploiement est uniquement disponible pour les locataires actifs. Une fois qu’un client est intégré, vous pouvez comparer la configuration actuelle de vos clients à la configuration de référence par défaut et prendre les mesures appropriées.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que vous et vos clients respectez les conditions requises répertoriées dans [la](m365-lighthouse-requirements.md) Microsoft 365 Lighthouse.

## <a name="view-a-deployment-plan"></a>Afficher un plan de déploiement

1. Dans la page de navigation de gauche, **sélectionnez Locataires**.

2. Dans la liste des locataires, sélectionnez le client que vous souhaitez afficher.

3. Sélectionnez **l’onglet Plan de** déploiement.

    L’onglet Plan de déploiement fournit une liste utilisable dans une recherche et exportable de chaque étape de déploiement incluse dans le plan de déploiement du client, qui inclut les informations suivantes pour chaque étape de déploiement :

    | Colonne            | Description |
    |-----------------|-------------------------------------------------------------------------------------|
    | Étape de déploiement | Description de l’étape de déploiement.                                                     |
    | État          | État de l’étape de déploiement.                                                  |
    | Baseline        | Base de référence à partir de laquelle l’étape de déploiement est dérivée.                             |
    | Catégorie        | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données. |
    | Dernière mise à jour    | Date à laquelle l’étape de déploiement a été mise à jour pour la dernière fois.                             |

4. Dans la liste, sélectionnez une étape de déploiement à réviser.

    La page Étape du déploiement fournit les informations suivantes :

    | Colonne            | Description |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Résumé        | Résumé de l’objectif de l’étape de déploiement.                                         |
    | Baseline       | Base de référence à partir de laquelle l’étape de déploiement est dérivée.                             |
    | Catégorie       | Indique si l’étape de déploiement est associée à la gestion des appareils, de l’identité ou des données. |
    | Référence SKU requise   | S SKUs requis pour effectuer l’étape de déploiement.                                      |
    | Impact sur les utilisateurs    | Impact du déploiement de l’étape pour les utilisateurs du client.                             |
    | Pour vos utilisateurs | Les liens vers les ressources que les utilisateurs du client peuvent trouver utiles.                             |
    | Étapes suivantes     | Liens et conseils sur les étapes suivantes applicables.                                |

    Les étapes de déploiement sont constituées d’un ou de plusieurs processus qui doivent être effectués pour satisfaire aux exigences de l’étape de déploiement. La page Étape du déploiement inclut le tableau des processus qui répertorie chaque processus inclus dans l’étape de déploiement et fournit les informations suivantes :

    | Colonne            | Description |
    |-------------------|-------------------------------------------------------------|
    | Nom du processus      | Nom du processus, qui, lorsqu’il est sélectionné, ouvre l’onglet Processus applicable.          |
    | État            | État détecté de ces configurations de paramètres incluses dans le processus de déploiement.           |
    | Portail de gestion | Portail via lequel les paramètres de configuration associés au processus sont gérés. |

## <a name="deploy-a-deployment-step"></a>Déployer une étape de déploiement

1. Dans la page de navigation de gauche, **sélectionnez Locataires**.

2. Dans la liste des locataires, sélectionnez le client que vous souhaitez afficher.

3. Sélectionnez **l’onglet Plan de** déploiement.

4. Dans la liste Étape de déploiement, sélectionnez une étape de déploiement à déployer.

5. Sélectionnez **Examiner et déployer**.

6. Dans le **volet Confirmer les configurations** , sélectionnez **Déployer**.

## <a name="test-a-deployment-step"></a>Tester une étape de déploiement

Pour les étapes de déploiement déployées par le biais de stratégies d’accès conditionnel, vous pouvez comparer les paramètres de configuration de l’étape de déploiement avec ceux des stratégies existantes sans déployer les paramètres sur le client.

1. Dans la page de navigation de gauche, **sélectionnez Locataires**.

2. Dans la liste des locataires, sélectionnez le client que vous souhaitez afficher.

3. Sélectionnez **l’onglet Plan de** déploiement.

4. Dans la liste Étape de déploiement, sélectionnez une étape de déploiement à déployer.

5. Sélectionnez **Examiner et déployer**.

6. Dans le **volet Confirmer les configurations** , **sélectionnez Tester ces paramètres sans déploiement**.

7. Sélectionnez **Test**.

Le volet Confirmer les configurations se ferme et affiche la comparaison de stratégies. Chaque stratégie au sein du client existant est répertoriée dans la table Paramètres détectés.

Le tableau Paramètres détectés répertorie chaque stratégie existante et récapitule le nombre de paramètres et, entre parenthèses, le nombre d’utilisateurs qui se sont dans l’un des états suivants :

| État         | Description
|-------------|------------------------------------------------------------|
| Paramètres égaux       | Nombre total de paramètres de configuration dans le plan de déploiement avec une valeur équivalente dans le client.      |
| Paramètres manquants     | Nombre total de paramètres de configuration dans le plan de déploiement dont il manque une valeur dans le client.      |
| Paramètres conflictuelles | Nombre total de paramètres de configuration dans le plan de déploiement qui ont une valeur en conflit dans le client. |

Les paramètres détectés peuvent également être vus dans une table modulaire qui fournit des détails sur les paramètres de configuration pour chaque stratégie au niveau du paramètre et de l’utilisateur, et peut être trié selon chacun des états de paramètres suivants :

| État         | Description
|-------------|------------------------------------------------------------|
| Nombre total de paramètres       | Nombre total de paramètres de configuration inclus dans le processus de déploiement.                        |
| Paramètres égaux       | Nombre total de paramètres de configuration dans le plan de déploiement avec une valeur équivalente dans le client.      |
| Paramètres manquants     | Nombre total de paramètres de configuration dans le plan de déploiement dont il manque une valeur dans le client.      |
| Paramètres conflictuelles | Nombre total de paramètres de configuration dans le plan de déploiement qui ont une valeur en conflit dans le client. |
| Paramètres supplémentaires       | Nombre total de paramètres de configuration avec une valeur dans le client, mais aucune valeur dans le plan de déploiement.     |

Lorsque cette comparaison est réalisée, le Logiciel d’installation met automatiquement à jour l’état détecté, l’état du déploiement et l’état de l’étape de déploiement.

S’il n’existe aucune stratégie à comparer, sélectionnez Révision et déploiement pour rouvrir le volet Confirmer les configurations et sélectionnez Déployer.

S’il existe des stratégies existantes à comparer, vous pouvez :

- Modifiez les paramètres de configuration du plan de déploiement et testez-les à nouveau par rapport  aux stratégies existantes, sélectionnez Examiner et déployer pour rouvrir le volet Confirmer les configurations, ajustez les paramètres de configuration souhaités, réélectionnez la case à cocher, puis sélectionnez **Tester** en bas du volet.

- Modifiez les stratégies existantes dans le portail de gestion applicable pour rapprocher les différences en :
  - Application des paramètres manquants
  - Modification des paramètres conflictuelles
  - Suppression de stratégies existantes

Pour chaque processus de déploiement qui peut être automatisé via le Contrôle d’installation, il existe à la fois un état de déploiement et un état détecté.

- L’état détecté indique dans quelle mesure les paramètres de ce processus sont actuellement déployés.
- L’état du déploiement est l’état du dernier déploiement pour le client.

Les étapes de déploiement peuvent être déployées quelles que soient les stratégies existantes, mais ne seront pas considérées comme terminées tant qu’aucun paramètre n’est en conflit. L’échec de la résolution de ces paramètres conflictuelles peut avoir un impact sur l’expérience utilisateur. 

Le déploiement de l’étape de déploiement dans les cas où des paramètres égaux sont présents dans le client à partir d’une stratégie existante entraîne la duplication des paramètres existants au sein du client, mais n’a pas d’impact sur l’expérience utilisateur. 

Des paramètres supplémentaires sont fournis pour votre sensibilisation, mais ne vous obligez pas à prendre des mesures.

Pour plus d’informations sur la gestion des conflits de stratégie, [Azure AD documentation sur l’accès conditionnel](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Mettre à jour l’état de l’étape de déploiement

1. Dans la page de navigation de gauche, **sélectionnez Locataires**.

2. Dans la liste des locataires, sélectionnez le client que vous souhaitez afficher.

3. Sélectionnez **l’onglet Plan de** déploiement.

4. Dans la liste des étapes de déploiement, sélectionnez l’étape de déploiement que vous souhaitez mettre à jour.

5. Dans la **liste de listes** de listes d’adresses À, sélectionnez un état d’action.

    | État de l’action                        | Description      |
    |---------------------------------------|----------------------------------------|
    | Adresse                        | État par défaut de toutes les étapes de déploiement qui n’incluent PAS plusieurs processus d’étape de déploiement.      |
    | Planifié                           | L’étape de déploiement a été planifiée mais n’est pas encore terminée.                                      |
    | Risque accepté                     | L’utilisateur a accepté le risque qui aurait été évité en appliquant l’étape de déploiement. |
    | Risque résolu par le biais d’un tiers | Le risque a été résolu par l’implémentation d’une application ou d’un logiciel tiers.             |
    | Résolu par d’autres moyens  | Le risque a été résolu par d’autres moyens, tels que l’implémentation d’un outil interne.    |
    | Configuration manuelle appliquée      | La configuration prescrite dans le plan de déploiement a été appliquée manuellement.                         |

## <a name="share-deployment-step"></a>Étape de déploiement du partage

1. Dans la page de navigation de gauche, **sélectionnez Locataires**.

2. Dans la liste des locataires, sélectionnez le client que vous souhaitez afficher.

3. Sélectionnez **l’onglet Plan de** déploiement.

4. Dans la liste Étape du déploiement, sélectionnez une étape de déploiement que vous souhaitez partager.

5. Dans la **liste** de listes de partage, sélectionnez l’une des options suivantes.

    | Option  | Description |
    |-----------|-------------------------------------------------------------------------|
    | Copier  | Copie un lien vers l’étape de déploiement dans votre Presse-papiers.                                     |
    | E-mail | Ouvre votre nouveau message électronique sur votre ordinateur local et insère un lien vers l’étape de déploiement. |

    Le lien permet à toute personne  autorisée dans votre organisation d’afficher le plan de déploiement du client.


## <a name="related-content"></a>Contenu associé

[Vue d’ensemble de l’utilisation des lignes de base pour déployer des configurations client standard](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (article)\
[Microsoft 365 vue d’ensemble de la page Tenants](m365-lighthouse-tenants-page-overview.md) (article)\
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Configurer la sécurité Microsoft 365 Lighthouse portail d’entreprise](m365-lighthouse-configure-portal-security.md) (article) 