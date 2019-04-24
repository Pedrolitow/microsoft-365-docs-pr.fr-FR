---
title: Authentification multifacteur pour votre environnement de test Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/21/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: ConFigurez l'authentification multifacteur à l'aide de messages texte envoyés à un téléphone intelligent dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: 8e202936451030718c0c86601c2c621c50f78e1a
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32291139"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-enterprise-test-environment"></a>Authentification multifacteur pour votre environnement de test Microsoft 365 Enterprise

Pour un niveau de sécurité supplémentaire pour la connexion à Office 365 ou tout service ou application qui utilise le client Azure AD pour votre organisation, vous pouvez activer l'authentification multifacteur Azure, qui nécessite plus qu'un nom d'utilisateur et un mot de passe pour vérifier une comptes. Avec l'authentification multifacteur, les utilisateurs doivent accuser réception d'un appel téléphonique, taper un code de vérification envoyé dans un message texte ou spécifier un mot de passe d'application sur leurs téléphones intelligents après avoir entré correctement leurs mots de passe. Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté. 
  
Cet article explique comment activer et tester l'authentification par message texte pour un compte spécifique.
  
Il existe deux phases de configuration de l'authentification multifacteur pour un compte dans votre environnement de test Microsoft 365 entreprise:
  
1. Créez l'environnement de test Microsoft 365 entreprise.
    
2. Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1: créer votre environnement de test Microsoft 365 Enterprise

Si vous souhaitez simplement tester l'authentification multifacteur d'une façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l'authentification multifacteur dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de l'authentification multifacteur ne nécessite pas l'environnement de test d'entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d'annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance distincte privée de votre navigateur, accédez au portail Office ([https://office.com](https://office.com)), puis connectez-vous avec votre compte d'administrateur général.
    
2. Sur la page principale du portail, cliquez sur **Administrateur**.
    
3. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
4. Dans le volet utilisateurs actifs, cliquez sur **plus d' > d'authentification multifacteur**.
    
5. Dans la liste, sélectionnez le compte **utilisateur 2** .
    
6. Dans la section **Utilisateur 2**, sous **Étapes rapides**, cliquez sur **Activer**.
    
7. Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur**, cliquez sur **Activer Multi-Factor Authentication**.
    
8. Dans la boîte de dialogue **mises à jour réussies** , cliquez sur **Fermer**.
    
9. Dans l’onglet **Microsoft Office Famille**, cliquez sur l’icône du compte utilisateur en haut à droite, puis cliquez sur **Déconnexion**.
    
10. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Accédez au portail Office ([https://office.com](https://office.com)) et connectez-vous avec le compte utilisateur 2 (utilisateur2 @\<organisation name>. onmicrosoft. com) et le mot de passe.
    
3. Une fois connecté, vous êtes invité à configurer le compte pour obtenir plus d'informations. Cliquez sur **Suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Tapez le numéro de téléphone du smartphone qui recevra les SMS.
    
   - Dans **méthode**, cliquez sur **m'envoyer un code par message texte**.
    
5. Cliquez sur **Suivant**.
    
6. Entrez le code de vérification du SMS reçu sur votre smartphone, puis cliquez sur **Vérifier**.
    
7. Sur la page **Étape 3 : Conservez la page des applications existantes**, enregistrez le mot de passe de l’application affiché pour le compte d’utilisateur 2 dans un endroit sûr, puis cliquez sur **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis cliquez sur **Mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devriez voir Office Portal pour l'utilisateur 2 sur l'onglet **Accueil Microsoft Office** de votre navigateur.


Consultez l'étape de configuration de l' [authentification multifacteur](identity-multi-factor-authentication.md#identity-mfa) dans la phase d'identité pour obtenir des informations et des liens permettant de déployer l'authentification multifacteur en production.
    
## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement d'entreprise Microsoft 365](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
