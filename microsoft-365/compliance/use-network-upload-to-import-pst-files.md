---
title: Utilisez le chargement réseau pour importer les fichiers PST de votre organisation.
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 103f940c-0468-4e1a-b527-cc8ad13a5ea6
description: 'Pour les administrateurs : apprenez comment utiliser le chargement réseau pour importer en bloc plusieurs fichiers PST dans les boîtes aux lettres d’utilisateur de Microsoft 365.'
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c9ab46c5f801a9069f4b1614f6b04161ee431d5b
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531773"
---
# <a name="use-network-upload-to-import-your-organizations-pst-files-to-microsoft-365"></a>Utilisez le chargement réseau pour importer les fichiers PST de votre organisation dans Microsoft 365

> [!NOTE]
> Cet article s’adresse aux administrateurs. Vous souhaitez importer des fichiers PST dans votre propre boîte aux lettres ? Consultez la rubrique [Importer le courrier électronique, les contacts et le calendrier à partir d’un fichier .pst Outlook](https://go.microsoft.com/fwlink/p/?LinkID=785075)
  
Voici les instructions détaillées requises pour utiliser le chargement réseau pour importer en bloc plusieurs fichiers PST dans les boîtes aux lettres Microsoft 365. Pour les questions fréquemment posées sur l’utilisation du chargement réseau pour importer en bloc des fichiers PST dans les boîtes aux lettres Microsoft 365, consultez la rubrique [FAQ sur l’utilisation du chargement réseau pour importer les fichiers PST](./faqimporting-pst-files-to-office-365.yml#using-network-upload-to-import-pst-files).
  
[Étape 1 : Copier l’URL SAS et télécharger AzCopy](#step-1-copy-the-sas-url-and-download-azcopy)

[Étape 2 : Charger des fichiers PST dans Microsoft 365](#step-2-upload-your-pst-files-to-microsoft-365)

[(Facultatif) Étape 3 : Afficher la liste des fichiers PST chargés](#optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365)

[Étape 4 : Créer le fichier de mappage d’importation PST](#step-4-create-the-pst-import-mapping-file)

[Étape 5 : Créer une tâche d’importation PST](#step-5-create-a-pst-import-job)

[Étape 6 : Filtrer les données et démarrer la tâche d’importation PST](#step-6-filter-data-and-start-the-pst-import-job)

Vous ne devez effectuer l’étape 1 qu’une seule fois pour importer des fichiers PST dans les boîtes aux lettres Microsoftˆ365. Une fois que vous avez réalisé cette étape, répétez les étapes 2 à 6 chaque fois que vous souhaitez télécharger et importer un lot de fichiers PST.

## <a name="before-you-import-pst-files"></a>Avant d’importer des fichiers PST
  
- Le rôle Importation/Exportation de boîtes aux lettres doit vous avoir été attribué dans Exchange Online pour pouvoir importer des fichiers PST dans des boîtes aux lettres Microsoft 365. Par défaut, ce rôle n’est affecté à aucun groupe de rôles dans Exchange Online. Vous pouvez ajouter le rôle Importation/Exportation de boîtes aux lettres au groupe de rôles Gestion de l’organisation. Vous pouvez aussi créer un groupe de rôles, lui attribuer le rôle Importation/Exportation de boîtes aux lettres, puis vous ajouter en tant que membre. Pour plus d’informations, consultez les sections « Ajouter un rôle à un groupe de rôles » ou « Créer un groupe de rôles » dans [Gérer les groupes de rôles](/Exchange/permissions-exo/role-groups).

    En outre, pour créer des tâches d’importation dans le Centre de conformité Microsoft 365, l’une des conditions suivantes doit être remplie :

  - Vous devez avoir le rôle de destinataire de courrier dans Exchange Online. Par défaut, ce rôle est assigné aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.

    Ou

  - Vous devez être un administrateur général au sein de votre organisation.

    > [!TIP]
    > Envisagez de créer un nouveau groupe de rôles dans Exchange Online spécialement conçu pour importer les fichiers PST. Pour obtenir le niveau minimum de privilèges requis pour importer des fichiers PST, affectez les rôles d’importation/exportation de boîte aux lettres et de destinataire de courrier au nouveau groupe de rôles et ajoutez ensuite les membres.
  
- La seule méthode prise en charge pour importer des fichiers PST dans Microsoft 365 consiste à utiliser l’outil AzCopy, comme décrit dans cet article. Vous ne pouvez pas utiliser l’Explorateur de stockage Azure pour charger des fichiers PST directement dans la zone de stockage Azure.

- Vous devez stocker les fichiers PST que vous souhaitez importer dans Microsoft 365 sur un serveur de fichiers ou un dossier partagé dans votre organisation. Il n’est actuellement pas pris en charge de copier des fichiers PST à partir du compte stockage Azure de votre organisation vers l’emplacement stockage Azure utilisé par le service d’importation Microsoft 365. À l’étape 2, vous exécutez l’outil AzCopy qui charge les fichiers PST stockés sur un serveur de fichiers ou dossier partagé dans le cloud Microsoft.

- Les fichiers PST volumineux peuvent avoir un impact sur les performances du processus d’importation PST. Par conséquent, nous vous recommandons de ne pas dépasser 20 Go pour chaque fichier PST téléchargé sur l’emplacement de stockage Azure à l’étape 2.

- Cette procédure nécessite la copie et l’enregistrement d'une copie d'une URL contenant une clé d'accès. Ces informations seront utilisées à l’étape 2 pour charger vos fichiers PST et à l’étape 3 si vous souhaitez afficher la liste des fichiers PST chargés dans Microsoft 365. Veillez à prendre toutes les précautions nécessaires pour protéger ces URL, tout comme vous le feriez avec vos mots de passe ou d’autres informations liées à la sécurité. Par exemple, vous pouvez les enregistrer dans un document Microsoft Word protégé par mot de passe ou sur une clé USB cryptée. Consultez la section [Informations supplémentaires](#more-information) pour obtenir un exemple de cette combinaison d'URL et de clé.

- Vous pouvez importer des fichiers PST dans une boîte aux lettres inactive dans Microsoft 365. Pour ce faire, vous devez spécifier le GUID de la boîte aux lettres inactive dans le paramètre `Mailbox` du fichier de mappage d’importation PST. Pour plus d’informations, consultez l’étape 4 de l’onglet **Instructions** de cet article.

- Dans un déploiement hybride Exchange, vous pouvez importer des fichiers PST dans une boîte aux lettres d'archivage basé sur le cloud pour un utilisateur dont la boîte aux lettres principale est locale. Pour ce faire, procédez comme suit dans le fichier de mappage d’importation PST :

  - Indiquez l’adresse électronique de la boîte aux lettres locale de l'utilisateur dans le paramètre `Mailbox`.

  - Spécifiez la valeur **TRUE** dans le paramètre `IsArchive`.

    Pour plus d’informations, consultez l’[Étape 4](#step-4-create-the-pst-import-mapping-file).

- Une fois les fichiers PST importés, le paramètre de conservation de rétention de la boîte aux lettres est activé pour une durée indéterminée. Cela signifie que la stratégie de rétention attribuée à la boîte aux lettres ne sera pas traitée tant que vous n’aurez pas désactivé la conservation de rétention ou défini une date pour désactiver la conservation. Quel est le but de cette action ? Si les messages importés dans une boîte aux lettres sont anciens, ils peuvent être supprimés définitivement (purgés) parce que leur période de conservation a expiré selon les paramètres de conservation configurés pour cette boîte aux lettres. La mise de la boîte aux lettres en attente de conservation donne au propriétaire de la boîte aux lettres le temps de gérer ces nouveaux messages importés ou de modifier les paramètres de conservation de la boîte aux lettres. Consultez la section [Plus d’informations](#more-information) de cet article pour obtenir des suggestions sur la gestion de la conservation.

- Par défaut, la taille maximale d’un message pouvant être reçu par une boîte aux lettres Microsoft 365 est de 35 Mo. En effet, la valeur par défaut de la propriété *MaxReceiveSize* pour une boîte aux lettres est définie sur 35 Mo. Toutefois, la limite de la taille maximale de réception d’un message dans Microsoft 365 est de 150 Mo. Par conséquent, si vous importez un fichier PST qui contient un élément d’une taille supérieure à 35 Mo, le service d’importation Microsoft 365 modifie automatiquement la valeur de la propriété *MaxReceiveSize* sur la boîte aux lettres cible à 150 Mo. Ainsi, les messages allant jusqu’à 150 Mo sont importés dans les boîtes aux lettres d’utilisateur.

    > [!TIP]
    > Pour identifier la taille de réception des messages pour une boîte aux lettres, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :  `Get-Mailbox <user mailbox> | FL MaxReceiveSize`

- Pour une vue d’ensemble du processus d’importation PST, voir [Fonctionnement du processus d’importation](#how-the-import-process-works) dans cet article.

## <a name="step-1-copy-the-sas-url-and-download-azcopy"></a>Étape 1 : Copier l’URL SAS et télécharger AzCopy

La première étape consiste à télécharger l’outil AzCopy, qui est l’outil que vous exécutez à l’étape 2 pour charger des fichiers PST dans Microsoft 365. Vous copiez également l’URL de SAS pour votre organisation. Cette URL est une combinaison de l'URL réseau de l'emplacement de stockage Azure dans le cloud Microsoft de votre entreprise et d'une clé de signature d’accès partagé (SAS). Cette clé vous fournit les autorisations nécessaires pour charger des fichiers PST vers un emplacement de stockage Azure. Veillez à prendre des précautions pour protéger l’URL de SAS. Elle est propre à votre organisation et sera utilisée à l’étape 2.

> [!IMPORTANT]
> Pour importer des fichiers PST à l’aide de la méthode de chargement réseau et de la syntaxe de commande signalées dans cet article, vous devez utiliser la version d'AzCopy qui peut être téléchargée à l’étape 6b de la procédure suivante. Vous pouvez également télécharger la même version de AzCopy [ici](https://aka.ms/downloadazcopylatest). L’utilisation d’une version différente de AzCopy n’est pas prise en charge.
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet gauche du Centre de conformité Microsoft 365, cliquez sur **Gouvernance des informations** \> **Importer**.

    > [!NOTE]
    > Vous devez disposer des autorisations appropriées pour accéder à la page **Importer** dans le Centre de conformité Microsoft 365. Consultez la section **Avant de commencer** pour plus d’informations. 

3. Sous l’onglet **Importer**, cliquez sur l’![Icône Ajouter.](../media/ITPro-EAC-AddIcon.gif)**nouvelle tâche d’importation**.

    L’assistant de l’importation de tâche s’affiche.

4. Entrez le nom de la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.

5. Dans la page **Souhaitez-vous charger ou expédier les données ?**, cliquez sur **Charger vos données**, puis cliquez sur **Suivant**.

    ![Cliquez sur Charger vos données pour créer une tâche d'importation en réseau.](../media/e59f9dc3-ccde-44ff-ac38-c4e39d76ae85.png)
  
6. Dans la page **Importer des données**, effectuez les deux opérations suivantes :

    ![Copier l’URL de SAS et télécharger l’outil AzCopy sur la page Importer des données](../media/74411014-ec4b-4e25-9065-404c934cce17.png)
  
    1. À l’étape 2, cliquez sur **Afficher l’URL de la SAS de chargement réseau**. Une fois l’URL de la SAS affichée, cliquez sur **Copier dans le presse-papiers**, puis collez-la et enregistrez-la dans un fichier pour pouvoir y accéder plus tard.

    2. À l’étape 3, cliquez sur **Télécharger Azure AzCopy** pour télécharger l’outil AzCopy sur votre ordinateur local. Cette version d’AzCopy est simplement un fichier exécutable. Il n’y a donc rien à installer.

   > [!NOTE]
   > Vous pouvez laisser la page **Importer des données** ouverte (au cas où vous devriez recopier l’URL de SAS) ou cliquer sur **Annuler** pour la fermer.

## <a name="step-2-upload-your-pst-files-to-microsoft-365"></a>Étape 2 : Charger des fichiers PST dans Microsoft 365

Vous êtes maintenant prêt à utiliser l’outil AzCopy pour charger des fichiers PST dans Microsoft 365. Cet outil charge et stocke les fichiers PST dans un emplacement de stockage Azure fourni par Microsoft dans le cloud Microsoft. Comme précédemment expliqué, l’emplacement de stockage Azure vers lequel vous chargez vos fichiers PST se trouve dans le centre de données Microsoft régional où se trouve votre organisation. Pour effectuer cette étape, les fichiers PST doivent se trouver dans un partage de fichiers ou un serveur de fichiers de votre organisation ou dans un emplacement de stockage Azure géré par votre organisation. L’emplacement de stockage PST est appelé emplacement source dans cette procédure. Chaque fois que vous exécutez l’outil AzCopy, vous pouvez spécifier un emplacement source différent.

> [!NOTE]
> Comme indiqué précédemment, ne pas dépasser 20 Go pour chaque fichier PST téléchargé sur l’emplacement de stockage Azure. Les fichiers PST d’une taille supérieure à 20 Go peuvent avoir un impact sur les performances du processus d’importation PST démarré à l’étape 6. De plus, chaque fichier PST doit avoir un nom unique.

1. Ouvrez une invite de commandes sur votre ordinateur local.

2. Accédez au répertoire où vous avez téléchargé le fichier azcopy.exe à l’étape 1.

3. Exécutez la commande suivante pour charger les fichiers PST sur Microsoft 365.

    ```powershell
    azcopy.exe copy "<Source location of PST files>" "<SAS URL>"
    ```

    > [!IMPORTANT]
    > Vous pouvez spécifier un répertoire ou un emplacement de stockage Azure comme emplacement source dans la commande précédente ; vous ne pouvez pas spécifier un fichier PST individuel. Tous les fichiers PST de l’emplacement source seront chargés.

    Le tableau suivant décrit les champs azcopy.exe et leurs valeurs requises. Les informations que vous avez obtenues à l’étape précédente sont utilisées dans les valeurs de ces champs.

    | Field | Description |
    |:-----|:-----|
    | Source |Le premier champ spécifie le répertoire source de votre organisation qui contient les fichiers PST qui seront chargés dans Microsoft 365. Vous pouvez également spécifier un emplacement de stockage Azure comme emplacement source des fichiers PST à charger. <br/> Veillez à entourer la valeur de ce champ de guillemets doubles ( » « ).  <br/> <br/>**Exemples** : <br/>`"\\FILESERVER01\PSTs"` <br/> Ou  <br/>`"https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx"`|  
    | Destination |Indique l’URL de SAS obtenue à l’étape 1.  <br/> N’oubliez pas de placer la valeur de ce paramètre entre guillemets doubles (" ").<br/><br/>**Remarque :** Si vous utilisez l’URL SAS dans un script ou un fichier de commandes, faites attention à certains caractères qui doivent être placés dans une séquence d’échappement. Par exemple, vous devez modifier `%` en `%%` et `&` en `^&`.<br/><br/>**Astuce :** (facultatif) vous pouvez spécifier un sous-dossier dans l’emplacement de stockage Azure dans lequel charger les fichiers PST. Pour ce faire, vous devez ajouter un emplacement de sous-dossier (après « ingestiondata ») dans l’URL de SAS. Le premier exemple ne spécifie pas un sous-dossier. Cela signifie que les fichiers PST sont chargés dans la racine (nommée *ingestiondata* ) de l’emplacement de stockage Azure. Le deuxième exemple charge les fichiers PST dans un sous-dossier (nommé  *PSTFiles*) dans la racine de l’emplacement de stockage Azure.  <br/><br/>**Exemples** : <br/> `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> Ou  <br/>  `"https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata/PSTFiles?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"` <br/> |
    | `--recursive` |Cet indicateur facultatif spécifie le mode récursif afin que l’outil AzCopy copie les fichiers PST situés dans des sous-dossiers dans le répertoire source spécifié par le champ source. La valeur par défaut de cet indicateur est `true`. <br/>**Remarque :** Si vous incluez cet indicateur, les fichiers PST dans les sous-dossiers ont un nom de chemin d’accès de fichier différent dans l’emplacement stockage Azure après leur chargement. Vous devrez spécifier le chemin d’accès exact dans le fichier CSV créé à l’étape 4.|
    | `--s2s-preserve-access-tier` | Cet indicateur facultatif n’est requis que lorsque l’emplacement source est un emplacement de stockage Azure v2 universel qui prend en charge les niveaux d’accès. Pour le scénario d’importation PST, il n’est pas nécessaire de conserver le niveau d’accès lorsque vous copiez des fichiers PST à partir de votre compte de stockage Azure vers l’emplacement de stockage Azure fourni par Microsoft. Dans ce cas, vous pouvez inclure cet indicateur et utiliser une valeur de `false`. Vous n’avez pas besoin d’utiliser cet indicateur lors de la copie de fichiers PST à partir d’un compte de stockage Azure classique, qui ne prend pas en charge les niveaux d’accès.|
   |||

Pour plus d’informations sur la commande **azcopy.exe copy**, consultez [copie azcopy](/azure/storage/common/storage-ref-azcopy-copy).

Voici des exemples de syntaxe pour l’outil AzCopy utilisant des valeurs réelles pour chaque paramètre.

### <a name="example-1"></a>Exemple 1

Il s’agit d’un exemple pour un répertoire source situé sur un serveur de fichiers ou un ordinateur local.

```powershell
azcopy.exe copy "\\FILESERVER1\PSTs" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D"
```

### <a name="example-2"></a>Exemple 2

Il s’agit d’un exemple pour un répertoire source situé dans un compte de stockage Azure classique avec des sous-répertoires.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --recursive
```

### <a name="example-3"></a>Exemple 3

Il s’agit d’un exemple pour un répertoire source situé dans un compte de stockage Azure v2 à usage général. Les niveaux d’accès ne sont pas conservés lorsque les fichiers PST sont chargés.

```powershell
azcopy.exe copy "https://storageaccountid.blob.core.windows.net/PSTs?sp=racwdl&st=2021-09-21T07:25:53Z&se=2021-09-21T15:25:53Z&sv=2020-08-04&sr=c&sig=xxxxxx" "https://3c3e5952a2764023ad14984.blob.core.windows.net/ingestiondata?sv=2012-02-12&amp;se=9999-12-31T23%3A59%3A59Z&amp;sr=c&amp;si=IngestionSasForAzCopy201601121920498117&amp;sig=Vt5S4hVzlzMcBkuH8bH711atBffdrOS72TlV1mNdORg%3D" --s2s-preserve-access-tier=false
```

Une fois la commande exécutée, les messages d’état affichent la progression du processus de chargement des fichiers PST. Un message d’état final affiche le nombre total de fichiers qui ont été téléchargés.

> [!TIP]
> Après avoir exécuté la commande **copie azcopy.exe** et vérifié que tous les paramètres sont corrects, enregistrez une copie de la syntaxe de ligne de commande dans le même fichier (sécurisé) où vous avez copié les informations que vous avez obtenues à l’étape 1. Vous pouvez ensuite copier et coller cette commande dans une invite de commandes chaque fois que vous souhaitez exécuter l’outil AzCopy pour charger des fichiers PST dans Microsoft 365. La seule valeur que vous devrez peut-être modifier concerne le champ source. Ceci dépend du répertoire source où se trouvent les fichiers PST.

## <a name="optional-step-3-view-a-list-of-the-pst-files-uploaded-to-microsoft-365"></a>(Facultatif) Étape 3 : afficher la liste des fichiers PST chargés dans Microsoft 365

(Facultatif) Vous pouvez installer et utiliser l’explorateur de stockage Microsoft Azure (un outil gratuit et open source) pour afficher la liste des fichiers PST que vous avez téléchargé sur le blob Azure. Il existe deux raisons à le faire :
  
- Vérifiez que les fichiers PST du dossier partagé ou d’un serveur de fichiers dans votre organisation ont été chargés sur le Blob d’Azure.

- Vérifier le nom de fichier (et le chemin d’accès du sous-dossier si vous en avez inclus un) pour chaque fichier PST téléchargé sur le blob Azure. Cela s’avère utile lorsque vous créez le fichier mappage PST à l’étape suivante, car vous devez spécifier le chemin d’accès de dossier et le nom de fichier pour chaque fichier PST. La vérification de ces noms peut permettre de réduire les erreurs potentielles dans votre fichier de mappage PST.

L’application autonome Explorateur Stockage Microsoft Azure est généralement disponible. Vous pouvez télécharger la dernière version en utilisant le lien fourni dans la procédure qui suit.
  
> [!IMPORTANT]
> Vous ne pouvez pas utiliser l’Explorateur Stockage Azure pour charger ou modifier des fichiers PST. La seule méthode prise en charge pour importer des fichiers PST est d’utiliser AzCopy. Vous ne pouvez donc pas supprimer des fichiers PST téléchargés dans le Blob Azure. Si vous tentez de supprimer un fichier PST, vous recevrez une erreur indiquant que vous ne disposez pas des autorisations requises. Notez que tous les fichiers PST sont supprimés automatiquement de votre zone de stockage Azure. S’il n’y a aucune tâche d’importation en cours, tous les fichiers PST dans le conteneur **ingestiondata** sont supprimés 30 jours après la création de la dernière tâche d’importation.
  
Pour installer l’Explorateur Stockage Microsoft Azure et vous connecter à votre zone de stockage Azure, procédez comme suit :
  
1. Téléchargez et installez [l’outil Explorateur Stockage Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=544842).

2. Démarrer Explorateur Stockage Microsoft Azure.

3. Sur la page **Sélectionner une ressource** dans la boîte de dialogue **Connexion à Stockage Azure** , cliquez sur **Conteneur d’objets blob**.
  
4. Sur la page **Sélectionner une méthode d’authentification**, sélectionnez l’option **Signature d’accès partagé (SAS)**, puis cliquez sur **Suivant**.

5. Sur la page **Entrer des informations de connexion**, collez l’URL de la signature d’accès partagé obtenue à l’étape 1 dans la zone sous **URL de la signature d’accès partagé du conteneur d’objets blob**, puis cliquez sur **Suivant**. Après avoir collé l’URL SAS, la zone sous **Nom d’affichage** est renseignée automatiquement avec **ingestiondata**.

6. Sur la page **Résumé**, vous pouvez passer en revue les informations de connexion, puis cliquez sur **Se connecter**.

    Le conteneur **ingestiondata** est ouvert. Il contient les fichiers PST que vous avez téléchargés à l’étape 2. Le conteneur **ingestiondata** se trouve sous **Comptes de stockage** \> **(Conteneurs joints)** \> **Conteneurs blob**. 
  
7. Lorsque vous avez terminé d’utiliser l’Explorateur Stockage Azure, cliquez avec le bouton droit sur **ingestiondata**, puis sur **Détacher** pour vous déconnecter de votre espace de stockage Azure. Dans le cas contraire, vous recevrez une erreur la prochaine fois que vous tenterez de joindre un élément.
  
## <a name="step-4-create-the-pst-import-mapping-file"></a>Étape 4 : Créer le fichier de mappage d’importation PST

Une fois les fichiers PST téléchargés sur l’emplacement de stockage Azure de votre organisation, vous devez créer un fichier (CSV) de valeurs séparées par une virgule qui indique les boîtes aux lettres d’utilisateur dans lesquelles les fichiers PST seront importés. Ce fichier PST est envoyé à l’étape suivante lors de la création d’une tâche d’importation PST.
  
1. [Téléchargez une copie du fichier de mappage d’importation PST](https://go.microsoft.com/fwlink/p/?LinkId=544717).

2. Ouvrez ou enregistrez le fichier CSV sur votre ordinateur local. L’exemple suivant montre le contenu d’un fichier de mappage d’importation PST (ouvert dans le Bloc-notes). Utilisez plutôt Microsoft Excel pour modifier le fichier CSV.

    ```console
    Workload,FilePath,Name,Mailbox,IsArchive,TargetRootFolder,ContentCodePage,SPFileContainer,SPManifestContainer,SPSiteUrl
    Exchange,,annb.pst,annb@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,annb_archive.pst,annb@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,,donh.pst,donh@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,,donh_archive.pst,donh@contoso.onmicrosoft.com,TRUE,,,,,
    Exchange,PSTFiles,pilarp.pst,pilarp@contoso.onmicrosoft.com,FALSE,/,,,,
    Exchange,PSTFiles,pilarp_archive.pst,pilarp@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,tonyk.pst,tonyk@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,tonyk_archive.pst,tonyk@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    Exchange,PSTFiles,zrinkam.pst,zrinkam@contoso.onmicrosoft.com,FALSE,,,,,
    Exchange,PSTFiles,zrinkam_archive.pst,zrinkam@contoso.onmicrosoft.com,TRUE,/ImportedPst,,,,
    ```

    La première ligne ou ligne d’en-tête du fichier CSV répertorie les paramètres qui seront utilisés par le service d’importation pour importer les fichiers PST dans les boîtes aux lettres d’utilisateur. Les noms des paramètres sont séparés par des virgules. Chaque ligne sous la ligne d’en-tête représente les valeurs des paramètres pour l’importation d’un fichier PST dans une boîte aux lettres spécifique. Vous avez besoin d’une ligne pour chaque fichier PST que vous souhaitez importer dans une boîte aux lettres d’utilisateur. Vous pouvez avoir 500 lignes maximum dans le fichier de mappage CSV. Pour importer plus de 500 fichiers PST, vous devez créer plusieurs fichiers de mappage et créer plusieurs tâches d’importation à l’étape 5.

    > [!NOTE]
    > Ne modifiez en aucun cas la ligne d’en-tête, ni les paramètres SharePoint ; ils seront ignorés pendant le processus d’importation des fichiers PST. De plus, n’oubliez pas de remplacer les données d’espace réservé dans le fichier de mappage par les données réelles.

3. Utilisez les informations du tableau suivant pour remplir le fichier CSV avec les informations requises.

    | Paramètre | Description | Exemple |
    |:-----|:-----|:-----|
    | `Workload` <br/> |Indique le service où les données seront importées. Pour importer des fichiers PST dans les boîtes aux lettres d’utilisateur, utilisez `Exchange`.  <br/> | `Exchange` <br/> |
    | `FilePath` <br/> |Indique l’emplacement du dossier dans l’emplacement de stockage Azure dans lequel vous avez chargé les fichiers PST à l’étape 2.  <br/> Si vous n'avez pas inclus un nom de sous-dossier facultatif dans l'URL de SAS dans le paramètre `/Dest:` à l’étape 2, laissez ce paramètre vide dans le fichier CSV. Si vous avez inclus un nom de sous-dossier, indiquez-le dans ce paramètre (voir deuxième exemple). La valeur de ce paramètre est sensible à la casse.  <br/> Dans tous les cas, n'incluez *pas* « ingestiondata » dans la valeur du paramètre `FilePath`.  <br/><br/> **Important :** Le cas du nom du chemin d’accès au fichier doit être identique au cas que vous avez utilisé si vous avez inclus un nom de sous-dossier facultatif dans l’URL SAS dans le champ de destination à l’étape 2. Par exemple, si vous avez utilisé `PSTFiles` pour le nom du sous-dossier à l’étape 2 `pstfiles` dans le paramètre `FilePath` dans le fichier CSV, l’importation du fichier PST échouera. Veillez à utiliser la même casse dans les deux instances.  <br/> |(Laisser vide)  <br/> Ou  <br/>  `PSTFiles` <br/> |
    | `Name` <br/> |Indique le nom du fichier PST qui sera importé dans la boîte aux lettres d’utilisateur. La valeur de ce paramètre est sensible à la casse. Le nom de fichier de chaque fichier PST dans le fichier de mappage d’une tâche d’importation doit être unique. <br/> <br/>**Important :** La casse du nom du fichier PST dans le fichier CSV doit être identique à celle du fichier PST chargé dans l’emplacement de stockage Azure à l’étape 2. Par exemple, si vous utilisez  `annb.pst` dans le  paramètre `Name` du fichier CSV, mais que le nom du fichier PST réel est `AnnB.pst`, l’importation de ce fichier PST échouera. Assurez-vous que le nom du fichier PST dans le fichier CSV utilise la même casse que le fichier PST réel.  <br/> | `annb.pst` <br/> |
    | `Mailbox` <br/> |Indique l’adresse électronique de la boîte aux lettres dans laquelle le fichier PST est importé. Vous ne pouvez pas spécifier un dossier public, car le service d’importation PST ne prend pas en charge l’importation de fichiers PST dans les dossiers publics.  <br/> Pour importer un fichier PST dans une boîte aux lettres inactive, vous devez indiquer le GUID de la boîte aux lettres pour ce paramètre. Pour obtenir ce GUID, exécutez la commande PowerShell suivante dans Exchange Online :  `Get-Mailbox <identity of inactive mailbox> -InactiveMailboxOnly | FL Guid` <br/> <br/>**Remarque :** Parfois, vous pouvez avoir plusieurs boîtes aux lettres avec la même adresse électronique, où une boîte aux lettres est une boîte aux lettres active et l’autre boîte aux lettres est dans un état supprimé (ou inactif). Dans ce cas, vous devez spécifier le GUID de boîte aux lettres pour identifier de façon unique la boîte aux lettres dans laquelle importer le fichier PST. Pour obtenir ce GUID des boîtes aux lettres actives, exécutez la commande PowerShell suivante :  `Get-Mailbox <identity of active mailbox> | FL Guid` Pour obtenir le GUID des boîtes aux lettres supprimées (ou inactives), exécutez cette commande  `Get-Mailbox <identity of soft-deleted or inactive mailbox> -SoftDeletedMailbox | FL Guid`.  <br/> | `annb@contoso.onmicrosoft.com` <br/> Ou  <br/>  `2d7a87fe-d6a2-40cc-8aff-1ebea80d4ae7` <br/> |
    | `IsArchive` <br/> | Indique si vous importez le fichier PST dans la boîte aux lettres d’archivage de l’utilisateur. Il existe deux options :<br/><br/>**FALSE :** importe le fichier PST dans la boîte aux lettres principale de l’utilisateur.  <br/> **TRUE :** importe le fichier PST dans la boîte aux lettres d’archivage de l’utilisateur. Cela implique l’[activation de la boîte aux lettres d’archivage de l’utilisateur](enable-archive-mailboxes.md). <br/><br/>Si vous définissez ce paramètre sur `TRUE` et que la boîte aux lettres d’archivage de l’utilisateur n’est pas activée, l’importation échouera pour cet utilisateur. Si une importation échoue pour un utilisateur (car son archive n’est pas activée et que cette propriété est définie sur `TRUE`), les autres utilisateurs dans le travail d’importation ne seront pas affectés.<br/>  Si vous ne renseignez pas ce paramètre, le fichier PST est importé dans la boîte aux lettres principale de l’utilisateur.  <br/> <br/>**Remarque :** Pour importer un fichier PST dans une boîte aux lettres d’archivage dans le cloud pour un utilisateur dont la boîte aux lettres principale est accessible localement, indiquez `TRUE` pour ce paramètre et indiquez l’adresse de courrier de la boîte aux lettres locale de l’utilisateur pour le paramètre `Mailbox`.  <br/> | `FALSE` <br/> Ou  <br/>  `TRUE` <br/> |
    | `TargetRootFolder` <br/> | Indique le dossier de la boîte aux lettres dans lequel le fichier PST est importé.  <br/> <br/> Si vous ne renseignez pas ce paramètre, le fichier PST est importé dans un nouveau dossier nommé **Importé** situé au niveau racine de la boîte aux lettres (le même niveau que le dossier Boîte de réception et les autres dossiers de boîte aux lettres par défaut).  <br/> <br/> Si vous spécifiez  `/`, les dossiers et les éléments du fichier PST sont importés en haut de la structure des dossiers dans la boîte aux lettres ou l'archive cible. Si un dossier est présent dans la boîte aux lettres cible (par exemple, des dossiers par défaut tels que Boîte de réception, Éléments envoyés et Éléments supprimés), les éléments de ce dossier du fichier PST sont fusionnés dans le dossier existant dans la boîte aux lettres cible. Par exemple, si le fichier PST contient un dossier Boîte de réception, les éléments de ce dossier sont importés dans le dossier Boîte de réception de la boîte aux lettres cible. Les nouveaux dossiers sont créés s’ils n’existent pas dans la structure des dossiers de la boîte aux lettres cible.  <br/><br/>  Si vous spécifiez `/<foldername>`, les éléments et dossiers du fichier PST sont importés directement dans le dossier nommé  *\<foldername\>*. Par exemple, si vous utilisez  `/ImportedPst`, les éléments sont importés dans un dossier nommé **ImportedPst**. Ce dossier se trouve dans la boîte aux lettres de l’utilisateur au même niveau que le dossier boîte de réception.  <br/><br/> **Astuce :** Pensez à réaliser quelques tests pour appréhender ce paramètre afin de déterminer le meilleur emplacement pour le dossier d’importation des fichiers PST.  <br/> |(Laisser vide)  <br/> Ou  <br/>  `/` <br/> Ou  <br/>  `/ImportedPst` <br/> |
    | `ContentCodePage` <br/> |Ce paramètre facultatif indique une valeur numérique que la page de codes doit utiliser pour importer des fichiers PST au format de fichier ANSI. Ce paramètre permet d’importer des fichiers PST à partir d’organisations chinoises, japonaises et coréennes, car ces langues utilisent généralement un jeux de caractères à deux octets (DBCS) pour le codage de caractères. Si ce paramètre n’est pas utilisé pour importer des fichiers PST pour les langues qui utilisent des caractères DBCS pour les noms des dossiers de boîte aux lettres, les noms des dossiers sont souvent déformés une fois qu’ils sont importés.  <br/><br/> Pour obtenir la liste des valeurs prises en charge à utiliser pour ce paramètre, consultez [Identificateurs de page de codes](/windows/win32/intl/code-page-identifiers).  <br/> <br/>**Remarque :** Comme indiqué précédemment, il s’agit d’un paramètre facultatif et vous n’avez pas besoin de l’inclure dans le fichier CSV. Ou vous pouvez également l’inclure et conserver la valeur vide pour une ou plusieurs lignes.  <br/> |(Laisser vide)  <br/> Ou  <br/>  `932` (il s’agit de l’identificateur de page de codes pour le japonais ANSI/OEM)  <br/> |
    | `SPFileContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPManifestContainer` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |
    | `SPSiteUrl` <br/> |Pour l’importation PST, laissez ce paramètre vide.  <br/> |Non applicable  <br/> |

## <a name="step-5-create-a-pst-import-job"></a>Étape 5 : Créer une tâche d’importation PST

L'étape suivante consiste à créer la tâche d'importation PST dans le service d'importation dans Microsoft 365. Comme indiqué précédemment, vous envoyez le fichier de mappage d’importation PST créé à l’étape 4. Une fois la nouvelle tâche créée, Microsoft 365 analyse les données des fichiers PST et vous donne la possibilité de filtrer les données qui sont effectivement importées dans les boîtes aux lettres indiquées dans le fichier de mappage des importations PST (consulter [Étape 6](#step-6-filter-data-and-start-the-pst-import-job)).
  
1. Accédez à <https://compliance.microsoft.com> et connectez-vous à l'aide des informations d'identification d'un compte administrateur dans votre organisation.

2. Dans le volet gauche du Centre de conformité Microsoft 365, cliquez sur **Gouvernance des informations > Importer**.

3. Sous l’onglet **Importer**, cliquez sur l’![Icône Ajouter.](../media/ITPro-EAC-AddIcon.gif)**nouvelle tâche d’importation**.

   > [!NOTE]
   > Vous devez disposer des autorisations appropriées pour accéder à la page **Importer** dans le Centre de conformité Microsoft 365 afin de créer une tâche d’importation. Voir la section **Avant de commencer** pour plus d’informations. 

4. Entrez le nom de la tâche d’importation PST, puis cliquez sur **Suivant**. Utilisez des lettres minuscules, des nombres, des traits d’union et des traits bas. Vous ne pouvez pas utiliser de lettres majuscules ou inclure des espaces dans le nom.

5. Dans la page **Souhaitez-vous charger ou expédier les données ?**, cliquez sur **Charger vos données**, puis cliquez sur **Suivant**.
  
6. À l’étape 4, sur la page **Importer les données**, cliquez sur les cases à cocher **J’ai terminé le téléchargement de mes fichiers** et **J’ai accès au fichier de mappage**, puis cliquez sur **Suivant**.

    ![Cliquez sur les deux cases à cocher à l’étape 4.](../media/9f2427e8-3af2-4e27-95e6-a9f08430d3d8.png)
  
7. Sur la page **Sélectionner le fichier de mappage**, cliquez sur **Sélectionner le fichier de mappage** pour soumettre le fichier de mappage CSV que vous avez créé à l’étape 4.

    ![Cliquez sur Sélectionner le fichier de mappage pour soumettre le fichier CSV que vous avez créé pour la tâche d’importation.](../media/d30b1d73-80bb-491e-a642-a21673d06889.png)
  
8. Lorsque le nom du fichier CSV apparaît dans la liste, **Nom de fichier de mappage**, cliquez sur **Valider** pour vérifier que votre fichier CSV ne contient pas d’erreurs.

    ![Cliquez sur Valider pour rechercher les erreurs dans le fichier CSV.](../media/4680999d-5538-4059-b878-2736a5445037.png)
  
    Le fichier CSV doit être validé avec succès pour créer une tâche d'importation PST. Le nom du fichier passe à la couleur verte une fois qu'il a été validé avec succès. Si la validation échoue, cliquez sur le lien **Afficher le journal**. Un rapport d'erreur de validation est ouvert, avec un message d'erreur pour chaque ligne du fichier qui a échoué.

   > [!NOTE]
   > Comme indiqué précédemment, un fichier de mappage peut comporter un maximum de 500 lignes. La validation échoue si le fichier de mappage contient plus de 500 lignes. Pour importer plus de 500 fichiers PST, vous devez créer plusieurs fichiers de mappage et plusieurs tâches d’importation.

9. Une fois le fichier de mappage validé avec succès, lisez le document sur les conditions générales, puis cochez la case.

10. Cliquez sur **Enregistrer** pour envoyer la tâche, puis cliquez sur **Fermer** une fois la tâche créée avec succès.

    Une page de menu volant d’état s’affiche avec l'état d’**Analyse en cours** et la nouvelle tâche d’importation s’affiche dans la liste de la page **Importer des fichiers PST**.

11. Cliquez sur **Actualiser** ![Icône actualiser.](../media/O365-MDM-Policy-RefreshIcon.gif) pour mettre à jour les informations d’état affichées dans la colonne **Status**. Une fois l’analyse terminée et les données prêtes à être importées, l’état est modifié en **Analyse terminée**.

    Vous pouvez cliquer sur la tâche d’importation pour afficher la page de menu volant d’état qui contient les informations plus détaillées sur la tâche d’importation, telles que l’état de chaque fichier PST répertorié dans le fichier de mappage.

## <a name="step-6-filter-data-and-start-the-pst-import-job"></a>Étape 6 : Filtrer les données et démarrer la tâche d’importation PST

Une fois la tâche d'importation créée à l'étape 5, Microsoft 365 analyse les données des fichiers PST (de manière sûre et sécurisée) en identifiant l'âge des éléments et les différents types de messages inclus dans les fichiers PST. Une fois l’analyse terminée et les données prêtes à être importées, vous avez la possibilité d’importer toutes les données contenues dans les fichiers PST. Vous pouvez également réduire la quantité de données importées en définissant des filtres qui contrôlent les données importées.
  
1. Sous l’onglet **Importer** dans le Centre de conformité Microsoft 365, sélectionnez les tâches d’importation que vous avez créées à l’étape 5, puis cliquez sur **Importer pour Microsoft 365**.
  
   La page **Filtrez vos données** s’affiche. Il contient les insights de données résultant de l’analyse effectuée sur les fichiers PST par Microsoft 365, y compris des informations sur l’âge des données. À ce stade, vous avez la possibilité de filtrer les données qui seront importées ou d’importer toutes les données telles quelles. 

    ![Vous pouvez découper les données dans les fichiers PST ou les importer.](../media/287fc030-99e9-417b-ace7-f64617ea5d4e.png)
  
2. Effectuez l'une des opérations suivantes :

   1. Pour découper les données que vous importez, cliquez sur **Oui, je souhaite les filtrer avant l’importation**.

      Pour obtenir des instructions détaillées sur le filtrage des données dans les fichiers PST, puis le démarrage du travail d’importation, consultez [Filtrer les données lors de l’importation de fichiers PST dans Microsoft 365](filter-data-when-importing-pst-files.md).

      Ou

   2. Pour importer toutes les données des fichiers PST, cliquez sur **Non, je souhaite tout importer,** puis cliquez sur **Suivant**.

3. Si vous avez choisi d’importer toutes les données, cliquez sur **Importer les données** pour démarrer la tâche d’importation. 

   L’état de la tâche d’importation s’affiche dans la page **Importer de fichiers PST**. Cliquez sur l’![ Icone actualiser.](../media/O365-MDM-Policy-RefreshIcon.gif) **Actualiser** pour mettre à jour les informations d’état affichées dans la colonne **Status**. Cliquez sur la tâche d’importation pour afficher la page de menu volant d’état qui affiche des informations sur l’état de chaque fichier PST importé.

## <a name="more-information"></a>Plus d’informations

- Pourquoi importer des fichiers PST dans Microsoft 365

  - C’est un bon moyen d’importer les données de messagerie archivées dans Microsoft 365.

  - L’utilisateur peut accéder aux données à partir de n’importe quel périphérique, car elles sont stockées dans le cloud.

  - Elle aide à répondre aux besoins de conformité de votre organisation en vous permettant d'appliquer les fonctions de conformité de Microsoft 365 aux données des fichiers PST que vous avez importés. Cela inclut :

  - Activation des [boîtes aux lettres d'archivage](enable-archive-mailboxes.md) et de l'[archivage auto-expansif](enable-autoexpanding-archiving.md) pour donner aux utilisateurs un espace de stockage de boîte aux lettres supplémentaire pour stocker les données que vous avez importées.

  - Placement des boîtes aux lettres [en attente de litige](./create-a-litigation-hold.md) pour conserver les données que vous avez importées.

  - Utilisation des [outils eDiscovery](search-for-content.md) de Microsoft pour rechercher les données que vous avez importées.

  - Utilisation des [stratégies de rétention de Microsoft 365](retention.md) pour contrôler la durée de conservation des données importées et l’action à entreprendre à l’expiration de la période de rétention.

  - Recherche dans le [journal d’audit](search-the-audit-log-in-security-and-compliance.md) pour les événements liés aux boîtes aux lettres qui affectent les données que vous avez importées.

  - Importation de données dans les [boîtes aux lettres inactives](inactive-mailboxes-in-office-365.md) pour archiver les données à des fins de conformité. 

  - Utilisation de [stratégies de prévention contre la perte de données](dlp-learn-about-dlp.md) pour empêcher les fuites de données sensibles à l'extérieur de votre organisation.

- Comme expliqué précédemment, le service d’importation Microsoft 365 active le paramètre de conservation (pour une durée indéfinie) après l’importation de fichiers PST dans une boîte aux lettres. Cela signifie que la propriété *RetentionHoldEnabled* est définie sur **True** pour que la stratégie de rétention assignée à la boîte aux lettres ne soit pas traitée. Le propriétaire de la boîte aux lettres a ainsi le temps de gérer les messages nouvellement importés en empêchant une stratégie de suppression ou d’archivage de supprimer ou d’archiver des messages plus anciens. Voici quelques étapes à suivre pour gérer ce blocage de rétention :

  - Après un certain temps, vous pouvez désactiver le blocage de rétention en exécutant la commande **Set-Mailbox-RetentionHoldEnabled $false**. Pour plus d'instructions, consultez [Activer le blocage de rétention d’une boîte aux lettres](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

  - Vous pouvez configurer le blocage de rétention pour qu’il se désactive à une date ultérieure. Pour ce faire, vous exécutez la commande **Set-Mailbox-EndDateForRetentionHold *de date***. Par exemple, en supposant que la date du jour est le 1er juin 2016 et que vous voulez désactiver le blocage de rétention au bout de 30 jours, vous devez exécuter la commande suivante : **Set-Mailbox-EndDateForRetentionHold 01/07/2016**. Dans ce scénario, vous devez laisser la propriété **RetentionHoldEnabled** sur la valeur *True*. Pour plus d’informations, consultez [Set-Mailbox](/powershell/module/exchange/set-mailbox).

  - Vous pouvez modifier les paramètres de stratégie de rétention attribuée à la boîte aux lettres pour que les anciens éléments qui ont été importés ne soient ni supprimés immédiatement, ni déplacés vers la boîte aux lettres d’archivage de l’utilisateur. Par exemple, vous pouvez allonger l’âge de rétention d’une stratégie de suppression ou d’archivage associée à la boîte aux lettres. Dans ce scénario, vous devez désactiver le blocage de rétention sur la boîte aux lettres après la modification des paramètres de la stratégie de rétention. Pour plus d’informations, voir [Configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

### <a name="how-the-import-process-works"></a>Fonctionnement du processus d'importation
  
Vous pouvez utiliser l’option de chargement réseau et le service d’importation Microsoft 365 pour importer en bloc des fichiers PST dans des boîtes aux lettres utilisateurs. Le chargement réseau signifie que vous chargez les fichiers PST dans une zone de stockage temporaire dans le cloud Microsoft. Ensuite, le service d’importation Microsoft 365 copie les fichiers PST de la zone de stockage vers les boîtes aux lettres utilisateurs cibles.
  
Voici une illustration et une description du processus de chargement réseau pour importer des fichiers PST dans des boîtes aux lettres dans Microsoft 365.
  
![Flux de travail du processus de chargement réseau pour importer des fichiers PST dans Microsoft 365.](../media/9e05a19e-1e7a-4f1f-82df-9118f51588c4.png)
  
1. **Télécharger les outils d’importation de fichiers PST et la clé pour l’emplacement de stockage Azure privé :** la première étape consiste à télécharger l'outil de ligne de commande AzCopy et une clé d'accès utilisée pour charger les fichiers PST dans un emplacement de stockage Azure dans le cloud Microsoft. Vous les obtenez à partir de la page **Importer** dans le Centre de conformité Microsoft 365. La clé (appelée clé SAS pour Signature d'accès partagé), vous donne les permissions nécessaires pour charger des fichiers PST dans un emplacement de stockage Azure privé et sécurisé. Cette clé d’accès est propre à votre organisation et empêche l’accès non autorisé à vos fichiers PST après leur chargement dans le cloud Microsoft. L’importation de fichiers PST ne nécessite pas que votre organisation dispose d’un abonnement Azure séparé. 

2. **Charger les fichiers PST dans l’emplacement de stockage Azure :** L’étape suivante consiste à utiliser l’outil azcopy.exe (téléchargé à l’étape 1) pour charger et stocker vos fichiers PST dans un emplacement de stockage Azure qui réside dans le même centre de données Microsoft régional que celui où se trouve votre organisation. Pour les charger, les fichiers PST que vous souhaitez importer doivent se trouver dans un partage de fichiers ou un serveur de fichiers au sein de votre organisation.

    Il existe une étape facultative que vous pouvez effectuer pour afficher la liste des fichiers PST après leur chargement dans l’emplacement de stockage Azure.

3. **Créer un fichier de mappage d’importation de fichiers PST :** une fois que les fichiers PST ont été chargés dans l’emplacement de stockage Azure, l'étape suivante consiste à créer un fichier de valeurs séparées par des virgules (CSV) qui indique les boîtes aux lettres d'utilisateur dans lesquelles les fichiers PST seront importés, notez qu'un fichier PST peut être importé dans la boîte aux lettres principale d'un utilisateur ou dans sa boîte aux lettres d'archivage. Le service d’importation Microsoft 365 utilise les informations contenues dans le fichier CSV pour importer les fichiers PST.

4. **Créer une tâche d’importation de fichiers PST :** l’étape suivante consiste à créer une tâche d’importation de fichiers PST sur la page **Importer des fichiers PST** dans le Centre de conformité Microsoft 365 et à envoyer le fichier de mappage d’importation PST créé à l’étape précédente. Une fois la tâche d'importation créée, Microsoft 365 analyse les données des fichiers PST et vous donne la possibilité de définir des filtres qui contrôlent les données réellement importées dans les boîtes aux lettres spécifiées dans le fichier d'importation PST. 

5. **Filtrer les données PST qui seront importées dans les boîtes aux lettres :** après la création et le démarrage de la tâche d'importation, Microsoft 365 analyse les données des fichiers PST (de manière sûre et sécurisée) en identifiant l'âge des éléments et les différents types de messages inclus dans les fichiers PST. Une fois l’analyse terminée et les données prêtes à être importées, vous avez la possibilité d’importer toutes les données contenues dans les fichiers PST. Vous pouvez également réduire la quantité de données importées en définissant des filtres qui contrôlent les données importées.

6. **Lancer la tâche d’importation de fichiers PST** : une fois la tâche d’importation lancée, Microsoft 365 utilise les informations du fichier de mappage d’importation de fichiers PST pour importer les fichiers PST à partir de l’emplacement de stockage Azure vers les boîtes aux lettres des utilisateurs. Les informations relatives à l’état de la tâche d’importation (y compris les informations relatives à chaque fichier PST importé) s’affichent sur la page **Importer des fichiers PST** du Centre de conformité Microsoft 365. Une fois la tâche d’importation terminée, l’état de la tâche est défini sur **Terminé**.
