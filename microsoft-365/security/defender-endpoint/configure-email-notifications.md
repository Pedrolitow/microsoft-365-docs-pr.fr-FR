---
title: Configurer des notifications d’alerte dans Microsoft Defender pour point de terminaison
description: Vous pouvez utiliser Microsoft Defender pour point de terminaison pour configurer les paramètres de notification par e-mail pour les alertes de sécurité, en fonction de la gravité et d’autres critères.
keywords: notifications par e-mail, configurer des notifications d’alerte, Microsoft Defender pour point de terminaison, Microsoft Defender pour point de terminaison notifications, Microsoft Defender pour point de terminaison alertes, Windows Entreprise, Windows Éducation
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 7ff95f5ca4f2608a522d075f8e880c2aafa32323
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623760"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Configurer des notifications d’alerte dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-emailconfig-abovefoldlink)

Vous pouvez configurer Defender pour point de terminaison pour envoyer des notifications par e-mail aux destinataires spécifiés pour les nouvelles alertes. Cette fonctionnalité vous permet d’identifier un groupe de personnes qui seront immédiatement informées et peuvent agir sur les alertes en fonction de leur gravité.

Si vous utilisez [Defender entreprise](../defender-business/mdb-overview.md), vous pouvez configurer des notifications par e-mail pour des utilisateurs spécifiques (pas des rôles ou des groupes).

> [!NOTE]
> - Seuls les utilisateurs disposant des autorisations « Gérer les paramètres de sécurité » peuvent configurer des notifications par e-mail. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs dotés de rôles Administrateur de sécurité ou Administrateur général peuvent configurer des notifications par e-mail.
> - La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

Vous pouvez définir les niveaux de gravité d’alerte qui déclenchent des notifications. Vous pouvez également ajouter ou supprimer des destinataires de la notification par e-mail. Les nouveaux destinataires sont avertis des alertes déclenchées après leur ajout. Pour plus d’informations sur les alertes, consultez [Afficher et organiser la file d’attente d’alertes](alerts-queue.md).

Si vous utilisez le contrôle d’accès en fonction du rôle (RBAC), les destinataires reçoivent uniquement des notifications basées sur les groupes d’appareils configurés dans la règle de notification. Les utilisateurs disposant de l’autorisation appropriée peuvent uniquement créer, modifier ou supprimer des notifications limitées à leur étendue de gestion de groupe d’appareils. Seuls les utilisateurs affectés au rôle Administrateur général peuvent gérer les règles de notification configurées pour tous les groupes d’appareils.

La notification par e-mail inclut des informations de base sur l’alerte et un lien vers le portail où vous pouvez effectuer une investigation plus approfondie.

## <a name="create-rules-for-alert-notifications"></a>Créer des règles pour les notifications d’alerte
Vous pouvez créer des règles qui déterminent les appareils et les gravités d’alerte pour envoyer des notifications par e-mail et les destinataires des notifications.

1. Dans le volet de navigation, sélectionnez **Paramètres des** \> **points de terminaison** \> **Général** \> **Email notifications**.

2. Cliquez sur **Ajouter un élément**.

3. Spécifiez les informations générales :
    - **Nom de la règle** : spécifiez un nom pour la règle de notification.
    - **Inclure le nom de l’organisation** : spécifiez le nom du client qui apparaît dans la notification par e-mail.
    - **Inclure un lien de portail spécifique au locataire** : ajoute un lien avec l’ID de locataire pour autoriser l’accès à un locataire spécifique.
    - **Inclure des informations sur l’appareil** : inclut le nom de l’appareil dans le corps de l’alerte par e-mail.

        > [!NOTE]
        > Ces informations peuvent être traitées par des serveurs de messagerie de destinataires qui ne se trouvent pas dans l’emplacement géographique que vous avez sélectionné pour vos données Defender pour point de terminaison.

    - **Appareils** : indiquez si les destinataires doivent recevoir des alertes sur tous les appareils (Administrateur général rôle uniquement) ou sur des groupes d’appareils sélectionnés. Pour plus d’informations, consultez [Créer et gérer des groupes d’appareils](machine-groups.md). (Si vous utilisez [Defender pour Entreprises](../defender-business/mdb-overview.md), les groupes d’appareils ne s’appliquent pas.)
    - **Gravité de l’alerte** : choisissez le niveau de gravité de l’alerte.

4. Cliquez sur **Suivant**.

5. Entrez l’adresse e-mail du destinataire, puis cliquez sur **Ajouter un destinataire**. Vous pouvez ajouter plusieurs adresses e-mail.

6. Vérifiez que les destinataires de l’e-mail peuvent recevoir les notifications par e-mail en sélectionnant **Envoyer un e-mail de test**.

7. Cliquez sur **Enregistrer la règle de notification**.

## <a name="edit-a-notification-rule"></a>Modifier une règle de notification

1. Sélectionnez la règle de notification que vous souhaitez modifier.

2. Mettez à jour les informations de l’onglet Général et Destinataire.

3. Cliquez sur **Enregistrer la règle de notification**.

## <a name="delete-notification-rule"></a>Supprimer une règle de notification

1. Sélectionnez la règle de notification que vous souhaitez supprimer.

2. Cliquez sur **Supprimer**.

## <a name="troubleshoot-email-notifications-for-alerts"></a>Résoudre les problèmes de notifications par e-mail pour les alertes

Cette section répertorie les différents problèmes que vous pouvez rencontrer lors de l’utilisation de notifications par e-mail pour les alertes.

**Problème:** Les destinataires prévus signalent qu’ils ne reçoivent pas les notifications.

**Solution:** Assurez-vous que les notifications ne sont pas bloquées par les filtres d’e-mail :

1. Vérifiez que les notifications par e-mail Defender pour point de terminaison ne sont pas envoyées au dossier Junk Email. Marquez-les comme non indésirables.
2. Vérifiez que votre produit de sécurité par e-mail ne bloque pas les notifications par e-mail de Defender pour point de terminaison.
3. Vérifiez les règles de votre application de messagerie qui peuvent intercepter et déplacer vos notifications par e-mail Defender pour point de terminaison.

## <a name="related-topics"></a>Voir aussi

- [Mettre à jour les paramètres de rétention des données](data-retention-settings.md)
- [Configurer des fonctionnalités avancées](advanced-features.md)
- [Configurer des notifications par e-mail de vulnérabilité dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/configure-vulnerability-email-notifications)
