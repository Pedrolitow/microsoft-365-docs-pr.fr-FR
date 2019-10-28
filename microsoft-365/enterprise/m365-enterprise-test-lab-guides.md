---
title: Guides de laboratoire de test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Servez-vous des guides de laboratoire de test pour configurer les environnements de développement/test, de preuve de concept et de démonstration pour Microsoft 365 Entreprise.
ms.openlocfilehash: 082d110ca7b25d3613ee276b30066683cd0232b5
ms.sourcegitcommit: 64a21c59d31a283ccbe87d16f0a174998e3aeba8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2019
ms.locfileid: "37733419"
---
# <a name="microsoft-365-enterprise-test-lab-guides"></a>Guides de laboratoire de test Microsoft 365 Entreprise

Les guides de laboratoire de test vous permettent de vous familiariser rapidement avec les produits Microsoft. Ils fournissent des instructions normatives sur la configuration d’environnements de test simplifiés mais représentatifs. Vous pouvez utiliser ces environnements pour la démonstration, la personnalisation ou la création de preuves de concept complexes pour la durée d’un abonnement d’évaluation ou payant. 

Les guides de laboratoire de test sont conçus pour être modulaires. Ils s’appuient les uns sur les autres pour créer plusieurs configurations qui correspondent mieux à vos besoins de configuration d’apprentissage ou de test. L’expérience pratique du type « je l’ai créé moi-même et ça fonctionne » vous permet de comprendre les exigences de déploiement d’un nouveau produit ou scénario afin que vous puissiez mieux planifier son hébergement lors de la production.

Les guides de laboratoire de test vous permettent également de créer des environnements représentatifs pour le développement et le test d’applications, également connus sous le nom d’environnements de développement/test.
  
![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="base-configuration"></a>Configuration de base

Tout d’abord, créez un environnement de test pour [Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/) qui inclut Office 365 E5, Enterprise Mobility + Security (EMS) E5 et Windows 10 Entreprise. Vous pouvez créer deux types de configuration de base différents :

- Utilisez la [configuration de base minimale](lightweight-base-configuration-microsoft-365-enterprise.md) pour configurer et faire une démonstration des fonctionnalités de Microsoft 365 Entreprise dans un environnement cloud uniquement, sans aucun composant local.

- Utilisez la [configuration de base d’une entreprise simulée](simulated-ent-base-configuration-microsoft-365-enterprise.md) pour configurer et démontrer des fonctionnalités de Microsoft 365 Entreprise dans un environnement cloud hybride, qui utilise des composants locaux à l’instar d’un domaine Windows Server Active Directory (AD DS).
    
## <a name="identity"></a>Identité

Pour obtenir une description des fonctionnalités liées à l’identité, reportez-vous aux ressources suivantes :

- [Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md)
  
   Activez et testez la synchronisation de répertoires basée sur le hachage de mots de passe à partir d’un contrôleur de domaine AD DS.

- [Authentification directe](pass-through-auth-m365-ent-test-environment.md)
  
   Activez et testez l’authentification directe à un contrôleur de domaine Windows Server AD DS.

- [Authentification unique transparente Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   Activer et tester l’authentification unique transparente Azure AD (SSO) avec un contrôleur de domaine Windows Server AD.

- [Authentification multifacteur](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Activez et testez l’authentification multifacteur sur smartphone pour un compte utilisateur spécifique.

- [Protéger des comptes Administrateur général](protect-global-administrator-accounts-microsoft-365-test-environment.md)
 
   Verrouillez vos comptes d’administrateur général avec des stratégies d’accès conditionnel.

- [Écriture différée de mot de passe](password-writeback-m365-ent-test-environment.md)

   Utilisez l’écriture différée de mot de passe pour modifier le mot de passe de votre compte d’utilisateur Windows Server AD DS à partir d’Azure AD.

- [Réinitialisation des mots de passe](password-reset-m365-ent-test-environment.md)

   Utilisez la réinitialisation du mot de passe en libre-service (SSPR) pour réinitialiser votre mot de passe.

- [Attribution automatique de licences et appartenance au groupe](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Facilitez l’administration des nouveaux comptes grâce à l’attribution automatique de licences et l’appartenance au groupe dynamique.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Recherchez des vulnérabilités dans vos comptes utilisateur actuel.

- [Accès aux identités et appareils](identity-device-access-m365-test-environment.md)

   Créez un environnement pour tester les configurations recommandées pour l’accès aux identités aux appareils et les stratégies d’accès conditionnel.


## <a name="mobile-device-management"></a>Gestion des appareils mobiles

Pour obtenir une description des fonctionnalités liées à la gestion des appareils mobiles, reportez-vous aux ressources suivantes :

- [Stratégies de conformité d’appareil](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Créez un groupe d’utilisateurs et une stratégie de conformité d’appareil pour les appareils Windows 10.
    
- [Inscription d’appareils iOS et Android](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Inscrivez des appareils iOS ou Android et gérez-les à distance.


## <a name="information-protection"></a>Protection des informations

Pour faire la démonstration de fonctionnalités liées à la protection des informations, reportez-vous à :

- [Sécurité Office 365 accrue](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez les paramètres pour une sécurité Office 365 accrue et examinez les outils de sécurité intégrée.
  
- [Classification des données](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez et appliquez des étiquettes Office 365 à un document dans un site d’équipe SharePoint Online.
    
- [Gestion des accès privilégiés](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez la gestion des accès privilégiés pour un accès juste-à-temps aux tâches élevées et privilégiées dans votre organisation Office 365.

## <a name="see-also"></a>Voir aussi

[Tester Office 365 à l’aide des Guides de laboratoire de test relatifs à l’adoption de Microsoft Cloud (TLGs)](https://docs.microsoft.com/office365/enterprise/cloud-adoption-test-lab-guides-tlgs)
