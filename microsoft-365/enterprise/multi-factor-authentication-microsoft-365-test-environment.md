---
title: Authentification multifacteur pour votre environnement de test Microsoft 365 Enterprise
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez l’authentification multifacteur à l’aide de messages texte envoyés à un téléphone intelligent dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: b17c6b3b39bebaff2737ea5e9bb198beef00844c
ms.sourcegitcommit: e525bcf073a61e1350484719a0c3ceb6ff0d8db1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "43153879"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-enterprise-test-environment"></a>Authentification multifacteur pour votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut être utilisé pour les environnements de test Microsoft 365 Entreprise et Office 365 Entreprise*.

Pour un niveau de sécurité supplémentaire pour la connexion à Microsoft 365 ou tout service ou application qui utilise le client Azure AD pour votre abonnement, vous pouvez activer l’authentification multifacteur Azure, qui nécessite plus qu’un nom d’utilisateur et un mot de passe pour vérifier un compte. 

Avec l’authentification multifacteur, les utilisateurs doivent accuser réception d’un appel téléphonique, taper un code de vérification envoyé dans un message texte ou spécifier un mot de passe d’application sur leurs téléphones intelligents après avoir entré correctement leurs mots de passe. Ils peuvent se connecter uniquement lorsque ce deuxième facteur d’authentification a été respecté. 
  
Cet article explique comment activer et tester l’authentification par message texte pour un compte d’utilisateur spécifique.
  
Il existe deux phases de configuration de l’authentification multifacteur pour un compte dans votre environnement de test Microsoft 365 entreprise :
  
1. Créer l’environnement de test Microsoft 365 Entreprise.
    
2. Activez et testez l’authentification multifacteur pour le compte d’utilisateur 2.

3. Activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel (facultatif).

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester l’authentification multifacteur d’une façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l’authentification multifacteur dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de l’authentification multifacteur ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance distincte privée de votre navigateur, accédez au centre d’administration 365 de Microsoft ([https://portal.microsoft.com](https://portal.microsoft.com)), puis connectez-vous avec votre compte d’administrateur général.
    
2. Dans la navigation de gauche, cliquez sur **Utilisateurs > Utilisateurs actifs**.
    
3. Dans le volet utilisateurs actifs, cliquez sur **authentification multifacteur**.
    
4. Dans la liste, sélectionnez le compte **utilisateur 2** .
    
5. Dans la section **Utilisateur 2**, sous **Étapes rapides**, cliquez sur **Activer**.
    
6. Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur**, cliquez sur **Activer Multi-Factor Authentication**.
    
7. Dans la boîte de dialogue **mises à jour réussies** , cliquez sur **Fermer**.
    
8. Dans l’onglet **Centre d’administration Microsoft 365** , cliquez sur l’icône du compte d’utilisateur dans le coin supérieur droit, puis cliquez sur **déconnexion**.
    
9. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Accédez au portail Office 365 ([https://portal.office.com](https://portal.office.com)) et connectez-vous avec le nom de compte et le mot de passe de l’utilisateur 2.
    
3. Une fois connecté, vous êtes invité à configurer le compte pour obtenir plus d’informations. Cliquez sur **Suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Tapez le numéro de téléphone du smartphone qui recevra les SMS.
    
   - Dans **méthode**, cliquez sur **m’envoyer un code par message texte**.
    
5. Cliquez sur **Suivant**.
    
6. Entrez le code de vérification du SMS reçu sur votre smartphone, puis cliquez sur **Vérifier**.
    
7. Sur la page **Étape 3 : Conservez la page des applications existantes**, enregistrez le mot de passe de l’application affiché pour le compte d’utilisateur 2 dans un endroit sûr, puis cliquez sur **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Tapez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis cliquez sur **Mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devriez voir Office Portal pour l’utilisateur 2 sur l’onglet **Accueil Microsoft Office** de votre navigateur.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Phase 3 : activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel

*Cette phase ne peut être utilisée que pour un environnement de test Microsoft 365 Enterprise.*

Dans cette phase, vous activez l’authentification multifacteur pour le compte utilisateur 3 à l’aide d’un groupe et d’une stratégie d’accès conditionnel.

Ensuite, créez un groupe nommé MFAUsers et ajoutez-y le compte utilisateur 3.

1. Dans l’onglet **Centre d’administration Microsoft 365** , cliquez sur **groupes** dans le volet de navigation de gauche, puis cliquez sur **groupes**.
2. Cliquez sur **Ajouter un groupe**.
3. Dans le volet **choisir un type de groupe** , sélectionnez **sécurité**, puis cliquez sur **suivant**.
4. Dans le volet **configurer les concepts de base** , cliquez sur **créer un groupe**, puis cliquez sur **Fermer**.
5. Dans le volet **vérifier et terminer l’ajout** d’un groupe, tapez **MFAUsers**, puis cliquez sur **suivant**.
6. Dans la liste des groupes, cliquez sur le groupe **MFAUsers** .
7. Dans le volet **MFAUsers** , cliquez sur **membres**, puis sur **Afficher tout et gérer les membres**.
8. Dans le volet **MFAUsers** , cliquez sur **Ajouter des membres**, sélectionnez le compte **utilisateur 3** , puis cliquez sur **Enregistrer > fermer > fermer**.

Ensuite, créez une stratégie d’accès conditionnel pour exiger l’authentification multifacteur pour les membres du groupe MFAUsers.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Cliquez sur **Azure Active Directory > sécurité > accès conditionnel**.
3. Dans le volet **accès conditionnel – stratégies** , cliquez sur **nouvelle stratégie**.
4. Dans le volet **nouveau** , tapez **MFA pour les comptes d’utilisateur** dans **nom**.
5. Dans la section **affectations** , cliquez sur **utilisateurs et groupes**.
6. Sous l’onglet **inclure** du volet **utilisateurs et groupes** , cliquez sur Sélectionner des utilisateurs et des groupes **> utilisateurs et des groupes > sélectionner**.
7. Dans le volet **Sélectionner** , cliquez sur le groupe **MFAUsers** , puis cliquez sur **Sélectionner > terminée**.
8. Dans la section **contrôles d’accès** du **nouveau** volet, cliquez sur **accorder**.
9. Dans le volet **accorder** , cliquez sur **exiger l’authentification multifacteur**, puis cliquez sur **Sélectionner**.
10. Dans le volet **nouveau** , cliquez sur **activé** pour **activer la stratégie**, puis cliquez sur **créer**.
11. Fermez les onglets **portail Azure** et **Centre d’administration Microsoft 365** .

Pour tester cette stratégie, déconnectez-vous, puis connectez-vous avec le compte utilisateur 3. Vous devez être invité à configurer l’authentification multifacteur. Cela illustre l’application de la stratégie MFAUsers.

Consultez l’étape de configuration de l' [authentification multifacteur](identity-secure-user-sign-ins.md#identity-mfa) dans la phase d’identité pour obtenir des informations et des liens permettant de déployer l’authentification multifacteur en production.
    
## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
