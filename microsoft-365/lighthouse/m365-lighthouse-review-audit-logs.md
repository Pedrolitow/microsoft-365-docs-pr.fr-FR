---
title: Examiner les journaux d’audit
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
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment consulter les journaux d’audit.
ms.openlocfilehash: 69eb057c0b6a7daf835ec613b7d386e1a7fbfbaa
ms.sourcegitcommit: 6e43aeff217afe97876137b1ead8df26db6e9937
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/16/2022
ms.locfileid: "62859240"
---
# <a name="review-audit-logs"></a>Examiner les journaux d’audit

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences](m365-lighthouse-requirements.md). Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse journaux d’audit enregistrent les actions qui génèrent une modification dans le Groupement ou d’Microsoft 365 services. Créer, modifier, supprimer, affecter et actions distantes créent tous des événements d’audit que vous pouvez examiner. Par défaut, l’audit est activé pour tous les clients. Elle ne peut pas être désactivée.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher les journaux d’audit, vous devez avoir l’une des autorisations suivantes :

- Azure Active Directory (Azure AD) : administrateur général du client partenaire

- Rôle de l’Centre partenaires Microsoft - Agent d’administration

## <a name="review-audit-logs"></a>Examiner les journaux d’audit

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Journaux d’audit**.

    > [!NOTE]
    > L’accès aux nouveaux journaux peut prendre jusqu’à 1 heure. Go to the respective service to see the most recent changes.

2. Filtrez les journaux, si nécessaire, en utilisant les options suivantes :

    - **Plage de dates** : mois, semaine ou jour précédents.
    - **Clients : balises** de client ou noms de clients.
    - **Activité** : Microsoft 365 type d’activité qui correspond à l’action entreprise. Pour plus d’informations, voir [le tableau Activités](#activities) .
    - **Initiée par** - Qui l’action.

3. Sélectionnez un journal dans la liste pour voir tous les détails, y compris le **corps de la** demande.

    Pour exporter les données du journal vers un fichier de valeurs séparées par des virgules (.csv), sélectionnez **Exporter**.

## <a name="activities"></a>Activités

Le tableau suivant répertorie les activités capturées dans les journaux d’audit de la sécurité. La liste est sujette à modification à mesure que de nouvelles actions sont créées. Vous pouvez utiliser l’activité répertoriée dans le journal d’audit pour voir quelle action a été lancée.<br><br>

| Nom de l’activité | Zone en île | Action initiée | Service impacté |
|--|--|--|--|
| **apply** | Clients | Appliquer un plan de déploiement | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Clients | Appliquer une balise à partir d’un client | Île |
| **changeDeploymentStatus** | Clients | État du plan d’action pour le plan de déploiement | Île |
| **offboardTenant** | Clients | Désactiver un client | Île |
| **resetTenantOnboardingStatus** | Clients | Réactive d’un client | Île |
| **tenantTags** | Clients | Créer ou supprimer une balise | Île |
| **tenantCustomizedInformation** | Clients | Créer, mettre à jour ou supprimer un site web client ou des informations de contact | Île |
| **unassignTag** | Clients | Supprimer une balise d’un client | Île |
| **blockUserSignin** | Utilisateurs | Bloquer la sign-in | Azure AD |
| **confirmUsersCompromised** | Utilisateurs | Vérifier qu’un utilisateur est compromis | Azure AD |
| **dismissUsersRisk** | Utilisateurs | Ignorer les risques pour l’utilisateur | Azure AD |
| **resetUserPassword** | Utilisateurs | Réinitialiser le mot de passe | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Utilisateurs | Activer l’authentification multifacteur (MFA) avec des paramètres de sécurité par défaut | Azure AD |
| **restartDevice** | Appareils | Redémarrer | MEM |
| **syncDevice** | Appareils | Synchronisation | MEM |
| **rebootNow** | Gestion des menaces | Redémarrage | MEM |
| **reprovision** | Windows 365 | Nouvelle tentative d’approvisionnement | Windows 365 |
| **windowsDefenderScanFull** | Gestion des menaces | Analyse complète | MEM |
| **windowsDefenderScan** | Gestion des menaces | Analyse rapide | MEM |
| **windowsDefenderUpdateSignatures** | Gestion des menaces | Mettre à jour un antivirus | MEM |

## <a name="next-steps"></a>Prochaines étapes

Si vous avez besoin d’informations supplémentaires, utilisez l’API microsoft Graph pour accéder à d’autres événements d’audit. Pour plus d’informations, voir [Vue d’ensemble de la gestion multi-locataires à l’aide de l’API Microsoft 365 Lighthouse client](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Contenu associé

[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
