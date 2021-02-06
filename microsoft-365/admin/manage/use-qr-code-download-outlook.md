---
title: Utiliser un code QR pour vous inscrire aux applications mobiles Outlook
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
description: Découvrez comment utiliser un code QR pour authentifier et télécharger Outlook Mobile.
ms.openlocfilehash: b9e433e0c7d3f5f3466924b318e242e5ac29181c
ms.sourcegitcommit: 719b89baca1bae14455acf2e517ec18fc473636c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50122371"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>Utiliser un code QR pour vous inscrire aux applications mobiles Outlook

> [!IMPORTANT]
> Cette fonctionnalité Microsoft 365 est en prévisualisation publique. La prévisualisation publique fournit un accès en avant-première aux fonctionnalités de Microsoft 365.

En tant qu’administrateur Microsoft 365, vous pouvez permettre à vos utilisateurs de se connectent à Outlook pour Android ou à l’application iOS sur leurs appareils mobiles sans avoir à entrer leur nom d’utilisateur et leur mot de passe. En analysant un code QR, les utilisateurs peuvent s’authentifier et se connectent en toute sécurité à Outlook Mobile.

Dans Outlook sur le web ou dans d’autres applications Outlook de bureau, les utilisateurs peuvent voir des notifications les informant qu’ils peuvent utiliser Outlook sur leur appareil mobile. Ces notifications peuvent être gérées par l’administrateur à l’aide d’Exchange Powershell. Si les utilisateurs choisissent de s’envoyer eux-mêmes un SMS pour télécharger l’application sur leur appareil mobile, un code QR s’affiche sur leur ordinateur. Ils pourront analyser le code QR pour se connecter à Outlook sur leur téléphone ou tablette. Ce code QR est un jeton à durée de vie courte qui ne peut être échangé qu’une seule fois.

> [!NOTE]
> Dans certains cas, vos utilisateurs devront s’authentifier à nouveau sur leur ordinateur pour générer le code QR.

## <a name="use-exchange-powershell"></a>Utiliser Exchange PowerShell

Cette expérience est en place par défaut. Pour désactiver cette fonctionnalité, suivez les étapes ci-dessous.

1. [Connectez-vous à Exchange PowerShell.](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell?view=exchange-ps)
2. À l’aide de PowerShell, vous pouvez désactiver les notifications informant vos utilisateurs des applications mobiles Outlook. Cela empêche également l’affichage du flux de la signature du code QR.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

Voir aussi

[Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig?view=exchange-ps)
