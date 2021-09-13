---
title: Référence  Stratégies, pratiques et conseils
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ff3f140b-b005-445f-bfe0-7bc3f328aaf0
ms.collection:
- M365-security-compliance
description: Microsoft a développé diverses stratégies, procédures et adopté plusieurs meilleures pratiques du secteur pour protéger nos utilisateurs contre les courriers électroniques abusifs, indésirables ou malveillants.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f1a71b891829a2c9ea31502342c855db4126a6b5
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59203742"
---
# <a name="reference-policies-practices-and-guidelines"></a>Référence : Stratégies, pratiques et conseils

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft s'engage à vous fournir l'expérience utilisateur la plus fiable sur le web. Par conséquent, Microsoft a développé diverses stratégies, procédures et adopté plusieurs meilleures pratiques du secteur pour aider à protéger ses utilisateurs contre les messages abusifs, indésirables ou malveillants. Les expéditeurs qui tentent d’envoyer des courriers électroniques aux utilisateurs doivent s’assurer qu’ils comprennent parfaitement et suivent les instructions de cet article pour vous aider dans cet effort et éviter les problèmes de remise potentiels.

Si vous ne respectez pas ces instructions et stratégies, il se peut que notre équipe de support ne puisse pas vous assister. Si les problèmes de livraison basés sur votre adresse IP d'envoi persistent bien que vous suiviez les instructions, pratiques et stratégies présentées dans cet article, suivez la procédure d'envoi d'une demande de retrait de la liste. Pour obtenir des instructions, voir Utiliser le portail Supprimer de la liste pour vous supprimer de la [liste des expéditeurs bloqués.](use-the-delist-portal-to-remove-yourself-from-the-office-365-blocked-senders-lis.md)

## <a name="general-microsoft-policies"></a>Stratégies générales Microsoft

Les messages électroniques envoyés Microsoft 365 utilisateurs doivent se conformer à toutes les stratégies Microsoft régissant la transmission et l’utilisation des Microsoft 365.

- Conditions d’utilisation applicables aux Microsoft 365 ; en particulier, l’interdiction d’utiliser le service pour le courrier indésirable ou la distribution de programmes malveillants.

- [Contrat de Services Microsoft](https://www.microsoft.com/servicesagreement/)

## <a name="governmental-regulations"></a>Réglementations gouvernementales

Les messages envoyés Microsoft 365 utilisateurs doivent respecter toutes les lois et réglementations applicables en matière de communications électroniques dans la juridiction applicable.

- [CAN-SPAM Act: A Compliance Guide for Business](https://www.ftc.gov/tips-advice/business-center/guidance/can-spam-act-compliance-guide-business)

- ["Remove Me" Responses and Responsibilities: Email Marketers Must Honor "Unsubscribe" Claims](https://www.lawpublish.com/ftc-emai-marketers-unsubscribe-claims.html)

## <a name="technical-guidelines"></a>Instructions techniques

Les messages envoyés Microsoft 365 doivent être conformes aux recommandations applicables répertoriées dans les documents ci-dessous (certains liens sont disponibles uniquement en anglais).

- [RFC 2505: Anti-Spam Recommendations for SMTP MTAs](https://www.ietf.org/rfc/rfc2505.txt)

- [RFC 2920: SMTP Service Extension for Command Pipelining](https://www.ietf.org/rfc/rfc2920.txt)

En outre, les serveurs de messagerie qui se connectent Microsoft 365 doivent respecter les exigences suivantes :

- L'expéditeur doit être conforme à toutes les normes techniques en matière de transmission de messages Internet, tel que publié par The Internet Society's Internet Engineering Task Force (IETF), y compris RFC 5321, RFC 5322, entre autres.

- Une fois qu'un expéditeur a reçu un code de réponse d'erreur SMTP numérique compris entre 500 et 599 (également appelé notification d'échec de remise ou NDR), il ne doit pas essayer de retransmettre ce message à ce destinataire.

- Après plusieurs notifications d'échec de remise, l'expéditeur ne doit plus effectuer de tentatives d'envoi de messages à ce destinataire.

- Les messages ne doivent pas être transmis au moyen de serveurs proxy ou de relais de messagerie non sécurisés.

- Le mécanisme de désabonnement (de listes individuelles ou de toutes les listes hébergées par l'expéditeur) doit être clairement documenté et simple à trouver et à utiliser pour les destinataires.

- Il se peut que les connexions à partir de l'espace IP dynamique ne soient pas acceptées.

- Les serveurs de messagerie doivent avoir des enregistrements DNS inverses valides.

## <a name="reputation-management"></a>Gestion de la réputation

Les expéditeurs, les fournisseurs de services Internet et autres fournisseurs de services doivent gérer activement la réputation de vos adresses IP sortantes.

## <a name="microsoft-365-limits"></a>Microsoft 365 limites

Les expéditeurs doivent respecter Microsoft 365 limites répertoriées dans [Exchange Online Protection limites.](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-limits)

## <a name="email-delivery-resources-and-organizations"></a>Organisations et ressources de remise de courrier électronique

Microsoft collabore activement avec des organismes et fournisseurs de services du secteur afin d'améliorer l'écosystème de la messagerie et d'Internet. Ces organisations ont publié des documents relatifs aux meilleures pratiques que nous soutenons et que nous recommandons aux expéditeurs d'utiliser. Cela améliore votre capacité à remettre des courriers électroniques parmi plusieurs fournisseurs de services de messagerie dans le monde entier.

- [Messaging Malware Mobile Anti-Abuse Working Group](https://www.m3aawg.org/)

- [Online Trust Alliance](https://www.internetsociety.org/ota/)

- [Email Sender & Provider Coalition](https://www.espcoalition.org/)

## <a name="abuse-and-spam-reporting"></a>Création de rapport de courrier indésirable et de mauvaise utilisation

Pour signaler des messages illicites, abusifs, indésirables ou malveillants, reportez-vous [aux messages et fichiers envoyés à Microsoft.](report-junk-email-messages-to-microsoft.md) L’envoi de ces types de communications constitue une violation de la stratégie de Microsoft et des mesures appropriées seront prises sur les rapports confirmés.

## <a name="law-enforcement"></a>Application des lois

Si vous êtes un service chargé de l’application des lois et que vous souhaitez fournir à Microsoft Corporation une documentation juridique concernant Office 365, ou si vous avez des questions concernant une documentation juridique que vous avez envoyée à Microsoft, appelez le (1) (425) 722-1299.