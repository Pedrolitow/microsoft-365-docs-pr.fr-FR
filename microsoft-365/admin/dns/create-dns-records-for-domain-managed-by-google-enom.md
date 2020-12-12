---
title: Créer des enregistrements DNS lorsque votre domaine est géré par Google (eNom)
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
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 3c490fbf-7833-4e43-be34-ed0dc3cce5e3
description: Apprenez à accéder à eNom et à créer un DNS via la page Google Domains.
ms.openlocfilehash: 3294be667653c568fbbd1a911bcfab9b6ea7788b
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49656854"
---
# <a name="create-dns-records-when-your-domain-is-managed-by-google-enom"></a>Créer des enregistrements DNS lorsque votre domaine est géré par Google (eNom)

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Pour migrer vos comptes de messagerie vers Microsoft, vous devez créer un enregistrement DNS au niveau de votre bureau d’enregistrement de domaines.
  
Si vous avez acheté votre domaine par le biais de Google lors de votre inscription à votre compte **Google Apps for Work** , vos enregistrements DNS sont gérés par Google, mais enregistrés auprès de eNom. 
  
Vous pouvez accéder à eNom et créer DNS, via la page Google **Domains** . Suivez simplement les étapes décrites dans cet article. 
  
## <a name="create-the-dns-record"></a>Créer l'enregistrement DNS

1. Dans la [console d’administration Google](https://www.google.com/work/apps/business), sélectionnez **se connecter**.
    
    ![Google-Apps-Configure-1-1-0](../../media/37a6e9f6-319e-4c02-aa18-d8d06df7953d.png)
  
2. Entrez votre nom de domaine, puis sélectionnez **OK**.
    
    ![Google-Apps-Configure-1-1-1](../../media/2caf8dcb-4d40-4cfa-bc40-d634e454e699.png)
  
3. Au bas de la page, sélectionnez **autres contrôles**.
    
    ![Google-Apps-Configure-1-2-0](../../media/1518ff78-035b-423e-85a3-c16d7faa0968.png)
  
4. Sélectionnez **Domaines**.
    
    ![Google-Apps-Configure-1-2-1](../../media/c2972c06-9bca-43bd-9876-2cee63043bf1.png)
  
5. Dans la page **domaines** , sélectionnez **Ajouter/supprimer des domaines**.
    
    ![Google-Apps-Configure-1-2-2](../../media/07b8068f-9a05-40aa-a041-fc495c729a18.png)
  
6. Dans la page **domaines** , sélectionnez **paramètres DNS avancés**.
    
    > [!NOTE]
    > Si vous n'avez pas acheté un nom de domaine via Google lors de la création de votre compte **Google Apps for Work**, vous n'aurez de **Paramètres DNS avancés** sur votre page **Domaines**. Au lieu de cela, vous devez aller directement au site web de l'hôte de votre domaine pour accéder à vos paramètres DNS et effectuer cette étape ainsi que les étapes suivantes. Pour plus d’informations, consultez [la rubrique accéder aux paramètres de votre domaine G suite](https://support.google.com/a/answer/54693?hl=en) . 
  
    ![Google-Apps-eNom-configure-1-3](../../media/b244b29c-e479-40be-b380-4ffa0f74b421.png)
  
7. Sur la page **paramètres DNS avancés** , sélectionnez **se connecter à la console DNS**. Notez les informations **Nom de connexion** et **Mot de passe**. Vous en aurez besoin à l'étape suivante. 
    
    ![Google-Apps-eNom-configure-1-4](../../media/056a2767-462f-4847-acee-d01e3f773add.png)
  
8. Connectez-vous au **Gestionnaire de domaine** Google en utilisant les **Nom de connexion** et **Mot de passe** mentionnés dans la page **Paramètres DNS avancés**. 
    
    ![Google-Apps-eNom-configure-1-5](../../media/08b74652-8cdb-4560-a5fd-0899f86deee8.png)
  
9. Sur la **page _domain_name_*_, dans la section _ enregistrements de l'* hôte** , sélectionnez **modifier**.
    
    ![Google-Apps-eNom-configure-1-6](../../media/d54fec18-b9d1-4796-8397-0393c964eade.png)
  
10. Dans la section **Host Records (enregistrements d’hôte** ), sélectionnez **Add New (Ajouter nouveau**).
    
    ![Google-Apps-eNom-configure-1-7](../../media/3562806a-4328-4e60-a717-0566841204cf.png)
  
11. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    |**HOST (HÔTE)**|**TXT VALUE**|**TYPE D’ENREGISTREMENT**|
    |:-----|:-----|:-----|
    |@  <br/> ||TXT  <br/> |

    > [!NOTE]
    > This is an example. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau. 
  
    [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)
  
12. Sélectionnez **Enregistrer**.
    
    ![Google-Apps-eNom-configure-1-9](../../media/7a6f7b45-8f79-487b-afe4-05949c2c04e8.png)
  
13. Sélectionnez **enregistrer les modifications**.
    
    ![Google-Apps-Configure-1-11](../../media/7f321236-33fb-4a7d-9d03-26605e9e558c.png)
  
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
