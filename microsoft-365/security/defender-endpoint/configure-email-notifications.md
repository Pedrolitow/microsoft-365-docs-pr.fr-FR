---
title: Configurer les notifications d’alerte dans Microsoft Defender pour le point de terminaison
description: Vous pouvez utiliser Microsoft Defender pour le point de terminaison pour configurer les paramètres de notification par courrier électronique pour les alertes de sécurité, en fonction de la gravité et d’autres critères.
keywords: notifications par courrier électronique, configurer les notifications d’alerte, Microsoft Defender pour le point de terminaison, Microsoft Defender pour les notifications de point de terminaison, Microsoft Defender pour les alertes de point de terminaison, Windows 10 Entreprise, Windows 10 Éducation
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c60bed1fb2cc17c9f5dfbd1289ae5f5b5e13faec
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933948"
---
# <a name="configure-alert-notifications-in-microsoft-defender-for-endpoint"></a>Configurer les notifications d’alerte dans Microsoft Defender pour le point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-emailconfig-abovefoldlink)

Vous pouvez configurer Defender pour le point de terminaison pour envoyer des notifications par courrier électronique aux destinataires spécifiés pour les nouvelles alertes. Cette fonctionnalité vous permet d’identifier un groupe de personnes qui seront immédiatement informées et qui pourront agir sur les alertes en fonction de leur gravité.

> [!NOTE]
> Seuls les utilisateurs ayant des autorisations « Gérer les paramètres de sécurité » peuvent configurer des notifications par courrier électronique. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs ayant des rôles Administrateur de sécurité ou Administrateur général peuvent configurer des notifications par courrier électronique.

Vous pouvez définir les niveaux de gravité des alertes qui déclenchent des notifications. Vous pouvez également ajouter ou supprimer des destinataires de la notification par courrier électronique. Les nouveaux destinataires sont avertis des alertes déclenchées après leur ajout. Pour plus d’informations sur les alertes, voir [Afficher et organiser la file d’attente des alertes.](alerts-queue.md)

Si vous utilisez le contrôle d’accès basé sur un rôle (RBAC), les destinataires recevront uniquement des notifications basées sur les groupes d’appareils configurés dans la règle de notification.
Les utilisateurs ayant l’autorisation appropriée peuvent uniquement créer, modifier ou supprimer des notifications limitées à leur étendue de gestion des groupes d’appareils.
Seuls les utilisateurs affectés au rôle d’administrateur général peuvent gérer les règles de notification configurées pour tous les groupes d’appareils.

La notification par courrier électronique inclut des informations de base sur l’alerte et un lien vers le portail où vous pouvez faire des recherches plus approfondies.


## <a name="create-rules-for-alert-notifications"></a>Créer des règles pour les notifications d’alerte
Vous pouvez créer des règles qui déterminent les appareils et les gravités des alertes pour envoyer des notifications par courrier électronique pour les destinataires de la notification.


1. Dans le volet de navigation, sélectionnez **Paramètres**  >  **notifications par courrier électronique.**

2. Cliquez **sur Ajouter un élément.**

3. Spécifiez les informations générales :
    - **Nom de la** règle : spécifiez un nom pour la règle de notification.
    - **Inclure le nom de l’organisation** : spécifiez le nom du client qui apparaît dans la notification par courrier électronique.
    - **Inclure un lien portail propre au client** : ajoute un lien avec l’ID de client pour autoriser l’accès à un client spécifique.
    - **Inclure des informations sur l’appareil** : inclut le nom de l’appareil dans le corps de l’alerte par courrier électronique.
    
        >[!NOTE]
        > Ces informations peuvent être traitées par des serveurs de messagerie destinataire qui ne se trouve pas dans l’emplacement géographique que vous avez sélectionné pour vos données Defender pour le point de terminaison.

    - **Appareils** : choisissez d’avertir les destinataires pour les alertes sur tous les appareils (rôle d’administrateur général uniquement) ou sur des groupes d’appareils sélectionnés. Pour plus d’informations, voir [Créer et gérer des groupes d’appareils.](machine-groups.md)
    - **Gravité de l’alerte** : choisissez le niveau de gravité de l’alerte.

4. Cliquez sur **Suivant**.
    
5. Entrez l’adresse e-mail du destinataire, puis cliquez **sur Ajouter un destinataire.** Vous pouvez ajouter plusieurs adresses e-mail.

6. Vérifiez que les destinataires du courrier électronique peuvent recevoir les notifications par courrier électronique en sélectionnant **Envoyer un message électronique de test.**

7. Cliquez **sur Enregistrer la règle de notification.**

## <a name="edit-a-notification-rule"></a>Modifier une règle de notification
1. Sélectionnez la règle de notification que vous souhaitez modifier.

2. Mettez à jour les informations des onglets Général et Destinataire.

3. Cliquez **sur Enregistrer la règle de notification.**


## <a name="delete-notification-rule"></a>Supprimer une règle de notification

1. Sélectionnez la règle de notification que vous souhaitez supprimer.

2. Cliquez sur **Supprimer**.


## <a name="troubleshoot-email-notifications-for-alerts"></a>Résoudre les problèmes de notifications par courrier électronique pour les alertes
Cette section répertorie les différents problèmes que vous pouvez rencontrer lors de l’utilisation de notifications par courrier électronique pour les alertes.

**Problème :** Les destinataires prévus signalent qu’ils n’ont pas reçu les notifications.

**Solution :** Assurez-vous que les notifications ne sont pas bloquées par des filtres de courrier électronique :

1. Vérifiez que les notifications par courrier électronique defender pour point de terminaison ne sont pas envoyées au dossier Courrier indésirable. Marquez-les comme courrier non indésirable.
2. Vérifiez que votre produit de sécurité de messagerie ne bloque pas les notifications par courrier électronique de Defender for Endpoint.
3. Vérifiez les règles de votre application de messagerie qui peuvent être en train d’capturer et de déplacer vos notifications par courrier électronique Defender for Endpoint.

## <a name="related-topics"></a>Voir aussi
- [Mettre à jour les paramètres de rétention des données](data-retention-settings.md)
- [Configurer des fonctionnalités avancées](advanced-features.md)
