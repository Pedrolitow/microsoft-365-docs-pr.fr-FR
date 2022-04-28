---
title: Microsoft 365 pour l’authentification multifacteur de l’environnement de test d’entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
- seo-marvel-apr2020
- admindeeplinkMAC
description: Configurez l’authentification multifacteur à l’aide de sms envoyés à un téléphone intelligent dans votre Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: aa72375342bdf60e1fe1bc504f14b1f51a48b701
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078732"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Authentification multifacteur pour votre Microsoft 365 pour l’environnement de test d’entreprise

*Ce guide de laboratoire de test peut être utilisé pour les Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Pour bénéficier d’un niveau de sécurité supplémentaire pour la connexion à Microsoft 365 ou à tout service ou application qui utilise le locataire Azure AD pour votre abonnement, vous pouvez activer Azure AD authentification multifacteur, qui nécessite plus qu’un nom d’utilisateur et un mot de passe pour vérifier un compte.

Avec l’authentification multifacteur, les utilisateurs doivent reconnaître un appel téléphonique, taper un code de vérification envoyé dans un SMS ou vérifier l’authentification avec une application sur leur smartphone après avoir entré correctement leurs mots de passe. Ils ne peuvent se connecter qu’une fois ce deuxième facteur d’authentification satisfait.
  
Cet article explique comment activer et tester l’authentification par SMS pour un compte d’utilisateur spécifique.
  
La configuration de l’authentification multifacteur pour un compte dans votre Microsoft 365 pour l’environnement de test d’entreprise implique deux phases et une troisième phase facultative :
- [Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Phase 3 : Activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles du Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise, accédez à [Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise

Si vous souhaitez simplement tester l’authentification multifacteur de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l’authentification multifacteur dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test de l’authentification multifacteur ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance privée distincte de votre navigateur, accédez à la Centre d'administration Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)), puis connectez-vous avec votre compte d’administrateur général.
    
2. Dans le volet de navigation de gauche, sélectionnez **Utilisateurs** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Actifs**</a>.
    
3. Dans le volet Utilisateurs actifs, sélectionnez **Authentification multifacteur**.
    
4. Dans la liste, sélectionnez le compte **Utilisateur 2** .
    
5. Dans la section **Utilisateur 2** , sous **Étapes rapides**, **sélectionnez Activer**.
    
6. Dans la boîte de dialogue **À propos de l’activation de l’authentification multifacteur** , sélectionnez **Activer l’authentification multifacteur**.
    
7. Dans la boîte de dialogue **Mises à jour réussies** , sélectionnez **Fermer**.
    
8. Sous l’onglet **Centre d'administration Microsoft 365**, sélectionnez l’icône de compte d’utilisateur en haut à droite, puis **déconnectez-vous**.
    
9. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Accédez à la [Centre d'administration Microsoft 365](https://admin.microsoft.com) et connectez-vous avec le nom et le mot de passe du compte Utilisateur 2.
    
3. Une fois connecté, vous êtes invité à configurer le compte pour plus d’informations. Sélectionnez **Suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Entrez le numéro de téléphone du téléphone intelligent qui recevra des SMS.
    
   - Dans **Méthode**, **sélectionnez Envoyer-moi un code par SMS**.
    
5. Sélectionnez **Suivant**.
    
6. Entrez le code de vérification du sms reçu sur votre smartphone, puis sélectionnez **Vérifier**.
    
7. À **l’étape 3 : Conserver la page de vos applications existantes** , sélectionnez **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Entrez deux fois le mot de passe d’origine et un nouveau mot de passe, puis sélectionnez **Mettre à jour le mot de passe et connectez-vous**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Vous devez voir le portail Office pour l’utilisateur 2 sous l’onglet **Microsoft Office Accueil** de votre navigateur.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Phase 3 : Activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel

*Cette phase ne peut être utilisée que pour un Microsoft 365 pour l’environnement de test d’entreprise.*

Dans cette phase, vous activez l’authentification multifacteur pour le compte Utilisateur 3 à l’aide d’un groupe et d’une stratégie d’accès conditionnel.

Ensuite, créez un groupe nommé MFAUsers et ajoutez-y le compte Utilisateur 3.

1. Sous l’onglet **Centre d'administration Microsoft 365**, sélectionnez **Groupes** dans le volet de navigation gauche, puis <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.
2. Sélectionnez **Ajouter un groupe**.
3. Dans le volet **Choisir un type de groupe** , sélectionnez **Sécurité**, puis **Suivant**.
4. Dans le volet **Configurer les informations de base** , **sélectionnez Créer un groupe**, puis **Fermez**.
5. Dans le volet **Révision et fin de l’ajout de groupe** , entrez **MFAUsers**, puis sélectionnez **Suivant**.
6. Dans la liste des groupes, sélectionnez le groupe **MFAUsers** .
7. Dans le volet **MFAUsers** , sélectionnez **Membres**, puis **sélectionnez Afficher tout et gérer les membres**.
8. Dans le volet **MFAUsers**, sélectionnez **Ajouter des membres**, sélectionnez le compte **Utilisateur 3**, puis **saveCloseClose** >  > .

Ensuite, créez une stratégie d’accès conditionnel pour exiger une authentification multifacteur pour les membres du groupe MFAUsers.

1. Dans un nouvel onglet de votre navigateur, accédez à [https://portal.azure.com](https://portal.azure.com).
2. Sélectionnez **Azure Active Directory** >  **SecurityConditional** >  Access.
3. Dans le volet **Accès conditionnel – Stratégies** , sélectionnez **Nouvelle stratégie**.
4. Dans le volet **Nouveau** , entrez **l’authentification multifacteur pour les comptes d’utilisateur** dans la zone **Nom** .
5. Dans la section **Affectations** , sélectionnez **Utilisateurs et groupes**.
6. Sous l’onglet **Inclure** du volet **Utilisateurs et groupes**, **sélectionnez Sélectionner les utilisateurs et les groupesUsers** >  **et** **groupsSelect** > .
7. Dans le volet **Sélectionner**, sélectionnez le groupe **MFAUsers**, puis **sélectionnez SelectDone** > .
8. Dans la section **Contrôles d’accès** du **volet Nouveau** , sélectionnez **Accorder**.
9. Dans le volet **Accorder** , **sélectionnez Exiger l’authentification multifacteur**, puis **sélectionnez Sélectionner**.
10. Dans le volet **Nouveau** , sélectionnez **Activé** pour **activer la stratégie**, puis **sélectionnez Créer**.
11. Fermez les onglets **Portail Azure** et **Centre d'administration Microsoft 365**.

Pour tester cette stratégie, déconnectez-vous et connectez-vous avec le compte Utilisateur 3. Vous devez être invité à configurer l’authentification multifacteur. Cela montre que la stratégie MFAUsers est appliquée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Déployer une identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)