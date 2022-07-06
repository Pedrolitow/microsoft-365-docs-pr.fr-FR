---
title: Migrer Exchange Online stratégies DLP vers le Centre de conformité
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
description: Découvrez comment planifier et migrer vos stratégies de protection contre la perte de données en ligne Exchange vers DLP.
ms.openlocfilehash: 371dfafbbf6acf31587b0786a5b5594fb83571d9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638276"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-microsoft-purview-compliance-portal"></a>Migrer Exchange Online stratégies de protection contre la perte de données vers portail de conformité Microsoft Purview

[Exchange Online stratégies de protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) sont dépréciées. [Des fonctionnalités DLP beaucoup plus riches](dlp-learn-about-dlp.md), notamment Exchange Online DLP, sont proposées dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies). Vous pouvez utiliser l’Assistant Migration de stratégie DLP pour vous aider à transmettre vos stratégies DLP Exchange Online au Centre de conformité où vous les gérerez.

L’Assistant Migration fonctionne en lisant la configuration de vos stratégies DLP dans Exchange, puis en créant des stratégies en double dans le Centre de conformité. Par défaut, l’Assistant crée les nouvelles versions des stratégies en mode **Test** , afin que vous puissiez voir l’impact qu’elles auraient dans votre environnement sans appliquer l’une des actions. Une fois que vous êtes prêt à effectuer une transition complète vers les versions du Centre de conformité, **_vous devez_** :

1. Désactivez ou supprimez la stratégie source dans le Centre de Administration Exchange (EAC).
1. Modifiez la version du Centre de conformité de la stratégie et **remplacez** son état par Test par **Appliquer**.

> [!WARNING]
> Si vous ne supprimez pas ou ne désactivez pas la stratégie source dans le CAE avant de définir la version du Centre de conformité pour **Appliquer** les deux ensembles de stratégies, vous tentez d’appliquer des actions et vous recevrez des événements en double. **_Il s’agit d’une configuration non prise en charge._**

L’Assistant Migration migre uniquement les stratégies EXO et les règles de flux de messagerie associées. Les règles de flux de messagerie Exchange autonomes ne sont pas migrées.

## <a name="migration-workflow"></a>Flux de travail de migration

Il existe quatre phases pour migrer des stratégies DLP d’Exchange vers la console de gestion DLP unifiée dans le Centre de conformité.

1. Préparer la migration
    1. Évaluez et comparez vos stratégies DLP Exchange Online (EXO) et vos stratégies DLP du Centre de conformité pour les fonctionnalités en double.
    1. Déterminez les stratégies EXO DLP que vous souhaitez apporter exactement telles quelles. Vous pouvez utiliser l’Assistant pour les migrer.
    1. Déterminez les stratégies EXO DLP que vous souhaitez consolider et consolider dans le centre d’administration Exchange, puis utilisez l’Assistant Migration pour les placer dans le Centre de conformité.
1. Effectuer la migration - Utiliser l’Assistant
1. Test et validation - Examiner les résultats
1. Activer les stratégies migrées

## <a name="before-you-begin"></a>Avant de commencer

### <a name="licensing-and-versions"></a>Licences et versions

Avant de commencer à migrer des stratégies DLP, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) et tous les modules complémentaires.

Pour accéder à l’Assistant Migration de stratégie et l’utiliser, vous devez disposer de l’un de ces abonnements ou modules complémentaires

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 Conformité
- Microsoft 365 A5 Conformité
- Microsoft 365 E5, Protection des informations et gouvernance
- Microsoft 365 A5, Protection des informations et gouvernance

Pour obtenir une liste détaillée des exigences en matière de licences DLP, consultez [l’aide relative aux licences Microsoft 365 pour la sécurité & la conformité, la protection contre la perte de données](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>Autorisations

Le compte que vous utilisez pour exécuter l’Assistant Migration doit avoir accès à la page Exchange Administration Console DLP et à la console Unified DLP dans le Centre de conformité.

## <a name="prepare-for-migration"></a>Préparer la migration

1. Si vous n’êtes pas familiarisé avec DLP, la console DLP du Centre de conformité ou la console DLP exchange Administration centre, vous devez vous familiariser avant de tenter une migration de stratégie.
    1. [Exchange Online stratégies de protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
    1. [Créer, tester et paramétrer une stratégie DLP](create-test-tune-dlp-policy.md)
1. Évaluez vos stratégies exchange DLP et centre de conformité en posant les questions suivantes :

|Question|Action|Procédure de migration|
|---|---|---|
|La stratégie est-elle toujours nécessaire ?|Si ce n’est pas le cas, supprimez ou désactivez-le|ne pas migrer|
|Se chevauche-t-il avec d’autres stratégies DLP exchange ou de centre de conformité ?|Si oui, pouvez-vous consolider les stratégies qui se chevauchent ?|- Si elle chevauche une autre stratégie Exchange, créez manuellement la stratégie DLP consolidée dans le centre de Administration Exchange, puis utilisez l’Assistant migration. </br> - S’il chevauche une stratégie de Centre de conformité existante, vous pouvez modifier la stratégie du Centre de conformité existante pour qu’elle corresponde, ne pas migrer la version d’Exchange|
|La stratégie Exchange DLP est-elle étroitement délimitée et dispose-t-elle de conditions, d’actions, d’inclusions et d’exclusions bien définies ?|Si oui, c’est un bon candidat pour migrer avec l’Assistant, prenez note de la stratégie afin de vous rappeler de revenir pour la supprimer ultérieurement|migrer avec l’Assistant|

## <a name="migration"></a>Migration

Une fois que vous avez évalué toutes vos stratégies DLP exchange et de conformité pour les besoins et la compatibilité, vous pouvez utiliser l’Assistant Migration.

1. Ouvrez la [console DLP portail de conformité Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies).
2. S’il existe des stratégies Exchange DLP qui peuvent être migrées, une bannière s’affiche en haut de la page pour vous informer.
3. Choisissez **Les stratégies de migration** dans la bannière pour ouvrir l’Assistant Migration. Toutes les stratégies DLP Exchange sont répertoriées. Les stratégies précédemment migrées ne peuvent pas être sélectionnées.
4. Sélectionnez les stratégies que vous souhaitez migrer. Vous pouvez les migrer individuellement ou en groupes à l’aide d’une approche par phases ou tout à la fois. Sélectionnez **Suivant**.
5. Examinez le volet volant pour obtenir des avertissements ou des messages. Résolvez les problèmes avant de continuer.
6. Sélectionnez le mode dans lequel vous souhaitez que la nouvelle stratégie du Centre de conformité soit créée, **Active**, **Test** ou **Désactivée**.  La valeur par défaut est **Test**. Sélectionnez **Suivant**.
7. Si vous le souhaitez, vous pouvez créer d’autres stratégies basées sur les stratégies DLP Exchange pour d’autres emplacements DLP unifiés. Cela entraîne une nouvelle stratégie DLP unifiée pour la stratégie Exchange migérée et une nouvelle stratégie DLP unifiée pour tous les autres emplacements que vous choisissez ici.

> [!IMPORTANT]
> Toutes les conditions et actions de stratégie Exchange DLP qui ne sont pas prises en charge par d’autres emplacements DLP, tels que les appareils, SharePoint, OneDrive, local, MCAS ou Les messages de conversation et de canal Teams seront supprimés de la stratégie supplémentaire. En outre, il existe des travaux préalables qui doivent être effectués pour les autres emplacements. Voir :
>- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
>- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
>- [Utilisation des points de terminaison protection contre la perte de données](endpoint-dlp-using.md)
>- [En savoir plus sur le scanneur local de protection contre la perte de données](dlp-on-premises-scanner-learn.md)
>- [Prise en main du scanneur local de protection contre la perte de données(préversion)](dlp-on-premises-scanner-get-started.md)
>- [Utiliser le scanneur local de protection contre la perte de données Microsoft Purview](dlp-on-premises-scanner-use.md)
>- [Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md)
 
8. Passez en revue les paramètres de session de l’Assistant Migration. Sélectionnez **Suivant**.
9. Passez en revue le rapport de migration. Soyez attentif aux défaillances impliquant des règles de flux de messagerie Exchange. Vous pouvez les corriger et remigrater les stratégies associées.

Les stratégies migrées apparaissent désormais dans la liste des stratégies DLP dans la console DLP du Centre de conformité.

## <a name="common-errors-and-mitigation"></a>Erreurs courantes et atténuation

|Message d’erreur|Reason|Atténuation/Étapes recommandées|
|---|---|---|
|Une stratégie de conformité portant un nom `<Name of the policy>` existe déjà dans les scénarios `Dlp`.|Il est probable que cette migration de stratégie ait été effectuée plus tôt, puis retenté dans la même session|Actualisez la session pour mettre à jour la liste des stratégies disponibles pour la migration. Toutes les stratégies précédemment migrées doivent être dans l’état `Already migrated` .|
|Une stratégie de conformité portant un nom `<Name of the policy>` existe déjà dans les scénarios `Hold`.|Une stratégie de rétention portant le même nom existe dans le même locataire.|- Renommez la stratégie DLP dans EAC sous un autre nom. </br> - Réessayez la migration pour la stratégie impactée.|
|`DLP-group@contoso.com` ne peut pas être utilisé comme valeur pour la condition Shared By, car il s’agit d’un groupe de distribution ou d’un groupe de sécurité à extension messagerie. Utilisez Shared by Member of predicate pour détecter les activités par les membres de certains groupes.|Les règles de transport permettent d’utiliser des groupes dans la `sender is` condition, mais la DLP unifiée ne l’autorise pas.|Mettez à jour la règle de transport pour supprimer toutes les adresses e-mail de groupe de la `sender is` condition et ajoutez le groupe à la `sender is a member of` condition si nécessaire. Réessayer la migration pour la stratégie impactée|
|Destinataire introuvable `DLP-group@contoso.com`. Si vous venez de créer, réessayez l’opération après un certain temps. En cas de suppression ou d’expiration, réinitialisez avec des valeurs valides, puis réessayez.|Il est probable que l’adresse de groupe utilisée dans ou `recipient is a member of` la `sender is a member of` condition est expirée ou non valide.|- Supprimez/remplacez toutes les adresses e-mail de groupe non valides dans la règle de transport dans le Centre d’administration Exchange. </br> - Réessayez la migration pour la stratégie impactée.|
|La valeur spécifiée dans le `FromMemberOf` prédicat doit être un groupe de sécurité à extension messagerie.|Les règles de transport permettent d’utiliser des utilisateurs individuels dans la condition, mais la `sender is a member of` protection contre la perte de données unifiée ne l’autorise pas.|- Mettez à jour la règle de transport pour supprimer toutes les adresses e-mail utilisateur individuelles de la `sender is a member of` condition et ajouter les utilisateurs à la `sender is` condition si nécessaire. </br> - Réessayez la migration pour la stratégie impactée.|
|La valeur spécifiée dans le `SentToMemberOf` prédicat doit être un groupe de sécurité à extension messagerie.|Les règles de transport permettent d’utiliser des utilisateurs individuels dans la condition, mais la `recipient is a member of` protection contre la perte de données unifiée ne l’autorise pas.|- Mettez à jour la règle de transport pour supprimer toutes les adresses e-mail utilisateur individuelles de la `recipient is a member of` condition et ajouter les utilisateurs à la `recipient is` condition si nécessaire. </br> - Réessayez la migration pour la stratégie impactée.|
|L’utilisation du `<Name of condition>` paramètre est prise en charge uniquement pour Exchange. Supprimez ce paramètre ou activez uniquement l’emplacement Exchange.|Il est probable qu’une autre stratégie portant le même nom existe dans le Centre de conformité avec d’autres emplacements tels que SPO/ODB/Teams pour lesquels la condition mentionnée n’est pas prise en charge.|Renommez la stratégie DLP dans le Centre d’administration Exchange et réessayez la migration.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test et validation <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Testez et passez en revue vos stratégies.

1. Suivez les procédures [de stratégie Test a DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Passez en revue les événements créés par la stratégie dans [l’Explorateur d’activités](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-purview-unified-dlp"></a>Passer en revue les correspondances de stratégie entre Exchange Administration Center DLP et Microsoft Purview Unified DLP

Pour vous assurer que les stratégies migrées se comportent comme prévu, vous pouvez exporter les rapports à partir des deux centres d’administration et effectuer une comparaison des correspondances de stratégie.

1. Connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Exportez le [rapport EAC DLP](/powershell/module/exchange/get-maildetaildlppolicyreport). Vous pouvez copier cette applet de commande et insérer les valeurs appropriées :

   ```powershell
   Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

3. Exportez le [rapport DLP unifié](/powershell/module/exchange/get-dlpdetailreport). Vous pouvez copier cette applet de commande et insérer les valeurs appropriées :

   ```powershell
   Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

## <a name="activate-your-migrated-policies"></a>Activer vos stratégies migrées

Une fois que vous êtes satisfait du fonctionnement de vos stratégies migrées, vous pouvez les définir sur **Appliquer**.

1. Ouvrez la console DLP exchange Administration Center.
2. Désactivez ou supprimez la stratégie source.
3. Ouvrez la [console DLP portail de conformité Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies) et sélectionnez la stratégie que vous souhaitez activer pour la modifier.
4. Modifiez l’état pour **activer**.

## <a name="related-articles"></a>Articles connexes

- [Exchange Online stratégies de protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Créer, tester et paramétrer une stratégie DLP](create-test-tune-dlp-policy.md)
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
- [Exchange Online stratégies de protection contre la perte de données (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
