---
title: Signaler le courrier indésirable, le courrier non indésirable et le hameçonnage à Microsoft
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir les différentes façons de signaler les messages et fichiers bon et mauvais à Microsoft pour analyse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 52133756ffab28975c1d384c7e455892ce6b0dfc
ms.sourcegitcommit: 537e513a4a232a01e44ecbc76d86a8bcaf142482
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50029173"
---
# <a name="report-messages-and-files-to-microsoft"></a>Signaler les messages et fichiers à Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les utilisateurs et les administrateurs ont plusieurs méthodes différentes pour signaler des messages électroniques et des fichiers à Microsoft.

****

|Méthode|Description|
|---|---|
|[Utilisez la soumission de l’administrateur pour soumettre des courriers indésirables, l’hameçonnage, des URL et des fichiers à Microsoft](admin-submission.md)|Méthode de rapport recommandée pour les administrateurs dans les organisations ayant des boîtes aux lettres Exchange Online (non disponible dans EOP autonome).|
|[Activer le complément Signaler le message](enable-the-report-message-add-in.md)|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <p> En fonction de votre abonnement, les messages que les utilisateurs ont signalés avec le add-in sont disponibles dans [](threat-explorer-views.md#email--submissions)le portail de soumissions d’administration, les résultats d’examen et de réponse [automatisés (AIR),](air-view-investigation-results.md)le rapport des [messages](view-email-security-reports.md#user-reported-messages-report)signalés par l’utilisateur et l’Explorateur de [menaces.](admin-submission.md) <p> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)
|[Activez le complément Signaler un message de hameçonnage](enable-the-report-phish-add-in.md)|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <p> En fonction de votre abonnement, les messages que les utilisateurs ont signalés avec le add-in sont disponibles dans [](threat-explorer-views.md#email--submissions)le portail de soumissions d’administration, les résultats d’examen et de réponse [automatisés (AIR),](air-view-investigation-results.md)le rapport des [messages](view-email-security-reports.md#user-reported-messages-report)signalés par l’utilisateur et l’Explorateur de [menaces.](admin-submission.md) <p> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)|
|[Installer et utiliser le add-in Junk Email Reporting pour Microsoft Outlook](junk-email-reporting-add-in-for-microsoft-outlook.md)|Fonctionne uniquement dans Outlook.|
|[Signaler le courrier indésirable et le hameçonnage dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)|Utilisez les fonctionnalités intégrées dans Outlook sur le web pour les organisations ayant des boîtes aux lettres Exchange Online (non disponibles dans EOP autonome). <p> Les messages que les utilisateurs signalent sont disponibles [dans le portail Soumissions d’administration.](admin-submission.md) <p> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)|
|[Signaler le courrier indésirable et le hameçonnage dans Outlook pour iOS et Android](report-junk-email-and-phishing-scams-in-outlook-for-iOS-and-Android.md)|Utilisez les fonctionnalités intégrées dans Outlook pour iOS et Android pour les organisations avec des boîtes aux lettres Exchange Online (non disponibles dans EOP autonome). <p> Les messages que les utilisateurs signalent sont disponibles [dans le portail Soumissions d’administrateur.](admin-submission.md) <p> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)|
|[Envoyer manuellement des messages à Microsoft pour analyse](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md)|Envoyez manuellement des messages joints à des adresses de messagerie Microsoft spécifiques pour le courrier indésirable, et non le courrier indésirable et le hameçonnage.|
|[Utiliser des règles de flux de messagerie pour voir ce que vos utilisateurs ont signalé à Microsoft](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)|Découvrez comment créer une règle de flux de messagerie (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft pour analyse.
|||
|[Soumettre des programmes malveillants et non malveillants à Microsoft pour analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Utilisez le site Microsoft Security Intelligence pour envoyer des pièces jointes et d’autres fichiers.|

Si le courrier indésirable ou le hameçonnage a été mis en quarantaine au lieu d’être remis, les utilisateurs peuvent signaler les messages à Microsoft à partir du portail de mise en quarantaine dans le Centre de sécurité & conformité. Pour plus d’informations, voir Rechercher et libérer les messages mis en quarantaine en tant [qu’utilisateur dans Microsoft 365.](find-and-release-quarantined-messages-as-a-user.md)
