---
title: Réinitialisation de mot de passe pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/13/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Résumé : Configurez et testez la réinitialisation de mot de passe pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 9aa55f42ca295577bf3b1c81ee54b1160adf3d27
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198372"
---
# <a name="password-reset-for-your-microsoft-365-test-environment"></a>Réinitialisation de mot de passe pour votre environnement de test Microsoft 365

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

La réinitialisation de mot de passe en libre-service (SSPR) d’Azure Active Directory (Azure AD) permet aux utilisateurs de réinitialiser ou de déverrouiller leurs mots de passe ou leurs comptes.

Cet article explique comment configurer et tester les réinitialisations de mot de passe dans Microsoft 365 environnement de test.

La configuration de SSPR implique trois phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Étape 2 : Activation de la réécriture du mot de passe](#phase-2-enable-password-writeback)
- [Étape 3 : Configuration et test de la réinitialisation de mot de passe](#phase-3-configure-and-test-password-reset)
    
![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Tout d’abord, suivez les instructions de la synchronisation [de hachage de mot de passe.](password-hash-sync-m365-ent-test-environment.md) 

La configuration qui en résulte ressemble à ceci :
  
![Environnement de test de l’entreprise simulée avec synchronisation de hachage de mot de passe.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure.
- Azure AD Connect s’exécute sur APP1 pour synchroniser le domaine TESTLAB Active Directory Domain Services (AD DS) avec le client Azure AD de votre abonnement Microsoft 365.

## <a name="phase-2-enable-password-writeback"></a>Étape 2 : Activation de la réécriture du mot de passe

Suivez les instructions dans [Phase 2 du guide de laboratoire de test de réécriture du mot de passe](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

La fonction de réécriture du mot de passe doit être activée pour qu’il soit possible d’opérer une réinitialisation de mot de passe.
  
## <a name="phase-3-configure-and-test-password-reset"></a>Étape 3 : Configuration et test de la réinitialisation de mot de passe

Dans cette phase, configurez la réinitialisation du mot de passe dans le client Azure AD via l’appartenance à un groupe, puis vérifiez qu’elle fonctionne.

Tout d’abord, activez la réinitialisation de mot de passe pour les comptes d’un groupe Azure AD spécifique.

1. Dans une instance privée de votre navigateur, ouvrez [https://portal.azure.com](https://portal.azure.com), puis connectez-vous avec les informations d’identification de votre compte Administrateur général.
2. Dans le portail Azure, sélectionnez **Azure Active Directory**  >  **Groupe Nouveau**  >  **groupe.**
3. Définissez le **Type de groupe** sur **Sécurité**, le **Nom du groupe** sur **PWReset** et le **Type d’appartenance** sur **Affecté**.
4. Sélectionnez **Membres,** recherchez et **sélectionnez Utilisateur 3,** **sélectionnez Sélectionner,** puis **créez.**
5. Fermez le volet **Groupes**.
6. Dans le volet Azure Active Directory, sélectionnez **Réinitialiser** le mot de passe dans le volet de navigation gauche.
7. Sur la page **Propriétés–Réinitialiser le mot de passe**, sous l’option **Réinitialisation du mot de passe en libre-service activée**, choisissez **Sélectionné**.
8. Sélectionnez **Sélectionner** un groupe, sélectionnez le groupe **PWReset,** puis **sélectionnez**  >  **Enregistrer.**
9. Fermez l’instance privée du navigateur.

Ensuite, testez la réinitialisation du mot de passe pour le compte Utilisateur 3.

1. Ouvrez une nouvelle instance privée du navigateur et accédez à [https://aka.ms/ssprsetup](https://aka.ms/ssprsetup).
1. Connectez-vous avec les informations d’identification du compte Utilisateur 3.
1. Dans plus **d’informations requises,** sélectionnez **Suivant.** 
1. Dans **Ne perdez pas l’accès à votre compte**, indiquez votre numéro de téléphone portable pour configurer l’authentification par téléphone et votre adresse électronique personnelle ou professionnelle pour configurer l’authentification par adresse électronique.
1. Une fois les deux vérifiés, **sélectionnez Apparences,** puis fermez l’instance privée du navigateur.
1. Dans une nouvelle instance de navigateur privé, allez à [https://aka.ms/sspr](https://aka.ms/sspr) .
1. Entrez le nom du compte Utilisateur 3, entrez les caractères de la CAPTCHA, puis sélectionnez **Suivant**.
1. Pour **l’étape de vérification 1,** **sélectionnez Envoyer un e-mail** à mon courrier de remplacement, puis sélectionnez **Courrier électronique.** Lorsque vous recevez l’e-mail, entrez le code de vérification, puis sélectionnez **Suivant**.
1. Dans **Revenir à votre compte,** entrez un nouveau mot de passe pour le compte Utilisateur 3, puis sélectionnez **Terminer.** Notez le mot de passe modifié du compte d’utilisateur 3 et stockez-le dans un endroit sûr.
1. Dans un onglet distinct du même navigateur, accédez à [https://admin.microsoft.com](https://admin.microsoft.com), puis connectez-vous avec le nom de compte Utilisateur 3 et son nouveau mot de passe. Vous devez voir la **page d’accueil Microsoft Office**.

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)