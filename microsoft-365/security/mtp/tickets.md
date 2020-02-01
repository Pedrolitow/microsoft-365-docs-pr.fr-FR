---
title: Créer et suivre des tickets via ServiceNow
description: Le centre de sécurité Microsoft 365 est optimisé grâce à la capacité à créer et suivre en mode natif des tickets dans ServiceNow. Les administrateurs de la sécurité peuvent envoyer une recommandation de score sécurisé directement à ServiceNow et créer un ticket.
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
ms.openlocfilehash: 26e227b4b1e8047ca962ca9e65b139bacae55e03
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599991"
---
# <a name="manage-tickets-through-servicenow"></a>Gérer les tickets via ServiceNow

Le centre de sécurité Microsoft 365 est optimisé grâce à la capacité à créer et suivre en mode natif des tickets dans ServiceNow. Les administrateurs de la sécurité peuvent envoyer une action d’amélioration de la [note sécurisée Microsoft](microsoft-secure-score.md) directement à ServiceNow et créer un ticket. Les tickets de gestion des modifications et de gestion des incidents peuvent être créés.

## <a name="prerequisites"></a>Conditions préalables

Avoir accès au centre de sécurité Microsoft 365 et à une instance ServiceNow avec :  

* Kingston ou version ultérieure
* Disposer des informations d’identification d’administrateur AIM
* Disposer des privilèges d’administrateur sur l’instance de votre fournisseur cible

ServiceNow recommande que les utilisateurs conservent les paramètres par défaut dans votre instance de ServiceNow. Les personnalisations peuvent entraîner des erreurs lors de la fin de la liste de vérification de l’installation et de l’intégration avec le centre de sécurité Microsoft 365.

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

Accédez à la page d’accueil du centre de sécurité Microsoft 365 pour afficher la carte de connexion ServiceNow.

![Utilisez-vous ServiceNow](../images/do-you-use-servicenow-250.png)

Sélectionnez « se connecter à ServiceNow » pour accéder à la page de configuration de ServiceNow. Suivez les instructions pour autoriser l’application Connecteur Microsoft 365.

> [!NOTE]
> Avant d’autoriser la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser le nom d’utilisateur et le mot de passe d’intégration que vous avez créés lors des étapes d’installation. N’utilisez pas vos informations d’identification personnelles.

Une fois que vous avez suivi les instructions et autorisé la connexion, consultez l’état de la connexion sur la page de connexion du centre de sécurité Microsoft 365 et dans l’expérience de l’application ServiceNow Microsoft 365 Ticketing Connector. Vous êtes maintenant prêt à commencer à créer des tâches !

## <a name="create-a-task-and-share-it-to-servicenow"></a>Créer une tâche et la partager avec ServiceNow

Une fois l’intégration configurée, créez des tâches ServiceNow basées sur des actions d’amélioration spécifiques de Microsoft Secure score. Accédez à une action d’amélioration dans le score de sécurité dans le portail du centre de sécurité Microsoft 365, puis sélectionnez l’icône « partager ». L’une des options de liste déroulante est ServiceNow.

![Partage ServiceNow dans le score de sécurité](../images/servicenow-share.png)

Une tâche est générée, dans laquelle vous pouvez définir la priorité et modifier le nom, la description ou la date d’échéance. Une fois que tous les champs obligatoires sont renseignés, envoyez la tâche à ServiceNow.

La tâche est visible dans ServiceNow en tant que demande de modification de la configuration et de la sécurité de Microsoft 365.

## <a name="track-tickets"></a>Suivre les tickets

Une fois que les tickets de gestion des modifications et de gestion des incidents ont été créés, ils s’affichent sur des cartes dans la page d’accueil du centre de sécurité Microsoft 365. À partir de ces cartes, vous pouvez créer un ticket, afficher tous les tickets ou gérer la configuration de ServiceNow.

![Tickets de gestion des modifications ServiceNow](../images/change-management-375.png)  ![Tickets de gestion des incidents ServiceNow](../images/incident-management-375.png)

Pour reconfigurer ou gérer votre intégration ServiceNow dans le centre de sécurité Microsoft 365, sélectionnez **gérer la configuration de ServiceNow** sur l’une des cartes. À partir de là, supprimez la connexion ServiceNow actuelle et personnalisez les noms d’état des tickets.

Avec les tickets ServiceNow visibles dans le centre de sécurité Microsoft 365, vos tâches vivent à un endroit où elles peuvent être suivies et traitées parallèlement à vos autres éléments de tableau de bord de sécurité.

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="you-receive-an-error-in-the-first-step-of-the-installation-checklist-oauth-creation"></a>Vous recevez une erreur dans la première étape de la liste de vérification de l’installation (création OAuth)

**Message d’erreur**: l’opération de lecture sur « oauth_entity » de l’étendue « x_mioms_m365ticket » a été refusée en raison de la stratégie d’accès aux étendues de la table

L’application part du principe que n’importe quel administrateur de l’instance de ServiceNow peut créer et lire des entités OAuth. Cette erreur peut être due à une personnalisation sur votre instance de ServiceNow, ce qui limite les personnes autorisées à créer/lire des entités OAuth.

**ServiceNow recommande que les utilisateurs conservent les fonctionnalités par défaut.**

Définissez les configurations des tables « registres des applications » sur par défaut :

* Label = registres de l’application
* Nom = oauth_entity
* Accessible à partir de = toutes les étendues d’application
* Lecture possible = case à cocher activée

### <a name="how-to-validate-the-oauth-entity-created-for-microsoft-365-security--compliance-connector"></a>Procédure de validation de l’entité OAuth créée pour Microsoft 365 Security & Compliance Connector

Accédez à la table des registres des applications (**Menu > système oauth > application Registry**) dans ServiceNow et recherchez l’entité OAuth créée par vous, avec le nom que vous lui avez attribué.

### <a name="logging-in-as-the-integration-user"></a>Connexion en tant qu’utilisateur de l’intégration

Avant d’autoriser la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser le nom d’utilisateur et le mot de passe d’intégration que vous avez créés lors des étapes d’installation. N’utilisez pas vos informations d’identification personnelles.

1. Accédez à la page Authorization (autorisation) dans ServiceNow.
2. Si vous êtes connecté avec vos informations d’identification personnelles, sélectionnez le lien qui ne se trouve **pas** dans le coin supérieur droit.
3. Connectez-vous à ServiceNow en tant qu’utilisateur d’intégration que vous avez créé précédemment à partir de la liste de vérification d’installation.  
4. Sélectionnez **autoriser** dans la page ServiceNow pour demander si le connecteur sécurité + conformité peut se connecter à votre compte ServiceNow.
5. Suivez les étapes de configuration.

### <a name="how-to-validate-the-integration-user-created-with-the-installation-checklist-for-microsoft-365-security--compliance-connector"></a>Procédure de validation de l’utilisateur d’intégration créé avec la liste de vérification d’installation pour le connecteur de sécurité & conformité Microsoft 365

Accédez à la table utilisateurs **(Menu > l’administration des utilisateurs > les utilisateurs**) dans ServiceNow et recherchez l’utilisateur d’intégration que vous avez créé, avec le nom que vous lui avez attribué.

### <a name="your-company-has-single-sign-on-enabled-which-prevents-you-from-connecting-to-servicenow-through-the-microsoft-365-security-center"></a>Votre entreprise a activé l’authentification unique, ce qui vous empêche de vous connecter à ServiceNow via le centre de sécurité Microsoft 365

Si votre entreprise a activé l’authentification unique et que vous recevez une erreur ou si la connexion échoue, suivez l’une des deux solutions.

#### <a name="log-into-servicenow-as-the-integration-user"></a>Connectez-vous à ServiceNow en tant qu’utilisateur d’intégration.

1. Revenez à la page autorisation dans ServiceNow.
2. Sélectionnez le lien qui **n’est pas** dans le coin supérieur droit.
3. Connectez-vous à ServiceNow en tant qu’utilisateur d’intégration que vous avez créé précédemment à partir de la liste de vérification d’installation.  
4. Sélectionnez **autoriser** dans la page ServiceNow pour demander si le connecteur sécurité + conformité peut se connecter à votre compte ServiceNow.
5. Suivez les étapes de configuration.

#### <a name="create-a-security-admin-user"></a>Créer un utilisateur d’administrateur de sécurité

1. Créez un utilisateur avec des privilèges d’administrateur de sécurité dans Azure Active Directory. L’utilisateur doit avoir les mêmes nom et adresse de messagerie que l’utilisateur d’intégration que vous avez créé à partir de la liste de vérification d’installation. Vous pouvez supprimer le rôle d’administrateur de sécurité une fois la connexion et la connexion terminées.
2. Connectez-vous au centre de sécurité Microsoft 365 en tant qu’utilisateur et suivez les étapes de configuration.

### <a name="installation-is-complete-but-dont-see-tickets-and-cant-share"></a>L’installation est terminée, mais ne vois pas les tickets et ne peut pas partager

Si les étapes d’installation et de configuration sont terminées, mais que vous ne voyez pas les cartes ServiceNow sur la page d’accueil et que vous ne pouvez pas partager de ServiceNow à partir du score de sécurité https://security.microsoft.com/ticketProvisioningMicrosoft, vérifiez l’état de la page de mise en service sur. Sélectionnez **autoriser** et revenir à la page d’accueil. Les cartes doivent apparaître.

