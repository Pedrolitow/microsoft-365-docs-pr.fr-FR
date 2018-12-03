---
title: 'Étape 2 : Protéger des comptes Administrateur général'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez vos comptes d’administrateur pour une protection maximale.
ms.openlocfilehash: ccab7c8526817ee5140a5315c56f6f8a42f085d2
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867476"
---
# <a name="step-2-protect-global-administrator-accounts"></a>Étape 2 : Protéger des comptes Administrateur général

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

Lors de cette étape, vous aiderez à empêcher des attaques numériques dans votre organisation en vérifiant que vos comptes d’administrateur sont aussi sécurisés que possible. Pour ce faire, vous devez :

- créer des comptes Administrateur général dédiés avec des [mot de passe très forts](https://support.microsoft.com//help/4026406/microsoft-account-create-a-strong-password) et les utiliser uniquement en cas de nécessité ;
- effectuer des tâches d’administration quotidienne en attribuant des rôles d’administrateur spécifiques (par exemple, administrateur Exchange ou administrateur de mots de passe) aux comptes d’utilisateur de votre personnel informatique, selon les besoins.

Pour vos comptes Administrateur général dédiés, vous devez aussi effectuer les opérations suivantes :

1. Testez les paramètres d’authentification multifacteur par compte d’utilisateur ou par accès conditionnel sur un compte d’utilisateur test afin de vérifier que l’authentification multifacteur fonctionne correctement et de manière prévisible. L’authentification multifacteur nécessite une forme secondaire d’authentification (par exemple, un code de vérification envoyé à un smartphone).
2. Configurez l’authentification multifacteur pour chacun des comptes Administrateur général d’Office 365 dédiés et utilisez la forme d’authentification secondaire disponible la plus forte dans votre organisation. Reportez-vous à la rubrique relative à l’[authentification multifacteur](identity-multi-factor-authentication.md) pour plus d’informations.
2. Utiliser une stratégie d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général. Voir [Protection des comptes d’administrateur](identity-access-prerequisites.md#protecting-administrator-accounts) pour plus d’informations.
4. Utiliser une stratégie Office 365 Cloud App Security pour surveiller l’activité du compte Administrateur général. Reportez-vous à la rubrique [Configurez une sécurité accrue pour Office 365](infoprotect-configure-increased-security-office-365.md) pour plus d’informations.

Reportez-vous à la rubrique [Protéger vos comptes d’administrateur général Office 365](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts) pour plus d’informations sur la configuration.

> [!Note]
> Les organisations doivent utiliser des identités exclusivement cloud pour créer des comptes privilégiés (par exemple, administrateurs généraux pour les scénarios d’accès en situation d’urgence comme une cyber-attaque). Pour plus d’informations, voir [Gérer les comptes d’administration d’urgence dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access).

Les résultats de cette étape sont les suivants :

- Les seuls comptes d’utilisateur dans votre abonnement dotés du rôle Administrateur général sont le nouvel ensemble de comptes Administrateur général dédiés. Vérifiez cela avec la commande PowerShell Windows Azure AD V2 suivante : 
  ```
  Get-AzureADDirectoryRole | Where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```
- Tous les autres comptes d’utilisateur qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur qui sont associés à leurs responsabilités.

> [!Note]
> Reportez-vous à [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell) pour obtenir des instructions sur l’installation du module Azure AD V2 PowerShell et la connexion.

|||
|:-------|:-----|
|![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : protéger des comptes Administrateur général](protect-global-administrator-accounts-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-global-admin) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step3.png)| [Configurez des administrateurs généraux à la demande](identity-privileged-identity-management.md) |

