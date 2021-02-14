---
title: Mise à niveau vers Microsoft 365 Business Premium à partir de Microsoft 365 Business Standard
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 5b4ba843-24b8-4526-8e1f-f9b9eab89d06
description: Découvrez la différence entre Microsoft 365 Business Standard et Microsoft 365 Business Premium et la façon dont vous pouvez mettre à niveau vers Microsoft 365 Business Premium.
ms.openlocfilehash: bdab8165623170926b17efa4cae9408b78a2f5f5
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44401379"
---
# <a name="upgrade-to-microsoft-365-business-premium-from-microsoft-365-business-standard"></a>Mise à niveau vers Microsoft 365 Business Premium à partir de Microsoft 365 Business Standard

Si vous avez un abonnement [Microsoft 365](https://products.office.com/compare-all-microsoft-office-products-4-column?activetab=tab:primaryr2)pour les entreprises, par exemple Microsoft 365 Business Standard, vous pouvez facilement mettre à niveau vers Microsoft 365 Business Premium. Mettre à niveau vers Microsoft 365 Business Premium si vous souhaitez ajouter :

- Windows 10 Professionnel (vers les PC exécutant Windows 8 ou une ultérieure)

- Contrôles simples qui gèrent les données métiers sur les appareils

- Fonctionnalités de sécurité avancées.
Pour en savoir plus sur Microsoft 365 Business Premium, [Microsoft.com](https://www.microsoft.com/microsoft-365/business)

## <a name="whats-the-difference-between-microsoft-365-business-standard-and-microsoft-365-business-premium"></a>Quelle est la différence entre Microsoft 365 Business Standard et Microsoft 365 Business Premium ?

Nous avons ajouté une comparaison côte à côte de ces deux plans à la description du [service Microsoft 365 Business Premium.](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-business-service-description) 

## <a name="before-you-get-started"></a>Avant de commencer

- **Quand choisir de mettre à niveau ?** La mise à niveau est le bon choix lorsque vous souhaitez mettre à niveau **tous les utilisateurs** affectés à un plan unique. Lorsque vous choisissez la mise à niveau, tous les utilisateurs du plan basculent vers un autre plan en même temps. Si vous ne souhaitez pas mettre à niveau toutes les personnes affectées à une offre unique, achetez des licences pour la nouvelle offre (dans ce cas, Microsoft 365 Business Premium) et attribuez ces [licences](../admin/manage/assign-licenses-to-users.md) individuellement à chaque utilisateur que vous souhaitez mettre à niveau.

- **Certains modules peuvent empêcher la mise à niveau** Si vous essayez de démarrer une mise à niveau et que vous avez un module qui vous empêche de continuer, vous pouvez d’abord supprimer le module, puis l’ajouter ultérieurement si vous en avez encore besoin.

- **Si vous avez prépayé votre offre** Il n’existe pas de chemin de mise à niveau simple pour les plans prépayés. Vous savez si vous avez une offre prépayée, car vous la définissez à l’aide d’un ID produit que vous avez peut-être acheté dans un magasin. Contactez un partenaire, go to the Microsoft Store, or wait until your prepaid plan expires to switch to a new plan.

## <a name="upgrade-to-microsoft-365-business-premium"></a>Mise à niveau vers Microsoft 365 Business Premium

1. Connectez-vous au Centre d’administration à <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a> l’adresse .

2. Go to the navigation pane and select **Billing** \> **Your products**. Recherchez votre abonnement actuel et sélectionnez-le pour afficher les détails.

3. Sur la page suivante, sélectionnez **Mettre à niveau.**

  > [!NOTE]
  > Si un message vous indique que la mise à niveau de votre abonnement n’est pas prise en charge avec les licences basées sur des groupes dans **Azure Active Directory,** vous pouvez ignorer cela en toute sécurité, sauf si vous avez une organisation très importante. Les organisations qui ont sélectionné cette option savent qu’elles utilisent des licences basées sur des groupes.

4. Ensuite, vous pouvez afficher la liste des plans vers qui vous pouvez mettre à niveau. Dans ce cas, recherchez l’offre Microsoft 365 Business Premium. Vous pouvez faire défiler vers le bas si vous souhaitez voir toutes les applications et services inclus dans ce plan. Sous **Microsoft 365 Business Premium, sélectionnez** **Mettre** à niveau pour ajouter Microsoft 365 Business Premium à votre panier.

5. Dans le panier :

    1. Nous inclurons automatiquement des licences pour tous vos utilisateurs actuels. Si vous avez besoin de plus ou moins de licences, vous devez acheter et [attribuer ces licences individuellement.](../admin/manage/assign-licenses-to-users.md)  
    2. Vous pouvez ajuster la façon dont vous souhaitez payer : mensuelle ou mensuelle. Sélectionnez le menu déroulant pour effectuer votre choix.

6. Sélectionnez **Go to Checkout** où vous verrez un résumé de votre achat, y compris le mode de paiement de ce compte. Vous pouvez également ajouter un code promotionnel ici si vous en avez un.

7. Select **Place order** to complete your purchase.\
La mise en place de vos nouvelles plans de service prend quelques minutes à Microsoft. Pour vérifier la progression, sélectionnez **Vérifier l’état de la mise à niveau.**

8. Lorsque votre plan est prêt, vous devrez peut-être effectuer quelques étapes de configuration supplémentaires dans le Centre d’administration. Dans le volet de navigation, sélectionnez **Accueil** pour effectuer les étapes de configuration supplémentaires.

> [!NOTE]
> Vous recevrez un remboursement au prorat pour les licences Microsoft 365 dont vous n’avez plus besoin. Votre compte bancaire ou carte bancaire sera facturé environ deux jours après la mise en place de la nouvelle plan.
  
## <a name="protect-user-devices-and-files"></a>Protéger les appareils et les fichiers des utilisateurs

Maintenant que des licences Microsoft 365 Business Premium ont été attribuées, vous devez effectuer les étapes nécessaires pour commencer à protéger les appareils et les fichiers. Vous utiliserez de nouvelles options incluses dans le volet de navigation du Centre d’administration.
  
1. Dans le centre d’administration, dans le volet de navigation, allez à **Stratégies des** \> **appareils.**

2. Dans la page **Stratégies d’appareil,** **sélectionnez Ajouter.**

3. Dans le **volet Ajouter** une stratégie, donnez un nom à la stratégie (par exemple, Protéger les fichiers de travail), puis choisissez un **type** de stratégie dans la liste liste.

    Vous pouvez configurer des stratégies d’application pour la protection des fichiers sur les appareils Android et iPhone, ainsi que Windows 10, et vous pouvez configurer des stratégies de configuration d’appareil pour les appareils Windows 10 d’entreprise. Pour plus d’informations, voir les liens suivants :

    - [Définir les paramètres de protection des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md)

    - [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md)

    - [Définir les paramètres de protection des appareils pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)

4. Une fois les stratégies définies, vous et vos employés pouvez configurer des appareils :

    - Si vos appareils Windows n’utilisent pas déjà la mise à jour du Créateur Windows Pro, vous devez les mettre à niveau vers [Windows Pro Creators Update.](upgrade-to-windows-pro-creators-update.md)

    - Voir [Configurer des appareils Windows pour les utilisateurs de Microsoft 365 Business Premium](set-up-windows-devices.md) pour obtenir la procédure à suivre pour les appareils Windows.

    - Voir Configurer des appareils mobiles pour les utilisateurs [de Microsoft 365 Business Premium](set-up-mobile-devices.md) pour obtenir la procédure pour les téléphones et iPhone Android.