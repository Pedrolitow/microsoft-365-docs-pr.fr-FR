---
title: Collecter les informations dont vous avez besoin pour créer des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Collectez les valeurs/informations dont vous avez besoin pour créer des enregistrements DNS afin de connecter votre domaine à Microsoft 365 abonnement.
ms.openlocfilehash: 44421f9730cb238bc06b41c82c31471bf8431adfe77ff66aa34587fe2b2f72be
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53825702"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Collecter les informations dont vous avez besoin pour créer des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Étape 1 : rechercher la valeur de l’enregistrement TXT et vérifier

::: moniker range="o365-worldwide"

1. Dans la Centre d’administration Microsoft 365, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a>.

::: moniker-end
    
2. Dans la page **Domaines,** sélectionnez votre domaine, puis sélectionnez **Démarrer la configuration.** Revenez à l'Assistant de configuration de domaines pour afficher la valeur spécifique que vous devez ajouter.
    
3. Dans la page **Vérification du** domaine, sélectionnez Ajouter un enregistrement TXT aux enregistrements **DNS** du domaine, puis sélectionnez **Continuer**.
    
4. Copiez **la valeur TXT** affichée. Il se ressemble à ceci : **MS=msXXXXXXXX**. 
    
5. Go to [Add DNS records to connect your domain](create-dns-records-at-any-dns-hosting-provider.md), and follow the steps to add records at your DNS host’s website.
    
6. Suivez les étapes de création de l’enregistrement TXT (ou enregistrement MX) sur votre hôte DNS, puis vérifiez de nouveau le domaine dans Microsoft 365.

7. Supprimez l’enregistrement TXT (ou enregistrement MX) de votre hôte DNS une fois que le domaine est vérifié Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Étape 2 : Rechercher la valeur d’enregistrement MX pour le courrier électronique et bien plus encore

::: moniker range="o365-worldwide"

1. Dans la Centre d’administration Microsoft 365, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domains</a> page.

::: moniker-end
    
::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines</a>.

::: moniker-end
    
2. Dans la page **Domaines**, sélectionnez votre domaine.
    
3. Choisissez **Gérer DNS,** sélectionnez **Autres options** Ajouter votre propre DNS et sélectionnez Continuer à voir les enregistrements  >   DNS à ajouter. 
    
    Il est recommandé de conserver ces informations disponibles tandis que vous apportez des modifications à votre hôte DNS, pour que vous puissiez copier et coller les valeurs.
    
    Les groupes d'enregistrements DNS figurant dans cette page dépendent des choix disponibles sous **Intention de domaine**.
    
4. Go to [Add DNS records to connect your domain](create-dns-records-at-any-dns-hosting-provider.md), and follow the steps to add records at your DNS host’s website.

5. Suivez la procédure de création des enregistrements auprès de votre hôte DNS.

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](index.yml) (page de lien)