---
title: Collecter les informations dont vous avez besoin pour créer des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- highpri
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Collectez les valeurs/informations dont vous avez besoin pour créer des enregistrements DNS pour connecter votre domaine à votre abonnement Microsoft 365.
ms.openlocfilehash: 6cbfb96f142c412960684427e4eac1cacc41f381
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203242"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Collecter les informations dont vous avez besoin pour créer des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Étape 1 : Rechercher la valeur de l’enregistrement TXT et vérifier

::: moniker range="o365-worldwide"

1. Dans le Centre d'administration Microsoft 365, accédez à la page **Domaines de paramètres**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a>.

::: moniker-end
    
2. Dans la page **Domaines** , sélectionnez votre domaine, puis **sélectionnez Démarrer l’installation**. Revenez à l'Assistant de configuration de domaines pour afficher la valeur spécifique que vous devez ajouter.
    
3. Dans la page **Vérification du domaine** , sélectionnez **Ajouter un enregistrement TXT aux enregistrements DNS du domaine**, puis **sélectionnez Continuer**.
    
4. Copiez la **valeur TXT** affichée. Il ressemble à ceci : **MS=msXXXXXXXX**. 
    
5. Accédez à [Ajouter des enregistrements DNS pour connecter votre domaine](create-dns-records-at-any-dns-hosting-provider.md), puis suivez les étapes pour ajouter des enregistrements sur le site web de votre hôte DNS.
    
6. Suivez les étapes de création de l’enregistrement TXT (ou enregistrement MX) sur votre hôte DNS, puis vérifiez le domaine dans Microsoft 365.

7. Supprimez l’enregistrement TXT (ou enregistrement MX) de votre hôte DNS une fois le domaine vérifié dans Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Étape 2 : Rechercher la valeur de l’enregistrement MX pour l’e-mail et bien plus encore

::: moniker range="o365-worldwide"

1. Dans le Centre d'administration Microsoft 365, accédez à la page **Domaines de paramètres**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a>.

::: moniker-end
    
2. Dans la page **Domaines**, sélectionnez votre domaine.
    
3. Choisissez  **Gérer DNS**, sélectionnez **Autres options** > **Ajouter votre propre DNS** , puis **sélectionnez Continuer** pour afficher les enregistrements DNS à ajouter.
    
    Il est recommandé de conserver ces informations disponibles tandis que vous apportez des modifications à votre hôte DNS, pour que vous puissiez copier et coller les valeurs.
    
    Les groupes d'enregistrements DNS figurant dans cette page dépendent des choix disponibles sous **Intention de domaine**.
    
4. Accédez à [Ajouter des enregistrements DNS pour connecter votre domaine](create-dns-records-at-any-dns-hosting-provider.md), puis suivez les étapes pour ajouter des enregistrements sur le site web de votre hôte DNS.

5. Suivez la procédure de création des enregistrements auprès de votre hôte DNS.

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](/admin) (page de lien)