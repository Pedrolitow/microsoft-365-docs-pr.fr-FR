---
title: Conditions préalables d’accès aux identités et appareils pour la synchronisation du hachage du mot de passe dans votre environnement de test Microsoft 365
author: kelleyvice-msft
f1.keywords:
  - NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
  - M365-subscription-management
  - Strat_O365_Enterprise
ms.custom: null
description: Créez un environnement Microsoft 365 pour tester l’accès aux identités et appareils avec les conditions préalables applicables à l’authentification de la synchronisation du hachage du mot de passe.
---

# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>Conditions préalables d’accès aux identités et appareils pour la synchronisation du hachage du mot de passe dans votre environnement de test Microsoft 365

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les configurations d’accès aux [identités](../security/office-365-security/microsoft-365-policies-configurations.md) et appareils sont un ensemble de configurations et de stratégies d’accès conditionnel pour protéger l’accès à tous les services dans Microsoft 365 pour les entreprises qui sont intégrés à Azure Active Directory (Azure AD).

Cet article explique comment configurer un environnement de test Microsoft 365 qui répond aux exigences de l’environnement hybride avec la [configuration](../security/office-365-security/identity-access-prerequisites.md#prerequisites) requise de l’authentification de synchronisation de hachage de mot de passe pour l’accès aux identités et appareils.

La configuration de cet environnement de test se fait en dix phases :

1. Créer une entreprise simulée avec un environnement de test de synchronisation du hachage du mot de passe
2. Configurer l’authentification unique transparente Azure AD
3. Configurer des emplacements nommés
4. Configurer la réécriture du mot de passe
5. Configurer la réinitialisation de mot de passe en libre-service pour tous les comptes d’utilisateur
6. Configurer l’authentification multifacteur pour tous les comptes d’utilisateur
7. Activer l’inscription automatique de l’appareil des ordinateurs Windows domaine
8. Configurer la protection Azure AD mot de passe 
9. Activer Azure AD Identity Protection
10. Activer l’authentification moderne pour Exchange Online et Skype Entreprise Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>Étape 1 : Construire votre entreprise simulée avec un environnement de test Microsoft 365 pour la synchronisation du hachage du mot de passe

Suivez les instructions du Guide [de](password-hash-sync-m365-ent-test-environment.md) laboratoire de test de synchronisation de hachage de mot de passe.
Voici la configuration obtenue.

![Environnement de test de l’entreprise simulée avec synchronisation de hachage de mot de passe.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>Étape 2 : Configurer l’authentification unique transparente Azure AD

Suivez les instructions de [Phase 2 du guide laboratoire test de l’authentification transparente unique Azure AD](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>Étape 3 : configurer des emplacements nommés

Tout d’abord, déterminer les adresses IP publiques ou les plages d’adresse utilisées par votre organisation.

Ensuite, suivez les instructions de [configurer des emplacements nommé dans Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) pour ajouter les adresses ou les plages d’adresses comme emplacements nommés. 

## <a name="phase-4-configure-password-writeback"></a>Étape 4 : configurer l’écriture différée du mot de passe

Suivez les instructions dans [Phase 2 du guide de laboratoire de test réinitialisation de mot de passe](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>Étape 5 : configurer la réinitialisation du mot de passe libre-service

Suivez les instructions du Guide de laboratoire de Test dans la [Phase 3 de la réinitialisation de mot de passe](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

Lors de l’activation de réinitialisation de mot de passe pour les comptes dans un groupe Azure AD spécifique, ajoutez ces comptes au groupe **réinitialiser le mot de passe**:

- Utilisateur 2
- Utilisateur 3
- Utilisateur 4
- Utilisateur 5

Testez la réinitialisation de mot de passe pour le compte Utilisateur 2.

## <a name="phase-6-configure-multi-factor-authentication"></a>Étape 6 : configurer l’authentification multifacteur

Suivez les instructions de [Phase 2 de Guide de laboratoire de Test authentification multifacteur ](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) pour les comptes d’utilisateurs :

- Utilisateur 2
- Utilisateur 3
- Utilisateur 4
- Utilisateur 5

Testez l’authentification multifacteur uniquement pour le compte Utilisateur 2.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>Phase 7 : Activer l’inscription automatique des appareils joints à un domaine Windows ordinateurs 

Suivez [ces instructions pour](/azure/active-directory/devices/hybrid-azuread-join-plan) activer l’inscription automatique des ordinateurs joints Windows domaine.

## <a name="phase-8-configure-azure-ad-password-protection"></a>Phase 8 : Configurer la protection Azure AD mot de passe 

Suivez [ces instructions pour](/azure/active-directory/authentication/concept-password-ban-bad) bloquer les mots de passe faibles connus et leurs variantes.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>Phase 9 : Activer Azure AD Identity Protection

Suivez les instructions de [Étape 2 du Guide de laboratoire de Test Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>Phase 10 : Activer l’authentification moderne pour Exchange Online et Skype Entreprise Online

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

Le résultat est un environnement de test conforme aux exigences de [configuration préalable de synchronisation du hachage du mot de passe Active Directory](../security/office-365-security/identity-access-prerequisites.md#prerequisites) pour l’accès aux identités et appareils. 

## <a name="next-step"></a>Étape suivante

Utilisez [Stratégies d’accès courantes identité et appareil](../security/office-365-security/identity-access-policies.md) pour configurer les stratégies qui se basent sur les conditions préalables et protègent identités et appareils.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de Test Autres identités](m365-enterprise-test-lab-guides.md#identity)

[Déployer l’identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
