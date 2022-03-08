---
title: Configurer des rôles pour gérer les clients
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
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment configurer des rôles pour gérer les clients.
ms.openlocfilehash: 82203c7faa361bf512c3184616b47760655083d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63331154"
---
# <a name="set-up-roles-to-manage-customer-tenants"></a>Configurer des rôles pour gérer les clients

Les fournisseurs de services gérés (MSP) peuvent permettre un accès granulaire et limité au temps aux locataires de leurs clients dans Microsoft 365 Lighthouse en configurant des privilèges d’administration délégués granulaires (GDAP) dans l’Centre partenaires. Le GDAP offre aux MSP un niveau élevé de contrôle et de flexibilité en offrant aux clients un accès Azure Active Directory [(Azure AD) intégrés](/azure/active-directory/roles/permissions-reference). L’attribution des [rôles les moins](/azure/active-directory/roles/delegate-by-task) privilégiés par tâche via GDAP aux techniciens MSP réduit les risques de sécurité pour les MSP et les clients. Autorisez GDAP à attribuer des rôles plus granulaires à vos techniciens qui utilisent Le poste de travail et adoptent une approche moins privilégiée de la sécurité entre les clients.

Si les techniciens MSP accèdent toujours aux environnements clients avec les rôles Agent du service d’assistance ou Agent d’administration accordés via des privilèges d’administration délégués (DAP), consultez [DAP dans l’article sur le DAP dans cet](#dap-in-lighthouse) article. Si GDAP et DAP coexistent, les rôles accordés aux utilisateurs via GDAP prévalent pour les clients où une relation GDAP a été établie.

## <a name="set-up-gdap-in-lighthouse"></a>Configurer GDAP en île

Les étapes de haut niveau ci-dessous sont nécessaires pour créer une relation GDAP avec un client. Pour plus d’informations sur GDAP, voir [Introduction aux privilèges d’administration délégués granulaires.](/partner-center/gdap-introduction)

1. [Catégoriser les utilisateurs en groupes de](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal#create-a-basic-group-and-add-members) sécurité au sein de l’Azure AD du partenaire.

2. [Créez et envoyez une demande de relation GDAP](/partner-center/gdap-obtain-admin-permissions-to-manage-customer) au client.

3. Assurez-vous que [le client approuve la demande de relation GDAP](/partner-center/gdap-customer-approval).

4. [Affectez les groupes de sécurité appropriés](/partner-center/gdap-assign-azure-ad-roles#grant-permissions-to-security-groups) à la relation GDAP.

5. Attribuez les [rôles Azure Active Directory intégrés](/azure/active-directory/roles/permissions-reference) appropriés aux groupes de sécurité De la sécurité Du monde, alignés pour la gestion des clients.

Nous vous recommandons d’nommer des groupes de sécurité en fonction des tâches que les techniciens MSP gèrent dans Lem. Par exemple, vous pouvez créer des groupes de sécurité pour les techniciens du service d’aide, les administrateurs système et les ingénieurs en escalade. Nous vous recommandons d’utiliser les rôles décrits dans le tableau suivant pour gérer Le Poste.

### <a name="example-security-groups"></a>Exemples de groupes de sécurité

||Techniciens du service d’aide |Administrateurs système |Ingénieurs d’escalade|
|--------------------|-------------|-------------|------------|
|**Rôles GDAP recommandés** |<ul><li>Administrateur du support technique</li><li>Lecteur de sécurité</li></ul>   |<ul><li>Administrateur d’utilisateurs</li><li>Administrateur d’authentification</li><li>Lecteur général</li><li>Administrateur Intune</li><li>Administrateur de sécurité</li></ul>   |Administrateur général  |
|**Tâches** |Lire les informations client dans Le Monde et prendre des mesures limitées (par exemple, réinitialiser les mots de passe des utilisateurs ou mettre à jour les informations de contact)   |Maintenez la sécurité des clients en prenant des mesures correctives dans le Contrôle d’appareil (par exemple, redémarrage d’appareils).   |Prendre des mesures privilégiées si nécessaire pour protéger le client client (par exemple, le blocage de la signature d’un administrateur compromis).  |

Pour obtenir des descriptions d’autorisations spécifiques, [voir Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference). Pour les rôles et les tâches propres aux partenaires, voir [Rôles avec privilèges minimum](/partner-center/gdap-least-privileged-roles-by-task).

## <a name="dap-in-lighthouse"></a>DAP en île

DAP limite l’accès aux clients en poste avec deux rôles : Agent d’administration et Agent du service d’aide. Vous pouvez vérifier quels utilisateurs du client partenaire ont les rôles Agent d’administration ou Agent du helpdesk en vérifiant les appartenances aux groupes de sécurité sur la page [Azure AD –](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) Tous les groupes. Pour consulter les clients qui ont encore un DAP en place, voir [Surveillance des relations administratives et suppression de DAP en libre-service](/partner-center/dap-monitor-self-serve-removal).

Pour les clients avec DAP et sans GDAP, le rôle Agent d’administration accorde des autorisations pour afficher toutes les informations sur le client et prendre des mesures dans la barre de sécurité (voir ci-dessous pour d’autres actions qui nécessitent également un rôle dans le client partenaire). 

Le rôle d’agent du service d’assistance accorde des autorisations pour afficher toutes les informations client et prendre des mesures limitées dans le Jeu de mots de passe (par exemple, réinitialiser les mots de passe des utilisateurs, bloquer les connecteurs d’utilisateurs et mettre à jour les informations de contact client et les sites web).

Étant donné les autorisations étendues accordées aux utilisateurs partenaires avec DAP, nous vous recommandons d’adopter GDAP dès que possible. Les deux modèles coexistent, mais GDAP remplacera finalement DAP et les autorisations GDAP seront prioritaire sur les autorisations DAP pendant la période de transition. Pour plus d’informations, consultez [les questions fréquemment posées par GDAP](/partner-center/gdap-faq).

## <a name="other-roles-and-permissions"></a>Autres rôles et autorisations

Pour certaines actions dans le Groupement, les attributions de rôles dans le client partenaire sont requises. Le tableau suivant répertorie les rôles des clients partenaires et leurs autorisations associées.<br><br>

| Rôles des locataires partenaires | Autorisations |
|--|--|
| Administrateur général du client partenaire | <ul><li>Inscrivez-vous à l’inscription à l’Centre d'administration Microsoft 365.</li><li>Accepter les modifications apportées au contrat partenaire lors de la première expérience d’utilisateur.</li><li>Activer et désactiver un client.</li><li>Créer, mettre à jour et supprimer des balises.</li><li>Affecter et supprimer des balises d’un client.</li></ul> |
| Membre du client partenaire avec au moins un rôle Azure AD affecté avec le jeu de propriétés suivant : **microsoft.office365.supportTickets/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference). | Créer des demandes de service d’accès. |
| Membre du client partenaire qui répond aux *deux* conditions suivantes : <ul><li>A au moins un rôle Azure AD affecté avec le jeu de propriétés suivant : **microsoft.office365.serviceHealth/allEntities/allTasks**<br>(Pour obtenir la liste complète des rôles Azure AD, voir Azure AD [rôles intégrés](/azure/active-directory/roles/permissions-reference)</li><li>Au moins un rôle délégué DAP est attribué (agent d’administration ou agent d’aide)</li></ul> | Afficher les informations d’état du service. |

## <a name="next-steps"></a>Étapes suivantes

Une fois les rôles créés, vous devez configurer une sécurité supplémentaire du portail De Lattérité, en particulier l’authentification multifacteur (MFA) et éventuellement Azure AD Identity Management (PIM). Pour plus d’informations, [voir Configure Microsoft 365 Lighthouse portal security](m365-lighthouse-configure-portal-security.md).

## <a name="related-content"></a>Contenu associé

[Rôles les moins privilégiés par tâche](/partner-center/gdap-least-privileged-roles-by-task?branch=pr-en-us-2577) (article)  
[Faq sur les privilèges d’administration délégués (DAP)](/partner-center/dap-faq) (article)  
[Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview) (article)  
[Conditions requises pour Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (article)  
[Vue d’Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (article)  
[S’inscrire à Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (article)  
[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
