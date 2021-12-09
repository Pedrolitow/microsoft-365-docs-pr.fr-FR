---
title: Migrer des stratégies de protection contre la perte de données Exchange Online vers le Centre de conformité
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Découvrez comment planifier et migrer vos stratégies Exchange protection contre la perte de données en ligne vers Microsoft 365 DLP.
ms.openlocfilehash: 744ba3edbee1c6b84df9b8b5316c7df7e734cd6d
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61374063"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Migrer des stratégies de protection contre la perte de données Exchange Online vers le Centre de conformité

Exchange Online stratégies de protection contre la perte de données [(DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) sont en cours d’precaté. [Des fonctionnalités DLP](dlp-learn-about-dlp.md)beaucoup plus riches, notamment Exchange Online DLP, sont proposées dans le centre [Microsoft 365 conformité.](https://compliance.microsoft.com/datalossprevention?viewid=policies) Vous pouvez utiliser l’Assistant Migration des stratégies DLP pour vous aider à faire migrer vos stratégies DLP Exchange Online vers le centre de conformité où vous les gérerez.

L’Assistant Migration fonctionne en lisant la configuration de vos stratégies DLP dans Exchange puis en créant des stratégies en double dans le Centre de conformité. Par défaut, l’Assistant crée les nouvelles versions des stratégies en mode **Test,** afin que vous pouvez voir l’impact qu’elles auraient dans votre environnement sans appliquer aucune des actions. Une fois que vous êtes prêt à passer entièrement aux versions du Centre de conformité, **_vous devez_**:

1. Désactivez ou supprimez la stratégie source dans le Exchange Admin Center (EAC).
1. Modifiez la version du Centre de conformité de la stratégie et modifiez son état de **Test** à **Appliquer.** 

> [!WARNING]
> Si vous ne supprimez pas ou ne désactivez pas la stratégie  source dans le CENTRE de conformité avant de définir la version du Centre de conformité pour appliquer les deux ensembles de stratégies, vous tenterez d’appliquer des actions et vous recevrez des événements en double. **_Il s’agit d’une configuration non pris en place._**


L’Assistant Migration migre uniquement les stratégies EXO et les règles de flux de messagerie associées. Les règles Exchange de flux de messagerie ne sont pas migrées.

## <a name="migration-workflow"></a>Flux de travail de migration

Il existe quatre phases pour migrer des stratégies DLP de Exchange la console de gestion DLP unifiée dans le Centre de conformité.  

1. Préparer la migration
    1. Évaluez et comparez vos stratégies Exchange Online DLP (EXO) et vos stratégies DLP du Centre de conformité pour les fonctionnalités en double.
    1. Décidez quelles stratégies EXO DLP vous souhaitez faire migrer exactement telles quelles, vous pouvez utiliser l’Assistant pour les migrer.
    1. Déterminez les stratégies EXO DLP que vous souhaitez consolider et consolider dans le Centre d’administration Exchange, puis utilisez l’Assistant migration pour les faire migrer dans le Centre de conformité.
1. Effectuer la migration : utiliser l’Assistant
1. Test et validation : examiner les résultats
1. Activer les stratégies migrées

## <a name="before-you-begin"></a>Avant de commencer

### <a name="licensing-and-versions"></a>Licences et versions

Avant de commencer la migration des stratégies DLP, vous devez confirmer votre abonnement [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et les modules. 

Pour accéder à l’Assistant Migration de stratégie et l’utiliser, vous devez avoir l’un de ces abonnements ou modules.

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 Conformité
- Microsoft 365 A5 Conformité
- Microsoft 365 E5, Protection des informations et gouvernance
- Microsoft 365 A5, Protection des informations et gouvernance

Pour obtenir une liste détaillée des exigences en matière de licences DLP, voir Microsoft 365 [Licensing guidance for security & compliance, data loss prevention](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)


### <a name="permissions"></a>Autorisations

Le compte que vous utilisez pour exécuter l’Assistant Migration doit avoir accès à la page DLP de la console d’administration Exchange et à la console DLP unifiée dans le Centre de conformité.

## <a name="prepare-for-migration"></a>Préparer la migration

1. Si vous ne connaissez pas la DLP, la console DLP du Centre de conformité ou la console DLP du centre d’administration Exchange, vous devez vous familiariser avant de tenter une migration de stratégie.
    1. [Exchange Online protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [Créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md)
1. Évaluez vos stratégies Exchange DLP et du Centre de conformité en vous posez les questions suivantes :


|Question  |Action  | Procédure de migration|
|---------|---------|---------|
|La stratégie est-elle toujours nécessaire ?    |Si ce n’est pas le cas, supprimez-le ou désactivez-le. |ne pas migrer|
|Se superpose-t-il à d’Exchange stratégies DLP du centre de conformité ou de conformité ?     |Si oui, pouvez-vous consolider les stratégies qui se chevauchent ?         |- Si elle chevauche une autre stratégie Exchange, créez manuellement la stratégie DLP consolidée dans le Centre d’administration Exchange, puis utilisez l’Assistant migration. </br> - Si elle chevauche une stratégie du Centre de conformité existante, vous pouvez modifier la stratégie du Centre de conformité existante pour qu’elle corresponde, ne migrez pas la version Exchange version|
|La stratégie Exchange DLP est-elle étroitement délimitée et a-t-elle des conditions, des actions, des inclusions et des exclusions bien définies ?     |Si oui, il s’agit d’un bon candidat pour migrer avec l’Assistant, notez la stratégie afin que vous n’oubliez pas de revenir pour la supprimer ultérieurement.         | migrer avec l’Assistant|

## <a name="migration"></a>Migration

Une fois que vous avez évalué toutes vos stratégies DLP Exchange et du centre de conformité pour les besoins et la compatibilité, vous pouvez utiliser l’Assistant migration.

1. Ouvrez la console [DLP Microsoft 365 conformité.](https://compliance.microsoft.com/datalossprevention?viewid=policies)
2. Si des stratégies Exchange DLP peuvent être migrées, une bannière s’affiche en haut de la page pour vous en faire savoir plus.
3. Sélectionnez **Migrer des stratégies** dans la bannière pour ouvrir l’Assistant Migration. Toutes les stratégies Exchange DLP sont répertoriées. Les stratégies précédemment migrées ne peuvent pas être sélectionnées.
4. Sélectionnez les stratégies que vous souhaitez migrer. Vous pouvez les migrer individuellement ou en groupes à l’aide d’une approche par phases ou en une seule fois. Sélectionnez **Suivant**.
5. Examinez le volet volant pour obtenir des avertissements ou des messages. Résolvez les problèmes avant de poursuivre.
6. Sélectionnez le mode dans qui vous souhaitez créer la nouvelle stratégie du Centre de conformité, **Active,** **Test** ou **Désactivé.**  La valeur par défaut **est Test**. Sélectionnez **Suivant**.
7. Si vous le souhaitez, vous pouvez créer des stratégies supplémentaires basées sur les stratégies Exchange DLP pour d’autres emplacements DLP unifiés. Cela entraîne la génération d’une nouvelle stratégie DLP unifiée pour la stratégie Exchange migrée et d’une nouvelle stratégie DLP unifiée pour tous les emplacements supplémentaires que vous sélectionnez ici.

> [!IMPORTANT]
> Toutes les conditions et actions de stratégie DLP Exchange qui ne sont pas prises en charge par d’autres emplacements DLP, tels que périphériques, SharePoint, OneDrive, locaux, MCAS ou les messages de conversation et de canal Teams seront supprimés de la stratégie supplémentaire. En outre, des travaux préalables doivent être effectués pour les autres emplacements. Voir :
>- [Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
>- [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
>- [Utilisation de la prévention des pertes de données sur les points de terminaison](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
>- [En savoir plus sur le scanner local de prévention des pertes de données Microsoft 365](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Prise en main du scanneur local de protection contre la perte de données(préversion)](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
>- [Utiliser le scanner local de prévention des pertes de données Microsoft 365 ](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)
 
8. Examinez les paramètres de session de l’Assistant Migration. Sélectionnez **Suivant**.
9. Examinez le rapport de migration. Prêtez attention aux défaillances impliquant Exchange règles de flux de messagerie. Vous pouvez les résoudre et migrer à partir de là les stratégies associées.

Les stratégies migrées apparaissent désormais dans la liste des stratégies DLP dans la console DLP du centre de conformité. 

## <a name="common-errors-and-mitigation"></a>Erreurs courantes et atténuation
|Message d’erreur  |Reason  | Atténuation/Étapes recommandées|
|---------|---------|---------|
|Une stratégie de conformité avec un nom `<Name of the policy>` existe déjà dans les scénarios. `Dlp`    |Il est probable que cette migration de stratégie a été effectuée précédemment, puis réattribuée dans la même session. |Actualisez la session pour mettre à jour la liste des stratégies disponibles pour la migration. Toutes les stratégies précédemment migrées doivent être à `Already migrated` l’état.|
|Une stratégie de conformité avec un nom `<Name of the policy>` existe déjà dans les scénarios. `Hold`     |Une stratégie de rétention du même nom existe dans le même client.       |- Renommer la stratégie DLP dans le EAC sous un autre nom. </br> - Réessayez la migration pour la stratégie impactée. |
|`DLP-group@contoso.com` ne peut pas être utilisé comme valeur pour la condition Shared By, car il s’agit d’un groupe de distribution ou d’un groupe de sécurité à messagerie. Utilisez le prédicat Partagé par un membre pour détecter les activités des membres de certains groupes.     |Les règles de transport permettent d’utiliser des groupes dans la condition, mais `sender is` la DLP unifiée ne l’autorise pas.         | Mettez à jour la règle de transport pour supprimer toutes les adresses de messagerie de groupe de la condition et ajoutez le groupe `sender is` à la condition si `sender is a member of` nécessaire. Nouvelle tentative de migration pour la stratégie impactée|
|Le destinataire n’a pas pu `DLP-group@contoso.com` être trouvé. Si vous débutez, réessayez l’opération après un certain temps. Si vous avez supprimé ou expiré, réinitialisez-le avec des valeurs valides et réessayez.     |Il est probable que l’adresse de groupe utilisée dans `sender is a member of` ou la condition a expiré ou `recipient is a member of` n’est pas valide.         | - Supprimez/remplacez toutes les adresses de messagerie de groupe non valides dans la règle de transport Exchange centre d’administration. </br> - Réessayez la migration pour la stratégie impactée.|
|La valeur spécifiée dans `FromMemberOf` le prédicat doit être un groupe de sécurité à messagerie.     |Les règles de transport permettent d’utiliser des utilisateurs individuels dans la condition, mais `sender is a member of` la DLP unifiée ne l’autorise pas.         | - Mettez à jour la règle de transport pour supprimer toutes les adresses de messagerie des utilisateurs individuels de la condition et ajoutez les utilisateurs `sender is a member of` à la condition si `sender is` nécessaire. </br> - Réessayez la migration pour la stratégie impactée.|
|La valeur spécifiée dans `SentToMemberOf` le prédicat doit être un groupe de sécurité à messagerie.    |Les règles de transport permettent aux utilisateurs individuels d’être utilisés dans la condition, mais `recipient is a member of` la DLP unifiée ne l’autorise pas.         | - Mettez à jour la règle de transport pour supprimer toutes les adresses de messagerie des utilisateurs individuels de la condition et ajoutez les utilisateurs `recipient is a member of` à la condition si `recipient is` nécessaire. </br> - Réessayez la migration pour la stratégie impactée.|
|L’utilisation `<Name of condition>` du paramètre est prise en charge uniquement pour Exchange. Supprimez ce paramètre ou n’allumez que Exchange emplacement.         | Il est probable qu’une autre stratégie du même nom existe dans le Centre de conformité avec d’autres emplacements tels que SPO/ODB/Teams pour lesquels la condition mentionnée n’est pas prise en charge. | Renommez la stratégie DLP dans Exchange centre d’administration et réessayez la migration.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test et validation <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Testez et examinez vos stratégies.

1. Suivez les [procédures de stratégie Test d’une stratégie DLP.](create-test-tune-dlp-policy.md#test-a-dlp-policy)
2. Examinez les événements créés par la stratégie dans [l’Explorateur d’activités.](data-classification-activity-explorer.md)

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Passer en revue les correspondances de stratégie entre Exchange DLP du Centre d’administration Microsoft 365 la DLP unifiée

Pour vous assurer que les stratégies migrées se comportent comme prévu, vous pouvez exporter les rapports à partir des deux centres d’administration et comparer les correspondances de stratégie.

1. Connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Exporter le [rapport DLP du EAC.](/powershell/module/exchange/get-maildetaildlppolicyreport?view=exchange-ps) Vous pouvez copier cette cmdlet et insérer les valeurs appropriées :

```powershell
Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv"> 
```
3. Exportez [le rapport DLP unifié.](/powershell/module/exchange/get-dlpdetailreport?view=exchange-ps) Vous pouvez copier cette cmdlet et insérer les valeurs appropriées :

```powershell
Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">  
```

## <a name="activate-your-migrated-policies"></a>Activer vos stratégies migrées

Une fois que vous êtes satisfait du fonctionnement de vos stratégies migrées, vous pouvez les définir sur **Appliquer**.

1. Ouvrez la console Exchange DLP du centre d’administration.
2. Désactivez ou supprimez la stratégie source.
3. Ouvrez la console [DLP Microsoft 365](https://compliance.microsoft.com/datalossprevention?viewid=policies) conformité et sélectionnez la stratégie que vous souhaitez rendre active pour la modifier.
4. Modifiez l’état **sur Activer.**

## <a name="related-articles"></a>Articles connexes

- [Exchange Online protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
- [Exchange Online protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
