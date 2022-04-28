---
title: Conditions préalables à l’accès aux identités et appareils uniquement pour le cloud dans votre environnement de test Microsoft 365
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Créez un environnement Microsoft 365 pour tester l’accès aux identités et appareils avec les conditions préalables pour l’authentification uniquement dans le cloud.
ms.openlocfilehash: 88138600e516412b74c38234647147197742f2de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097511"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>Conditions préalables à l’accès aux identités et aux appareils uniquement pour le cloud dans votre environnement de test Microsoft 365

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

[Les configurations d’identité et d’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md) sont un ensemble de configurations recommandées et de stratégies d’accès conditionnel pour protéger l’accès à tous les services intégrés à Azure Active Directory (Azure AD).

Cet article décrit comment configurer un environnement de test Microsoft 365 qui respecte les exigences de [configuration préalable uniquement pour le cloud](../security/office-365-security/identity-access-prerequisites.md#prerequisites) pour l’accès aux identités et aux appareils.

La configuration de cet environnement de test comprend huit étapes :

1. Créer de votre environnement de test léger
2. Configurer des emplacements nommés
3. Configurer la réinitialisation du mot de passe libre-service
4. Configurer l’authentification multifacteur
5. Activer l’inscription automatique des appareils des ordinateurs Windows joints à un domaine
6. Configurer Azure AD protection par mot de passe 
7. Activer Azure AD Identity Protection
8. Activer l’authentification moderne pour Exchange Online et Skype Entreprise Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>Étape 1 : Créer de votre environnement de test Microsoft 365 léger

Suivez les instructions de [Configuration base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
Voici la configuration obtenue.

![Environnement de test Léger Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>Étape 2 : Configurer des emplacements nommés

Commencez par déterminer les adresses IP publiques ou les plages d’adresses que votre organisation utilise.

Ensuite, suivez les instructions de [Configurer des emplacements nommés dans Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) pour ajouter les adresses ou plages d’adresses en tant qu’emplacements nommés. 

## <a name="phase-3-configure-self-service-password-reset"></a>Phase 3 : Configurer la réinitialisation de mot de passe en libre-service

Suivez les instructions de l’[Étape 3 du Guide de laboratoire de Test Réinitialisation de mot de passe](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Lors de l’activation de réinitialisation de mot de passe pour les comptes dans un groupe Azure AD spécifique, ajoutez ces comptes au groupe **réinitialiser le mot de passe**:

- Utilisateur 2
- Utilisateur 3
- Utilisateur 4
- Utilisateur 5

Testez la réinitialisation de mot de passe pour le compte Utilisateur 2.

## <a name="phase-4-configure-multi-factor-authentication"></a>Phase 4 : Configurer l’authentification multifacteur

Suivez les instructions de [Étape 2 de Guide de laboratoire de Test Authentification multifacteur ](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) pour les comptes d’utilisateurs :

- Utilisateur 2
- Utilisateur 3
- Utilisateur 4
- Utilisateur 5

Testez l’authentification multifacteur uniquement pour le compte Utilisateur 2.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Phase 5 : Activer l’inscription automatique d’appareils d’ordinateurs Windows joints à un domaine 

Suivez [ces instructions](/azure/active-directory/devices/hybrid-azuread-join-plan) pour activer l’inscription automatique des appareils joints à un domaine Windows ordinateurs.

## <a name="phase-6-configure-azure-ad-password-protection"></a>Phase 6 : Configurer Azure AD protection par mot de passe 

Suivez [ces instructions](/azure/active-directory/authentication/concept-password-ban-bad) pour bloquer les mots de passe faibles connus et leurs variantes.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>Étape 7 : activer Azure AD Identity Protection

Suivez les instructions de [Étape 2 du guide laboratoire test de l’authentification transparente unique Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Étape 8 : activer l’authentification moderne pour Exchange Online et Skype Entreprise Online

Pour Exchange Online, suivez [ces instructions](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

Pour Skype Entreprise Online :

1. Se connecter à [Skype Entreprise Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. Exécutez cette commande.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. Vérifiez que la commande a correctement appliqué la modification.

  ```powershell
  Get-CsOAuthConfiguration
  ```

Le résultat est un environnement de test qui répond aux exigences de la [configuration requise cloud uniquement](../security/office-365-security/identity-access-prerequisites.md#prerequisites) pour l’identité et l’accès aux appareils. 

## <a name="next-step"></a>Étape suivante

Utilisez [Stratégies d’accès courantes identité et appareil](../security/office-365-security/identity-access-policies.md) pour configurer les stratégies qui se basent sur les conditions préalables et protègent identités et appareils.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Autres identités](m365-enterprise-test-lab-guides.md#identity)

[Déployer une identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
