---
title: Notifications de mise en quarantaine (notifications de courrier indésirable pour l’utilisateur final) Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les notifications de courrier indésirable pour les messages mis en quarantaine dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 706303e7bdab7297fbc1dd353238db3542c28177
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465836"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Utiliser les notifications de mise en quarantaine pour libérer et signaler les messages mis en quarantaine

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, [voir Messages mis en quarantaine dans EOP](quarantine-email-messages.md).

_Les stratégies de_ mise en quarantaine définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités pris en charge). Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md). Les polices de mise en quarantaine contrôlent également si les destinataires affectés (y compris les boîtes aux lettres partagées) obtiennent des _notifications périodiques_ de mise en quarantaine concernant leurs messages mis en quarantaine. Les notifications de mise en quarantaine remplacent les notifications de courrier indésirable à l’utilisateur final pour toutes les fonctionnalités de protection prise en charge (et pas seulement les verdicts de stratégie anti-courrier indésirable).

Les notifications de mise en quarantaine ne sont pas allumées dans les notifications de mise en quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Les notifications de mise en quarantaine sont allumées dans la stratégie de mise en quarantaine intégrée nommée NotificationEnabledPolicy si [votre organisation l’a.](quarantine-policies.md#full-access-permissions-and-quarantine-notifications) Dans le cas contraire, pour activer les notifications de mise en quarantaine dans les stratégies de mise en quarantaine, vous devez créer et [configurer une nouvelle stratégie de mise en quarantaine](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

En outre, pour que l’option « Bloquer l’expéditeur » dans les notifications de mise en quarantaine fonctionne correctement, les utilisateurs doivent être activés pour PowerShell à distance. Pour obtenir des instructions, voir [Activer ou désactiver l’accès Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Les administrateurs peuvent également utiliser les paramètres globaux des stratégies de mise en quarantaine pour personnaliser le nom complet de l’expéditeur, le texte de la clause d’exclusion de responsabilité dans différentes langues et le logo de l’entreprise utilisé dans les notifications de mise en quarantaine. Pour obtenir des instructions, voir [Configurer les paramètres globaux de notification de mise en quarantaine](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

Pour les boîtes aux lettres partagées, les notifications de mise en quarantaine sont uniquement pris en charge pour les utilisateurs qui ont une autorisation FullAccess sur la boîte aux lettres partagée. Pour plus d’informations, voir [Utiliser le EAC pour modifier la délégation de boîte aux lettres partagée](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Par défaut, les messages mis en quarantaine comme hameçonnage à haut niveau de confiance, programmes malveillants, par règles de flux de messagerie (également appelées règles de transport) ou stratégies de pièces jointes Coffre dans Defender pour Office 365 sont uniquement disponibles pour les administrateurs (par défaut, la stratégie de mise en quarantaine AdminOnlyAccessPolicy est utilisée). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).
>
> Actuellement, les notifications de mise en quarantaine ne sont pas pris en charge pour les groupes ou les messages de hameçonnage à haut niveau de confiance. 

Lorsque vous recevez une notification de mise en quarantaine, les informations suivantes sont toujours disponibles pour chaque message mis en quarantaine :

- **Expéditeur :** nom d’envoi et adresse e-mail du message mis en quarantaine.
- **Objet** : texte de la ligne d’objet du message mis en quarantaine.
- **Date** : date et heure (au UTC) de mise en quarantaine du message.

Les actions disponibles dans la notification de mise en quarantaine dépendent de la raison pour laquelle le message a été mis en quarantaine et des autorisations attribuées par la stratégie de mise en quarantaine associée. Pour plus d’informations, consultez [les détails de l’autorisation de stratégie de mise en quarantaine](quarantine-policies.md#quarantine-policy-permission-details).

Par défaut, les actions suivantes sont disponibles dans la notification de mise en quarantaine pour les messages mis en quarantaine comme courrier indésirable, courrier indésirable à niveau de confiance élevé ou en bloc :

- **Bloquer l’expéditeur** : cliquez sur ce lien pour ajouter l’expéditeur à la liste des expéditeurs bloqués sur _votre boîte aux_ lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Release** : vous pouvez libérer le message ici sans **passer en quarantaine** dans Microsoft 365 Defender portail.
- **Review**: Click this link to go to **Quarantine** in the Microsoft 365 Defender portal, where you can (depending on why the message was quarantined) view, release, delete or report your quarantined messages. Pour plus d’informations, voir [Rechercher et libérer les messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Exemple de notification de mise en quarantaine" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> Un expéditeur bloqué peut toujours vous envoyer des messages électroniques. Tous les messages provenant de cet expéditeur qui parviennent à votre boîte aux lettres sont immédiatement déplacés vers le dossier Courrier indésirable. Les futurs messages de cet expéditeur seront placés dans votre dossier Courrier indésirable ou mis en quarantaine. Si vous souhaitez supprimer ces messages à l’arrivée au lieu de les mettre en quarantaine, utilisez des règles de flux de [messagerie (également](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) appelées règles de transport) pour supprimer les messages à l’arrivée.
