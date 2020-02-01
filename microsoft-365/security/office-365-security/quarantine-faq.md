---
title: FAQ sur la mise en quarantaine
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
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
description: Cette rubrique présente les questions fréquemment posées ainsi que les réponses au sujet de la mise en quarantaine hébergée.
ms.openlocfilehash: b4112bf785a6ee2f4c833ab08d2c199388585093
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41598661"
---
# <a name="quarantine-faq"></a>FAQ sur la mise en quarantaine

Cette rubrique présente les questions fréquemment posées ainsi que les réponses au sujet de la mise en quarantaine hébergée. Les réponses sont applicables pour les clients Microsoft Exchange Online et Exchange Online Protection.

 **Q. Comment puis-je gérer les messages mis en quarantaine contre les programmes malveillants ?**

Vous devez utiliser le centre de sécurité & conformité afin d’afficher et de manipuler les messages qui ont été envoyés en quarantaine car ils contiennent des programmes malveillants. Pour plus d’informations, consultez la rubrique [mise en quarantaine des messages électroniques dans Office 365](quarantine-email-messages.md).

 **Q. Comment puis-je configurer le service pour envoyer des messages de courrier indésirable mis en quarantaine vers la mise en quarantaine ?**

R. Par défaut, les messages dont le contenu est filtré sont envoyés vers le dossier de courrier indésirable des destinataires. Toutefois, les administrateurs peuvent configurer des stratégies de filtrage de contenu pour envoyer le courrier indésirable mis en quarantaine vers la mise en quarantaine. Pour plus d'informations sur les différentes actions qui peuvent être menées sur les messages dont le contenu est filtré, voir [Configuration de vos stratégies de filtrage du courrier indésirable](configure-your-spam-filter-policies.md).

 **Q. Le service permet-il une gestion par un administrateur ou un utilisateur final des messages de courrier indésirable mis en quarantaine ?**

A. En tant qu’administrateur, vous pouvez rechercher et afficher des détails sur tous les messages électroniques mis en quarantaine dans le centre de sécurité et de conformité (SCC). Après avoir localisé un message, vous pouvez le débloquer pour l'envoyer à des utilisateurs spécifiques et, si vous le souhaitez, le signaler comme faux positif (message légitime) à l'équipe d'analyse du courrier indésirable de Microsoft. Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans Office 365](manage-quarantined-messages-and-files.md).

En tant qu'utilisateur final, vous pouvez gérer vos propres messages mis en quarantaine via :

- L'interface utilisateur de mise en quarantaine du courrier électronique. Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Office 365](find-and-release-quarantined-messages-as-a-user.md).

 **Q. Comment puis-je accorder l’accès à la mise en quarantaine pour mes utilisateurs finaux ?**

A. Pour pouvoir accéder à la mise en quarantaine du courrier indésirable de l’utilisateur final, les utilisateurs finaux doivent disposer d’un ID d’utilisateur et d’un mot de passe Office 365 valides. Les clients EOP qui protègent les boîtes aux lettres locales doivent être des utilisateurs de messagerie valides créés via la synchronisation d’annuaires ou le centre d’administration Exchange. Pour plus d’informations sur la gestion des utilisateurs, les administrateurs EOP peuvent se référer à la rubrique [gérer les utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md). Pour les clients autonomes EOP, nous vous recommandons d’utiliser la synchronisation d’annuaires et d’activer le blocage du périmètre basé sur l’annuaire ; Pour plus d’informations, consultez la rubrique [utiliser le blocage du périmètre basé sur l’annuaire pour rejeter les messages envoyés à des destinataires non valides](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

 **Q. Quels messages les utilisateurs finaux peuvent-ils accéder en quarantaine ?**

A. Les utilisateurs finaux peuvent accéder à leurs propres messages hameçons, de courrier indésirable et de courrier en nombre. Les utilisateurs finaux ne peuvent pas accéder à leur propre programme malveillant, à la confiance élevée ou aux messages qui correspondent à une règle de flux de messagerie (également appelée règle de transport); celles-ci sont disponibles uniquement dans la mise en quarantaine de l’administrateur. 

 **Q. Pendant combien de temps les messages sont-ils mis en quarantaine ?**

A. Par défaut, les messages de courrier indésirable mis en quarantaine sont conservés en quarantaine pendant 30 jours, tandis que les messages mis en quarantaine qui correspondent à une règle de flux de messagerie sont conservés en quarantaine pendant 30 jours, en fonction de la période de rétention définie dans votre stratégie de filtrage de contenu par défaut. Une fois cette période écoulée, les messages sont supprimés et ne sont pas récupérables. La période de rétention des messages mis en quarantaine qui correspondent à une règle de flux de messagerie n’est pas configurable. Vous pouvez raccourcir la période de rétention à l'aide du paramètre **Conserver les courriers indésirables pendant (jours)** dans vos stratégies de filtrage du contenu. Pour plus d'informations, voir [Configuration de vos stratégies de filtrage du courrier indésirable](configure-your-spam-filter-policies.md).

 **Q. Est-ce que je peux libérer ou signaler plusieurs messages mis en quarantaine à la fois ?**

R. Oui, jusqu’à 100 messages peuvent être publiés en même temps dans le portail de mise en quarantaine. De plus, les administrateurs peuvent créer un script Windows PowerShell à distance pour accomplir cette tâche. Utilisez la cmdlet [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-quarantinemessage) pour rechercher des messages, et la cmdlet [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/release-quarantinemessage) pour les libérer.

 **Q. Are wildcards supported when searching for quarantined messages? Can I search for quarantined messages for a specific domain?**

R. Les caractères génériques ne sont pas pris en charge lors de la spécification des critères de recherche dans le Centre d'administration Exchange. Par exemple, si vous recherchez un expéditeur, vous devez indiquer l'adresse électronique complète.

Le recours à Windows PowerShell à distance permet aux administrateurs d'utiliser la cmdlet [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-quarantinemessage) pour rechercher des messages mis en quarantaine pour un domaine spécifique (par exemple, contoso.com) :

```powershell
Get-QuarantineMessage | ? {$_.Senderaddress -like "*@contoso.com"}
```

Les résultats peuvent être transmis à la cmdlet [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/release-quarantinemessage). Incluez le paramètre -ReleaseToAll pour débloquer le message et l'envoyer à tous ses destinataires. Une fois qu'un message est débloqué, il ne peut plus l'être de nouveau.

```powershell
Get-QuarantineMessage | ? {$_.Senderaddress -like "*@contoso.com"}
```
