---
title: Répondre à un connecteur compromis dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Découvrez comment reconnaître et répondre à un connecteur compromis dans Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 8552c0d6181e17c460e3fd6a4db0daa400e4f828
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67496980"
---
# <a name="respond-to-a-compromised-connector"></a>Répondre à un connecteur compromis

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les connecteurs sont utilisés pour activer le flux de messagerie entre Microsoft 365 ou Office 365 et les serveurs de messagerie que vous avez dans votre environnement local. Pour plus d'informations, voir [Configurer le flux de messagerie à l'aide de connecteurs dans Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

Un connecteur entrant compromis est défini comme lorsqu’une personne non autorisée applique des modifications à un connecteur entrant existant ou crée un connecteur entrant dans un locataire Microsoft 365, avec l’intention d’envoyer du courrier indésirable ou des e-mails hameçons. Notez que cela s’applique uniquement aux connecteurs entrants de type OnPremises. 

## <a name="detect-a-compromised-connector"></a>Détecter un connecteur compromis

Voici quelques-unes des caractéristiques d’un connecteur compromis :

- Pic soudain du volume de courrier sortant. 

- Incompatibilité entre les expéditeurs P1 et P2 dans les messages sortants. Pour plus d’informations sur les expéditeurs P1 et P2, consultez [comment EOP valide l’adresse From pour empêcher le hameçonnage](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

- Courriers sortants envoyés à partir d’un domaine qui n’est pas approvisionné ou inscrit. 

- Le connecteur n’est pas autorisé à envoyer des messages de relais. 

- La présence d’un connecteur entrant n’a pas été créée par l’utilisateur ou l’administrateur prévu. 

- Modifications non autorisées dans la configuration du connecteur existante, telles que le nom, le nom de domaine et l’adresse IP. 

- Un compte d’administrateur récemment compromis. Notez que vous ne pouvez modifier la configuration du connecteur que si vous disposez d’un accès administratif. 

## <a name="secure-and-restore-email-function-to-a-suspected-compromised-connector"></a>Sécuriser et restaurer la fonction e-mail sur un connecteur suspecté compromis

Vous devez effectuer toutes les étapes suivantes pour récupérer l’accès à votre connecteur. Ces étapes vous aident à supprimer toutes les entrées de porte d’entrée qui peuvent avoir été ajoutées à votre connecteur.

### <a name="step-1-identify-if-an-inbound-connector-has-been-compromised"></a>Étape 1 : Identifier si un connecteur entrant a été compromis 

#### <a name="review-recent-suspicious-connector-traffic-or-related-messages"></a>Examiner le trafic de connecteur suspect récent ou les messages connexes

Si vous avez [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md), accédez directement à https://security.microsoft.com/threatexplorer. 

1. Sélectionnez **connecteur**, insérez **le nom du connecteur**, sélectionnez la plage de dates, puis cliquez sur **Actualiser**. 

    :::image type="content" source="../../media/connector-compromise-explorer.png" alt-text="Vue de l’Explorateur de connecteurs entrants" lightbox="../../media/connector-compromise-explorer.png":::

2. Identifiez s’il existe un pic anormal ou une baisse du trafic de messagerie.

    :::image type="content" source="../../media/connector-compromise-abnormal-spike.png" alt-text="Nombre d’e-mails remis au dossier indésirable" lightbox="../../media/connector-compromise-abnormal-spike.png":::

3. Identifier: 

    - Si **l’adresse IP de l’expéditeur** correspond à l’adresse IP locale de votre organisation. 

    - Si un nombre important d’e-mails ont été récemment envoyés au dossier **Courrier indésirable** . Il s’agit d’un bon indicateur de l’utilisation d’un connecteur compromis pour envoyer du courrier indésirable. 

    - Si les destinataires sont les destinataires avec qui votre organisation reste généralement en contact. 

    :::image type="content" source="../../media/connector-compromise-sender-ip.png" alt-text="Adresse IP de l’expéditeur et adresse IP locale de votre organisation" lightbox="../../media/connector-compromise-sender-ip.png":::

Si vous avez [Microsoft Defender pour Office 365 plan 1](defender-for-office-365.md) ou [Exchange Online Protection](exchange-online-protection-overview.md), accédez à https://admin.exchange.microsoft.com/#/messagetrace. 

1. Ouvrez l’alerte **d’activité suspecte du connecteur** dans https://security.microsoft.com/alerts.  

2. Sélectionnez une activité dans la **liste d’activités**, puis copiez le **domaine de connecteur** suspect et l’adresse **IP** détectées dans l’alerte.

    :::image type="content" source="../../media/connector-compromise-outbound-email-details.png" alt-text="Détails des e-mails sortants compromis par le connecteur" lightbox="../../media/connector-compromise-outbound-email-details.png":::
    
3. Effectuez une recherche à l’aide d’un **domaine de connecteur** et d’une **adresse IP** dans la [**trace des messages**](https://admin.exchange.microsoft.com/#/messagetrace). 

    :::image type="content" source="../../media/connector-compromise-new-message-trace.png" alt-text="Nouveau menu volant de suivi des messages" lightbox="../../media/connector-compromise-new-message-trace.png":::
    
4. Dans les résultats de la recherche de **trace** de message, identifiez : 

    - Si un nombre important d’e-mails ont été récemment **marqués comme FilteredAsSpam**. Il s’agit d’un bon indicateur de l’utilisation d’un connecteur compromis pour envoyer du courrier indésirable. 

    - Si les destinataires sont les destinataires avec qui votre organisation reste généralement en contact. 

    :::image type="content" source="../../media/connector-compromise-message-trace-results.png" alt-text="Nouveaux résultats de recherche de trace de messages" lightbox="../../media/connector-compromise-message-trace-results.png":::

#### <a name="investigate-and-validate-connector-related-activity"></a>Examiner et valider l’activité liée au connecteur 

Utilisez la ligne de commande suivante dans PowerShell pour examiner et valider l’activité liée au connecteur par un utilisateur dans le journal d’audit. Pour plus d’informations, consultez [Utiliser un script PowerShell pour rechercher dans le journal d’audit](/compliance/audit-log-search-script). 

```powershell
Search-UnifiedAuditLog -StartDate "<ExDateTime>" -EndDate "<ExDateTime>" -Operations "New-InboundConnector", "Set-InboundConnector", "Remove-InboundConnector
```

### <a name="step-2-review-and-revert-unauthorized-changes-in-a-connector"></a>Étape 2 : Examiner et rétablir les modifications non autorisées dans un connecteur 

1. https://admin.exchange.microsoft.com/Connectez-vous . 

2. Passez en revue et rétablissez les modifications de connecteur non autorisées. 

### <a name="step-3-unblock-the-connector-to-re-enable-mail-flow"></a>Étape 3 : Débloquer le connecteur pour réactiver le flux de messagerie 

1. https://security.microsoft.com/restrictedentitiesConnectez-vous . 

2. Sélectionnez le connecteur restreint pour débloquer le connecteur. 

### <a name="step-4-investigate-and-remediate-potentially-compromised-administrative-user-account"></a>Étape 4 : Examiner et corriger un compte d’utilisateur administratif potentiellement compromis

Si un utilisateur avec une activité de connecteur non autorisée est identifié, vous pouvez examiner cet utilisateur pour trouver une compromission potentielle. Pour plus d’informations, voir [Répondre à un compte de messagerie compromis](responding-to-a-compromised-email-account.md).

## <a name="more-information"></a>Informations supplémentaires

- [Supprimer les connecteurs bloqués](remove-blocked-connectors.md)
- [Supprimer les utilisateurs bloqués](removing-user-from-restricted-users-portal-after-spam.md)
