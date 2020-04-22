---
title: Services pour les non clients qui envoient des messages vers Office 365
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/2/2016
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 19fd3e0f-8dbf-4049-a810-2c8ee6cefd48
ms.collection:
- M365-security-compliance
description: Pour préserver la confiance des utilisateurs dans l'utilisation de la messagerie électronique, Microsoft a mis en place diverses stratégies et technologies pour aider à protéger ses utilisateurs.
ms.openlocfilehash: 2d8de601fd24f30c342768b8b27e44248f05b5fe
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43638391"
---
# <a name="services-for-non-customers-sending-mail-to-office-365"></a>Services pour les non clients qui envoient des messages vers Office 365

L'utilisation abusive de la messagerie électronique, les courriers indésirables et les e-mails frauduleux (hameçonnage) continuent à peser sur l'ensemble de l'écosystème de la messagerie. Pour préserver la confiance des utilisateurs dans l'utilisation de la messagerie électronique, Microsoft a mis en place diverses stratégies et technologies pour aider à protéger ses utilisateurs. Cependant, Microsoft comprend que les e-mails légitimes ne doivent pas être affectés négativement. Par conséquent, nous avons établi une suite de services pour aider les expéditeurs à améliorer leur capacité à livrer des courriers électroniques aux utilisateurs de Microsoft 365 en gérant leur réputation d’envoi de manière proactive.

Cette vue d’ensemble fournit des informations sur les avantages que nous fournissons à votre organisation, même si vous n’êtes pas un client.

## <a name="sender-solutions"></a>Solutions de l'expéditeur

|**Service**|**Avantages**|
|:-----|:-----|
|Ce contenu d'aide en ligne| Fournit :  <br/>  Un point de départ pour toutes les questions relatives à la mise à disposition de communications aux utilisateurs EOP  <br/>  Comprend un guide en ligne simple avec nos stratégies et exigences  <br/>  Une présentation des filtres de courrier indésirable et des technologies d'authentification utilisés par Microsoft|
|[Support technique Microsoft](#microsoft-support)|Offre un support autonome et de transmission à une instance supérieure pour les problèmes de remise.|
|[Portail d’adresses IP de blocage du courrier indésirable](#anti-spam-ip-delist-portal)|Un outil permettant d'envoyer une demande de suppression d'adresse IP de la liste. Avant d'envoyer cette demande, il incombe à l'expéditeur de s'assurer que tout autre courrier provenant de l'adresse IP en question n'est pas abusif ou malveillant.|
|[Création de rapport de courrier indésirable et de mauvaise utilisation pour le courrier indésirable provenant d'Exchange Online](#abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online)|Permet de ne pas envoyer le courrier indésirable à partir d'Exchange Online et de ne pas encombrer Internet et votre système de messagerie.|

## <a name="microsoft-support"></a>Support technique Microsoft

Microsoft offre plusieurs options de prise en charge pour les personnes qui rencontrent des problèmes pour envoyer des messages à des boîtes aux lettres Microsoft 365. Nous vous recommandons d'effectuer les actions suivantes :

- Suivez les instructions fournies dans les rapports de non-remise que vous recevez.

- Consultez les problèmes les plus courants que rencontrent les non clients dans [Résolution des problèmes de messages envoyés à Office 365](troubleshooting-mail-sent-to-office-365.md).

- Utilisez le [portail délister Microsoft 365](https://sender.office.com) pour soumettre une demande de suppression de votre adresse IP de la liste des expéditeurs bloqués.

- Lisez les [forums de la communauté Microsoft](https://community.office365.com/f/).

- Contactez le client auquel vous essayez d’envoyer un courrier électronique à l’aide d’une autre méthode et demandez-lui de contacter le support Microsoft et d’ouvrir un ticket de support en votre nom. Dans certains cas, pour des raisons juridiques, le support Microsoft doit communiquer directement avec l'expéditeur qui possède l'espace IP qui est bloqué. Toutefois, les personnes qui ne sont pas des clients ne peuvent généralement pas demander de tickets d'assistance.

  Pour plus d'informations sur le support technique de Microsoft pour Office 365, voir [Prise en charge](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/support).

## <a name="anti-spam-ip-delist-portal"></a>Portail d’adresses IP de blocage du courrier indésirable

Il s’agit d’un portail libre-service que vous pouvez utiliser pour vous supprimer de la liste des expéditeurs bloqués Microsoft 365. Utilisez ce portail si vous recevez un message d’erreur lorsque vous essayez d’envoyer un message électronique à un destinataire dont l’adresse de messagerie est dans Microsoft 365 et que vous ne pensez pas être. Pour plus d’informations, consultez la rubrique [utiliser le portail supprimer de la liste pour vous supprimer de la liste des expéditeurs bloqués](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md).

## <a name="abuse-and-spam-reporting-for-junk-email-originating-from-exchange-online"></a>Création de rapport de courrier indésirable et de mauvaise utilisation pour le courrier indésirable provenant d'Exchange Online

Parfois, Microsoft365 est utilisé par des tiers pour envoyer des courriers indésirables, en violation de nos conditions d’utilisation et de notre stratégie. Si vous recevez un courrier indésirable d’Office 365, vous pouvez signaler ces messages à Microsoft. Pour obtenir des instructions, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).
