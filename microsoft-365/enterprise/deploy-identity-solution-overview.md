---
title: Déployer votre infrastructure d’identité pour Microsoft 365
f1.keywords:
  - NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
  - M365-identity-device-management
  - Strat_O365_Enterprise
  - m365initiative-coredeploy
  - m365solution-m365-identity
  - m365solution-scenario
  - m365solution-overview
ms.custom:
  - intro-overview
description: Déployez votre infrastructure d’identité pour Microsoft 365.
---

# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Déployer votre infrastructure d’identité pour Microsoft 365

Dans Microsoft 365 entreprise, une infrastructure d’identités bien planifiée et exécutée ouvre la voie à une sécurité renforcée, notamment en limitant l’accès à vos charges de travail de productivité et à leurs données uniquement aux utilisateurs et appareils authentifiés. La sécurité des identités est un élément clé d’un déploiement de confiance zéro, dans lequel toutes les tentatives d’accès aux ressources locales et dans le cloud sont authentifiées et autorisées.

Pour plus d’informations sur les fonctionnalités d’identité de chaque Microsoft 365 pour entreprise, le rôle de Azure Active Directory (Azure AD), les composants locaux et basés sur le cloud et les configurations d’authentification les plus courantes, voir l’affiche Infrastructure d’identités[.](../downloads/m365e-identity-infra.pdf)

[![Affiche Infrastructure des identités.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Examinez cette affiche de deux pages pour accélérer rapidement les concepts et les configurations d’identité pour Microsoft 365 entreprise.

Vous pouvez [télécharger cette affiche et](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="whats-in-this-solution"></a>Qu’y a-t-il dans cette solution ?

Cette solution vous permet de déployer une infrastructure d’identité pour votre client Microsoft 365 afin de fournir un accès à vos employés et une protection contre les attaques basées sur l’identité.

![Déployer votre infrastructure d’identité pour Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Les étapes de cette solution sont les suivantes :

1. [Déterminez votre modèle d’identité.](deploy-identity-solution-identity-model.md)
2. [Protégez vos Microsoft 365 privilégiés.](protect-your-global-administrator-accounts.md)
3. [Protégez vos Microsoft 365 utilisateurs.](microsoft-365-secure-sign-in.md)
4. [Déployez votre modèle d’identité.](cloud-only-identities.md)

Cette solution prend en charge les principes clés de [confiance zéro](https://www.microsoft.com/security/business/zero-trust/) :

- **Vérifiez explicitement :** Toujours authentifier et autoriser en fonction de tous les points de données disponibles.
- **Utilisez l’accès selon le privilège minimum :** Limitez l’accès des utilisateurs avec un accès juste-à-temps et juste-suffisant (JIT/JEA), des stratégies adaptatives basées sur les risques et la protection des données.
- **Supposons une violation :** Réduisez le rayon d’explosion et l’accès aux segments. Vérifiez le chiffrement de bout en bout et utilisez l’analyse pour obtenir la visibilité, détecter les menaces et améliorer les défenses.

Contrairement à l’accès intranet classique, qui fait confiance à tous les éléments derrière le pare-feu d’une organisation, la confiance zéro traite chaque connexion et accès comme s’il provenait d’un réseau non contrôlé, qu’il se trouve derrière le pare-feu de l’organisation ou sur Internet. La confiance zéro nécessite une protection pour le réseau, l’infrastructure, les identités, les points de terminaison, les applications et les données.

## <a name="microsoft-365-capabilities-and-features"></a>Fonctionnalités de Microsoft 365

Azure AD offre une suite complète de fonctionnalités de gestion des identités et de sécurité pour Microsoft 365 client.

|Fonctionnalité|Description|Licence|
|---|---|---|
|[Authentification multifacteur (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|L’appelez mappé exige que les utilisateurs fournissent deux formes de vérification, telles qu’un mot de passe d’utilisateur, ainsi qu’une notification de l’application Microsoft Authenticator ou un appel téléphonique. L’portable réduit considérablement le risque que les informations d’identification volées soient utilisées pour accéder à votre environnement. Microsoft 365 utilise le service Azure AD Multi-Factor Authentication pour les authentifications basées sur l’authentification multifacteur.|Microsoft 365 E3 ou E5|
|[Accès conditionnel](/azure/active-directory/conditional-access/overview)|Azure AD évalue les conditions de la connectez-vous de l’utilisateur et utilise des stratégies d’accès conditionnel pour déterminer l’accès autorisé. Par exemple, dans ces instructions, nous vous montrons comment créer une stratégie d’accès conditionnel pour exiger la conformité de l’appareil pour l’accès aux données sensibles. Cela réduit considérablement le risque qu’un pirate informatique avec son propre appareil et des informations d’identification volées puisse accéder à vos données sensibles. Elle protège également les données sensibles sur les appareils, car ces derniers doivent répondre à des exigences spécifiques en matière d’état de santé et de sécurité.|Microsoft 365 E3 ou E5|
|[Azure AD groupes](/azure/active-directory/fundamentals/active-directory-manage-groups)|Les stratégies d’accès conditionnel, la gestion des appareils avec Intune et même les autorisations sur les fichiers et les sites de votre organisation reposent sur l’affectation à des comptes d’utilisateurs ou à Azure AD groupes. Nous vous recommandons de créer des Azure AD qui correspondent aux niveaux de protection que vous implémentez. Par exemple, vos cadres sont probablement des cibles plus importantes pour les pirates informatiques. Par conséquent, il est logique d’ajouter les comptes d’utilisateur de ces employés à un groupe Azure AD et d’affecter ce groupe à des stratégies d’accès conditionnel et à d’autres stratégies qui appliquent un niveau de protection plus élevé pour l’accès.|Microsoft 365 E3 ou E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Vous permet de détecter les vulnérabilités potentielles affectant les identités de votre organisation et de configurer une stratégie de correction automatisée en cas de risque de communication faible, moyen et élevé, ainsi que de risque pour l’utilisateur. Ces instructions s’appuient sur cette évaluation des risques pour appliquer des stratégies d’accès conditionnel pour l’authentification multifacteur. Ces instructions incluent également une stratégie d’accès conditionnel qui oblige les utilisateurs à modifier leur mot de passe si une activité à risque élevé est détectée pour leur compte.|Microsoft 365 E5, Microsoft 365 E3 avec le module de sécurité E5, EMS E5 ou Azure AD Premium P2 licences|
|[Réinitialisation du mot de passe en libre-service (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Autorisez vos utilisateurs à réinitialiser leurs mots de passe en toute sécurité et sans intervention du service d’aide, en fournissant la vérification de plusieurs méthodes d’authentification que l’administrateur peut contrôler.|Microsoft 365 E3 ou E5|
|[Azure AD protection par mot de passe](/azure/active-directory/authentication/concept-password-ban-bad)|Détectez et bloquez les mots de passe faibles connus, leurs variantes et d’autres termes faibles propres à votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts.|Microsoft 365 E3 ou E5|
|

## <a name="next-steps"></a>Prochaines étapes

Utilisez ces étapes pour déployer un modèle d’identité et une infrastructure d’authentification pour Microsoft 365 client :

1. [Déterminez votre modèle d’identité cloud.](deploy-identity-solution-identity-model.md)
2. [Protégez vos Microsoft 365 privilégiés.](protect-your-global-administrator-accounts.md)
3. [Protégez vos Microsoft 365 utilisateurs.](microsoft-365-secure-sign-in.md)
4. Déployez votre modèle d’identité cloud : [cloud uniquement](cloud-only-identities.md) ou [hybride](prepare-for-directory-synchronization.md).

[![Déterminer le modèle d’identité à utiliser pour votre client Microsoft 365 client](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Autres ressources d’identité cloud Microsoft

### <a name="manage"></a>Gestion

Pour gérer votre déploiement d’identité cloud Microsoft, voir :

- [Comptes d’utilisateur](manage-microsoft-365-accounts.md)
- [Licences](assign-licenses-to-user-accounts.md)
- [Mots de passe](manage-microsoft-365-passwords.md)
- [Groupes](manage-microsoft-365-groups.md)
- [Governance](manage-microsoft-365-identity-governance.md)
- [Synchronisation d’annuaires](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Comment Microsoft fait l’identité pour Microsoft 365

Découvrez comment les experts informatiques de [Microsoft gèrent les identités et la sécurisation des accès](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Cette ressource IT Showcase est disponible uniquement en anglais.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Comment Contoso a fait l’identité pour Microsoft 365

Pour obtenir un exemple de la façon dont une multinationale fictive mais représentative a déployé une infrastructure d’identité hybride pour les services cloud Microsoft 365, voir [Identity for the Contoso Corporation](contoso-identity.md).

<!--

## Plan

To plan for your identity implementation:

- [Understand the different identity models](about-microsoft-365-identity.md)
- [Plan for hybrid identity and directory synchronization](plan-for-directory-synchronization.md)

## Deploy

To deploy your identity implementation:

- [Protect your global administrator accounts](protect-your-global-administrator-accounts.md)
- [Configure and use cloud-only identities](cloud-only-identities.md)
- [Configure and use hybrid identities](prepare-for-directory-synchronization.md)
- [Set up directory synchronization](set-up-directory-synchronization.md)
- If needed, deploy [hybrid identity scenarios](hybrid-solutions.md)

### Identity and device access recommendations

To help ensure a secure and productive workforce, Microsoft provides a set of recommendations for [identity and device access](../security/office-365-security/microsoft-365-policies-configurations.md). For identity, use the recommendations and settings in these articles:

- [Prerequisites](../security/office-365-security/identity-access-prerequisites.md)
- [Common identity and device access policies](../security/office-365-security/identity-access-policies.md)

--> 
