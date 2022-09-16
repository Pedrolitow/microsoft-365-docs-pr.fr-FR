---
title: Réinitialiser les mots de passe
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
description: Réinitialiser les mots de passe des utilisateurs dans Microsoft 365 Business Premium.
ms.openlocfilehash: 1d38b19222280d14ce953fb793c4be903f0a8793
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67739937"
---
# <a name="reset-passwords-in-microsoft-365-business-premium"></a>Réinitialiser les mots de passe dans Microsoft 365 Business Premium

Découvrez comment réinitialiser les mots de passe pour vous-même et vos utilisateurs si nécessaire. En tant qu’administrateur, vous pouvez réinitialiser le mot de passe d’un utilisateur s’il l’oublie.

## <a name="user-initiated-password-reset"></a>Réinitialisation de mot de passe initiée par l’utilisateur

Lorsqu’un utilisateur demande un nouveau mot de passe, une demande de réinitialisation de mot de passe est envoyée par e-mail.

1. Pour réinitialiser le mot de passe, ouvrez le lanceur d’applications, sélectionnez **Administration** et connectez-vous avec vos informations d’identification.

2. Dans le Microsoft 365 系統管理中心, sélectionnez **Utilisateurs**, <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Utilisateurs actifs**</a>, puis sélectionnez l’icône de clé en regard de l’utilisateur qui a demandé la réinitialisation.

3. Sélectionnez **Générer automatiquement un mot de passe** pour créer automatiquement un mot de passe aléatoire.

4. Sélectionnez **Réinitialiser**. 

## <a name="admin-initiated-password-reset"></a>réinitialisation de mot de passe initiée par Administration

Il arrive qu’un administrateur souhaite forcer la réinitialisation de mot de passe sur les comptes.

1. Dans le centre Administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a>.

2. Dans la page **Utilisateurs actifs** , sélectionnez l’utilisateur spécifique à réinitialiser, puis sélectionnez **Réinitialiser le mot de passe**.

3. Suivez les instructions de la page **Réinitialiser le mot de passe** pour générer automatiquement un nouveau mot de passe pour l’utilisateur ou en créer un pour lui, puis sélectionnez **Réinitialiser**.  

4. Entrez une adresse e-mail à laquelle l’utilisateur peut accéder pour recevoir le nouveau mot de passe, puis effectuez un suivi avec lui pour vous assurer qu’il l’a obtenu.

## <a name="let-users-reset-their-own-passwords"></a>Autoriser les utilisateurs à réinitialiser leurs mots de passe

Nous vous recommandons vivement de configurer la réinitialisation de mot de passe en libre-service. Ainsi, vous n'êtes pas tenu de réinitialiser manuellement les mots de passe de vos utilisateurs. Pour savoir comment procéder, voir [Autoriser les utilisateurs à réinitialiser leur mot de passe dans Office 365](/admin/add-users/let-users-reset-passwords.md).

## <a name="reset-my-admin-password"></a>Réinitialiser mon mot de passe d’administrateur

Procédez comme suit si vous avez oublié votre mot de passe, mais que vous pouvez vous connecter à Microsoft 365, car, par exemple, votre mot de passe est enregistré dans votre navigateur :

1. Sélectionnez votre nom (icône) dans le coin supérieur droit > Mes **informations personnelles** **de compte** > .

2. Sous **Coordonnées**, vérifiez que votre **autre adresse e-mail** est exacte et que vous avez fourni un numéro de téléphone mobile. Si ce n’est pas le cas, modifiez-les maintenant.

3. Déconnexion : sélectionnez votre nom dans le coin \> supérieur droit **. Déconnectez-vous**.

4. À présent, reconnectez-vous : tapez votre nom \> **d’utilisateur Suivant**\>, puis sélectionnez **Mot de passe oublié**.

5. Suivez les étapes de l’Assistant pour réinitialiser votre mot de passe. Il utilise vos autres informations de contact pour vérifier que vous êtes la bonne personne pour réinitialiser votre mot de passe.

Si vous avez oublié votre mot de passe et que vous ne pouvez pas vous connecter :

- Demandez à un autre administrateur général de votre entreprise de réinitialiser votre mot de passe pour vous.

- Assurez-vous que vous avez fourni d’autres informations de contact, y compris un numéro de téléphone mobile.

## <a name="reset-all-business-passwords-for-everyone-at-the-same-time"></a>Réinitialiser tous les mots de passe d’entreprise pour tout le monde en même temps

<a name="bkmk_forgot"> </a>

Ces étapes s'appliquent à une entreprise comptant des dizaines d'utilisateurs. Si vous avez des centaines ou des milliers d’utilisateurs, consultez la section suivante sur la réinitialisation des mots de passe en bloc (maximum 40 utilisateurs à la fois).
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’option en regard du **nom d’affichage** pour sélectionner tous les membres de votre entreprise. Alors, désélectionnez-vous. Vous ne pouvez pas réinitialiser votre propre mot de passe en même temps que vous réinitialisez le mot de passe de tous les autres utilisateurs.

3. Cliquez sur **Réinitialiser le mot de passe**.

4. Suivez les instructions de la page **Réinitialiser le mot de passe** , puis sélectionnez **Réinitialiser**.  Si vous avez choisi de générer automatiquement les mots de passe, les nouveaux mots de passe temporaires s’affichent.

5. Entrez une adresse e-mail dans laquelle vous pouvez recevoir les mots de passe temporaires. Vous devez informer vos utilisateurs de leurs mots de passe temporaires.
  
## <a name="reset-business-passwords-in-bulk"></a>Réinitialiser les mots de passe métier en bloc

<a name="bkmk_forgot"> </a>

Pour réinitialiser les mots de passe de plusieurs comptes, utilisez PowerShell. Lisez ce billet rédigé par Eyal Doron : [Gestion des mots de passe avec PowerShell](https://go.microsoft.com/fwlink/?linkid=853696).

Pour obtenir des informations de vue d’ensemble, consultez [Gérer Microsoft 365 avec PowerShell](../enterprise/manage-microsoft-365-with-microsoft-365-powershell.md).
  
## <a name="related-content"></a>Contenu associé
  
[Permettre aux utilisateurs de réinitialiser leurs propres mots de passe](../admin/add-users/let-users-reset-passwords.md)
 [Réinitialiser les mots de passe dans Microsoft 365 pour les entreprises](../admin/add-users/reset-passwords.md)
 [Définir le mot de passe d’un utilisateur individuel pour qu’il n’expire](../admin/add-users/set-password-to-never-expire.md) 
 jamais [Définir la stratégie d’expiration du mot de passe pour votre organisation](../admin/manage/set-password-expiration-policy.md)