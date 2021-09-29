---
title: Signaler le courrier indésirable, le courrier non indésirable et le hameçonnage à Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: 77b370bcd0a1ee59e80a638669598cf27ef32942
ms.sourcegitcommit: 4b1bf6e4f4a0c016d148cdde7f7880dd774403d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2021
ms.locfileid: "59988906"
---
# <a name="report-messages-and-files-to-microsoft"></a>Signaler les messages et fichiers à Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les utilisateurs et les administrateurs ont plusieurs méthodes différentes pour signaler des messages électroniques et des fichiers à Microsoft.

<br>

****

|Méthode|Description|
|---|---|
|[Utiliser le portail soumissions pour soumettre des courriers indésirables, du hameçonnage, des URL et des fichiers suspectés à Microsoft](admin-submission.md)|La méthode de rapport recommandée pour les administrateurs dans les organisations Exchange Online boîtes aux lettres (non disponible dans EOP autonome).|
|[Activez les modules complémentaires Report Message ou Report Phishing.](enable-the-report-message-add-in.md)|Fonctionne avec Outlook et Outlook sur le web (anciennement Outlook Web App). <p> En fonction de votre abonnement, les messages que les utilisateurs ont signalés avec les modules sont disponibles dans le portail de soumissions d’administration, les résultats de l’examen et de la réponse [automatisés (AIR),](air-view-investigation-results.md)le rapport des [messages](view-email-security-reports.md#user-reported-messages-report) [signalés](admin-submission.md)par l’utilisateur et l’Explorateur. [](threat-explorer-views.md#email--submissions) <p> Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)
|[Signaler les faux positifs et les faux négatifs dans Outlook](report-false-positives-and-false-negatives.md)|Envoyez les faux positifs (e-mails fiables bloqués ou déplacés vers le dossier courrier indésirable) et les faux négatifs (courrier indésirable ou hameçonnage remis dans la boîte de réception) à Exchange Online Protection (EOP) à l’aide de la fonctionnalité Signaler un message.|
|[Envoyer manuellement des messages à Microsoft pour analyse](submit-spam-non-spam-and-phishing-scam-messages-to-microsoft-for-analysis.md)|Envoyez manuellement des messages joints à des adresses de messagerie Microsoft spécifiques pour le courrier indésirable, et non le courrier indésirable et le hameçonnage.|
|[Utiliser des règles de flux de courriers pour afficher les comptes-rendus envoyés par les utilisateurs à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Découvrez comment créer une règle de flux de messagerie (également appelée règle de transport) qui vous avertit lorsque les utilisateurs signalent des messages à Microsoft pour analyse.|
|[Soumettre des programmes malveillants et non malveillants à Microsoft pour analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Utilisez le site Veille de sécurité Microsoft pour envoyer des pièces jointes et d’autres fichiers.|
|

> [!NOTE]
> Les données des soumissions à Microsoft résident dans la limite de conformité Office 365 des centres de données d’Amérique du Nord. Les données sont examinées par les analystes de l’équipe d’ingénierie afin d’améliorer l’efficacité des filtres.
