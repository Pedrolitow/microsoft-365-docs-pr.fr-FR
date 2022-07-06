---
title: Informations de référence sur la protection contre la perte de données
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
feedback_system: None
description: documentation de référence sur la protection contre la perte de données
ms.openlocfilehash: 5a52d79a073a9735d5c32ce3a9646ccacf1a0dcb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636466"
---
# <a name="data-loss-prevention-reference"></a>Informations de référence sur la protection contre la perte de données

> [!IMPORTANT]
> Il s’agit d’une rubrique de référence qui n’est plus la ressource principale pour les informations Protection contre la perte de données Microsoft Purview (DLP). Le jeu de contenu DLP est mis à jour et restructuré. Les rubriques traitées dans cet article passeront aux articles nouveaux et mis à jour. Pour plus d’informations sur la protection contre la perte de données, consultez [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> Des fonctionnalités de protection contre la perte de données ont récemment été ajoutées aux messages de discussion et de canal Microsoft Teams pour les utilisateurs titulaires d’une licence de Conformité avancée Office 365, disponible sous la forme d’une option autonome et incluse dans Office 365 E5 et Microsoft 365 E5 Conformité. Pour en savoir plus sur les conditions d’octroi de licences, consultez [Conseils sur la gestion des licences des services de niveau client de Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Microsoft Purview compliance portal, you can identify, monitor, and automatically protect sensitive information across Office 365.

With a DLP policy, you can:

- **Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.**

    For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.

- **Prevent the accidental sharing of sensitive information**.

    For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.

- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.**

    Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.

- **Help users learn how to stay compliant without interrupting their workflow.**

    You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.

- **View DLP alerts and reports showing content that matches your organization’s DLP policies.**

    To view alerts and metadata related to your DLP policies you can use the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md). You can also view policy match reports to assess how your organization is complying with a DLP policy. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported

-->
## <a name="create-and-manage-dlp-policies"></a>Créer et gérer des stratégies DLP

Vous créez et gérez des stratégies DLP sur la page de protection contre la perte de données du portail de conformité Microsoft Purview.

![Page de protection contre la perte de données dans le portail de conformité Microsoft Purview](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

<!-- MOVED TO LEARN ABOUT ## What a DLP policy contains

A DLP policy contains a few basic things:

- Where to protect the content: **locations** such as Exchange Online, SharePoint Online, and OneDrive for Business sites, as well as Microsoft Teams chat and channel messages.

- When and how to protect the content by enforcing **rules** comprised of:

  - **Conditions** the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that's been shared with people outside your organization.

  - **Actions** that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all of the rules needed to comply with a specific regulation.

For example, you might have a DLP policy that helps you detect the presence of information subject to the Health Insurance Portability and Accountability Act (HIPAA). This DLP policy could help protect HIPAA data (the what) across all SharePoint Online sites and all OneDrive for Business sites (the where) by finding any document containing this sensitive information that's shared with people outside your organization (the conditions) and then blocking access to the document and sending a notification (the actions). These requirements are stored as individual rules and grouped together as a DLP policy to simplify management and reporting.

![Diagram shows that DLP policy contains locations and rules.](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png) -->

<!-- MOVED TO LEARN ABOUT ### Locations

DLP policies are applied to sensitive items across Microsoft 365 locations and can be further scoped as detailed in this table.


|Location | Include/exclude by|
|---------|---------|
|Exchange email| distribution groups|
|SharePoint sites |sites |
|OneDrive accounts |accounts |
|Teams chat and channel messages |accounts |
|Windows 10 devices |user or group |
|Microsoft Cloud App Security |instance |
 -->

<!-- moved to dlp-policy-reference.md
If you choose to include specific distribution groups in Exchange, the DLP policy will be scoped only to the members of that group. Similarly excluding a distribution group will exclude all the members of that distribution group from policy evaluation. You can choose to scope a policy to the members of distribution lists, dynamic distribution groups, and security groups. A DLP policy can contain no more than 50 such inclusions and exclusions.

If you choose to include or exclude specific SharePoint sites, a DLP policy can contain no more than 100 such inclusions and exclusions. Although this limit exists, you can exceed this limit by applying either an org-wide policy or a policy that applies to entire locations.

If you choose to include or exclude specific OneDrive accounts or groups, a DLP policy can contain no more than 100 user accounts or 50 groups as inclusion or exclusion.

### Rules

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. For each rule, when the conditions are met, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

Here are the components of a rule, each explained below.

![Sections of the DLP rule editor.](../media/1859d504-b9c2-45ed-961b-a0092251acc2.png)

#### Conditions

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.

Conditions focus on the **content**, such as what types of sensitive information you're looking for, and also on the **context**, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally might be lower risk and require fewer actions than sensitive content shared with people outside the organization.

![List showing available DLP conditions.](../media/0fa43f90-d007-4506-ae93-43e8424fe103.png)

The conditions now available can determine if:

- Content contains a type of sensitive information.

- Content contains a label. For more information, see the below section [Using a retention label as a condition in a DLP policy](#using-a-retention-label-as-a-condition-in-a-dlp-policy).

- Content is shared with people outside or inside your organization.

  > [!NOTE]
  > Users who have non-guest accounts in a host organization's Active Directory or Azure Active Directory tenant are considered as people inside the organization.

#### Types of sensitive information

A DLP policy can help protect sensitive information, which is defined as a **sensitive information type**. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.

![List of available sensitive information types.](../media/3eaa9911-bc94-44be-902f-363dbf3b07fe.png)

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't simply look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords.

- Internal functions to validate checksums or composition.

- Evaluation of regular expressions to find pattern matches.

- Other content examination.

This helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.

#### Actions

When content matches a condition in a rule, you can apply actions to automatically protect the content.

![List of available DLP actions.](../media/8aef17fc-1e99-4ac7-adfc-0f2c9c1a0697.png)

With the actions now available, you can:

- **Restrict access to the content** Depending on your need, you can restrict access to content in three ways:

  1. Restrict access to content for everyone.
  2. Restrict access to content for people outside the organization.
  3. Restrict access to "Anyone with the link."

  For site content, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. These people can remove the sensitive information from the document or take other remedial action. When the document is in compliance, the original permissions are automatically restored. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site.

  ![Policy tip showing access to document is blocked.](../media/b6cefed3-d212-43d7-8534-4b92b26ebd50.png)

  For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender sees an NDR or (if the rule uses a notification) a policy tip and/or email notification.

  ![Warning that unauthorized recipients must be removed from the message.](../media/302f9994-912d-41e7-861f-8a4539b3c285.png)

#### User notifications and user overrides

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.

![User notifications and user overrides sections of DLP rule editor.](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)

The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.

In addition to sending an email notification, a user notification displays a policy tip:

- In Outlook and Outlook on the web.

- For the document on a SharePoint Online or OneDrive for Business site.

- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.

Here's what a policy tip looks like in a OneDrive for Business account.

![Policy tip for a document in a OneDrive account.](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

#### Alerts and Incident reports

When a rule is matched, you can send an alert email to your compliance officer (or any person(s) you choose) with details of the alert. This alert email will carry a link of the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md) which the compliance officer can go to view the details of alert and events. The dashboard contains details of the event that triggered the alert along with details of the DLP policy matched and the sensitive content detected.

In addition, you can also send an incident report with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.

> [!div class="mx-imgBorder"]
> ![Page for configuring incident reports.](../media/Alerts-and-incident-report.png)

DLP scans email differently from items in SharePoint Online or OneDrive for Business. In SharePoint Online and OneDrive for Business, DLP scans existing items as well as new ones and generates an alert and incident report whenever a match is found. In Exchange Online, DLP only scans new email messages and generates a report if there is a policy match. DLP ***does not*** scan or match previously existing email items that are stored in a mailbox or archive.

## Grouping and logical operators

Often your DLP policy has a straightforward requirement, such as to identify all content that contains a U.S. Social Security Number. However, in other scenarios, your DLP policy might need to identify more loosely defined data.

For example, to identify content subject to the U.S. Health Insurance Act (HIPAA), you need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

    AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from very large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

You can easily identify such loosely defined data by using grouping and logical operators (AND, OR). When you create a DLP policy, you can:

- Group sensitive information types.

- Choose the logical operator between the sensitive information types within a group and between the groups themselves.

### Choosing the operator within a group

Within a group, you can choose whether any or all of the conditions in that group must be satisfied for the content to match the rule.

![Group showing the operators within the group.](../media/6a12f1e8-112d-48ee-9a73-82b3dd0542e7.png)

### Adding a group

You can quickly add a group, which can have its own conditions and operator within that group.

![Add group button.](../media/5f72f292-d1f3-4f11-a911-a9f71e10abf6.png)

### Choosing the operator between groups

Between groups, you can choose whether the conditions in just one group or all of the groups must be satisfied for the content to match the rule.

For example, the built-in **U.S. HIPAA** policy has a rule that uses an **AND** operator between the groups so that it identifies content that contains:

- from the group **PII Identifiers** (at least one SSN number **OR** DEA number)

    **AND**

- from the group **Medical Terms** (at least one ICD-9-CM keyword **OR** ICD-10-CM keyword)

![Groups showing the operator between groups.](../media/354aa77f-569c-4847-9dfe-605ee2bb28d1.png)

## The priority by which rules are processed

When you create rules in a policy, each rule is assigned a priority in the order in which it's created — meaning, the rule created first has first priority, the rule created second has second priority, and so on.

> [!div class="mx-imgBorder"]
> ![Rules in priority order.](../media/dlp-rules-in-priority-order.png)

After you have set up more than one DLP policy, you can change the priority of one or more policies. To do that, select a policy, choose **Edit policy**, and use the **Priority** list to specify its priority.

> [!div class="mx-imgBorder"]
> ![Set priority for a policy.](../media/dlp-set-policy-priority.png)

When content is evaluated against rules, the rules are processed in priority order. If content matches multiple rules, the rules are processed in priority order and the most restrictive action is enforced. For example, if content matches all of the following rules, Rule 3 is enforced because it's the highest priority, most restrictive rule:

- Rule 1: only notifies users

- Rule 2: notifies users, restricts access, and allows user overrides

- Rule 3: notifies users, restricts access, and does not allow user overrides

- Rule 4: only notifies users

- Rule 5: restricts access

- Rule 6: notifies users, restricts access, and does not allow user overrides

In this example, note that matches for all of the rules are recorded in the audit logs and shown in the DLP reports, even though only the most restrictive rule is enforced.

Regarding policy tips, note that:

- Only the policy tip from the highest priority, most restrictive rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that simply sends a notification. This prevents people from seeing a cascade of policy tips.

- If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.

-->

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>Optimisation des règles pour une correspondance plus facile ou plus difficile

Lorsque les utilisateurs créent et activent leurs stratégies DLP, ils rencontrent parfois les problèmes suivants :

- Trop de contenu qui **ne constitue pas** des informations sensibles correspond aux règles. Autrement dit, le nombre de faux positifs est trop élevé.

- Trop peu de contenu **qui constitue** des informations sensibles correspond aux règles. En d’autres termes, les mesures de protection ne sont pas appliquées aux informations sensibles.

Pour résoudre ces problèmes, vous pouvez optimiser vos règles en ajustant le nombre d’instances et la précision de correspondance pour que le contenu corresponde plus ou moins aux règles. Chaque type d’informations sensibles utilisé dans une règle a un nombre d’instances et une précision de correspondance.

### <a name="instance-count"></a>Nombre d’instances

Le nombre d’instances indique simplement combien d’occurrences d’un type spécifique d’informations sensibles doivent être présentes pour que le contenu corresponde à la règle. Par exemple, le contenu correspond à la règle illustrée ci-dessous si les valeurs entre 1 et 9 sont uniques dans un pays donné. les numéros de passeport sont identifiés.

> [!NOTE]
> Le nombre d’instances inclut uniquement le nombre de correspondances **Uniques** avec des types d’informations confidentielles et des mots clés. Par exemple, si un courrier contient 10 occurrences du même numéro de carte de paiement, ces 10 occurrences comptent pour une seule instance d’un numéro de carte de paiement.

L’optimisation des règles à l’aide du nombre d’instances est simple :

- Pour que la règle corresponde plus facilement, diminuez la valeur **min** et/ou augmentez la valeur **max**. Vous pouvez également donner à **max** une valeur **quelconque** en supprimant la valeur numérique.

- Pour que la règle corresponde plus difficilement, augmentez la valeur **min**.

En règle générale, les actions moins restrictives, telles que l’envoi de notifications à l’utilisateur, s’utilisent dans une règle avec un nombre d’instances inférieur (par exemple, 1 à 9). Quant aux actions plus restrictives, telles que la limitation de l’accès au contenu sans autoriser les remplacements de l’utilisateur, elles s’utilisent dans une règle avec un nombre d’instances supérieur (par exemple, entre 10 et une valeur supérieure).

![Nombre d’instances dans l’éditeur de règles.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>Précision de correspondance

Comme décrit ci-dessus, un type d’informations sensibles est défini et détecté en utilisant une combinaison de différents types de critères. En règle générale, un type d’informations sensibles est défini par plusieurs de ces combinaisons, appelés modèles. Un modèle qui nécessite moins de critères a une précision de correspondance (ou niveau de confiance) inférieure, alors qu’un modèle qui nécessite plus de critères a une précision de correspondance (ou niveau de confiance) supérieure. Pour en savoir plus sur les modèles et les niveaux de confiance réels utilisés par chaque type d’informations sensibles, consultez [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md).

Par exemple, le type d’informations sensibles Numéro de carte bancaire est défini par deux modèles :

- Un modèle avec une confiance de 65 % qui nécessite :

  - Un nombre dans le format d’un numéro de carte bancaire.

  - Un nombre qui passe la somme de contrôle.

- Un modèle avec une confiance de 85 % qui nécessite :

  - Un nombre dans le format d’un numéro de carte bancaire.

  - Un nombre qui passe la somme de contrôle.

  - Un mot clé ou une date d’expiration dans le bon format.

Vous pouvez utiliser ces niveaux de confiance (ou précision de correspondance) dans vos règles. En règle générale, les actions moins restrictives, telles que l’envoi de notifications à l’utilisateur, s’utilisent dans une règle avec une précision de correspondance inférieure. Quant aux actions plus restrictives, telles que la limitation de l’accès au contenu sans autoriser les remplacements de l’utilisateur, elles s’utilisent dans une règle avec une précision de correspondance supérieure.

Il est essentiel de comprendre que lorsqu’un type spécifique d’informations sensibles, comme un numéro de carte bancaire, est identifié dans le contenu, un seul niveau de confiance est renvoyé :

- Si toutes les correspondances correspondent à un seul modèle, le niveau de confiance de ce modèle est renvoyé.

- En cas de correspondances à plusieurs modèles (par exemple, des correspondances à deux niveaux de confiance différents), un niveau de confiance supérieur à celui de chacun des modèles est renvoyé. Il s’agit de la partie délicate. Par exemple, pour une carte bancaire, si les modèles à 65 % et 85 % correspondent, le niveau de confiance renvoyé pour ce type d’informations sensibles est supérieur à 90 %, car plus de critères signifie plus de confiance.

Par conséquent si vous voulez créer deux règles mutuellement exclusives pour les cartes bancaires, une pour la précision de correspondance de 65 % et une pour la précision de correspondance de 85 %, les plages de précision de correspondance se présenteraient comme suit. La première règle ne prend que les correspondances au modèle à 65 %. La deuxième règle prend les correspondances avec **au moins une** correspondance à 85 % et **peut éventuellement avoir** d’autres correspondances de confiance inférieure.

![Deux règles avec des plages différentes pour la précision des correspondances.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

Pour ces raisons, les conseils pour la création de règles avec des précisions de correspondance différentes sont les suivants :

- En général, le niveau de confiance le plus faible utilise la même valeur pour **min** et **max** (pas un intervalle).

- Le niveau de confiance le plus élevé est généralement un intervalle commençant juste au-dessus du niveau de confiance inférieur et allant jusqu’à 100.

- Tous les niveaux de confiance intermédiaires commencent généralement juste au-dessus du niveau de confiance inférieur pour finir juste en dessous du niveau de confiance supérieur.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>Utilisation d’une étiquette de rétention comme condition dans une stratégie DLP

Lorsque vous utilisez une [étiquette de rétention](retention.md#retention-labels) précédemment créée et publiée comme condition dans une stratégie DLP, vous devez tenir compte des éléments suivants :

- L’étiquette de rétention doit être déjà créée et publiée avant de tenter de l’utiliser en tant que condition dans une stratégie DLP.
- La synchronisation des étiquettes de rétention publiées peut prendre de un à sept jours. Pour plus d’informations, voir [Lorsque les étiquettes de rétention sont disponibles à l’application](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) pour les étiquettes de rétention publiées dans une stratégie de rétention, et [Temps nécessaire pour la prise d’effet des étiquettes de rétention](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) pour les étiquettes de rétention publiées automatiquement.
- L’utilisation d’une étiquette de rétention dans une stratégie **est prise en charge uniquement pour des éléments SharePoint et OneDrive**.

  ![Étiquettes en tant que condition.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  Vous souhaitez peut-être utiliser une étiquette de rétention dans une stratégie DLP si vous avez des éléments sous rétention et suppression auxquels vous voulez appliquer des contrôles supplémentaires, par exemple :

  - Vous avez publié une étiquette de rétention nommée **année fiscale 2018** qui, lorsqu’elle est appliquée à des documents fiscaux de 2018 stockés dans SharePoint, les conserve pendant 10 ans, puis les supprime. Vous ne souhaitez pas non plus que ces éléments soient partagés à l’extérieur de votre organisation, ce que vous pouvez faire grâce à une stratégie DLP.

  > [!IMPORTANT]
  > L’erreur ci-après s’affiche si vous spécifiez une étiquette de rétention comme condition dans une stratégie DLP et que vous incluez également Exchange et/ou Teams comme emplacement : **« La protection du contenu étiqueté dans les messages électroniques et d’équipe n’est pas prise en charge. Supprimez l’étiquette ci-dessous ou désactivez Exchange ou Teams en tant qu’emplacement. »** Cela est dû au fait qu’Exchange transport n’évalue pas les métadonnées d’étiquette lors de l’envoi et de la distribution des messages.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>Utilisation d’une étiquette de confidentialité comme condition dans une stratégie DLP

[En savoir plus](./dlp-sensitivity-label-as-condition.md) sur l’utilisation de l’étiquette de confidentialité comme condition dans les stratégies DLP.

### <a name="how-this-feature-relates-to-other-features"></a>Relations entre cette fonctionnalité et d’autres fonctionnalités

Plusieurs fonctionnalités peuvent être appliquées à du contenu comportant des informations sensibles :

- Une [étiquette de rétention et une stratégie de rétention](retention.md) peuvent toutes deux permettre d’appliquer des mesures de **rétention** à ce type de contenu.

- Et une stratégie DLP peut permettre d’y appliquer des mesures de **protection**. Avant l’application de ces mesures, une stratégie DLP peut exiger que d’autres conditions soient remplies en plus du contenu comportant une étiquette.

![Diagramme des fonctionnalités qui peuvent s’appliquer aux informations sensibles.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

Notez qu’une stratégie DLP offre des capacités de détection plus approfondies qu’une étiquette ou qu’une stratégie de rétention appliquées à des informations sensibles. Une stratégie DLP peut déclencher l’application de mesures de protection sur du contenu comportant des informations sensibles, et si les informations sensibles sont supprimées du contenu, ces mesures de protection sont annulées lors de l’analyse de contenu suivante. Mais si une stratégie de rétention ou une étiquette est appliquée au contenu comportant des informations sensibles, il s’agit d’une mesure unique qui ne peut pas être annulée, même si les informations sensibles sont supprimées.

L’utilisation d’une étiquette comme condition dans une stratégie DLP vous permet d’appliquer des mesures de rétention et de protection au contenu associé à cette étiquette. Un contenu comportant une étiquette et un contenu comportant des informations sensibles sont semblables : l’étiquette et les informations sensibles sont des propriétés utilisées pour classifier le contenu dans le but d’y appliquer des mesures.

![Diagramme de la stratégie DLP utilisant l’étiquette comme condition.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>Paramètres simples et paramètres avancés

Lorsque vous créez une stratégie DLP, vous devez choisir entre les paramètres simples ou avancés :

- Les **paramètres simples** permettent de créer le type le plus courant de stratégie DLP sans utiliser l’éditeur de règles pour créer ou modifier des règles.

- Les **paramètres avancés** utilisent l’éditeur de règles pour vous donner un contrôle total sur chaque paramètre de votre stratégie DLP.

Soyez rassuré, en réalité, les paramètres simples et avancés fonctionnent de la même manière, en appliquant des règles composées de conditions et d’actions, uniquement avec les paramètres simples, vous ne pouvez pas afficher l’éditeur de règle. C’est un moyen rapide de créer une stratégie DLP.

### <a name="simple-settings"></a>Paramètres simples

Le scénario de protection contre la perte de données (DLP) de loin le plus courant consiste à créer une stratégie pour empêcher le partage de contenu comportant des informations sensibles avec des personnes extérieures à votre organisation, et à exécuter des actions de correction automatiques telles que la restriction de l’accès au contenu, l’envoi de notifications aux utilisateurs finaux ou à l’administrateur, et l’audit de l’événement en vue d’un examen ultérieur. Les stratégies de protection contre la perte de données (DLP) permettent d’empêcher la divulgation accidentelle d’informations sensibles.

Pour atteindre cet objectif plus facilement, vous pouvez choisir d’utiliser les **paramètres simples** lorsque vous créez une stratégie DLP. Ces paramètres proposent toutes les options nécessaires pour implémenter les stratégies DLP les plus courantes, sans avoir à ouvrir l’éditeur de règles.

![Options DLP pour les paramètres simples et avancés.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>Paramètres avancés

Si vous devez créer des stratégies DLP plus personnalisées, vous pouvez choisir d’utiliser les **paramètres avancés**.

Les paramètres avancés présentent l’éditeur de règles, où vous contrôlez entièrement chaque option, y compris le nombre d’instances et la précision des correspondances (niveau de confiance) pour chaque règle.

Pour accéder rapidement à une section, cliquez sur un élément de la navigation supérieure de l’éditeur de règles.

![Menu de navigation supérieur de l’éditeur de règles DLP.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>Modèles de stratégie de protection contre la perte de données (DLP)

La première étape de la création d’une stratégie DLP consiste à choisir les informations à protéger. En utilisant un modèle DLP, vous n’avez alors pas à faire l’effort de créer intégralement un ensemble de règles et d’identifier les types d’informations à inclure par défaut. Vous pouvez ensuite ajouter des éléments à ces exigences ou modifier ces dernières pour ajuster la règle afin de répondre aux besoins spécifiques de votre organisation.

Un modèle de stratégie DLP préconfiguré peut vous aider à détecter des types spécifiques d’informations sensibles, comme des données HIPAA, des données PCI-DSS, des données Gramm-Leach-Bliley Act ou même des informations d’identification personnelle propres aux paramètres régionaux. Pour faciliter la recherche et la protection des types d’informations sensibles courants, les modèles de stratégie inclus dans Microsoft 365 contiennent déjà les types d’informations sensibles les plus courants, nécessaires pour commencer.

![Liste des modèles pour les stratégies de protection contre la perte de données, avec l’accent mis sur le modèle pour le Patriot Act des États-Unis.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

Votre organisation peut également avoir ses exigences propres, auquel cas vous pouvez créer entièrement une stratégie DLP en choisissant l’option **Stratégie personnalisée**. Une stratégie personnalisée est vide et ne contient aucune règle prédéfinie.

<!-- ## Roll out DLP policies gradually with test mode

rehomed to Plan for DLP

When you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before fully enforcing them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require access to in order to get their work done.

If you're creating DLP policies with a large potential impact, we recommend following this sequence:

1. **Start in test mode without Policy Tips** and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

2. **Move to Test mode with notifications and Policy Tips** so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

3. **Start full enforcement on the policies** so that the actions in the rules are applied and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    You can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its status in the rule editor.

    ![Options for turning off a rule in a policy.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    You can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In a row for a rule, choose the ellipses (**...**), and then choose an option, such as **Move down** or **Bring to last**.

    > [!div class="mx-imgBorder"]
    > ![Set rule priority.](../media/dlp-set-rule-priority.png)-->

## <a name="dlp-reports"></a>Rapports DLP

Après avoir créé et activé vos stratégies DLP, vous voudrez vérifier qu’elles fonctionnent comme prévu et vous aident à assurer la conformité. Avec les rapports DLP, vous pouvez rapidement consulter le nombre de correspondances de stratégie DLP et de règle dans le temps, ainsi que le nombre de faux positifs et de remplacements. Pour chaque rapport, vous pouvez filtrer ces correspondances par emplacement, par période et même affiner le filtrage sur une stratégie, règle ou action spécifique.

Grâce aux rapports DLP, vous pouvez obtenir une vue d’ensemble des activités et :

- Vous concentrer sur des périodes de temps spécifiques et comprendre les raisons des pics et des tendances.

- Découvrir les processus d’entreprise qui enfreignent les stratégies de conformité de votre organisation.

- Comprendre l’incidence des stratégies DLP sur l’entreprise.

En outre, vous pouvez utiliser les rapports DLP pour affiner vos stratégies DLP lorsque vous les exécutez.

![Tableau de bord rapports dans le Centre de sécurité et de conformité.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>Fonctionnement des stratégies DLP

DLP détecte les informations sensibles à l’aide d’une analyse approfondie du contenu (et pas d’une simple analyse de texte). Cette analyse approfondie utilise les correspondances de mots clés, les correspondances de dictionnaire, l’évaluation des expressions régulières, les fonctions internes et d’autres méthodes pour détecter le contenu qui correspond à vos stratégies DLP. Seul un petit pourcentage de vos données peut être considéré comme sensible. Une stratégie DLP peut identifier, surveiller et protéger automatiquement ces données uniquement, sans gêner ou affecter les personnes travaillant avec le reste de votre contenu.

### <a name="policies-are-synced"></a>Synchronisation des stratégies

Après avoir créé une stratégie DLP dans le portail de conformité Microsoft Purview, elle est stockée dans un magasin de stratégies central, puis synchronisée avec les différentes sources de contenu, notamment :

- Depuis Exchange Online vers Outlook sur le web et Outlook.

- Sites OneDrive Entreprise.

- Sites SharePoint Online.

- Programmes de bureau Office (Excel, PowerPoint et Word).

- Canaux et messages de conversations Microsoft Teams.

Une fois la stratégie synchronisée avec les emplacements adéquats, elle commence à évaluer le contenu et à mettre en place des actions.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>Évaluation des stratégies dans les sites OneDrive Entreprise et SharePoint Online

Dans l’ensemble de vos sites SharePoint Online et OneDrive Entreprise, les documents changent constamment : ils sont continuellement créés, modifiés, partagés, etc. Cela signifie que les documents peuvent à tout moment soit être en conflit, soit être conformes à la stratégie DLP. Par exemple, une personne peut télécharger un document ne contenant aucune information sensible sur le site de son équipe mais une autre personne peut ensuite modifier le même document et y ajouter des informations sensibles.

Pour cette raison, les stratégies DLP vérifient les correspondances de stratégie fréquemment dans les documents en arrière-plan. Vous pouvez considérer ceci comme une évaluation asynchrone des stratégies.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>Mode de fonctionnement

Au fur et à mesure de l’ajout ou de la modification de documents dans ses sites, le moteur de recherche analyse le contenu de sorte que vous puissiez le rechercher ultérieurement. Pendant ce temps, le contenu est également analysé pour vérifier s’il présente des informations sensibles et s’il est partagé. Les informations sensibles trouvées sont stockées en toute sécurité dans l’index de recherche, afin que seule l’équipe de conformité puisse y accéder, et pas les utilisateurs standard. Chaque stratégie DLP que vous avez activée s’exécute en arrière-plan (de façon asynchrone), en vérifiant fréquemment le contenu qui correspond à une stratégie et en appliquant des actions pour le protéger de toute divulgation accidentelle.

![Diagramme montrant comment la stratégie DLP évalue le contenu de façon asynchrone.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording --> Enfin, les documents peuvent entrer en conflit avec une stratégie DLP, mais ils peuvent également y devenir conformes. Par exemple, si une personne ajoute des numéros de carte de crédit à un document, une stratégie DLP peut alors bloquer l’accès au document automatiquement. Toutefois, si cette personne supprime ensuite les informations sensibles, l’action (dans ce cas, le blocage) est annulée automatiquement à la prochaine évaluation du document par rapport à la stratégie.

La protection contre la perte de données évalue le contenu pouvant être indexé. Pour plus d’informations sur les types de fichiers analysés par défaut, consultez la rubrique [Extensions de nom de fichier et types de fichier analysés par défaut dans SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> Afin d’empêcher le partage de documents avant que les stratégies DLP aient eu la possibilité de les analyser, le partage de nouveaux fichiers dans SharePoint peut être bloqué jusqu’à ce que son contenu ait été indexé. Pour plus d’informations, consultez [Marquer les nouveaux fichiers comme sensibles par défaut](/sharepoint/sensitive-by-default).

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>Évaluation des stratégies dans Exchange Online, Outlook et Outlook sur le web

Lorsque vous créez une stratégie DLP qui inclut Exchange Online en tant qu’emplacement, la stratégie est synchronisée entre le portail de conformité Microsoft Purview et Exchange Online, puis de Exchange Online à Outlook sur le web  et Outlook.

Lors de la rédaction d’un message dans Outlook, l’utilisateur peut voir les conseils de stratégie, puisque le contenu en cours de création est évalué par rapport aux stratégies DLP. Une fois qu’un message est envoyé, il est évalué par rapport aux stratégies DLP dans le cadre normal du flux de messagerie, ainsi que les règles de flux de messagerie Exchange (également appelées règles de transport) et les stratégies DLP créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>. Les stratégies DLP analysent le message ainsi que les éventuelles pièces jointes.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>Évaluation des stratégies dans les programmes de bureau Office

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel, PowerPoint et Word incluent la même capacité à identifier les informations sensibles et à appliquer les stratégies DLP que SharePoint Online et OneDrive Entreprise. Ces programmes Office synchronisent leurs stratégies DLP directement à partir du magasin central de stratégies, puis évaluent en permanence le contenu par rapport aux stratégies DLP lorsque les utilisateurs travaillent avec des documents ouverts à partir d’un site inclus dans une stratégie DLP.

L’évaluation des stratégies DLP dans Office est conçue pour ne pas avoir d’incidence sur les performances des programmes ou la productivité des personnes qui travaillent sur le contenu. Si elles travaillent sur un document volumineux ou que l’ordinateur de l’utilisateur est occupé, l’affichage d’un conseil de stratégie peut prendre quelques secondes.

### <a name="policy-evaluation-in-microsoft-teams"></a>Évaluation des stratégies dans Microsoft Teams
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

Lorsque vous créez une stratégie DLP qui inclut Microsoft Teams comme emplacement, la stratégie est synchronisée entre le portail de conformité Microsoft Purview et les comptes d’utilisateur, les canaux et les messages de conversation Microsoft Teams. Selon la configuration des stratégies DLP, lorsque quelqu’un tente de partager des informations sensibles dans une conversation ou un message de canal Microsoft Teams, le message peut être bloqué ou révoqué. Les documents qui contiennent des informations sensibles et qui sont partagés avec des invités (utilisateurs externes) ne s’ouvrent pas pour ces utilisateurs. Consultez l’article sur la [protection contre la perte de données et Microsoft Teams](dlp-microsoft-teams.md) pour obtenir plus d’informations à ce sujet.

## <a name="permissions"></a>Autorisations

Par défaut, les administrateurs généraux, les administrateurs de sécurité et les administrateurs de conformité ont accès à la création et à l’application d’une stratégie DLP. Les autres membres de votre équipe de conformité qui créeront des stratégies DLP ont besoin d’autorisations sur le portail de conformité Microsoft Purview. Par défaut, votre administrateur de locataire a accès à cet emplacement et peut accorder aux agents de conformité et à d’autres personnes l’accès au portail de conformité Microsoft Purview, sans leur accorder toutes les autorisations d’un administrateur de locataire. Pour ce faire, nous vous recommandons d’effectuer les opérations suivantes :

1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.

2. Créez un groupe de rôles sur la page **Autorisations** du portail de conformité Microsoft Purview.

3. Lors de la création du groupe de rôles, utilisez la section **Choisir des rôles** pour ajouter le rôle suivant au groupe de rôles : **Gestion de la conformité DLP**.

4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Vous pouvez également créer un groupe de rôles avec des privilèges en affichage seul vers les stratégies DLP et les rapports DLP en accordant au rôle **Gestion de la conformité DLP en affichage seul**.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

Ces autorisations sont requises uniquement pour créer et appliquer une stratégie DLP. L’application d’une stratégie ne nécessite pas d’accès au contenu.

## <a name="find-the-dlp-cmdlets"></a>Trouver les applets de commande DLP

Pour utiliser la plupart des applets de commande pour le portail de conformité Microsoft Purview, vous devez :

1. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Utiliser l’une de ces [applets de commande de stratégie et de conformité DLP](/powershell/module/exchange/export-dlppolicycollection).

Toutefois, les rapports DLP doivent extraire des données de Microsoft 365, y compris Exchange Online. Pour cette raison, ***les applets de commande des rapports DLP sont disponibles dans Exchange Online PowerShell, et non dans portail de conformité Microsoft Purview PowerShell***. Par conséquent, pour utiliser les applets de commande pour les rapports DLP, vous devez :

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’une de ces applets de commande pour les rapports DLP :

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>Plus d’informations

- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)

- [Envoyer des notifications et afficher des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md)

- [Créer une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés](protect-documents-that-have-fci-or-other-properties.md)

- [Contenu des modèles de stratégie DLP](what-the-dlp-policy-templates-include.md)

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)

- [Fonctions de type d’informations sensibles](sit-functions.md)

- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
