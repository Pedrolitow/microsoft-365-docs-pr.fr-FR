---
title: Ajouter un domaine à Office 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Ajoutez votre domaine à Office 365 dans le centre d’administration Microsoft 365 en ajoutant un enregistrement DNS au niveau de votre hôte DNS. L’Assistant installation vous guide tout au long du processus.
ms.openlocfilehash: a6ef611ec210bbfb2299b6d41edb7d6410d50073
ms.sourcegitcommit: 8edad75338cf74712ca1ab5d6631b9b52ff54410
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "43116013"
---
# <a name="add-a-domain-to-office-365"></a>Ajouter un domaine à Office 365

 **[Consultez les Forums aux questions sur les domaines](domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
 *Pour ajouter, modifier ou supprimer des domaines, vous **devez** être **administrateur général** d’un [plan d’entreprise ou d’entreprise](https://products.office.com/business/office). Ces modifications affectent l’ensemble du client, les *administrateurs personnalisés* ou *les utilisateurs réguliers* ne peuvent pas effectuer ces modifications.*  

 Procédez comme suit pour ajouter, configurer ou continuer à configurer un domaine. 

::: moniker range="o365-worldwide"
  
::: moniker-end

::: moniker range="o365-germany"

> [!VIDEO https://www.microsoft.com/videoplayer/embed/dda6df6d-37b0-41ff-905b-089448355a31?autoplay=false]
  
::: moniker-end

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end
::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Accédez à la page**domaines** **d’installation** > . 

3. Sélectionnez **Ajouter un domaine**.
    
4. Entrez le nom du domaine que vous souhaitez ajouter, puis cliquez sur **suivant**.
    
5. Choisissez la manière dont vous souhaitez vérifier que vous êtes propriétaire du domaine.
    
    1. Si votre domaine est inscrit sur GoDaddy ou 1&amp;1, sélectionnez **se connecter** > à l'**étape suivante** et Office 365 [définira automatiquement vos enregistrements](../get-help-with-domains/domain-connect.md).
    
    2. Vous pouvez demander à ce qu'un courrier incluant un code de vérification soit envoyé au contact enregistré pour le domaine. Si vous ne reconnaissez pas ou n’avez pas accès au courrier électronique, vous pouvez utiliser la troisième option.
    
    3. Vous pouvez utiliser un enregistrement TXT pour vérifier votre domaine. Sélectionnez-le et cliquez sur **suivant** pour obtenir des instructions sur la façon d’ajouter cet enregistrement DNS au site Web de votre registraire. La vérification peut prendre jusqu’à 30 minutes après l’ajout de l’enregistrement. 
    
6. Choisissez comment vous souhaitez appliquer les modifications DNS requises pour Office pour utiliser votre domaine.
    
    1. Sélectionnez **Ajouter les enregistrements DNS pour moi** si vous souhaitez qu’Office configure votre DNS automatiquement. 
    
  
    2. Sélectionnez **j’aurai ajouté les enregistrements DNS moi-même** si vous voulez joindre uniquement des services Office 365 spécifiques à votre domaine ou si vous souhaitez ignorer cette opération pour le moment et effectuer cette opération plus tard. **Choisissez cette option si vous savez exactement ce que vous faites.**
    
7. Si vous décidez d' *Ajouter des enregistrements DNS vous-même* , sélectionnez **suivant** et vous verrez une page contenant tous les enregistrements que vous devez ajouter à votre site Web des registres pour configurer votre domaine. 
    
  
  
    Si le portail ne reconnaît pas votre bureau d'enregistrement, vous pouvez [suivre ces instructions générales](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
    
    Consultez notre liste d’[instructions spécifiques selon l’hôte](https://support.office.com/article/ae950c9e-e8d9-4108-b0cb-449156998580) pour rechercher votre hôte et suivre les étapes d’ajout des enregistrements dont vous avez besoin. 
    
    Si vous ne connaissez pas le fournisseur d'hébergement DNS ou le bureau d'enregistrement pour votre domaine, voir [Rechercher mon bureau d'enregistrement de domaines ou mon fournisseur d'hébergement DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    Si vous souhaitez attendre plus tard, faites défiler la liste vers le bas et sélectionnez **ignorer cette étape**.
    
8. Sélectionnez **Terminer** -vous avez terminé ! 

## <a name="related-articles"></a>Articles connexes

[Foire aux questions domaines](domains-faq.md)

[Qu’est-ce qu’un domaine ?](../get-help-with-domains/what-is-a-domain.md)

[Acheter un nom de domaine dans Office 365](../get-help-with-domains/buy-a-domain-name.md)

[Configurer votre domaine (instructions spécifiques de l’hôte)](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md)

[Obtenir de l’aide sur les domaines Office 365](../get-help-with-domains/get-help-with-domains.md)
