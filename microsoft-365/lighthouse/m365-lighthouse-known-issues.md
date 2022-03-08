---
title: Problèmes connus avec les Microsoft 365 Lighthouse
f1.keywords: NOCSH
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, consultez la liste des problèmes connus pour Le domaine des fonctionnalités.
ms.openlocfilehash: c91ef6a05bf335ed503615cbd058d12a5a43fd5a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319137"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Problèmes connus avec les Microsoft 365 Lighthouse

Cet article répertorie les problèmes connus pour les Microsoft 365 Lighthouse par domaine de fonctionnalité. Pour plus d’informations sur le sujet, voir [Overview of Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Utilisateurs

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **L’agent du helpdesk ne parvient pas à réinitialiser un mot de passe utilisateur** | Les techniciens du fournisseur de services gérés (MSP) qui sont membres du groupe Agent du service d’assistance ne peuvent pas réinitialiser les mots de passe des utilisateurs des clients. Lorsqu’ils essaient de réinitialiser le mot de passe d’un utilisateur, ils obtiennent le message d’erreur suivant : « Vous n’êtes pas autorisé à le faire. [En savoir plus](m365-lighthouse-configure-portal-security.md) » | Pour contourner le problème des autorisations, les agents du helpdesk doivent réinitialiser les mots de passe à l’aide Centre d'administration Microsoft 365 ou Azure Active Directory. |

## <a name="devices"></a>Appareils

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **La stratégie supprimée s’affiche** | Une fois qu’une stratégie de conformité d’appareil a été supprimée d’Intune, elle reste temporairement visible dans le Contrôle d’accès. Si les techniciens MSP tentent d’établir une comparaison de stratégie incluant une stratégie qui a été supprimée, les techniciens obtiennent l’erreur suivante : « Un problème s’est passé. Veuillez actualiser la page et réessayer. » | Pour résoudre l’erreur, effacez la stratégie supprimée de la comparaison de stratégies et comparez uniquement les stratégies existantes. |

## <a name="threat-management"></a>Gestion des menaces

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Le nom de la menace est manquant** | Lorsque les techniciens MSP visualisent la liste des menaces à partir de la page Gestion des menaces, il se peut que le nom de la menace soit manquant pour certaines menaces. Cela se produit lorsque l’appareil sur qui la menace a été détectée a été récemment supprimé d’Intune. | Le problème sera résolu dans les 48 heures. Aucune étape supplémentaire n’est requise. |

## <a name="baselines"></a>Bases de référence

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Paramètres conflictuelles lors de la comparaison des étapes de blocage de l’authentification héritée et du déploiement de l’authentification multifacteur** | Si un client a déployé bloquer l’authentification héritée et l’une des étapes de déploiement de l’authentification multifacteur, un test de comparaison décrit par erreur ces paramètres comme étant en conflit. | Aucune solution de contournement n’est requise. Les paramètres ne sont pas réellement en conflit et les utilisateurs du client ne sont pas touchés. |

## <a name="windows-365"></a>Windows 365

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Erreur de mise en service de nouvelle tentative** | Les techniciens MSP obtiennent un message d’erreur « Vous n’êtes pas autorisé à le faire » lorsque vous tentez de réessayer la mise en service d’un PC Cloud. | Pour contourner ce problème, connectez-vous au client, puis réapprovisionnez les PC cloud à partir du Centre d’administration microsoft Endpoint Manager. Pour obtenir des instructions, [voir Reprovision a Cloud PC](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Journaux d’audit


| Problème | Description | Solution |
|--|--|--|
| **Les actions Désactiver et Réactiver ne sont pas répertoriées dans les journaux d’audit** | Les activités suivantes ne sont actuellement pas signalées dans la page Journaux d’audit dans le Journal d’audit : <ul><li>Name: offboardTenant \| Action: Inactivate a customer</li> <li>Nom : action resetTenantOnboardingStatus \| : client réactif</li></ul> | Il n’existe aucune solution de contournement, mais nous travaillons sur un correctif. Ces activités apparaissent dans les journaux d’audit une fois le correctif déployé dans le service. |
| **Le filtre n’affiche pas tous les utilisateurs** | Lorsque les techniciens MSP tentent de filtrer à l’aide de l’outil **Initiated By**, la liste de tous les noms d’utilisateur principaux (UPN) (correspondant aux ID de messagerie des techniciens ayant initié des actions générant des journaux d’audit) n’est pas entièrement affichée sous le filtre.<br><br>Notez que les journaux d’audit eux-mêmes seront entièrement affichés ; seule la possibilité de les filtrer à l’aide de **l’outil Initiated By** est impactée. | Il n’existe aucune solution de contournement, mais nous travaillons sur un correctif. Le filtre revient à son comportement attendu (affichage de la liste complète des UPN à filtrer par) une fois que le correctif est déployé dans le service. |

## <a name="delegated-admin-permissionsdap"></a>Autorisations d’administration déléguées (DAP)

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Retard des autorisations lors de la modification des rôles DAP** | Si un technicien MSP est ajouté ou supprimé du groupe Agent d’administration ou Agent du service d’aide, il peut y avoir un retard dans la réflexion des autorisations appropriées au sein de l’agent d’administration ou du groupe d’agents d’aide. | Le problème est résolu dans les 30 minutes. Aucune étape supplémentaire n’est requise. |

## <a name="granular-delegated-admin-permissionsgdap"></a>Autorisations d’administration déléguées granulaires (GDAP)

> [!NOTE]
> Le GDAP est actuellement en prévisualisation [technique (](/partner-center/announcements/2022-february#6) prévisualisation publique) pour permettre aux partenaires d’attribuer des autorisations granulaires avant que le GDAP ne soit généralement disponible.

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Divers problèmes d’autorisation GDAP dans l’ensemble du monde** | <ul><li>Les administrateurs de sécurité GDAP ne peuvent pas afficher les utilisateurs à risque, ignorer les risques ou confirmer les utilisateurs compromis.</li><li>Les lecteurs de sécurité GDAP ne peuvent pas afficher les utilisateurs à risque.</li><li>Les administrateurs globaux GDAP voient un message d’erreur lors de la tentative d’affichage de l’état du service.</li></ul> | Avant la disponibilité générale du GDAP, la solution de contournement consiste à attribuer à l’utilisateur un rôle GDAP d’administrateur général ou d’agent d’administration. Pour obtenir des instructions sur l’attribution du rôle GDAP Administrateur général, voir [Obtenir des autorisations d’administrateur précises pour gérer le service d’un client](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Pour obtenir des instructions sur l’attribution du rôle DAP d’agent administrateur, voir [Attribuer des rôles et des autorisations aux utilisateurs](/partner-center/permissions-overview). Pour obtenir une liste d’actions dans l’Exemple qui nécessitent certains rôles Azure Active Directory dans le client partenaire, voir Configurer la sécurité [Microsoft 365 Lighthouse portail.](/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security)

## <a name="localization"></a>Localisation

| Problème | Description | Solution |
| ---------------- | ---------------- | ---------------- |
| **Problèmes de traduction** | Les utilisateurs peuvent être face à des problèmes de traduction linguistique lorsque la langue de leur navigateur, ou leur sélection de langue dans le Navigateur, est autre que l’anglais. | Pour minimiser les problèmes de traduction dans le Portail, assurez-vous que la sélection de la langue du navigateur correspond à celle du paramètre de langue dans le portail De Latteur. Pour modifier la sélection de la langue dans Le Parcage, connectez-vous à Ce dernier et sélectionnez l’icône d’engrenage en haut de la page pour ouvrir la page Paramètres du portail, sélectionnez Langue **+** région, puis sélectionnez la langue et les formats régionaux appropriés. |

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Résoudre les problèmes et les messages d’erreur dans Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (article)\
[Obtenir de l’aide et du support Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (article)