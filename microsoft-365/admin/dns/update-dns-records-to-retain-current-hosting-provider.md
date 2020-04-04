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
description: Découvrez comment router le trafic vers un site Web public existant hébergé en dehors d’Office 365, si vous avez configuré Office 365 pour gérer les enregistrements DNS pour votre domaine personnalisé.
ms.openlocfilehash: 3e71925f9b50e5520bd383aa5318db513202f6ec
ms.sourcegitcommit: ff62dd99fa0d4e780da25dc622f93ddc8f7f95a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "43142538"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>Mettre à jour les enregistrements DNS pour conserver votre site web chez votre fournisseur d'hébergement actuel

 [] **Si vous gérez les enregistrements Office 365 de votre domaine au niveau de votre fournisseur d'hébergement DNS**, vous n'avez pas à vous soucier des étapes de cette rubrique. Votre site web reste en place et les utilisateurs peuvent toujours y accéder. 
  
 **Si Office 365 gère vos enregistrements DNS**, procédez comme suit pour router le trafic vers un site web public existant hébergé à l'extérieur d'Office 365, après avoir ajouté votre domaine à Office 365 : 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Mettre à jour les enregistrements DNS dans le centre d’administration Microsoft 365
1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .

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
  
[Mettez à jour les enregistrements de serveur de noms de votre domaine](https://support.office.com/article/a46bec33-2c78-4f45-a96c-b64b2a5bae22.aspx) pour qu'ils pointent vers Office 365. 
  
Quand les enregistrements de serveur de noms ont été mis à jour de façon à pointer vers Office 365, votre domaine est configuré. Les messages électroniques sont acheminés vers Office 365 et le trafic vers l'adresse de votre site web continue d'être acheminé vers votre fournisseur d'hébergement actuel.
 
