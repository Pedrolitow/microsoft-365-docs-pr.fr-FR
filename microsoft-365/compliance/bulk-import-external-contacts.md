---
title: Importation en bloc de contacts externes dans Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
description: Découvrez comment les administrateurs peuvent utiliser Exchange Online PowerShell et un fichier CSV pour importer en bloc des contacts externes dans la liste d’adresses globale.
ms.openlocfilehash: 4d0b1a826583a032fd27c216367e99a6b7f8b371
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43636342"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Importation en bloc de contacts externes dans Exchange Online

**Cet article est réservé aux administrateurs. Essayez-vous d’importer des contacts dans votre propre boîte aux lettres ? Voir [Importer des contacts dans Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Votre entreprise a-t-elle de nombreux contacts professionnels existants que vous souhaitez inclure dans le carnet d’adresses partagé (également appelé liste d’adresses globale) dans Exchange Online ? Souhaitez-vous ajouter des contacts externes en tant que membres de groupes de distribution, comme vous le pouvez avec des utilisateurs au sein de votre entreprise ? Si c’est le cas, vous pouvez utiliser Exchange Online PowerShell et un fichier CSV (valeurs séparées par des virgules) pour importer en bloc des contacts externes dans Exchange Online. Il s’agit d’un processus en trois étapes :
  
[Étape 1 : Créer un fichier CSV qui contient des informations sur les contacts externes](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[Étape 2 : Créer les contacts externes avec PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[Étape 3 : Ajouter des informations aux propriétés des contacts externes](#step-3-add-information-to-the-properties-of-the-external-contacts)

Une fois que vous avez effectué ces étapes pour importer des contacts, vous pouvez effectuer les tâches supplémentaires suivantes :
  
- [Ajouter des contacts externes](#add-more-external-contacts)
  
- [Masquer les contacts externes dans le carnet d’adresses partagé](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>Étape 1 : Créer un fichier CSV qui contient des informations sur les contacts externes

La première étape consiste à créer un fichier CSV qui contient des informations sur chaque contact externe que vous souhaitez importer dans Exchange Online. 
  
1. Copiez le texte suivant dans un fichier texte dans le Bloc-notes et enregistrez-le sur votre bureau en tant que fichier CSV à l’aide du suffixe de nom de fichier .csv . par exemple, ExternalContacts.csv.
    
    > [!TIP]
    > Si votre langue contient des caractères spéciaux (par exemple, **å**, **ä** et **ö** en suédois), enregistrez le fichier CSV avec UTF-8 ou un autre codage Unicode lorsque vous enregistrez le fichier dans le Bloc-notes. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    La première ligne, ou ligne d’en-tête, du fichier CSV répertorie les propriétés des contacts qui peuvent être utilisées lorsque vous les importez dans Exchange Online. Chaque nom de propriété est séparé par une virgule. Chaque ligne sous la ligne d’en-tête représente les valeurs de propriété pour l’importation d’un contact externe unique. 
    
    > [!NOTE]
    > Ce texte inclut des exemples de données que vous pouvez supprimer. Mais ne supprimez pas ou ne modifiez pas la première ligne (en-tête). Il contient toutes les propriétés des contacts externes. 
  
2. Ouvrez le fichier CSV dans Microsoft Excel pour modifier le fichier CSV, car il est beaucoup plus facile d’utiliser Excel pour modifier le fichier CSV.
    
3. Créez une ligne pour chaque contact que vous souhaitez importer dans Exchange Online. Remplir autant de cellules que possible. Ces informations s’affichent dans le carnet d’adresses partagé pour chaque contact. 
    
    > [!IMPORTANT]
    >  Les propriétés suivantes (qui sont les quatre premiers éléments de la ligne d’en-tête) sont requises pour créer un contact externe et doivent être remplies dans le fichier CSV : **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. La commande PowerShell que vous exécutez à l’étape 2 utilisera les valeurs de ces propriétés pour créer les contacts. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>Étape 2 : Créer les contacts externes avec PowerShell

L’étape suivante consiste à utiliser le fichier CSV que vous avez créé à l’étape 1 et PowerShell pour importer en bloc les contacts externes répertoriés dans le fichier CSV dans Exchange Online. 
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396554). N’oubliez pas d’utiliser le nom d’utilisateur et le mot de passe de votre compte d’administrateur général lorsque vous vous connectez à Exchange Online PowerShell. 
    
2. Après avoir connecté PowerShell à Exchange Online, allez dans le dossier de bureau où vous avez enregistré le fichier CSV à l’étape 1 . par `C:\Users\Administrator\desktop` exemple.
    
3. Exécutez la commande suivante pour créer les contacts externes :

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    La création des contacts peut prendre un certain temps, en fonction du nombre que vous importez. Lorsque l’exécution de la commande est terminée, PowerShell affiche la liste des nouveaux contacts qui ont été créés. 
    
4. Pour afficher les nouveaux contacts externes, go to the Exchange admin center (EAC), and then click **Recipients** \> **Contacts**. 
    
    > [!TIP]
    > Pour obtenir des instructions sur la connexion au CENTRE d’administration Exchange, consultez le Centre [d’administration Exchange dans Exchange Online.](https://go.microsoft.com/fwlink/p/?LinkId=328197) 
  
5. Si nécessaire, cliquez sur **Actualiser** pour mettre à jour la liste et voir les contacts externes qui ont été importés. 
    
    Les contacts importés apparaissent dans le carnet d’adresses partagé dans Outlook et Outlook sur le web.
    
    > [!NOTE]
    > Vous pouvez également afficher les contacts dans le Centre d’administration Microsoft 365 en allant **à** \> **Contacts des utilisateurs.** 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>Étape 3 : Ajouter des informations aux propriétés des contacts externes

Après avoir exécuté la commande à l’étape 2, les contacts externes sont créés, mais ils ne contiennent aucune information de contact ou d’organisation, c’est-à-dire les informations de la plupart des cellules du fichier CSV. En effet, lorsque vous créez de nouveaux contacts externes, seules les propriétés requises sont remplies. Ne vous inquiétez pas si vous n’avez pas toutes les informations remplies dans le fichier CSV. S’il n’est pas là, il n’est pas ajouté.
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396554).
    
2. Go to the desktop folder where you saved the CSV file in Step 1; par exemple, `C:\Users\Administrator\desktop` .
    
3. Exécutez les deux commandes suivantes pour ajouter les autres propriétés du fichier CSV aux contacts externes que vous avez créés à l’étape 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > Le  _paramètre Manager_ peut être problématique. Si la cellule est vide dans le fichier CSV, vous obtenez une erreur et aucune information de propriété n’est ajoutée au contact. Si vous n’avez pas besoin de spécifier un responsable, supprimez simplement  ` -Manager $_.Manager ` de la commande PowerShell précédente. 
  
    Là encore, la mise à jour des contacts peut prendre un certain temps, en fonction du nombre d’importations à l’étape 1. 
    
4. Pour vérifier que les propriétés ont été ajoutées aux contacts : 
    
1. Dans le CAE, accédez à **Destinataires** \> **Contacts**.
    
2. Cliquez sur un contact, puis **cliquez** sur ![ Modifier ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) l’icône pour afficher les propriétés du contact. 
    
Voilà ! Les utilisateurs peuvent voir les contacts et les informations supplémentaires dans le carnet d’adresses Outlook et Outlook sur le web.
  
## <a name="add-more-external-contacts"></a>Ajouter des contacts externes

Vous pouvez répéter les étapes 1 à 3 pour ajouter de nouveaux contacts externes dans Exchange Online. Vous ou les utilisateurs de votre entreprise pouvez simplement ajouter une nouvelle ligne dans le fichier CSV du nouveau contact. Vous pouvez ensuite exécuter les commandes PowerShell des étapes 2 et 3 pour créer et ajouter des informations aux nouveaux contacts.
  
> [!NOTE]
> Lorsque vous exécutez la commande pour créer de nouveaux contacts, vous pouvez obtenir une erreur vous disant que les contacts qui ont été créés précédemment existent déjà. Toutefois, tout contact ajouté au fichier CSV est créé. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Masquer les contacts externes dans le carnet d’adresses partagé>

Certaines sociétés peuvent utiliser des contacts externes uniquement pour pouvoir être ajoutées en tant que membres de groupes de distribution. Dans ce scénario, il se peut qu’ils souhaitent masquer les contacts externes dans le carnet d’adresses partagé. Voici comment procéder :
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=396554).
    
2. Pour masquer un contact externe unique, exécutez la commande suivante.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Par exemple, pour masquer Pilar Pinilla dans le carnet d’adresses partagé, exécutez la commande ci-après :

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Pour masquer tous les contacts externes du carnet d’adresses partagé, exécutez la commande ci-après :

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Une fois que vous les avez cachés, les contacts externes ne sont pas affichés dans le carnet d’adresses partagé, mais vous pouvez toujours les ajouter en tant que membres d’un groupe de distribution.
