---
title: Utiliser un code QR pour se connecter aux applications mobiles Outlook
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: Découvrez comment utiliser un code QR pour authentifier et télécharger Outlook Mobile.
ms.openlocfilehash: a648722877580899f9747afa20bd758be2589a7ab2fb794a636614b032e063cf
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53824394"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>Utiliser un code QR pour se connecter aux applications mobiles Outlook

> [!IMPORTANT]
> Cette fonctionnalité est uniquement disponible pour les organisations qui ont activé la version ciblée dans le Centre d’administration Microsoft 365. Pour activer la version ciblée et en savoir plus sur son fonctionnement, consultez [Configurer les options de mise en production standard ou ciblée](release-options-in-office-365.md). Nous étendrons à d’autres organisations au cours des prochaines semaines via la préversion publique. La préversion publique fournit un accès anticipé aux fonctionnalités Microsoft 365.

En tant qu’administrateur Microsoft 365, vous pouvez autoriser vos utilisateurs à se connecter à l’application Outlook pour Android ou iOS sur leurs appareils mobiles sans avoir à entrer leur nom d’utilisateur et leur mot de passe. En analysant un code QR, les utilisateurs peuvent s’authentifier et se connecter en toute sécurité à Outlook Mobile.

Dans Outlook sur le web ou d’autres applications Outlook de bureau, les utilisateurs peuvent voir des notifications les informant qu’ils peuvent utiliser Outlook sur leur appareil mobile. Ces notifications peuvent être gérées par l’administrateur à l’aide d’Exchange PowerShell. Si les utilisateurs choisissent de s’envoyer eux-mêmes un SMS pour télécharger l’application sur leur appareil mobile, un code QR s’affiche sur leur ordinateur. Ils pourront scanner le code QR pour se connecter à Outlook sur leur téléphone ou tablette. Ce code QR est un jeton de courte durée qui ne peut être utilisé qu’une seule fois.

La notification est générée uniquement si les conditions suivantes sont remplies :

1. L’expérience de code QR est activée pour le locataire (cette expérience est activée par défaut).

2. L’utilisateur n’utilise pas déjà Outlook pour iOS et Android.

3. L’utilisateur a un état vide dans le volet de lecture (ne sélectionne pas l’option d’ouverture automatique du premier e-mail).

4. L’utilisateur n’a pas ignoré la notification.

> [!NOTE]
> Dans certains cas, vos utilisateurs doivent s’authentifier à nouveau sur leur ordinateur pour générer le code QR.

## <a name="use-exchange-powershell"></a>Utiliser Exchange PowerShell

Cette fonctionnalité est activée par défaut. Pour désactiver cette fonctionnalité, suivez les étapes ci-dessous.

1. [Connexion à Exchange PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. À l’aide de PowerShell, vous pouvez désactiver les notifications informant vos utilisateurs des applications mobiles Outlook. Cela empêche également l’affichage du flux de connexion du code QR.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

## <a name="related-content"></a>Contenu associé

[Configurer les options de publication standard ou ciblée](release-options-in-office-365.md) (article)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (article)
