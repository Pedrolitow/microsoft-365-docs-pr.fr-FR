---
title: Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: magarlan, chrigreen
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, en savoir plus sur les exigences d’autorisation Lighthouse.
ms.openlocfilehash: dd8b5be367b7a3c682aa93081583d784112c8323
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68728728"
---
# <a name="overview-of-permissions-in-microsoft-365-lighthouse"></a>Vue d’ensemble des autorisations dans Microsoft 365 Lighthouse

L’accès délégué aux locataires clients est requis pour que les fournisseurs de services managés (MSP) utilisent Microsoft 365 Lighthouse. Les privilèges de Administration délégués granulaires (GDAP) offrent aux fournisseurs de services de gestion des services un niveau élevé de contrôle et de flexibilité en fournissant un accès client via [des rôles intégrés Azure Active Directory (Azure AD).](/azure/active-directory/roles/permissions-reference) L’attribution des rôles les moins privilégiés par tâche via GDAP aux techniciens MSP réduit les risques de sécurité pour les msp et les clients. Pour plus d’informations sur les rôles avec privilèges minimum par tâche, consultez [Rôles avec privilèges minimum - Espace partenaires](/partner-center/gdap-least-privileged-roles-by-task) et [Rôles avec privilèges minimum par tâche dans Azure Active Directory](/azure/active-directory/roles/delegate-by-task). Pour plus d’informations sur la configuration d’une relation GDAP avec un locataire client, consultez [Obtenir des autorisations d’administrateur précises pour gérer le service d’un client - Espace partenaires.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer)

Nous vous recommandons d’attribuer des rôles à des groupes de techniciens MSP en fonction des tâches que chaque groupe doit effectuer pour le compte du client. Par exemple, les techniciens de Service Desk peuvent simplement avoir besoin de lire les données du client ou de réinitialiser les mots de passe utilisateur. En revanche, les ingénieurs d’escalade peuvent avoir besoin de prendre des mesures correctives supplémentaires pour mettre à jour les paramètres de sécurité du locataire client. Il est recommandé d’attribuer le rôle le moins permissif requis pour effectuer une tâche afin que les données des clients et des partenaires restent sécurisées. Nous vous recommandons d’utiliser Privileged Identity Management (PIM) pour activer l’accès limité au rôle Administrateur général, si nécessaire. L’octroi d’un accès global à un trop grand nombre d’utilisateurs constitue un risque pour la sécurité, et nous vous recommandons de le limiter autant que possible. Pour plus d’informations sur l’activation de PIM, consultez [Configurer Azure AD PIM.](m365-lighthouse-configure-portal-security.md#set-up-azure-ad-privileged-identity-management-pim)

Les tableaux de la section suivante décrivent les rôles GDAP qui accordent l’autorisation de lire les données client et de prendre des mesures sur les locataires clients dans Lighthouse. Consultez [Autorisations dans le locataire partenaire](#permissions-in-the-partner-tenant) dans cet article pour connaître les rôles supplémentaires requis pour gérer les entités Lighthouse (par exemple, les étiquettes et les demandes de service Lighthouse).

## <a name="example-msp-service-tiers-recommended-gdap-roles-and-permissions"></a>Exemples de niveaux de service MSP, rôles GDAP recommandés et autorisations

Le tableau suivant répertorie les rôles GDAP recommandés pour certains exemples de niveaux de service MSP. 

|| Gestionnaires de comptes| Techniciens du Service Desk | Administrateurs système | Ingénieurs d’escalade|
|---|---|---|---|---|
| **Rôles GDAP recommandés** |<ul><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur de sécurité<br>+</li><li>Administrateur du support technique</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>Administrateur d’authentification</li></ul> |<ul><li>Lecteur général<br>+</li><li>Administrateur d’utilisateurs<br>+</li><li>administrateur Intune<br>+</li><li>Administrateur de sécurité</li></ul>|

Le tableau suivant répertorie les actions que les exemples de niveaux de service MSP peuvent effectuer sur les différentes pages Lighthouse, comme déterminé par les rôles GDAP qui leur sont attribués (indiqués dans le tableau précédent).

| Page Phare | Actions autorisées des gestionnaires de compte| Actions autorisées par les techniciens du Service Desk |Actions autorisées par les administrateurs système | Actions autorisées par les ingénieurs d’escalade|
|---|---|---|---|---|
| Famille  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | 
| Clients     | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts clients et le site web</li><li>Afficher les plans de déploiement</li></ul>  | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts clients et le site web</li><li>Afficher les plans de déploiement</li></ul>   |  <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts clients et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation des services Microsoft 365</li></ul> | <ul><li>Afficher la liste des locataires</li><li>Mettre à jour les contacts clients et le site web</li><li>Afficher les plans de déploiement</li><li>Afficher l’utilisation des services Microsoft 365</li></ul>  |
| Utilisateurs   | <ul><li>Afficher les données au niveau du locataire (non spécifiques à l’utilisateur)</li><li>Rechercher des comptes d’utilisateur dans des locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>  | <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur dans des locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li></ul>|  <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur dans des locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</i><li>Bloquer la connexion</li></ul>  | <ul><li>Afficher toutes les données spécifiques à l’utilisateur</li><li>Rechercher des comptes d’utilisateur dans des locataires</li><li>Réinitialiser le mot de passe pour les non-administrateurs*</li><li>Bloquer la connexion</li><li>Confirmer les utilisateurs compromis</li><li>Ignorer les risques pour les utilisateurs</li></ul> |
| Appareils    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Synchroniser l’appareil</li><li>Redémarrer l’appareil</li><li>Collecter les diagnostics</li></ul>|
| Gestion des menaces  | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li><li>Exécuter l’analyse complète</li><li>Exécuter une analyse rapide</li><li>Mettre à jour la protection antivirus</li><li>Redémarrer l’appareil</li></ul>|
| Bases de référence    | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul>  | <ul><li>Afficher toutes les données</li></ul> |
| Windows 365 | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> | <ul><li>Afficher toutes les données</li></ul> |
| État des services**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |
| Journaux d’audit**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |

*Consultez [Autorisations de réinitialisation de mot de passe](/azure/active-directory/roles/permissions-reference#password-reset-permissions) pour obtenir un tableau qui répertorie les rôles requis pour réinitialiser les mots de passe pour les administrateurs clients.

**Différents rôles et autorisations sont nécessaires pour afficher les journaux d’État des services et d’audit. Pour plus d’informations, consultez [Autorisations dans le locataire partenaire](#permissions-in-the-partner-tenant).

> [!NOTE]
> Si vous recevez un message dans Lighthouse indiquant que vous n’avez pas l’autorisation d’afficher ou de modifier des informations, vous êtes affecté à un rôle qui ne dispose pas des autorisations appropriées pour effectuer l’action. Vous devez contacter un administrateur de votre locataire partenaire qui peut vous attribuer le rôle approprié pour l’action que vous essayez d’effectuer.

## <a name="delegated-admin-privileges-dap-in-lighthouse"></a>Privilèges Administration délégués (DAP) dans Lighthouse

GDAP remplacera finalement DAP comme méthode principale pour configurer l’accès délégué pour les locataires clients. Toutefois, si GDAP n’a pas été configuré, les techniciens MSP peuvent toujours accéder à Lighthouse en utilisant l’agent de support technique ou Administration rôles d’agent accordés via DAP. Pour les clients où GDAP et DAP coexistent, les rôles accordés aux techniciens MSP via GDAP sont prioritaires. Pour plus d’informations sur la dépréciation de GDAP ou DAP, consultez les [questions fréquentes sur GDAP](/partner-center/gdap-faq) ou les [annonces de l’Espace partenaires pour connaître](/partner-center/announcements/2022-march#15) les dates et les chronologies.

Pour les clients avec DAP et sans GDAP, le rôle agent Administration accorde des autorisations pour afficher toutes les données du locataire et effectuer toute action dans Lighthouse (voir ci-dessous pour d’autres actions qui nécessitent également un rôle dans le locataire partenaire).

Le rôle Agent du support technique accorde des autorisations pour afficher toutes les données client et effectuer des actions limitées dans Lighthouse, telles que la réinitialisation des mots de passe utilisateur, le blocage des connexions utilisateur et la mise à jour des informations de contact et des sites web du client.

Étant donné les autorisations étendues accordées aux utilisateurs partenaires disposant de rôles DAP, nous vous recommandons d’adopter GDAP dès que possible. 

## <a name="permissions-in-the-partner-tenant"></a>Autorisations dans le locataire partenaire

Pour certaines actions dans Lighthouse, des attributions de rôles dans le locataire partenaire sont requises. Le tableau suivant répertorie les rôles de locataire partenaires et les autorisations associées.

| Rôles de locataire partenaires | Autorisations |
|--|--|
| Administrateur général du locataire partenaire | <ul><li>Inscrivez-vous à Lighthouse dans le Centre d'administration Microsoft 365.</li><li>Acceptez les avenants au contrat partenaire lors de la première utilisation.</li><li>Activer et désactiver un locataire.</li><li>Créer, mettre à jour et supprimer des balises.</li><li>Affectez et supprimez des étiquettes d’un locataire client.</li><li>Consulter les journaux d’audit</li></ul> |
| Membre de locataire partenaire avec au moins un rôle Azure AD attribué avec les propriétés suivantes définies :<br>**microsoft.office365.supportTickets/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, consultez [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).) | Créer des demandes de service Lighthouse. |
| Membre locataire partenaire qui remplit *les deux* conditions suivantes : <ul><li>A au moins un rôle Azure AD attribué avec les propriétés suivantes définies :<br>**microsoft.office365.serviceHealth/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, consultez [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).)</li><li>Au moins un rôle délégué DAP est attribué (agent Administration ou agent du support technique)</li></ul> | Afficher les informations d’intégrité du service. |

## <a name="related-content"></a>Contenu associé

[Configuration requise pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)  
[FAQ sur les privilèges d’administration délégués (DAP)](/partner-center/dap-faq) (article)  
[Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)  
[Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview) (article)  
[Vue d’ensemble de Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)  
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)  
[FAQ Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (article)
