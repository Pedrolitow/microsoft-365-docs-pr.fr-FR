---
title: Protéger vos comptes Microsoft 365 administrateur général
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365initiative-coredeploy
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Cet article fournit des informations sur la protection de l’accès administrateur général à Microsoft 365 abonnement.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9693a8321643539e21ff10f3c624a0558916eb29
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198348"
---
# <a name="protect-your-microsoft-365-global-administrator-accounts"></a>Protéger vos comptes Microsoft 365 administrateur général

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les violations de sécurité d’un abonnement Microsoft 365, y compris la collecte d’informations et les attaques par hameçonnage, sont généralement dues à la compromissation des informations d’identification d’un Microsoft 365 d’administrateur général. La sécurité dans le cloud est un partenariat entre vous et Microsoft :
  
- Les services de cloud computing Microsoft reposent sur la confiance et la sécurité. Microsoft met à votre disposition des contrôles et fonctionnalités de sécurité pour vous aider à protéger vos données et applications.
    
- Il est de votre responsabilité de protéger vos données et votre identité, ainsi que d’assurer la sécurité de vos ressources locales et des composants cloud que vous contrôlez.
    
Microsoft fournit des fonctionnalités pour aider à protéger votre organisation, mais elles ne sont efficaces que si vous les utilisez. Si vous ne les utilisez pas, vous risquez d’être vulnérable aux attaques. Pour protéger vos comptes d’administrateur général, Microsoft est là pour vous aider avec des instructions détaillées pour :
  
1. Créez des Microsoft 365 administrateur général dédiés et utilisez-les uniquement si nécessaire.
    
2. Configurez l’authentification multifacteur pour Microsoft 365 comptes d’administrateur général dédiés et utilisez la forme d’authentification secondaire la plus forte.
    
> [!Note]
> Bien que cet article soit axé sur les comptes d’administrateur général, vous devez déterminer si des comptes supplémentaires avec des autorisations étendues pour accéder aux données de votre abonnement, tels que les comptes d’administrateur eDiscovery ou d’administrateur de sécurité ou de conformité, doivent être protégés de la même manière. <br > Un compte d’administrateur général peut être créé sans ajouter de licences.
  
## <a name="step-1-create-dedicated-microsoft-365-global-administrator-accounts-and-use-them-only-when-necessary"></a>Étape 1. Créer des comptes Microsoft 365 administrateur général dédiés et les utiliser uniquement si nécessaire

Il existe relativement peu de tâches administratives, telles que l’attribution de rôles à des comptes d’utilisateurs, qui nécessitent des privilèges d’administrateur général. Par conséquent, au lieu d’utiliser quotidiennement des comptes d’utilisateurs qui ont été affectés au rôle d’administrateur global, utilisez les étapes suivantes :
  
1. Déterminez l’ensemble des comptes d’utilisateurs qui ont reçu le rôle d’administrateur global. Vous pouvez le faire dans le Centre d'administration Microsoft 365 ou avec l’annuaire Azure Active (Azure AD) PowerShell suivant pour Graph commande :
  
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Global Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

2. Connectez-vous à Microsoft 365 abonnement avec un compte d’utilisateur qui a reçu le rôle d’administrateur global.
    
3. Créez jusqu’à quatre comptes d’utilisateur d’administrateur général dédiés. **Utilisez des mots de passe forts d’au moins 12 caractères.** Pour plus [d’informations, voir](https://support.microsoft.com/help/4026406/microsoft-account-create-a-strong-password) Créer un mot de passe fort. Stockez les mots de passe des nouveaux comptes dans un emplacement sécurisé. 
    
4. Attribuez le rôle d’administrateur général à chacun des nouveaux comptes d’utilisateur d’administrateur général dédiés.
    
5. Se Microsoft 365.
    
6. Connectez-vous avec l’un des nouveaux comptes d’utilisateur d’administrateur général dédiés.
    
7. Pour chaque compte d’utilisateur existant affecté au rôle d’administrateur global à l’étape 1 :
    
  - Supprimez le rôle d’administrateur global.
    
  - Attribuez des rôles d’administrateur au compte qui sont appropriés à la fonction et à la responsabilité de cet utilisateur. Pour plus d’informations sur les différents rôles d’administrateur Microsoft 365, voir [à propos des rôles d’administrateur.](/office365/admin/add-users/about-admin-roles)
    
8. Se Microsoft 365.
    
Les résultats doivent être :
  
- Les seuls comptes d’utilisateurs de votre abonnement dotés du rôle Administrateur général sont les comptes du nouvel ensemble de comptes Administrateur général dédiés. Vérifiez-le avec la commande PowerShell suivante :
    
  ```powershell
  Get-AzureADDirectoryRole | where { $_.DisplayName -eq "Company Administrator" } | Get-AzureADDirectoryRoleMember | Ft DisplayName
  ```

- Tous les autres comptes d’utilisateurs qui gèrent votre abonnement quotidiennement ont des rôles d’administrateur associés à leurs responsabilités.
    
À partir de maintenant, vous vous connectez avec les comptes d’administrateur général dédiés uniquement pour les tâches qui nécessitent des privilèges d’administrateur général. Toutes les autres Microsoft 365 administration doivent être réalisées en attribuant d’autres rôles d’administration à des comptes d’utilisateurs.
  
> [!NOTE]
> Cela nécessite des étapes supplémentaires pour vous dé connectez en tant que compte d’utilisateur quotidien et avec un compte d’administrateur général dédié. Toutefois, cette opération ne doit être effectuée qu’occasionnellement pour les opérations d’administrateur général. Considérez que la récupération de votre abonnement Microsoft 365 suite à une violation de compte d’administrateur général nécessite beaucoup plus d’étapes.
  
## <a name="step-2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-global-administrator-accounts"></a>Étape 2. Configurer l’authentification multifacteur pour vos comptes Microsoft 365 administrateur général dédiés

L’authentification multifacteur (MFA) nécessite des informations supplémentaires au-delà du nom de compte et du mot de passe. Microsoft 365 prend en charge ces méthodes de vérification supplémentaires :
  
- L’application Microsoft Authenticator

- appel téléphonique ;
    
- Code de vérification généré de manière aléatoire envoyé par le biais d’un message texte
    
- carte à puce (virtuelle ou physique) ;
    
- appareil biométrique.
    
>[!Note]
>Pour les organisations qui doivent respecter les normes du National Institute of Standards and Technology (NIST), l’utilisation d’un appel téléphonique ou de méthodes de vérification supplémentaires basées sur des SMS est restreinte. Cliquez [ici](https://pages.nist.gov/800-63-FAQ/#q-b01) pour plus d’informations.
>

Si vous êtes une petite entreprise qui utilise des comptes d’utilisateurs stockés uniquement dans le cloud (le modèle d’identité cloud uniquement), configurez l’appelez-moi en mode [MFA](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) à l’aide d’un appel téléphonique ou d’un code de vérification par SMS envoyé à un smartphone pour chaque compte d’administrateur général dédié.
    
Si vous êtes une grande organisation qui utilise un modèle Microsoft 365 identité hybride, vous avez davantage d’options de vérification. Si vous avez déjà mis en place l’infrastructure de sécurité pour une méthode d’authentification secondaire plus [forte,](../admin/security-and-compliance/set-up-multi-factor-authentication.md) configurez l’authentification multifacteur et configurez chaque compte d’administrateur général dédié pour la méthode de vérification appropriée.
  
Si l’infrastructure de sécurité de la méthode de vérification renforcée souhaitée n’est pas en place et ne fonctionne pas pour Microsoft 365 MFA, nous vous recommandons vivement de configurer des comptes d’administrateur général dédiés avec l’appelez-moi à l’aide de l’application Microsoft Authenticator, d’un appel téléphonique ou d’un code de vérification de message texte envoyé à un smartphone pour vos comptes d’administrateur général comme sécurité intermédiaire . Ne laissez pas vos comptes d’administrateur général dédiés sans la protection supplémentaire fournie par l’mf.
  
Pour plus d’informations, [consultez l’mf pour Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
Pour vous connecter à Microsoft 365 services avec mfa et PowerShell, consultez les articles suivants :

- [PowerShell for Microsoft 365 for user accounts, groups, and licenses](connect-to-microsoft-365-powershell.md)
- [Microsoft Teams](/microsoftteams/teams-powershell-install)
- [Exchange Online](/powershell/exchange/mfa-connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa)
- [SharePoint Online](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online#to-connect-with-multifactor-authentication-mfa)
- [Skype Entreprise Online](manage-skype-for-business-online-with-microsoft-365-powershell.md#connect-using-an-admin-account-with-multi-factor-authentication)

## <a name="additional-protections-for-enterprise-organizations"></a>Protections supplémentaires pour les organisations d’entreprise

Utilisez ces méthodes supplémentaires pour vous assurer que votre compte d’administrateur général et la configuration que vous effectuez en l’utilisant sont aussi sécurisés que possible.
  
### <a name="privileged-access-workstation"></a>Station de travail à accès privilégié

Pour vous assurer que l’exécution des tâches hautement privilégiées est aussi sécurisée que possible, utilisez une station de travail à accès privilégié.. Un paw est un ordinateur dédié qui est utilisé uniquement pour les tâches de configuration sensibles, telles que Microsoft 365 configuration nécessitant un compte d’administrateur général. Étant donné que cet ordinateur n’est pas utilisé quotidiennement pour la navigation internet ou la messagerie, il est mieux protégé contre les attaques et les menaces Internet.
  
Pour obtenir des instructions sur la façon de configurer une paw, voir [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices) .

Pour activer Azure PIM pour votre client Azure AD et vos comptes d’administrateur, consultez les [étapes de configuration de PIM](/azure/active-directory/active-directory-privileged-identity-management-configure).

Reportez-vous à la rubrique [Sécurisation de l’accès privilégié pour les déploiements hybrides et cloud dans Azure AD](/azure/active-directory/admin-roles-best-practices) pour développer une feuille de route détaillée qui sécurise l’accès privilégié contre les cyber-attaquants.

### <a name="azure-ad-privileged-identity-management"></a>Azure AD Privileged Identity Management

Au lieu d’attribuer définitivement le rôle d’administrateur général à vos comptes d’administrateur général, vous pouvez utiliser Azure AD Privileged Identity Management (PIM) pour activer l’attribution à la demande et juste-à-temps du rôle d’administrateur général lorsqu’il est nécessaire.
  
Vos comptes d’administrateur général ne sont plus des administrateurs permanents, mais des administrateurs éligibles. Le rôle d’administrateur général est inactif jusqu’à ce que quelqu’un en a besoin. Vous terminez ensuite un processus d’activation pour ajouter le rôle d’administrateur général au compte d’administrateur général pendant un laps de temps prédéterminé. Lorsque le délai expire, PIM supprime le rôle d’administrateur général du compte d’administrateur général.
  
L’utilisation de PIM et de ce processus réduit considérablement le temps que vos comptes d’administrateur général sont vulnérables aux attaques et à l’utilisation par des utilisateurs malveillants.

PIM est disponible avec Azure Active Directory Premium P2, qui est inclus avec Microsoft 365 E5. Vous pouvez également acheter des licences Azure Active Directory Premium P2 individuelles pour vos comptes d’administrateur.
  
Pour plus d’informations, [voir Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
  

### <a name="privileged-access-management"></a>Gestion des accès privilégiés

Vous activez la gestion des accès privilégiés en configurant des stratégies qui indiquent l’accès juste-à-temps pour les activités basées sur des tâches dans votre client. Elle peut vous aider à protéger votre organisation contre les violations qui pourraient survenir par le biais de comptes d’administrateur privilégiés existants qui donnent un accès permanent à des données sensibles ou à des paramètres de configuration critiques. Par exemple, vous pouvez configurer une stratégie de gestion des accès privilégiés qui requiert une approbation explicite pour pouvoir accéder aux paramètres de boîte aux lettres de votre organisation dans votre client et les modifier.

Pour cette étape, vous allez activer la gestion des accès privilégiés dans votre client et configurer les stratégies d’accès privilégiés qui permettent de renforcer la sécurité des accès basés sur les tâches à vos paramètres de configuration et à vos données pour votre organisation. Il existe trois étapes simples pour commencer à utiliser les accès privilégiés dans votre organisation :

- Création d’un groupe d’approbateurs
- Activation des accès privilégiés
- Création de stratégies d’approbation

La gestion des accès privilégiés permet à votre organisation de fonctionner avec zéro privilège permanent et de fournir une couche de défense contre les vulnérabilités résultant de cet accès administratif permanent. L’accès privilégié nécessite des approbations pour l’exécution de toute tâche dont une stratégie d’approbation associée est définie. Les utilisateurs qui doivent exécuter des tâches incluses dans la stratégie d’approbation doivent demander et obtenir une approbation d’accès.

Pour activer la gestion des accès privilégiés, voir [Configurer la gestion des accès privilégiés.](/office365/securitycompliance/privileged-access-management-configuration)

Pour plus d’informations, voir [Privileged access management](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Logiciel de gestion des événements et des informations de sécurité (SIEM) pour la journalisation Microsoft 365 données

Le logiciel SIEM exécuté sur un serveur effectue une analyse en temps réel des alertes et des événements de sécurité créés par les applications et le matériel réseau. Pour permettre à votre serveur SIEM d’inclure Microsoft 365 alertes et événements de sécurité dans ses fonctions d’analyse et de rapport, intégrez Azure AD à SEIM. Voir [introduction à Azure Log Integration](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Étape suivante

Si vous êtes en train de définir l’identité de votre abonnement Microsoft 365, voir :

- [Identités cloud uniquement si](cloud-only-identities.md) vous utilisez l’identité cloud uniquement
- [Préparer la synchronisation d’annuaires](prepare-for-directory-synchronization.md) si vous utilisez l’identité hybride

  
## <a name="see-also"></a>Voir aussi

[Microsoft 365 sécurité](/office365/securitycompliance/security-roadmap)