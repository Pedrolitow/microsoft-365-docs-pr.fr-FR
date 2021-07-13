---
title: Utiliser un code QR pour vous Outlook applications mobiles
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: Découvrez comment utiliser un code QR pour vous authentifier et télécharger Outlook mobile.
ms.openlocfilehash: c13fbeabd320c64925165ba16797d5a3471961ad
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53391338"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>Utiliser un code QR pour vous Outlook applications mobiles

> [!IMPORTANT]
> Cette fonctionnalité est uniquement disponible pour les organisations qui ont désactivé la publication ciblée dans le Centre d’administration Microsoft 365. Pour activer la version ciblée et en savoir plus sur son fonctionnement, voir Configurer les options de publication [standard ou ciblée.](release-options-in-office-365.md) Nous allons développer davantage d’organisations au cours des prochaines semaines jusqu’à la prévisualisation publique. La prévisualisation publique permet d’accéder en avant-première Microsoft 365 fonctionnalités.

En tant qu’administrateur Microsoft 365, vous pouvez permettre à vos utilisateurs de se connectez à Outlook pour Android ou l’application iOS sur leurs appareils mobiles sans avoir à entrer leur nom d’utilisateur et leur mot de passe. En analysant un code QR, les utilisateurs peuvent s’authentifier en toute sécurité et se Outlook mobile.

Dans Outlook sur le web applications de bureau ou d’autres applications Outlook bureau, les utilisateurs peuvent voir des notifications les informant qu’ils peuvent utiliser Outlook sur leur appareil mobile. Ces notifications peuvent être gérées par l’administrateur à l’aide Exchange PowerShell. Si les utilisateurs choisissent de s’envoyer eux-mêmes un SMS pour télécharger l’application sur leur appareil mobile, un code QR s’affiche sur leur ordinateur. Ils pourront analyser le code QR pour se connecter Outlook téléphone ou tablette. Ce code QR est un jeton à durée de vie courte qui ne peut être échangé qu’une seule fois.

> [!NOTE]
> Dans certains cas, vos utilisateurs doivent s’authentifier à nouveau sur leur ordinateur pour générer le code QR.

## <a name="use-exchange-powershell"></a>Utiliser Exchange PowerShell

Cette fonctionnalité est activée par défaut. Pour désactiver cette fonctionnalité, suivez les étapes ci-dessous.

1. [Connecter à Exchange PowerShell.](/powershell/exchange/connect-to-exchange-online-powershell)
2. À l’aide de PowerShell, vous pouvez désactiver les notifications informant vos utilisateurs des Outlook applications mobiles. Cela empêche également l’affichage du flux de la signature du code QR.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

## <a name="related-content"></a>Contenu associé

[Configurer les options de publication standard](release-options-in-office-365.md) ou ciblée (article)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (article)