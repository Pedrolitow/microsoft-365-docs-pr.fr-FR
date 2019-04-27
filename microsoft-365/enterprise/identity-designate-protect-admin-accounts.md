---
title: 'Étape 2 : sécuriser vos identités privilégiées'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/01/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Comprenez et configurez vos comptes d’administrateur pour une protection maximale.
ms.openlocfilehash: 0be82fc6f431001c69e79a0a26007c54a87424c3
ms.sourcegitcommit: 3b2d3e2b38c4860db977e73dda119a465c669fa4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2019
ms.locfileid: "33353086"
---
# <a name="step-2-secure-your-privileged-identities"></a>Étape 2 : sécuriser vos identités privilégiées

![](./media/deploy-foundation-infrastructure/identity_icon-small.png)

<a name="identity-global-admin"></a>
## <a name="protect-global-administrator-accounts"></a>Protéger des comptes d’administrateur général

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans le cadre de cette section, vous allez contribuer à empêcher des attaques numériques dirigées contre votre organisation en vérifiant que vos comptes d’administrateur sont aussi sécurisés que possible. Pour ce faire, vous devez :

- créer des comptes Administrateur général dédiés avec des [mot de passe très forts](https://support.microsoft.com//help/4026406/microsoft-account-create-a-strong-password) et les utiliser uniquement en cas de nécessité ;
- effectuer des tâches d’administration quotidienne en attribuant des rôles d’administrateur spécifiques (par exemple, administrateur Exchange ou administrateur de mots de passe) aux comptes d’utilisateur de votre personnel informatique, selon les besoins.

Pour vos comptes Administrateur général dédiés, vous devez aussi effectuer les opérations suivantes :

1. Testez les paramètres d’authentification multifacteur par compte d’utilisateur ou par accès conditionnel sur un compte d’utilisateur test afin de vérifier que l’authentification multifacteur fonctionne correctement et de manière prévisible. L’authentification multifacteur nécessite une forme secondaire d’authentification (par exemple, un code de vérification envoyé à un smartphone).
2. Configurez l’authentification multifacteur pour chacun des comptes Administrateur général d’Office 365 dédiés et utilisez la forme d’authentification secondaire disponible la plus forte dans votre organisation. Reportez-vous à la rubrique relative à l’[authentification multifacteur](identity-multi-factor-authentication.md#identity-mfa) pour plus d’informations.
2. Utiliser une stratégie d’accès conditionnel pour exiger l’authentification multifacteur pour les comptes d’administrateur général. Voir [Protection des comptes d’administrateur](identity-access-prerequisites.md#protecting-administrator-accounts) pour plus d’informations.

Reportez-vous à la rubrique [Protéger vos comptes d’administrateur général Office 365](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts) pour plus d’informations sur la configuration.

> [!Note]
> Les organisations doivent utiliser des identités exclusivement cloud pour créer des comptes privilégiés (par exemple, administrateurs généraux pour les scénarios d’accès en situation d’urgence comme une cyber-attaque). Pour plus d’informations, voir [Gérer les comptes d’administration d’urgence dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access).

Les résultats de cette section sont :

- Les seuls comptes d’utilisateurs de votre abonnement dotés du rôle Administrateur général sont les comptes du nouvel ensemble de comptes Administrateur général dédiés. Vérifiez cela avec la commande Azure Active Directory PowerShell pour Graph suivante : 
  ```
  Get-AzureADDirectoryRole | Where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```
- Tous les autres comptes d’utilisateurs qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur associés à leurs responsabilités.

> [!Note]
> Reportez-vous à [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell) pour obtenir des instructions sur l’installation du module Azure AD PowerShell pour Graph et la connexion.

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)| [Guide du laboratoire de test : protéger des comptes Administrateur général](protect-global-administrator-accounts-microsoft-365-test-environment.md) |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-global-admin) pour cette section.


<a name="identity-pim"></a>
## <a name="set-up-on-demand-global-administrators"></a>Configurer des administrateurs généraux à la demande

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Dans le cadre de cette section, vous allez configurer Azure AD Privileged Identity Management (PIM) afin de réduire la durée pendant laquelle vos comptes d’administrateur général sont vulnérables aux attaques d’utilisateurs malveillants. PIM assure une affectation à la demande, juste-à-temps du rôle d’administrateur général en fonction des besoins.  

Au lieu que vos comptes d’administrateur général soient un administrateur permanent, ils deviennent des administrateurs éligibles. Le rôle Administrateur général est inactif tant que personne n’en a besoin. Vous effectuerez ensuite un processus d’activation pour ajouter le rôle Administrateur général au compte d’administrateur général pour une durée spécifique. À l’expiration du délai, PIM supprime le rôle Administrateur général du compte d’administrateur général.

PIM est disponible avec Azure Active Directory Premium P2, qui est inclus avec Microsoft 365 Entreprise E5. Vous pouvez également acheter des licences Azure Active Directory Premium P2 individuelles pour vos comptes d’administrateur général.

Pour activer Azure PIM pour votre client Azure AD et vos comptes d’administrateur général, consultez les [étapes de configuration de PIM](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).

Reportez-vous à la rubrique [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure AD](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices) pour développer une feuille de route détaillée qui sécurise l’accès privilégié contre les cyber-attaquants.

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pim) pour cette section.


## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step3.png)| [Configurer une identité hybride](identity-azure-ad-connect.md) |

