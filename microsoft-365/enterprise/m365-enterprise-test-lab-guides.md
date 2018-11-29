---
title: Guides de laboratoire de test Microsoft 365 Entreprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/19/2018
ms.audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Servez-vous des guides de laboratoire de test pour configurer les environnements de développement/test, de preuve de concept et de démonstration pour Microsoft 365 Entreprise.
ms.openlocfilehash: df723647748532936e40bbdb4e34ff698b9fa650
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867339"
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

- Utilisez la [configuration de base d’une entreprise simulée](simulated-ent-base-configuration-microsoft-365-enterprise.md) pour configurer et démontrer des fonctionnalités de Microsoft 365 Entreprise dans un environnement cloud hybride, qui utilise des composants locaux à l’instar d’un domaine Windows Server Active Directory (AD).
    
## <a name="identity"></a>Identité

Pour obtenir une description des fonctionnalités liées à l’identité, reportez-vous aux ressources suivantes :

- [Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md)
  
   Permet d’activer et de tester la synchronisation d’annuaires basée sur le hachage de mot de passe à partir d’un contrôleur de domaine Windows Server AD.

- [Authentification directe](pass-through-auth-m365-ent-test-environment.md)
  
   Permet d’activer et de tester l’authentification directe à un contrôleur de domaine Windows Server AD.

- [Authentification unique transparente Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   Permet d’activer et de tester l’authentification unique transparente Azure AD avec un contrôleur de domaine Windows Server AD.

- [Authentification multifacteur](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Activez et testez l’authentification multifacteur sur smartphone pour un compte utilisateur spécifique.

- [Protéger des comptes Administrateur général](protect-global-administrator-accounts-microsoft-365-test-environment.md)
 
   Verrouiller vos comptes d’administrateur général avec la sécurité des applications cloud Office 365 et les stratégies d’accès conditionnel.

- [Réinitialisation des mots de passe](password-reset-m365-ent-test-environment.md)

   Utilisez la réinitialisation du mot de passe en libre-service (SSPR) pour réinitialiser votre mot de passe.

- [Attribution automatique de licences et appartenance au groupe](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Facilitez l’administration des nouveaux comptes grâce à l’attribution automatique de licences et l’appartenance au groupe dynamique.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Recherchez des vulnérabilités dans vos comptes utilisateur actuel.

## <a name="mobile-device-management"></a>Gestion des appareils mobiles

Pour obtenir une description des fonctionnalités liées à la gestion des appareils mobiles, reportez-vous aux ressources suivantes :

- [Stratégies de gestion des applications mobiles](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Créez des groupes d’utilisateurs et des stratégies de gestion des applications mobiles pour les appareils iOS et Android.
    
- [Inscription d’appareils iOS et Android](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Inscrivez des appareils iOS ou Android et gérez-les à distance.


## <a name="information-protection"></a>Protection des informations

Pour faire la démonstration de fonctionnalités liées à la protection des informations, reportez-vous à :

- [Sécurité Office 365 accrue](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez les paramètres pour une sécurité Office 365 accrue et examinez les outils de sécurité intégrée.
  
- [Classification des données](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez et appliquez des étiquettes Office 365 à un document dans un site d’équipe SharePoint Online.
    
- [Gestion des accès privilégiés pour votre environnement de test Microsoft 365 Entreprise](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Configurez la gestion des accès privilégiés pour un accès juste-à-temps aux tâches élevées et privilégiées dans votre organisation Office 365.

## <a name="see-also"></a>Voir aussi

[Découvrez Microsoft Cloud grâce aux Guides de laboratoire de test d’adoption cloud](https://mva.microsoft.com/training-courses/experience-the-microsoft-cloud-with-cloud-adoption-test-lab-guides-17960?l=LXNRdhSLE_1000115881)
    
[Pile de guides de laboratoire de test Microsoft Cloud unique](http://aka.ms/catlgstack)
