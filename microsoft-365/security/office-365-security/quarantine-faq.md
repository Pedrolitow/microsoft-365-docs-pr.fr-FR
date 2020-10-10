---
title: FAQ sur les messages mis en quarantaine
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c440b2ac-cafa-4be5-ba4c-14278a7990ae
ms.collection:
- M365-security-compliance
- m365-initiative-m365-defender
description: Les administrateurs peuvent consulter les réponses et les questions fréquemment posées sur les messages mis en quarantaine dans Exchange Online Protection (EOP).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 00768b3584c854ef0648f75f1966a8fa331b2866
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413423"
---
# <a name="quarantined-messages-faq"></a>FAQ sur les messages mis en quarantaine

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Cette rubrique fournit des questions fréquemment posées et des réponses sur les messages électroniques mis en quarantaine pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online (EOP) autonomes sans boîte aux lettres Exchange Online.

Pour obtenir des questions et des réponses sur la protection contre le courrier indésirable, consultez la rubrique [protection contre le courrier indésirable](anti-spam-protection-faq.md).

Pour obtenir des questions et des réponses sur la protection contre les programmes malveillants, consultez la rubrique [anti-malware protection FAQ](anti-malware-protection-faq-eop.md).

Pour obtenir des questions et des réponses sur la protection contre l’usurpation d’identité, consultez la rubrique [anti-spoofing protection FAQ](anti-spoofing-protection-faq.md).

## <a name="how-do-i-manage-messages-that-were-quarantined-for-malware"></a>Comment puis-je gérer les messages qui ont été mis en quarantaine pour les programmes malveillants ?

Seuls les administrateurs peuvent gérer les messages mis en quarantaine pour les programmes malveillants. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur](manage-quarantined-messages-and-files.md).

## <a name="how-do-i-quarantine-spam"></a>Comment mettre en quarantaine le courrier indésirable ?

Par défaut, les messages classés comme courriers indésirables ou en masse par filtrage du courrier indésirable sont remis à la boîte aux lettres de l’utilisateur et sont déplacés vers le dossier courrier indésirable. Toutefois, vous pouvez créer et configurer des stratégies de blocage du courrier indésirable pour mettre en quarantaine les messages électroniques en masse ou le courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

## <a name="how-do-i-give-users-access-to-the-quarantine"></a>Comment accorder aux utilisateurs l’accès à la mise en quarantaine ?

Un utilisateur doit disposer d’un compte valide pour accéder à ses propres messages en quarantaine. La fonctionnalité EOP autonome nécessite que les utilisateurs soient représentés en tant qu’utilisateurs de messagerie dans EOP (création manuelle ou création via la synchronisation d’annuaires). Pour plus d’informations sur la gestion des utilisateurs dans les environnements autonomes EOP, consultez la rubrique [gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

## <a name="what-messages-can-end-users-access-in-quarantine"></a>Quels messages les utilisateurs finaux peuvent-ils accéder en quarantaine ?

Les utilisateurs peuvent accéder aux messages de courrier indésirable, de courrier en nombre et (à partir d’avril 2020) lorsqu’ils sont destinataires. Les utilisateurs finaux ne peuvent pas accéder aux programmes malveillants mis en quarantaine, à la confiance élevée ou aux messages mis en quarantaine en raison de la **remise du message à l’action de mise en quarantaine hébergée dans les** règles de flux de messagerie (également appelées règles de transport). Pour plus d’informations sur les utilisateurs qui accèdent aux messages mis en quarantaine, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur](find-and-release-quarantined-messages-as-a-user.md).

## <a name="how-long-are-messages-kept-in-the-quarantine"></a>Combien de temps les messages sont-ils conservés en quarantaine ?

Vous configurez la durée pendant laquelle les courriers indésirables, les messages hameçons et les messages électroniques en masse sont conservés en quarantaine à l’aide de stratégies de blocage du courrier indésirable. La valeur par défaut est 30 jours, ce qui est également le maximum. Pour plus d’informations, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md)

Pour les messages mis en quarantaine par l’action de règle de flux de messagerie, **remet le message à la quarantaine hébergée**, les messages sont conservés en quarantaine pendant 30 jours. Vous ne pouvez pas configurer cette durée.

Une fois la période expirée, les messages sont supprimés et ne sont pas récupérables.

## <a name="can-i-release-or-report-more-than-one-quarantined-message-at-a-time"></a>Est-ce que je peux libérer ou signaler plusieurs messages mis en quarantaine à la fois ?

Dans le centre de sécurité & conformité, vous pouvez sélectionner et publier jusqu’à 100 messages à la fois.

Les administrateurs peuvent utiliser les cmdlets [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage) et [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/release-quarantinemessage) dans Exchange Online PowerShell ou autonome EOP PowerShell pour rechercher et débloquer les messages mis en quarantaine en bloc, et pour signaler les faux positifs en bloc.

## <a name="are-wildcards-supported-when-searching-for-quarantined-messages-can-i-search-for-quarantined-messages-for-a-specific-domain"></a>Les caractères génériques sont-ils pris en charge lors de la recherche de messages mis en quarantaine ? Puis-je rechercher des messages mis en quarantaine pour un domaine spécifique ?

Les caractères génériques ne sont pas pris en charge dans le centre de sécurité & conformité. Par exemple, lors de la recherche d’un expéditeur, vous devez spécifier l’adresse de messagerie complète. Toutefois, vous pouvez utiliser des caractères génériques dans Exchange Online PowerShell ou autonome EOP PowerShell.

Par exemple, exécutez la commande suivante pour rechercher les messages de courrier indésirable mis en quarantaine à partir de tous les expéditeurs dans le domaine contoso.com :

```powershell
$CQ = Get-QuarantineMessage -Type Spam | where {$_.SenderAddress -like "*@contoso.com"}
```

Ensuite, exécutez la commande suivante pour libérer ces messages à tous les destinataires d’origine :

```powershell
$CQ | foreach {Release-QuarantineMessage -Identity $_.Identity -ReleaseToAll}
```

Une fois que vous avez publié un message, vous ne pouvez plus le libérer.
