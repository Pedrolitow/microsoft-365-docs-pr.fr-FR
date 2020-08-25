---
title: Intégration des tickets ServiceNow dans le centre de sécurité et le centre de sécurité Microsoft 365
description: Découvrez comment créer et suivre des tickets dans ServiceNow à partir du centre de sécurité et du centre de sécurité Microsoft 365.
keywords: sécurité, Microsoft 365, M365, conformité, centre de conformité, centre de sécurité, ServiceNow, tickets, tâches, neige, connexion
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
ms.openlocfilehash: 12ac7d0a3d07749e16443e645f50de8fda185658
ms.sourcegitcommit: 787b198765565d54ee73972f664bdbd5023d666b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "46866778"
---
# <a name="integrate-servicenow-tickets-into-the-microsoft-365-security-center-and-compliance-center"></a>Intégration des tickets ServiceNow dans le centre de sécurité et le centre de sécurité Microsoft 365

[!include[Prerelease information](../includes/prerelease.md)]

ServiceNow est une plateforme de Cloud Computing populaire qui permet aux entreprises de gérer les flux de travail numériques pour les opérations d’entreprise. La plate-forme actuelle possède des flux de travail informatiques, des flux de travail d’employés et des flux de travail client. [En savoir plus sur ServiceNow](https://www.servicenow.com/)

Microsoft s’est associé à ServiceNow pour permettre aux administrateurs informatiques de gérer plus facilement leurs tickets et leurs tâches sur les deux plateformes. Le centre de [sécurité microsoft 365](overview-security-center.md) et le [Centre de conformité Microsoft 365](https://docs.microsoft.commicrosoft-365/compliance/microsoft-365-compliance-center) sont en cours d’amélioration avec la possibilité de créer et suivre en mode natif des tickets dans ServiceNow.

- [**Gérer les tickets ServiceNow dans le centre de sécurité**](tickets-security-center.md)
- **Gérer les tickets ServiceNow dans le centre de conformité** (bientôt disponible)

## <a name="prerequisites"></a>Conditions préalables

Avoir accès au centre de sécurité Microsoft 365 ou au centre de conformité et une instance ServiceNow avec :  

* Kingston ou version ultérieure
* Disposer des informations d’identification d’administrateur AIM
* Disposer des privilèges d’administrateur sur l’instance de votre fournisseur cible

ServiceNow recommande que les utilisateurs conservent les paramètres par défaut dans votre instance de ServiceNow. Les personnalisations peuvent entraîner des erreurs lors de la fin de la liste de vérification de l’installation et de l’intégration avec le centre de sécurité Microsoft 365.

## <a name="data-exchange"></a>Échange de données

Lorsque vous connectez le centre de sécurité Microsoft 365 ou le centre de conformité à ServiceNow, Microsoft reçoit les données supplémentaires suivantes :

* Nom de l’instance ServiceNow
* ID client ServiceNow
* Clé secrète client ServiceNow
* Jetons d’accès ServiceNow & d’actualisation

Lorsque vous créez un ticket ServiceNow à partir du centre de sécurité Microsoft 365 ou du centre de conformité, les données suivantes sont envoyées à ServiceNow :

* ID d’utilisateur qui initie la création du ticket
* Nom de la tâche
* Description de la tâche
* Priorité
* Date d’échéance
* Source de recommandation (recommandation de l’utilisateur ou recommandation de Microsoft)
* Catégorie de recommandation (périphériques, données, applications, identité, infrastructure)

## <a name="connect-to-servicenow"></a>Se connecter à ServiceNow

Pour savoir comment vous connecter à ServiceNow, accédez à [la création et au suivi des tickets ServiceNow dans le centre de sécurité Microsoft 365](tickets-security-center.md) . La connexion à partir du centre de conformité Microsoft 365 sera bientôt disponible.

## <a name="troubleshooting"></a>Résolution des problèmes

### <a name="you-receive-an-error-in-the-first-step-of-the-installation-checklist-oauth-creation"></a>Vous recevez une erreur dans la première étape de la liste de vérification de l’installation (création OAuth)

**Message d’erreur**: l’opération de lecture sur « oauth_entity » de l’étendue « x_mioms_m365ticket » a été refusée en raison de la stratégie d’accès entre les étendues de la table

L’application part du principe que n’importe quel administrateur de l’instance de ServiceNow peut créer et lire des entités OAuth. Cette erreur peut être due à une personnalisation dans votre instance de ServiceNow qui limite la création ou la lecture d’entités OAuth.

**ServiceNow recommande que les utilisateurs conservent les fonctionnalités par défaut.**

Définissez les configurations des tables « registres des applications » sur par défaut :

* Label = registres de l’application
* Nom = oauth_entity
* Accessible à partir de = toutes les étendues d’application
* Lecture possible = case à cocher activée

### <a name="how-to-validate-the-oauth-entity-created-for-microsoft-365-security--compliance-connector"></a>Procédure de validation de l’entité OAuth créée pour Microsoft 365 Security & Compliance Connector

Accédez à la table des registres des applications (**Menu > système OAuth > application Registry**) dans ServiceNow. Recherchez l’entité OAuth que vous avez créée, avec le nom que vous lui avez attribué.

### <a name="signing-in-as-the-integration-user"></a>Connexion en tant qu’utilisateur de l’intégration

Avant d’autoriser la connexion entre le centre de sécurité Microsoft 365 et ServiceNow, veillez à utiliser la connexion et le mot de passe de l’utilisateur d’intégration que vous avez créé lors de la procédure d’installation. N’utilisez pas vos informations d’identification personnelles.

1. Accédez à la page Authorization (autorisation) dans ServiceNow.
2. Si vous êtes connecté avec vos informations d’identification personnelles, sélectionnez le lien **pas** dans le coin supérieur droit.
3. Connectez-vous à ServiceNow en tant qu’utilisateur d’intégration que vous avez créé précédemment à partir de la liste de vérification d’installation.  
4. Sélectionnez **autoriser** dans la page ServiceNow pour demander si le connecteur sécurité + conformité peut se connecter à votre compte ServiceNow.
5. Poursuivez la procédure de configuration.

### <a name="how-to-validate-the-integration-user-created-with-the-installation-checklist-for-microsoft-365-security--compliance-connector"></a>Procédure de validation de l’utilisateur d’intégration créé avec la liste de vérification d’installation pour le connecteur de sécurité & conformité Microsoft 365

Accédez à la table utilisateurs **(Menu > l’administration des utilisateurs > les utilisateurs**) dans ServiceNow et recherchez l’utilisateur d’intégration que vous avez créé, avec le nom que vous lui avez attribué.

### <a name="your-company-has-single-sign-on-enabled-which-prevents-you-from-connecting-to-servicenow-through-the-microsoft-365-security-center"></a>Votre entreprise a activé l’authentification unique, ce qui vous empêche de vous connecter à ServiceNow via le centre de sécurité Microsoft 365

Si votre entreprise a activé l’authentification unique et que vous recevez une erreur ou si vous ne parvenez pas à vous connecter, suivez l’une des deux solutions.

#### <a name="sign-in-to-servicenow-as-the-integration-user"></a>Se connecter à ServiceNow en tant qu’utilisateur d’intégration

1. Revenez à la page autorisation dans ServiceNow.
2. Sélectionnez le lien qui **n’est pas** dans le coin supérieur droit.
3. Connectez-vous à ServiceNow en tant qu’utilisateur d’intégration que vous avez créé précédemment à partir de la liste de vérification d’installation.  
4. Sélectionnez **autoriser** dans la page ServiceNow pour demander si le connecteur sécurité + conformité peut se connecter à votre compte ServiceNow.
5. Poursuivez la procédure de configuration.

#### <a name="create-a-security-admin-user"></a>Créer un utilisateur d’administrateur de sécurité

1. Créez un utilisateur avec des privilèges d’administrateur de sécurité dans Azure Active Directory. L’utilisateur doit avoir les mêmes nom et adresse de messagerie que l’utilisateur d’intégration que vous avez créé à partir de la liste de vérification d’installation. Vous pouvez supprimer le rôle d’administrateur de sécurité une fois que la connexion est terminée et que la connexion a été établie.
2. Connectez-vous au centre de sécurité Microsoft 365 en tant qu’utilisateur et suivez les étapes de configuration.

### <a name="ip-filtering"></a>Filtrage IP

Si vous avez activé le filtrage IP, vous devrez peut-être autoriser explicitement les adresses IP. Pour plus d’informations sur l’autorisation des plages IP dans ServiceNow, voir [contrôle d’accès aux adresses IP](https://docs.servicenow.com/bundle/orlando-platform-administration/page/administer/login/task/t_AccessControl.html) . Consultez la rubrique [Azure IP Ranges and service Tags-public Cloud](https://www.microsoft.com/en-us/download/details.aspx?id=56519) pour obtenir la liste des adresses IP à autoriser.

### <a name="installation-is-complete-but-dont-see-tickets-and-cant-share"></a>L’installation est terminée, mais ne vois pas les tickets et ne peut pas partager

Si les étapes d’installation et de configuration sont terminées, mais que vous ne voyez pas les cartes ServiceNow sur la page d’accueil et que vous ne pouvez pas partager de ServiceNow à partir du score de sécurité Microsoft, vérifiez l’état de la page de mise en service sur https://security.microsoft.com/ticketProvisioning . Sélectionnez **autoriser** et revenir à la page d’accueil. Les cartes doivent apparaître.

## <a name="resources"></a>Ressources

- [Gérer les tickets ServiceNow dans le centre de sécurité](tickets-security-center.md)