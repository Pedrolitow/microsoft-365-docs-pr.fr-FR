---
title: Obtenir des notifications d’incident dans Microsoft 365 Defender
description: Découvrez comment créer des règles pour obtenir des notifications par courrier électronique pour les incidents dans Microsoft 365 Defender
keywords: incident, e-mail, courrier électronique, notfications, configurer, utilisateurs, boîte aux lettres, e-mail, incidents
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
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
ms.openlocfilehash: 3af1dcfec165c88a18cbc0d8cbf6866bb6398adc
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49668198"
---
# <a name="get-incident-notifications-by-email"></a>Obtenir des notifications d’incident par courrier électronique

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

>[!IMPORTANT]
> La fonctionnalité notifications par courrier électronique pour les incidents est actuellement en préversion publique. Certaines informations sur cette fonctionnalité peuvent changer avant la disponibilité commerciale. Microsoft makes no warranties, express or implied, with respect to the information provided here.

**S’applique à :**
- Microsoft 365 Defender

Vous pouvez configurer Microsoft 365 Defender pour qu’il vous avertisse par courrier électronique chaque fois qu’il y a de nouveaux incidents ou de nouvelles mises à jour apportées aux incidents existants. 

Vous pouvez choisir d’obtenir des notifications en fonction de la gravité de l’incident ou du groupe d’appareils. Vous pouvez également choisir d’obtenir une notification uniquement lors de la première mise à jour par incident.

Vous pouvez ajouter ou supprimer des destinataires dans les notifications par courrier électronique. Les destinataires nouvellement ajoutés reçoivent une notification sur les incidents une fois qu’ils ont été ajoutés. 

La notification par courrier électronique contient des informations importantes sur l’incident, telles que le nom, la gravité et les catégories de l’incident, entre autres. Vous pouvez également accéder directement aux incidents afin de commencer immédiatement votre enquête. Pour plus d’informations sur les incidents, consultez la rubrique [identifier les incidents dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/investigate-incidents).

>[!NOTE]
>Vous avez besoin des autorisations « gérer les paramètres de sécurité » pour configurer les paramètres de notification par courrier électronique. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs disposant de rôles d’administrateur général ou d’administrateur de sécurité peuvent configurer des notifications par courrier électronique pour vous. <br> <br>
De même, si votre organisation utilise le contrôle d’accès basé sur un rôle (RBAC), vous pouvez uniquement créer, modifier, supprimer et recevoir des notifications basées sur les groupes d’appareils que vous êtes autorisé à gérer.

## <a name="create-rules-for-incident-notifications"></a>Créer des règles pour les notifications d’incident

Pour configurer votre première notification par courrier électronique pour les incidents, créez une nouvelle règle et personnalisez les paramètres de notification par courrier électronique.

1. Dans le volet de navigation, sélectionnez **paramètres**  >  **des notifications par courrier électronique des incidents**.
2. Sélectionnez **Ajouter un élément**.
3. Attribuez un **nom à la** règle et fournissez une **Description**.

    ![Fenêtre créer une règle pour le courrier électronique d’incident notifs](../../media/incidentemailnotif1.png) 
4. Sélectionnez **suivant** pour accéder aux **paramètres de notification**. Vous pouvez spécifier les éléments suivants :
    - **Gravité des alertes** : choisissez la gravité d’alerte qui déclenchera une notification d’incident. Par exemple, si vous souhaitez uniquement être informé des incidents de gravité élevée, sélectionnez haute.
    - **Étendue du groupe d’appareils** : cette liste déroulante affiche tous les groupes d’appareils auxquels l’utilisateur peut accéder. Sélectionnez les groupes de périphériques pour lesquels vous créez les règles de notification d’incident.
    - Notification **uniquement lors de la première occurrence par incident** -la sélection de cette option envoie une notification par courrier électronique uniquement sur la première alerte correspondant à vos autres sélections. Les mises à jour ultérieures ou les alertes liées à l’incident ne déclencheront pas de notification.
    - **Inclure le nom** de l’Organisation : indique si le nom du client apparaît dans la notification par courrier électronique ou non.
    - **Inclure le lien portail propre au client** : ajoute un lien avec l’ID de client pour autoriser l’accès à un client spécifique.
    
    ![Fenêtre des paramètres de notification pour le courrier électronique d’incident notifs](../../media/incidentemailnotif2.png)
5. Sélectionnez **suivant** pour accéder à la section **destinataires** . Ici, vous pouvez spécifier les adresses de messagerie qui recevront les notifications par courrier électronique de l’incident. Sélectionnez **Ajouter un destinataire** après avoir tapé toutes les adresses de messagerie.

    ![Fenêtre Ajouter des destinataires pour le courrier électronique d’incident notifs](../../media/incidentemailnotif3.png) 

6. Enfin, sélectionnez **suivant** pour accéder à la **règle de révision** afin de pouvoir voir tous les paramètres associés à votre nouvelle règle. Les destinataires commenceront à recevoir des notifications d’incidents par courrier électronique en fonction des paramètres.

## <a name="see-also"></a>Voir aussi
- [Présentation des incidents dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/incidents-overview)
- [Hiérarchisation des incidents dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue)
- [Enquête sur les incidents dans Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/investigate-incidents)

