---
title: Notifications de quarantaine (notifications de courrier indésirable de l’utilisateur final) dans Microsoft 365
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
description: Les administrateurs peuvent en savoir plus sur les notifications de courrier indésirable de l’utilisateur final pour les messages mis en quarantaine dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 44ed83a95fe8f588369f0a1bbae4809f32581f87
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043471"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Utiliser des notifications de quarantaine pour publier et signaler des messages mis en quarantaine

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, consultez [messages mis en quarantaine dans EOP](quarantine-email-messages.md).

_Les stratégies de quarantaine_ définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prises en charge). Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md). Les stratégies de quarantaine contrôlent également si les destinataires affectés (y compris les boîtes aux lettres partagées) reçoivent des _notifications de quarantaine périodiques_ concernant leurs messages mis en quarantaine. Les notifications de quarantaine remplacent les notifications de courrier indésirable par l’utilisateur final pour toutes les fonctionnalités de protection prises en charge (pas seulement les verdicts de stratégie anti-courrier indésirable).

Les notifications de quarantaine ne sont pas activées dans les notifications de quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Les notifications de quarantaine sont activées dans la stratégie de quarantaine intégrée nommée NotificationEnabledPolicy [si votre organisation en dispose](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). Sinon, pour activer les notifications de quarantaine dans les stratégies de quarantaine, vous devez [créer et configurer une nouvelle stratégie de quarantaine](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

En outre, pour permettre à l’option « Bloquer l’expéditeur » dans les notifications de quarantaine de fonctionner correctement, les utilisateurs doivent être activés pour PowerShell distant. Pour obtenir des instructions, consultez [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

Les administrateurs peuvent également utiliser les paramètres globaux dans les stratégies de quarantaine pour personnaliser le nom d’affichage de l’expéditeur, le texte d’exclusion de responsabilité dans différentes langues et le logo de l’entreprise utilisé dans les notifications de mise en quarantaine. Pour obtenir des instructions, consultez [Configurer les paramètres de notification de quarantaine globale](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

Pour les boîtes aux lettres partagées, les notifications de mise en quarantaine sont prises en charge uniquement pour les utilisateurs disposant de l’autorisation FullAccess sur la boîte aux lettres partagée. Pour plus d’informations, consultez [Utiliser le CAE pour modifier la délégation de boîte aux lettres partagée](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Par défaut, les messages mis en quarantaine en tant qu’hameçonnage à haut niveau de confiance, les programmes malveillants, les règles de flux de messagerie (également appelées règles de transport) ou les stratégies de Coffre pièces jointes dans Defender pour Office 365 sont uniquement disponibles pour les administrateurs (par défaut, la stratégie de quarantaine AdminOnlyAccessPolicy est utilisée). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).
>
> Les notifications de mise en quarantaine pour les messages envoyés aux groupes de distribution ou aux groupes de sécurité à extension messagerie sont envoyées à tous les membres du groupe.
>
> Les notifications de mise en quarantaine pour les messages envoyés à Groupes Microsoft 365 sont envoyées à tous les membres du groupe uniquement si le paramètre **Envoyer des copies des conversations et des événements de groupe aux membres du groupe** est activé.

Lorsque vous recevez une notification de mise en quarantaine, les informations suivantes sont toujours disponibles pour chaque message mis en quarantaine :

- **Expéditeur** : nom d’envoi et adresse e-mail du message mis en quarantaine.
- **Objet** : texte de la ligne d’objet du message mis en quarantaine.
- **Date** : date et heure (en UTC) auxquelles le message a été mis en quarantaine.

Les actions disponibles dans la notification de quarantaine dépendent de la raison pour laquelle le message a été mis en quarantaine et des autorisations affectées par la stratégie de quarantaine associée. Pour plus d’informations, consultez [les détails de l’autorisation de stratégie de quarantaine](quarantine-policies.md#quarantine-policy-permission-details).

Par défaut, les actions suivantes sont disponibles dans la notification de mise en quarantaine pour les messages qui ont été mis en quarantaine comme courrier indésirable, courrier indésirable à haut niveau de confiance ou en bloc :

- **Bloquer l’expéditeur** : cliquez sur ce lien pour ajouter l’expéditeur à la liste Des expéditeurs bloqués dans _votre_ boîte aux lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Version** : vous pouvez libérer le message ici sans passer en **quarantaine** dans le portail Microsoft 365 Defender.
- **Révision** : cliquez sur ce lien pour accéder à **Quarantaine** dans le portail Microsoft 365 Defender, où vous pouvez (selon la raison pour laquelle le message a été mis en quarantaine) afficher, libérer, supprimer ou signaler vos messages mis en quarantaine. Pour plus d’informations, consultez [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Exemple de notification de mise en quarantaine" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> Un expéditeur bloqué peut toujours vous envoyer des messages électroniques. Tous les messages de cet expéditeur qui sont envoyés à votre boîte aux lettres sont immédiatement déplacés vers le dossier Courrier indésirable. Les messages futurs de cet expéditeur seront envoyés à votre dossier Courrier indésirable ou en quarantaine. Si vous souhaitez supprimer ces messages à l’arrivée au lieu de les mettre en quarantaine, utilisez des [règles de flux de courrier](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) pour supprimer les messages à l’arrivée.
