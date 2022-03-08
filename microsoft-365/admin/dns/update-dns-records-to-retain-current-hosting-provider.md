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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Découvrez comment router le trafic vers un site web public existant hébergé en dehors de Microsoft, si vous avez demandé à Microsoft de gérer les enregistrements DNS pour votre domaine personnalisé.
ms.openlocfilehash: 9bb12d4f73e8d95717ddd90492fb9cb97c73eec9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314819"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel

 **Si vous gérez les enregistrements Microsoft** de votre domaine chez votre fournisseur d’hébergement DNS, vous n’avez pas à vous soucier des étapes de cette rubrique. Votre site web reste en place et les utilisateurs peuvent toujours y accéder. 
  
 **Si Microsoft gère vos enregistrements DNS**, pour router le trafic vers un site web public existant hébergé en dehors de Microsoft, après avoir ajouté votre domaine à Microsoft, vous devez : 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Mettre à jour les enregistrements DNS dans le Centre d'administration Microsoft 365
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

1. Dans la page **Domaines** , sélectionnez le domaine, puis choisissez **Enregistrements DNS**.

1. **Sélectionnez + Ajouter un enregistrement**, puis entrez ce qui suit : 
    
   - For **type** enter: **A (Address)**
    
   - Pour **Nom d'hôte ou Alias**, tapez **@**.
    
   - Pour **Adresse IP**, tapez l'adresse IP statique correspondant à l'hébergement actuel de votre site web (par exemple, 172.16.140.1). 
    
   Il doit s'agir d'une adresse IP  *statique*  pour le site web (et non d'une adresse IP  *dynamique*  ). Vérifiez l'emplacement d'hébergement de votre site web pour vous assurer que vous pouvez obtenir une adresse IP statique pour votre site web public. 
    
1. Sélectionnez **Enregistrer**. 
    
De plus, vous pouvez créer un enregistrement CNAME pour aider les clients à trouver votre site web.
  
1. **Sélectionnez + Ajouter un enregistrement**, puis entrez ce qui suit : 
    
   - For **type** enter: **CNAME (Alias)**
    
   - Pour **Nom d'hôte ou Alias**, tapez **www**
    
   - Pour **Adresse de pointage**, tapez le nom de domaine complet (FQDN) de votre site web (par exemple, contoso.com). 
    
2. Sélectionnez **Enregistrer**. 
    
Pour terminer, procédez comme suit :
  
[Mettez à jour les enregistrements NS de votre domaine pour qu’ils](../setup/add-domain.md) pointent vers Microsoft. 
  
Lorsque les enregistrements NS ont été mis à jour pour pointer vers Microsoft, votre domaine est tous mis en place. Le courrier électronique est acheminé vers Microsoft et le trafic vers votre adresse de site web continue d’être acheminé vers l’hôte de votre site web actuel.
