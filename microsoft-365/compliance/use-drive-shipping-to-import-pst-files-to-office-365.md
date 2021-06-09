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
description: L’administrateur peut apprendre à importer en bloc des fichiers PST dans Microsoft 365 boîtes aux lettres en copiant des fichiers PST sur un disque dur, puis en les expédiant à Microsoft.
ms.openlocfilehash: a0858e3c1b6bcbe48a4060e8efaa3094768236fb
ms.sourcegitcommit: a6fb731fdf726d7d9fe4232cf69510013f2b54ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684079"
---
# <a name="use-drive-shipping-to-import-your-organizations-pst-files"></a>Utiliser l’expédition de disque pour importer les fichiers PST de votre organisation

**Cet article est pour les administrateurs. Essayez-vous d’importer des fichiers PST dans votre propre boîte aux lettres ? Voir Importer le courrier électronique, les contacts et le calendrier à partir [Outlook fichier .pst](https://go.microsoft.com/fwlink/p/?LinkID=785075)**
   
Utilisez le service d Office 365 d’importation et d’expédition de disque pour importer en bloc des fichiers PST dans des boîtes aux lettres utilisateur. L’expédition de disque consiste à copier les fichiers PST sur un lecteur de disque dur et à expédier physiquement le lecteur à Microsoft. Lorsque Microsoft reçoit votre disque dur, le personnel du centre de données copie les données du disque dur vers une zone de stockage dans le cloud Microsoft. Ensuite, vous avez la possibilité de découper les données PST importées dans les boîtes aux lettres cibles en définir des filtres qui contrôlent les données importées. Après avoir commencé la tâche d’importation, le service d’importation importe les données PST de l’espace de stockage vers les boîtes aux lettres des utilisateurs. L’utilisation de l’expédition de disque pour importer des fichiers PST dans les boîtes aux lettres des utilisateurs est un moyen de migrer le courrier électronique de votre organisation vers Office 365.
  
Voici les étapes à suivre pour utiliser l’expédition de disque pour importer des fichiers PST dans Microsoft 365 boîtes aux lettres :
  
[Étape 1 : Télécharger la clé de stockage sécurisé et l’outil d’importation PST](#step-1-download-the-secure-storage-key-and-pst-import-tool)

[Étape 2 : Copier les fichiers PST sur le disque dur](#step-2-copy-the-pst-files-to-the-hard-drive)

[Étape 3 : Créer le fichier de mappage d’importation PST](#step-3-create-the-pst-import-mapping-file)

[Étape 4 : Créer une tâche d’importation PST dans Office 365](#step-4-create-a-pst-import-job-in-office-365)

[Étape 5 : Expédier le disque dur à Microsoft](#step-5-ship-the-hard-drive-to-microsoft)

[Étape 6 : Filtrer les données et démarrer la tâche d’importation PST](#step-6-filter-data-and-start-the-pst-import-job)
  
> [!IMPORTANT]
> Vous devez effectuer l’étape 1 une seule fois pour charger la clé de stockage sécurisé et l’outil d’importation. Après avoir effectué ces étapes, suivez les étapes 2 à 6 chaque fois que vous souhaitez expédier un disque dur à Microsoft. 
  
Pour les questions fréquemment posées sur l’utilisation de l’expédition de disque pour importer des fichiers PST dans Office 365, voir FAQ pour l’utilisation de l’expédition de disque pour importer des [fichiers PST.](./faqimporting-pst-files-to-office-365.yml#using-drive-shipping-to-import-pst-files) 
  
## <a name="before-you-import-pst-files"></a>Avant d’importer des fichiers PST

- Le rôle Importation/Exportation de boîtes aux lettres doit vous avoir été attribué dans Exchange Online pour pouvoir importer des fichiers PST dans des boîtes aux lettres Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîte aux lettres au groupe de rôles Gestion de l’organisation. Vous pouvez aussi créer un nouveau groupe de rôles, lui attribuer le rôle Importation/Exportation de boîtes aux lettres, puis vous ajouter en tant que membre. Pour plus d’informations, consultez les sections « Ajouter un rôle à un groupe de rôles » ou « Créer un groupe de rôles » dans [Gérer les groupes de rôles](/Exchange/permissions-exo/role-groups).
    
    En outre, pour créer des tâches d’importation dans le centre Microsoft 365 conformité, l’une des conditions suivantes doit être vraie :
    
  - Vous devez avoir le rôle de destinataire de courrier dans Exchange Online. Par défaut, ce rôle est assigné aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.
    
    Ou
    
  - Vous devez être un administrateur général au sein de votre organisation.
    
    > [!TIP]
    > Envisagez de créer un nouveau groupe de rôles dans Exchange Online spécialement conçu pour importer les fichiers PST dans Office 365. Pour obtenir le niveau minimum de privilèges requis pour importer des fichiers PST, affectez les rôles d’importation/exportation de boîte aux lettres et de destinataire de courrier au nouveau groupe de rôles et ajoutez ensuite les membres. 
  
- Vous devez stocker les fichiers PST que vous souhaitez copier vers un disque dur sur un serveur de fichiers ou un dossier partagé dans votre organisation. À l’étape 2, vous exécutez l’outil Azure Import Export (WAImportExport.exe) qui copie les fichiers PST stockés sur ce serveur de fichiers ou ce dossier partagé sur le disque dur.

- Les fichiers PST volumineux peuvent avoir un impact sur les performances du processus d’importation PST. Nous vous recommandons donc que chaque fichier PST que vous copiez sur le disque dur à l’étape 2 ne doit pas être supérieur à 20 Go.
    
- Seuls les disques SSD de 2,5 pouces ou les disques durs internes SATA II/III de 2,5 pouces ou 3,5 pouces sont pris en charge pour une utilisation avec le service d’importation Office 365. Vous pouvez utiliser des disques durs jusqu'à 10 To. Pour les tâches d’importation, uniquement le premier volume de données sur le disque dur est traité. Le volume de données doit être au format NTFS. Lorsque vous copiez des données sur un disque dur, vous pouvez les attacher directement à l’aide d’un connecteur SSD 2,5 pouces ou SATA II/III de 2,5 pouces ou 3,5 pouces ou vous pouvez l’attacher en externe à l’aide d’un adaptateur USB EXTERNE DE 2,5 pouces ou SATA II/III de 2,5 pouces ou 3,5 pouces.
    
    > [!IMPORTANT]
    > Les disques durs externes fournis avec une carte USB intégrée ne sont pas pris en charge par le Service d’importation Office 365. En outre, le disque à l’intérieur du boîtier d’un disque dur externe ne peut pas être utilisé. Veuillez ne pas envoyer de disques durs externes. 
  
- Le disque dur sur lequel vous copiez les fichiers PST doit être chiffré avec BitLocker. L’outil WAImportExport.exe exécuté à l’étape 2 vous permet de configurer BitLocker. Il génère également une clé de chiffrement BitLocker que le personnel du centre de données Microsoft utilise pour accéder au lecteur afin de télécharger les fichiers PST dans la zone stockage Azure dans le cloud Microsoft.
    
- L’expédition de disque est disponible via une Accord Entreprise Microsoft (EA). L’expédition de disque n’est pas disponible dans le cadre d’un Contrat de Fourniture de Produits et de Services Microsoft (MPSA).
    
- Le tarif pour importer des fichiers PST dans les boîtes aux lettres Microsoft 365 via l’expédition de disque s’élève à 2 $ USD par Go de données. Par exemple, si vous expédiez un disque dur qui contient 1 000 Go (1 To) de fichiers PST, cela revient à 2 000 dollars. Vous pouvez travailler en collaboration avec un partenaire qui se chargera de payer les frais d’importation. Pour plus d’informations sur la recherche d’un partenaire, consultez la page [Trouver votre partenaire ou revendeur](../admin/manage/find-your-partner-or-reseller.md).
    
- Vous, ou votre organisation, devez également disposer d’un compte auprès de FedEx ou DHL. 
    
  - Les organisations aux États-Unis, au Brésil et en Europe doivent avoir des comptes FedEx.
    
  - Les organisations en Asie de l’Est, en Asie du Sud-Est, au Japon, en République de Corée et en Australie doivent avoir des comptes DHL.
    
    Microsoft utilise (et facture) ce compte pour vous renvoyer le disque dur.
    
- Le disque dur que vous expédiez à Microsoft peut traverser des frontières internationales. Dans ce cas, vous devez vous assurer que le disque dur et les données qu’il contient sont importés et/ou exportés conformément aux lois applicables. Avant d’envoyer un disque dur, vérifiez auprès de vos conseillers juridiques que votre disque et vos données peuvent être légalement expédiés au centre de données Microsoft concerné. Cela permet de s’assurer qu’elle atteint Microsoft en temps voulu.
    
- Cette procédure nécessite la copie et l’enregistrement d’une clé de stockage sécurisé et d’une clé de chiffrement BitLocker. Veillez à prendre toutes les précautions nécessaires pour protéger ces clés, comme vous le feriez avec vos mots de passe ou d’autres informations de sécurité. Par exemple, vous pouvez les enregistrer dans un document Microsoft Word protégé par mot de passe ou dans un lecteur USB chiffré. Consultez la section [Plus](#more-information) d’informations pour obtenir un exemple de ces clés. 
    
- Une fois les fichiers PST importés dans une boîte aux lettres Microsoft 365, le paramètre de conservation de rétention de la boîte aux lettres est allumé pour une durée indéfinie. Cela signifie que la stratégie de rétention attribuée à la boîte aux lettres ne sera pas traitée tant que vous n’aurez pas désactivé la conservation de rétention ou défini une date pour désactiver la conservation. Quel est le but de cette action ? Si les messages importés dans une boîte aux lettres sont anciens, ils peuvent être supprimés définitivement (purgés) parce que leur période de conservation a expiré selon les paramètres de conservation configurés pour cette boîte aux lettres. La mise de la boîte aux lettres en attente de conservation donne au propriétaire de la boîte aux lettres le temps de gérer ces nouveaux messages importés ou de modifier les paramètres de conservation de la boîte aux lettres. Consultez la section [Plus d’informations](#more-information) pour obtenir des suggestions sur la gestion du conservation de rétention. 
    
- Par défaut, la taille maximale d’un message pouvant être reçu par une boîte aux lettres Microsoft 365 est de 35 Mo. En effet, la valeur par défaut de la propriété *MaxReceiveSize* pour une boîte aux lettres est définie sur 35 Mo. Toutefois, la limite de la taille maximale de réception d’un message dans Microsoft 365 est de 150 Mo. Par conséquent, si vous importez un fichier PST qui contient un élément d’une taille supérieure à 35 Mo, le service d’importation d’Office 365 modifie automatiquement la valeur de la propriété *MaxReceiveSize* sur la boîte aux lettres cible à 150 Mo. Ainsi, les messages allant jusqu’à 150 Mo sont importés dans les boîtes aux lettres d’utilisateur. 
    
    > [!TIP]
    > Pour identifier la taille de réception des messages pour une boîte aux lettres, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :  `Get-Mailbox <user mailbox> | FL MaxReceiveSize` 
  
- Vous pouvez importer des fichiers PST dans une boîte aux lettres inactive dans Office 365. Pour ce faire, vous devez spécifier le GUID de la boîte aux lettres inactive dans le paramètre `Mailbox` du fichier de mappage d’importation PST. Pour plus d’informations, voir Étape 3 : créer le fichier de [mappage d’importation PST.](#step-3-create-the-pst-import-mapping-file) 
    
- Dans un déploiement hybride Exchange, vous pouvez importer des fichiers PST dans une boîte aux lettres d'archivage basé sur le cloud pour un utilisateur dont la boîte aux lettres principale est locale. Pour ce faire, procédez comme suit dans le fichier de mappage d’importation PST :
    
  - Indiquez l’adresse électronique de la boîte aux lettres locale de l'utilisateur dans le paramètre `Mailbox`. 
    
  - Spécifiez la valeur **TRUE** dans le paramètre `IsArchive`. 
    
    Pour plus d’informations, voir Étape 3 : créer le fichier de [mappage d’importation PST.](#step-3-create-the-pst-import-mapping-file) 

## <a name="step-1-download-the-secure-storage-key-and-pst-import-tool"></a>Étape 1 : Télécharger la clé de stockage sécurisé et l’outil d’importation PST

La première étape consiste à télécharger la clé de stockage sécurisé et l’outil, et que vous utilisez à l’étape 2 pour copier des fichiers PST sur le disque dur.
  
> [!IMPORTANT]
> Vous devez utiliser l’outil Azure Import/Export version 1 (WAimportExportV1) pour importer correctement des fichiers PST à l’aide de la méthode d’expédition de disque. La version 2 de l’outil Azure Import/Export n’est pas prise en charge et son utilisation entraîne une préparation incorrecte du disque dur pour le travail d’importation. N’oubliez pas de télécharger l’outil Azure Import/Export à partir du centre de conformité Microsoft 365 en suivant les procédures de cette étape. 
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet de navigation gauche du centre Microsoft 365 conformité, cliquez sur **Importer la gouvernance des** \> **informations.**
    
    > [!NOTE]
    > Comme indiqué précédemment, vous devez obtenir les autorisations appropriées pour accéder à la **page** d’importation dans Microsoft 365 conformité. 
  
3. Dans la page **Importer**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.
    
4. Dans l’Assistant Importation, tapez un nom pour la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.
    
5. Dans la page **Choisir le type de travail** d’importation, cliquez sur Expédier des **disques durs à** l’un de nos emplacements physiques, puis cliquez sur **Suivant.**
    
    ![Cliquez sur Expédier des disques durs vers l’un de nos emplacements physiques pour créer une tâche d’importation d’expédition de disque](../media/1584fdc5-cd4c-4e47-932e-db6c8e07f5f8.png)
  
6. Dans la page **Importer des données**, effectuez les deux opérations suivantes : 
    
    ![Copiez la clé de stockage sécurisé et téléchargez l’outil d’importation et d’exportation Azure sur la page Importer des données](../media/e22e0b48-e5ce-48e0-95bc-0490a2b3b983.png)
  
    a. À l’étape 2, cliquez **sur Afficher la clé de stockage sécurisé.** Une fois la clé de  stockage affichée, cliquez sur Copier dans le Presse-papiers, collez-la et enregistrez-la dans un fichier pour y accéder ultérieurement.
    
    b. À l’étape 3, **téléchargez l’outil Azure Import/Export** pour télécharger et installer l’outil Azure Import/Export (version 1).
    
    - Dans la fenêtre pop-up, cliquez sur Enregistrer sous pour enregistrer le fichier WaImportExportV1.zip dans un dossier  \>  de votre ordinateur local. 
    
    - Extrayez WaImportExportV1.zip fichier.
    
7. Cliquez **sur Annuler** pour fermer l’Assistant. 
    
    Vous revenir à la page **Importer** dans le centre Microsoft 365 conformité lorsque vous créez la tâche d’importation à l’étape 4. 

## <a name="step-2-copy-the-pst-files-to-the-hard-drive"></a>Étape 2 : Copier les fichiers PST sur le disque dur

Pour réaliser cette étape, vous devez utiliser l’outil WAImportExport.exe pour copier les fichiers PST sur le disque dur. Cet outil chiffre le disque dur avec BitLocker, copie les fichiers PST sur le disque dur et crée un fichier journal qui stocke des informations sur le processus de copie. Pour cela, les fichiers PST doivent se trouver sur un dossier partagé ou un serveur de fichiers dans votre organisation. Il s’agit du répertoire source mentionné dans la procédure suivante. 

 Comme indiqué précédemment, chaque fichier PST que vous copiez sur le disque dur ne doit pas être supérieur à 20 Go. Les fichiers PST d’une taille supérieure à 20 Go peuvent avoir un impact sur les performances du processus d’importation PST démarré à l’étape 6.
  
> [!IMPORTANT]
> Après avoir exécuté l’outil WAImportExport.exe pour la première fois pour un disque dur, vous devez utiliser une syntaxe différente les fois suivantes. Cette syntaxe est expliquée à l’étape 4 de cette procédure pour copier des fichiers PST sur le disque dur. 
  
1. Ouvrez une invite de commandes sur votre ordinateur local.
    
    > [!TIP]
    > Si vous exécutez l’invite de commandes en tant qu’administrateur (en sélectionnant « Exécuter en tant qu’administrateur » quand vous l’ouvrez), la fenêtre d’invite de commandes affiche des messages d’erreur. Cela peut vous aider à résoudre les problèmes d’exécution de l’outil WAImportExport.exe. 
  
2. Accédez au répertoire où vous avez installé l’outil WAImportExport.exe à l’étape 1.
    
3. Exécutez la commande suivante lorsque vous utilisez l’outil WAImportExport.exe pour la première fois pour copier les fichiers PST sur un disque dur.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /t:<Drive letter> /id:<Name of session> /srcdir:<Location of PST files> /dstdir:<PST file path> /sk:<Storage account key> /blobtype:BlockBlob /encrypt /logdir:<Log file location>
    ```

    Le tableau suivant décrit les paramètres et leurs valeurs requises. 
    
    |**Parameter**|**Description**|**Exemple**|
    |:-----|:-----|:-----|
    | `/j:` <br/> |Indique le nom du fichier journal. Ce fichier est enregistré dans le dossier où se trouve l’outil WAImportExport.exe. Un fichier journal doit être créé sur chaque disque dur envoyé à Microsoft. Chaque fois que vous exécutez l’outil WAImportTool.exe pour copier des fichiers PST sur un disque dur, des informations sont ajoutées au fichier journal de ce disque. 
  <br/> Le personnel du centre de données Microsoft utilise les informations du fichier journal pour associer le disque dur à la tâche d’importation que vous créez à l’étape 4 et pour télécharger les fichiers PST dans la zone stockage Azure dans le cloud Microsoft.  <br/> | `/j:PSTHDD1.jrn` <br/> |
    | `/t:` <br/> |Indique la lettre de lecteur du disque dur quand celui-ci est connecté à votre ordinateur local.  <br/> | `/t:h` <br/> |
    | `/id:` <br/> |Indique le nom de la session de copie. Une session est définie dès que vous exécutez l’outil WAImportExport.exe pour copier des fichiers sur le disque dur. Les fichiers PST sont copiés dans un dossier portant le même nom que la session spécifiée par ce paramètre.   <br/> | `/id:driveship1` <br/> |
    | `/srcdir:` <br/> |Indique le répertoire source de votre organisation contenant les fichiers PST qui seront copiés pendant la session. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `/srcdir:"\\FILESERVER01\PSTs"` <br/> |
    | `/dstdir:` <br/> |Spécifie le répertoire de destination dans la stockage Azure dans le cloud Microsoft où les fichiers PTS seront téléchargés. Vous devez utiliser la valeur  `ingestiondata/` . N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> Si vous le souhaitez, vous pouvez également ajouter un chemin d’accès de fichier supplémentaire à la valeur de ce paramètre. Par exemple, vous pouvez utiliser le chemin d’accès au fichier du répertoire source sur le disque dur (converti au format URL), qui est spécifié dans le  `/srcdir:` paramètre. Par exemple,  `\\FILESERVER01\PSTs` est modifié en  `FILESERVER01/PSTs` . Dans ce cas, vous devez toujours inclure  `ingestiondata` dans le chemin d’accès du fichier. Ainsi, dans cet exemple, la valeur du  `/dstdir:` paramètre serait  `"ingestiondata/FILESERVER01/PSTs"` .  <br/> Ajouter un chemin d’accès supplémentaire peut être utile si plusieurs fichiers PST portent le même nom.  <br/> > [!NOTE]> Si vous incluez le chemin d’accès facultatif, l’espace de noms d’un fichier PST après son chargement dans la zone stockage Azure inclut le chemin d’accès et le nom du fichier PST ; par exemple, `FILESERVER01/PSTs/annb.pst` . Si vous n’incluez pas de chemin d’accès, l’espace de noms est uniquement le nom de fichier PST ; par  `annb.pst` exemple.           | `/dstdir:"ingestiondata/"` <br/> Ou  <br/>  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` <br/> |
    | `/sk:` <br/> |Spécifie la clé du compte de stockage obtenue à l’étape 1. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `"yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ=="` <br/> |
    | `/blobtype:` <br/> |Spécifie le type d’objets blob dans la stockage Azure pour importer les fichiers PST. Pour importer des fichiers PST, utilisez la valeur **BlockBlob**. Ce paramètre est obligatoire.   <br/> | `/blobtype:BlockBlob` <br/> |
    | `/encrypt` <br/> |Ce commutateur active BitLocker pour le disque dur. Ce paramètre est obligatoire la première fois que vous exécutez l’outil WAImportExport.exe.  <br/> La BitLocker de chiffrement est copiée dans le fichier journal et le fichier journal créé si vous utilisez le `/logfile:` paramètre. Comme indiqué précédemment, le fichier journal est enregistré dans le dossier où se trouve l’outil WAImportExport.exe.  <br/> | `/encrypt` <br/> |
    | `/logdir:` <br/> |Ce paramètre facultatif indique le dossier dans lequel les fichiers journaux seront enregistrés. S’il n’est pas spécifié, les fichiers journaux sont enregistrés dans le dossier où se trouve WAImportExport.exe'outil. N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").  <br/> | `/logdir:"c:\users\admin\desktop\PstImportLogs"` <br/> |
   
    Voici un exemple de la syntaxe de l’outil WAImportExport.exe qui reprend les valeurs réelles de chaque paramètre :
    
    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /t:f /id:driveship1 /srcdir:"\\FILESERVER01\PSTs" /dstdir:"ingestiondata/" /sk:"yaNIIs9Uy5g25Yoak+LlSHfqVBGOeNwjqtBEBGqRMoidq6/e5k/VPkjOXdDIXJHxHvNoNoFH5NcVUJXHwu9ZxQ==" blobtype:BlockBlob /encrypt /logdir:"c:\users\admin\desktop\PstImportLogs"
    ```

    Une fois la commande exécutée, les messages d’état affichent la progression du processus de copie des fichiers PST sur le disque dur. Un message d’état final affiche le nombre total de fichiers qui ont été copiés. 
    
4. Exécutez cette commande chaque fois que vous exécutez l’outil WAImportExport.ext pour copier des fichiers PST sur le même disque dur.

    ```powershell
    WAImportExport.exe PrepImport /j:<Name of journal file> /id:<Name of new session> /srcdir:<Location of PST files> /dstdir:<PST file path> /blobtype:BlockBlob 
    ```

    Voici un exemple de la syntaxe pour copier ultérieurement des fichiers PST sur le même disque dur.  

    ```powershell
    WAImportExport.exe PrepImport /j:PSTHDD1.jrn /id:driveship2 /srcdir:"\\FILESERVER01\PSTs\SecondBatch" /dstdir:"ingestiondata/" /blobtype:BlockBlob
    ```

## <a name="step-3-create-the-pst-import-mapping-file"></a>Étape 3 : Créer le fichier de mappage d’importation PST

Une fois que le personnel du centre de données Microsoft a chargé les fichiers PST du disque dur vers la zone stockage Azure, le service d’importation utilise les informations du fichier de mappage d’importation PST, qui est un fichier de valeurs séparées par des virgules (CSV), qui spécifie dans quelles boîtes aux lettres utilisateur les fichiers PST sont importés. Ce fichier PST est envoyé à l’étape suivante lors de la création d’une tâche d’importation PST.
  
1. [Téléchargez une copie du fichier de mappage d’importation PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).
    
2. Ouvrez ou enregistrez le fichier CSV sur votre ordinateur local. L’exemple suivant montre le contenu d’un fichier de mappage d’importation PST (ouvert dans le Bloc-notes). Utilisez plutôt Microsoft Excel pour modifier le fichier CSV.

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
    > Ne modifiez en aucun cas la ligne d’en-tête, ni les paramètres SharePoint ; ils seront ignorés pendant le processus d’importation des fichiers PST. 
  
3. Utilisez les informations du tableau suivant pour remplir le fichier CSV avec les informations requises.
    
    |**Parameter**|**Description**|**Exemple**|
    |:-----|:-----|:-----|
    | `Workload` <br/> |Indique le service où les données seront importées. Pour importer des fichiers PST dans les boîtes aux lettres d’utilisateur, utilisez  `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> | Spécifie l’emplacement du dossier dans la stockage Azure où les fichiers PST seront copiés lors de l’expédition du disque dur à Microsoft.  <br/>  Ce que vous ajoutez dans cette colonne dans le fichier CSV dépend de ce que vous avez spécifié pour le paramètre à  `/dstdir:` l’étape précédente. Si vous avez des sous-dossiers sur l’emplacement source, la valeur dans le paramètre doit contenir le chemin d’accès relatif du sous-dossier , par `FilePath` exemple, /folder1/user1/.  <br/>  Si vous avez  `/dstdir:"ingestiondata/"` utilisé , laissez ce paramètre vide dans le fichier CSV.  <br/>  Si vous avez inclus un chemin d’accès facultatif pour la valeur du paramètre (par exemple, utilisez ce chemin d’accès (sans inclure « ingestiondata ») pour ce paramètre dans le fichier  `/dstdir:`  `/dstdir:"ingestiondata/FILESERVER01/PSTs"` CSV. La valeur de ce paramètre est sensible à la casse.  <br/>  Dans tous les cas, n'incluez *pas* « ingestiondata » dans la valeur du paramètre `FilePath`. Laissez ce paramètre vide ou spécifiez uniquement le chemin d’accès facultatif.  <br/> > [!IMPORTANT]> le nom du chemin d’accès du fichier doit être identique à celui que vous avez spécifié dans le paramètre à  `/dstdir:` l’étape précédente. Par exemple, si vous avez utilisé le nom du sous-dossier à l’étape précédente, puis utilisé dans le paramètre dans le fichier CSV, l’importation du fichier  `"ingestiondata/FILESERVER01/PSTs"`  `fileserver01/psts`  `FilePath` PST échouera. Veillez à utiliser la même casse dans les deux instances.           |(Laisser vide)  <br/> Ou  <br/>  `FILESERVER01/PSTs` <br/> |
    | `Name` <br/> |Indique le nom du fichier PST qui sera importé dans la boîte aux lettres d’utilisateur. La valeur de ce paramètre est sensible à la casse.  <br/> > [!IMPORTANT]> Le nom du fichier PST dans le fichier CSV doit être identique au fichier PST qui a été téléchargé vers l’emplacement stockage Azure à l’étape 2. Par exemple, si vous utilisez  `annb.pst` dans le paramètre `Name` du fichier CSV, mais que le nom du fichier PST réel est  `AnnB.pst`, l’importation de ce fichier PST échouera. Assurez-vous que le nom du fichier PST dans le fichier CSV utilise la même casse que le fichier PST réel.           | `annb.pst` <br/> |
    | `Mailbox` <br/> |Indique l’adresse électronique de la boîte aux lettres dans laquelle le fichier PST est importé. Vous ne pouvez pas spécifier un dossier public, car le service d’importation PST ne prend pas en charge l’importation de fichiers PST dans les dossiers publics.  <br/> Pour importer un fichier PST dans une boîte aux lettres inactive, vous devez indiquer le GUID de la boîte aux lettres pour ce paramètre. Pour obtenir ce GUID, exécutez la commande PowerShell suivante dans Exchange Online :  `Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> > [!NOTE]> parfois, vous pouvez avoir plusieurs boîtes aux lettres avec la même adresse de messagerie, où une boîte aux lettres est une boîte aux lettres active et l’autre est dans un état supprimé (ou inactif) à l’état supprimé (ou inactif). Dans ce cas, vous devez spécifier le GUID de boîte aux lettres pour identifier de façon unique la boîte aux lettres dans laquelle importer le fichier PST. Pour obtenir ce GUID des boîtes aux lettres actives, exécutez la commande PowerShell suivante :  `Get-Mailbox <identity of active mailbox> | FL Guid` Pour obtenir le GUID des boîtes aux lettres supprimées (ou inactives), exécutez la commande ci-après : `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`           | `annb@contoso.onmicrosoft.com` <br/> Ou  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Indique si vous importez le fichier PST dans la boîte aux lettres d’archivage de l’utilisateur. Il existe deux options :<br/> **FALSE** Importe le fichier PST dans la boîte aux lettres principale de l’utilisateur.  <br/> **TRUE** Importe le fichier PST dans la boîte aux lettres d’archivage de l’utilisateur. Cela implique l’[activation de la boîte aux lettres d’archivage de l’utilisateur](enable-archive-mailboxes.md). Si vous définissez ce paramètre sur `TRUE` et que la boîte aux lettres d’archivage de l’utilisateur n’est pas activée, l’importation échouera pour cet utilisateur. Si une importation échoue pour un utilisateur (car son archive n’est pas activée et que cette propriété est définie sur `TRUE`), les autres utilisateurs dans la tâche d’importation ne seront pas affectés.  <br/>  Si vous ne renseignez pas ce paramètre, le fichier PST est importé dans la boîte aux lettres principale de l’utilisateur.  <br/> **Remarque :** Pour importer un fichier PST dans une boîte aux lettres d’archivage dans le cloud pour un utilisateur dont la boîte aux lettres principale est accessible localement, indiquez `TRUE` pour ce paramètre et indiquez l’adresse de courrier de la boîte aux lettres locale de l’utilisateur pour le paramètre `Mailbox`.  <br/> | `FALSE` <br/> Ou  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Indique le dossier de la boîte aux lettres dans lequel le fichier PST est importé.  <br/>  Si vous laissez ce paramètre vide, le fichier PST est importé dans un nouveau dossier nommé **Importé** situé au niveau racine de la boîte aux lettres (au même niveau que le dossier Boîte de réception et les autres dossiers de boîte aux lettres par défaut).  <br/>  Si vous spécifiez , les éléments du fichier PST seront importés directement dans le dossier Boîte de réception de  `/` l’utilisateur.  <br/>  Si vous spécifiez , les éléments du fichier PST seront  `/<foldername>` importés dans un dossier nommé  *\<foldername\>* . Par exemple, si vous utilisez  `/ImportedPst`, les éléments sont importés dans un dossier nommé **ImportedPst**. Ce dossier se trouve dans la boîte aux lettres de l’utilisateur au même niveau que le dossier boîte de réception.  <br/> |(Laisser vide)  <br/> Ou  <br/>  `/` <br/> Ou  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ce paramètre facultatif indique une valeur numérique que la page de codes doit utiliser pour importer des fichiers PST au format de fichier ANSI. Ce paramètre permet d’importer des fichiers PST à partir d’organisations chinoises, japonaises et coréennes, car ces langues utilisent généralement un jeux de caractères à deux octets (DBCS) pour le codage de caractères. Si ce paramètre n’est pas utilisé pour importer des fichiers PST pour les langues qui utilisent des caractères DBCS pour les noms des dossiers de boîte aux lettres, les noms des dossiers sont souvent déformés une fois qu’ils sont importés.  <br/> Pour obtenir la liste des valeurs prises en charge à utiliser pour ce paramètre, consultez [Identificateurs de page de codes](/windows/win32/intl/code-page-identifiers).  <br/> > [!NOTE]> comme indiqué précédemment, il s’agit d’un paramètre facultatif et vous n’avez pas besoin de l’inclure dans le fichier CSV. Ou vous pouvez également l’inclure et conserver la valeur vide pour une ou plusieurs lignes.           |(Laisser vide)  <br/> Ou  <br/>  `932` (il s’agit de l’identificateur de page de codes pour le japonais ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPManifestContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPSiteUrl` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |

## <a name="step-4-create-a-pst-import-job-in-office-365"></a>Étape 4 : Créer une tâche d’importation PST dans Office 365

L'étape suivante consiste à créer la tâche d'importation PST dans le service d'importation dans Office 365. Comme indiqué précédemment, vous envoyez le fichier de mappage d’importation PST que vous avez créé à l’étape 3. Après avoir créé la tâche, le service d’importation utilise les informations du fichier de mappage pour importer les fichiers PST dans la boîte aux lettres utilisateur spécifiée une fois que les fichiers PST sont copiés du disque dur vers la zone stockage Azure et que vous créez et démarrez la tâche d’importation.
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet de navigation gauche du centre Microsoft 365 conformité, cliquez sur **Importer la gouvernance des** \> **informations.**

3. Dans la page **Importer**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.

    > [!NOTE]
    > Comme indiqué précédemment, vous devez obtenir les autorisations appropriées pour accéder à la **page** d’importation dans Microsoft 365 conformité.
  
4. Entrez le nom de la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.

5. Dans la page **Choisir le type de travail** d’importation, cliquez sur Expédier des **disques durs à** l’un de nos emplacements physiques, puis cliquez sur **Suivant.**
  
6. À l’étape 6, cliquez sur le disque dur que j’ai préparé et que j’ai accès aux fichiers de journal de lecteur nécessaires et **j’ai** accès aux cases à cocher de fichier de mappage, puis cliquez sur  **Suivant**.

    ![Cliquez sur les deux cases à cocher de l’étape 6](../media/fad43078-ea68-4acd-b2ed-75a800183262.png)
  
7. Dans la page Sélectionner **le** fichier de lecteur, cliquez sur Sélectionner un fichier de **lecteur,** puis dans le dossier où se trouve WAImportExport.exe'outil. Le fichier journal créé à l’étape 2 a été copié dans ce dossier.

    ![Cliquez sur Sélectionner un fichier de lecteur pour envoyer le fichier journal qui a été créé lorsque vous avez WAImportExport.exe'outil](../media/1ea35c04-bd88-4d7e-b7d9-dc390149d94f.png)
  
8. Sélectionnez le fichier journal ; par exemple, `PSTHDD1.jrn` .

    > [!TIP]
    > Lorsque vous avez WAImportExport.exe'outil à l’étape 2, le nom du fichier journal a été spécifié par le  `/j:` paramètre.
  
9. Une fois que le nom du fichier de lecteur apparaît sous le nom du fichier **lecteur,** cliquez sur **Valider** pour vérifier si votre fichier de lecteur présente des erreurs.

    ![Cliquez sur Valider pour valider le fichier de lecteur que vous avez sélectionné](../media/4b707f5a-152a-4e74-b9f5-449c88d1fec4.png)
  
    Le fichier de lecteur doit être validé pour créer une tâche d’importation PST. Le nom du fichier passe à la couleur verte une fois qu'il a été validé avec succès. Si la validation échoue, cliquez sur le lien **Afficher le journal**. Un rapport d’erreur de validation s’ouvre, avec un message d’erreur avec des informations sur la raison de l’échec du fichier. 

    > [!NOTE]
    > Vous devez ajouter et valider un fichier journal pour chaque disque dur que vous expédiez à Microsoft. 
  
10. Après avoir ajouté et validé un fichier journal pour chaque disque dur que vous expédiez à Microsoft, cliquez sur **Suivant**.
    
11. Cliquez sur Ajouter un fichier de mappage De sélection d’icône pour envoyer le fichier de mappage d’importation PST que ![ vous avez créé à ](../media/ITPro-EAC-AddIcon.gif)  l’étape 3. 

    ![Cliquez sur Sélectionner le fichier de mappage pour envoyer le fichier CSV que vous avez créé pour la tâche d’importation.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
12. Lorsque le nom du fichier CSV apparaît dans la liste, **Nom de fichier de mappage**, cliquez sur **Valider** pour vérifier que votre fichier CSV ne contient pas d’erreurs. 

    ![Cliquez sur Valider pour rechercher les erreurs dans le fichier CSV.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Le fichier CSV doit être validé avec succès pour créer une tâche d'importation PST. Le nom du fichier passe à la couleur verte une fois qu'il a été validé avec succès. Si la validation échoue, cliquez sur le lien **Afficher le journal**. Un rapport d'erreur de validation est ouvert, avec un message d'erreur pour chaque ligne du fichier qui a échoué. 

13. Une fois le fichier de mappage PST validé, cliquez sur **Suivant.**

14. Dans la page **Fournir des informations de contact,** tapez vos informations de contact dans les zones applicables. 

    L’adresse de l’emplacement Microsoft vers qui vous expédiez vos disques durs s’affiche. Cette adresse est générée automatiquement en fonction de votre emplacement de centre de données Microsoft. Copiez cette adresse dans un fichier ou effectuez une capture d’écran.

15. Lisez le document des conditions générales, cochez la case, puis cliquez sur **Enregistrer** pour envoyer la tâche d’importation. 

    Lorsque la tâche d’importation est correctement créée, une page d’état s’affiche qui explique les étapes suivantes du processus d’expédition de disque.

16. Sous **l’onglet** Importation, cliquez sur Actualiser l’icône Actualiser pour afficher la nouvelle tâche d’importation d’expédition de disque dans la ![ liste des tâches ](../media/O365-MDM-Policy-RefreshIcon.gif)  d’importation. L’état est définie sur **En attente de numéro de suivi**. Vous pouvez également cliquer sur la tâche d’importation pour afficher la page de présentation de l’état, qui contient des informations plus détaillées sur la tâche d’importation.

## <a name="step-5-ship-the-hard-drive-to-microsoft"></a>Étape 5 : Expédier le disque dur à Microsoft

L’étape suivante consiste à expédier le disque dur à Microsoft, puis à fournir le numéro de suivi de l’expédition et à renvoyer les informations d’expédition pour le travail d’expédition de disque. Une fois le lecteur reçu par Microsoft, il faudra entre 7 et 10 jours ouvés pour que le personnel du centre de données télécharge vos fichiers PST dans la zone stockage Azure de votre organisation.
  
> [!NOTE]
> Si vous ne fournissez pas le numéro de suivi et ne retournez pas d’informations sur l’expédition dans les 14 jours suivant la création de la tâche d’importation, la tâche d’importation a expiré. Si cela se produit, vous devez créer une tâche d’importation d’expédition de disque (voir Étape 4 : Créer une tâche d’importation PST dans [Office 365)](#step-4-create-a-pst-import-job-in-office-365)et soumettre à nouveau le fichier de lecteur et le fichier de mappage d’importation PST.
  
### <a name="ship-the-hard-drive"></a>Envoyer le disque dur

Gardez ces informations à l’esprit quand vous envoyez des disques durs à Microsoft :
  
- N’expédiez pas l’adaptateur SATA-USB ; vous devez uniquement expédier le disque dur.

- Emballez le disque dur correctement (par exemple, utilisez un sac anti-statique ou du papier bulle).

- Prenez le transporteur de votre choix pour envoyer le disque dur à Microsoft.

- Envoyez le disque dur à l’adresse du site Microsoft affichée lors de la création de la tâche d’importation à l’étape 4. N’oubliez pas d’indiquer « Service d’importation Office 365 » dans l’adresse d’expédition.

- Une fois votre disque dur envoyé, pensez à noter le nom du transporteur et le numéro de suivi. Vous devrez les indiquer à l’étape suivante.
    
### <a name="enter-the-tracking-number-and-other-shipping-information"></a>Entrer le numéro de suivi et d’autres informations d’expédition

Une fois le disque dur envoyé à Microsoft, effectuez les étapes suivantes sur la page du service d’importation.
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur Gouvernance des informations **> Importer**.

3. Sous **l’onglet** Importation, cliquez sur le travail pour l’expédition de disque dont vous souhaitez entrer le numéro de suivi.

4. Dans la page du volant d’état, cliquez **sur Entrer le numéro de suivi.**

5. Fournissez les informations suivantes :

   1. **Opérateur de remise** Tapez le nom de l’opérateur de remise que vous avez utilisé pour livrer le disque dur à Microsoft. 

   2. **Numéro de suivi** Tapez le numéro de suivi de l’expédition du disque dur. 

   3. **Numéro de compte de l’opérateur de retour** Tapez le numéro de compte de votre organisation pour l’opérateur répertorié sous **Opérateur de retour.** Microsoft utilise (et facture) ce compte pour vous retourner votre disque dur. Les organisations aux États-Unis et en Europe doivent avoir un compte fedex. Les organisations en Asie et dans le reste du monde doivent posséder un compte DHL.

6. Cliquez sur **Enregistrer** pour enregistrer ces informations pour la tâche d’importation. 

    Sous **l’onglet Importer,** cliquez sur Actualiser l’icône Actualiser pour mettre à jour les informations de votre ![ tâche d’importation ](../media/O365-MDM-Policy-RefreshIcon.gif)  d’expédition de disque. Notez que le statut est désormais défini sur **Disques en transit**.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Étape 6 : Filtrer les données et démarrer la tâche d’importation PST

Une fois votre disque dur reçu par Microsoft, l’état de la tâche d’importation sur la page Importer des fichiers **PST** passe à **Lecteurs reçus.** Le personnel du centre de données utilise les informations du fichier journal pour télécharger vos fichiers PST dans la stockage Azure de votre organisation. À ce stade, l’état est en cours **d’importation.** Comme indiqué précédemment, le chargement des fichiers PST prend entre 7 et 10 jours ou jours après la réception de votre disque dur.
  
Une fois les fichiers PST téléchargés vers Azure, l’état est modifié **en Analyse en cours.** Cela indique que Microsoft 365 analyse les données des fichiers PST (de manière sécurisée et sécurisée) pour identifier l’âge des éléments et les différents types de messages inclus dans les fichiers PST. Lorsque l’analyse est terminée et que les données sont prêtes à être importées, l’état de la tâche d’importation est modifié en **Analyse terminée.** À ce stade, vous avez la possibilité d’importer toutes les données contenues dans les fichiers PST ou vous pouvez découper les données importées en fixant des filtres qui contrôlent les données importées.
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet de navigation gauche du centre Microsoft 365 conformité, cliquez sur **Gouvernance** des informations \> **Importer****.

3. Sous **l’onglet** Importation, sélectionnez la tâche d’importation que vous avez créée à l’étape 4, puis cliquez sur **Importer Office 365**.
  
    Une page volante s’affiche avec des informations sur les fichiers PST et d’autres informations sur la tâche d’importation.

4. Cliquez **sur Importer Office 365**.

5. La page **Filtrez vos données** s’affiche. Elle contient les aperçus des données résultant de l'analyse des fichiers PST effectuée par Office 365, y compris des informations sur l'âge des données. À ce stade, vous avez la possibilité de filtrer les données qui seront importées ou d’importer toutes les données telles quelles. 

    ![Vous pouvez découper les données dans les fichiers PST ou les importer](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
6. Effectuez l’une des opérations suivantes :

    a. Pour découper les données que vous importez, cliquez sur **Oui, je souhaite les filtrer avant l’importation**.

    Pour obtenir des instructions détaillées sur le filtrage des données dans les fichiers PST et le démarrage de la tâche d’importation, consultez la rubrique [Filtrer les données lors de l’importation de fichiers PST dans Office 365](filter-data-when-importing-pst-files.md).

    Ou

    b. Pour importer toutes les données des fichiers PST, cliquez sur **Non, je souhaite tout importer,** puis cliquez sur **Suivant**.

7. Si vous avez choisi d’importer toutes les données, cliquez sur **Importer les données** pour démarrer la tâche d’importation. 

    L’état de la tâche d’importation s’affiche dans la page **Importer des fichiers PST.** Cliquer sur ![Actualiser l’icône](../media/O365-MDM-Policy-RefreshIcon.gif)**Actualiser** pour mettre à jour les informations d’état affichées dans la colonne **État**. Cliquez sur la tâche d’importation pour afficher la page de menu volant d’état qui affiche des informations sur l’état de chaque fichier PST importé. Une fois l’importation terminée et les fichiers PST importés dans les boîtes aux lettres d’utilisateur, l’état devient **Terminé**.

## <a name="view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>Afficher la liste des fichiers PST téléchargés vers Microsoft 365

Vous pouvez installer et utiliser le Explorateur Stockage Microsoft Azure (qui est un outil open source gratuit) pour afficher la liste des fichiers PST que nous avons téléchargés (par le personnel du centre de données Microsoft) dans la zone stockage Azure de votre organisation. Vous pouvez le faire pour vérifier que les fichiers PST des disques durs que vous avez envoyés à Microsoft ont été chargés vers la stockage Azure de données.
  
> [!IMPORTANT]
> Vous ne pouvez pas utiliser l’Explorateur de stockage Azure pour charger ou modifier des fichiers PST. La seule méthode prise en charge pour importer des fichiers PST dans Microsoft 365 est d’utiliser AzCopy. Il est également impossible de supprimer les fichiers PST que vous avez chargés vers l’objet Blob Azure. Si vous essayez de supprimer un fichier PST, vous recevez une erreur de ne pas disposer des autorisations requises. Tous les fichiers PST sont automatiquement supprimés de votre stockage Azure de données. Si aucune tâche d’importation n’est en cours, tous les fichiers PST dans le conteneur ** ingestiondata ** sont supprimés 30 jours après la création de la tâche d’importation la plus récente.
  
Effectuez les étapes suivantes pour obtenir l’URL de signature d’accès partagé (SAS) pour votre organisation. Cette URL est une combinaison de l’URL réseau pour l’emplacement stockage Azure dans le cloud Microsoft de votre organisation et d’une clé SAS. Cette clé vous fournit les autorisations nécessaires pour accéder à l’emplacement stockage Azure organisation.

Pour installer l’Explorateur Stockage Microsoft Azure et vous connecter à votre zone de stockage Azure, procédez comme suit :

1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet gauche du Centre de conformité Microsoft 365, cliquez sur **Gouvernance des informations > Importer**.

3. Dans la page **Importer**, cliquez sur ![Ajouter une icône](../media/ITPro-EAC-AddIcon.gif) **Nouvelle tâche d’importation**.

4. Dans l’Assistant Importation, tapez un nom pour la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.

5. Dans la page **Choisir le type de** travail d’importation, cliquez Télécharger **données,** puis cliquez sur **Suivant**.

6. À l’étape 2, cliquez sur **Afficher l’URL de la SAS de chargement réseau**.

7. Une fois l’URL affichée, copiez-la et enregistrez-la dans un fichier. Veillez à copier la totalité de l’URL.

    > [!IMPORTANT]
    > Veillez à prendre des précautions pour protéger l’URL de SAS. Cette fonctionnalité peut être utilisée par tout le monde pour accéder à l’espace de stockage Azure de votre organisation.
  
8. Cliquez **sur Annuler** pour fermer l’Assistant Importation.

9. Téléchargez et installez [l’outil Explorateur Stockage Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=544842).

10. Démarrez l’Explorateur Stockage Microsoft Azure, cliquez avec le bouton droit sur **Comptes de stockage** dans le volet de gauche, puis cliquez sur **Se connecter au stockage Azure**.

    ![Cliquez avec le bouton droit de la souris sur Comptes de stockage, puis cliquez sur Se connecter au stockage Azure](../media/75b80cc3-c336-4f96-ad32-54ac9b96a7af.png)
  
11. Cliquez sur **Utiliser une URI de la signature d’accès partagé (SAS) ou une chaîne de connexion** puis cliquez sur **Suivant**.

12. Cliquez **sur Utiliser un URI SAS,** collez l’URL SAS obtenue à l’étape 1 dans la zone sous **URI,** puis cliquez sur **Suivant**.

13. Sur la page **Résumé de connexion**, vous pouvez passer en revue les informations de connexion, puis cliquez sur **Se connecter**.

    Le conteneur **ingestiondata** est ouvert. Il contient les fichiers PST de votre disque dur. Le conteneur **ingestiondata** se trouve sous **Compte de stockage** \> **(Services connectés SAS)** \> **Les conteneurs Blob**.

    ![L’explorateur de stockage Azure affiche la liste des fichiers PST que vous avez chargés](../media/12376fed-13a5-4a09-8fe6-e819e011b334.png)
  
14. Lorsque vous avez fini d’utiliser l’Explorateur Stockage Microsoft Azure, cliquez avec le bouton droit sur **ingestiondata**, puis cliquez sur **Détacher** pour vous déconnecter de votre zone de stockage. Dans le cas contraire, vous recevrez un message d’erreur la prochaine fois que vous tenterez de joindre un élément. 

    ![Cliquez avec le bouton droit de la souris sur Ingestion, puis cliquez sur Détacher pour vous déconnecter à partir de votre zone de stockage Azure](../media/1e8e5e95-4215-4ce4-a13d-ab5f826a0510.png)

## <a name="troubleshooting-tips"></a>Conseils de dépannage

- **Que se passe-t-il si la tâche d’importation échoue en raison d’erreurs dans le fichier de mappage CSV d’importation PST ?** Si une tâche d’importation échoue en raison d’erreurs dans le fichier de mappage, vous n’avez pas besoin de réasser le disque dur à Microsoft pour créer une tâche d’importation. Cela est dû au fait que les fichiers PST du disque dur que vous avez soumis pour la tâche d’importation d’expédition de disque ont déjà été téléchargés vers la zone stockage Azure de votre organisation. Dans ce cas, il vous suffit de corriger les erreurs dans le fichier de mappage CSV d’importation PST, puis de créer une tâche d’importation « chargement réseau » et d’envoyer le fichier de mappage CSV révisé. Pour créer et démarrer une tâche d’importation de chargement réseau, voir Étape 5 : Créer une tâche d’importation [PST](use-network-upload-to-import-pst-files.md#step-5-create-a-pst-import-job) dans Microsoft 365 et étape 6 : filtrer les données et démarrer la tâche d’importation [PST](use-network-upload-to-import-pst-files.md#step-6-filter-data-and-start-the-pst-import-job) dans la rubrique « Utiliser le chargement réseau pour importer des fichiers PST dans Office 365 ». 
    
    > [!NOTE]
    > Pour vous aider à résoudre les problèmes du fichier de mappage [CSV](#view-a-list-of-the-pst-files-uploaded-to-microsoft-365) d’importation PST, utilisez l’outil Explorateur Stockage Azure pour afficher la structure de dossiers dans le conteneur **ingestiondata** pour les fichiers PST à partir de votre disque dur qui ont été téléchargés vers la zone de stockage Azure. Les erreurs de fichier de mappage sont généralement causées par une valeur incorrecte dans le paramètre FilePath. Ce paramètre spécifie l’emplacement d’un fichier PST dans la zone de stockage Azure. Consultez la description du paramètre FilePath dans le tableau de [l’étape 3.](#step-3-create-the-pst-import-mapping-file) Comme indiqué précédemment, l’emplacement des fichiers PST dans la zone de stockage Azure a été spécifié par le paramètre lorsque vous avez lancé l’outil WAImportExport.exe à `/dstdir:` [l’étape 2.](#step-2-copy-the-pst-files-to-the-hard-drive) 
  
## <a name="more-information"></a>Plus d’informations

- L’expédition de disques est un moyen efficace d’importer de grandes quantités de données de messagerie d’archivage vers Microsoft 365 afin de tirer parti des fonctionnalités de conformité disponibles pour votre organisation. Une fois les données d’archivage importées dans les boîtes aux lettres des utilisateurs, vous pouvez :

  - Activez [les boîtes aux lettres d’archivage](enable-archive-mailboxes.md) et [l’archivage](enable-unlimited-archiving.md) à extension automatique pour offrir aux utilisateurs davantage d’espace de stockage pour les données. 

  - Placez les boîtes aux lettres [en attente pour litige](./create-a-litigation-hold.md) pour conserver les données. 

  - Utilisez les [outils eDiscovery de](search-for-content.md) Microsoft pour effectuer des recherches dans les données. 

  - Appliquez [Microsoft 365 stratégies](retention.md) de rétention pour contrôler la durée de conservation des données et l’action à prendre après l’expiration de la période de rétention. 

  - Recherchez [dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md) les événements liés à ces données. 

  - Importer des données dans des [boîtes aux lettres inactives](create-and-manage-inactive-mailboxes.md) pour archiver des données à des fins de conformité. 

  - Protégez votre organisation contre [la perte de données](dlp-learn-about-dlp.md) d’informations sensibles. 

- Voici un exemple de la clé de compte de stockage sécurisé et d’une clé de chiffrement BitLocker. Cet exemple contient également la syntaxe de la commande WAImportExport.exe qui permet de copier les fichiers PST sur un disque dur. Veillez à prendre toutes les précautions nécessaires pour protéger ces clés, tout comme vous le feriez avec vos mots de passe ou d’autres informations de sécurité.

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

- Comme indiqué auparavant, le service importation pour Office 365 active le paramètre de blocage de rétention (pour une durée indéterminée) après l’importation de fichiers PST dans une boîte aux lettres. Cela signifie que  *la propriété RentionHoldEnabled*  est définie de sorte que la stratégie de rétention affectée à la boîte aux lettres  `True` ne soit pas traitée. Le propriétaire de la boîte aux lettres a ainsi le temps de gérer les messages nouvellement importés en empêchant une stratégie de suppression ou d’archivage de supprimer ou d’archiver des messages plus anciens. Voici quelques étapes à suivre pour gérer ce blocage de rétention : 

  - Après un certain temps, vous pouvez désactiver le conservation de rétention en exécutant la  `Set-Mailbox -RetentionHoldEnabled $false` commande. Pour plus d'instructions, consultez [Activer le blocage de rétention d’une boîte aux lettres](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Vous pouvez configurer le blocage de rétention pour qu’il se désactive à une date ultérieure. Pour ce faire, exécutez la  `Set-Mailbox -EndDateForRetentionHold <date>` commande. Par exemple, en supposant que la date du jour est le 1er juin 2016 et que vous souhaitez que la conservation de rétention soit désactivée dans 30 jours, exécutez la commande suivante  `Set-Mailbox -EndDateForRetentionHold 7/1/2016` : Dans ce scénario, vous laisseriez la  *propriété RentionHoldEnabled*  définie sur  *True*. Pour plus d’informations, consultez [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Vous pouvez modifier les paramètres de stratégie de rétention attribuée à la boîte aux lettres pour que les anciens éléments qui ont été importés ne soient ni supprimés immédiatement, ni déplacés vers la boîte aux lettres d’archivage de l’utilisateur. Par exemple, vous pouvez allonger l’âge de rétention d’une stratégie de suppression ou d’archivage associée à la boîte aux lettres. Dans ce scénario, vous devez désactiver le blocage de rétention sur la boîte aux lettres après la modification des paramètres de la stratégie de rétention. Pour plus d’informations, voir [Configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).
