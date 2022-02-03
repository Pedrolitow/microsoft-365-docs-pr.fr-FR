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
ms.openlocfilehash: a2c9efe88930ad0aae197a5cac26cf06b1386a53
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62354935"
---
# <a name="review-audit-logs"></a>Examiner les journaux d’audit

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences](m365-lighthouse-requirements.md). Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse journaux d’audit enregistrent les actions qui génèrent une modification dans le Groupement ou d’Microsoft 365 services. Créer, modifier, supprimer, affecter et actions distantes créent tous des événements d’audit que vous pouvez examiner. Par défaut, l’audit est activé pour tous les clients. Elle ne peut pas être désactivée.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher les journaux d’audit, vous devez avoir l’une des autorisations suivantes :

- Azure AD - Administrateur général du client partenaire

- Rôle de l’Centre partenaires - Agent d’administration

## <a name="review-logs"></a>Consulter les journaux

1. Dans le volet de navigation de gauche de l’écran, sélectionnez **Journaux d’audit**.

    > [!NOTE]
    > L’accès aux nouveaux journaux peut prendre jusqu’à 1 heure. Go to the respective service to see the most recent changes.

2. Pour filtrer les journaux, affinez la liste à l’aide des options suivantes :

    - **Plage de dates** : mois, semaine ou jour précédents.
    - **Clients : balises** de client ou noms de clients.
    - **Activité** : Microsoft 365 type d’activité qui correspond à l’action entreprise. Pour plus d’informations, voir le tableau Types d’activité.
    - **Initiée par** - Qui l’action.

3. Sélectionnez un journal dans la liste pour voir tous les détails, y compris le **corps de la** demande.

**Sélectionnez Exporter** pour exporter les données du journal dans un fichier de valeurs séparées par des virgules (.csv).

## <a name="activity-types"></a>Types d’activité

Le tableau suivant est une liste des types d’activité capturés dans les journaux d’audit de la sécurité. La liste est sujette à modification à mesure que de nouvelles actions sont créées. Vous pouvez utiliser la valeur d’activité du journal d’audit pour voir quelle action a été lancée.

| Nom de l’activité    | Zone dans Microsoft 365 Lighthouse | Action initiée  | Service impacté           |
|------------------|----------------------------------|-------------------|----------------------------|
|**apply**                                   | Clients                          | Appliquer un plan de déploiement                                           | Azure AD, Microsoft Endpoint Manager                   |
|**assignTag**                                | Clients                          | Appliquer une balise à partir d’un client                                      | Microsoft 365 Lighthouse   |
|**changeDeploymentStatus**                   | Clients                          | État du plan d’action pour le plan de déploiement                        | Microsoft 365 Lighthouse   |
|**offboardTenant**                            | Clients                          | Désactiver un client                                          | Microsoft 365 Lighthouse   |
|**resetTenantOnboardingStatus**              | Clients                          | Réactive d’un client                                              | Microsoft 365 Lighthouse   |
|**tenantTags**                               | Clients                          | Créer ou supprimer une balise                                           | Microsoft 365 Lighthouse   |
|**tenantCustomizedInformation**              | Clients                          | Créer, mettre à jour ou supprimer des informations de contact ou de site web client | Microsoft 365 Lighthouse   |
|**unassignTag**                              | Clients                          | Supprimer une balise d’un client                                    | Microsoft 365 Lighthouse   |
| **blockUserSignin**                          | Utilisateurs                            | Bloquer la sign-in                                                     | Azure AD                   |
| **confirmUsersCompromised**                  | Utilisateurs                            | Confirmer que l’utilisateur a été compromis                                        | Azure AD                   |
| **dismissUsersRisk**                         | Utilisateurs                            | Ignorer les risques pour l’utilisateur                                                | Azure AD                   |
| **resetUserPassword**                        | Utilisateurs                            | Réinitialiser le mot de passe                                                   | Azure AD                   |
| **setCustomerSecurityDefaultsEnabledStatus** | Utilisateurs                            | Activer l’mf avec paramètres de sécurité par défaut                               | Azure AD                   |
|**restartDevice**                            | Appareils                          | Redémarrer                                                          | Microsoft Endpoint Manager |
| **syncDevice**                               | Appareils                          | Synchronisation                                                             | Microsoft Endpoint Manager |
| **rebootNow**                                | Gestion des menaces                | Redémarrage                                                           | Microsoft Endpoint Manager |
| **reprovision**                              | Clients                          | Nouvelle tentative d’approvisionnement                                               | Windows 365                |
| **windowsDefenderScanFull**                  | Gestion des menaces                | Analyse complète                                                       | Microsoft Endpoint Manager |
| **windowsDefenderScan**                      | Gestion des menaces                | Analyse rapide                                                       | Microsoft Endpoint Manager |
| **windowsDefenderUpdateSignatures**          | Gestion des menaces                | Mettre à jour un antivirus                                                | Microsoft Endpoint Manager |

## <a name="next-steps"></a>Prochaines étapes

Si vous avez besoin d’informations supplémentaires, vous pouvez utiliser l’API Microsoft Graph pour accéder à d’autres événements d’audit. Pour plus d’informations, voir [Vue d’ensemble de la gestion multi-locataires à l’aide de l’API Microsoft 365 Lighthouse client](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Contenu connexe

[Microsoft 365 Lighthouse FAQ](m365-lighthouse-faq.yml) (article)
