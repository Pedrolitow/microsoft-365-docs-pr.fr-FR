---
title: Utiliser Exchange Online et le centre de sécurité et conformité pour se conformer à la règle SEC 17a-4
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Configurer le Centre de conformité et Exchange Online pour de répondre aux exigences réglementaires de la règle CFTC 1.31 (c)-(d), règle FINRA 4511 et la règle SEC 17a -4.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 6dc53ec9dd016a2423ca96886bba400e2f17e17a
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819074"
---
# <a name="use-exchange-online-and-the-security--compliance-center-to-comply-with-sec-rule-17a-4"></a>Utiliser Exchange Online et le centre de sécurité et conformité pour se conformer à la règle SEC 17a-4

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

If your organization needs to comply with regulatory standards for retaining your data, the Security & Compliance Center provides features to manage the lifecycle of your data in Exchange Online. This includes the ability to retain, audit, search, and export your data. These capabilities are sufficient to meet the needs of most organizations.

However, some organizations in highly regulated industries are subject to more stringent regulatory requirements. For example, financial institutions such as banks or broker dealers are subject to Rule 17a-4 issued by the Securities and Exchange Commission (SEC). Rule 17a-4 has specific requirements for electronic data storage, including many aspects of record management, such as the duration, format, quality, availability, and accountability of records retention.

Pour aider ces organisations à mieux comprendre comment le Centre de Sécurité et Conformité peut être utilisé pour répondre à leurs obligations légales pour Exchange Online. plus précisément par rapport à la configuration requise relative à la règle 17 a-4, nous avons publié une évaluation en partenariat avec Cohasset Associates.

Cohasset validated that when Exchange Online and the Security & Compliance Center are configured as recommended, they meet the relevant storage requirements of CFTC Rule 1.31(c)-(d), FINRA Rule 4511, and SEC Rule 17a-4. We targeted this set of rules because they represent the most prescriptive guidance globally for records retention for financial institutions.

## <a name="download-the-cohasset-assessment"></a>Télécharger l’évaluation Cohasset

Vous pouvez [télécharger ici l’évaluation Cohasset](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=9fa8349d-a0c9-47d9-93ad-472aa0fa44ec&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers).

![La page de titre de l’évaluation téléchargeable par Cohasset Associates](../media/cohasset-associates-assessment.png)

## <a name="this-assessment-is-specific-to-exchange-online"></a>Cette évaluation est spécifique à Exchange Online

Note that this assessment is specific to Exchange Online. The assessment does not include other Microsoft 365 services such as SharePoint Online or OneDrive for Business, although we are planning support for those services with respect to SEC 17a-4 in the future.

It's important to understand that Skype for Business and Teams also store data in Exchange Online. Therefore, the assessment does cover messages from Skype for Business and channel and chat messages from Teams.

## <a name="using-preservation-lock-is-key-to-the-recommended-configuration"></a>À l’aide de verrouillage de conservation est essentiel pour la configuration recommandée

Highly regulated industries are often required to store electronic communications to meet the WORM (write once, read many) requirement. The WORM requirement dictates a storage solution in which a record must be:

- Conservée pendant une période de rétention obligatoire qui ne peut pas être raccourcie uniquement augmentée.
- Immuable, ce qui signifie que l’enregistrement ne peut pas être remplacée, supprimée ou modifiée pendant la période de rétention requise.

In Exchange Online, when a [retention policy](retention-policies.md) is applied to a user's mailbox, all the user's content will be retained based on the criteria of the policy. In fact, if a user attempts to delete or modify an email, a copy of the email before the change is made will be preserved in a secure, hidden location in the user's mailbox. Retention policies can help ensure that an organization retains electronic communications, but those policies can be modified.

By placing a Preservation Lock on a retention policy, an organization ensures that the policy cannot be modified. In fact, after a Preservation Lock is applied to a retention policy, the following actions are restricted:

- La période de rétention de la stratégie peut uniquement être accrue, elle ne raccourcie pas.
- Les utilisateurs peuvent être ajoutés à la stratégie, mais aucun utilisateur ne peut être supprimé.
- La stratégie de rétention ne peut pas être supprimée par un administrateur.

Le verrouillage de conservation peut vous aider à répondre aux exigences réglementaires SEC 17 a-4.

## <a name="how-to-set-up-preservation-lock"></a>Comment configurer le verrouillage de conservation

Vous pouvez verrouiller une stratégie de rétention à l’aide de PowerShell. Pour plus d’informations, voir [Utiliser le verrouillage de conservation pour se conformer aux exigences réglementaires](retention-policies.md#use-preservation-lock-to-comply-with-regulatory-requirements).

## <a name="known-limitations"></a>Limitations connues

Il existe actuellement quelques limitations dans Exchange Online :

- Les fils de communications ne sont pas disponibles pour les messages de conversation et le canal équipes.
- Les mentions j’aime ne sont pas conservées pour les messages de conversation et le canal équipes.

> [!NOTE]
> L’audit au niveau de l’élément est désormais disponible pour les boîtes aux lettres de groupe Microsoft 365. Pour plus d’informations, voir [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md).
