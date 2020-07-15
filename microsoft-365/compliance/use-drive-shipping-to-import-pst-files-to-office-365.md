---
title: Utiliser l’expédition de disque pour importer les fichiers PST de votre organisation
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 40829b57-793c-4d41-b171-e9270129173d
ms.custom: seo-marvel-apr2020
description: L’administrateur peut apprendre à importer des fichiers PST dans des boîtes aux lettres Microsoft 365 en copiant des fichiers PST sur un disque dur, puis en les expédiant à Microsoft.
ms.openlocfilehash: e94a59b19271af275f74a08355a017533f8ef45d
ms.sourcegitcommit: e8b9a4f18330bc09f665aa941f1286436057eb28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "45127341"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Utiliser l’expédition de disque pour importer les fichiers PST de votre organisation

**Cet article est destiné aux administrateurs. Essayez-vous d’importer des fichiers PST dans votre propre boîte aux lettres ? Voir [importer le courrier, les contacts et le calendrier à partir d’un fichier. pst Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
Utilisez le service d’importation Office 365 et encouragez la livraison à importer en bloc des fichiers PST dans des boîtes aux lettres utilisateur. L’expédition de disque consiste à copier les fichiers PST sur un lecteur de disque dur et à expédier physiquement le lecteur à Microsoft. Lorsque Microsoft reçoit votre disque dur, le personnel du centre de données copie les données du disque dur vers une zone de stockage dans le Cloud Microsoft. Ensuite, vous avez la possibilité de découper les données PST importées vers les boîtes aux lettres cibles en définissant des filtres qui contrôlent les données à importer. Une fois le travail d’importation démarré, le service d’importation importe les données PST de la zone de stockage vers les boîtes aux lettres utilisateur. L’utilisation de l’expédition de disque pour importer des fichiers PST vers des boîtes aux lettres utilisateur est une façon de migrer le courrier électronique de votre organisation vers Office 365.
  
Voici les étapes à suivre pour utiliser l’expédition de disque pour importer des fichiers PST dans des boîtes aux lettres Microsoft 365 :
  
[Étape 1 : Télécharger la clé de stockage sécurisée et l’outil d’importation PST](#step-1-download-the-secure-storage-key-and-pst-import-tool)

[Étape 2 : copier les fichiers PST sur le disque dur](#step-2-copy-the-pst-files-to-the-hard-drive)

[Étape 3 : créer le fichier de mappage d’importation PST](#step-3-create-the-pst-import-mapping-file)

[Étape 4 : Créer une tâche d’importation PST dans Office 365](#step-4-create-a-pst-import-job-in-office-365)

[Étape 5 : Expédier le disque dur à Microsoft](#step-5-ship-the-hard-drive-to-microsoft)

[Étape 6 : Filtrer les données et démarrer la tâche d’importation PST](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> Vous devez effectuer l’étape 1 une fois pour charger la clé de stockage sécurisée et l’outil d’importation. Après avoir effectué ces étapes, suivez les étapes 2 à 6 chaque fois que vous souhaitez livrer un disque dur à Microsoft. 
  
Pour consulter les questions fréquemment posées sur l’utilisation de l’expédition de disque pour importer des fichiers PST dans Office 365, consultez la rubrique [FAQ sur l’utilisation de Drive Shipping to import PST Files](faqimporting-pst-files-to-office-365.md#using-drive-shipping-to-import-pst-files). 
  
## <a name="before-you-import-pst-files"></a>Avant d’importer des fichiers PST

- Le rôle Importation/Exportation de boîtes aux lettres doit vous avoir été attribué dans Exchange Online pour pouvoir importer des fichiers PST dans des boîtes aux lettres Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation. Vous pouvez aussi créer un nouveau groupe de rôles, lui attribuer le rôle Importation/Exportation de boîtes aux lettres, puis vous ajouter en tant que membre. Pour plus d’informations, consultez les sections « Ajouter un rôle à un groupe de rôles » ou « Créer un groupe de rôles » dans [Gérer les groupes de rôles](https://go.microsoft.com/fwlink/p/?LinkId=730688).
    
    En outre, pour créer des tâches d’importation dans le Centre de sécurité et de conformité, une des conditions suivantes doit être remplie :
    
  - Vous devez avoir le rôle de destinataire de courrier dans Exchange Online. Par défaut, ce rôle est assigné aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.
    
    Ou
    
  - Vous devez être un administrateur général au sein de votre organisation.
    
    > [!TIP]
    > Envisagez de créer un nouveau groupe de rôles dans Exchange Online spécialement conçu pour importer les fichiers PST dans Office 365. Pour obtenir le niveau minimum de privilèges requis pour importer des fichiers PST, affectez les rôles d’importation/exportation de boîte aux lettres et de destinataire de courrier au nouveau groupe de rôles et ajoutez ensuite les membres. 
  
- Vous devez stocker les fichiers PST que vous souhaitez copier vers un disque dur sur un serveur de fichiers ou un dossier partagé dans votre organisation. À l’étape 2, vous exécutez l’outil Azure Import Export Tool (WAImportExport.exe) qui copie les fichiers PST stockés sur ce serveur de fichiers ou dossier partagé sur le disque dur.

- Les fichiers PST volumineux peuvent avoir un impact sur les performances du processus d’importation PST. Par conséquent, nous vous recommandons de ne pas dépasser 20 Go pour chaque fichier PST que vous copiez sur le disque dur à l’étape 2.
    
- 2,5 Seuls les disques durs à disque SSD (SSD) ou 2,5-2,5 pouces ou 3,5-x sont pris en charge pour être utilisés avec le service d’importation Office 365. Vous pouvez utiliser des disques durs jusqu'à 10 To. Pour les tâches d’importation, uniquement le premier volume de données sur le disque dur est traité. Le volume de données doit être au format NTFS. Lorsque vous copiez des données sur un disque dur, vous pouvez les attacher directement à l’aide d’un connecteur SATA II/III de 2,5 2,5 pouces ou de 3,5 pouces ou vous pouvez les attacher de façon externe à l’aide d’un adaptateur USB 2,5 externe de l’interface SATA II/2,5 ou 3,5.
    
    > [!IMPORTANT]
    > Les disques durs externes fournis avec une carte USB intégrée ne sont pas pris en charge par le Service d’importation Office 365. En outre, le disque à l’intérieur du boîtier d’un disque dur externe ne peut pas être utilisé. Veuillez ne pas envoyer de disques durs externes. 
  
- Le disque dur sur lequel vous copiez les fichiers PST doit être chiffré avec BitLocker. L’outil WAImportExport.exe exécuté à l’étape 2 vous permet de configurer BitLocker. Il génère également une clé de chiffrement BitLocker que le personnel du centre de données Microsoft utilise pour accéder au lecteur afin de charger les fichiers PST dans la zone de stockage Azure du Cloud Microsoft.
    
- La livraison de disque est possible via un contrat d’entreprise Microsoft (EA). L’expédition de disque n’est pas disponible dans le cadre d’un Contrat de Fourniture de Produits et de Services Microsoft (MPSA).
    
- Le coût d’importation des fichiers PST dans des boîtes aux lettres Microsoft 365 à l’aide de l’expédition de disque est de $2 USD par Go de données. Par exemple, si vous expédiez un disque dur qui contient 1 000 Go (1 To) de fichiers PST, cela revient à 2 000 dollars. Vous pouvez travailler en collaboration avec un partenaire qui se chargera de payer les frais d’importation. Pour plus d’informations sur la recherche d’un partenaire, consultez la page [Trouver votre partenaire ou revendeur](https://go.microsoft.com/fwlink/p/?LinkId=785197).
    
- Vous, ou votre organisation, devez également disposer d’un compte auprès de FedEx ou DHL. 
    
  - Les organisations aux États-Unis, au Brésil et en Europe doivent disposer de comptes FedEx.
    
  - Les organisations dans l’Asie de l’est, l’Asie du sud-est, le Japon, la République de Corée et l’Australie doivent disposer de comptes DHL.
    
    Microsoft utilise (et facture) ce compte pour vous renvoyer le disque dur.
    
- Le disque dur que vous livrez à Microsoft peut franchir les bordures internationales. Dans ce cas, vous devez vous assurer que le disque dur et les données qu’il contient sont importés et/ou exportés conformément à la législation applicable. Avant d’envoyer un disque dur, vérifiez auprès de vos conseillers juridiques que votre disque et vos données peuvent être légalement expédiés au centre de données Microsoft concerné. Cela permet de s’assurer qu’il parvient à Microsoft de manière opportune.
    
- Cette procédure nécessite la copie et l’enregistrement d’une clé de stockage sécurisé et d’une clé de chiffrement BitLocker. Veillez à prendre toutes les précautions nécessaires pour protéger ces clés, comme vous le feriez avec vos mots de passe ou d’autres informations de sécurité. Par exemple, vous pouvez les enregistrer dans un document Microsoft Word protégé par mot de passe ou dans un lecteur USB chiffré. Consultez la section [plus d’informations](#more-information) pour obtenir un exemple de ces clés. 
    
- Une fois que les fichiers PST sont importés dans une boîte aux lettres Microsoft 365, le paramètre de blocage de rétention de la boîte aux lettres est activé pour une durée indéterminée. Cela signifie que la stratégie de rétention attribuée à la boîte aux lettres ne sera pas traitée tant que vous n’aurez pas désactivé la conservation de rétention ou défini une date pour désactiver la conservation. Quel est le but de cette action ? Si les messages importés dans une boîte aux lettres sont anciens, ils peuvent être supprimés définitivement (purgés) parce que leur période de conservation a expiré selon les paramètres de conservation configurés pour cette boîte aux lettres. La mise de la boîte aux lettres en attente de conservation donne au propriétaire de la boîte aux lettres le temps de gérer ces nouveaux messages importés ou de modifier les paramètres de conservation de la boîte aux lettres. Consultez la section [plus d’informations](#more-information) pour obtenir des suggestions sur la gestion du blocage de rétention. 
    
- Par défaut, la taille maximale d’un message pouvant être reçu par une boîte aux lettres Microsoft 365 est de 35 Mo. En effet, la valeur par défaut de la propriété *MaxReceiveSize* pour une boîte aux lettres est définie sur 35 Mo. Toutefois, la limite de la taille maximale de réception d’un message dans Microsoft 365 est de 150 Mo. Par conséquent, si vous importez un fichier PST qui contient un élément d’une taille supérieure à 35 Mo, le service d’importation d’Office 365 modifie automatiquement la valeur de la propriété *MaxReceiveSize* sur la boîte aux lettres cible à 150 Mo. Ainsi, les messages allant jusqu’à 150 Mo sont importés dans les boîtes aux lettres d’utilisateur. 
    
    > [!TIP]
    > Pour identifier la taille de réception des messages pour une boîte aux lettres, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :  `Get-Mailbox <user mailbox> | FL MaxReceiveSize` 
  
- Vous pouvez importer des fichiers PST dans une boîte aux lettres inactive dans Office 365. Pour ce faire, vous devez spécifier le GUID de la boîte aux lettres inactive dans le paramètre `Mailbox` du fichier de mappage d’importation PST. Pour plus d’informations, voir [étape 3 : créer le fichier de mappage d’importation PST](#step-3-create-the-pst-import-mapping-file) . 
    
- Dans un déploiement hybride Exchange, vous pouvez importer des fichiers PST dans une boîte aux lettres d'archivage basé sur le cloud pour un utilisateur dont la boîte aux lettres principale est locale. Pour ce faire, procédez comme suit dans le fichier de mappage d’importation PST :
    
  - Indiquez l’adresse électronique de la boîte aux lettres locale de l'utilisateur dans le paramètre `Mailbox`. 
    
  - Spécifiez la valeur **TRUE** dans le paramètre `IsArchive`. 
    
    Pour plus d’informations, voir [étape 3 : créer le fichier de mappage d’importation PST](#step-3-create-the-pst-import-mapping-file) . 

## <a name="step-1-download-the-secure-storage-key-and-pst-import-tool"></a>Étape 1 : Télécharger la clé de stockage sécurisée et l’outil d’importation PST

La première étape consiste à télécharger la clé de stockage sécurisée et l’outil et à l’utiliser à l’étape 2 pour copier des fichiers PST sur le disque dur.
  
> [!IMPORTANT]
> Vous devez utiliser l’outil d’importation/exportation Azure version 1 (WAimportExportV1) pour importer les fichiers PST à l’aide de la méthode de livraison de disque. La version 2 de l’outil d’importation/exportation Azure n’est pas prise en charge et son utilisation entraînerait une préparation incorrecte du disque dur pour le travail d’importation. Assurez-vous de télécharger l’outil d’importation/exportation Azure à partir du centre de sécurité & conformité en suivant les procédures décrites dans cette étape. 
  
1. Accédez à [https://protection.office.com/](https://protection.office.com/) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Gouvernance de l'information ** \> **Importer** \> **Importer des fichiers PST**.
    
    > [!NOTE]
    > Comme indiqué précédemment, vous devez disposer des autorisations appropriées pour accéder à la page d' **importation** dans le centre de sécurité & conformité. 
  
3. Dans la page **Importer des fichiers PST**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.
    
4. Dans l’Assistant importation de tâche, tapez un nom pour le travail d’importation PST, puis cliquez sur **suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.
    
5. Dans la page **choisir le type de travail d’importation** , cliquez sur **expédier des disques durs vers l’un de nos emplacements physiques** , puis cliquez sur **suivant**.
    
    ![Cliquez sur expédier des disques durs vers l’un de nos emplacements physiques pour créer une tâche d’importation d’envoi de disques.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Dans la page **Importer des données**, effectuez les deux opérations suivantes : 
    
    ![Copier la clé de stockage sécurisée et télécharger l’outil d’importation/exportation Azure sur la page importer les données](../media/e22e0b48-e5ce-48e0-95bc-0490a2b3b983.png)
  
    a. À l’étape 2, cliquez sur **copier la clé de stockage sécurisée**. Une fois la clé de stockage affichée, cliquez sur **copier dans le presse-papiers** , puis collez-la dans un fichier pour pouvoir y accéder ultérieurement.
    
    b. À l’étape 3, **Téléchargez l’outil d’importation/exportation Azure** pour télécharger et installer l’outil d’importation/exportation Azure (version 1).
    
    - Dans la fenêtre contextuelle, cliquez sur **Enregistrer** \> **Enregistrer sous** pour enregistrer le fichier WaImportExportV1.zip dans un dossier de votre ordinateur local. 
    
    - Extrayez le fichier WaImportExportV1.zip.
    
7. Cliquez sur **Annuler** pour fermer l’Assistant. 
    
    Vous revenez à la page d' **importation** dans le centre de sécurité & conformité lorsque vous créez le travail d’importation à l’étape 4. 

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>Étape 2 : copier les fichiers PST sur le disque dur

Pour réaliser cette étape, vous devez utiliser l’outil WAImportExport.exe pour copier les fichiers PST sur le disque dur. Cet outil chiffre le disque dur avec BitLocker, copie les fichiers PST sur le disque dur et crée un fichier journal qui stocke des informations sur le processus de copie. Pour cela, les fichiers PST doivent se trouver sur un dossier partagé ou un serveur de fichiers dans votre organisation. Il s’agit du répertoire source mentionné dans la procédure suivante. 

 Comme indiqué précédemment, chaque fichier PST que vous copiez sur le disque dur ne doit pas dépasser 20 Go. Les fichiers PST d’une taille supérieure à 20 Go peuvent avoir un impact sur les performances du processus d’importation PST démarré à l’étape 6.
  
> [!IMPORTANT]
> Après avoir exécuté l’outil WAImportExport.exe pour la première fois pour un disque dur, vous devez utiliser une syntaxe différente les fois suivantes. Cette syntaxe est expliquée à l’étape 4 de cette procédure pour copier des fichiers PST sur le disque dur. 
  
1. Ouvrez une invite de commandes sur votre ordinateur local.
    
    > [!TIP]
    > If you run the command prompt as an administrator (by selecting "Run as administrator" when you open it) error messages will be displayed in the command prompt window. This can help you troubleshoot problems running the WAImportExport.exe tool. 
  
2. Accédez au répertoire où vous avez installé l’outil WAImportExport.exe à l’étape 1.
    
3. Exécutez la commande suivante lorsque vous utilisez l’outil WAImportExport.exe pour la première fois pour copier les fichiers PST sur un disque dur.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /sk:<Storage account key> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    Le tableau suivant décrit les paramètres et leurs valeurs requises. 
    
    |**Paramètre**|**Description**|**Exemple**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Indique le nom du fichier journal. Ce fichier est enregistré dans le dossier où se trouve l’outil WAImportExport.exe. Un fichier journal doit être créé sur chaque disque dur envoyé à Microsoft. Chaque fois que vous exécutez l’outil WAImportTool.exe pour copier des fichiers PST sur un disque dur, des informations sont ajoutées au fichier journal de ce disque.  <br/> Personnel du centre de données Microsoft utilisez les informations contenues dans le fichier journal pour associer le disque dur au travail d’importation que vous créez à l’étape 4, et pour télécharger les fichiers PST dans la zone de stockage Azure de Microsoft Cloud.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Indique la lettre de lecteur du disque dur quand celui-ci est connecté à votre ordinateur local.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Specifies the name of the copy session. A session is defined as each time you run the WAImportExport.exe tool to copy files to the hard drive. The PST files are copied to a folder named with the session name specified by this parameter.  <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Indique le répertoire source de votre organisation contenant les fichiers PST qui seront copiés pendant la session. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |Spécifie le répertoire de destination dans la zone de stockage Azure du Cloud Microsoft où les fichiers PST seront téléchargés. Vous devez utiliser la valeur `ingestiondata/` . N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> Vous pouvez également ajouter un chemin d’accès de fichier supplémentaire à la valeur de ce paramètre. Par exemple, vous pouvez utiliser le chemin d’accès au fichier du répertoire source sur le disque dur (converti au format URL), qui est spécifié dans le `/srcdir:` paramètre. Par exemple, `\\FILESERVER01\PSTs` est remplacé par `FILESERVER01/PSTs` . Dans ce cas, vous devez toujours inclure `ingestiondata` dans le chemin d’accès au fichier. Par conséquent, dans cet exemple, la valeur du `/dstdir:` paramètre serait `"ingestiondata/FILESERVER01/PSTs"` .  <br/> Ajouter un chemin d’accès supplémentaire peut être utile si plusieurs fichiers PST portent le même nom.  <br/> > [!NOTE]> si vous incluez le chemin d’accès facultatif, l’espace de noms d’un fichier PST après son chargement dans la zone de stockage Azure inclut le chemin d’accès et le nom du fichier PST ; par exemple, `FILESERVER01/PSTs/annb.pst` . Si vous n’incluez pas de chemin d’accès, l’espace de noms est uniquement le nom de fichier PST ; par exemple `annb.pst` .           | `/dstdir:"ingestiondata/"` <br/> Ou  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/sk:` <br/> |Spécifie la clé du compte de stockage obtenue à l’étape 1. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `"yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ=="` <br/> |
    | `/blobtype:` <br/> |Spécifie le type d’objets BLOB dans la zone de stockage Azure où importer les fichiers PST. Pour l’importation de fichiers PST, utilisez la valeur **BlockBlob**. Ce paramètre est obligatoire.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Ce commutateur active BitLocker pour le disque dur. Ce paramètre est obligatoire la première fois que vous exécutez l’outil WAImportExport.exe.  <br/> La clé de chiffrement BitLocker est copiée dans le fichier journal et dans le fichier journal créé si vous utilisez le `/logfile:` paramètre. Comme indiqué précédemment, le fichier journal est enregistré dans le dossier où se trouve l’outil WAImportExport.exe.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Ce paramètre facultatif indique le dossier dans lequel les fichiers journaux seront enregistrés. Si ce n’est pas spécifié, les fichiers journaux sont enregistrés dans le dossier où se trouve l’outil WAImportExport.exe. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Voici un exemple de la syntaxe de l’outil WAImportExport.exe qui reprend les valeurs réelles de chaque paramètre :
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" /sk:"yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    After you run the command, status messages are displayed that show the progress of copying the PST files to the hard drive. A final status message shows the total number of files that were successfully copied.
    
4. Exécutez cette commande chaque fois que vous exécutez l’outil WAImportExport.ext pour copier des fichiers PST sur le même disque dur.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Voici un exemple de la syntaxe pour copier ultérieurement des fichiers PST sur le même disque dur.  

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>Étape 3 : créer le fichier de mappage d’importation PST

Une fois que le personnel du centre de données Microsoft a téléchargé les fichiers PST depuis le disque dur vers la zone de stockage Azure, le service d’importation utilise les informations du fichier de mappage d’importation PST, qui est un fichier CSV, qui spécifie les boîtes aux lettres d’utilisateurs dans lesquelles les fichiers PST sont importés. Ce fichier PST est envoyé à l’étape suivante lors de la création d’une tâche d’importation PST.
  
1. [Téléchargez une copie du fichier de mappage d’importation PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. Open or save the CSV file to your local computer. The following example shows a completed PST Import mapping file (opened in NotePad). It's much easier to use Microsoft Excel to edit the CSV file.

    ```text
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,FILESERVER01/PSTs,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,FILESERVER01/PSTs,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,FILESERVER01/PSTs,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,,,,,
    ```

    La première ligne ou ligne d’en-tête du fichier CSV répertorie les paramètres qui seront utilisés par le service d’importation pour importer les fichiers PST dans les boîtes aux lettres d’utilisateur. Les noms des paramètres sont séparés par des virgules. Chaque ligne sous la ligne d’en-tête représente les valeurs des paramètres pour l’importation d’un fichier PST dans une boîte aux lettres spécifique. Vous avez besoin d’une ligne pour chaque fichier PST qui a été copié sur le disque dur. N’oubliez pas de remplacer les données d’espace réservé dans le fichier de mappage par les données réelles.

    > [!NOTE]
    > Ne modifiez en aucun cas la ligne d’en-tête, ni les paramètres SharePoint ; ils seront ignorés pendant le processus d’importation des fichiers PST. 
  
3. Utilisez les informations du tableau suivant pour remplir le fichier CSV avec les informations requises.
    
    |**Parameter**|**Description**|**Exemple**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Indique le service où les données seront importées. Pour importer des fichiers PST dans les boîtes aux lettres d’utilisateur, utilisez  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Spécifie l’emplacement du dossier dans la zone de stockage Azure dans laquelle les fichiers PST seront copiés lorsque le disque dur sera livré à Microsoft.  <br/>  Les éléments que vous ajoutez dans cette colonne dans le fichier CSV dépendent de ce que vous avez spécifié dans pour le `/dstdir:` paramètre à l’étape précédente. Si vous avez des sous-dossiers sur l’emplacement source, la valeur dans le `FilePath` paramètre doit contenir le chemin d’accès relatif pour le sous-dossier, par exemple,/Folder1/User1/.  <br/>  Si vous avez utilisé `/dstdir:"ingestiondata/"` , laissez ce paramètre vide dans le fichier CSV.  <br/>  Si vous avez inclus un chemin d’accès facultatif pour la valeur du `/dstdir:` paramètre (par exemple, `/dstdir:"ingestiondata/FILESERVER01/PSTs"` , puis utilisez ce chemin d’accès (pas « ingestiondata ») pour ce paramètre dans le fichier CSV. La valeur de ce paramètre est sensible à la casse.  <br/>  Dans tous les cas, n'incluez *pas* « ingestiondata » dans la valeur du paramètre `FilePath`. Laissez ce paramètre vide ou spécifiez uniquement le chemin d’accès facultatif.  <br/> > [!IMPORTANT]> la casse du nom de chemin d’accès du fichier doit être la même que celle spécifiée dans le `/dstdir:` paramètre de l’étape précédente. Par exemple, si vous avez utilisé `"ingestiondata/FILESERVER01/PSTs"` pour le nom du sous-dossier à l’étape précédente, mais que vous l’avez utilisé `fileserver01/psts` dans le `FilePath` fichier CSV, l’importation du fichier PST échoue. Veillez à utiliser la même casse dans les deux instances.           |(Laisser vide)  <br/> Ou  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Indique le nom du fichier PST qui sera importé dans la boîte aux lettres d’utilisateur. La valeur de ce paramètre est sensible à la casse.  <br/> > [!IMPORTANT]> le nom du fichier PST dans le fichier CSV doit être le même que celui qui a été téléchargé vers l’emplacement de stockage Azure à l’étape 2. Par exemple, si vous utilisez  `annb.pst` dans le paramètre `Name` du fichier CSV, mais que le nom du fichier PST réel est  `AnnB.pst`, l’importation de ce fichier PST échouera. Assurez-vous que le nom du fichier PST dans le fichier CSV utilise la même casse que le fichier PST réel.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |Indique l’adresse électronique de la boîte aux lettres dans laquelle le fichier PST est importé. Vous ne pouvez pas spécifier un dossier public, car le service d’importation PST ne prend pas en charge l’importation de fichiers PST dans les dossiers publics.  <br/> Pour importer un fichier PST dans une boîte aux lettres inactive, vous devez indiquer le GUID de la boîte aux lettres pour ce paramètre. Pour obtenir ce GUID, exécutez la commande PowerShell suivante dans Exchange Online :  `Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> parfois, vous pouvez avoir plusieurs boîtes aux lettres avec la même adresse de messagerie, où une boîte aux lettres est une boîte aux lettres active et l’autre est dans un état supprimé (ou inactif). Dans ce cas, vous devez spécifier le GUID de boîte aux lettres pour identifier de façon unique la boîte aux lettres dans laquelle importer le fichier PST. Pour obtenir ce GUID des boîtes aux lettres actives, exécutez la commande PowerShell suivante :  `Get-Mailbox <identity of active mailbox> | FL Guid` Pour obtenir le GUID des boîtes aux lettres supprimées (ou inactives), exécutez la commande suivante : `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid` .           | `annb@contoso.onmicrosoft.com` <br/> Ou  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Indique si le fichier PST doit être importé dans la boîte aux lettres d’archivage de l’utilisateur. Il existe deux options :  <br/> **Valeur false** Importe le fichier PST dans la boîte aux lettres principale de l’utilisateur.  <br/> **True** Importe le fichier PST dans la boîte aux lettres d’archivage de l’utilisateur. Cela implique l’[activation de la boîte aux lettres d’archivage de l’utilisateur](enable-archive-mailboxes.md). Si vous définissez ce paramètre sur `TRUE` et que la boîte aux lettres d’archivage de l’utilisateur n’est pas activée, l’importation échouera pour cet utilisateur. Si une importation échoue pour un utilisateur (car son archive n’est pas activée et que cette propriété est définie sur `TRUE`), les autres utilisateurs dans la tâche d’importation ne seront pas affectés.  <br/>  Si vous ne renseignez pas ce paramètre, le fichier PST est importé dans la boîte aux lettres principale de l’utilisateur.  <br/> **Remarque :** Pour importer un fichier PST dans une boîte aux lettres d’archivage dans le cloud pour un utilisateur dont la boîte aux lettres principale est accessible localement, indiquez `TRUE` pour ce paramètre et indiquez l’adresse de courrier de la boîte aux lettres locale de l’utilisateur pour le paramètre `Mailbox`.  <br/> | `FALSE` <br/> Ou  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Indique le dossier de la boîte aux lettres dans lequel le fichier PST est importé.  <br/>  Si vous laissez ce paramètre vide, le fichier PST sera importé dans un nouveau dossier nommé **importés** au niveau racine de la boîte aux lettres (le même niveau que le dossier boîte de réception et les autres dossiers de boîte aux lettres par défaut).  <br/>  Si vous spécifiez `/` , les éléments du fichier PST seront importés directement dans le dossier boîte de réception de l’utilisateur.  <br/>  Si vous spécifiez `/<foldername>` , les éléments du fichier PST seront importés dans un dossier nommé *\<foldername\>* . Par exemple, si vous utilisez  `/ImportedPst`, les éléments sont importés dans un dossier nommé **ImportedPst**. Ce dossier se trouve dans la boîte aux lettres de l’utilisateur au même niveau que le dossier boîte de réception.  <br/> |(Laisser vide)  <br/> Ou  <br/>  `/` <br/> Ou  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ce paramètre facultatif indique une valeur numérique que la page de codes doit utiliser pour importer des fichiers PST au format de fichier ANSI. Ce paramètre permet d’importer des fichiers PST à partir d’organisations chinoises, japonaises et coréennes, car ces langues utilisent généralement un jeux de caractères à deux octets (DBCS) pour le codage de caractères. Si ce paramètre n’est pas utilisé pour importer des fichiers PST pour les langues qui utilisent des caractères DBCS pour les noms des dossiers de boîte aux lettres, les noms des dossiers sont souvent déformés une fois qu’ils sont importés.  <br/> Pour obtenir la liste des valeurs prises en charge à utiliser pour ce paramètre, consultez [Identificateurs de page de codes](https://go.microsoft.com/fwlink/p/?LinkId=328514).  <br/> > [!NOTE]> comme indiqué précédemment, il s’agit d’un paramètre facultatif et vous n’avez pas besoin de l’inclure dans le fichier CSV. Ou vous pouvez également l’inclure et conserver la valeur vide pour une ou plusieurs lignes.           |(Laisser vide)  <br/> Ou  <br/>  `932` (il s’agit de l’identificateur de page de codes pour le japonais ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPManifestContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPSiteUrl` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>Étape 4 : Créer une tâche d’importation PST dans Office 365

L'étape suivante consiste à créer la tâche d'importation PST dans le service d'importation dans Office 365. Comme expliqué précédemment, vous devez soumettre le fichier de mappage d’importation PST que vous avez créé à l’étape 3. Une fois le travail créé, le service d’importation utilise les informations du fichier de mappage pour importer les fichiers PST dans la boîte aux lettres de l’utilisateur spécifié une fois que les fichiers PST sont copiés du disque dur vers la zone de stockage Azure et que vous créez et démarrez le travail d’importation.
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Gouvernance de l'information ** \> **Importer** \> **Importer des fichiers PST**.
    
3. Dans la page **Importer des fichiers PST**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.
    
    > [!NOTE]
    > Comme indiqué précédemment, vous devez disposer des autorisations appropriées pour accéder à la page d' **importation** dans le centre de sécurité & conformité. 
  
4. Entrez le nom de la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.
    
5. Dans la page **choisir le type de travail d’importation** , cliquez sur **expédier des disques durs vers l’un de nos emplacements physiques** , puis cliquez sur **suivant**.
    
    ![Cliquez sur expédier des disques durs vers l’un de nos emplacements physiques pour créer une tâche d’importation d’envoi de disques.](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. À l’étape 6, cliquez sur les cases à cocher **j’ai préparé les disques durs et ont accès aux fichiers journaux des lecteurs nécessaires** et **j’ai accès au fichier de mappage** , puis cliquez sur **suivant**.
    
    ![Cliquez sur les deux cases à cocher à l’étape 6](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. Dans la page **Sélectionner le fichier du lecteur** , cliquez sur **Sélectionner un fichier de lecteur**, puis accédez au dossier dans lequel se trouve l’outil WAImportExport.exe. Le fichier journal créé à l’étape 2 a été copié dans ce dossier.
    
    ![Cliquez sur Sélectionner un fichier de lecteur pour soumettre le fichier journal qui a été créé lors de l’exécution de l’outil WAImportExport.exe](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Sélectionnez le fichier journal ; par exemple, `PSTHDD1.jrn` .
    
    > [!TIP]
    > Lorsque vous avez exécuté l’outil WAImportExport.exe à l’étape 2, le nom du fichier journal a été spécifié par le `/j:` paramètre. 
  
9. Une fois le nom du fichier du lecteur affiché sous **nom du fichier**, cliquez sur **valider** pour vérifier que votre fichier de lecteur ne comporte pas d’erreurs. 
    
    ![Cliquez sur valider pour valider le fichier lecteur que vous avez sélectionné.](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Le fichier du lecteur doit être validé pour créer une tâche d’importation PST. Notez que le nom du fichier passe au vert une fois qu'il a été validé avec succès. Si la validation échoue, cliquez sur le lien **Afficher le journal**. Un rapport d’erreur de validation est ouvert, avec un message d’erreur contenant des informations sur la raison de l’échec du fichier. 
    
    > [!NOTE]
    > Vous devez ajouter et valider un fichier journal pour chaque disque dur que vous livrez à Microsoft. 
  
10. Après avoir ajouté et validé un fichier journal pour chaque disque dur que vous envoyez à Microsoft, cliquez sur **suivant**.
    
11. Cliquez sur ![ Ajouter une icône ](../media/ITPro-EAC-AddIcon.gif) **Sélectionnez mappage de fichier** pour soumettre le fichier de mappage d’importation PST que vous avez créé à l’étape 3. 
    
    ![Cliquez sur Sélectionner le fichier de mappage pour envoyer le fichier CSV que vous avez créé pour la tâche d’importation.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. Lorsque le nom du fichier CSV apparaît dans la liste, **Nom de fichier de mappage**, cliquez sur **Valider** pour vérifier que votre fichier CSV ne contient pas d’erreurs. 
    
    ![Cliquez sur Valider pour rechercher les erreurs dans le fichier CSV.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Le fichier CSV doit être validé avec succès pour créer une tâche d'importation PST. Notez que le nom du fichier passe au vert une fois qu'il a été validé avec succès. Si la validation échoue, cliquez sur le lien **Afficher le journal**. Un rapport d'erreur de validation est ouvert, avec un message d'erreur pour chaque ligne du fichier qui a échoué. 
    
13. Une fois le fichier de mappage PST correctement validé, cliquez sur **suivant**.
    
14. Sur la page **fournir les informations de contact** , entrez vos informations de contact dans les zones appropriées. 
    
    L’adresse de l’emplacement de Microsoft vers lequel vous livrez vos disques durs est affichée. Cette adresse est générée automatiquement en fonction de votre emplacement de centre de Microsoft. Copiez cette adresse dans un fichier ou effectuez une capture d’écran.
    
15. Lisez le document conditions générales, cliquez sur la case à cocher, puis cliquez sur **Enregistrer** pour soumettre la tâche d’importation. 
    
    Une fois la tâche d’importation créée, une page d’État s’affiche pour vous expliquer les étapes suivantes du processus de livraison des lecteurs.
    
16. Sur la page **Importer les fichiers PST** , cliquez sur Actualiser ![ l’icône ](../media/O365-MDM-Policy-RefreshIcon.gif) **Actualiser** pour afficher le travail d’importation de nouveau lecteur de disque dans la liste des travaux d’importation. Le statut est défini sur en **attente du numéro de suivi**. Vous pouvez également cliquer sur le travail d’importation pour afficher la page de menu volant d’État, qui contient des informations plus détaillées sur la tâche d’importation.
 
## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>Étape 5 : Expédier le disque dur à Microsoft

L’étape suivante consiste à expédier le disque dur à Microsoft, puis à fournir le numéro de suivi pour les informations de livraison et de retour pour le travail d’expédition de disque. Une fois que Microsoft a reçu le lecteur, il faut entre 7 et 10 jours ouvrés pour que le personnel du centre de données télécharge vos fichiers PST vers la zone de stockage Azure de votre organisation.
  
> [!NOTE]
> Si vous ne fournissez pas les informations de numéro de suivi et d’expédition de retour dans les 14 jours suivant la création de la tâche d’importation, la tâche d’importation expirera. Dans ce cas, vous devrez créer une tâche d’importation de lecteur de disque (voir [étape 4 : créer une tâche d’importation PST dans Office 365](#step-4-create-a-pst-import-job-in-office-365)) et soumettre de nouveau le fichier de lecteur et le fichier de mappage d’importation PST. 
  
### <a name="ship-the-hard-drive"></a>Envoyer le disque dur

Gardez ces informations à l’esprit quand vous envoyez des disques durs à Microsoft :
  
- Ne fournissez pas l’adaptateur SATA-USB ; il vous suffit d’expédier le disque dur.
    
- Emballez le disque dur correctement (par exemple, utilisez un sac anti-statique ou du papier bulle).
    
- Prenez le transporteur de votre choix pour envoyer le disque dur à Microsoft.
    
- Envoyez le disque dur à l’adresse du site Microsoft affichée lors de la création de la tâche d’importation à l’étape 4. N’oubliez pas d’indiquer « Service d’importation Office 365 » dans l’adresse d’expédition.
    
- After you ship the hard drive, be sure to write down the name of the delivery carrier and the tracking number. You'll provide these in the next step.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Entrer le numéro de suivi et d’autres informations d’expédition

Une fois le disque dur envoyé à Microsoft, effectuez les étapes suivantes sur la page du service d’importation.
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Dans le volet de gauche, cliquez sur **gouvernance des informations > importer > fichiers PST d’importation**.
    
3. Sur la page **Importer les fichiers PST** , cliquez sur le travail pour le livraison de disque pour lequel vous souhaitez entrer le numéro de suivi. 
    
4. Sur la page flyout d’État, cliquez sur **entrer le numéro de suivi**.
    
5. Fournissez les informations suivantes :
    
1. **Opérateur de remise** Tapez le nom de l’opérateur de remise que vous avez utilisé pour envoyer le disque dur à Microsoft. 
    
2. **Numéro de suivi** Tapez le numéro de suivi de la livraison du disque dur. 
    
3. **Numéro de compte** de l’opérateur de retour Tapez le numéro de compte de votre organisation pour le transporteur qui apparaît sous l' **opérateur de retour**. Microsoft utilise (et facture) ce compte pour vous remettre votre disque dur. Les organisations aux États-Unis et en Europe doivent disposer d’un compte auprès de FedEx. Les organisations en Asie et dans le reste du monde doivent posséder un compte DHL.
    
6. Cliquez sur **Enregistrer** pour enregistrer ces informations pour la tâche d’importation. 
    
    Sur la page **Importer les fichiers PST** , cliquez sur Actualiser ![ l’icône ](../media/O365-MDM-Policy-RefreshIcon.gif) **Actualiser** pour mettre à jour les informations de votre tâche d’importation d’envoi de lecteurs. Notez que le statut est désormais défini sur **Disques en transit**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Étape 6 : Filtrer les données et démarrer la tâche d’importation PST

Une fois que Microsoft a reçu votre disque dur, l’état de la tâche d’importation sur la page **importer des fichiers PST** se transforme en **lecteurs reçus**. Personnel du centre de données Utilisez les informations contenues dans le fichier journal pour charger vos fichiers PST dans la zone de stockage Azure de votre organisation. À ce stade, l’État devient **importer en cours**. Comme indiqué précédemment, il faudra entre 7 et 10 jours ouvrables après la réception de votre disque dur pour charger les fichiers PST.
  
Une fois les fichiers PST téléchargés vers Azure, l’État est modifié **en analyse en cours**. Cela indique que Microsoft 365 analyse les données des fichiers PST (de manière sûre et sécurisée) pour identifier l’âge des éléments et les différents types de messages inclus dans les fichiers PST. Lorsque l’analyse est terminée et que les données sont prêtes à être importées, l’état de la tâche d’importation devient **analyse terminée**. À ce stade, vous avez la possibilité d’importer toutes les données contenues dans les fichiers PST ou vous pouvez réduire les données importées en définissant des filtres qui contrôlent les données à importer.
  
1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Dans le volet de gauche, cliquez sur **information gouvernance** \> **Import** \> **Import PST Files**.
    
3. Dans la page **importer des fichiers PST** , cliquez sur **prêt pour l’importation vers Office 365** pour le travail d’importation que vous avez créé à l’étape 4. 
    
    ![Cliquez sur Prêt à importer dans Microsoft 365 à côté de la tâche d’importation que vous avez créée.](../media/5760aac3-300b-4e31-b894-253c42a4b82b.png)
  
    Une page volante s’affiche avec des informations sur les fichiers PST et d’autres informations sur la tâche d’importation.
    
4. Cliquez sur **importer vers Office 365**.
    
5. La page **Filtrez vos données** s’affiche. Elle contient les aperçus des données résultant de l'analyse des fichiers PST effectuée par Office 365, y compris des informations sur l'âge des données. À ce stade, vous avez la possibilité de filtrer les données qui seront importées ou d’importer toutes les données telles quelles. 
    
    ![Vous pouvez découper les données dans les fichiers PST ou les importer](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Effectuez l’une des opérations suivantes :
    
    a. Pour découper les données que vous importez, cliquez sur **Oui, je souhaite les filtrer avant l’importation**.
    
    Pour obtenir des instructions détaillées sur le filtrage des données dans les fichiers PST et le démarrage de la tâche d’importation, consultez la rubrique [Filtrer les données lors de l’importation de fichiers PST dans Office 365](filter-data-when-importing-pst-files.md).
    
    Ou
    
    b. Pour importer toutes les données des fichiers PST, cliquez sur **Non, je souhaite tout importer,** puis cliquez sur **Suivant**.
    
7. Si vous avez choisi d’importer toutes les données, cliquez sur **Importer les données** pour démarrer la tâche d’importation. 
    
    L’état de la tâche d’importation est affiché dans la page **Importer les fichiers PST** . Cliquer sur ![Actualiser l’icône](../media/O365-MDM-Policy-RefreshIcon.gif)**Actualiser** pour mettre à jour les informations d’état affichées dans la colonne **État**. Cliquez sur la tâche d’importation pour afficher la page de menu volant d’état qui affiche des informations sur l’état de chaque fichier PST importé. Une fois l’importation terminée et les fichiers PST importés dans les boîtes aux lettres d’utilisateur, l’état devient **Terminé**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Afficher la liste des fichiers PST téléchargés vers Microsoft 365

Vous pouvez installer et utiliser l’Explorateur de stockage Microsoft Azure (il s’agit d’un outil gratuit open source) pour afficher la liste des fichiers PST que nous avons téléchargés (par le personnel du centre de données Microsoft) vers la zone de stockage Azure de votre organisation. Vous pouvez effectuer cette opération pour vérifier que les fichiers PST des disques durs que vous avez envoyés à Microsoft ont été téléchargés dans la zone de stockage Azure.
  
L’Explorateur de stockage Azure de Microsoft est dans l’aperçu.
  
 **Important :** Vous ne pouvez pas utiliser l’Explorateur de stockage Azure pour télécharger ou modifier des fichiers PST. La seule méthode prise en charge pour l’importation de fichiers PST vers Microsoft 365 consiste à utiliser AzCopy. Il est également impossible de supprimer les fichiers PST que vous avez chargés vers l’objet Blob Azure. Si vous essayez de supprimer un fichier PST, vous recevez une erreur indiquant que vous ne disposez pas des autorisations requises. Tous les fichiers PST sont automatiquement supprimés de votre zone de stockage Azure. S’il n’y a pas de tâches d’importation en cours, tous les fichiers PST du conteneur * * ingestiondata * * sont supprimés 30 jours après la création de la tâche d’importation la plus récente. 
  
Pour installer l’Explorateur Stockage Microsoft Azure et vous connecter à votre zone de stockage Azure, procédez comme suit :
  
1. Pour obtenir l’URL de signature d’accès partagé (SAS) de votre organisation, procédez comme suit. Cette URL est une combinaison de l’URL réseau de l’emplacement de stockage Azure dans le Cloud Microsoft pour votre organisation et d’une clé SAS. Cette clé vous fournit les autorisations nécessaires pour accéder à l’emplacement de stockage Azure de votre organisation.
    
1. Accédez à [https://protection.office.com/](https://protection.office.com/) et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation. 
    
2. Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Gouvernance de l'information > Importer > Importer des fichiers PST**.
    
3. Dans la page **Importer des fichiers PST**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.
    
4. Dans l’Assistant importation de tâche, tapez un nom pour le travail d’importation PST, puis cliquez sur **suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.
    
5. Dans la page **choisir le type de travail d’importation** , cliquez sur **télécharger vos données**, puis sur **suivant**.
    
6. À l’étape 2, cliquez sur **Afficher l’URL de la SAS de chargement réseau**.
    
7. Une fois l’URL affichée, copiez-la et enregistrez-la dans un fichier. Veillez à copier la totalité de l’URL.
    
    > [!IMPORTANT]
    > Veillez à prendre des précautions pour protéger l’URL de SAS. Elle peut être utilisée par tout le monde pour accéder à la zone de stockage Azure de votre organisation. 
  
8. Cliquez sur **Annuler** pour fermer l’Assistant importation de tâche. 
    
2. Téléchargez et installez [l’outil Explorateur Stockage Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=544842).
    
3. Démarrez l’Explorateur Stockage Microsoft Azure, cliquez avec le bouton droit sur **Comptes de stockage** dans le volet de gauche, puis cliquez sur **Se connecter au stockage Azure**.
    
    ![Cliquez avec le bouton droit de la souris sur Comptes de stockage, puis cliquez sur Se connecter au stockage Azure](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
4. Cliquez sur **Utiliser une URI de la signature d’accès partagé (SAS) ou une chaîne de connexion** puis cliquez sur **Suivant**.
    
5. Cliquez sur **utiliser un URI SAS**, collez l’URL SAS que vous avez obtenue à l’étape 1 dans à dans la zone sous **URI**, puis cliquez sur **suivant**.
    
6. Sur la page **Résumé de connexion**, vous pouvez passer en revue les informations de connexion, puis cliquez sur **Se connecter**.
    
    Le conteneur **ingestiondata** est ouvert. Il contient les fichiers PST de votre disque dur. Le conteneur **ingestiondata** se trouve sous ** Compte de stockage** \> **(Services connectés SAS)** \> **Les conteneurs Blob**.
    
    ![L’explorateur de stockage Azure affiche la liste des fichiers PST que vous avez chargés](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
7. Lorsque vous avez fini d’utiliser l’Explorateur Stockage Microsoft Azure, cliquez avec le bouton droit sur **ingestiondata**, puis cliquez sur **Détacher** pour vous déconnecter de votre zone de stockage. Dans le cas contraire, vous recevrez un message d’erreur la prochaine fois que vous tenterez de joindre un élément. 
    
    ![Cliquez avec le bouton droit de la souris sur Ingestion, puis cliquez sur Détacher pour vous déconnecter à partir de votre zone de stockage Azure](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Conseils de dépannage

- **Que se passe-t-il si la tâche d’importation échoue en raison d’erreurs dans le fichier de mappage CSV d’importation PST ?** Si une tâche d’importation échoue en raison d’erreurs dans le fichier de mappage, il n’est pas nécessaire de réexpédier le disque dur à Microsoft pour créer une tâche d’importation. En effet, les fichiers PST du disque dur que vous avez soumis pour le travail d’importation de l’expédition de disque ont déjà été téléchargés dans la zone de stockage Azure de votre organisation. Dans ce cas, il vous suffit de corriger les erreurs dans le fichier de mappage CSV d’importation PST, puis de créer une nouvelle tâche d’importation de « chargement réseau » et de soumettre le fichier de mappage CSV révisé. Pour créer et démarrer un travail d’importation de chargement réseau, reportez-vous à [étape 5 : créer une tâche d’importation PST dans Microsoft 365](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) et [étape 6 : filtrer les données et démarrer le travail d’importation PST](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) dans la rubrique « utiliser le chargement réseau pour importer des fichiers PST vers Office 365 ». 
    
    > [!NOTE]
    > Pour vous aider à résoudre les problèmes du fichier de mappage CSV d’importation PST, utilisez l’outil [Azure Storage Explorer](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) pour afficher la structure de dossiers dans le conteneur **ingestiondata** pour les fichiers PST de votre disque dur qui ont été chargés dans la zone de stockage Azure. Les erreurs de fichier de mappage sont généralement causées par une valeur incorrecte dans le paramètre FilePath. Ce paramètre spécifie l’emplacement d’un fichier PST dans la zone de stockage Azure. Consultez la description du paramètre FilePath dans le tableau de l' [étape 3](#step-3-create-the-pst-import-mapping-file). Comme expliqué précédemment, l’emplacement des fichiers PST dans la zone de stockage Azure était spécifié par le `/dstdir:` paramètre lors de l’exécution de l’outil WAImportExport.exe à l' [étape 2](#step-2-copy-the-pst-files-to-the-hard-drive). 
  
## <a name="more-information"></a>Plus d’informations

- L’expédition de disque constitue un moyen efficace pour importer de grandes quantités de données de messagerie archivées vers Microsoft 365 afin de tirer parti des fonctionnalités de conformité disponibles pour votre organisation. Une fois que les données d’archivage sont importées dans des boîtes aux lettres utilisateur, vous pouvez :
    
  - Activez les [boîtes aux lettres d’archivage](enable-archive-mailboxes.md) et la [croissance automatique de l’archivage](enable-unlimited-archiving.md) pour fournir aux utilisateurs davantage d’espace de stockage de boîtes aux lettres. 
    
  - Placez les boîtes aux lettres en [conservation pour litige](https://go.microsoft.com/fwlink/?linkid=856286) pour conserver les données. 
    
  - Utiliser les [Outils eDiscovery](search-for-content.md) de Microsoft pour effectuer des recherches dans les données. 
    
  - Appliquez les [stratégies de rétention de Microsoft 365](retention.md) pour contrôler la durée de conservation des données, ainsi que les mesures à prendre après l’expiration de la période de rétention. 
    
  - Recherchez dans le [Journal d’audit](search-the-audit-log-in-security-and-compliance.md) les événements liés à ces données. 
    
  - Importer des données dans des [boîtes aux lettres inactives](create-and-manage-inactive-mailboxes.md) pour archiver des données à des fins de conformité. 
    
  - Protégez votre organisation contre la [perte de données](data-loss-prevention-policies.md) sensibles. 
    
- Here's an example of the secure storage account key and a BitLocker encryption key. This example also contains the syntax for the WAImportExport.exe command that you run to copy PST files to a hard drive. Be sure to take precautions to protect these just like you would protect passwords or other security-related information.
    

    ```text
    Secure storage account key: 

    yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==

    BitLocker encryption key:

    397386-221353-718905-535249-156728-127017-683716-083391

  COMMAND SYNTAX

  First time:

  WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /sk:<Storage account key> /blobtype:BlockBlob /encrypt /logdir:<Log file location>

  Subsequent times:

  WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 

  EXAMPLES

  First time:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER1\PSTs" /dstdir:"ingestiondata/" /sk:"yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==" /blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"

  Subsequent times:

  WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER1\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

- Comme indiqué auparavant, le service importation pour Office 365 active le paramètre de blocage de rétention (pour une durée indéterminée) après l’importation de fichiers PST dans une boîte aux lettres. Cela signifie que la propriété *RentionHoldEnabled* est définie sur de `True` sorte que la stratégie de rétention attribuée à la boîte aux lettres ne soit pas traitée. Le propriétaire de la boîte aux lettres a ainsi le temps de gérer les messages nouvellement importés en empêchant une stratégie de suppression ou d’archivage de supprimer ou d’archiver des messages plus anciens. Voici quelques étapes à suivre pour gérer ce blocage de rétention : 
    
  - Au bout d’un certain temps, vous pouvez désactiver le blocage de rétention en exécutant la `Set-Mailbox -RetentionHoldEnabled $false` commande. Pour plus d'instructions, consultez [Activer le blocage de rétention d’une boîte aux lettres](https://go.microsoft.com/fwlink/p/?LinkId=544749).
    
  - Vous pouvez configurer le blocage de rétention pour qu’il se désactive à une date ultérieure. Pour ce faire, exécutez la `Set-Mailbox -EndDateForRetentionHold <date>` commande. Par exemple, en supposant que la date du jour est le 1er juin 2016 et que vous voulez désactiver le blocage de rétention dans 30 jours, exécutez la commande suivante : `Set-Mailbox -EndDateForRetentionHold 7/1/2016` . Dans ce scénario, vous laisserez la propriété *RentionHoldEnabled* définie sur *true*. Pour plus d’informations, consultez [Set-Mailbox](https://go.microsoft.com/fwlink/p/?LinkId=150317).
    
  - Vous pouvez modifier les paramètres de stratégie de rétention attribuée à la boîte aux lettres pour que les anciens éléments qui ont été importés ne soient ni supprimés immédiatement, ni déplacés vers la boîte aux lettres d’archivage de l’utilisateur. Par exemple, vous pouvez allonger l’âge de rétention d’une stratégie de suppression ou d’archivage associée à la boîte aux lettres. Dans ce scénario, vous devez désactiver le blocage de rétention sur la boîte aux lettres après la modification des paramètres de la stratégie de rétention. Pour plus d’informations, voir [Configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
    

  

