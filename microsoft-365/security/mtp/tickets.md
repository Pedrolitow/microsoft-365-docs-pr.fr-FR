---
title: Créer et suivre des tickets via ServiceNow
description: Le centre de sécurité Microsoft 365 est optimisé grâce à la capacité à créer et suivre en mode natif des tickets dans ServiceNow. Cela permet aux administrateurs de sécurité d’envoyer une recommandation de score sécurisé directement à ServiceNow et de créer un ticket.
keywords: sécurité, Microsoft 365, M365, Secure score, Security Center, ServiceNow, tickets, Tasks
ms.prod: w10
ms.mktglfcycl: deploy
ms.localizationpriority: medium
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
ms.openlocfilehash: b0b8cda81bb6cec3958e7b2a758da191d803a0ed
ms.sourcegitcommit: acf29701bfba3e4843e49a79fde012f3c7a7024a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "37350328"
---
# <a name="manage-tickets-through-servicenow"></a>Gérer les tickets via ServiceNow

Le centre de sécurité Microsoft 365 est optimisé grâce à la capacité à créer et suivre en mode natif des tickets dans ServiceNow. Cela permet aux administrateurs de sécurité d’envoyer une action d’amélioration de la [note sécurisée Microsoft](microsoft-secure-score.md) directement à ServiceNow et de créer un ticket. Les tickets de gestion des modifications et de gestion des incidents peuvent être créés.

## <a name="prerequisites"></a>Conditions préalables

Avoir accès au centre de sécurité Microsoft 365 et à une instance ServiceNow avec :  

* Kingston ou version ultérieure
* Disposer des informations d’identification d’administrateur AIM
* Disposer des privilèges d’administrateur sur l’instance de votre fournisseur cible

ServiceNow recommande aux utilisateurs de conserver les paramètres par défaut dans votre instance de ServiceNow.  Le fait d’avoir des personnalisations peut provoquer des erreurs lors de la vérification de la liste de contrôle et de l’intégration avec le centre de sécurité Microsoft 365.

## <a name="data-exchange"></a>Échange de données

Lorsque vous connectez le centre de sécurité Microsoft 365 à ServiceNow, Microsoft reçoit les données supplémentaires suivantes :

* Nom de l’instance ServiceNow
* ID client ServiceNow
* Clé secrète client ServiceNow
* Jetons d’accès ServiceNow & d’actualisation

Lorsque vous créez un ticket ServiceNow à partir du centre de sécurité Microsoft 365, les données suivantes sont envoyées à ServiceNow :

* ID d’utilisateur qui initie la création du ticket
* Nom de la tâche
* Description de la tâche
* Priority
* Date d’échéance
* Source de recommandation (recommandation de l’utilisateur ou recommandation de Microsoft)
* Catégorie de recommandation (périphériques, données, applications, identité, infrastructure)

## <a name="connect-microsoft-365-security-center-to-servicenow"></a>Connecter le centre de sécurité Microsoft 365 à ServiceNow

Accédez à la page d’accueil du centre de sécurité Microsoft 365, dans laquelle vous verrez une carte vous demandant si vous utilisez ServiceNow.

![Utilisez-vous ServiceNow](../images/do-you-use-servicenow-250.png)

À partir de là, vous serez redirigé vers la page de configuration de ServiceNow, dans laquelle vous suivrez les instructions pour autoriser l’application de connecteur Microsoft 365.

Lors de l’autorisation de la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser la connexion utilisateur et le mot de passe d’intégration que vous avez créés lors de la procédure d’installation et pas vos informations d’identification personnelles.

Après avoir suivi les instructions et autorisé la connexion, vous pouvez afficher l’état de la connexion sur la page de connexion du centre de sécurité Microsoft 365 et dans l’expérience de l’application ServiceNow Microsoft 365 Ticketing Connector. Vous êtes maintenant prêt à commencer à créer des tâches !

## <a name="create-a-task-and-share-it-to-servicenow"></a>Créer une tâche et la partager avec ServiceNow

Une fois l’intégration configurée, vous pouvez créer des tâches ServiceNow basées sur des actions d’amélioration spécifiques de Microsoft Secure score. Accédez à une action d’amélioration dans le score de sécurité dans le portail du centre de sécurité Microsoft 365, puis sélectionnez l’icône « partager ». L’une des options de liste déroulante est ServiceNow.

![Partage ServiceNow dans le score de sécurité](../images/servicenow-share.png)

Une tâche est ensuite générée, dans laquelle vous pouvez définir la priorité et modifier le nom, la description ou la date d’échéance. Une fois que tous les champs obligatoires sont renseignés, vous pouvez envoyer la tâche à ServiceNow.

La tâche est visible dans ServiceNow en tant que demande de modification de la configuration et de la sécurité de Microsoft 365.

## <a name="track-tickets"></a>Suivre les tickets

Une fois que les tickets de gestion des modifications et de gestion des incidents ont été créés, ils s’afficheront sur les cartes dans la page d’accueil du centre de sécurité Microsoft 365. À partir de ces cartes, vous pouvez créer un ticket, afficher tous les tickets ou gérer la configuration de ServiceNow.

![Tickets de gestion des modifications ServiceNow](../images/change-management-375.png)  ![Tickets de gestion des incidents ServiceNow](../images/incident-management-375.png)

Pour reconfigurer ou gérer votre intégration ServiceNow dans le centre de sécurité Microsoft 365, sélectionnez **gérer la configuration de ServiceNow** sur l’une des cartes. À partir de là, vous pouvez supprimer la connexion ServiceNow actuelle et personnaliser les noms d’état des tickets.

Lorsque les tickets ServiceNow sont visibles dans le centre de sécurité Microsoft 365, vos tâches sont placées dans un endroit où elles peuvent être suivies et traitées parallèlement à vos autres éléments de tableau de bord de sécurité.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="i-am-receiving-an-error-in-the-first-step-of-the-installation-checklist-oauth-creation"></a>Je reçois une erreur dans la première étape de la liste de vérification de l’installation (création OAuth)

**Message d’erreur**: l’opération de lecture sur « oauth_entity » de l’étendue « x_mioms_m365ticket » a été refusée en raison de la stratégie d’accès aux étendues de la table

Notre application part du principe que n’importe quel administrateur de l’instance de ServiceNow peut créer et lire des entités OAuth. Cette erreur peut être due à une personnalisation sur votre instance de ServiceNow, ce qui limite les personnes autorisées à créer/lire des entités OAuth. ServiceNow recommande aux utilisateurs de rester à l’extérieur des fonctionnalités (par défaut).

Définissez les configurations des tables « registres des applications » sur par défaut :

* Label = registres de l’application
* Nom = oauth_entity
* Accessible à partir de = toutes les étendues d’application
* Lecture possible = case à cocher activée

**ServiceNow recommande aux utilisateurs de rester à l’extérieur des fonctionnalités (par défaut).**

### <a name="how-do-i-validate-the-oauth-entity-created-for-microsoft-365-security--compliance-connector"></a>Comment puis-je valider l’entité OAuth créée pour Microsoft 365 Security & Compliance Connector ?

Accédez à la table des registres des applications (menu > système OAuth > application Registry) dans ServiceNow et recherchez l’entité OAuth créée par vous (nom que vous lui avez attribué).

### <a name="how-do-i-validate-the-integration-user-created-in-step-two-of-installation-checklist-for-microsoft-365-security--compliance-connector"></a>Comment puis-je valider l’utilisateur d’intégration créé lors de l’étape 2 de la liste de vérification de l’installation pour Microsoft 365 Security & Compliance Connector ?

Accédez à la table utilisateurs (menu > l’administration des utilisateurs > les utilisateurs) dans ServiceNow et recherchez l’utilisateur d’intégration que vous avez créé (nom que vous lui avez attribué).

Lors de l’autorisation de la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser la connexion utilisateur et le mot de passe d’intégration que vous avez créés lors de la procédure d’installation et pas vos informations d’identification personnelles.

### <a name="i-have-completed-the-installation-and-set-up-steps-but-i-am-unable-to-see-the-servicenow-cards-on-the-home-page-and-cannot-see-the-share-icon-in-microsoft-secure-score"></a>J’ai terminé l’installation et configuré les étapes, mais je ne parviens pas à voir les cartes ServiceNow sur la page d’accueil et je ne vois pas l’icône de partage dans le score de sécurité Microsoft.

Vérifiez l’état de la page de mise en service en accédant à https://security.microsoft.com/ticketProvisioning. Sélectionnez **Enregistrer** et revenir à la page d’accueil. Les cartes doivent apparaître.
