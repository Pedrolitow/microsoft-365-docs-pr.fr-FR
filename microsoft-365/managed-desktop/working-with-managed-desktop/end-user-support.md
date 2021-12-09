---
title: Obtenir la prise en charge des utilisateurs pour Microsoft Manged Desktop
description: Comment les utilisateurs peuvent obtenir de l’aide sur le service et les appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: d10f2e938e201fa25505abc820d05b03af04e543
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61374411"
---
# <a name="getting-help-for-users"></a>Obtenir de l’aide pour les utilisateurs

Si vous avez atteint le [](../service-description/user-support.md) point dans le flux de travail où vous devez demander l’accès ou l’escalade d’appareil élevé à Microsoft, suivez les étapes suivantes :
 
>[!NOTE]
>Ces options de prise en charge ne sont pas disponibles pour les appareils du groupe Test.

## <a name="elevation-requests"></a>Demandes d’élévation

Avant de demander un accès élevé à un appareil, il est préférable de passer en revue les actions les mieux adaptées.

- **Ce processus** vise généralement à effectuer des actions qui seraient régulièrement effectuées lors de la résolution des problèmes liés Microsoft Manged Desktop appareils mobiles. Les exemples incluent :
    - Élévation des niveaux des dépannages du système intégrés, de l’invite de commandes ou des Windows PowerShell
    - Résolution des problèmes des applications métier
    - Utilisation d’une solution de contournement pour corriger quelque chose qui doit fonctionner par conception (par exemple, l’activation de BitLocker ou le temps système non mis à jour)
    - Élévation de la fonction Gestionnaire de périphériques pour faire des opérations telles que les pilotes de mise à jour, désinstaller un appareil ou analyser les nouvelles modifications

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

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils.**
2. Recherchez la section **Microsoft Manged Desktop,** puis sélectionnez le volet Périphériques,  qui contient deux onglets : l’onglet Périphériques et l’onglet Demandes **d’élévation.**  
3. Pour créer une demande  d’élévation sous l’onglet Appareil, sélectionnez un  seul appareil à élever, puis sélectionnez Demander l’élévation à partir du menu déroulant Actions de l’appareil. Un nouveau volet volant de demande d’élévation s’affiche avec le nom de l’appareil prére implémenté dans ce champ.
4. Sinon, pour créer une demande d’élévation sous l’onglet **Demandes d’élévation,** sélectionnez **+Nouvelle demande d’élévation.**
5. Fournissez les détails ci-après :
    - **ID de ticket de support** à partir de votre propre système de tickets de support.
    - **Nom de l’appareil**(uniquement lors de la création d’une demande à partir de l’onglet **Demandes** d’élévation) : entrez le numéro de série de l’appareil, puis sélectionnez l’appareil dans le menu.
    - **Catégorie**: sélectionnez la catégorie qui correspond le mieux à votre problème. Si aucune option ne semble proche, sélectionnez **Autre**. Il est préférable de sélectionner une catégorie si possible.
    - **Titre**: fournissez une brève description du problème sur l’appareil.
    - **Plan d’action**: fournissez les étapes de résolution des problèmes que vous prévoyez d’suivre une fois l’élévation accordée. 
6. Sélectionnez **Envoyer**.
7. La liste et les détails de toutes les demandes actives et fermées sont visibles sous l’onglet **Demandes d’élévation.**



## <a name="escalation-requests"></a>Demandes d’escalade


Si vous devez faire [une escalade d’un](../service-description/user-support.md#escalation-portal) problème à Microsoft, suivez les étapes suivantes :

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **d’administration du** client.
2. Recherchez la section Microsoft Manged Desktop, puis sélectionnez **Demandes de service.**
3. Dans le bouton **Demandes de service,** **sélectionnez + Nouvelle demande de support.**
4. Fournissez une brève description dans la **zone Titre.** Ensuite, définissez **le type de demande** sur **Incident**. 
5. Sélectionnez **la catégorie** et la **sous-catégorie** qui s’adaptent le mieux à votre **problème,** puis sélectionnez Suivant .
6. Dans la section **Détails,** fournissez les informations suivantes :
    - **Description**: ajoutez tous les détails supplémentaires qui pourraient aider notre équipe à comprendre le problème. Si vous devez joindre des fichiers, vous pouvez le faire en revenir à la demande après l’avoir soumis.
    - **Informations de contact principales**: fournissez des informations sur la façon de contacter la personne principale responsable de l’collaboration avec notre équipe.
7. Sélectionnez **le niveau de** gravité. Pour plus d’informations, voir définitions de gravité des demandes de support.
8. Fournissez autant d’informations que possible sur la demande pour aider l’équipe à répondre rapidement. En fonction du type de demande, vous pouvez être tenu de fournir des détails différents.
9. Examinez toutes les informations que vous avez fournies pour plus d’informations.
10. Quand vous êtes prêt, sélectionnez **Créer**.
