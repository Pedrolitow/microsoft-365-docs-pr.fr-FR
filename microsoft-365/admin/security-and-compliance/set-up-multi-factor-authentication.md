---
title: Configurer l’authentification multifacteur pour les utilisateurs d’Office 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Découvrez comment utiliser les paramètres par défaut de sécurité pour configurer multi-factor authentication pour les utilisateurs d’Office 365.
monikerRange: o365-worldwide
ms.openlocfilehash: 7e48f72f2fd8cfc5042bd15f994cc98bfa5fca8c
ms.sourcegitcommit: dbbdeca5a6cd048e1bde9e820a8b8a0d6022c7a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "43503970"
---
# <a name="set-up-multi-factor-authentication"></a>Configurer Multi-factor Authentification (MFA)
  
> [!IMPORTANT]
> Si vous avez acheté votre abonnement ou une version d’évaluation après le 21 octobre 2019, et que vous êtes invité de manière inattendue à utiliser l’authentification multifacteur (MFA), les [paramètres par défaut de sécurité](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) ont été automatiquement activés pour votre abonnement.

Les paramètres de sécurité par défaut sont automatiquement activés avec tout nouvel abonnement Office 365 pour les entreprises ou Microsoft 365 Entreprise. Cela signifie que chaque utilisateur devra configurer MFA et installer l’application Microsoft Authenticator sur son appareil mobile. Pour en savoir plus, voir [Configurer la vérification en deux étapes pour Office 365](https://support.office.com/article/ace1d096-61e5-449b-a875-58eb3d74de14).  

Les neuf rôles d’administrateur suivants sont nécessaires pour effectuer une authentification supplémentaire lorsqu’ils se connectent :

- Administrateur général
- Administrateur SharePoint
- Administrateur Exchange
- Administrateur de l’accès conditionnel
- Administrateur de sécurité
- Administrateur du support technique ou Administrateur de mot de passe
- Administrateur de facturation
- Administrateur d’utilisateurs
- Administrateur d’authentification

Tous les autres utilisateurs seront invités à effectuer une authentification supplémentaire si nécessaire. Pour plus d’informations, consultez [qu’est-ce que les paramètres de sécurité par défaut ?](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

> [!NOTE]
> Vous devez être un administrateur général Office 365 pour configurer ou modifier l’authentification multifacteur. <br><br>
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

Si vous avez déjà configuré Multi-Factor Authentication avec des stratégies de référence, [vous devez les désactiver et activer les paramètres de sécurité par défaut](#move-from-baseline-policies-to-security-defaults). Toutefois, si vous avez Microsoft 365 Business ou que votre abonnement inclut [Azure Active Directory Premium P1 ou Azure Active Directory Premium P2](https://azure.microsoft.com/pricing/details/active-directory/), vous pouvez également configurer des stratégies d' [accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) . Pour utiliser des stratégies d’accès conditionnel, vous devez vous assurer que [l’authentification moderne](#enable-modern-authentication-for-your-organization) est activée.

> [!TIP]
> Pour expliquer la configuration de l’application Authenticator à vos utilisateurs, consultez [Utiliser Microsoft Authenticator avec Office 365](https://support.office.com/article/use-microsoft-authenticator-with-office-365-1412611f-ad8d-43ab-807c-7965e5155411?ui=en-US&rs=en-US&ad=US#ID0EAADAAA=_Step_1).

## <a name="manage-security-defaults"></a>Gérer les paramètres de sécurité par défaut

1. Connectez-vous au [centre d'administration](https://go.microsoft.com/fwlink/p/?linkid=834822) à l'aide de vos informations d'identification d'administrateur général.
2. Accès à [Propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
3. Au bas de la page, sélectionnez **Gérer les paramètres de sécurité par défaut**.
4. Choisissez **Oui** pour activer les paramètres de sécurité par défaut ou **non** pour désactiver les paramètres de sécurité par défaut, puis cliquez sur **Enregistrer**.

## <a name="move-from-baseline-policies-to-security-defaults"></a>Basculez des stratégies de base aux paramètres de sécurité par défaut

1. Dans le [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=834822), sélectionnez **Afficher tout**, puis **Azure Active Directory** sous **centres d’administration**.

2. Dans le **Centre d’administration Azure Active Directory** , choisissez**sécurité** **Azure Active Directory** > .

3. Dans la **sécurité | Page mise en route** , choisissez **accès conditionnel**. 

4. Sur la page conditions d' **accès conditionnelles** , choisissez chaque stratégie de planification **activée**et définissez-les sur **désactivé**.
5. Accédez à la page [Propriétés d'Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
6. En bas de la page, choisissez **gérer les paramètres de sécurité par défaut**, puis dans le volet **activer les paramètres de sécurité par défaut** , définissez activer les **paramètres** de sécurité par défaut sur **Oui**, puis cliquez sur **Enregistrer**. 

## <a name="enable-modern-authentication-for-your-organization"></a>Activer l’authentification moderne pour votre organisation

Les applications clientes Office 2016 prennent en charge l'authentification multifacteur via l'utilisation de la bibliothèque ADAL (Active Directory Authentication Library). Par conséquent, les mots de passe d'application ne sont pas requis pour les clients Office 2016. Vous devez toutefois vous assurer que votre abonnement Office 365 est activé pour ADAL ou authentification moderne.

1. Pour activer l’authentification moderne, dans le [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=834822), sélectionnez **Paramètres** \> **Paramètres**, puis dans l’onglet **Services**, choisissez **Authentification moderne** dans la liste.

2. Activez la case à cocher **activer l’authentification moderne (recommandé)** dans le panneau **authentification moderne** , puis choisissez **enregistrer les modifications**. 

    ![Panneau d’authentification moderne avec la case Activer cochée.](../../media/enablemodernauth.png)
    
> [!IMPORTANT]
> Depuis août 2017, tous les nouveaux clients Office 365 qui incluent Skype Entreprise Online et Exchange Online ont l’authentification moderne activée par défaut. Pour vérifier le statut de votre authentification moderne pour Skype Entreprise Online, vous pouvez utiliser PowerShell Skype Entreprise Online avec les informations d’identification d’Administrateur général. Exécutez Get-CsOAuthConfiguration pour vérifier la sortie de-ClientADALAuthOverride. Si-ClientADALAuthOverride est « Autorisé », votre authentification moderne est activée.

Pour vérifier l’état de votre MA pour Exchange Online, consultez [Activer l’authentification moderne dans Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online).

## <a name="related-articles"></a>Articles connexes

[10 principales méthodes pour sécuriser les offres Office 365 et Microsoft 365 Entreprise](secure-your-business-data.md)

[Activer l’Authentification moderne pour Office 2013 sur les appareils Windows](enable-modern-authentication.md)
