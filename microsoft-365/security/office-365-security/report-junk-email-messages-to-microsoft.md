---
title: Signaler les messages de courrier indésirable, non-courrier indésirable et de hameçonnage à Microsoft
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir les différentes façons de signaler les messages corrects et incorrects à Microsoft.
ms.openlocfilehash: 4084d5b9da6f44a2d36a8b573651f4d3bd89d57a
ms.sourcegitcommit: c7f11d851073ef14a69669f6c8b7e0c11e4bb7a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43939486"
---
# <a name="report-messages-and-files-to-microsoft"></a>Signalez les messages et fichiers à Microsoft

Les utilisateurs et administrateurs de Microsoft 365 organisations disposant de boîtes aux lettres dans Exchange Online, ou les organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online disposent de différentes méthodes pour signaler des messages et des fichiers à Microsoft.

|||
|---|---|
|**Méthode**|**Description**|
|[Utilisez la soumission de l’administrateur pour soumettre des courriers indésirables, l’hameçonnage, des URL et des fichiers à Microsoft](admin-submission.md)|Méthode de création de rapports recommandée pour les administrateurs dans les organisations avec des boîtes aux lettres Exchange Online (non disponible dans la version autonome d’EOP).|
|[Activer le complément de message de rapport dans Office 365](enable-the-report-message-add-in.md)|Fonctionne avec Outlook, Outlook pour Mac et Outlook sur le Web (anciennement appelé Outlook Web App) et est le complément recommandé. <br/><br/> En fonction de votre abonnement, les messages que les utilisateurs ont signalés avec le complément sont disponibles dans [le portail de soumission des administrateurs](admin-submission.md), les résultats de l' [enquête et de la réponse (air) automatisés](air-view-investigation-results.md), le [rapport de messages signalés par l’utilisateur](view-email-security-reports.md#user-reported-messages-report)et l’Explorateur de [menaces](threat-explorer-views.md#email--submissions). <br/><br/> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, consultez [la rubrique spécifier une boîte aux lettres pour les soumissions utilisateur de messages de courrier indésirable et de hameçonnage dans Office 365](user-submission.md).|
|[Installer et utiliser le complément de création de rapports de courrier indésirable pour Microsoft Outlook dans Office 365](junk-email-reporting-add-in-for-microsoft-outlook.md)|Fonctionne uniquement dans Outlook.|
|[Signaler les messages de courrier indésirable et de hameçonnage dans Outlook sur le Web dans Office 365](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md)|Utiliser les fonctionnalités intégrées dans Outlook sur le Web pour les organisations avec des boîtes aux lettres Exchange Online (non disponible dans la version autonome d’EOP). <br/><br/> Les messages signalés par les utilisateurs sont disponibles dans [le portail des soumissions de l’administrateur](admin-submission.md). <br/><br/> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, consultez [la rubrique spécifier une boîte aux lettres pour les soumissions utilisateur de messages de courrier indésirable et de hameçonnage dans Office 365](user-submission.md).|
|[Envoi manuel de messages à Microsoft pour analyse](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md)|Envoyer manuellement les messages joints à des adresses de messagerie Microsoft spécifiques pour le courrier indésirable, non le courrier indésirable et le hameçonnage.|
|[Utiliser des règles de flux de messagerie pour voir ce que vos utilisateurs ont signalé à Microsoft](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md)|Découvrez comment créer une règle de flux de messagerie (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft pour analyse.|
|||
|[Soumission de programmes malveillants et non malveillants à Microsoft pour analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Utiliser le site d’intelligence de sécurité Microsoft pour soumettre des pièces jointes et d’autres fichiers.|
|

Si les messages de courrier indésirable ou de hameçonnage ont été mis en quarantaine au lieu d’être remis, les utilisateurs peuvent signaler les messages à Microsoft à partir du portail de mise en quarantaine dans le centre de sécurité & Compliance Center. Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Microsoft 365](find-and-release-quarantined-messages-as-a-user.md).
