---
title: Ajouter et remplacer votre domaine de secours onmicrosoft.com dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- VSBFY23
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ''
description: Découvrez comment créer un domaine onmicrosoft.com et en faire votre nouveau domaine de secours.
ms.openlocfilehash: 9382921fcb8d93770c056b11b2c3bb89ceb01a2d
ms.sourcegitcommit: ab32c6e19af08837aaa84a058653c3a209d366ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2022
ms.locfileid: "67445179"
---
# <a name="add-and-replace-your-onmicrosoftcom-fallback-domain-in-microsoft-365"></a>Ajouter et remplacer votre domaine de secours onmicrosoft.com dans Microsoft 365

Lorsque vous vous inscrivez à Microsoft 365, Microsoft fournit un domaine *onmicrosoft.com* ( votre **domaine de secours** ) si vous ne possédez pas de domaine ou ne souhaitez pas le connecter à Microsoft 365 (par exemple, tailspintoys.onmicrosoft.com). Votre domaine de secours est utilisé par défaut dans :

- Noms d’utilisateur et adresses e-mail
- Les équipes Microsoft 365 & groupes d’alias de messagerie
- Déplacements automatiques des dépendances de domaine

Il sert d’adresse de routage par défaut pour votre environnement Microsoft 365. Lorsqu’un utilisateur est configuré avec une boîte aux lettres, l’e-mail est acheminé vers le domaine de secours.  Même si un domaine personnalisé est utilisé (par exemple, tailspintoys.com), si ce domaine personnalisé est supprimé de votre environnement Microsoft 365, le domaine de secours garantit que l’e-mail de votre utilisateur est correctement routée.

Vous pouvez modifier votre domaine de secours dans le Centre d'administration Microsoft 365. Les raisons courantes pour lesquelles les clients modifient leur domaine de secours sont les suivantes :

- Ne sachant pas le nom de l’entreprise à utiliser lors de sa première inscription à Microsoft 365. Maintenant qu’ils connaissent le nom de l’entreprise, ils veulent que leurs utilisateurs aient les noms de compte de connexion appropriés. 
- Ils souhaitent modifier l’apparence de leurs URL SharePoint lorsqu’ils créent un site. Les URL SharePoint dans votre environnement Microsoft 365 sont créées en fonction de votre nom de domaine de secours. Si vous n’avez pas utilisé le nom d’entreprise approprié lors de votre première inscription, vos URL SharePoint pour vos sites continueront à utiliser ce nom lorsque vous créerez des sites SharePoint. 


Bien que vous puissiez ajouter d’autres domaines onmicrosoft.com, un seul domaine onmicrosoft.com peut être utilisé comme domaine de secours. Les étapes décrites dans cet article décrivent comment :
- Créer un domaine onmicrosoft.com
- Affectez-le comme domaine de secours

> [!NOTE]
> Vous êtes limité à cinq domaines onmicrosoft.com dans votre environnement Microsoft 365. Une fois qu’elles sont ajoutées, elles ne peuvent pas être supprimées. 
  
## <a name="before-you-begin"></a>Avant de commencer

Pour ajouter, modifier ou supprimer des domaines, vous **devez** être **administrateur de domaine** ou **administrateur général** d’un [plan d'affaires ou d'entreprise](https://products.office.com/business/office). Ces modifications affectent l’ensemble du locataire ; *les administrateurs personnalisés* ou *utilisateurs réguliers* ne pourront pas apporter ces modifications.


## <a name="add-a-new-onmicrosoftcom-domain"></a>Ajouter un nouveau domaine onmicrosoft.com

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Paramètres**, puis **Domaines**.
2. Sélectionnez votre onmicrosoft.com domaine par défaut.

    ![Page Domaines.](../../media/onmicrosoft-domains.png)
  
3. Dans la page Propriétés du domaine, dans la section **À propos de ce domaine** , sélectionnez **Ajouter un domaine onmicrosoft**.

    ![À propos de cette page de domaines.](../../media/add-onmicrosoft-domain-link.png)

4. Dans la page **Ajouter un domaine onmicrosoft** , dans la zone **Nom de domaine** , tapez le nom de votre nouveau domaine onmicrosoft.com. 

    ![Capture d’écran de la page Ajouter un domaine onmicrosoft.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > Veillez à vérifier l’orthographe et la précision du nom de domaine que vous avez entré. Vous êtes limité à cinq domaines onmicrosoft.com et ne peuvent pas être supprimés une fois créés.     

5. Sélectionnez **Ajouter un domaine**. Une fois l’ajout réussi, vous verrez un message indiquant cela. 
    
    ![Capture d’écran de l’ajout réussi du domaine.](../../media/domain-added.png)



## <a name="make-your-new-onmicrosoftcom-domain-your-fallback-domain"></a>Faites de votre nouveau domaine onmicrosoft.com votre domaine de secours


> [!NOTE]
> Avant de remplacer votre domaine de secours par un nouveau domaine onmicrosoft.com, vous pouvez envisager de modifier votre domaine SharePoint onmicrosoft.com. La création d’un domaine onmicrosoft supplémentaire et son utilisation en tant que domaine de secours n’entraînent pas de changement de nom pour SharePoint Online. Vos URL SharePoint et OneDrive existantes restent les mêmes.  Vous pouvez modifier votre domaine SharePoint .onmicrosoft en suivant les étapes PowerShell fournies dans la [préversion du renommage de domaine SharePoint](/sharepoint/change-your-sharepoint-domain-name) (actuellement disponible pour tout locataire avec moins de 10 000 sites).

Une fois que vous avez créé votre nouveau domaine onmicrosoft.com, procédez comme suit pour le remplacer par votre domaine de secours.

1. Dans le Centre d'administration Microsoft 365, sélectionnez **Paramètres**, puis **Domaines**. 

2. Sélectionnez le nouveau domaine onmicrosoft.com que vous avez créé.

    ![Sélectionnez un domaine.](../../media/onmicrosoft-domains-added.png) 

3. Dans la page de propriétés du domaine, **sélectionnez Définir le domaine de secours**.
 
    ![Capture d’écran de la sélection d’un nouveau domaine de secours.](../../media/new-fallback.png) 

4. Un message s’affiche sur la page indiquant que votre domaine de secours a été remplacé par le nouveau domaine.

    ![Ajout réussi d’un nouveau domaine de secours.](../../media/fallback-success.png) 

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](domains-faq.yml) (article)</br>
[Qu’est-ce qu’un domaine ?](../get-help-with-domains/what-is-a-domain.md) (article)</br>
[Acheter un nom de domaine dans Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)</br>
[Ajouter des enregistrements DNS pour connecter votre domaine](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (article)</br>
[Modifier les serveurs de noms de manière à configurer Microsoft 365 avec n'importe quel bureau d'enregistrement de domaines](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (article)
