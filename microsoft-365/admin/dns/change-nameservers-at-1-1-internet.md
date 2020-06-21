---
title: Modifier les serveurs de noms pour configurer Microsoft avec 1&1 IONOS
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
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 31efc571-c8b9-46fb-b42d-203c2fb25289
description: Découvrez comment configurer Office 365 géré par 21Vianet pour gérer vos enregistrements DNS, quand 1&1 Internet est le fournisseur d’hébergement DNS.
ms.openlocfilehash: 79870d534e7d825fd59dbbbec54c796227f5faf1
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780372"
---
# <a name="change-nameservers-to-set-up-microsoft-365-with-11-ionos"></a>Modifier les serveurs de noms pour configurer Microsoft 365 avec 1&1 IONOS

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
Suivez ces instructions si vous voulez que Microsoft 365 gère vos enregistrements DNS Microsoft 365. (Si vous préférez, vous pouvez [gérer tous vos enregistrements DNS Microsoft 365 à 1&1 Ionos](create-dns-records-at-1-1-internet.md).) 
  

    
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification


Before you use your domain with Microsoft 365, we have to make sure that you own it. Your ability to log in to your account at your domain registrar and create the DNS record proves to Microsoft 365 that you own the domain.
  
> [!NOTE]
> This record is used only to verify that you own your domain; it doesn't affect anything else. You can delete it later, if you like. 
  
Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 0:42)](https://support.microsoft.com/office/0ef1b3b5-d27a-4004-8ca1-fbe0453a0ea3).
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS via [ce lien](https://account.1and1.com/?redirect_url=https%3A%2F%2Fmy.1and1.com%2F). You'll be prompted to log in. 
    
2. Sous **Mes domaines**, sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaines** , recherchez le domaine que vous souhaitez mettre à jour ; Ensuite, sélectionnez le contrôle de **volet** ( **v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **txt and SRV Records (enregistrements TXT** ), sélectionnez **Add record (ajouter un enregistrement**).
    
    (You may have to scroll down.) 
    
6. In the **Add Record** area, in the boxes for the new record, type or copy and paste the values from the following table. 
    
||||
|:-----|:-----|:-----|
|**Type** <br/> |**Prefix (Préfixe)** <br/> |**Name Value (Valeur de nom)** <br/> |
|TXT  <br/> |(Leave this field empty.)  <br/> |MS=ms *XXXXXXXX* <br/> **Remarque**: Voici un exemple. Utilisez votre valeur **Adresse de destination ou de pointage** spécifique ici, à partir du tableau dans Microsoft 365. [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) <br/> |

   
7. Sélectionnez **Enregistrer**, puis **Enregistrer** à nouveau. 
    
8. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
9. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Microsoft 365 et demandez à Microsoft 365 de rechercher l’enregistrement.
  
Lorsque Microsoft 365 trouve l’enregistrement TXT approprié, votre domaine est vérifié.
  
1. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
2. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
3. Dans la page **Configuration**, sélectionnez **Démarrer la configuration**.
    
4. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messagerie ou d’autres problèmes après avoir ajouté des enregistrements DNS, consultez [la rubrique Rechercher et corriger les problèmes après avoir ajouté votre domaine ou des enregistrements DNS dans Microsoft 365](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="change-your-domains-nameserver-ns-records"></a>Modifier les enregistrements de serveur de noms (NS) de votre domaine

Pour terminer la configuration de votre domaine avec Microsoft 365, vous devez modifier les enregistrements de serveur de noms de votre domaine au niveau de votre bureau d’enregistrement de domaines afin de pointer vers les serveurs de noms principaux et secondaires Microsoft 365. Cela permet de configurer Microsoft 365 afin de mettre à jour les enregistrements DNS du domaine pour vous. Pour finaliser la configuration, nous ajouterons tous les enregistrements de façon à ce que vous puissiez utiliser la messagerie, Skype Entreprise Online et votre site web public avec votre domaine.
  
> [!CAUTION]
> Lorsque vous modifiez les enregistrements de serveur de noms de votre domaine pour qu’ils pointent vers les serveurs de noms Microsoft 365, tous les services actuellement associés à votre domaine sont affectés. Par exemple, tous les messages électroniques envoyés à votre domaine (par exemple, rob@ *your_domain* . com) débuteront à Microsoft 365 une fois cette modification apportée. 
  
Vous êtes prêt à modifier vos enregistrements NS de sorte que Microsoft 365 puisse configurer votre domaine ? Suivez les étapes décrites ci-dessous ou [regardez la vidéo (commencez la lecture à 2:47)](https://support.microsoft.com/office/0ef1b3b5-d27a-4004-8ca1-fbe0453a0ea3).
  
> [!IMPORTANT]
>  La procédure suivante montre comment supprimer tous les autres serveurs de noms indésirables de la liste, et également comment ajouter les serveurs de noms corrects s’ils ne sont pas déjà répertoriés. > lorsque vous avez effectué les étapes de cette section, les seuls serveurs de noms qui doivent être répertoriés sont les quatre suivants : > ns1.bdm.microsoftonline.com > ns2.bdm.microsoftonline.com > ns3.bdm.microsoftonline.com > ns4.bdm.microsoftonline.com 
  
1. Pour commencer, accédez à la page de vos domaines à l’adresse 1&1 IONOS à l’aide de [ce lien](https://account.1and1.com/?redirect_url=https%3A%2F%2Fmy.1and1.com%2F). You'll be prompted to log in. 
    
2. Sous **Mes domaines**, sélectionnez **gérer les domaines**.
    
3. Sur la page **Centre de domaine** , recherchez le domaine que vous souhaitez mettre à jour, puis sélectionnez le contrôle de **volet** ( **v**) pour ce domaine.
    
4. Dans la zone **paramètres du domaine** , sélectionnez Modifier les **paramètres DNS**.
    
5. Dans la section **Name Server Settings (Paramètres du serveur de noms)**, sélectionnez **Other name servers (Autres serveurs de noms)**.
    
    (Vous devrez peut-être faire défiler la page vers le bas.)
    
6. Suivez l'une des procédures suivantes en fonction du scénario qui s'applique à votre cas dans la page qui s'affiche :
    
  - Si **AUCUN** serveur de noms n'est encore répertorié, [Si AUCUN serveur de noms n'est encore répertorié](#if-there-are-no-nameservers-already-listed).
    
  - Si **DES** serveurs de noms sont déjà répertoriés, [Si DES serveurs de noms sont déjà répertoriés](#if-there-are-nameservers-already-listed).
    
### <a name="if-there-are-no-nameservers-already-listed"></a>Si AUCUN serveur de noms n'est encore répertorié

1. Dans la zone **Name server 1 (Serveur de noms 1)**, tapez ou copiez-collez la valeur du tableau suivant. 
    
|||
|:-----|:-----|
|**Name server 1 (Serveur de noms 1)** <br/> |ns1.bdm.microsoftonline.com  <br/> |
   
   ![Saisie d’une valeur dans la zone Nom du serveur 1](../../media/34509935-461f-427f-9796-c3cf840bd9be.png)
  
2. Dans le menu déroulant **Additional name servers (Autres serveurs de noms)**, sélectionnez **My secondary name servers (Mes serveurs de noms secondaires)**.
    
    ![Choosing My secondary name servers in the list](../../media/7eb14856-86da-45c2-910c-c72312250a18.png)
  
3. Dans les zones **Serveur de noms (2, 3 et 4)**, tapez ou copiez-collez les valeurs du tableau suivant. 
    
|||
|:-----|:-----|
|**Name server 2 (Serveur de noms 2)** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 3** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 4** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
![Entrée de valeurs de serveur de noms](../../media/0f15880c-88b6-4133-8f31-62f0d98ee63f.png)
  
4. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer dans la page Paramètres du serveur de noms.](../../media/864f7927-7127-4784-b8d2-dadfea2f9dc8.png)
  
5. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
    ![Sélection de l’option Enregistrer dans la boîte de dialogue Modifier les paramètres DNS](../../media/0558e24c-17cd-428c-9ec1-5ed46481af7c.png)
  
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  
### <a name="if-there-are-nameservers-already-listed"></a>Si DES serveurs de noms sont déjà répertoriés

> [!CAUTION]
> Follow these steps  *only*  if you have existing nameservers other than the four  *correct*  nameservers. (That is, delete  *only*  any current nameservers that are  *not*  named **ns1.bdm.microsoftonline.com**, **ns2.bdm.microsoftonline.com**, **ns3.bdm.microsoftonline.com**, or **ns4.bdm.microsoftonline.com**.) 
  
1. Si d'autres serveurs de noms sont répertoriés dans les zones **Name server (Serveur de noms)**, supprimez-les en les sélectionnant et en appuyant sur la touche **Suppr** du clavier. 
    
    ![Deleting name servers](../../media/af0a68cc-b058-4925-b3b1-52dfded003c1.png)
  
2. Dans les zones **Serveur de noms (1, 2, 3 et 4)**, tapez ou copiez-collez les valeurs du tableau suivant. 
    
|||
|:-----|:-----|
|**Name server 1 (Serveur de noms 1)** <br/> |ns1.bdm.microsoftonline.com  <br/> |
|**Name server 2 (Serveur de noms 2)** <br/> |ns2.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 3** <br/> |ns3.bdm.microsoftonline.com  <br/> |
|**Serveur de noms 4** <br/> |ns4.bdm.microsoftonline.com  <br/> |
   
   ![Entrée de valeurs de serveur de noms](../../media/52826bd1-0596-4103-a728-d5d28b9610d2.png)
  
3. Sélectionnez **Enregistrer**.
    
    ![Sélectionnez Enregistrer dans la page Paramètres du serveur de noms.](../../media/cd10e4fb-b7fa-480f-855b-a443f2705cf2.png)
  
4. Dans la boîte de dialogue **modifier les paramètres DNS** , sélectionnez **Oui**.
    
    ![Sélection de l’option Enregistrer dans la boîte de dialogue Modifier les paramètres DNS](../../media/0558e24c-17cd-428c-9ec1-5ed46481af7c.png)
  
> [!NOTE]
> Your nameserver record updates may take up to several hours to update across the Internet's DNS system. Votre messagerie Microsoft et les autres services seront tous configurés pour fonctionner avec votre domaine. 
  


