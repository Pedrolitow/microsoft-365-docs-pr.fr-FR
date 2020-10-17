---
title: Microsoft 365 pour l’environnement de test d’entreprise Multi-Factor Authentication
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
- seo-marvel-apr2020
description: Configurez l’authentification multifacteur à l’aide de messages texte envoyés à un téléphone intelligent dans votre environnement de test Microsoft 365 pour entreprise.
ms.openlocfilehash: f41fe7ad933f85c4b44a1e90529a998651412191
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487139"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Authentification multifacteur pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

Pour un niveau de sécurité supplémentaire pour la connexion à Microsoft 365 ou tout service ou application qui utilise le client Azure AD pour votre abonnement, vous pouvez activer l’authentification multifacteur Azure, qui nécessite plus qu’un nom d’utilisateur et un mot de passe pour vérifier un compte.

Avec l’authentification multifacteur, les utilisateurs doivent accuser réception d’un appel téléphonique, taper un code de vérification envoyé dans un message texte ou vérifier l’authentification avec une application sur leurs téléphones intelligents après avoir entré correctement leurs mots de passe. Ils ne peuvent se connecter qu’après la satisfaction de ce deuxième facteur d’authentification.
  
Cet article explique comment activer et tester l’authentification par message texte pour un compte d’utilisateur spécifique.
  
La configuration de l’authentification multifacteur pour un compte dans votre environnement de test Microsoft 365 pour entreprise implique deux phases et une troisième phase facultative :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Phase 3 : activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez simplement tester l’authentification multifacteur d’une façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l’authentification multifacteur dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de l’authentification multifacteur ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance distincte privée de votre navigateur, accédez au centre d’administration 365 de Microsoft ( [https://portal.microsoft.com](https://portal.microsoft.com) ), puis connectez-vous avec votre compte d’administrateur général.
    
2. Dans le volet de navigation de gauche **, sélectionnez utilisateurs**  >  **actifs**.
    
3. Dans le volet utilisateurs actifs, sélectionnez **authentification multifacteur**.
    
4. Dans la liste, sélectionnez le compte **utilisateur 2** .
    
5. Dans la section **utilisateur 2** , sous **étapes rapides**, sélectionnez **activer**.
    
6. Dans la boîte de dialogue à propos de l’activation de l' **authentification multifacteur** , sélectionnez **activer l’authentification**multifacteur.
    
7. Dans la boîte de dialogue **mises à jour réussies** , sélectionnez **Fermer**.
    
8. Sous l’onglet **Centre d’administration 365 de Microsoft** , sélectionnez l’icône du compte d’utilisateur dans le coin supérieur droit, puis sélectionnez **déconnexion**.
    
9. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Accédez au [Centre d’administration de Microsoft 365](https://admin.microsoft.com) et connectez-vous avec le nom de compte et le mot de passe de l’utilisateur 2.
    
3. Une fois connecté, vous êtes invité à configurer le compte pour obtenir plus d’informations. Sélectionnez **Suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Entrez le numéro de téléphone du téléphone intelligent qui recevra les messages texte.
    
   - Dans la **méthode**, sélectionnez **m’envoyer un code par message texte**.
    
5. Sélectionnez **Suivant**.
    
6. Entrez le code de vérification à partir du message texte reçu sur votre téléphone intelligent, puis sélectionnez **vérifier**.
    
7. Dans la page **étape 3 : conserver votre application existante** , sélectionnez **Terminer**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Entrez le mot de passe d’origine et un nouveau mot de passe à deux reprises, puis sélectionnez **mettre à jour le mot de passe et se connecter**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devriez voir Office Portal pour l’utilisateur 2 sur l’onglet **Accueil Microsoft Office** de votre navigateur.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Phase 3 : activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel

*Cette phase ne peut être utilisée que pour un environnement de test Microsoft 365 pour les entreprises.*

Dans cette phase, vous activez l’authentification multifacteur pour le compte utilisateur 3 à l’aide d’un groupe et d’une stratégie d’accès conditionnel.

Ensuite, créez un groupe nommé MFAUsers et ajoutez-y le compte utilisateur 3.

1. Sous l’onglet **Centre d’administration 365 de Microsoft** , sélectionnez **groupes** dans le volet de navigation de gauche, puis sélectionnez **groupes**.
2. Sélectionnez **Ajouter un groupe**.
3. Dans le volet **choisir un type de groupe** , sélectionnez **sécurité**, puis **suivant**.
4. Dans le volet **configure the Basics** , sélectionnez **Create Group**, puis **Close**.
5. Dans le volet **vérifier et terminer l’ajout** d’un groupe, entrez **MFAUsers**, puis cliquez sur **suivant**.
6. Dans la liste des groupes, sélectionnez le groupe **MFAUsers** .
7. Dans le volet **MFAUsers** , sélectionnez **membres**, puis **Afficher tous et gérer les membres**.
8. Dans le volet **MFAUsers** , sélectionnez **Ajouter des membres**, sélectionnez le compte **utilisateur 3** , puis sélectionnez **Enregistrer**  >  **Fermer**  >  **Fermer**.

Ensuite, créez une stratégie d’accès conditionnel pour exiger l’authentification multifacteur pour les membres du groupe MFAUsers.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com) .
2. Sélectionnez **Azure Active Directory**  >  **Security**  >  **accès conditionnel**de sécurité Azure Active Directory.
3. Dans le volet **accès conditionnel – stratégies** , sélectionnez **nouvelle stratégie**.
4. Dans le volet **nouveau** , entrez **MFA pour les comptes d’utilisateur** dans la zone **nom** .
5. Dans la section **affectations** , sélectionnez **utilisateurs et groupes**.
6. Sous l’onglet **inclure** du volet **utilisateurs et groupes** , sélectionnez **Sélectionner des**utilisateurs et des groupes d'  >  **utilisateurs et**  >  **de groupes**.
7. Dans le volet **Sélectionner** , sélectionnez le groupe **MFAUsers** , **puis sélectionnez**  >  **Terminer**.
8. Dans la section **contrôles d’accès** du **nouveau** volet, sélectionnez **accorder**.
9. Dans le volet **accorder** , sélectionnez **exiger l’authentification multifacteur**, puis sélectionnez **Sélectionner**.
10. Dans le volet **nouveau** , sélectionnez **activé** pour **activer la stratégie**, puis **créer**.
11. Fermez les onglets **portail Azure** et **Centre d’administration Microsoft 365** .

Pour tester cette stratégie, déconnectez-vous, puis connectez-vous avec le compte utilisateur 3. Vous devez être invité à configurer l’authentification multifacteur. Cela illustre l’application de la stratégie MFAUsers.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Feuille de route d’identité](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
