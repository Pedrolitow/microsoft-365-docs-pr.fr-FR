---
title: Listes des expéditeurs autorisés et des expéditeurs bloqués dans Exchange Online
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 111ab6b0-2dd2-4a87-a928-4931df6b3c4d
ms.collection:
- M365-security-compliance
description: En tant qu'administrateur Exchange Online ou Exchange Online Protection (EOP), vous pouvez faire en sorte qu'un message électronique circulant via le service ne soit pas marqué comme courrier indésirable. Une manière de procéder consiste à créer des listes d'expéditeurs approuvés et d'expéditeurs bloqués pour les membres de votre organisation.
ms.openlocfilehash: 9c281460aeff64226343af5e5608ccf42fc83799
ms.sourcegitcommit: a122fd1fce523171529c7f610bb7faf09d30a8bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2020
ms.locfileid: "41238391"
---
# <a name="safe-sender-and-blocked-sender-lists-in-exchange-online"></a>Listes des expéditeurs autorisés et des expéditeurs bloqués dans Exchange Online

En tant qu'administrateur Exchange Online ou Exchange Online Protection (EOP), vous pouvez faire en sorte qu'un message électronique circulant via le service ne soit pas marqué comme courrier indésirable. Une manière de procéder consiste à créer des listes d'expéditeurs approuvés et d'expéditeurs bloqués pour les membres de votre organisation.

*Reportez-vous à la version mise à jour des conseils et procédures relatifs à l’utilisation de ces listes en tant qu’administrateur* pour [empêcher que des messages électroniques soient marqués comme courrier indésirable dans Office 365](prevent-email-from-being-marked-as-spam.md).

Si vous n’êtes pas un administrateur et que vous voulez simplement gérer votre courrier indésirable dans Outlook à l’aide d’une liste d’expéditeurs approuvés, consultez les étapes décrites dans la[rubrique vue d’ensemble du filtre de courrier indésirable](https://support.office.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

## <a name="what-is-the-safe-and-blocked-sender-limits-in-exchange-online"></a>Quelles sont les limites d’expéditeurs autorisés et d’expéditeurs bloqués dans Exchange Online ?

Les limites d’expéditeurs autorisés et d’expéditeurs bloqués dans Exchange Online diffèrent des limites d’Active Directory et d’Outlook. Ces limites sont :

- Limite d’expéditeurs autorisés : 1 024

- Limite des expéditeurs bloqués : 500

Remarque :

Vous pouvez observer l’erreur décrite dans [KB2590466](https://support.microsoft.com/help/2590466/you-receive-the-error-junk-e-mail-validation-error-in-outlook-web-app). Pour résoudre ce problème, désactivez la case à cocher « approuver les courriers électroniques en provenance de mes contacts ». Vous pouvez également réduire le nombre d’adresses de messagerie figurant dans votre dossier de contacts par défaut afin de l’appliquer à la limite maximale autorisée de 1024 dans Exchange Online qui est définie pour l’attribut « Paramètres MaxSafeSenders ». Pour plus d’informations sur cet attribut et sur la cmdlet Set-Mailbox, voirscript rubrique suivante :

[Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/mailboxes/Set-Mailbox)

## <a name="see-also"></a>Consultez aussi

[Filtrage des expéditeurs dans Exchange Server](https://docs.microsoft.com/exchange/antispam-and-antimalware/antispam-protection/sender-filtering)
