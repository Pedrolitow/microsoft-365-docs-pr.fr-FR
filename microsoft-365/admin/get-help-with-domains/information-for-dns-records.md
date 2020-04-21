---
title: Collecter les informations nécessaires pour créer des enregistrements DNS
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: 'Découvrez comment trouver les valeurs/informations dont vous avez besoin pour créer des enregistrements DNS pour Microsoft 365. '
ms.custom: okr_smb
ms.openlocfilehash: 9cfefa2620b6a46b7488a29c22a58d70f53c6ad2
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43628445"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>Collecter les informations nécessaires pour créer des enregistrements DNS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Étape 1 : Rechercher la valeur de l’enregistrement TXT et vérifier

::: moniker range="o365-worldwide"

1. Dans le centre d’administration Microsoft 365, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> **d’installation** > .

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaines</a> **d’installation** > .

::: moniker-end
    
2. Sur la page **domaines** , sélectionnez votre domaine, puis **Démarrer le programme d’installation**. Revenez à l'Assistant de configuration de domaines pour afficher la valeur spécifique que vous devez ajouter.
    
3. Sur la page **vérifier le domaine** , sélectionnez **Ajouter un enregistrement txt**à la place, puis sélectionnez **suivant**.
    
4. Copiez la **valeur txt** affichée. Il se présente comme ceci : **MS = msXXXXXXXX**. 
    
5. Accédez à [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS](create-dns-records-at-any-dns-hosting-provider.md)et sélectionnez votre hôte DNS dans la liste des bureaux d’enregistrement pour voir les instructions pas à pas.
    
6. Suivez les étapes de création de l’enregistrement TXT (ou enregistrement MX) au niveau de votre hôte DNS, puis vérifiez le domaine dans Microsoft 365.

7. Supprimez l’enregistrement TXT (ou l’enregistrement MX) de votre hôte DNS une fois le domaine vérifié dans Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Étape 2 : trouver la valeur de l’enregistrement MX pour la messagerie électronique et plus

::: moniker range="o365-worldwide"

1. Dans le centre d’administration Microsoft 365, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .

::: moniker-end
    
::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> **d’installation** > .

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaines</a> **d’installation** > .

::: moniker-end
    
2. Dans la page **Domaines**, sélectionnez votre domaine. 
    
3. Les enregistrements DNS à ajouter se trouvent sous **Paramètres DNS requis**.
    
    Il est recommandé de conserver ces informations disponibles tandis que vous apportez des modifications à votre hôte DNS, pour que vous puissiez copier et coller les valeurs.
    
    Les groupes d'enregistrements DNS figurant dans cette page dépendent des choix disponibles sous **Intention de domaine**.
    
4. Accédez à [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS](create-dns-records-at-any-dns-hosting-provider.md), puis sélectionnez votre hôte DNS dans la liste des bureaux d’enregistrement pour voir les instructions pas à pas pour ajouter des enregistrements sur le site Web de l’hôte DNS.
    
5. Suivez la procédure de création des enregistrements auprès de votre hôte DNS.
