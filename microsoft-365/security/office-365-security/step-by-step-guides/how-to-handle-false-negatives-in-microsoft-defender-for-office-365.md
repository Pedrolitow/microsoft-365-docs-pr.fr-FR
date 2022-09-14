---
title: (Faux négatifs) Comment gérer les e-mails malveillants remis aux destinataires à l’aide de Microsoft Defender pour Office 365
description: Étapes de gestion des e-mails malveillants envoyés aux utilisateurs finaux et aux boîtes de réception (sous forme de faux négatifs) avec Microsoft Defender pour Office 365 afin d’éviter toute perte d’activité.
search.product: ''
ms.prod: m365-security
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
ms.technology: mdo
search.appverid: met150
ms.openlocfilehash: f93d210482fe66bddfbaee7ef059ec85afe0186b
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67688228"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>Comment gérer les e-mails malveillants qui sont remis aux destinataires (faux négatifs), à l’aide de Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 aide à gérer les e-mails malveillants (faux négatifs) qui sont remis aux destinataires et qui mettent en danger la productivité de votre organisation.
Defender pour Office 365 pouvez vous aider à comprendre pourquoi les e-mails sont remis, comment résoudre la situation rapidement et comment empêcher des situations similaires de se produire à l’avenir.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 1 et 2 (inclus dans le cadre de l’E5). Exchange Online clients peuvent également en tirer parti.
- Autorisations suffisantes (rôle Administrateur de la sécurité).
- 5 à 10 minutes pour effectuer les étapes ci-dessous.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>Gestion des e-mails malveillants dans le dossier Boîte de réception des utilisateurs finaux

1. Demandez aux utilisateurs finaux de signaler l’e-mail comme **hameçonnage** ou **courrier indésirable** à l’aide du complément Microsoft Message, du complément Microsoft Phish ou des boutons Outlook.
2. Les utilisateurs finaux peuvent également ajouter l’expéditeur à la [liste des expéditeurs de blocs](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) dans Outlook pour empêcher la remise des e-mails de cet expéditeur à leur boîte de réception.
3. Les administrateurs peuvent trier les messages signalés par l’utilisateur à partir du portail de [contenu signalé par l’utilisateur](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. À partir de ces messages signalés, les administrateurs peuvent **soumettre à** [Microsoft pour analyse](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) afin d’apprendre pourquoi cet e-mail a été autorisé en premier lieu.
5. Si nécessaire, lors de la soumission à Microsoft à des fins d’analyse, les administrateurs peuvent créer un [bloc pour l’expéditeur](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) afin d’atténuer le problème.
6. Une fois les résultats des soumissions disponibles, lisez le verdict pour comprendre pourquoi les e-mails ont été autorisés et comment la configuration de votre locataire pourrait être améliorée pour éviter que des situations similaires se produisent à l’avenir.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>Gestion des e-mails malveillants dans le dossier indésirable des utilisateurs finaux

1. Demandez aux utilisateurs finaux de signaler l’e-mail comme **hameçonnage** à l’aide du complément Microsoft Message, du complément Phish Microsoft ou des boutons Outlook.
2. Les administrateurs peuvent trier les messages signalés par l’utilisateur à partir du portail de [contenu signalé par l’utilisateur](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
3. À partir de ces messages signalés, les administrateurs peuvent **envoyer à** [Microsoft pour analyse](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) et découvrir pourquoi cet e-mail a été autorisé en premier lieu.
4. Si nécessaire, lors de la soumission à Microsoft à des fins d’analyse, les administrateurs peuvent créer un [bloc pour l’expéditeur](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) afin d’atténuer le problème.
5. Une fois les résultats des soumissions disponibles, lisez le verdict pour comprendre pourquoi les e-mails ont été autorisés et comment la configuration de votre locataire pourrait être améliorée pour éviter que des situations similaires se produisent à l’avenir.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>Gestion des e-mails malveillants qui arrivent dans le dossier de quarantaine des utilisateurs finaux

1. Les utilisateurs finaux reçoivent un [résumé des messages](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) mis en quarantaine conformément aux paramètres activés par les administrateurs.
2. Les utilisateurs finaux peuvent afficher un aperçu des messages en quarantaine, bloquer l’expéditeur et envoyer ces messages à Microsoft pour analyse.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>Gestion des e-mails malveillants qui arrivent dans le dossier de quarantaine des administrateurs

1. Les administrateurs peuvent afficher les e-mails mis en quarantaine (y compris ceux qui demandent l’autorisation de demander la mise en production) à partir de la [page de révision](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. Les administrateurs peuvent envoyer des messages malveillants ou suspects à Microsoft à des fins d’analyse et créer un bloc pour atténuer la situation en attendant le verdict.
3. Une fois les résultats des soumissions disponibles, lisez le verdict pour savoir pourquoi les e-mails ont été autorisés et comment la configuration de votre locataire pourrait être améliorée pour éviter que des situations similaires se produisent à l’avenir.
