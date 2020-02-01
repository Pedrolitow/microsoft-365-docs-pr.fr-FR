---
title: Mise à niveau vers Microsoft 365 entreprise à partir d’Office 365 Business Premium
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
search.appverid:
- BCS160
- MET150
ms.assetid: 5b4ba843-24b8-4526-8e1f-f9b9eab89d06
description: Étapes de mise à niveau de votre entreprise à partir d’Office 365 Business Premium vers Microsoft 365 Business.
ms.openlocfilehash: 0732f76e5bd8540e5954bd7ea7b88061326901b5
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41593676"
---
# <a name="upgrade-to-microsoft-365-business-from-office-365-business-premium"></a>Mise à niveau vers Microsoft 365 entreprise à partir d’Office 365 Business Premium

Si vous disposez d’un [abonnement office 365 pour les entreprises](https://products.office.com/compare-all-microsoft-office-products-4-column?activetab=tab:primaryr2), par exemple, Office 365 Business Premium, vous pouvez facilement effectuer une mise à niveau vers Microsoft 365 Business. Effectuez une mise à niveau vers Microsoft 365 Business si vous voulez ajouter : 
- Windows 10 professionnel (vers des PC exécutant Windows 8 ou version ultérieure)
- Contrôles simples qui gèrent les données métiers sur les appareils
- Fonctionnalités de sécurité avancées.
En savoir plus sur Microsoft 365 Business at [Microsoft.com](https://www.microsoft.com/microsoft-365/business)

## <a name="whats-the-difference-between-office-365-business-premium-and-microsoft-365-business"></a>Quelle est la différence entre Office 365 Business Premium et Microsoft 365 Business ?
Nous avons ajouté une comparaison côte à côte de ces deux plans à la description du [service d’entreprise Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-business-service-description). 

## <a name="before-you-get-started"></a>Avant de commencer

- **Quand dois-je choisir de procéder à la mise à niveau ?** La mise à niveau est le bon choix lorsque vous souhaitez mettre à niveau **tous les utilisateurs** affectés à une seule offre. Lorsque vous choisissez mise à niveau, tous les utilisateurs de plan sont passés à un autre plan en même temps. Si vous ne souhaitez pas mettre à niveau tout le monde affecté à une seule offre, achetez des licences pour le nouveau plan (dans ce cas Microsoft 365 Business) et [affectez ces licences individuellement](https://docs.microsoft.com/office365/admin/manage/assign-licenses-to-users) à chaque utilisateur que vous souhaitez mettre à niveau. 
- **Certains modules complémentaires peuvent empêcher la mise à niveau** Si vous essayez de démarrer une mise à niveau et que vous disposez d’un module complémentaire qui vous empêche de continuer, vous pouvez supprimer d’abord le module complémentaire, puis le rajouter ultérieurement si vous en avez besoin. 
- **Si vous avez prépayé votre forfait** Il n’existe pas de mise à niveau simple pour les forfaits prépayés. Vous saurez si vous disposez d’un forfait prépayé car vous avez configuré votre plan à l’aide d’un ID de produit que vous avez peut-être acheté dans un magasin. Contactez un partenaire, accédez au Microsoft Store ou patientez jusqu’à ce que votre plan prépayé expire pour passer à un nouveau plan.

## <a name="upgrade-to-microsoft-365-business"></a>Mise à niveau vers Microsoft 365 Business
Pour acheter vos licences, procédez comme suit dans le [nouveau centre d’administration](https://docs.microsoft.com/office365/admin/microsoft-365-admin-center-preview):
1. Connectez-vous au centre d' <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>administration à l’adresse.
2. Accédez au volet de navigation et sélectionnez produits de **facturation** \> **& services**. Recherchez votre abonnement Office 365 et sélectionnez-le pour afficher les détails. 

    ![Une capture d’écran montre comment rechercher et sélectionner votre abonnement dans le centre d’administration.](media/FindYourSubscription.png)

3. Sur la page suivante, sélectionnez **mise à niveau**. 

      ![Une capture d’écran indique où sélectionner la mise à niveau dans le centre d’administration.](media/SelectUpgrade.png)

  > [!NOTE]
  > Si vous voyez un message indiquant que **la mise à niveau de votre abonnement n’est pas prise en charge avec la gestion des licences basée sur les groupes dans Azure Active Directory**, vous pouvez l’ignorer en toute sécurité, sauf si vous disposez d’une organisation très importante. Les organisations qui ont sélectionné cette option seront conscientes de l’utilisation d’une licence basée sur les groupes.

4. Ensuite, vous pouvez afficher la liste des plans Office vers lesquels vous pouvez effectuer une mise à niveau. Dans ce cas, recherchez le forfait Microsoft 365 Business. Vous pouvez faire défiler vers le bas si vous souhaitez voir tous les services et applications Office inclus dans ce plan. Sous **microsoft 365 entreprise**, sélectionnez **mettre à niveau** pour ajouter Microsoft 365 entreprise à votre panier.
5. Dans le panier :
    1. Nous inclurons automatiquement les licences pour tous vos utilisateurs actuels. Si vous avez besoin de plus ou moins de licences, vous devez [acheter et attribuer ces licences individuellement](https://docs.microsoft.com/office365/admin/manage/assign-licenses-to-users).  
    2. Vous pouvez modifier la façon dont vous souhaitez payer : tous les mois ou tous les ans. Sélectionnez le menu déroulant pour effectuer votre choix.
6. Sélectionnez **aller à la conclusion** de la transaction où vous verrez un résumé de votre achat, dont le mode de paiement pour ce compte. Vous pouvez également ajouter un code promotionnel ici si vous en avez un.
7. Sélectionnez **passer une commande** pour finaliser votre achat.
Microsoft met en place quelques minutes pour configurer vos nouveaux plans de service. Pour vérifier la progression, sélectionnez **vérifier le statut de la mise à niveau**. 
1. Une fois que votre plan est prêt, vous devrez peut-être effectuer certaines étapes de configuration supplémentaires dans le centre d’administration. Dans le volet de navigation, sélectionnez **Accueil** pour effectuer les étapes de configuration supplémentaires.

> [!NOTE]
> Vous recevrez un remboursement proversement pour les licences Office 365 dont vous n’avez plus besoin. Votre compte bancaire ou votre carte de crédit sera débité d’environ deux jours après avoir configuré le nouveau plan.
  
## <a name="protect-user-devices-and-files"></a>Protéger les appareils et les fichiers des utilisateurs

Maintenant que les licences professionnelles de Microsoft 365 ont été attribuées, suivez les étapes pour commencer à protéger les appareils et les fichiers. Vous allez utiliser certaines nouvelles options incluses dans le volet de navigation du centre d’administration.
  
1. Dans le volet de navigation du centre d’administration, accédez à **** \> **stratégies**de périphériques.
    
2. Sur la page **stratégies d’appareil** , sélectionnez **Ajouter**.
    
3. Dans le volet **Ajouter une stratégie** , donnez un nom à la stratégie (par exemple, protéger les fichiers de travail), puis choisissez un type de **stratégie** dans la liste déroulante. 
    
    Vous pouvez configurer des stratégies d’application pour protéger les fichiers sur les appareils Android et iPhone, ainsi que Windows 10, et vous pouvez configurer des stratégies de configuration d’appareil pour les appareils Windows 10 appartenant à une société. Pour plus d’informations, consultez les liens suivants :
    
  - [Définir les paramètres de protection des applications pour les appareils Android ou iOS](app-protection-settings-for-android-and-ios.md)
    
  - [Définir les paramètres de protection des applications pour les appareils Windows 10](protection-settings-for-windows-10-devices.md)
    
  - [Définir les paramètres de protection des appareils pour les PC Windows 10](protection-settings-for-windows-10-pcs.md)
    
  
4. Une fois que vous avez configuré les stratégies, vous et vos employés pouvez configurer des appareils :
    
  - Si vos appareils Windows ne sont pas déjà en cours d’utilisation par la mise à jour du créateur Windows professionnel, vous devrez [les mettre à niveau vers Windows Pro Creators Update](upgrade-to-windows-pro-creators-update.md).
    
  - Consultez la rubrique [configurer des appareils Windows pour les utilisateurs professionnels de Microsoft 365 pour les](set-up-windows-devices.md) étapes des appareils Windows. 
    
  - Pour plus d’informations sur les téléphones Android et les iPhone, consultez la rubrique [configurer des appareils mobiles pour les utilisateurs professionnels de Microsoft 365](set-up-mobile-devices.md) . 
