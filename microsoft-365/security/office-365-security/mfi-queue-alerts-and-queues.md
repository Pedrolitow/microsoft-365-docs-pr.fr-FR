---
title: Informations sur les files d’attente dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.custom: ''
ms.localizationpriority: medium
ms.assetid: 37640c80-ce6f-47e2-afd1-bc1d3c50e637
description: Les administrateurs peuvent apprendre à utiliser le widget Files d’attente dans le tableau de bord flux de courrier du Centre de sécurité & conformité pour surveiller les flux de courrier non réussis vers leurs organisations locales ou partenaires sur les connecteurs sortants.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 146ce26c32f1ff80a451b85fd343990db547a131
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972648"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Informations sur les files d’attente dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Lorsque les messages ne peuvent pas être envoyés de votre organisation à vos serveurs de messagerie locaux ou partenaires à l’aide de connecteurs, les messages sont mis en file d’attente dans Microsoft 365. Voici des exemples courants qui provoquent cette condition :

- Le connecteur n’est pas configuré correctement.
- Des modifications ont été apportées à la mise en réseau ou au pare-feu dans votre environnement local.

Microsoft 365 continuera de réessayer de livrer pendant 24 heures. Au bout de 24 heures, les messages expirent et sont retournés aux expéditeurs dans des rapports de non-remise (également appelés notifications de remise de données ou messages de rebond).

Si le volume de courrier en file d’attente dépasse le seuil prédéfini (la valeur par défaut est 200 messages), les informations sont disponibles aux emplacements suivants :

- Informations sur **les files d’attente** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) du [Centre de sécurité & conformité](https://protection.office.com). Pour plus d’informations, consultez [l’aperçu des files d’attente dans la section du tableau de bord flux de](#queues-insight-in-the-mail-flow-dashboard) messagerie de cet article.

- Une alerte s’affiche dans **les alertes récentes** du tableau de bord Alertes dans le [Centre de sécurité & conformité](https://protection.office.com) (**tableau de bord** **alertes** \> ou <https://protection.office.com/alertsdashboard>).

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="Alertes récentes dans le tableau de bord Alertes du Centre de sécurité & conformité" lightbox="../../media/mfi-queued-messages-alert.png":::

- Les administrateurs recevront une notification par e-mail en fonction de la configuration de la stratégie d’alerte par défaut nommée **Messages ont été retardés**. Pour configurer les paramètres de notification pour cette alerte, consultez la section suivante.

  Pour plus d’informations sur les stratégies d’alerte, consultez [Stratégies d’alerte dans le Centre de sécurité & conformité](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Personnaliser les alertes de file d’attente

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), accédez aux **stratégies d’alerte** **d’alerte** \> ou ouvrez <https://protection.office.com/alertpolicies>.

2. Dans la page **Stratégies d’alerte** , recherchez et sélectionnez la stratégie nommée **Messages qui a été retardée**.

3. Dans le **menu volant Message ayant été retardé** qui s’ouvre, vous pouvez activer ou désactiver l’alerte et configurer les paramètres de notification.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="Les détails de l’alerte Messages ont été retardés" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **État** : vous pouvez activer ou désactiver l’alerte.

   - **Destinataires de courrier électronique** et **limite de notification quotidienne** : cliquez sur **Modifier** pour configurer les paramètres suivants :

4. Pour configurer les paramètres de notification, cliquez sur **Modifier**. Dans le menu volant **Modifier la stratégie** qui s’affiche, configurez les paramètres suivants :

   - **Envoyer des notifications par e-mail** : la valeur par défaut est activée.
   - **Destinataires de l’e-mail** : la valeur par défaut est **TenantAdmins**.
   - **Limite de notification quotidienne** : la valeur par défaut est **Aucune limite**.
   - **Seuil** : la valeur par défaut est 200.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="Les paramètres de notification dans les messages ont été une alerte différée" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. Lorsque vous avez terminé, cliquez sur **Enregistrer** et **fermer**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Informations sur les files d’attente dans le tableau de bord de flux de messagerie

Même si le volume de messages en file d’attente n’a pas dépassé le seuil et généré une alerte, vous pouvez toujours utiliser l’insight **Files d’attente** dans le [tableau de bord de flux](mail-flow-insights-v2.md) de courrier pour afficher les messages qui ont été mis en file d’attente pendant plus d’une heure et prendre des mesures avant que le nombre de messages en file d’attente ne devienne trop important.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="Widget Files d’attente dans le tableau de bord Flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-queues-widget.png":::

Si vous cliquez sur le nombre de messages sur le widget, un menu volant Messages **mis en file d’attente** s’affiche avec les informations suivantes :

- **Nombre de messages en file d’attente**
- **Nom du connecteur** : sélectionnez le nom du connecteur pour gérer le connecteur dans le centre d’administration Exchange (EAC) à l’adresse <https://admin.exchange.microsoft.com/#/connectors>.
- **Heure de début de la file d’attente**
- **Les messages les plus anciens ont expiré**
- **Serveur de destination**
- **Dernière adresse IP**
- **Dernière erreur**
- **Guide pratique pour résoudre les** problèmes courants et les solutions disponibles. Si un lien **Correctif est maintenant** disponible, cliquez dessus pour résoudre le problème. Sinon, cliquez sur les liens disponibles pour plus d’informations sur l’erreur et les solutions possibles.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="Détails après avoir cliqué sur l’insight Files d’attente dans le tableau de bord de flux de messagerie" lightbox="../../media/mfi-queues-details.png":::

Le même menu volant s’affiche après que vous avez cliqué sur **Afficher la file d’attente** dans les détails d’une alerte De messages **ayant été retardée** .

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="Les détails de l’alerte messages ont été retardés dans le Centre de sécurité & conformité" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
