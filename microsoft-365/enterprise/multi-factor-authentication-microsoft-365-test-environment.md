---
title: Microsoft 365 pour l’authentification multifacteur de l’environnement de test d’entreprise
f1.keywords:
  - NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Configurez l’authentification multifacteur à l’aide de messages texte envoyés à un smartphone dans votre Microsoft 365 environnement de test d’entreprise.
---

# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Authentification multifacteur pour votre environnement de test Microsoft 365 entreprise

*Ce guide de laboratoire de test peut être utilisé à la fois pour Microsoft 365'entreprise et Office 365 Entreprise environnements de test.*

Pour un niveau de sécurité supplémentaire pour la connexion à Microsoft 365 ou à tout service ou application qui utilise le client Azure AD pour votre abonnement, vous pouvez activer l’authentification multifacteur Azure AD, qui nécessite plus qu’un simple nom d’utilisateur et mot de passe pour vérifier un compte.

Avec l’authentification multifacteur, les utilisateurs doivent confirmer un appel téléphonique, taper un code de vérification envoyé dans un SMS ou vérifier l’authentification avec une application sur leur smartphone après avoir entré correctement leur mot de passe. Ils ne peuvent se connecter qu’une fois que ce deuxième facteur d’authentification est satisfait.
  
Cet article explique comment activer et tester l’authentification par SMS pour un compte d’utilisateur spécifique.
  
La configuration de l’authentification multifacteur pour un compte dans votre Microsoft 365 pour un environnement de test d’entreprise comprend deux phases et une troisième phase facultative :
- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Phase 3 : Activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez simplement tester l’authentification multifacteur avec une configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester l’authentification multifacteur dans une entreprise [simulée](pass-through-auth-m365-ent-test-environment.md), suivez les instructions de l’authentification directe.
  
> [!NOTE]
> Le test de l’authentification multifacteur ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS (Active Directory Domain Services). Il est proposé comme option dans cet article afin que vous puissiez tester l’authentification multifacteur et faire des essais dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Phase 2 : Activer et tester l’authentification multifacteur pour le compte d’utilisateur 2

Activez l’authentification multifacteur pour le compte d’utilisateur 2 en procédant comme suit :
  
1. Ouvrez une instance privée distincte de votre navigateur, Centre d'administration Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)), puis connectez-vous avec votre compte d’administrateur général.
    
2. Dans le navigation de gauche, sélectionnez **Utilisateurs UsersActive** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
    
3. Dans le volet Utilisateurs actifs, sélectionnez **Authentification multifacteur**.
    
4. Dans la liste, sélectionnez le **compte Utilisateur 2** .
    
5. Dans la section **Utilisateur 2** , sous **Étapes rapides**, sélectionnez **Activer**.
    
6. Dans la **boîte de dialogue À propos de l’activation de l’erth multi-facteur** , sélectionnez **Activer l’thème multi-facteur**.
    
7. Dans la **boîte de dialogue Mises à jour** réussies, sélectionnez **Fermer**.
    
8. Sous **l’Centre d'administration Microsoft 365**, sélectionnez l’icône du compte d’utilisateur dans le coin supérieur droit, puis **sélectionnez Se sortir**.
    
9. Fermez l’instance de navigateur.
   
Terminez la configuration pour que le compte d’utilisateur 2 utilise un message texte pour la validation et testez-le en procédant comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur.
    
2. Go to the [Centre d'administration Microsoft 365](https://admin.microsoft.com) and sign in with the User 2 account name and password.
    
3. Après la signature, vous êtes invité à configurer le compte pour plus d’informations. Sélectionnez **Suivant**.
    
4. Sur la page **Vérification de sécurité supplémentaire** : 
    
   - Sélectionnez le pays ou la région.
    
   - Entrez le numéro de téléphone du smartphone qui recevra les messages texte.
    
   - Dans **Méthode**, **sélectionnez Envoyer un code par SMS**.
    
5. Sélectionnez **Suivant**.
    
6. Entrez le code de vérification du message texte reçu sur votre smartphone, puis sélectionnez **Vérifier**.
    
7. Dans la **page Étape 3 : Conserver vos applications existantes** , sélectionnez **Terminé**.
    
8. Si c’est la première fois que vous vous connectez avec le compte d’utilisateur 2, vous êtes invité à modifier le mot de passe. Entrez deux fois le mot de passe d’origine et un nouveau mot de passe, puis sélectionnez Mettre à jour le mot **de passe et connectez-vous**. Enregistrez le nouveau mot de passe dans un endroit sûr.
    
    Le portail d’Office utilisateur 2 doit s’Microsoft Office **l’onglet** Accueil de votre navigateur.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Phase 3 : Activer et tester l’authentification multifacteur avec une stratégie d’accès conditionnel

*Cette phase ne peut être utilisée que pour une Microsoft 365'environnement de test d’entreprise.*

Dans cette phase, vous activez l’authentification multifacteur pour le compte Utilisateur 3 à l’aide d’un groupe et d’une stratégie d’accès conditionnel.

Ensuite, créez un groupe nommé MFAUsers et ajoutez-y le compte Utilisateur 3.

1. Sous **l’Centre d'administration Microsoft 365**, sélectionnez **Groupes** dans le navigation de gauche, <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**puis Groupes.**</a>
2. **Sélectionnez Ajouter un groupe**.
3. Dans le **volet Choisir un type de groupe**, sélectionnez **Sécurité**, **puis Suivant.**
4. Dans le **volet Configurer les informations** de base **, sélectionnez** Créer un groupe, puis **Fermez**.
5. Dans le **volet Révision et fin de l’ajout de** groupes, entrez **MFAUsers**, puis sélectionnez **Suivant**.
6. Dans la liste des groupes, sélectionnez le **groupe MFAUsers** .
7. Dans le **volet MFAUsers** , sélectionnez **Membres**, puis **afficher tout et gérer les membres**.
8. Dans le **volet MFAUsers**, sélectionnez Ajouter des **membres,** sélectionnez le compte Utilisateur **3**, puis **sélectionnez** **SaveCloseClose** >  > .

Ensuite, créez une stratégie d’accès conditionnel pour exiger l’authentification multifacteur pour les membres du groupe MFAUsers.

1. Dans un nouvel onglet de votre navigateur, allez à [https://portal.azure.com](https://portal.azure.com).
2. **Sélectionnez Azure Active Directory** >  **SecurityConditional** >  Access.
3. Dans le **volet Accès conditionnel – Stratégies** , sélectionnez **Nouvelle stratégie**.
4. Dans le **volet Nouveau** , entrez **l’mf pour les comptes d’utilisateurs** dans la **zone** Nom.
5. Dans la section **Affectations** , sélectionnez **Utilisateurs et groupes**.
6. Sous **l’onglet** Inclure du  volet Utilisateurs et groupes, sélectionnez Sélectionner utilisateurs et **groupesUtiliseurs** >  et **groupesSelect** > .
7. Dans le **volet** Sélectionner, sélectionnez le **groupe MFAUsers**, puis **sélectionnez SelectDone** > .
8. Dans la section **Contrôles d’accès** du **nouveau** volet, sélectionnez **Accorder**.
9. Dans le **volet Accorder** , sélectionnez Exiger **l’authentification multifacteur**, puis **sélectionnez Sélectionner**.
10. Dans le **volet** Nouveau, sélectionnez **Activer** pour **activer** la stratégie, puis sélectionnez **Créer**.
11. Fermez **le portail Azure et** **Centre d'administration Microsoft 365** onglets.

Pour tester cette stratégie, connectez-vous avec le compte Utilisateur 3. Vous devez être invité à configurer l’mf. Cela montre que la stratégie MFAUsers est appliquée.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Déployer l’identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)