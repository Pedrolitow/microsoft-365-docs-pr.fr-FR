---
title: (Faux positifs) Comment gérer les e-mails légitimes bloqués à l’aide de Microsoft Defender pour Office 365
description: Étapes permettant de gérer les messages électroniques légitimes bloqués (Faux positifs) par Microsoft Defender pour Office 365 afin d’éviter toute perte d’activité.
search.product: ''
search.appverid: ''
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: jarogers
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.subservice: mdo
ms.openlocfilehash: ae7b66a2dc8c8b4fb96360ca2bc0625bfcdf6b43
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67596674"
---
# <a name="how-to-handle-legitimate-emails-getting-blocked-false-positive-using-microsoft-defender-for-office-365"></a>Comment gérer les e-mails légitimes bloqués (Faux positif), à l’aide de Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 aide à gérer les e-mails professionnels légitimes importants qui sont bloqués par erreur en tant que menaces (faux positifs). Defender pour Office 365 pouvez aider les administrateurs à comprendre *pourquoi* les e-mails légitimes sont bloqués, comment résoudre la situation rapidement et empêcher des situations similaires de se produire à l’avenir.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 1 ou 2 (inclus dans le cadre de l’E5). Exchange Online clients peuvent également tirer parti de cette fonctionnalité.
- Autorisations suffisantes (rôle Administrateur de la sécurité).
- 5 à 10 minutes pour effectuer les étapes ci-dessous.

## <a name="handling-legitimate-emails-in-to-junk-folder-of-end-users"></a>Gestion des e-mails légitimes dans le dossier Courrier indésirable des utilisateurs finaux

1. Demandez aux utilisateurs finaux de signaler l’e-mail comme **non indésirable** à l’aide du complément Microsoft Message ou des boutons Outlook.
2. Les utilisateurs finaux peuvent également ajouter l’expéditeur à la [**liste des expéditeurs approuvés**](https://support.microsoft.com/en-us/office/safe-senders-in-outlook-com-470d4ee6-e3b6-402b-8cd9-a6f00eda7339) dans Outlook pour empêcher l’envoi de l’e-mail de ces expéditeurs dans le dossier Courrier indésirable.
3. Les administrateurs peuvent trier les messages signalés par l’utilisateur à partir du portail de [contenu signalé par l’utilisateur](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. À partir de ces messages signalés, les administrateurs peuvent envoyer à [**Microsoft pour analyse**](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) et comprendre pourquoi cet e-mail a été bloqué en premier lieu.
5. Si nécessaire, lors de la soumission à Microsoft à des fins d’analyse, les administrateurs peuvent créer judicieusement une [**autorisation** permettant à un expéditeur](/microsoft-365/security/office-365-security/manage-tenant-allows?view=o365-worldwide#add-sender-allows-using-the-submissions-portal&preserve-view=true) d’atténuer le problème.
6. Une fois que les résultats de la soumission de l’administrateur sont disponibles, lisez-le pour comprendre pourquoi les e-mails ont été bloqués et comment la configuration de votre locataire pourrait être améliorée pour *éviter* que des situations similaires se produisent à l’avenir.

## <a name="handling-legitimate-emails-that-are-in-quarantine-folder-of-end-users"></a>Gestion des e-mails légitimes qui sont dans le dossier de quarantaine des utilisateurs finaux

1. Un utilisateur final reçoit un [condensé d’e-mail](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) sur les messages mis en quarantaine conformément aux paramètres activés par les administrateurs de sécurité.
2. Les utilisateurs finaux peuvent afficher un aperçu des messages en quarantaine, bloquer l’expéditeur, publier les messages, envoyer ces messages à Microsoft à des fins d’analyse et demander la publication de ces e-mails auprès des administrateurs.

## <a name="handling-legitimate-emails-in-quarantine-folder-of-an-admin"></a>Gestion des e-mails légitimes dans le dossier de quarantaine d’un administrateur

1. Les administrateurs peuvent afficher les e-mails mis en quarantaine (y compris ceux qui demandent l’autorisation de demander la mise en production) à partir de la [page de révision](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. Les administrateurs peuvent libérer le message de la quarantaine lors de son envoi à Microsoft à des fins d’analyse et créer une autorisation pour atténuer la situation.
3. Une fois les résultats des soumissions disponibles, les administrateurs doivent lire le verdict pour comprendre pourquoi les e-mails ont été bloqués et comment la configuration du locataire pourrait être améliorée pour éviter que des situations similaires se produisent à l’avenir.
