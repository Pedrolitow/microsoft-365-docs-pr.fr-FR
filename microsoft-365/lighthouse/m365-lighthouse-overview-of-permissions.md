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
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, en savoir plus sur les exigences en matière d’autorisations.
ms.openlocfilehash: 25f38b8cbc0c6815139fd6afd3616cfaa7df48e1
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595408"
---
# <a name="overview-of-permissions-in-microsoft-365-lighthouse"></a>Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse

L’accès délégué aux clients est requis pour que les fournisseurs de services gérés (MSP) utilisent Microsoft 365 Lighthouse. Les privilèges d’administration délégués granulaires (GDAP) offrent aux MSP un niveau élevé de contrôle et de flexibilité en leur offrant un accès client par le biais de rôles intégrés [Azure Active Directory (Azure AD](/azure/active-directory/roles/permissions-reference)). L’attribution des rôles les moins privilégiés par tâche via GDAP aux techniciens MSP réduit les risques de sécurité pour les MSP et les clients. Pour plus d’informations sur les rôles les moins privilégiés par tâche, voir Rôles avec privilèges minimum : l’Partner [Center](/partner-center/gdap-least-privileged-roles-by-task) et les rôles les moins privilégiés par [tâche dans Azure Active Directory](/azure/active-directory/roles/delegate-by-task). Pour plus d’informations sur la configuration d’une relation GDAP avec un client, voir Obtenir des [autorisations d’administrateur granulaires pour gérer le service d’un client - Partner Center.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer)

Nous vous recommandons d’attribuer des rôles à des groupes de techniciens MSP en fonction des tâches que chaque groupe doit effectuer pour le compte du client. Par exemple, il se peut que les techniciens du service technique doivent simplement lire les données client ou réinitialiser les mots de passe utilisateur. En revanche, les ingénieurs d’escalade devront peut-être prendre des mesures correctives pour mettre à jour les paramètres de sécurité du client client. Il est préférable d’attribuer le rôle le moins permissif requis pour effectuer une tâche afin que les données client et partenaire restent sécurisées. Nous vous recommandons d’Privileged Identity Management (PIM) pour activer l’accès dans le temps au rôle Administrateur général, si nécessaire. L’accès global à un trop grand nombre d’utilisateurs constitue un risque pour la sécurité et nous vous recommandons de le limiter autant que possible. Pour plus d’informations sur la façon d’activer PIM, voir [Configurer Azure AD PIM.](m365-lighthouse-configure-portal-security.md#set-up-azure-ad-privileged-identity-management-pim)

Le tableau de la section suivante décrit les rôles GDAP qui accordent l’autorisation de lire les données client et de prendre des mesures sur les locataires du client dans Le Poste. [Consultez les autorisations dans le client partenaire](#permissions-in-the-partner-tenant) dans cet article pour les rôles supplémentaires requis pour gérer les entités Dente (par exemple, les balises et les demandes de service De la poste).

> [!NOTE]
>Le GDAP est actuellement en [prévisualisation](/partner-center/announcements/2022-february#6) technique (prévisualisation publique) pour permettre aux partenaires d’attribuer des autorisations granulaires avant que le GDAP ne soit généralement disponible. Vérifiez [les problèmes connus si](m365-lighthouse-known-issues.md) vous avez un problème d’accès ou d’effectuer une action dans le Dossier.

## <a name="example-msp-service-tiers-and-recommended-gdap-roles"></a>Exemples de niveaux de service MSP et de rôles GDAP recommandés

Le tableau suivant répertorie les rôles GDAP recommandés pour certains exemples de niveaux de service MSP et les actions que ces rôles peuvent effectuer sur les différentes pages De la région.

|| AccountManagers&nbsp;| ServiceDeskTechnician&nbsp;&nbsp; |SystemAdministrators&nbsp; | EscalationEngineers&nbsp;|
|---|---|---|---|---|
| **Rôles GDAP recommandés** |<ul><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur de sécurité<br>+</li><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>Administrateur d’authentification</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>Intune administrateur<br>+</li><li>Administrateur de sécurité</li></ul>|
|**Cerpageallowedactions&nbsp;&nbsp;+&nbsp;&nbsp;**  |
| **Accueil**  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | 
| **Tenants**     | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li></ul>  | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li></ul>   |  <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation Microsoft 365 services</li></ul> | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts client et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation Microsoft 365 services</li></ul>  |
| **Utilisateurs**   | <ul><li>Afficher les données de niveau client (non spécifiques à l’utilisateur)</li><li>Rechercher des comptes d’utilisateurs sur plusieurs locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>  | <ul><li>Afficher toutes les données propres à l’utilisateur</li><li>Rechercher des comptes d’utilisateurs sur plusieurs locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>|  <ul><li>Afficher toutes les données propres à l’utilisateur</li><li>Rechercher des comptes d’utilisateurs sur plusieurs locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</i><li>Bloquer la sign-in</li></ul>  | <ul><li>Afficher toutes les données propres à l’utilisateur</li><li>Rechercher des comptes d’utilisateurs sur plusieurs locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li><li>Bloquer la sign-in</li><li>Confirmer les utilisateurs compromis</li><li>Ignorer les risques pour les utilisateurs</li></ul> |
| **Appareils**    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Synchroniser l’appareil</li><li>Redémarrer l’appareil</li><li>Collecter les diagnostics</li></ul>|
| **Gestion des menaces**  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Exécuter une analyse complète</li><li>Exécuter une analyse rapide</li><li>Mettre à jour la protection antivirus</li><li>Redémarrer l’appareil</li></ul>|
| **Bases de référence**    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul>  | <ul><li>Afficher toutes les données</li></ul> |
| **Windows 365** | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> |
| **État des services****|  
|**Journaux d’audit****|

*Voir [autorisations de réinitialisation du](/azure/active-directory/roles/permissions-reference#password-reset-permissions) mot de passe pour un tableau qui répertorie les rôles requis pour réinitialiser les mots de passe pour les administrateurs clients.

**D’autres rôles et autorisations sont requis pour afficher l’état du service et les journaux d’audit. Pour plus d’informations, [voir Autorisations dans le client partenaire](#permissions-in-the-partner-tenant).

> [!NOTE]
> Si vous recevez un message dans le Message en cours vous disant que vous n’êtes pas autorisé à afficher ou modifier des informations, un rôle qui ne vous est pas attribué vous permet d’effectuer l’action. Vous devez joindre un administrateur de votre client partenaire qui peut vous attribuer le rôle approprié pour l’action que vous essayez d’effectuer.

## <a name="delegated-admin-privileges-dap-in-lighthouse"></a>Privilèges d’administrateur délégués (DAP) en île

GDAP remplacera finalement DAP comme méthode principale pour configurer l’accès délégué pour les clients. Toutefois, si le GDAP n’a pas été installé, les techniciens MSP peuvent toujours accéder à l’aide des rôles Agent du service d’aide ou Agent d’administration accordés via DAP. Pour les clients où GDAP et DAP coexistent, les rôles accordés aux techniciens MSP via GDAP prévalent. Pour plus d’informations sur l’precation GDAP ou DAP, consultez les questions fréquemment [posées](/partner-center/announcements/2022-march#15) par [GDAP](/partner-center/gdap-faq) ou les annonces de l’Partner Center pour les dates et les chronologies.

Pour les clients avec DAP et sans GDAP, le rôle Agent d’administration accorde des autorisations pour afficher toutes les données client et prendre n’importe quelle action dans le Centre d’administration (voir ci-dessous pour d’autres actions qui nécessitent également un rôle dans le client partenaire).

Le rôle Agent du service d’assistance accorde des autorisations pour afficher toutes les données client et prendre des mesures limitées dans le Centre d’aide, telles que la réinitialisation des mots de passe utilisateur, le blocage de la signature utilisateur et la mise à jour des informations de contact client et des sites web.

Étant donné les autorisations étendues accordées aux utilisateurs partenaires avec des rôles DAP, nous vous recommandons d’adopter GDAP dès que possible. 

## <a name="permissions-in-the-partner-tenant"></a>Autorisations dans le client partenaire

Pour certaines actions dans le Groupement, les attributions de rôles dans le client partenaire sont requises. Le tableau suivant répertorie les rôles des clients partenaires et leurs autorisations associées.

| Rôles des locataires partenaires | Autorisations |
|--|--|
| Administrateur général du client partenaire | <ul><li>Inscrivez-vous à l’inscription à l’Centre d'administration Microsoft 365.</li><li>Accepter les modifications apportées au contrat partenaire lors de la première expérience d’utilisateur.</li><li>Activer et désactiver un client.</li><li>Créer, mettre à jour et supprimer des balises.</li><li>Affecter et supprimer des balises d’un client.</li></ul> |
| Membre du client partenaire avec au moins un Azure AD affecté avec le jeu de propriétés suivant :<br>**microsoft.office365.supportTickets/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference).) | Créer des demandes de service d’accès. |
| Membre du client partenaire qui répond aux *deux* conditions suivantes : <ul><li>A au moins un rôle Azure AD affecté avec le jeu de propriétés suivant :<br>**microsoft.office365.serviceHealth/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference).)</li><li>Au moins un rôle délégué DAP est attribué (agent d’administration ou agent d’aide)</li></ul> | Afficher les informations d’état du service. |

## <a name="related-content"></a>Contenu associé

[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)  
[Faq sur les privilèges d’administration délégués (DAP)](/partner-center/dap-faq) (article)  
[Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview) (article)  
[Vue d’Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)  
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)  
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
