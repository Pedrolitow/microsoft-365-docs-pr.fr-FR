---
title: Rôles d’utilisateur pour le démarrage des essais Microsoft 365
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Découvrez les rôles d’utilisateur nécessaires pour vous inscrire à une version d’évaluation de Microsoft 365 Purview, Priva et des produits de sécurité.
ms.openlocfilehash: d4613faf7815ca5d8f705a9b1efe76b5f75c435e
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67599778"
---
# <a name="user-roles-for-starting-microsoft-365-trials"></a>Rôles d’utilisateur pour le démarrage des essais Microsoft 365

Cet article décrit les rôles d’utilisateur requis pour inscrire votre organisation dans une version d’évaluation de Microsoft 365.

## <a name="who-can-start-all-trials"></a>Qui peut démarrer toutes les versions d’évaluation ?

Un utilisateur disposant de l’un des rôles répertoriés ci-dessous peut démarrer n’importe quelle version d’évaluation de Microsoft 365.
 
| Rôle | Groupe de rôles | Où attribuer | 
| :------------- | :-------------: | :------------: |
| Administrateur général | Administrateur général   | Portail de conformité Purview > autorisations > rôles > Azure AD |
| Administration de facturation | Administrateur de facturation | Portail de conformité Purview > autorisations > solutions Purview > rôles |

## <a name="roles-for-starting-specific-trials"></a>Rôles pour le démarrage d’essais spécifiques

Les essais Purview, Priva et Defender permettent aux utilisateurs ayant des rôles spécifiques en dehors de Administrateur général et de facturation Administration de commencer leurs essais. Pour plus d’informations, consultez les tableaux ci-dessous.

#### <a name="purview-trials"></a>Essais Purview

Les essais Purview incluent la version d’évaluation **des solutions Microsoft Purview** et la version **d’évaluation premium du Gestionnaire de conformité** . 

| Rôle | Groupe de rôles | Où attribuer | 
| :------------- | :-------------: | :------------: |
| Administrateur de conformité | Administrateur de conformité   | Portail de conformité Purview > autorisations > solutions Purview > rôles |
| Gestion de la conformité DLP, Information Protection Administration, RecordManagement, Gestion de la rétention et Administrateur d’étiquette de confidentialité | Administrateur de conformité des données | Portail de conformité Purview > autorisations > solutions Purview > rôles |

#### <a name="priva-trials"></a>Essais Priva

Les essais priva comprennent le procès **Privacy Risk Management** et le procès **Subject Rights Requests** .

| Rôle | Groupe de rôles | Où attribuer | 
| :------------- | :-------------: | :------------: |
| Administration de gestion de la confidentialité | Administrateurs de gestion de la confidentialité   | Portail de conformité Purview > autorisations > solutions Purview > rôles |
| Demande de droits de sujet Administration | Administrateurs des demandes de droits d’objet | Portail de conformité Purview > autorisations > solutions Purview > rôles |

#### <a name="security-trials"></a>Essais de sécurité

Les essais de sécurité incluent la version d’évaluation **de Gestion des vulnérabilités Defender** et la version **d’évaluation du module complémentaire Gestion des vulnérabilités Defender** . Les utilisateurs ont besoin d’un rôle avec l’une des autorisations répertoriées ci-dessous pour démarrer une version d’évaluation.

| Autorisation | Où attribuer | 
| :------------- | :-------------: |
Opérations de sécurité  | Microsoft 365 Defender portail > autorisations > rôles de points de terminaison & groupes > rôles  |
| La gestion des menaces et des vulnérabilités | Microsoft 365 Defender portail > autorisations > rôles de points de terminaison & groupes > rôles |

## <a name="how-to-assign-roles"></a>Procédure d’attribution des rôles

Pour plus d’informations sur l’attribution de rôles d’utilisateur et d’autorisations, consultez les articles suivants :

- **Rôles d’administrateur Microsoft 365** : [à propos des rôles d’administrateur dans le Centre d'administration Microsoft 365](../admin/add-users/about-admin-roles.md)
- **Microsoft Purview et Priva** : [autorisations dans le portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md)
- **Microsoft 365 Defender** : [Créer et gérer des rôles pour le contrôle d’accès en fonction du rôle](../security/defender-endpoint/user-roles.md)