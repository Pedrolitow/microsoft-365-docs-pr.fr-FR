---
title: Audit avancé de Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: L’audit avancé de Microsoft 365 offre de nouvelles fonctionnalités d’audit pour aider votre organisation à effectuer des enquêtes de conformité et de légalité.
ms.openlocfilehash: 6fb42e9df35fe025c5c5f292238217aebb4098c7
ms.sourcegitcommit: 7ff75a0f45371b247d975fc61cfa286f5b6f42f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "44141042"
---
# <a name="advanced-audit-in-microsoft-365"></a>Audit avancé de Microsoft 365

La [fonctionnalité d'audit unifiée](search-the-audit-log-in-security-and-compliance.md) de Microsoft 365 offre aux organisations une visibilité dans de nombreux types d’activités auditées dans différents services de Microsoft 365. Avec la publication de l’audit avancé de Microsoft 365, nous offrons de nouvelles fonctionnalités d’audit pouvant aider votre organisation à effectuer des enquêtes de conformité et de légalité.

> [!NOTE]
> Advanced audit est à la disposition des organisations disposant d’un abonnement Office 365 E5 ou Microsoft 365 Entreprise E5. De plus, une licence pour le composant Microsoft 365 E5 Conformité peut être attribué aux utilisateurs lorsqu'une licence par utilisateur est requise pour des fonctionnalités d’audit avancées, comme dans le cas de la conservation à long terme de journaux d’audit et d'un accès à des évènements essentiels lors d'enquêtes.

Cet article offre une vue d’ensemble de ces fonctionnalités d'audit avancées.

## <a name="long-term-retention-of-audit-logs"></a>Conservation à long terme des journaux d’audit

L’audit avancé conserve tous les enregistrements d’audit Exchange, SharePoint et Azure Active Directory pendant une durée d'un an. Ceci est réalisé par une stratégie de rétention du journal d’audit par défaut qui conserve tout enregistrement d’audit contenant la valeur **Exchange**, **SharePoint**ou **AzureActiveDirectory** pour la propriété **Charge de travail** (indiquant le service dans lequel l’activité s’est produite) pendant un an. Cela peut vous aider lors d'enquêtes en cours portant sur la conformité ou la légalité. Pour plus d’informations, voir la section « Stratégie de rétention du journal d’audit par défaut » dans [Gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md#default-audit-log-retention-policy).

## <a name="audit-log-retention-policies"></a>Stratégies de rétention du journal d'audit

Tous les enregistrements d’audit générés dans d’autres services qui ne sont pas couverts par la stratégie de rétention par défaut du journal d’audit (décrits dans la section précédente) sont conservés pendant une durée de 90 jours. Toutefois, vous pouvez désormais créer des stratégies de rétention de journal d’audit personnalisées pour conserver d'autres enregistrements d’audit pendant un an. Vous pouvez créer une stratégie pour conserver les enregistrements d’audit basés sur un ou plusieurs critères énumérés ci-après :

- Service Microsoft 365 dans lequel les activités d’audit se produisent

- Activités auditées spécifiques

- Utilisateur effectuant l'activité auditée

Vous pouvez également spécifier la durée de conservation des enregistrements d’audit qui correspondent à une stratégie et à un niveau de priorité pour que les stratégies spécifiques soient prioritaires sur les autres stratégies. Veuillez noter également que toute stratégie de rétention de journal d’audit personnalisée sera prioritaire sur la stratégie de rétention d’audit par défaut si vous devez conserver des enregistrements d’audit Exchange, SharePoint ou Azure Active Directory pendant au moins un an pour tout ou partie des utilisateurs de votre organisation. Pour plus d’informations, voir [Gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

## <a name="access-to-crucial-events-for-investigations"></a>Accès aux événements essentiels lors d'enquêtes

Les événements essentiels d’audit relatifs à la sécurité et à la conformité sont ceux pouvant vous aider à enquêter sur des violations éventuelles ou d'autres enquêtes légales. Le premier événement essentiel qui est publié est l’action d’audit de la boîte aux lettres *MailItemsAccessed*. Cette action se déclenche quand les données des e-mails sont consultées par les protocoles et les clients de messagerie. L’action MailItemsAccessed peut aider les enquêteurs à identifier les violations de données et à mesurer l’étendue des messages susceptibles d’être compromis. Si une personne malveillante a accès aux e-mails, l’action MailItemsAccessed se déclenche même s’il n’y a pas de signal explicite indiquant qu'un message a été réellement lu (en d’autres termes, le type d’accès comme BIND ou synchrone, par exemple, est sauvegardé dans l’enregistrement d’audit).

La nouvelle action MailItemsAccessed de la boîte aux lettres remplace MessageBind dans la journalisation d’audit des boîtes aux lettres dans Exchange Online et offre les améliorations suivantes :

- MessageBind était seulement configurable pour une ouverture de session utilisateur de type AuditAdmin et ne s’appliquait pas aux actions de propriétaires ou de délégués. MailItemsAccessed s’applique à tout type d’ouverture de session.

- MessageBind ne prenait en charge que l'accès à un client de messagerie. Il ne s’appliquait pas aux activités synchrones. Les événements MailItemsAccessed sont déclenchés par les types d’accès BIND et synchrone.

- Les actions MessageBind déclencheraient la création de plusieurs enregistrements d’audit lors de l’accès au même e-mail, ce qui entraînerait un audit « retentissant ». En revanche, les événements MailItemsAccessed sont regroupés dans un nombre réduit d’enregistrements d’audit.

Si vous souhaitez en savoir plus sur les enregistrements d’audit pour les activités MailItemsAccessed, consultez [Utiliser l’audit avancé pour enquêter sur les comptes compromis](mailitemsaccessed-forensics-investigations.md).

### <a name="search-for-mailitemsaccessed-audit-records"></a>Rechercher des enregistrements d’audit MailItemsAccessed

Pour rechercher des enregistrements d’audit MailItemsAccessed, vous pouvez rechercher les activités des **éléments de la boîte aux lettres consultés** dans la liste déroulante des **activités de la boîte aux lettres Exchange** dans l’[outil de recherche du journal d’audit](search-the-audit-log-in-security-and-compliance.md) dans le centre de sécurité et conformité.

![Recherche d’actions MailItemsAccessed dans l’outil de recherche du journal d’audit](../media/MailItemsAccessedSCC1.png)

Vous pouvez également exécuter la commande [Search-UnifiedAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) ou [Search-MailboxAuditLog -Operations MailItemsAccessed](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-mailboxauditlog) dans Exchange Online PowerShell.

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Accès haut débit à l’API Activité de gestion Office 365

Les organisations ayant accès à des journaux d’audit via l’API Activité de gestion Office 365 étaient restreintes par des seuils de limitation au niveau de l’éditeur. Cela signifie que pour un éditeur faisant une extraction de données pour le compte de plusieurs clients, la limite était partagée par tous les clients.

Grâce à la publication de l'audit avancé, nous allons passer d’une limite au niveau éditeur à une limite au niveau du client. Chaque organisation obtient ainsi son propre quota de bande passante entièrement allouée pour accéder à ses données d’audit. La bande passante n'est pas une limite statique prédéfinie. Elle est modelée sur une combinaison de facteurs, tels que le nombre de sièges au sein de l’organisation, et les organisations E5 obtiennent une bande passante plus importante que les organisations non E5.

Les organisations reçoivent une ligne de base de 2 000 demandes par minute. Cette limite augmentera de façon dynamique en fonction du nombre de sièges d’une organisation et du nombre de licences dans son abonnement. Les organisations E5 disposeront d’environ deux fois plus de bande passante que les autres organisations. La bande passante aura également un plafond maximal pour protéger l’état d’intégrité du service.

Pour plus d’informations, consultez la rubrique « Limitation de l'API » dans la [Référence de l’API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-advanced-audit"></a>FAQ pour l’audit avancé

**Où puis-je accéder à l’audit avancé ?**

Une fois l’audit avancé déployé dans votre organisation, vous pouvez créer des stratégies de rétention de journal d’audit et rechercher des enregistrements d’audit MailItemsAccessed à l’aide de l’outil de recherche du journal d’audit dans le [Centre de sécurité & conformité](https://protection.office.com). Nous faisons le nécessaire pour déployer l’audit avancé dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com) dans les prochaines semaines.

**Est-ce que chaque utilisateur a besoin d'une licence E5 pour bénéficier de l'Audit avancé ?**

Pour bénéficier des fonctionnalités d’audit avancées de niveau utilisateur, ce dernier doit se voir attribuer une licence E5. Certaines fonctionnalités vous permettront de vérifier la présence de la licence appropriée pour exposer la fonctionnalité à l’utilisateur. Par exemple, si vous essayez de conserver les enregistrements d’audit pour un utilisateur ne disposant pas d’une licence E5 pendant plus de 90 jours, le système renvoie un message d’erreur.

**Pourquoi je ne vois pas l’audit avancé dans mon organisation, même si nous avons un abonnement E5 et des utilisateurs auxquels des licences E5 ont été attribuées ?**

Il est possible que les fonctionnalités d’audit avancées (telles que la possibilité de créer des stratégies de rétention de journal d’audit et la journalisation des enregistrements d’audit MailItemsAccessed) ne soient pas disponibles dans votre organisation, même si les licences appropriées sont en place. Si cela vous arrive, c'est parce que le package d'audit avancé n'a pas encore été déployé dans votre organisation. Il s'agit d'un problème de remplacement temporaire de licence, qui devrait être résolu sous peu pour les organisations concernées . Pour résoudre ce problème, procédez comme suit pour chaque utilisateur E5 :

1. Dans le Centre d’administration Microsoft 365, accédez à **Utilisateurs > Utilisateurs actifs** et ensuite, sélectionnez l’utilisateur.

2. Dans la page déroulante des propriétés de l’utilisateur, cliquez sur **licences et applications**.

3. Développez la section **applications**, puis effectuez l’une des opérations suivantes :

   a. Si la case à cocher **audit avancé Microsoft 365** n’est pas activée, sélectionnez-la, puis cliquez sur **enregistrer les modifications.** Les enregistrements d’audit pour les actions MailItemsAccessed pour cet utilisateur devraient pouvoir être recherchés dans les 24 heures.

   b. Si la case**audit avancé Microsoft 365** est cochée, désactivez-la, puis cliquez sur **enregistrer les modifications.** Voir l’étape 4

4. Si vous avez désactivé la case à cocher à l’étape 3, patientez 60 minutes, puis répétez l’étape 3a pour activer l’application d’audit avancé Microsoft 365.

Pour les organisations qui attribuent des licences à des groupes d’utilisateurs à l’aide d’une gestion de licences basée sur les groupes, vous devez désactiver l’attribution des licences pour Microsoft 365 audit avancé pour le groupe. Une fois que vous avez enregistré vos modifications, vérifiez que l’audit avancé Microsoft 365 est désactivé pour le groupe. Réactivez ensuite l’attribution des licences pour le groupe. Pour obtenir des instructions sur la gestion des licences basée sur les groupes, voir [Attribuer des licences aux utilisateurs par appartenance aux groupes dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-groups-assign).

**Que se passe-t-il si mon organisation était en version d’évaluation privée pour une période de conservation d’un an des enregistrements d’audit ?**

Les stratégies de rétention d’audit du programme d’évaluation sont conservées tant que vous ne les remplacez pas et ne les modifiez pas avec les stratégies de rétention personnalisées.

**Que se passe-t-il si mon organisation souhaite conserver les journaux d’audit pendant plus d’un an ?**

Nous explorons les options pour trouver comment, et si, nous pouvons proposer des périodes de rétention plus longues pour les enregistrements d’audit. Vous pouvez faire des commentaires sur la rétention plus longue des enregistrements d’audit auprès de [Office 365 User Voice](https://office365.uservoice.com/forums/289138-office-365-security-compliance?category_id=137187).

**Mon organisation dispose d'un abonnement E5. Dois-je faire quelque chose pour accéder aux enregistrements d'audit des événements MailItemsAccessed?**

Pour les clients éligibles, il n'y a aucune action requise pour accéder aux événements MailItemsAccessed. Cependant, comme expliqué précédemment dans cette rubrique, la latence provoquée par le problème de renvoi de licence peut empêcher les enregistrements d'audit pour l'événement MailItemsAccessed d'être renvoyés dans une recherche dans le journal d'audit. Dans ce cas, suivez les instructions de la section Rechercher des enregistrements d’audit MailItemsAccessed.

**Envisagez-vous de publier d’autres événements cette année ?**

Oui, nous envisageons de publier de nouveaux événements essentiels pour les investigations dans les mois à venir. Nous publierons des informations sur ces nouveaux événements dans la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) à mesure que nous approcherons de la date de sortie.

**Les nouveaux événements dans l’audit avancé sont-ils disponibles dans l’API Activité de gestion Office 365 ?**

Oui. Tant que les enregistrements d’audit sont générés pour les utilisateurs disposant de la licence appropriée, vous pourrez accéder à ces enregistrements via l’API Activité de gestion Office 365.

**Une bande passante élevée est-elle synonyme d’une meilleure latence ou d’un SLA supérieur ?**

Pour le moment, lune bande passante élevée offre un meilleur pipeline, en particulier pour les organisations présentant un grand nombre de signaux d’audit et de modèles de consommation significatifs. Cela peut entraîner une meilleure latence. Cependant, il n’y a pas de SLA associé à une bande passante élevée. Les latences standard sont documentées et ne changent pas avec la version d’audit avancée.
