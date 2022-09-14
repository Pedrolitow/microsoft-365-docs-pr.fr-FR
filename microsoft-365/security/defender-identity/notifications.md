---
title: notifications Microsoft Defender pour Identity dans Microsoft 365 Defender
description: Découvrez comment définir des notifications Microsoft Defender pour Identity dans Microsoft 365 Defender.
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
search.appverid: met150
ms.openlocfilehash: 7015e87d79a01888a1315de597eecd39263e5d66
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67682302"
---
# <a name="defender-for-identity-notifications-in-microsoft-365-defender"></a>Notifications Defender pour Identity dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment utiliser des notifications [Microsoft Defender pour Identity](/defender-for-identity) dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé à partir de leur emplacement dans le portail Defender pour Identity. Lisez les détails ci-dessous pour découvrir où trouver les fonctionnalités familières et nouvelles.

## <a name="health-issues-notifications"></a>Notifications de problèmes d’intégrité

Dans Microsoft 365 Defender, vous pouvez ajouter des destinataires pour les notifications par e-mail des problèmes d’intégrité dans Defender pour Identity.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **paramètres**, puis **aux identités**.

  :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités dans la colonne Nom" lightbox="../../media/defender-identity/settings-identities.png":::


1. Sélectionnez **les notifications de problèmes d’intégrité**.

1. Entrez l’adresse e-mail du destinataire. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/defender-identity/health-email-recipient.png" alt-text="Élément de sous-menu Notifications des problèmes d’intégrité" lightbox="../../media/defender-identity/health-email-recipient.png":::

1. Lorsque Defender pour Identity détecte un problème d’intégrité, les destinataires reçoivent une notification par e-mail avec les détails.

   :::image type="content" source="../../media/defender-identity/health-email.png" alt-text="E-mail du problème d’intégrité" lightbox="../../media/defender-identity/health-email.png":::

    > [!NOTE]
    > L’e-mail fournit deux liens pour plus d’informations sur le problème. Vous pouvez accéder au **Centre d’intégrité MDI** ou au nouveau Centre de contrôle d’intégrité **dans M365D**.

## <a name="alert-notifications"></a>Notifications d’alerte

Dans Microsoft 365 Defender, vous pouvez ajouter des destinataires pour les notifications par e-mail des alertes détectées.

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **paramètres**, puis **aux identités**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option Identités" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sélectionnez **Notifications d’alerte**.

1. Entrez l’adresse e-mail du destinataire. Sélectionnez **Ajouter**.

   :::image type="content" source="../../media/defender-identity/alert-email-recipient.png" alt-text="Élément de sous-menu Notifications d’alerte" lightbox="../../media/defender-identity/alert-email-recipient.png":::

## <a name="syslog-notifications"></a>Notifications Syslog

Defender pour Identity peut vous avertir lorsqu’il détecte des activités suspectes en envoyant des alertes de sécurité et d’intégrité à votre serveur Syslog via un capteur nommé.

> [!NOTE]
> Pour savoir comment intégrer Defender for Identity à Microsoft Sentinel, consultez [Microsoft 365 Defender intégration à Microsoft Sentinel](/azure/sentinel/microsoft-365-defender-sentinel-integration).

1. Dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, accédez aux **paramètres**, puis **aux identités**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Option d’identités dans la colonne Nom" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sélectionnez **notifications Syslog**.

1. Pour activer la notification syslog, définissez le bouton bascule du **service Syslog** sur la position **activée** .

   :::image type="content" source="../../media/defender-identity/syslog-service.png" alt-text="Option de service Syslog qui peut être activée" lightbox="../../media/defender-identity/syslog-service.png":::

1. Sélectionnez **Configurer le service**. Un volet s’ouvre, où vous pouvez entrer les détails du service syslog.

   :::image type="content" source="../../media/defender-identity/syslog-sensor.png" alt-text="Page sur laquelle vous entrez les détails du service Syslog" lightbox="../../media/defender-identity/syslog-sensor.png":::

1. Entrez les détails suivants :

    - **Capteur** : dans la liste déroulante, choisissez le capteur qui enverra les alertes.
    - **Point de terminaison de service** et **port** : entrez l’adresse IP ou le nom de domaine complet (FQDN) du serveur syslog et spécifiez le numéro de port. Vous ne pouvez configurer qu’un seul point de terminaison Syslog.
    - **Transport** : sélectionnez le protocole **de transport** (TCP ou UDP).
    - **Format** : sélectionnez le format (RFC 3164 ou RFC 5424).

1. Sélectionnez **Envoyer une notification SIEM de test** , puis vérifiez que le message est reçu dans votre solution d’infrastructure Syslog.

1. Sélectionnez **Enregistrer**.

1. Une fois que vous avez configuré le **service Syslog**, vous pouvez choisir les types de notifications (alertes ou problèmes d’intégrité) à envoyer à votre serveur Syslog.

   :::image type="content" source="../../media/defender-identity/syslog-configured.png" alt-text="L’option de configuration du service Syslog est cochée" lightbox="../../media/defender-identity/syslog-configured.png":::

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité Defender pour Identity](manage-security-alerts.md)
