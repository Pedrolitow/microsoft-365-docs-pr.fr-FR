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
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Collectez les valeurs/informations dont vous avez besoin pour créer des enregistrements DNS afin de connecter votre domaine à Microsoft 365 abonnement.
ms.openlocfilehash: e65d53269f5fb8625b12c4eb22f78516818045be
ms.sourcegitcommit: 17f0aada83627d9defa0acf4db03a2d58e46842f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52635725"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Collecter les informations dont vous avez besoin pour créer des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Étape 1 : rechercher la valeur de l’enregistrement TXT et vérifier

::: moniker range="o365-worldwide"

1. Dans le Microsoft 365 d’administration,  allez à la page \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines d’installation.</a>

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, allez à la page  > <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines d’installation.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, allez à la page  > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines d’installation.</a>

::: moniker-end
    
2. Dans la page **Domaines,** sélectionnez votre domaine, puis sélectionnez **Démarrer la configuration.** Revenez à l'Assistant de configuration de domaines pour afficher la valeur spécifique que vous devez ajouter.
    
3. Dans la page **Vérifier le domaine,** **sélectionnez Ajouter un enregistrement TXT** à la place, puis sélectionnez **Suivant**.
    
4. Copiez **la valeur TXT** affichée. Il se ressemble à ceci : **MS=msXXXXXXXX**. 
    
5. Go to [Create DNS records at any DNS hosting provider](create-dns-records-at-any-dns-hosting-provider.md), and select your DNS host from the list of registrars to see the step-by-step instructions.
    
6. Suivez les étapes de création de l’enregistrement TXT (ou enregistrement MX) sur votre hôte DNS, puis vérifiez de nouveau le domaine dans Microsoft 365.

7. Supprimez l’enregistrement TXT (ou enregistrement MX) de votre hôte DNS une fois que le domaine est vérifié Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Étape 2 : Rechercher la valeur d’enregistrement MX pour le courrier électronique et bien plus encore

::: moniker range="o365-worldwide"

1. Dans le Microsoft 365 d’administration,  allez à la page \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines d’installation.</a>

::: moniker-end
    
::: moniker range="o365-germany"

1. Dans le centre d’administration, allez à la page  > <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">Domaines d’installation.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, allez à la page  > <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">Domaines d’installation.</a>

::: moniker-end
    
2. Dans la page **Domaines**, sélectionnez votre domaine. 
    
3. Les enregistrements DNS à ajouter se trouvent sous **Paramètres DNS requis**.
    
    Il est recommandé de conserver ces informations disponibles tandis que vous apportez des modifications à votre hôte DNS, pour que vous puissiez copier et coller les valeurs.
    
    Les groupes d'enregistrements DNS figurant dans cette page dépendent des choix disponibles sous **Intention de domaine**.
    
4. Go to [Create DNS records at any DNS hosting provider,](create-dns-records-at-any-dns-hosting-provider.md)and then select your DNS host from the list of registrars to see step-by-step instructions for adding records at that DNS host’s website.
    
5. Suivez la procédure de création des enregistrements auprès de votre hôte DNS.

## <a name="related-content"></a>Contenu associé

[FAQ sur les domaines](../setup/domains-faq.yml) (article)\
[Rechercher et corriger les problèmes, y compris de messagerie, après avoir ajouté votre domaine ou des enregistrements DNS](find-and-fix-issues.md) (article)\
[Gérer des domaines](index.yml) (page de lien)