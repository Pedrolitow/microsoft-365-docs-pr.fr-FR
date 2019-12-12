---
title: Corriger les problèmes de remise des courriers électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 06/11/2019
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
ms.openlocfilehash: 9c95a8aa3f2dbc7b44524b4392090f7435d2800b
ms.sourcegitcommit: 5710ce729c55d95b8b452d99ffb7ea92b5cb254a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2019
ms.locfileid: "39970450"
---
# <a name="fix-email-delivery-issues-for-error-code-577xx-in-exchange-online"></a>Corriger les problèmes de remise des courriers électroniques pour le code d’erreur 5.7.7 XX dans Exchange Online

Cette rubrique décrit ce que vous pouvez faire si vous voyez le code d’État 550 5.7.7 XX dans une notification d’échec de remise (également appelée notification de non-remise, message de renvoi, notification d’état de remise ou DSN). Cette notification automatique s’affiche lorsque votre client n’est pas autorisé à envoyer des courriers électroniques de manière unidirectionnelle ou à un autre. Ces codes d’erreur sont généralement les suivants : 705 ou 750.

## <a name="57705-tenant-has-exceeded-threshold-restriction-what-you-need-to-know"></a>5.7.705 : le client a dépassé la restriction de seuil : ce que vous devez savoir

Les expéditeurs internes pouvaient voir cette notification d’échec de remise chaque fois que vous essayez d’envoyer des messages si votre client a été compromis. Cela se occus généralement lorsque la majorité du trafic provenant de votre client a été détectée comme suspecte et a provoqué une interdiction d’envoi pour le client. Cela peut également se produire si vos utilisateurs envoient une grande quantité de courrier en nombre à partir d’Office 365. Comme indiqué dans la description du service, les clients Exchange Online qui doivent envoyer des courriers électroniques commerciaux en bloc légitimes (par exemple, des bulletins d’information clients) doivent utiliser des fournisseurs tiers spécialisés dans ces services.

Une fois que vos utilisateurs ont envoyé une certaine quantité de courrier suspect via le service, en tant que client, tous les utilisateurs peuvent être empêchés d’envoyer des messages jusqu’à ce que le problème soit résolu. Les utilisateurs reçoivent une notification d’échec de remise qui indique :

- 550 5.7.705 accès refusé, le client a dépassé le seuil

## <a name="57750-unregistered-domain-email-restriction-what-you-need-to-know"></a>5.7.750 : restriction de messagerie de domaine non enregistrée : ce que vous devez savoir

Office 365 permet aux clients de relayer certains messages via Exchange Online Protection (EOP). Par exemple, lorsque les utilisateurs disposent d’une boîte aux lettres Office 365 et que quelqu’un les envoie à une boîte aux lettres externe, le transfert de courrier est configuré de manière à ce qu’il redevienne la boîte aux lettres externe de l’utilisateur. Il s’agit le plus souvent dans les environnements d’éducation où les étudiants veulent tirer parti de leur interface de messagerie personnelle mais recevoir des courriers électroniques liés à l’école. Un autre exemple est lorsque les clients sont dans un scénario hybride et disposent de serveurs sur site qui envoient des messages provenant d’EOP.

### <a name="problems-with-unregistered-domains"></a>Problèmes liés aux domaines non enregistrés

Le problème est lié au fait que les serveurs sur site sont compromis et finissent par relayer un volume important de courrier indésirable de EOP. Dans presque tous les cas, les connecteurs corrects sont configurés, mais les courriers électroniques sont envoyés depuis les domaines non enregistrés, également appelés domaines. Office 365 autorise une quantité raisonnable de courrier provenant de domaines non enregistrés, mais un domaine accepté doit être configuré dans le centre d’administration pour chaque domaine que vous envisagez d’envoyer à.

Une fois compromis, les clients ne pourront pas envoyer de messages sortants pour les domaines non enregistrés. Les utilisateurs reçoivent une notification d’échec de remise qui indique :

- 550 5.7.750 service non disponible. Le client a bloqué l’envoi à partir de domaines non enregistrés

## <a name="how-to-unblocking-tenant-in-order-to-send-again"></a>Comment débloquer le client afin de le renvoyer

Il y a plusieurs choses à faire si votre client est bloqué pour l’envoi de messages électroniques :

1. Assurez-vous d’enregistrer tous vos domaines dans le centre d’administration Microsoft 365. Vous trouverez plus d’informations [ici](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).

2. Recherchez les connecteurs inhabituels. Les acteurs malveillants vont souvent créer de nouveaux connecteurs entrants dans votre client Office 365 pour envoyer du courrier indésirable. Vous trouverez plus d’informations sur la vérification de vos connecteurs [ici](https://docs.microsoft.com/powershell/module/exchange/mail-flow/get-inboundconnector).

3. Verrouillez vos serveurs locaux et assurez-vous qu’ils ne sont pas compromis.

   > [!TIP]
   > Il existe de nombreux facteurs impliqués, en particulier s’il s’agit de serveurs tiers. Quelle que soit la fonctionnalité, vous devez être en mesure de confirmer que tout le courrier sortant de vos serveurs est légitime.

4. Une fois la procédure terminée, vous devez appeler le support Microsoft et demander à ce que votre locataire débloquée pour envoyer à nouveau des domaines non enregistrés.  Le fait de fournir le code d’erreur est utile, mais vous devrez prouver que votre environnement est sécurisé et que le courrier indésirable ne sera pas renvoyé. Vous trouverez plus d’informations sur l’ouverture d’un cas de support [ici](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

## <a name="for-more-information"></a>Pour plus d’informations

[Protection contre le courrier indésirable pour Office 365](anti-spam-protection.md)

[Envoyer les notifications d’échec de remise par courrier électronique dans Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online)

Configurer le transfert du courrier pour une boîte aux lettres

[Comment configurer une application ou un périphérique multi-fonction pour envoyer des courriers électroniques à l’aide d’Office 365](https://docs.microsoft.com/Exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-office-3)

[Gérer les domaines acceptés dans Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
