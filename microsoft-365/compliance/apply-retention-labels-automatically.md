---
title: Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Créez et publiez automatiquement des étiquettes de rétention afin de pouvoir les appliquer de manière automatique pour conserver les éléments dont vous avez besoin et de supprimer ceux qui sont inutiles
ms.openlocfilehash: 80a5ef502450a24d9c8aeeb08d571bfcbd51a4e3
ms.sourcegitcommit: 51097b18d94da20aa727ebfbeb6ec84c263b25c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46648803"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Application automatique d’une étiquette de rétention pour conserver ou supprimer du contenu

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

L’une des fonctionnalités les plus puissantes des [étiquettes de rétention](retention.md) est la possibilité d’appliquer celles-ci automatiquement à tout contenu correspondant à certaines conditions spécifiques. Dans ce cas, les personnes au sein de votre organisation ne doivent pas appliquer les étiquettes de rétention. Microsoft 365 s’en charge à leur place.
  
Les étiquettes de rétention appliquées automatiquement sont puissantes pour les raisons suivantes :
  
- Vous n’avez pas besoin de former les utilisateurs concernant l’ensemble de vos classifications.
    
- Vous n’avez pas à dépendre des utilisateurs pour classer tout le contenu correctement.
    
- Les utilisateurs n’ont plus besoin de connaître les stratégies de gouvernance des données : ils peuvent se concentrer sur leur travail.
    
Vous pouvez appliquer automatiquement des étiquettes de rétention à du contenu lorsque celui-ci contient des informations sensibles, des mots clés ou une correspondance pour des [classifieurs pouvant être formés](classifier-getting-started-with.md).
    
Les processus d’application automatique d’une étiquette de rétention sont fonction des conditions suivantes :

![Diagramme des rôles et des tâches pour les étiquettes à appliquer automatiquement](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

Utilisez les instructions suivantes pour les deux étapes d’administration.

> [!NOTE]
> Les stratégies automatiques utilisent l’étiquetage côté service avec des conditions pour appliquer automatiquement des étiquettes de rétention. Vous pouvez également appliquer automatiquement une étiquette de rétention avec une stratégie d’étiquette lorsque vous procédez comme suit : 
>
> - Appliquez une étiquette de rétention par défaut à une bibliothèque, un dossier ou à un groupe de documents SharePoint afin que le contenu sans étiquette dans ce conteneur soit automatiquement étiqueté
>- Application automatique d’une étiquette de rétention pour les e-mails à l’aide de règles
>
> Pour ces scénarios, voir [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Avant de commencer

L’administrateur général de votre organisation dispose de toutes les autorisations pour créer et gérer les étiquettes de rétention et leurs stratégies. Si vous ne vous connectez pas en tant qu’administrateur général, voir [Autorisations nécessaires pour créer et gérer des stratégies et des étiquettes de confidentialité](get-started-with-retention.md#permissions-required-to-create-and-manage-retention-policies-and-retention-labels).

## <a name="how-to-auto-apply-a-retention-label"></a>Application automatique d’étiquettes de rétention

Tout d’abord, créez votre étiquette de rétention. Créez ensuite une stratégie automatique pour appliquer l’étiquette. Si vous avez déjà créé votre étiquette de rétention, passez à [Création d’une stratégie automatique](#step-2-create-an-auto-apply-policy).

Les instructions de navigation varient selon que vous utilisez la [gestion des enregistrements](records-management.md) ou non. Des instructions sont fournies pour les deux scénarios.

### <a name="step-1-create-a-retention-label"></a>Étape 1 : créer une étiquette de rétention

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements :
        - **Solutions** > **Gestion des enregistrements** > **Plan de fichiers** onglet > **+ Créer une étiquette** > **Étiquette de rétention**
        
    - Si vous n’utilisez pas la gestion des enregistrements :
       - **Solutions** > **Gouvernance d’informations** > **Étiquettes** onglet > + **Créer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant. Si vous utilisez la gestion des enregistrements :
    
    - Pour plus d’informations sur les descripteurs de plan de fichier, consultez [Utiliser le plan de gestion des fichiers pour gérer les étiquettes de rétention](file-plan-manager.md)
    
    - Pour utiliser l’étiquette de rétention pour déclarer du contenu en tant qu’enregistrement, activez la case à cocher **Utiliser une étiquette pour classifier du contenu en tant qu’« enregistrement »**.

Pour modifier une étiquette existante, sélectionnez-la, puis sélectionnez **Modifier l’étiquette** pour démarrer le même Assistant qui vous permet de modifier les descriptions d’étiquette et les [Paramètres éligibles](#updating-retention-labels-and-their-policies) à l’étape 2. Vous pouvez également sélectionner une option disponible **Modifier** pour accéder directement à la page correspondante afin de mettre à jour.


### <a name="step-2-create-an-auto-apply-policy"></a>Étape 2 : créer une stratégie d’application automatique

Lorsque vous créez une stratégie d’application automatique, vous sélectionnez une étiquette de rétention pour l’appliquer automatiquement à du contenu, en fonction des conditions spécifiées.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements : **Gouvernance d’informations** :
        - **Solutions** > **Gestion des enregistrements** > **Stratégies d’étiquette** onglet > **Auto-appliquer une étiquette**
    
    - Si vous n’utilisez pas la gestion des enregistrements :
        - **Solutions** > **Gouvernance d’informations** > **Stratégies d’étiquette** onglet > **Auto-appliquer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant.
    
    Pour plus d’informations sur la configuration des conditions qui appliquent automatiquement l’étiquette de rétention, voir la section [Configuration des conditions d’application automatique des étiquettes de rétention](#configuring-conditions-for-auto-apply-retention-labels) sur cette page.
    
    Pour plus d’informations sur la prise en charge des emplacements par des étiquettes de rétention, voir la section [Étiquettes de rétention et emplacements](retention.md#retention-label-policies-and-locations).

Pour modifier une stratégie d’étiquette d’application existante, sélectionnez-la, puis sélectionnez **Modifier la stratégie** pour démarrer le même Assistant qui vous permet de modifier les descriptions de la stratégie et les [Paramètres éligibles](#updating-retention-labels-and-their-policies) à l’étape 2. Vous pouvez également sélectionner une option disponible **Modifier** pour accéder directement à la page correspondante afin de mettre à jour.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Configuration des conditions d’application automatique des étiquettes de rétention

Vous pouvez appliquer automatiquement des étiquettes de rétention au contenu quand celui-ci inclut :

- [Types spécifiques d’informations sensibles](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Mots clés spécifiques correspondant à une requête que vous créez](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Correspondance pour les classifieurs entraînables](#auto-apply-labels-to-content-by-using-trainable-classifiers)

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Application automatique d’étiquettes au contenu incluant des types spécifiques d’informations sensibles

Lorsque vous créez des étiquettes de rétention d’application automatique pour des informations sensibles, vous voyez s’afficher la même liste de modèles de stratégie que lorsque vous créez une stratégie de protection contre la perte de données. Chaque modèle de stratégie est préconfiguré pour rechercher des types spécifiques d’informations sensibles. Par exemple, le modèle illustré ici recherche les numéros ITIN, SSN et de passeport américains. Pour plus d’informations sur la protection contre la perte de données, voir [Vue d’ensemble des stratégies de protection contre la perte de données](data-loss-prevention-policies.md).
  
![Modèles de stratégie avec des types d’informations sensibles](../media/dafd87d4-c7bb-439a-ac7b-193c018f98a5.png)
  
Après avoir sélectionné un modèle de stratégie, vous pouvez ajouter ou supprimer tout type d’informations sensibles, et vous pouvez modifier le nombre d’instances et la précision de correspondance. Dans l’exemple présenté ici, une étiquette de rétention sera appliquée automatiquement uniquement dans les cas suivants :
  
- Le contenu comprend entre 1 et 9 instances de l’un de ces trois types d’informations sensibles. Vous pouvez supprimer la valeur **max** pour la définir sur **any**.
    
- Le type d’information sensible est détecté avec une précision de correspondance (ou niveau de confiance) minimale de 75. De nombreux types d’informations sensibles sont définis avec plusieurs modèles. Un modèle définissant une précision de correspondance élevée impose davantage de critères (par exemple, mots clés, dates ou adresses) qu’un modèle définissant une précision de correspondance moindre. Plus la valeur de précision de correspondance **min** est faible, plus il y a de contenu correspondant à la condition. 
    
Pour plus d’informations relatives à ces options, voir[optimisation des règles afin de les rendre plus facile ou plus difficile à associer](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).
    
![Options permettant d’identifier les types d’informations sensibles](../media/de255881-f596-4c8d-8359-e974e3a0819a.png)
  
#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Application automatique d’étiquettes au contenu comprenant des mots clés ou des propriétés pouvant faire l’objet d’une recherche

Vous pouvez appliquer automatiquement des étiquettes au contenu remplissant certaines conditions. Les conditions actuellement disponibles prennent en charge l’application d’une étiquette au contenu comprenant des mots, des phrases spécifiques ou des valeurs de propriété pouvant faire l’objet d’une recherche. Vous pouvez affiner votre requête à l’aide des opérateurs de recherche tels que AND, OR et NOT.

Lors de l’application automatique d’étiquettes pour les propriétés pouvant faire l’objet d’une recherche, l’alias d’une propriété gérée ne peut pas être utilisé dans la requête. Il doit s’agir du nom réel de la propriété gérée, par exemple, RefinableString01.

Pour obtenir plus d’informations sur la syntaxe de requête, consultez l’article suivant :

- [Référence de syntaxe de langage de requête de mot clé (KQL)](https://docs.microsoft.com/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

Les étiquettes basées sur une requête utilisent l’index de recherche pour identifier le contenu. Pour plus d’informations sur les propriétés valides utilisables dans une requête, consultez l’article suivant :

- [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)
- [Vue d’ensemble des propriétés analysées et gérées dans SharePoint Server](https://docs.microsoft.com/SharePoint/technical-reference/crawled-and-managed-properties-overview)

Exemples de requêtes :

- Exchange
    - subject:"Quarterly Financials"
    - recipients:garthf<!--nolink-->@contoso.com
- SharePoint et OneDrive
    - contenttype:contract
    - site:https<!--nolink-->://contoso.sharepoint.com/sites/teams/procurement AND contenttype:contract

![Éditeur de requête](../media/ac5b8e5e-7453-4ec7-905c-160df57298d3.png)


#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Appliquer automatiquement des étiquettes au contenu à l’aide de classifieurs entraînables

Lorsque vous choisissez l’option de classifieur entraînable, vous pouvez sélectionner un classifieur intégré ou un classifieur personnalisé. Les classifieurs intégrés incluent : **CV**, **SourceCode**, **Harcèlement ciblé**, **Blasphème** et la **Menace** :

![Sélectionnez un classificateur à entraîner](../media/retention-label-classifers.png)

> [!CAUTION]
> Nous déprécions le **langage inconvenant** classifieur intégré, car il génère un grand nombre de faux positifs. N’utilisez pas ce classifieur intégré et si vous l’utilisez actuellement, vous devez déplacer vos processus métier. Nous vous recommandons d’utiliser les classifieurs intégrés de **Harcèlement ciblée** , de **blasphème** et de **Menace** à la place.

Pour appliquer automatiquement une étiquette à l’aide de cette option, les sites et boîtes aux lettres SharePoint Online doivent avoir au moins 10 Mo de données.

Pour plus d’informations sur les classifieurs entraînables, voir la [Prise en main des classifieurs entrainables (version d'évaluation)](classifier-getting-started-with.md).

Pour consulter un exemple de configuration, voir [Comment préparer et utiliser un classifieur prêt à l'emploi](classifier-using-a-ready-to-use-classifier.md#how-to-verify-that-a-built-in-classifier-will-meet-your-needs).

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Délai d’activation des étiquettes de rétention

Lorsque vous appliquez automatiquement des étiquettes de rétention, l’application de ces étiquettes à ce contenu peut prendre jusqu’à sept jours.
  
![Diagramme indiquant quand les étiquettes d’application automatique prennent effet](../media/b8c00657-477a-4ade-b914-e643ef97a10d.png)
  
## <a name="updating-retention-labels-and-their-policies"></a>Mise à jour des étiquettes de rétention et de leurs stratégies

Lorsque vous modifiez une étiquette de rétention ou une stratégie d’application automatique et que l’étiquette de rétention est déjà appliquée au contenu, vos paramètres mis à jour sont automatiquement appliqués à ce contenu, en plus du contenu nouvellement identifié.

Certains paramètres ne peuvent pas être modifiés une fois l’étiquette ou la stratégie créée et enregistrée, notamment :
- Paramètres de rétention à l’exception de la période de rétention, sauf si vous avez configuré l’étiquette pour conserver ou supprimer le contenu en fonction de sa date de création.
- Possibilité de classifier en tant qu’enregistrement.

## <a name="next-steps"></a>Étapes suivantes

Consultez [Utiliser les étiquettes de rétention pour gérer le cycle de vie des documents stockés dans SharePoint](auto-apply-retention-labels-scenario.md) pour un exemple de scénario qui utilise une stratégie d’application automatique avec des propriétés gérées dans SharePoint et la rétention basée sur les événements pour démarrer la période de rétention.
