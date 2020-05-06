---
title: Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel
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
- Adm_NonTOC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Découvrez comment acheminer le trafic vers un site Web public existant hébergé en dehors de Microsoft, si vous avez configuré Microsoft pour gérer les enregistrements DNS pour votre domaine personnalisé.
ms.openlocfilehash: 58b58479a2c880cc0193058abc328cc5feea4af1
ms.sourcegitcommit: 5476c2578400894640ae74bfe8e93c3319f685bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "44048830"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel

 **Si vous gérez les enregistrements Microsoft de votre domaine auprès de votre fournisseur d’hébergement DNS**, vous n’avez pas à vous soucier des étapes décrites dans cette rubrique. Votre site web reste en place et les utilisateurs peuvent toujours y accéder. 
  
 **Si Microsoft gère vos enregistrements DNS**, pour acheminer le trafic vers un site Web public existant hébergé en dehors de Microsoft, après avoir ajouté votre domaine à Microsoft, procédez comme suit : 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Mettre à jour les enregistrements DNS dans le centre d’administration Microsoft 365
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.

2. Sur la page **Domaines**, dans la liste de domaines, cliquez sur celui que vous utilisez pour votre site web, puis sélectionnez **Paramètres DNS** dans le volet de gestion. 
    
3. Sélectionnez **+Nouvel enregistrement personnalisé** et entrez les éléments suivants : 
    
  - Pour **Type de DNS** entrez : **A (Adresse)**
    
  - Pour **Nom d'hôte ou Alias**, tapez **@**.
    
  - Pour **Adresse IP**, tapez l'adresse IP statique correspondant à l'hébergement actuel de votre site web (par exemple, 172.16.140.1). 
    
    Il doit s'agir d'une adresse IP  *statique*  pour le site web (et non d'une adresse IP  *dynamique*  ). Vérifiez l'emplacement d'hébergement de votre site web pour vous assurer que vous pouvez obtenir une adresse IP statique pour votre site web public. 
    
3. Sélectionnez **Enregistrer**. 
    
De plus, vous pouvez créer un enregistrement CNAME pour aider les clients à trouver votre site web.
  
1. Sélectionnez **+Nouvel enregistrement personnalisé** et entrez les éléments suivants : 
    
  - Pour **Type de DNS** entrez : **CNAME (Alias)**
    
  - Pour **Nom d'hôte ou Alias**, tapez **www**
    
  - Pour **Adresse de pointage**, tapez le nom de domaine complet (FQDN) de votre site web (par exemple, contoso.com). 
    
2. Sélectionnez **Enregistrer**. 
    
Pour terminer, procédez comme suit :
  
[Mettez à jour les enregistrements NS de votre domaine](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions) pour qu’ils pointent vers Microsoft. 
  
Lorsque les enregistrements NS ont été mis à jour pour pointer vers Microsoft, votre domaine est configuré. Le courrier électronique sera acheminé vers Microsoft, et le trafic vers votre adresse de site Web continuera à accéder à votre hôte de site Web actuel.
 
