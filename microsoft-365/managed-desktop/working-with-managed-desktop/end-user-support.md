---
title: Obtenir la prise en charge des utilisateurs pour Microsoft Manged Desktop
description: Comment les utilisateurs peuvent obtenir de l’aide sur le service et les appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 48be29f8db689ddd0911d7512b267ba50c85a469
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62322406"
---
# <a name="getting-help-for-users"></a>Obtenir de l’aide pour les utilisateurs

Si vous avez atteint le point dans le flux [](../service-description/user-support.md) de travail où vous devez demander l’accès ou l’escalade d’appareil élevé à Microsoft, suivez les étapes suivantes :

>[!NOTE]
>Ces options de prise en charge ne sont pas disponibles pour les appareils du groupe Test.

## <a name="elevation-requests"></a>Demandes d’élévation

Avant de demander un accès élevé à un appareil, il est préférable de passer en revue les actions les mieux adaptées.

| Actions | Exemples |
| ------ | ------ |
| **Les actions classiques** sont destinées au processus de demande d’élévation. Elle est régulièrement effectuée lors de la résolution des problèmes liés Microsoft Manged Desktop appareils mobiles. | <ul><li>Élévation des niveaux des dépannages du système intégrés, de l’invite de commandes Windows PowerShell des applications métiers de dépannage.</li><li>Utilisation d’une solution de contournement pour corriger quelque chose qui doit fonctionner par conception (comme l’activation de BitLocker ou le temps système non mis à jour).</li><li>Élévation de la fonction Gestionnaire de périphériques pour qu’il recherche de nouvelles modifications, telles que les pilotes de mise à jour, la désinstallation d’un appareil ou l’analyse de nouvelles modifications.</li></ul>
| **Actions non recommandées** | <ul><li>Installation de logiciels ou de navigateurs.</li><li>Installation de pilotes en dehors de Windows paramètres, y compris les pilotes pour les périphériques.</li><li>Installation de .msi ou .exe fichiers.</li><li>Installation de Windows fonctionnalités.</li></ul>
| **Actions non prises en charge** | <ul><li>Installation de logiciels ou de fonctionnalités en conflit avec Microsoft Manged Desktop de sécurité ou de gestion ou des opérations.</li><li>Désactivation d’Windows fonctionnalité requise pour Microsoft Manged Desktop, telle que BitLocker.</li><li>Modification des paramètres gérés par votre organisation.</li><ul>

**Pour demander une élévation :**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **Appareils**.
1. Dans la section **Microsoft Manged Desktop**, sélectionnez **Périphériques**, qui contient deux onglets : l’onglet Périphériques et l’onglet **Demandes d’élévation**.
1. Pour créer une demande d’élévation sous l’onglet **Appareil** , sélectionnez un seul appareil à élever.
1. Dans le menu déroulant Actions de l’appareil, sélectionnez **Élévation de la demande**. Un nouveau fly-in de demande d’élévation apparaît avec le nom de l’appareil pré-rempli dans ce champ.
1. À la place, pour créer une demande d’élévation dans l’onglet **Demandes d’élévation,** sélectionnez **+Nouvelle demande d’élévation.**
1. Fournissez les détails ci-après :
    - **ID de ticket de support** : il s’agit de votre propre système de tickets de support.
    - **Nom de l’appareil** : ce n’est que lors de la création d’une demande à partir de **l’onglet Demandes d’élévation** . Entrez le numéro de série de l’appareil, puis sélectionnez l’appareil dans le menu.
    - **Catégorie** : sélectionnez la catégorie qui correspond le mieux à votre problème. Si aucune option ne semble proche, sélectionnez **Autre**. Il est préférable de sélectionner une catégorie si possible.
    - **Titre** : fournissez une brève description du problème sur l’appareil.
    - **Plan d’action** : fournissez les étapes de résolution des problèmes que vous prévoyez d’suivre une fois l’élévation accordée.
1. Sélectionnez **Envoyer**.
1. La liste et les détails de toutes les demandes actives et fermées sont visibles sous l’onglet **Demandes d’élévation** .

## <a name="escalation-requests"></a>Demandes d’escalade

**Pour [faire resserr](../service-description/user-support.md#escalation-portal) un problème à Microsoft :**

1. Connectez-vous [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) et accédez au menu **d’administration du** client.
2. Dans la section Microsoft Manged Desktop, sélectionnez **Demandes de service**.
3. Dans la section **Demandes de** service, **sélectionnez + Nouvelle demande de support**.
4. Fournissez une brève description dans le **champ** Titre. Ensuite, définissez le **type de demande** sur **Incident**.
5. Sélectionnez **la catégorie** et **la sous-catégorie** qui s’adaptent le mieux à votre problème. Puis sélectionnez **Suivant**.
6. Dans la section **Détails** , fournissez les informations suivantes :
    - **Description** : ajoutez des détails supplémentaires qui pourraient aider notre équipe à comprendre le problème. Si vous devez joindre des fichiers, vous pouvez le faire en revenir à la demande après l’avoir soumis.
    - **Informations de contact principales** : fournir des informations sur la façon de contacter la personne principale responsable de l’collaboration avec notre équipe.
7. Sélectionnez **le niveau de** gravité. Pour plus d’informations, voir [définitions de gravité des demandes de support](../working-with-managed-desktop/admin-support.md#support-request-severity-definitions).
8. Fournissez autant d’informations que possible sur la demande pour aider l’équipe à répondre rapidement. En fonction du type de demande, vous pouvez être tenu de fournir des détails différents.
9. Examinez toutes les informations que vous avez fournies pour plus d’informations.
10. Quand vous êtes prêt, sélectionnez **Créer**.
