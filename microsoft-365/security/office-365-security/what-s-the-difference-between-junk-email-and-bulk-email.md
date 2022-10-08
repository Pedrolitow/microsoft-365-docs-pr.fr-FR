---
title: Quelle est la différence entre l’e-mail indésirable et l’e-mail en nombre ?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent découvrir les différences entre le courrier indésirable (courrier indésirable) et le courrier en bloc (courrier gris) dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 6613502c858a87096b4220b17d94b8821b0f9835
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066143"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Quelle est la différence entre le courrier indésirable et le courrier électronique en bloc dans EOP ?

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les clients demandent parfois : « Quelle est la différence entre le courrier indésirable et le courrier en bloc ? » Cette rubrique explique la différence et décrit les contrôles disponibles dans EOP.

- **Le courrier indésirable** est un courrier indésirable, qui sont des messages non sollicités et universellement indésirables (lorsqu’ils sont identifiés correctement). Par défaut, l’EOP rejette le courrier indésirable en fonction de la réputation du serveur de messagerie source. Si un message réussit l’inspection IP source, il est envoyé au filtrage du courrier indésirable. Si le message est classé comme courrier indésirable par filtrage du courrier indésirable, le message est (par défaut) remis aux destinataires prévus et déplacé vers son dossier Junk Email.

  - Vous pouvez configurer les actions à prendre pour les verdicts de filtrage du courrier indésirable. Pour obtenir des instructions, consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

  - Si vous n’êtes pas d’accord avec le verdict de filtrage du courrier indésirable, vous pouvez signaler des messages que vous considérez comme du courrier indésirable ou non indésirable à Microsoft de plusieurs façons, comme décrit dans les [messages et fichiers du rapport à Microsoft](report-junk-email-messages-to-microsoft.md).

- **L’e-mail en bloc** (également appelé _courrier gris_) est plus difficile à classer. Alors que le courrier indésirable est une menace constante, le courrier électronique en bloc est souvent des publicités ponctuelles ou des messages marketing. Certains utilisateurs veulent des messages électroniques en bloc (et en fait, ils se sont volontairement inscrits pour les recevoir), tandis que d’autres utilisateurs considèrent le courrier électronique en bloc comme du courrier indésirable. Par exemple, certains utilisateurs souhaitent recevoir des messages publicitaires de Contoso Corporation ou des invitations à une prochaine conférence sur la cybersécurité, tandis que d’autres utilisateurs considèrent ces mêmes messages comme du courrier indésirable.

  Pour plus d’informations sur la façon dont le courrier électronique en bloc est identifié, consultez le [niveau de réclamation en bloc (BCL) dans EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Gestion des messages électroniques en masse

En raison de la réaction mixte à l’e-mail en bloc, il n’existe pas de conseils universels qui s’appliquent à chaque organisation.

Les stratégies anti-courrier indésirable ont un seuil BCL par défaut qui est utilisé pour identifier les courriers électroniques en bloc comme courrier indésirable. Les administrateurs peuvent augmenter ou diminuer le seuil. Pour plus d’informations, voir les rubriques suivantes :

- [Configurez des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).
- [Paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Une autre option facile à ignorer : si un utilisateur se plaint de recevoir des e-mails en bloc, mais que les messages proviennent d’expéditeurs réputés qui transmettent le filtrage du courrier indésirable dans EOP, faites vérifier par l’utilisateur une option de désabonnement dans le message électronique en bloc.

## <a name="how-to-tune-bulk-email"></a>Comment régler les e-mails en bloc

En septembre 2022, les clients Microsoft Defender pour Office 365 Plan 2 peuvent accéder à BCL à partir de [la chasse avancée](/microsoft-365/security/defender/advanced-hunting-overview). Cette fonctionnalité permet aux administrateurs d’examiner tous les expéditeurs en bloc qui ont envoyé des messages à leur organisation, ainsi que les valeurs BCL correspondantes et le volume de courrier reçu. Vous pouvez explorer les expéditeurs en bloc à l’aide d’autres colonnes de la table **EmailEvents** dans le schéma **de collaboration Email &**. Pour plus d’informations, consultez [EmailEvents](/microsoft-365/security/defender/advanced-hunting-emailevents-table).

Par exemple, si Contoso a défini son seuil en bloc actuel sur 7 dans les stratégies anti-courrier indésirable, les destinataires de Contoso recevront un e-mail de tous les expéditeurs avec BCL \< 7 dans leur boîte de réception. Les administrateurs peuvent exécuter la requête suivante pour obtenir la liste de tous les expéditeurs en bloc de l’organisation :

```console
EmailEvents
| where BulkComplaintLevel >= 1 and Timestamp > datetime(2022-09-XXT00:00:00Z)
| summarize count() by SenderMailFromAddress, BulkComplaintLevel
```

Cette requête permet aux administrateurs d’identifier les expéditeurs souhaités et indésirables. Si un expéditeur en bloc a un score BCL qui ne répond pas au seuil en bloc, les administrateurs peuvent [envoyer les messages de l’expéditeur à Microsoft à des fins d’analyse](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal), ce qui ajoute l’expéditeur en tant qu’entrée verte à la liste d’autorisation/de blocage du locataire.

Les organisations sans plan 2 Defender pour Office 365 peuvent essayer les fonctionnalités de Microsoft 365 Defender pour Office 365 plan 2 gratuitement. Utilisez l’évaluation de Defender pour Office 365 de 90 jours à l’adresse <https://security.microsoft.com/atpEvaluation>. Découvrez qui peut s’inscrire et les conditions d’évaluation [ici](try-microsoft-defender-for-office-365.md) ou vous pouvez utiliser le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) pour identifier les expéditeurs en bloc souhaités et indésirables :

1. Dans le rapport d’état de la protection contre les menaces, sélectionnez **Afficher les données par Email \> Courrier indésirable**. Pour accéder directement au rapport, ouvrez l’une des URL suivantes :

   - EOP: <https://security.microsoft.com/reports/TPSAggregateReport>
   - Defender pour Office 365 :<https://security.microsoft.com/reports/TPSAggregateReportATP>

2. Filtrez les e-mails en bloc, sélectionnez un e-mail à examiner, puis cliquez sur l’entité de messagerie pour en savoir plus sur l’expéditeur. Email entité est disponible uniquement pour les clients Defender pour Office 365 Plan 2.

3. Une fois que vous avez identifié les expéditeurs souhaités et indésirables, ajustez le seuil en bloc au niveau souhaité. S’il existe des expéditeurs en bloc avec un score BCL qui ne correspond pas à votre seuil en bloc, [envoyez les messages à Microsoft à des fins d’analyse](allow-block-email-spoof.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-domains-and-email-addresses-in-the-submissions-portal), ce qui ajoute l’expéditeur en tant qu’entrée d’autorisation à la liste d’autorisation/de blocage du locataire.

Les administrateurs peuvent suivre les [valeurs de seuil en bloc recommandées](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365.md#anti-spam-anti-malware-and-anti-phishing-protection-in-eop) ou choisir une valeur de seuil en bloc qui répond aux besoins de leur organisation.
