---
title: Créer, publier ou appliquer automatiquement des étiquettes de rétention
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
description: Instructions pour créer, publier et appliquer automatiquement des étiquettes de rétention pour conserver les informations nécessaires, supprimer l’inutile et déclarer un élément en tant qu’enregistrement dans votre environnement Office 365.
ms.openlocfilehash: 035038c90179354e0497813326b1fdad01693bec
ms.sourcegitcommit: 589f78fc0f39aff9109959ded48d146cc32fc3c5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2020
ms.locfileid: "44761650"
---
# <a name="create-publish-and-auto-apply-retention-labels"></a>Créer, publier ou appliquer automatiquement des étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Utilisez les informations suivantes pour créer des [étiquettes de rétention](labels.md), puis appliquez-les automatiquement aux documents et e-mails, ou publiez-les afin que les utilisateurs puissent les appliquer manuellement.

Les étiquettes de rétention vous permettent de conserver ce qui est nécessaire et de supprimer l’inutile. Elles s’utilisent également pour déclarer un élément en tant qu’enregistrement dans le cadre d’une [gestion des enregistrements](records-management.md) pour vos données Microsoft 365.

L’emplacement dans lequel vous créez et configurez vos étiquettes de rétention dépend de votre utilisation ou non de la gestion des enregistrements. Des instructions sont fournies pour les deux scénarios.

## <a name="before-you-begin"></a>Avant de commencer

Les membres de votre équipe de conformité appelés à créer des étiquettes de rétention ont besoin d’autorisations pour accéder au Centre de sécurité et de conformité. Par défaut, votre administrateur locataire a accès à cet emplacement et peut accorder l’accès aux responsables de la mise en conformité et à d’autres personnes du Centre de sécurité et de conformité, sans leur donner toutes les autorisations d’un administrateur locataire. Pour ce faire, nous vous recommandons d’accéder à la page **Autorisations** du Centre de sécurité et de conformité, de modifier le groupe de rôles **Administrateur de conformité** et d’ajouter des membres à ce groupe de rôles. 
  
Pour obtenir plus d’informations, consultez l’article [Octroi de l’accès au Centre de sécurité &amp; conformité Office 365 aux utilisateurs](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
These permissions are required only to create and apply retention labels and a label policy. Policy enforcement does not require access to the content.

## <a name="create-and-configure-retention-labels"></a>Créer et configurer des étiquettes de rétention

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements :
        - **Solutions** > **Gestion des enregistrements** > **Plan de fichiers** onglet > **+ Créer une étiquette** > **Étiquette de rétention**
        
    - Si vous n’utilisez pas la gestion des enregistrements :
       - **Solutions** > **Gouvernance d’informations** > **Étiquettes** onglet > + **Créer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant. Si vous utilisez la gestion des enregistrements :
    
    - Pour plus d’informations sur les descripteurs de plan de fichier, consultez [Utiliser le plan de gestion des fichiers pour gérer les étiquettes de rétention](file-plan-manager.md)
    
    - Pour utiliser l’étiquette de rétention pour déclarer du contenu en tant qu’enregistrement, activez la case à cocher **Utiliser une étiquette pour classifier du contenu en tant qu’« enregistrement »**.

3. Répétez ces étapes pour créer d’autres étiquettes.

Pour modifier une étiquette existante, sélectionnez-la, puis sélectionnez **Modifier l’étiquette** pour démarrer le même Assistant qui vous permet de modifier les descriptions d’étiquette et les [Paramètres éligibles](#updating-retention-labels-and-their-policies) à l’étape 2. Vous pouvez également sélectionner une option disponible **Modifier** pour accéder directement à la page correspondante afin de mettre à jour.

## <a name="publish-retention-labels-by-creating-a-retention-label-policy"></a>Publier des étiquettes de rétention en créant une stratégie de rétention d’étiquette

Publiez vos étiquettes de rétention pour que les utilisateurs puissent les appliquer manuellement.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements :
        - **Solutions** > **Gestion des enregistrements** > > **Stratégies d’étiquette** onglet > **Publier des étiquettes**
    
    - Si vous n’utilisez pas la gestion des enregistrements :
        - **Solutions** > **Gouvernance d’informations** > **Stratégies d’étiquette** onglet > **Publier des étiquettes**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant.
    
    Pour plus d’informations sur la prise en charge des emplacements par des étiquettes de rétention, voir la section [Étiquettes de rétention et emplacements](labels.md#retention-label-policies-and-locations). 

Pour modifier une stratégie d’étiquette de rétention existante, sélectionnez-la, puis sélectionnez **Modifier la stratégie** pour démarrer le même Assistant qui vous permet de modifier les descriptions de la stratégie et les [Paramètres éligibles](#updating-retention-labels-and-their-policies) à l’étape 2. Vous pouvez également sélectionner une option disponible **Modifier** pour accéder directement à la page correspondante afin de mettre à jour.

## <a name="auto-apply-a-retention-label"></a>Étiquettes de rétention appliquées automatiquement

Appliquez automatiquement une étiquette de rétention, en fonction des conditions que vous indiquez.

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/), accédez à l’un des emplacements suivants :
    
    - Si vous utilisez la gestion des enregistrements : **Gouvernance d’informations** :
        - **Solutions** > **Gestion des enregistrements** > **Stratégies d’étiquette** onglet > **Auto-appliquer une étiquette**
    
    - Si vous n’utilisez pas la gestion des enregistrements :
        - **Solutions** > **Gouvernance d’informations** > **Stratégies d’étiquette** onglet > **Auto-appliquer une étiquette**
    
    Votre option ne s’affiche pas immédiatement ? Sélectionnez tout d’abord **Afficher tout**. 

2. Suivez les invites de l’Assistant.
    
    Pour plus d’informations sur la configuration des conditions qui appliquent automatiquement l’étiquette de rétention, voir la section [Configuration des conditions d’application automatique des étiquettes de rétention](#configuring-conditions-for-auto-apply-retention-labels) sur cette page.
    
    Pour plus d’informations sur la prise en charge des emplacements par des étiquettes de rétention, voir la section [Étiquettes de rétention et emplacements](labels.md#retention-label-policies-and-locations).

Pour modifier une stratégie d’étiquette d’application existante, sélectionnez-la, puis sélectionnez **Modifier la stratégie** pour démarrer le même Assistant qui vous permet de modifier les descriptions de la stratégie et les [Paramètres éligibles](#updating-retention-labels-and-their-policies) à l’étape 2. Vous pouvez également sélectionner une option disponible **Modifier** pour accéder directement à la page correspondante afin de mettre à jour.


## <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Configuration des conditions d’application automatique des étiquettes de rétention

Vous pouvez appliquer automatiquement des étiquettes de rétention au contenu quand celui-ci inclut :
  
- [Types spécifiques d’informations sensibles](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)
    
- [Mots clés spécifiques correspondant à une requête que vous créez](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Correspondance pour les classifieurs entraînables](#auto-apply-labels-to-content-by-using-trainable-classifiers)
    
![Page Choisir une condition pour l'application automatique de l’étiquette](../media/classifier-pre-trained-apply-label-match-trainable-classifier.png)

L’application automatique d'étiquettes de rétention à tout le contenu correspondant aux conditions que vous avez configurées peut prendre jusqu’à sept jours.

### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Application automatique d’étiquettes au contenu incluant des types spécifiques d’informations sensibles

Lorsque vous créez des étiquettes de rétention d’application automatique pour des informations sensibles, vous voyez s’afficher la même liste de modèles de stratégie que lorsque vous créez une stratégie de protection contre la perte de données. Chaque modèle de stratégie est préconfiguré pour rechercher des types spécifiques d’informations sensibles. Par exemple, le modèle illustré ici recherche les numéros ITIN, SSN et de passeport américains. Pour plus d’informations sur la protection contre la perte de données, voir [Vue d’ensemble des stratégies de protection contre la perte de données](data-loss-prevention-policies.md).
  
![Modèles de stratégie avec des types d’informations sensibles](../media/dafd87d4-c7bb-439a-ac7b-193c018f98a5.png)
  
After you select a policy template, you can add or remove any types of sensitive information, and you can change the instance count and match accuracy. In the example shown here, a retention label will be auto-applied only when:
  
- The content contains between 1 and 9 instances of any of these three sensitive information types. You can delete the **max** value so that it changes to **any**.
    
- The type of sensitive information that's detected has a match accuracy (or confidence level) of at least 75. Many sensitive information types are defined with multiple patterns, where a pattern with a higher match accuracy requires more evidence to be found (such as keywords, dates, or addresses), while a pattern with a lower match accuracy requires less evidence. Simply put, the lower the **min** match accuracy, the easier it is for content to match the condition. 
    
Pour plus d’informations relatives à ces options, voir[optimisation des règles afin de les rendre plus facile ou plus difficile à associer](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).
    
![Options permettant d’identifier les types d’informations sensibles](../media/de255881-f596-4c8d-8359-e974e3a0819a.png)
  
### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Application automatique d’étiquettes au contenu comprenant des mots clés ou des propriétés pouvant faire l’objet d’une recherche

You can auto-apply labels to content that satisfies certain conditions. The conditions now available support applying a label to content that contains specific words, phrases, or values of searchable properties. You can refine your query by using search operators like AND, OR, and NOT.

Pour obtenir plus d’informations sur la syntaxe de requête, consultez l’article suivant :

- [Référence de syntaxe de langage de requête de mot clé (KQL)](https://docs.microsoft.com/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

Query-based labels use the search index to identify content. For more information on valid searchable properties, see:

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


### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Appliquer automatiquement des étiquettes au contenu à l’aide de classifieurs entraînables

Lorsque vous choisissez l’option de classifieur entraînable, vous pouvez sélectionner un classifieur intégré ou un classifieur personnalisé. Les classifieurs intégrés incluent : **CV**, **SourceCode**, **Harcèlement ciblé**, **Blasphème** et la **Menace** :

![Sélectionnez un classificateur à entraîner](../media/retention-label-classifers.png)

Pour appliquer automatiquement une étiquette à l’aide de cette option, les sites et boîtes aux lettres SharePoint Online doivent avoir au moins 10 Mo de données.

Pour plus d’informations sur les classifieurs entraînables, voir la [Prise en main des classifieurs entrainables (version d'évaluation)](classifier-getting-started-with.md).

Pour consulter un exemple de configuration, voir [Comment préparer et utiliser un classifieur prêt à l'emploi](classifier-using-a-ready-to-use-classifier.md#how-to-verify-that-a-built-in-classifier-will-meet-your-needs).

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Délai d’activation des étiquettes de rétention

Lorsque vous publiez ou appliquez automatiquement des étiquettes de rétention, elles ne prennent pas effet immédiatement :
  
1. La première étape consiste à accéder au centre d’administration pour synchroniser la stratégie d’étiquette avec les emplacements définis dans la stratégie.
    
2. Ensuite, selon l’emplacement, un certain temps pourra s’écouler avant que des étiquettes de rétention soient rendues disponibles aux utilisateurs finaux ou que des étiquettes d’application automatique soient attribuées à du contenu. Le temps nécessaire dépend de l’emplacement et du type d’étiquette de rétention.
    
### <a name="published-retention-labels"></a>Étiquettes de rétention publiées

If you publish retention labels to SharePoint or OneDrive, those labels  typically appear for end users to select within one day. However, allow up to seven days. If you publish retention labels to Exchange, it can take up to seven days for those retention labels to appear for end users, and the mailbox must contain at least 10 MB of data.

Par exemple :
  
![Diagramme de la date d’effet des étiquettes manuelles](../media/b19f3a10-f625-45bf-9a53-dd14df02ae7c.png)
  
### <a name="auto-apply-retention-labels"></a>Étiquettes de rétention appliquées automatiquement

Si vous appliquez automatiquement des étiquettes de rétention à du contenu remplissant des critères spécifiques, l’application de ces étiquettes à ce contenu peut prendre jusqu’à sept jours.
  
![Diagramme indiquant quand les étiquettes d’application automatique prennent effet](../media/b8c00657-477a-4ade-b914-e643ef97a10d.png)
  
### <a name="how-to-check-on-the-status-of-retention-labels-published-to-exchange"></a>Vérifier l’état des étiquettes de rétention publiées dans Exchange

Dans Exchange Online, les étiquettes de rétention deviennent disponibles pour les utilisateurs finaux à l’issue d’un processus qui s’exécute tous les sept jours. Powershell vous permet de voir quand ce processus a été exécuté pour la dernière fois et définit donc la période de sa prochaine exécution.
  
1. [Connectez-vous à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?linkid=799773).
    
2. Exécutez les commandes suivantes :
    
   ```powershell
   $logProps = Export-MailboxDiagnosticLogs <user> -ExtendedProperties
   ```

   ```powershell
   $xmlprops = [xml]($logProps.MailboxLog)
   ```

   ```powershell
   $xmlprops.Properties.MailboxTable.Property | ? {$_.Name -like "ELC*"}   ```

In the results, the `ELCLastSuccessTimeStamp` (UTC) property shows when the system last processed your mailbox. If it has not happened since the time you created the policy, the labels are not going to appear. To force processing, run  `Start-ManagedFolderAssistant -Identity <user>`.
    
If labels aren't appearing in Outlook on the web and you think they should be, make sure to clear the cache in your browser (CTRL+F5).
    

## Updating retention labels and their policies

When you edit a retention label, retention label policy, or auto-apply policy, and the retention label or policy is already applied to content, your updated settings will automatically be applied to this content in addition to content that's newly identified.

Some settings can't be changed after the label or policy is created and saved, which include:
- The retention settings except the retention period, unless you've configured the label to retain or delete the content based on when it was created.
- The option to classify as a record.

## Find the PowerShell cmdlets for retention labels

To use the retention label cmdlets:
  
1. [Connect to the Office 365 Security & Compliance Center Powershell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)
    
2. Use these Office 365 Security & Compliance Center cmdlets:
    
    - [Get-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/get-compliancetag)
    
    - [New-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/new-compliancetag)
    
    - [Remove-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/remove-compliancetag)
    
    - [Set-ComplianceTag](https://docs.microsoft.com/powershell/module/exchange/set-compliancetag)
    
    - [Enable-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/enable-compliancetagstorage)
    
    - [Get-ComplianceTagStorage](https://docs.microsoft.com/powershell/module/exchange/get-compliancetagstorage)
    
    - [Get-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/get-retentioncompliancepolicy)
    
    - [New-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancepolicy)
    
    - [Remove-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/remove-retentioncompliancepolicy)
    
    - [Set-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancepolicy)
    
    - [Get-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/get-retentioncompliancerule)
    
    - [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancerule)
    
    - [Remove-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/remove-retentioncompliancerule)
    
    - [Set-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancerule)
