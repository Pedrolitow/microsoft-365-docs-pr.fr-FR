---
title: Examiner les journaux d’audit dans Microsoft 365 Lighthouse
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
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment examiner les journaux d’audit.
ms.openlocfilehash: 59e45f33b1c6708b4743605bda6ac4c93499bf59
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188765"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>Examiner les journaux d’audit dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse journaux d’audit enregistrent les actions qui génèrent une modification dans Lighthouse ou d’autres services Microsoft 365. Les actions créer, modifier, supprimer, affecter et distantes créent toutes des événements d’audit que vous pouvez examiner. Par défaut, l’audit est activé pour tous les clients. Elle ne peut pas être désactivée.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher les journaux d’audit, vous devez disposer de l’une des autorisations suivantes :

- rôle Azure Active Directory (Azure AD) - Administrateur général du locataire partenaire

- Rôle De l’Espace partenaires Microsoft - Agent d’administration

## <a name="review-audit-logs"></a>Examiner les journaux d’audit

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Journaux d’audit**.

    > [!NOTE]
    > L’affichage des nouveaux journaux peut prendre jusqu’à 1 heure. Accédez au service respectif pour voir les modifications les plus récentes.

2. Filtrez les journaux, si nécessaire, en utilisant les options suivantes :

    - **Plage de dates** : mois, semaine ou jour précédents.
    - **Locataires : balises** de locataire ou noms de locataires client.
    - **Activité** : Microsoft 365 type d’activité qui correspond à l’action effectuée. Pour plus d’informations, consultez la table [Activités](#activities) .
    - **Initié par** - Qui a lancé l’action.

3. Sélectionnez un journal dans la liste pour afficher les détails complets, y compris le corps de la **demande** .

    Pour exporter des données de journal vers un fichier de valeurs séparées par des virgules (.csv), sélectionnez **Exporter**.

## <a name="activities"></a>Activités

Le tableau suivant répertorie les activités capturées dans les journaux d’audit Lighthouse. La liste est susceptible de changer à mesure que de nouvelles actions sont créées. Vous pouvez utiliser l’activité répertoriée dans le journal d’audit pour voir quelle action a été lancée.<br><br>

| Nom de l’activité | Zone dans Lighthouse | Action lancée | Service affecté |
|--|--|--|--|
| **appliquer** ou **déployer** | Clients | Appliquer un plan de déploiement | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Clients | Appliquer une balise à partir d’un client | Phare |
| **changeDeploymentStatus** ou **assign** | Clients | Mettre à jour l’état du plan d’action pour le plan de déploiement | Phare |
| **managedTenantOperations** | Clients | Afficher des informations sur un plan de déploiement | Azure AD |
| **offboardTenant** | Clients | Désactiver un client | Phare |
| **resetTenantOnboardingStatus** | Clients | Réactif d’un client | Phare |
| **tenantTags** | Clients | Créer ou supprimer une balise | Phare |
| **tenantCustomizedInformation** | Clients | Créer, mettre à jour ou supprimer un site web client ou des informations de contact | Phare |
| **unassignTag** | Clients | Supprimer une balise d’un client | Phare |
| **Valider** | Clients | Tester un plan de déploiement | Azure AD |
| **blockUserSignin** | Utilisateurs | Bloquer la connexion | Azure AD |
| **confirmUsersCompromised** | Utilisateurs | Confirmer qu’un utilisateur est compromis | Azure AD |
| **dismissUsersRisk** | Utilisateurs | Ignorer le risque de l’utilisateur | Azure AD |
| **resetUserPassword** | Utilisateurs | Réinitialiser le mot de passe | Azure AD |
| **getConditionalAccessPolicies** | Utilisateurs | Afficher les stratégies d’autorité de certification nécessitant l’authentification multifacteur | Azure AD |
| **getTenantIDToTenantNameMap** | Utilisateurs | Rechercher des ID | Azure AD |
| **getUsers** | Utilisateurs | Rechercher des utilisateurs | Azure AD |
| **getUsersWithoutMfa** | Utilisateurs | Afficher les utilisateurs non inscrits pour l’authentification multifacteur | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Utilisateurs | Afficher les utilisateurs non inscrits pour SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Utilisateurs | Activer l’authentification multifacteur (MFA) avec les paramètres de sécurité par défaut | Azure AD |
|**getCompliancePolicyInfo** | Appareils | Afficher une stratégie | MEM
|**getDeviceCompliancePolicyStates** | Appareils | Afficher les états de stratégie | MEM
|**getDeviceCompliancePolicySettingStates** | Appareils | Afficher les paramètres non conformes | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Appareils | Afficher les appareils non conformes | MEM
|**getTenantsDeviceCompliancePolicies** | Appareils | Comparer les stratégies | MEM
| **restartDevice** | Appareils | Redémarrer | MEM |
| **syncDevice** | Appareils | Synchronisation | MEM |
| **rebootNow** | Gestion des menaces | Redémarrer | MEM |
| **reprovisionner** | Windows 365 | Nouvelle tentative d’approvisionnement | Windows 365 |
| **getDeviceUserInfo** | Gestion des menaces | Afficher les informations utilisateur de l’appareil managé  | MEM |
| **getManagedDevice**, **remoteActionAudits** ou **deviceActionResults** | Gestion des menaces | Afficher les informations sur les appareils gérés  | MEM |
| **windowsDefenderScanFull** | Gestion des menaces | Analyse complète | MEM |
| **windowsDefenderScan** | Gestion des menaces | Analyse rapide | MEM |
| **windowsDefenderUpdateSignatures** | Gestion des menaces | Mettre à jour l’antivirus | MEM |

## <a name="next-steps"></a>Prochaines étapes

Utilisez Microsoft API Graph pour accéder à d’autres événements d’audit, si nécessaire. Pour plus d’informations, consultez [Vue d’ensemble de la gestion multilocataire à l’aide de l’API Microsoft 365 Lighthouse](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Contenu associé

[MICROSOFT 365 LIGHTHOUSE FAQ](m365-lighthouse-faq.yml) (article)\
[Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)