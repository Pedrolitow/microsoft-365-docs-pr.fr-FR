---
title: Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel
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
- Adm_O365
- Adm_NonTOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Découvrez comment acheminer le trafic vers un site web public existant hébergé en dehors de Microsoft, si vous avez défini Microsoft pour gérer les enregistrements DNS pour votre domaine personnalisé.
ms.openlocfilehash: 914c2374bd15d4a94769203142021db86c689427
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084144"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel

 **Si vous gérez les enregistrements Microsoft de votre domaine auprès de votre fournisseur d’hébergement DNS**, vous n’avez pas à vous soucier des étapes décrites dans cette rubrique. Votre site web reste en place et les utilisateurs peuvent toujours y accéder. 
  
 **Si Microsoft gère vos enregistrements DNS**, pour acheminer le trafic vers un site web public existant hébergé en dehors de Microsoft, après avoir ajouté votre domaine à Microsoft, procédez comme suit : 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Mettre à jour les enregistrements DNS dans le Centre d'administration Microsoft 365
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

1. Dans la page **Domaines** , sélectionnez le domaine, puis choisissez **Enregistrements DNS**.

1. Sélectionnez **+ Ajouter un enregistrement** et entrez ce qui suit : 
    
   - Pour **type** , entrez : **A (Adresse)**
    
   - Pour **Nom d'hôte ou Alias**, tapez **@**.
    
   - Pour **Adresse IP**, tapez l'adresse IP statique correspondant à l'hébergement actuel de votre site web (par exemple, 172.16.140.1). 
    
   Il doit s'agir d'une adresse IP  *statique*  pour le site web (et non d'une adresse IP  *dynamique*  ). Vérifiez l'emplacement d'hébergement de votre site web pour vous assurer que vous pouvez obtenir une adresse IP statique pour votre site web public. 
    
1. Sélectionnez **Enregistrer**. 
    
De plus, vous pouvez créer un enregistrement CNAME pour aider les clients à trouver votre site web.
  
1. Sélectionnez **+ Ajouter un enregistrement** et entrez ce qui suit : 
    
   - Pour **entrer le type** : **CNAME (Alias)**
    
   - Pour **Nom d'hôte ou Alias**, tapez **www**
    
   - Pour **Adresse de pointage**, tapez le nom de domaine complet (FQDN) de votre site web (par exemple, contoso.com). 
    
2. Sélectionnez **Enregistrer**. 
    
Pour terminer, procédez comme suit :
  
[Mettez à jour les enregistrements NS de votre domaine pour qu’ils](../setup/add-domain.md) pointent vers Microsoft. 
  
Lorsque les enregistrements NS ont été mis à jour pour pointer vers Microsoft, votre domaine est configuré. Email sera routée vers Microsoft, et le trafic vers votre adresse de site web continuera d’être acheminé vers votre hôte de site web actuel.
