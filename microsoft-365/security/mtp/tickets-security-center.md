---
title: Créer et suivre des tickets ServiceNow dans le centre de sécurité Microsoft 365
description: Découvrez comment créer et suivre des tickets dans ServiceNow à partir du centre de sécurité Microsoft 365.
keywords: sécurité, Microsoft 365, M365, Secure score, Security Center, ServiceNow, tickets, Tasks
ms.prod: w10
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
ms.openlocfilehash: bd5bf8533d38337c063acdf0dda073e4961e416a
ms.sourcegitcommit: 787b198765565d54ee73972f664bdbd5023d666b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "46867244"
---
# <a name="create-and-track-servicenow-tickets-in-the-microsoft-365-security-center"></a>Créer et suivre des tickets ServiceNow dans le centre de sécurité Microsoft 365

Le [Centre de sécurité Microsoft 365](overview-security-center.md) a été amélioré grâce à la capacité à créer et suivre en mode natif des tickets dans ServiceNow. [En savoir plus sur ServiceNow](https://www.servicenow.com/)

Dans le centre de sécurité, les administrateurs de la sécurité peuvent envoyer une action d’amélioration du [score sécurisé Microsoft](microsoft-secure-score.md) directement à ServiceNow et créer un ticket. Les tickets de gestion des modifications et de gestion des incidents peuvent être créés. Suivez les tickets dans la page d’accueil du centre de sécurité et ServiceNow.

- [**En savoir plus sur les conditions préalables, l’échange de données et la résolution des problèmes**](tickets.md)
- **Gérer les tickets ServiceNow dans le centre de conformité** (bientôt disponible)

## <a name="connect-microsoft-365-security-center-to-servicenow"></a>Connecter le centre de sécurité Microsoft 365 à ServiceNow

Accédez à la page d’accueil du centre de sécurité Microsoft 365 pour afficher la carte de connexion ServiceNow.

![Utilisez-vous ServiceNow](../../media/do-you-use-servicenow-250.png)

Sélectionnez « se connecter à ServiceNow » pour accéder à la page de configuration de ServiceNow. Suivez les instructions pour autoriser l’application Connecteur Microsoft 365.

> [!NOTE]
> Avant d’autoriser la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser le nom d’utilisateur et le mot de passe d’intégration que vous avez créés lors des étapes d’installation. N’utilisez pas vos informations d’identification personnelles.

Une fois que vous avez suivi les instructions et autorisé la connexion, affichez l’état de la connexion dans la page de connexion du centre de sécurité Microsoft 365 et dans l’expérience de l’application ServiceNow Microsoft 365 Ticketing Connector. Vous êtes maintenant prêt à commencer à créer des tâches !

### <a name="troubleshooting"></a>Résolution des problèmes

Découvrez les erreurs courantes que vous pouvez rencontrer dans le processus de connexion et comment les atténuer, dans la [section résolution des problèmes](tickets.md#troubleshooting).

## <a name="create-a-task-and-share-it-to-servicenow"></a>Créer une tâche et la partager avec ServiceNow

Une fois l’intégration configurée, créez des tâches ServiceNow basées sur des actions d’amélioration spécifiques de [Microsoft Secure score](microsoft-secure-score.md) . Accédez à n’importe quelle action d’amélioration de la note de sécurité dans le centre de sécurité Microsoft 365, puis sélectionnez **partager**. L’une des options de liste déroulante est ServiceNow.

Une tâche est générée, dans laquelle vous pouvez définir la priorité et modifier le nom, la description ou la date d’échéance. Une fois que tous les champs obligatoires sont renseignés, envoyez la tâche à ServiceNow.

La tâche est visible dans ServiceNow en tant que demande de modification de la configuration et de la sécurité de Microsoft 365.

## <a name="track-tickets"></a>Suivre les tickets

Une fois les tickets de gestion des modifications et de gestion des incidents créés, ils sont affichés sur les cartes dans la page d’accueil du centre de sécurité Microsoft 365. À partir de ces cartes, vous pouvez créer un ticket, afficher tous les tickets ou gérer la configuration de ServiceNow.

![Tickets de gestion des modifications ServiceNow](../../media/change-management-375.png)  ![Tickets de gestion des incidents ServiceNow](../../media/incident-management-375.png)

Pour réapprovisionner ou gérer votre intégration ServiceNow dans le centre de sécurité Microsoft 365, sélectionnez **gérer la configuration de ServiceNow** sur l’une des cartes. À partir de là, supprimez la connexion ServiceNow actuelle et personnalisez les noms d’état des tickets.

Avec les tickets ServiceNow visibles dans le centre de sécurité Microsoft 365, vos tâches vivent à un endroit où elles peuvent être suivies et traitées parallèlement à vos autres éléments de tableau de bord de sécurité.

## <a name="resources"></a>Ressources

- [En savoir plus sur les conditions préalables, l’échange de données et la résolution des problèmes](tickets.md)
- [Niveau de sécurité Microsoft](microsoft-secure-score.md)