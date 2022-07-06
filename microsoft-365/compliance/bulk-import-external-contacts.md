---
title: Importer en bloc des contacts externes dans Exchange Online
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 6/29/2018
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOP150
ms.assetid: bed936bc-0969-4a6d-a7a5-66305c14e958
ms.custom: admindeeplinkEXCHANGE
description: Découvrez comment les administrateurs peuvent utiliser Exchange Online PowerShell et un fichier CSV pour importer en bloc des contacts externes dans la liste d’adresses globale.
ms.openlocfilehash: 40e8c44a45e8d8d0c416f3f00df57e24504a4e70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633804"
---
# <a name="bulk-import-external-contacts-to-exchange-online"></a>Importer en bloc des contacts externes dans Exchange Online

**Cet article s’applique aux administrateurs. Essayez-vous d’importer des contacts dans votre propre boîte aux lettres ? Voir [Importer des contacts dans Outlook](https://support.office.com/article/bb796340-b58a-46c1-90c7-b549b8f3c5f8)**
   
Votre entreprise dispose-t-elle d’un grand nombre de contacts professionnels que vous souhaitez inclure dans le carnet d’adresses partagé (également appelé liste d’adresses globale) dans Exchange Online ? Voulez-vous ajouter des contacts externes en tant que membres de groupes de distribution, comme vous le pouvez avec les utilisateurs au sein de votre entreprise ? Si c’est le cas, vous pouvez utiliser Exchange Online PowerShell et un fichier CSV (valeur séparée par des virgules) pour importer en bloc des contacts externes dans Exchange Online. Il s’agit d’un processus en trois étapes :
  
[Étape 1 : Créer un fichier CSV qui contient des informations sur les contacts externes](#step-1-create-a-csv-file-that-contains-information-about-the-external-contacts)

[Étape 2 : Créer les contacts externes avec PowerShell](#step-2-create-the-external-contacts-with-powershell) 

[Étape 3 : Ajouter des informations aux propriétés des contacts externes](#step-3-add-information-to-the-properties-of-the-external-contacts)

Une fois que vous avez effectué ces étapes pour importer des contacts, vous pouvez effectuer ces tâches supplémentaires :
  
- [Ajouter d’autres contacts externes](#add-more-external-contacts)
  
- [Masquer les contacts externes du carnet d’adresses partagé](#hide-external-contacts-from-the-shared-address-book)
  
## <a name="step-1-create-a-csv-file-that-contains-information-about-the-external-contacts"></a>Étape 1 : Créer un fichier CSV qui contient des informations sur les contacts externes

La première étape consiste à créer un fichier CSV qui contient des informations sur chaque contact externe que vous souhaitez importer dans Exchange Online. 
  
1. Copiez le texte suivant dans un fichier texte dans le Bloc-notes et enregistrez-le sur votre bureau en tant que fichier CSV à l’aide d’un suffixe de nom de fichier de .csv ; par exemple, ExternalContacts.csv.
    
    > [!TIP]
    > Si votre langue contient des caractères spéciaux (tels que **å**, **ä** et **ö** en suédois), enregistrez le fichier CSV avec l’encodage UTF-8 ou d’autres encodages Unicode lorsque vous enregistrez le fichier dans le Bloc-notes. 
  
    ```text
    ExternalEmailAddress,Name,FirstName,LastName,StreetAddress,City,StateorProvince,PostalCode,Phone,MobilePhone,Pager,HomePhone,Company,Title,OtherTelephone,Department,CountryOrRegion,Fax,Initials,Notes,Office,Manager
    danp@fabrikam.com,Dan Park,Dan,Park,1234 23rd Ave,Golden,CO,80215,206-111-1234,303-900-1234,555-1212,123-456-7890,Fabrikam,Shipping clerk,555-5555,Shipping,US,123-4567,R.,Good worker,31/1663,Dan Park
    pilar@contoso.com,Pilar Pinilla,Pilar,Pinilla,1234 Main St.,Seattle,WA,98017,206-555-0100,206-555-0101,206-555-0102,206-555-1234,Contoso,HR Manager,206-555-0104,Executive,US,206-555-0105,P.,Technical decision maker,31/1000,Dan Park
    ```

    La première ligne, ou ligne d’en-tête, du fichier CSV répertorie les propriétés des contacts qui peuvent être utilisés lorsque vous les importez dans Exchange Online. Chaque nom de propriété est séparé par une virgule. Chaque ligne sous la ligne d’en-tête représente les valeurs de propriété pour l’importation d’un seul contact externe. 
    
    > [!NOTE]
    > Ce texte inclut des exemples de données que vous pouvez supprimer. Mais ne supprimez pas ou ne modifiez pas la première ligne (en-tête). Il contient toutes les propriétés des contacts externes. 
  
2. Ouvrez le fichier CSV dans Microsoft Excel pour modifier le fichier CSV, car il est beaucoup plus facile d’utiliser Excel pour modifier le fichier CSV.
    
3. Créez une ligne pour chaque contact que vous souhaitez importer dans Exchange Online. Remplissez autant de cellules que possible. Ces informations seront affichées dans le carnet d’adresses partagé pour chaque contact. 
    
    > [!IMPORTANT]
    >  Les propriétés suivantes (qui sont les quatre premiers éléments de la ligne d’en-tête) sont requises pour créer un contact externe et doivent être renseignées dans le fichier CSV : **ExternalEmailAddress**, **Name**, **FirstName**, **LastName**. La commande PowerShell que vous exécutez à l’étape 2 utilise les valeurs de ces propriétés pour créer les contacts. 

## <a name="step-2-create-the-external-contacts-with-powershell"></a>Étape 2 : Créer les contacts externes avec PowerShell

L’étape suivante consiste à utiliser le fichier CSV que vous avez créé à l’étape 1 et PowerShell pour importer en bloc les contacts externes répertoriés dans le fichier CSV pour Exchange Online. 
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Veillez à utiliser le nom d’utilisateur et le mot de passe de votre compte d’administrateur général lorsque vous vous connectez à Exchange Online PowerShell. 
    
2. Après avoir connecté PowerShell à Exchange Online, accédez au dossier de bureau dans lequel vous avez enregistré le fichier CSV à l’étape 1, par exemple `C:\Users\Administrator\desktop`.
    
3. Exécutez la commande suivante pour créer les contacts externes :

    ```powershell
    Import-Csv .\ExternalContacts.csv|%{New-MailContact -Name $_.Name -DisplayName $_.Name -ExternalEmailAddress $_.ExternalEmailAddress -FirstName $_.FirstName -LastName $_.LastName}
    ```

    La création des nouveaux contacts peut prendre un certain temps, selon le nombre que vous importez. Une fois l’exécution de la commande terminée, PowerShell affiche la liste des nouveaux contacts qui ont été créés. 
    
4. Pour afficher les nouveaux contacts externes, accédez au Centre d’administration Exchange ,puis cliquez sur **Contacts des destinataires**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2182970" target="_blank"></a> 
    
    > [!TIP]
    > Pour obtenir des instructions sur la connexion à la CAE, consultez [le Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center). 
  
5. Si nécessaire, cliquez sur **Actualiser** pour mettre à jour la liste et voir les contacts externes qui ont été importés. 
    
    Les contacts importés apparaissent dans le carnet d’adresses partagé dans Outlook et Outlook sur le web.
    
    > [!NOTE]
    > Vous pouvez également afficher les contacts dans le Centre d'administration Microsoft 365 en accédant à **Contacts** \> **utilisateurs**. 

## <a name="step-3-add-information-to-the-properties-of-the-external-contacts"></a>Étape 3 : Ajouter des informations aux propriétés des contacts externes

Après avoir exécuté la commande à l’étape 2, les contacts externes sont créés, mais ils ne contiennent aucune des informations de contact ou d’organisation, qui sont les informations de la plupart des cellules du fichier CSV. Cela est dû au fait que lorsque vous créez des contacts externes, seules les propriétés requises sont remplies. Ne vous inquiétez pas si vous n’avez pas toutes les informations renseignées dans le fichier CSV. S’il n’est pas là, il n’est pas ajouté.
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Accédez au dossier de bureau dans lequel vous avez enregistré le fichier CSV à l’étape 1 ; par exemple, `C:\Users\Administrator\desktop`.
    
3. Exécutez les deux commandes suivantes pour ajouter les autres propriétés du fichier CSV aux contacts externes que vous avez créés à l’étape 2.
    
    ```powershell
    $Contacts = Import-CSV .\ExternalContacts.csv
  
    ```

    ```powershell
    $contacts | ForEach {Set-Contact $_.Name -StreetAddress $_.StreetAddress -City $_.City -StateorProvince $_.StateorProvince -PostalCode $_.PostalCode -Phone $_.Phone -MobilePhone $_.MobilePhone -Pager $_.Pager -HomePhone $_.HomePhone -Company $_.Company -Title $_.Title -OtherTelephone $_.OtherTelephone -Department $_.Department -Fax $_.Fax -Initials $_.Initials -Notes  $_.Notes -Office $_.Office -Manager $_.Manager}
    ```

    > [!NOTE]
    > Le paramètre  _Manager_ peut être problématique. Si la cellule est vide dans le fichier CSV, vous obtenez une erreur et aucune des informations de propriété n’est ajoutée au contact. Si vous n’avez pas besoin de spécifier de gestionnaire, supprimez  ` -Manager $_.Manager ` simplement de la commande PowerShell précédente. 
  
    Là encore, la mise à jour des contacts peut prendre un certain temps, selon le nombre que vous avez importé à l’étape 1. 
    
4. Pour vérifier que les propriétés ont été ajoutées aux contacts : 
    
1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, accédez à **Contacts des** \> **destinataires**.
    
2. Cliquez sur un contact, puis sur **l’icône Modifier**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) pour afficher les propriétés du contact. 
    
Voilà ! Les utilisateurs peuvent voir les contacts et les informations supplémentaires dans le carnet d’adresses Outlook et Outlook sur le web.
  
## <a name="add-more-external-contacts"></a>Ajouter d’autres contacts externes

Vous pouvez répéter les étapes 1 à 3 pour ajouter de nouveaux contacts externes dans Exchange Online. Vous ou les utilisateurs de votre entreprise pouvez simplement ajouter une nouvelle ligne dans le fichier CSV pour le nouveau contact. Vous pouvez ensuite exécuter les commandes PowerShell à partir des étapes 2 et 3 pour créer et ajouter des informations aux nouveaux contacts.
  
> [!NOTE]
> Lorsque vous exécutez la commande pour créer de nouveaux contacts, vous pouvez recevoir une erreur indiquant que les contacts créés précédemment existent déjà. Tout nouveau contact ajouté au fichier CSV est toutefois créé. 
  
## <a name="hide-external-contacts-from-the-shared-address-book"></a>Masquer les contacts externes du carnet d’adresses partagé>

Certaines entreprises peuvent utiliser des contacts externes uniquement pour pouvoir être ajoutées en tant que membres de groupes de distribution. Dans ce scénario, ils peuvent vouloir masquer les contacts externes du carnet d’adresses partagé. Voici comment procéder :
  
1.  Connectez PowerShell à votre organisation Exchange Online. Pour obtenir des instructions, consultez [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
    
2. Pour masquer un seul contact externe, exécutez la commande suivante.
    
    ```powershell
    Set-MailContact <external contact> -HiddenFromAddressListsEnabled $true 
    ```

    Par exemple, pour masquer Pilar Pinilla du carnet d’adresses partagé, exécutez la commande suivante :

    ```powershell
    Set-MailContact "Pilar Pinilla" -HiddenFromAddressListsEnabled $true
    ```

3. Pour masquer tous les contacts externes du carnet d’adresses partagé, exécutez la commande suivante :

    ```powershell
    Get-Contact -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'MailContact')} | Set-MailContact -HiddenFromAddressListsEnabled $true  
    ```

Une fois que vous les avez masqués, les contacts externes ne sont pas affichés dans le carnet d’adresses partagé, mais vous pouvez toujours les ajouter en tant que membres d’un groupe de distribution.