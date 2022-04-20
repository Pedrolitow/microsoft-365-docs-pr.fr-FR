---
title: Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, en savoir plus sur les exigences d’autorisation Lighthouse.
ms.openlocfilehash: 62796df9e5bd5b437d06fe0c8ab6206e070c201b
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916120"
---
# <a name="overview-of-permissions-in-microsoft-365-lighthouse"></a>Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse

L’accès délégué aux locataires clients est requis pour que les fournisseurs de services gérés (MSP) utilisent Microsoft 365 Lighthouse. Les privilèges d’administrateur délégués granulaires (GDAP) offrent aux MSP un niveau élevé de contrôle et de flexibilité en fournissant un accès client par le biais de [Azure Active Directory (Azure AD) rôles intégrés](/azure/active-directory/roles/permissions-reference). L’attribution des rôles les moins privilégiés par tâche via GDAP aux techniciens MSP réduit les risques de sécurité pour les MSP et les clients. Pour plus d’informations sur les rôles les moins privilégiés par tâche, consultez [Rôles à privilèges minimum - Espace partenaires](/partner-center/gdap-least-privileged-roles-by-task) et [rôles à privilèges minimum par tâche dans Azure Active Directory](/azure/active-directory/roles/delegate-by-task). Pour plus d’informations sur la configuration d’une relation GDAP avec un locataire client, consultez [Obtenir des autorisations d’administrateur granulaires pour gérer le service d’un client - Espace partenaires.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer)

Nous vous recommandons d’attribuer des rôles à des groupes de techniciens MSP en fonction des tâches que chaque groupe doit effectuer pour le compte du client. Par exemple, les techniciens Service Desk peuvent simplement avoir besoin de lire les données client client ou de réinitialiser les mots de passe utilisateur. En revanche, les ingénieurs d’escalade devront peut-être prendre des mesures correctives supplémentaires pour mettre à jour les paramètres de sécurité du locataire client. Il est recommandé d’attribuer le rôle le moins permissif nécessaire pour effectuer une tâche afin que les données client et partenaire soient sécurisées. Nous vous recommandons d’utiliser Privileged Identity Management (PIM) pour activer l’accès limité dans le temps au rôle Administrateur général, si nécessaire. Accorder un accès global à un trop grand nombre d’utilisateurs est un risque pour la sécurité, et nous vous recommandons de le limiter autant que possible. Pour plus d’informations sur l’activation de PIM, consultez [Configurer Azure AD PIM.](m365-lighthouse-configure-portal-security.md#set-up-azure-ad-privileged-identity-management-pim)

Les tableaux de la section suivante décrivent les rôles GDAP qui accordent l’autorisation de lire les données client et d’agir sur les locataires clients dans Lighthouse. Pour plus d’informations sur les rôles nécessaires à la gestion des entités Lighthouse (par exemple, les balises et les demandes de service Lighthouse), consultez [les autorisations du locataire partenaire](#permissions-in-the-partner-tenant) dans cet article.

> [!NOTE]
>GDAP est actuellement en [préversion technique](/partner-center/announcements/2022-february#6) (préversion publique) pour permettre aux partenaires d’attribuer des autorisations granulaires avant que GDAP soit généralement disponible. Vérifiez [les problèmes connus](m365-lighthouse-known-issues.md) si vous rencontrez un problème d’accès ou d’exécution d’une action dans Lighthouse.

## <a name="example-msp-service-tiers-recommended-gdap-roles-and-permissions"></a>Exemples de niveaux de service MSP, rôles GDAP recommandés et autorisations

Le tableau suivant répertorie les rôles GDAP recommandés pour certains exemples de niveaux de service MSP. 

|| Gestionnaires de comptes| Techniciens service desk | Administrateurs système | Ingénieurs d’escalade|
|---|---|---|---|---|
| **Rôles GDAP recommandés** |<ul><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur de sécurité<br>+</li><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>Administrateur d’authentification</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>administrateur Intune<br>+</li><li>Administrateur de sécurité</li></ul>|

Le tableau suivant répertorie les actions que l’exemple de niveaux de service MSP peut effectuer sur les différentes pages Lighthouse, comme déterminé par leurs rôles GDAP affectés (indiqués dans le tableau précédent).

| Page Lighthouse | Actions autorisées par les gestionnaires de comptes| Actions autorisées des techniciens service desk |Actions autorisées par les administrateurs système | Actions autorisées par les ingénieurs d’escalade|
|---|---|---|---|---|
| Famille  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | 
| Clients     | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li></ul>  | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li></ul>   |  <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation des services Microsoft 365</li></ul> | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation des services Microsoft 365</li></ul>  |
| Utilisateurs   | <ul><li>Afficher les données au niveau du locataire (non spécifiques à l’utilisateur)</li><li>Rechercher des comptes d’utilisateur entre les locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>  | <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur entre les locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>|  <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur entre les locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</i><li>Bloquer la connexion</li></ul>  | <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur entre les locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li><li>Bloquer la connexion</li><li>Confirmer les utilisateurs compromis</li><li>Ignorer le risque pour les utilisateurs</li></ul> |
| Appareils    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Synchroniser l’appareil</li><li>Redémarrer l’appareil</li><li>Collecter les diagnostics</li></ul>|
| Gestion des menaces  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Exécuter l’analyse complète</li><li>Exécuter une analyse rapide</li><li>Mettre à jour la protection antivirus</li><li>Redémarrer l’appareil</li></ul>|
| Bases de référence    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul>  | <ul><li>Afficher toutes les données</li></ul> |
| Windows 365 | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> |
| État des services**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |
| Journaux d’audit**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |

*Consultez [les autorisations de réinitialisation de mot de passe](/azure/active-directory/roles/permissions-reference#password-reset-permissions) pour une table qui répertorie les rôles requis pour réinitialiser les mots de passe pour les administrateurs de locataires clients.

**Différents rôles et autorisations sont nécessaires pour afficher les journaux d’État des services et d’audit. Pour plus d’informations, consultez [Autorisations dans le locataire partenaire](#permissions-in-the-partner-tenant).

> [!NOTE]
> Si vous recevez un message dans Lighthouse indiquant que vous n’avez pas l’autorisation d’afficher ou de modifier des informations, un rôle qui ne dispose pas des autorisations appropriées pour effectuer l’action vous est attribué. Vous devez contacter un administrateur de votre locataire partenaire qui peut vous attribuer le rôle approprié pour l’action que vous essayez d’effectuer.

## <a name="delegated-admin-privileges-dap-in-lighthouse"></a>Privilèges d’administrateur délégués (DAP) dans Lighthouse

GDAP remplacera finalement DAP comme méthode principale pour configurer l’accès délégué pour les locataires clients. Toutefois, si GDAP n’a pas été configuré, les techniciens MSP peuvent toujours accéder à Lighthouse à l’aide des rôles Agent du support technique ou Agent d’administration accordés via DAP. Pour les clients où GDAP et DAP coexistent, les rôles accordés aux techniciens MSP via GDAP sont prioritaires. Pour plus d’informations sur la dépréciation de GDAP ou DAP, consultez les [questions fréquemment posées sur GDAP](/partner-center/gdap-faq) ou [les annonces de l’Espace partenaires](/partner-center/announcements/2022-march#15) pour les dates et les chronologies.

Pour les clients avec DAP et sans GDAP, le rôle Agent d’administration accorde des autorisations pour afficher toutes les données de locataire et prendre des mesures dans Lighthouse (voir ci-dessous pour d’autres actions qui nécessitent également un rôle dans le locataire partenaire).

Le rôle Agent du support technique accorde des autorisations pour afficher toutes les données client et prendre des mesures limitées dans Lighthouse, telles que la réinitialisation des mots de passe utilisateur, le blocage des connexions utilisateur et la mise à jour des informations de contact client et des sites web.

Étant donné les autorisations étendues accordées aux utilisateurs partenaires avec des rôles DAP, nous vous recommandons d’adopter GDAP dès que possible. 

## <a name="permissions-in-the-partner-tenant"></a>Autorisations dans le locataire partenaire

Pour certaines actions dans Lighthouse, des attributions de rôles dans le locataire partenaire sont requises. Le tableau suivant répertorie les rôles de locataire partenaires et leurs autorisations associées.

| Rôles de locataire de partenaire | Autorisations |
|--|--|
| Administrateur général du locataire partenaire | <ul><li>Inscrivez-vous à Lighthouse dans le Centre d'administration Microsoft 365.</li><li>Acceptez les modifications apportées aux contrats partenaires lors de la première exécution.</li><li>Activez et désactivez un locataire.</li><li>Créez, mettez à jour et supprimez des balises.</li><li>Affectez et supprimez des balises d’un locataire client.</li><li>Examiner les journaux d’audit</li></ul> |
| Membre du locataire partenaire avec au moins un rôle Azure AD attribué avec l’ensemble de propriétés suivant :<br>**microsoft.office365.supportTickets/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, consultez [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).) | Créez des demandes de service Lighthouse. |
| Membre du locataire partenaire qui répond aux *deux* exigences suivantes : <ul><li>Au moins un rôle Azure AD est attribué avec l’ensemble de propriétés suivant :<br>**microsoft.office365.serviceHealth/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, consultez [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).)</li><li>Au moins un rôle délégué DAP est attribué (Agent d’administration ou Agent du support technique)</li></ul> | Afficher les informations d’intégrité du service. |

## <a name="related-content"></a>Contenu associé

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)  
[FAQ sur les privilèges d’administration délégués (DAP)](/partner-center/dap-faq) (article)  
[Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview) (article)  
[Vue d’ensemble de Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)  
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)  
[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)
