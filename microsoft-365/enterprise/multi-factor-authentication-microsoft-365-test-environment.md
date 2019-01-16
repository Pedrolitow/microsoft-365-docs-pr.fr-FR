---
title: Environnement de test de l’authentification multifacteur pour votre entreprise 365 de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/21/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
description: Configurer l’authentification multifacteur à l’aide de messages texte envoyés vers un téléphone actif dans votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 353f09253794670e8107e084acb3a01cd309fd60
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866841"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-enterprise-test-environment"></a>Environnement de test de l’authentification multifacteur pour votre entreprise 365 de Microsoft

Pour un niveau supplémentaire de sécurité pour vous connecter à Office 365 ou un service ou une application qui utilise le client Azure AD pour votre organisation, vous pouvez activer l’authentification multifacteur Azure, ce qui nécessite plus qu’un nom d’utilisateur et le mot de passe pour vérifier un compte. Avec l’authentification multifacteur, les utilisateurs sont nécessaires pour confirmer un appel téléphonique, tapez un code de vérification envoyé dans un message texte ou spécifier un mot de passe d’application sur leur téléphone actives après avoir entré correctement leur mot de passe. Ils peuvent se connecter qu’une fois cet deuxième facteur d’authentification a été satisfait. 
  
Cet article explique comment activer et tester l’authentification basée sur un message texte pour un compte spécifique.
  
Il existe deux phases de configuration de l’authentification multifacteur pour un compte dans votre environnement de test Microsoft 365 pour entreprises :
  
1. Créer l’environnement de test Microsoft 365 pour entreprises.
    
2. Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez uniquement tester l’authentification multifacteur dans une solution légère avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l’authentification multifacteur dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test de l’authentification multifacteur ne nécessite pas l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option de sorte que vous pouvez tester l’authentification multifacteur et tester dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance distincte, privée de votre navigateur, accédez au portail Office ([https://office.com](https://office.com)), puis connectez-vous avec votre compte d’administrateur global.
    
2. Sur la page principale du portail, cliquez sur **Administrateur**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. Dans le volet utilisateurs actifs, cliquez sur **plus > le programme d’installation de l’authentification multifacteur**.
    
5. Dans la liste, sélectionnez le compte **d’utilisateur 2** .
    
6. Dans la section **Utilisateur 2**, sous **Étapes rapides**, cliquez sur **Activer**.
    
7. Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur**, cliquez sur **Activer Multi-Factor Authentication**.
    
8. Dans la boîte de dialogue **met à jour réussie** , cliquez sur **Fermer**.
    
9. Dans l’onglet **Microsoft Office Famille**, cliquez sur l’icône du compte utilisateur en haut à droite, puis cliquez sur **Déconnexion**.
    
10. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Accédez au portail Office ([https://office.com](https://office.com)) et la connexion avec le compte d’utilisateur 2 (user2 @\<nom de l’organisation >. onmicrosoft.com) et le mot de passe.
    
3. Après la connexion, vous êtes invité à configurer le compte pour plus d’informations. Cliquez sur **suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Tapez le numéro de téléphone du smartphone qui recevra les SMS.
    
   - Dans la **méthode**, cliquez sur **M’envoyer un code par message texte**.
    
5. Cliquez sur **Suivant**.
    
6. Entrez le code de vérification du SMS reçu sur votre smartphone, puis cliquez sur **Vérifier**.
    
7. Sur la page **Étape 3 : Conservez la page des applications existantes**, enregistrez le mot de passe de l’application affiché pour le compte d’utilisateur 2 dans un endroit sûr, puis cliquez sur **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis cliquez sur **Mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devez voir le portail Office pour l’utilisateur 2 sous l’onglet **Accueil de Microsoft Office** de votre navigateur.


Voir l’étape [configurer l’authentification multifacteur](identity-multi-factor-authentication.md) lors de la phase d’identité pour des informations et des liens pour déployer l’authentification multifacteur en production.
    
## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 pour entreprises](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
