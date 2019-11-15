---
title: 'Étape 1 : Créer et protéger vos comptes d’administrateur général'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/20/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Vos comptes d’administrateur général ont besoin d’un traitement spécial leur assurant une protection contre la compromission des informations d’identification.
ms.openlocfilehash: 257caf197df74d32b438a17158598237cf4c58b5
ms.sourcegitcommit: 1d376287f6c1bf5174873e89ed4bf7bb15bc13f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "38627080"
---
# <a name="step-1-create-and-protect-your-global-admin-accounts"></a>Étape 1 : Créer et protéger vos comptes d’administrateur général

![Phase 2 - Identité](./media/deploy-foundation-infrastructure/identity_icon-small.png)

<a name="identity-global-admin"></a>
## <a name="protect-global-administrator-accounts"></a>Protéger des comptes d’administrateur général

*Cette étape est requise et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

Dans le cadre de cette section, vous allez contribuer à empêcher des attaques numériques dirigées contre votre organisation en vérifiant que vos comptes d’administrateur sont aussi sécurisés que possible. Pour ce faire, vous devez :

- Créer plus d'un compte d'administrateur général dédié avec des [mot de passe forts](https://support.microsoft.com//help/4026406/microsoft-account-create-a-strong-password) et les utiliser uniquement en cas de nécessité.
- Effectuer des tâches d’administration quotidienne en attribuant des rôles d’administrateur spécifiques (par exemple, administrateur Exchange ou administrateur Mot de passe) aux comptes d’utilisateur de votre personnel informatique, selon les besoins.

Pour vos comptes Administrateur général dédiés, vous devez aussi effectuer les opérations suivantes :

1. Testez les paramètres d'authentification multifacteur Azure (MFA) par compte utilisateur ou par accès conditionnel sur un compte utilisateur test pour vous assurer que l'authentification multifacteur fonctionne correctement et de manière prévisible. L’authentification multifacteur requiert une forme secondaire d’authentification, telle qu’un code de vérification envoyé à un smartphone.
2. Créez et activez une stratégie d'accès conditionnel pour vos comptes d'administrateur général qui nécessite l'authentification multifacteur et utilise la forme d'authentification secondaire la plus efficace disponible au sein de votre entreprise. Pour plus d’informations, consultez [Authentification multifacteur Azure](identity-access-prerequisites.md#protecting-administrator-accounts).

Pour des protections supplémentaires, consultez [Protéger vos comptes d’administrateur général Office 365](https://docs.microsoft.com/office365/enterprise/protect-your-global-administrator-accounts#additional-protections-for-enterprise-organizations).

> [!Note]
> Les comptes d'urgence pour les scénarios catastrophes en cas d'urgence, telle une cyberattaque, devraient être des comptes de Cloud uniquement. Vous pouvez également disposer de comptes d’administrateur général (éligibles ou permanents) qui ne sont pas uniquement dans le Cloud. Pour plus d’informations, consultez [Gestion des comptes d’administration de l’accès d’urgence dans Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-emergency-access).

Les résultats de cette section sont les suivants :

- Les seuls comptes d’utilisateurs de votre abonnement dotés du rôle Administrateur général sont les comptes Administrateur général dédiés. Pour le vérifier, utilisez la commande Azure Active Directory PowerShell pour Graph suivante : 
  ```powershell
  Get-AzureADDirectoryRole | Where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```
- Tous les autres comptes d’utilisateurs qui gèrent les services de votre abonnement ont des rôles d’administrateur associés à leurs responsabilités.

> [!Note]
> Reportez-vous à [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell) pour obtenir des instructions sur l’installation du module Azure AD PowerShell pour Graph et la connexion.

|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)|  Pour tester cette configuration dans un environnement de laboratoire de test, consultez le [Guide de laboratoire de test Protéger des comptes d’administrateur général](protect-global-administrator-accounts-microsoft-365-test-environment.md). |
|||

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-global-admin) pour cette étape.


<a name="identity-pim"></a>
## <a name="set-up-on-demand-administrators"></a>Configurer des administrateurs à la demande

*Cette étape est facultative et s’applique uniquement à la version E5 de Microsoft 365 Entreprise*

Dans cette section, vous allez configurer Azure AD Privileged Identity Management (PIM) afin de réduire la durée pendant laquelle vos comptes d’administrateur général sont vulnérables aux attaques d’utilisateurs malveillants. PIM assure une attribution à la demande, juste-à-temps des rôles d’administrateur général en fonction des besoins.  

Au lieu d'être des administrateurs permanents, vos comptes d'administrateur deviennent des administrateurs admissibles. Le rôle d'administrateur est inactif tant que vous n'en avez pas besoin. Vous devez ensuite effectuer un processus d’activation pour ajouter le rôle d’administrateur au compte d’administrateur pour une durée spécifique. Une fois l’expiration du délai écoulée, PIM supprime le rôle d’administrateur du compte d’administrateur.

PIM est disponible avec Azure Active Directory Premium P2, qui est inclus avec Microsoft 365 Entreprise E5. Vous pouvez également acheter des licences Azure Active Directory Premium P2 individuelles pour vos comptes d’administrateur.

Pour activer Azure PIM pour votre client Azure AD et vos comptes d’administrateur, consultez les [étapes de configuration de PIM](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure).

Reportez-vous à la rubrique [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure AD](https://docs.microsoft.com/azure/active-directory/admin-roles-best-practices) pour développer une feuille de route détaillée qui sécurise l’accès privilégié contre les cyber-attaquants.

Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](identity-exit-criteria.md#crit-identity-pim) pour cette étape.


<a name="identity-pam"></a>
## <a name="privileged-access-management"></a>Gestion des accès privilégiés

Vous activez la gestion des accès privilégiés en configurant des stratégies qui indiquent l’accès juste-à-temps pour les activités basées sur des tâches dans votre client Office 365. Elle peut vous aider à protéger votre organisation contre les violations qui pourraient survenir par le biais de comptes d’administrateur privilégiés existants qui donnent un accès permanent à des données sensibles ou à des paramètres de configuration critiques. Par exemple, vous pouvez configurer une stratégie de gestion des accès privilégiés qui requiert une approbation explicite pour pouvoir accéder aux paramètres de boîte aux lettres de votre organisation dans votre client Office 365 et les modifier.

Pour cette étape, vous allez activer la gestion des accès privilégiés dans votre client Office 365 et configurer les stratégies d’accès privilégiés qui permettent de renforcer la sécurité des accès basés sur les tâches à vos paramètres de configuration et à vos données Office 365 pour votre organisation. Il existe trois étapes simples pour commencer à utiliser les accès privilégiés dans votre organisation Office 365 :

- Création d’un groupe d’approbateurs
- Activation des accès privilégiés
- Création de stratégies d’approbation

Une fois configurée, la gestion des accès privilégiés permettra à votre organisation de fonctionner sans aucun privilège permanent et de fournir une sécurité renforcée contre les lacunes d’un accès administratif permanent comme celui-ci. L’accès privilégié requiert des approbations pour exécuter toute tâche pour laquelle une stratégie d’approbation associée a été définie. Les utilisateurs ayant besoin d’exécuter des tâches incluses dans la stratégie d’approbation doivent demander l’approbation de l’accès et l’obtenir afin de disposer des autorisations nécessaires pour exécuter les tâches définies dans la stratégie.

Pour activer la gestion des accès privilégiés d’Office 365, consultez la rubrique relative à la [configuration de la gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration).

Pour plus d’informations, reportez-vous à la rubrique relative à la [gestion des accès privilégiés dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-overview).


|||
|:-------|:-----|
|![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon-small.png)|  Pour tester cette configuration dans un environnement de laboratoire de test, consultez le [Guide de laboratoire de test Gestion des accès privilégiés](privileged-access-microsoft-365-enterprise-dev-test-environment.md). |
|||

Comme point de contrôle intermédiaire, consultez les [critères de sortie](identity-exit-criteria.md#crit-identity-pam) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![Étape 2](./media/stepnumbers/Step2.png)| [Sécuriser vos mots de passe](identity-secure-your-passwords.md) |

