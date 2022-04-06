---
title: Notifications Microsoft Defender pour l’identité dans Microsoft 365 Defender
description: Découvrez comment définir Microsoft Defender pour les notifications d’identité dans Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 89ed7ae50bf89c28bde81ea02e8905d0056ede53
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470920"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Notifications Defender pour l’identité dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment travailler avec les notifications [d’identité Microsoft Defender](/defender-for-identity) [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender pour l’identité. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="health-issues-notifications"></a>Notifications de problèmes d’état de santé

Dans Microsoft 365 Defender, vous pouvez ajouter des destinataires pour les notifications par courrier électronique de problèmes d’état de santé dans Defender for Identity.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, go to **Paramètres** and then **Identities**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la colonne Nom" lightbox="../../media/defender-identity/settings-identities.png":::


1. Sélectionnez **les notifications de problèmes d’état d’santé**.

1. Entrez l’adresse e-mail du destinataire. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="L’élément de sous-menu notifications des problèmes d’état" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. Lorsque Defender pour l’identité détecte un problème d’état de santé, les destinataires reçoivent une notification par courrier électronique avec les détails.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="E-mail de problème d’état" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > L’e-mail fournit deux liens pour plus d’informations sur le problème. Vous pouvez soit aller au centre de santé **MDI** , soit au nouveau centre de santé **dans M365D**.

## <a name="alert-notifications"></a>Notifications d’alerte

Dans Microsoft 365 Defender, vous pouvez ajouter des destinataires pour les notifications par courrier électronique des alertes détectées.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, go to **Paramètres** and then **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sélectionnez **notifications d’alerte**.

1. Entrez l’adresse e-mail du destinataire. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="L’élément de sous-menu notifications d’alerte" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>Notifications Syslog

Defender for Identity peut vous avertir lorsqu’il détecte des activités suspectes en envoyant des alertes de sécurité et d’état à votre serveur Syslog via un capteur désigné.

> [!NOTE]
> Pour découvrir comment intégrer Defender for Identity à Microsoft Sentinel, voir [Microsoft 365 Defender’intégration à Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, go to **Paramètres** and then **Identities**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la colonne Nom" lightbox="../../media/defender-identity/settings-identities.png":::

1. **Sélectionnez les notifications Syslog**.

1. Pour activer la notification de syslog, définissez le **basculement du service Syslog** sur **la position activée** .

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="Option de service Syslog qui peut être désactivée" lightbox="../../media/defender-identity/syslog-service.png":::

1. **Sélectionnez Configurer le service**. Un volet s’ouvre et vous permet d’entrer les détails du service de syslog.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="Page sur laquelle vous entrez les détails du service Syslog" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. Entrez les détails suivants :

    - **Capteur** : dans la liste de listes, choisissez le capteur qui enverra les alertes.
    - **Point de terminaison** et **port** du service : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur syslog et spécifiez le numéro de port. Vous ne pouvez configurer qu’un seul point de terminaison Syslog.
    - **Transport** : sélectionnez **le** protocole de transport (TCP ou UDP).
    - **Format** : sélectionnez le format (RFC 3164 ou RFC 5424).

1. **Sélectionnez Envoyer une notification SIEM de test**, puis vérifiez que le message est reçu dans votre solution d’infrastructure Syslog.

1. Sélectionnez **Enregistrer**.

1. Une fois que vous avez configuré le **service Syslog**, vous pouvez choisir les types de notifications (alertes ou problèmes d’état) à envoyer à votre serveur Syslog.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="L’option de vérification de l’option du service Syslog est configurée" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité De Defender pour l’identité](manage-security-alerts.md)
