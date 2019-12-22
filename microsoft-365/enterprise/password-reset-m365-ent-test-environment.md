---
title: Réinitialisation de mot de passe pour votre environnement de test Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Configurez et testez la réinitialisation de mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 930c5b4a4ddcc4866a586ff444380ff6dcd66238
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40801409"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Réinitialisation de mot de passe pour votre environnement de test Microsoft 365

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

La réinitialisation de mot de passe en libre-service (SSPR) d’Azure Active Directory (Azure AD) permet aux utilisateurs de réinitialiser ou de déverrouiller leurs mots de passe ou leurs comptes. 

Cet article vous explique comment configurer et tester les réinitialisations de mot de passe dans votre environnement de test Microsoft 365 en trois étapes :

1.  Créer l’environnement de test Microsoft 365 Entreprise.
2.  Activer la réécriture du mot de passe.
3.  Configurer et tester la réinitialisation de mot de passe pour le compte Utilisateur 3.
    
![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Tout d’abord, suivez les instructions fournies dans l’article [Synchronisation de hachage de mot de passe](password-hash-sync-m365-ent-test-environment.md). Voici la configuration que vous obtenez.
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants :  
  
- Abonnements d’évaluation ou payants Microsoft 365 E5 ou Office 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, qui se compose des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. 
- Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine Windows Server AD TESTLAB (Active Directory Domain Services : AD DS) avec le client Azure AD de votre abonnement Microsoft 365 ou Office 365.

## <a name="phase-2-enable-password-writeback"></a>Étape 2 : Activation de la réécriture du mot de passe

Suivez les instructions dans [Phase 2 du guide de laboratoire de test de réécriture du mot de passe](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

La fonction de réécriture du mot de passe doit être activée pour qu’il soit possible d’opérer une réinitialisation de mot de passe.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Étape 3 : Configuration et test de la réinitialisation de mot de passe

Lors de cette étape, vous configurez la réinitialisation de votre mot de passe dans le client Azure AD en fonction de l’appartenance de groupe, puis vous vérifiez qu’elle fonctionne.

Tout d’abord, activez la réinitialisation de mot de passe pour les comptes d’un groupe Azure AD spécifique.

1. Dans une instance privée de votre navigateur, ouvrez [https://portal.azure.com](https://portal.azure.com), puis connectez-vous avec les informations d’identification de votre compte Administrateur général.
2. Dans le portail Azure, cliquez sur **Azure Active Directory > Groupes > Nouveau groupe**.
3. Définissez le **Type de groupe** sur **Sécurité**, le **Nom du groupe** sur **PWReset**et le **Type d’appartenance** sur **Affecté**. 
4. Cliquez sur **Membres**, recherchez et sélectionnez **Utilisateur 3**, cliquez sur **Sélectionner**, puis cliquez sur **Créer**.
5. Fermez le volet **Groupes**.
6. Dans la page d’Azure Active Directory, cliquez sur **Réinitialiser le mot de passe** du volet de navigation gauche.
7. Sur la page **Propriétés–Réinitialiser le mot de passe**, sous l’option **Réinitialisation du mot de passe en libre-service activée**, choisissez **Sélectionné**.
8. Cliquez sur **Sélectionner le groupe**, sélectionnez le groupe **PWReset**, puis cliquez sur **Sélectionner > Enregistrer**.
9. Fermez l’instance privée du navigateur.

Testez ensuite la réinitialisation de mot de passe pour le compte Utilisateur 3.

1. Ouvrez une nouvelle instance privée du navigateur et accédez à [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
2. Connectez-vous avec les informations d’identification du compte Utilisateur 3.
3. Dans **Plus d’informations sont nécessaires**, cliquez sur **Suivant**. 
5. Dans **Ne perdez pas l’accès à votre compte**, indiquez votre numéro de téléphone portable pour configurer le l’authentification par téléphone et votre adresse électronique personnelle ou professionnelle pour configurer l’authentification par adresse électronique.
7. Une fois que tous deux ont été vérifiés, cliquez sur **Les informations semblent correctes** et fermez l’instance privée du navigateur.
8. Ouvrez une nouvelle instance privée du navigateur et accédez à [https://aka.ms/sspr](https://aka.ms/sspr).
9. Tapez le nom du compte Utilisateur 3, saisissez les caractères de la CAPTCHA, puis cliquez sur **Suivant**.
10. Pour **la première étape de vérification**, cliquez sur **Envoyer un e-mail à mon autre adresse électronique**, puis cliquez sur **Envoyer**. Lorsque vous recevez l’e-mail, saisissez le code de vérification, puis cliquez sur **Suivant**.
11. Dans **Revenir à votre compte**, tapez un nouveau mot de passe pour le compte utilisateur 3, puis cliquez sur **Terminer**. Notez le mot de passe modifié du compte d’utilisateur 3 et stockez-le dans un endroit sûr.
12. Dans un onglet distinct du même navigateur, accédez à [https://portal.office.com](https://portal.office.com), puis connectez-vous avec le nom de compte Utilisateur 3 et son nouveau mot de passe. Vous devez voir la **page d’accueil Microsoft Office**.

Consultez l’étape [Simplifier les réinitialisations de mot de passe](identity-secure-your-passwords.md#identity-pw-reset) de la phase d’identification pour obtenir des informations et des liens qui vous permettront de configurer des réinitialisations de mot de passe en production.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
