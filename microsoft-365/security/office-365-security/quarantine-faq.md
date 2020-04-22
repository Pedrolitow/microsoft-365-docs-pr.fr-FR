---
title: FAQ sur la mise en quarantaine
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c440b2ac-cafa-4be5-ba4c-14278a7990ae
ms.collection:
- M365-security-compliance
description: Réponses aux questions fréquemment posées sur la mise en quarantaine dans Office 365.
ms.openlocfilehash: 3947fbed2a17380a18320a8bffd08a8178ad2b3f
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43634423"
---
# <a name="quarantine-faq"></a>FAQ sur la mise en quarantaine

Cette rubrique fournit des questions fréquemment posées et des réponses sur la mise en quarantaine pour les clients Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des clients Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online.

## <a name="q-how-do-i-manage-messages-that-were-quarantined-for-malware"></a>Q : Comment puis-je gérer les messages mis en quarantaine pour les programmes malveillants ?

Seuls les administrateurs peuvent gérer les messages mis en quarantaine pour les programmes malveillants. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans Office 365](manage-quarantined-messages-and-files.md).

## <a name="q-how-do-i-quarantine-spam"></a>Q : comment mettre en quarantaine le courrier indésirable ?

A. Par défaut, les messages classés comme courriers indésirables ou en masse par filtrage du courrier indésirable sont remis à la boîte aux lettres de l’utilisateur et sont déplacés vers le dossier courrier indésirable. Toutefois, vous pouvez créer et configurer des stratégies de blocage du courrier indésirable pour mettre en quarantaine les messages électroniques en masse ou le courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

## <a name="q-how-do-i-give-users-access-to-the-quarantine"></a>Q : comment accorder aux utilisateurs l’accès à la mise en quarantaine ?

A. Un utilisateur doit disposer d’un compte valide pour accéder à ses propres messages en quarantaine. La fonctionnalité EOP autonome nécessite que les utilisateurs soient représentés en tant qu’utilisateurs de messagerie dans EOP (création manuelle ou création via la synchronisation d’annuaires). Pour plus d’informations sur la gestion des utilisateurs dans les environnements autonomes EOP, consultez la rubrique [gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md).

## <a name="q-what-messages-can-end-users-access-in-quarantine"></a>Q : quels messages les utilisateurs finaux peuvent-ils accéder en quarantaine ?

A. Les utilisateurs peuvent accéder aux messages de courrier indésirable, de courrier en nombre et (à partir d’avril, 2020) dans lesquels ils sont destinataires. Les utilisateurs finaux ne peuvent pas accéder aux programmes malveillants mis en quarantaine, à la confiance élevée ou aux messages mis en quarantaine en raison de la **remise du message à l’action de mise en quarantaine hébergée dans les** règles de flux de messagerie (également appelées règles de transport). Pour plus d’informations sur les utilisateurs qui accèdent aux messages mis en quarantaine, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Office 365](find-and-release-quarantined-messages-as-a-user.md).

## <a name="q-how-long-are-messages-kept-in-the-quarantine"></a>Q : combien de temps les messages sont-ils conservés en quarantaine ?

A. Vous configurez la durée pendant laquelle les courriers indésirables, les messages hameçons et les messages électroniques en masse sont conservés en quarantaine à l’aide de stratégies de blocage du courrier indésirable. La valeur par défaut est 30 jours, ce qui est également le maximum. Pour plus d’informations, consultez la rubrique [Configuration des stratégies de blocage du courrier indésirable dans Office 365](configure-your-spam-filter-policies.md)

Pour les messages mis en quarantaine par l’action de règle de flux de messagerie, **remet le message à la quarantaine hébergée**, les messages sont conservés en quarantaine pendant 30 jours. Vous ne pouvez pas configurer cette durée.

Une fois la période expirée, les messages sont supprimés et ne sont pas récupérables.

## <a name="q-can-i-release-or-report-more-than-one-quarantined-message-at-a-time"></a>Q : puis-je publier ou signaler plusieurs messages en quarantaine à la fois ?

A. Dans le centre de sécurité & conformité, vous pouvez sélectionner et publier jusqu’à 100 messages à la fois.

Les administrateurs peuvent utiliser les cmdlets [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-quarantinemessage) et [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/release-quarantinemessage) dans Exchange Online PowerShell ou un environnement autonome Exchange Online Protection PowerShell pour rechercher et débloquer des messages mis en quarantaine en bloc, et pour signaler des faux positifs en bloc.

## <a name="q-are-wildcards-supported-when-searching-for-quarantined-messages-can-i-search-for-quarantined-messages-for-a-specific-domain"></a>Q : est-ce que les caractères génériques sont pris en charge lors de la recherche de messages mis en quarantaine ? Puis-je rechercher des messages mis en quarantaine pour un domaine spécifique ?

A. Les caractères génériques ne sont pas pris en charge dans le centre de sécurité & conformité. Par exemple, lors de la recherche d’un expéditeur, vous devez spécifier l’adresse de messagerie complète. Toutefois, vous pouvez utiliser des caractères génériques dans Exchange Online PowerShell ou Exchange Online Protection PowerShell.

Par exemple, exécutez la commande suivante pour rechercher les messages de courrier indésirable mis en quarantaine à partir de tous les expéditeurs dans le domaine contoso.com :

```powershell
$CQ = Get-QuarantineMessage -Type Spam | where {$_.SenderAddress -like "*@contoso.com"}
```

Ensuite, exécutez la commande suivante pour libérer ces messages à tous les destinataires d’origine :

```powershell
$CQ | foreach {Release-QuarantineMessage -Identity $_.Identity -ReleaseToAll}
```

Une fois que vous avez publié un message, vous ne pouvez plus le libérer.
