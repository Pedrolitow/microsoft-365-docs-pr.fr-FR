---
title: Obtenir des notifications d’incident par courrier électronique Microsoft 365 Defender
description: Découvrez comment créer des règles pour obtenir des notifications par courrier électronique pour les incidents Microsoft 365 Defender
keywords: incident, e-mail, notfications de courrier électronique, configurer, utilisateurs, boîte aux lettres, courrier électronique, incidents, analyser, réponse
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 600ff555762112222769fde0372716f4a89a12b9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60209176"
---
# <a name="get-incident-notifications-by-email"></a>Obtenir des notifications d’incident par courrier électronique

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Vous pouvez configurer des Microsoft 365 Defender pour informer votre personnel par courrier électronique des nouveaux incidents ou des mises à jour des incidents existants. Vous pouvez choisir d’obtenir des notifications basées sur :

- Gravité de l’incident.
- Groupe d’appareils.
- Uniquement sur la première mise à jour par incident.

La notification par courrier électronique contient des détails importants sur l’incident, tels que le nom de l’incident, sa gravité et ses catégories, entre autres. Vous pouvez également passer directement à l’incident et démarrer votre analyse immédiatement. Pour plus d’informations, voir [Examiner les incidents.](investigate-incidents.md)

Vous pouvez ajouter ou supprimer des destinataires dans les notifications par courrier électronique. Les nouveaux destinataires sont avertis des incidents après leur ajout. 

>[!NOTE]
>Vous avez besoin de l’autorisation « Gérer les paramètres de sécurité » pour configurer les paramètres de notification par courrier électronique. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs ayant des rôles Administrateur de sécurité ou Administrateur général peuvent configurer des notifications par courrier électronique pour vous. <br> <br>
De même, si votre organisation utilise le contrôle d’accès basé sur un rôle (RBAC), vous pouvez uniquement créer, modifier, supprimer et recevoir des notifications basées sur les groupes d’appareils que vous êtes autorisé à gérer.

## <a name="create-a-rule-for-email-notifications"></a>Créer une règle pour les notifications par courrier électronique

Suivez ces étapes pour créer une règle et personnaliser les paramètres de notification par courrier électronique.

1. Dans le volet de navigation, sélectionnez Paramètres > Microsoft 365 Defender > **notifications d’incident par courrier électronique.**
2. Sélectionnez **Ajouter un élément.**
3. Dans la page **Informations de** base, tapez le nom de la règle et une description, puis sélectionnez **Suivant**.
4. Dans la **page Paramètres de** notification, configurez :
    - **Gravité de l’alerte** : choisissez les gravités d’alerte qui déclencheront une notification d’incident. Par exemple, si vous souhaitez uniquement être informé des incidents de gravité élevée, sélectionnez **Élevé**.
    - **Étendue du groupe d’appareils** : vous pouvez spécifier tous les groupes d’appareils ou sélectionner dans la liste des groupes d’appareils de votre client.
    - **Notifier uniquement lors de la première occurrence par incident** : sélectionnez si vous souhaitez recevoir une notification uniquement sur la première alerte qui correspond à vos autres sélections. Les mises à jour ou alertes ultérieures liées à l’incident n’envoient pas de notifications supplémentaires.
    - **Inclure le nom de l’organisation dans l’e-mail** : sélectionnez si vous souhaitez que le nom de votre organisation apparaisse dans la notification par courrier électronique.
    - **Inclure un lien de portail propre au client** : sélectionnez si vous souhaitez ajouter un lien avec l’ID de client dans la notification par courrier électronique pour accéder à un client Microsoft 365 spécifique.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Paramètres de notification pour les notifications d’incident par courrier électronique.":::

5. Sélectionnez **Suivant**. Dans la page **Destinataires,** ajoutez les adresses de messagerie qui recevront les notifications d’incident. Sélectionnez **Ajouter** après avoir tapé chaque nouvelle adresse de messagerie. Pour tester les notifications et vérifier que les destinataires les reçoivent dans les boîtes de réception, **sélectionnez Envoyer un message électronique de test.** 
6. Sélectionnez **Suivant**. Dans la page **Examiner la règle,** examinez les paramètres de la règle, puis sélectionnez **Créer une règle.** Les destinataires commenceront à recevoir des notifications d’incident par courrier électronique en fonction des paramètres.

Pour modifier une règle existante, sélectionnez-la dans la liste des règles. Dans le volet avec le  nom de la règle, sélectionnez Modifier la règle et a apporté vos modifications dans les pages De **base,** **Paramètres** de notification et **Destinataires.**

Pour supprimer une règle, sélectionnez-la dans la liste des règles. Dans le volet avec le nom de la règle, sélectionnez **Supprimer.**

## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Enquêter sur des incidents](investigate-incidents.md)
