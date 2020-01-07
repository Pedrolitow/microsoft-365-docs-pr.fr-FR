---
title: Corriger les problèmes de remise des courriers électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Découvrez comment résoudre les problèmes liés aux messages électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online (le client a bloqué l’envoi de messages).
ms.openlocfilehash: 69ee2b7d707ae88cca7aa5d4a5f39e8458f6925f
ms.sourcegitcommit: 82baed362528fed30e9e09c6a4a37c07be2f138d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "40959652"
---
# <a name="fix-email-delivery-issues-for-error-code-577xx-in-exchange-online"></a>Corriger les problèmes de remise des courriers électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online

Cette rubrique décrit ce que vous pouvez faire si vous voyez le code d’État 550 5.7.7 XX dans une notification d’échec de remise (également appelée notification de non-remise, message de renvoi, notification d’état de remise ou DSN). Cette notification automatique s’affiche lorsque votre client n’est pas autorisé à envoyer des courriers électroniques de manière unidirectionnelle ou à un autre. Ces codes d’erreur sont généralement les suivants : 705 ou 750.

## <a name="57705-tenant-has-exceeded-threshold-restriction-what-you-need-to-know"></a>5.7.705 : le client a dépassé la restriction de seuil : ce que vous devez savoir

Une fois que vos utilisateurs (collectivement, en tant qu’organisation) envoient une certaine quantité d’e-mails suspects via le service, tous les utilisateurs peuvent être empêchés d’envoyer des courriers jusqu’à ce que le problème soit résolu. Il s’agit généralement du résultat d’un compromis (le plus courant) ou de l’envoi d’un message trop volumineux. Les utilisateurs recevront une notification d’état de remise indiquant :

`550 5.7.705 Access denied, tenant has exceeded threshold`

Dans de rares cas, cela peut également se produire si vous renouvelez votre abonnement une fois qu’il a expiré. Le service doit synchroniser les nouvelles informations de l’abonnement (en général, pas plus d’un jour), mais votre organisation peut ne pas pouvoir envoyer de courrier électronique entre temps. La meilleure façon d’éviter cela est de s’assurer que votre abonnement n’expire pas.

## <a name="57750-unregistered-domain-email-restriction-what-you-need-to-know"></a>5.7.750 : restriction de messagerie de domaine non enregistrée : ce que vous devez savoir

Office 365 permet aux clients de relayer des messages via Exchange Online Protection (EOP). Par exemple:

- Une boîte aux lettres Office 365 reçoit un message provenant d’un expéditeur externe. Le transfert du courrier est configuré sur la boîte aux lettres Office 365, de sorte que le message revient à l’adresse de messagerie externe de l’utilisateur. Ce scénario est le plus courant dans les environnements d’éducation où les étudiants veulent utiliser leurs comptes de messagerie personnels pour afficher les messages liés à l’école.

- Envrionments hybride qui ont des serveurs de messagerie locaux qui envoient des messages sortants via EOP.

### <a name="problems-with-unregistered-domains"></a>Problèmes liés aux domaines non enregistrés

Le problème est lorsque les serveurs de messagerie locaux compromis relaient un grand nombre de courriers indésirables via EOP. Dans presque tous les cas, les connecteurs sont correctement configurés, mais les courriers électroniques sont envoyés à partir de domaines non enregistrés (également appelés domaines non mis en service). Office 365 autorise une quantité raisonnable de courrier électronique provenant de domaines non enregistrés, mais vous devez configurer chaque domaine que vous utilisez pour envoyer des messages électroniques en tant que domaine accepté.

Une fois compromis, les clients ne pourront pas envoyer de messages électroniques sortants pour les domaines non enregistrés. Les utilisateurs recevront une notification d’état de remise indiquant :

`550 5.7.750 Service unavailable. Client blocked from sending from unregistered domains`

## <a name="how-to-unblocking-tenant-in-order-to-send-again"></a>Comment débloquer le client afin de le renvoyer

Il y a plusieurs choses que vous devez faire si votre client est bloqué pour l’envoi de messages électroniques :

1. Vérifiez que tous vos domaines de messagerie sont inscrits. Pour plus d’informations, consultez [la rubrique ajouter un domaine à Office 365](https://docs.microsoft.com/en-us/office365/admin/setup/add-domain) et [gérer les domaines acceptés dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

2. Recherchez les [connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)inhabituels. Les intervenants malveillants créeront souvent de nouveaux connecteurs entrants dans votre organisation Office 365 pour envoyer du courrier indésirable. Pour afficher vos connecteurs existants, consultez la rubrique [Validate Connectors in Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors).

3. Vérifiez les utilisateurs compromis, comme décrit dans [réponse à un compte de messagerie compromis dans Office 365](responding-to-a-compromised-email-account.md).

4. [Activez l’authentification multifacteur](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication) pour tous les administrateurs de votre organisation Office 365.

5. Verrouillez vos serveurs de messagerie locaux et assurez-vous qu’ils ne sont pas compromis.

   > [!TIP]
   > Il existe de nombreux facteurs, en particulier si vous utilisez des serveurs tiers. Quoi qu’il en soit, vous devrez vérifier que tous les messages sortants sont légitimes.

6. Appelez le support Microsoft et demandez-lui de débloquer l’envoi à partir de domaines non enregistrés. Le code d’erreur est utile, mais vous devez prouver que votre environnement a été sécurisé et qu’il ne peut pas envoyer de courrier indésirable. Pour ouvrir un cas de support technique, voir [contacter le support pour les entreprises-aide de l’administrateur](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

## <a name="for-more-information"></a>Pour plus d'informations

[Protection contre le courrier indésirable pour Office 365](anti-spam-protection.md)

[Guide de messagerie en bloc dans la section limites d’envoi de la description du service Exchange Online](https://docs.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits)

[Envoyer les notifications d’échec de remise par courrier électronique dans Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online)

Configurer le transfert du courrier pour une boîte aux lettres

[Comment configurer une application ou un périphérique multi-fonction pour envoyer des courriers électroniques à l’aide d’Office 365](https://docs.microsoft.com/Exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-office-3)

[Gérer les domaines acceptés dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
