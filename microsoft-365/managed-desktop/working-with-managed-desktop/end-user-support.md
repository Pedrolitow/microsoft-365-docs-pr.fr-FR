---
title: Obtenir la prise en charge des utilisateurs pour Microsoft Manged Desktop
description: Comment les utilisateurs peuvent obtenir de l’aide sur le service et les appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: ad3b53a9936fb40c8d699f656f88bf5a3fff20b9
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204908"
---
# <a name="getting-help-for-users"></a>Obtenir de l’aide pour les utilisateurs

Si vous avez atteint le [](../service-description/user-support.md) point dans le flux de travail où vous devez demander l’accès ou l’escalade d’appareil élevé à Microsoft, suivez les étapes suivantes :
 
>[!NOTE]
>Ces options de prise en charge ne sont pas disponibles pour les appareils du groupe Test.

## <a name="elevation-requests"></a>Demandes d’élévation

Avant de demander un accès élevé à un appareil, il est préférable de passer en revue les actions qui conviennent le mieux.

- **Ce processus** est généralement destiné à des actions qui seraient effectuées régulièrement lors de la résolution des problèmes liés Microsoft Manged Desktop appareils mobiles. Les exemples incluent :
    - Élévation des niveaux des dépannages du système intégrés, de l’invite de commandes ou des Windows PowerShell
    - Résolution des problèmes des applications métier
    - Utilisation d’une solution de contournement pour corriger quelque chose qui doit fonctionner par conception (par exemple, l’activation de BitLocker ou le temps système non mis à jour)
    - Élévation de la fonction Gestionnaire de périphériques pour qu’il recherche de nouvelles modifications, telles que la mise à jour des pilotes, la désinstallation d’un appareil ou l’analyse des nouvelles modifications

- **Les actions qui ne sont pas recommandées sont** les suivantes :
    - Installation de logiciels ou de navigateurs
    - Installation de pilotes en dehors des paramètres Windows, y compris ceux des périphériques
    - Installation de .msi ou de .exe fichiers
    - Installation de Windows fonctionnalités

- **Les actions qui ne sont pas prises en charge sont** les suivantes :
    - Installation de logiciels ou de fonctionnalités en conflit avec Microsoft Manged Desktop de sécurité ou de gestion ou des opérations
    - Désactivation d’une Windows requise pour les Microsoft Manged Desktop, telle que BitLocker
    - Modification des paramètres gérés par votre organisation

### <a name="to-request-elevation"></a>Pour demander une élévation

1. Go to the portal at [https://aka.ms/mmdelevationrequest](https://aka.ms/mmdelevationrequest) and sign in with your Azure Active Directory credentials.
2. Sélectionnez **Nouvelle demande d’élévation.**
3. Fournissez les détails ci-après :
    - **ID de ticket de support** à partir de votre propre système de tickets de support.
    - **Nom de l’appareil**: entrez le numéro de série de l’appareil, puis sélectionnez l’appareil dans le menu.
    - **Catégorie**: sélectionnez la catégorie qui correspond le mieux à votre problème. Si aucune option ne semble proche, sélectionnez **Autre**. Il est préférable de sélectionner une catégorie si possible.
    - **Sous-catégorie :** sélectionnez celle qui répond le mieux au problème. Si aucune option ne semble proche, sélectionnez **Autre**.
    - **Titre**: fournissez une brève description du problème sur l’appareil.
    - **Plan d’action**: fournissez les étapes de résolution des problèmes que vous prévoyez de suivre une fois l’élévation accordée. 
4. Sélectionnez **Envoyer**.


## <a name="escalation-requests"></a>Demandes d’escalade


Si vous devez faire [une escalade d’un](../service-description/user-support.md#escalation-portal) problème à Microsoft, suivez les étapes suivantes :

1. Go to the portal at [https://aka.ms/mmdelevationrequest](https://aka.ms/mmdelevationrequest) and sign in with your Azure Active Directory credentials.
2. Sélectionnez **Demandes d’escalade,** puis Nouvelle **demande d’escalade.**
3. Fournissez les détails ci-après :
    - **Catégorie**: sélectionnez la catégorie qui correspond le mieux à votre problème.
    - **Titre**: fournissez une brève description.
    - **Description**: ajoutez tous les détails supplémentaires qui pourraient aider notre équipe à comprendre le problème. Si vous devez joindre des fichiers, vous pouvez le faire en revenir à la demande après l’avoir soumis.
    - **Informations de contact principales**: fournissez des informations sur la façon de contacter la personne principale responsable de l’collaboration avec notre équipe.
4. Sélectionnez **Envoyer**.
5. Revenir sur le ticket dans le même portail pour interagir avec notre équipe.

> [!NOTE]
> Seuls les problèmes de gravité C peuvent être escalades via ce chemin d’accès. Pour d’autres problèmes, contactez votre administrateur informatique pour déposer la demande via le portail d’administration.
