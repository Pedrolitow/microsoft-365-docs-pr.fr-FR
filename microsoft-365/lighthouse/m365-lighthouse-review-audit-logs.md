---
title: Examiner les journaux d’audit dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: vivkuma
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment consulter les journaux d’audit.
ms.openlocfilehash: bf31aa45add04668379990c2d4fb166304223cb1
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68658948"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>Examiner les journaux d’audit dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse journaux d’audit enregistrent les actions qui génèrent une modification dans Lighthouse ou d’autres services Microsoft 365. Les actions Créer, modifier, supprimer, attribuer et distantes créent des événements d’audit que vous pouvez examiner. Par défaut, l’audit est activé pour tous les clients. Elle ne peut pas être désactivée.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher les journaux d’audit, vous devez disposer de l’une des autorisations suivantes :

- Rôle Azure Active Directory (Azure AD) - Administrateur général du locataire partenaire

- Rôle Espace partenaires Microsoft - Agent Administration

## <a name="review-audit-logs"></a>Consulter les journaux d’audit

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Journaux d’audit**.

    > [!NOTE]
    > Les nouveaux journaux peuvent prendre jusqu’à 1 heure. Accédez au service respectif pour voir les modifications les plus récentes.

2. Filtrez les journaux, si nécessaire, à l’aide des options suivantes :

    - **Plage de dates** : mois, semaine ou jour précédents.
    - **Locataires : étiquettes** de locataire ou noms de locataires clients.
    - **Activité** : type d’activité Microsoft 365 qui correspond à l’action effectuée. Pour plus d’informations, consultez la table [Activités](#activities) .
    - **Initié par** : qui a initié l’action.

3. Sélectionnez un journal dans la liste pour afficher les détails complets, y compris le corps de la **demande** .

    Pour exporter des données de journal vers un fichier de valeurs séparées par des virgules (.csv), sélectionnez **Exporter**.

## <a name="activities"></a>Activités

Le tableau suivant répertorie les activités capturées dans les journaux d’audit Lighthouse. La liste est susceptible d’être modifiée à mesure que de nouvelles actions sont créées. Vous pouvez utiliser l’activité répertoriée dans le journal d’audit pour voir quelle action a été lancée.<br><br>

| Nom de l’activité | Zone dans Lighthouse | Action lancée | Service impacté |
|--|--|--|--|
| **appliquer** ou **déployer** | Clients | Appliquer un plan de déploiement | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Clients | Appliquer une étiquette à partir d’un client | Phare |
| **changeDeploymentStatus** ou **assign** | Clients | Mettre à jour l’état du plan d’action pour le plan de déploiement | Phare |
| **offboardTenant** | Clients | Désactiver un client | Phare |
| **resetTenantOnboardingStatus** | Clients | Réactif d’un client | Phare |
| **tenantTags** | Clients | Créer ou supprimer une balise | Phare |
| **tenantCustomizedInformation** | Clients | Créer, mettre à jour ou supprimer un site web ou des informations de contact d’un client | Phare |
| **unassignTag** | Clients | Supprimer une étiquette d’un client | Phare |
| **Valider** | Clients | Tester un plan de déploiement | Azure AD |
| **blockUserSignin** | Utilisateurs | Bloquer la connexion | Azure AD |
| **confirmUsersCompromised** | Utilisateurs | Confirmer qu’un utilisateur est compromis | Azure AD |
| **dismissUsersRisk** | Utilisateurs | Ignorer le risque de l’utilisateur | Azure AD |
| **resetUserPassword** | Utilisateurs | Réinitialiser le mot de passe | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Utilisateurs | Activer l’authentification multifacteur (MFA) avec les paramètres de sécurité par défaut | Azure AD |
| **restartDevice** | Appareils | Redémarrer | Mem |
| **syncDevice** | Appareils | Synchronisation | Mem |
| **rebootNow** | Gestion des menaces | Redémarrer | Mem |
| **reprovisionner** | Windows 365 | Nouvelle tentative d’approvisionnement | Windows 365 |
| **windowsDefenderScanFull** | Gestion des menaces | Analyse complète | Mem |
| **windowsDefenderScan** | Gestion des menaces | Analyse rapide | Mem |
| **windowsDefenderUpdateSignatures** | Gestion des menaces | Mettre à jour l’antivirus | Mem |

## <a name="next-steps"></a>Prochaines étapes

Utilisez Microsoft API Graph pour accéder à d’autres événements d’audit, si nécessaire. Pour plus d’informations, consultez [Vue d’ensemble de la gestion multilocataire à l’aide de l’API Microsoft 365 Lighthouse](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)\
[Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)