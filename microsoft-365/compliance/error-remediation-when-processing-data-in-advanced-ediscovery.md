---
title: Correction d’erreur lors du traitement des données
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: ''
ms.openlocfilehash: 5421ba811e401bdd191aee0ddbff21a1286dc9fe
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42074571"
---
# <a name="error-remediation-when-processing-data"></a>Correction d’erreur lors du traitement des données

La correction des erreurs permet aux administrateurs eDiscovery de rectifier les problèmes de données qui empêchent la découverte électronique avancée de traiter correctement le contenu. Par exemple, les fichiers protégés par mot de passe ne peuvent pas être traités car les fichiers sont verrouillés ou chiffrés. À l’aide de la correction des erreurs, les administrateurs eDiscovery peuvent télécharger des fichiers avec de telles erreurs, supprimer la protection par mot de passe, puis télécharger les fichiers corrigés.

Utilisez le flux de travail suivant pour corriger les fichiers avec des erreurs dans les cas avancés de découverte électronique.

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>Créer une session d’erreur de correction pour corriger les fichiers avec des erreurs de traitement

>[!NOTE]
>Si l’Assistant de correction d’erreur est fermé à tout moment au cours de la procédure suivante, vous pouvez revenir à la session de correction d’erreur à partir de l’onglet **traitement** en sélectionnant **corrections** dans le menu déroulant **vue** .

1. Sous l’onglet **traitement** dans le cas avancé eDiscovery, sélectionnez **Erreurs** dans le menu déroulant **affichage** , puis sélectionnez un jeu de révision ou l’ensemble de la casse dans le menu déroulant **étendue** . Cette section affiche toutes les erreurs provenant du cas ou de l’erreur d’un jeu de réexamen spécifique.

   ![Correction des erreurs](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Sélectionnez les erreurs que vous souhaitez corriger en cliquant sur la case d’option en regard du type d’erreur ou du type de fichier.  Dans l’exemple suivant, nous effectuons la correction d’un fichier protégé par mot de passe.

3. Cliquez sur **nouvelle erreur de correction**.

    Le flux de travail de correction d’erreur commence par une phase de préparation où les fichiers contenant des erreurs sont copiés vers un emplacement de stockage Azure fourni par Microsoft afin que vous puissiez les télécharger sur votre ordinateur local pour résoudre les problèmes.

    ![Préparation de la correction des erreurs](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Une fois la préparation terminée, cliquez sur **suivant : Télécharger les fichiers** pour continuer le téléchargement.

    ![Télécharger des fichiers](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Pour télécharger des fichiers, spécifiez le **chemin de destination pour le téléchargement**. Il s’agit d’un chemin d’accès au dossier parent sur votre ordinateur local où le fichier sera téléchargé.  Le chemin d’accès par défaut,%USERPROFILE%\Downloads\errors, pointe vers le dossier downloads de l’utilisateur connecté. Vous pouvez modifier ce chemin si vous le souhaitez. Si vous le modifiez, nous vous recommandons d’utiliser un chemin d’accès local pour obtenir les meilleures performances. N’utilisez pas de chemin d’accès réseau distant. Par exemple, vous pouvez utiliser le chemin d’accès **C:\Remediation**. 

   Le chemin d’accès au dossier parent est automatiquement ajouté à la commande AzCopy (en tant que valeur du paramètre **/dest** ).

6. Copiez la commande prédéfinie en cliquant sur **copier dans le presse-papiers**. Ouvrez une invite de commandes Windows, collez la commande AzCopy, puis appuyez sur **entrée**.  

    ![Préparer la correction des erreurs](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)    

    > [!NOTE]
    > Vous devez utiliser AzCopy v 8.1 pour utiliser la commande fournie sur la page Télécharger les **fichiers** . Vous devez également utiliser AzCopy v 8.1 pour télécharger les fichiers à l’étape 10. Pour installer cette version de AzCopy, consultez [la rubrique transférer des données avec le AzCopy v 8.1 sous Windows](https://docs.microsoft.com/previous-versions/azure/storage/storage-use-azcopy). Si la commande AzCopy fournie échoue, reportez-vous à la rubrique [Troubleshoot AzCopy in Advanced eDiscovery](troubleshooting-azcopy.md).

    Les fichiers que vous avez sélectionnés sont téléchargés à l’emplacement que vous avez spécifié à l’étape 5. Dans le dossier parent (par exemple, **C:\Remediation**), la structure de sous-dossiers suivante est créée automatiquement :

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - Le *sous-dossier 1* est nommé avec l’ID du cas ou de l’ensemble de révision, en fonction de l’étendue que vous avez sélectionnée à l’étape 1.

    - Le *sous-dossier 2* est nommé avec l’ID de fichier du fichier téléchargé

    - Le fichier téléchargé se trouve dans le *sous-dossier 2* et est également nommé avec l’ID de fichier.

    Voici un exemple de chemin d’accès de dossier et de nom de fichier d’erreur qui est créé lorsque des éléments sont téléchargés dans le dossier parent **C:\Remediation** :

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Si plusieurs fichiers sont téléchargés, chacun d’entre eux est téléchargé dans un sous-dossier nommé avec l’ID de fichier.

    > [!IMPORTANT]
    > Lorsque vous chargez des fichiers à l’étape 9 et à l’étape 10, les fichiers corrigés doivent avoir le même nom de fichier et se trouver dans la même structure de sous-dossiers. Les noms de fichier et de sous-dossier sont utilisés pour associer le fichier corrigé au fichier d’erreur d’origine. Si la structure de dossiers ou les noms de fichiers sont modifiés, vous recevez l’erreur `Cannot apply Error Remediation to the current Workingset`suivante :. Pour éviter tout problème, nous vous recommandons de conserver les fichiers corrigés dans le même dossier parent et la même structure de sous-dossiers.

7. Après avoir téléchargé les fichiers, vous pouvez les corriger à l’aide d’un outil approprié. Pour les fichiers protégés par mot de passe, il existe plusieurs outils de craquage de mot de passe que vous pouvez utiliser. Si vous connaissiez les mots de passe des fichiers, vous pouvez les ouvrir et supprimer la protection par mot de passe.

8. Revenez à Advanced eDiscovery et à l’Assistant de correction des erreurs, puis cliquez sur **suivant : charger les fichiers**.  Cette action passe à la page suivante, dans laquelle vous pouvez à présent télécharger les fichiers.

    ![Charger des fichiers](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Spécifiez le dossier parent dans lequel se trouvent les fichiers corrigés dans la zone **de texte chemin d’accès à l’emplacement des fichiers** . Une fois encore, le dossier parent doit avoir la même structure de sous-dossiers que celle qui a été créée lorsque vous avez téléchargé les fichiers.

    Le chemin d’accès au dossier parent est automatiquement ajouté à la commande AzCopy (en tant que valeur du paramètre **/source** ).

10. Copiez la commande prédéfinie en cliquant sur **copier dans le presse-papiers**. Ouvrez une invite de commandes Windows, collez la commande AzCopy, puis appuyez sur **entrée**. Téléchargez les fichiers.

    ![ff2ff691-629f-4065-9b37-5333f937daf6. png](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. Après avoir exécuté la commande AzCopy, cliquez sur **suivant : process files**.

    Une fois le traitement terminé, vous pouvez accéder à la vue d’ensemble et afficher les fichiers corrigés. 

## <a name="remediating-errors-in-container-files"></a>Correction des erreurs dans les fichiers conteneur

Lorsque le contenu d’un fichier de conteneur (par exemple, un fichier. zip) ne peut pas être extrait par Advanced eDiscovery, les conteneurs peuvent être téléchargés et le contenu doit être développé dans le même dossier que le conteneur d’origine. Les fichiers étendus sont attribués au conteneur parent comme s’ils avaient été développés à l’origine par Advanced eDiscovery. Le processus fonctionne comme décrit ci-dessus, à l’exception du téléchargement d’un fichier unique en tant que fichier de remplacement.  Lorsque vous téléchargez des fichiers corrigés, n’incluez pas le fichier de conteneur d’origine.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Correction des erreurs en chargeant le texte extrait

Parfois, il n’est pas possible de convertir un fichier au format natif que Advanced eDiscovery peut interpréter. Toutefois, vous pouvez remplacer le fichier d’origine par un fichier texte qui contient le texte d’origine du fichier natif (dans un processus appelé *superposition de texte*). Pour ce faire, suivez les étapes décrites dans cet article, mais au lieu de corriger le fichier d’origine au format natif, créez un fichier texte contenant le texte extrait du fichier d’origine, puis téléchargez le fichier texte à l’aide du nom de fichier d’origine ajouté avec un suffixe. txt. Par exemple, vous téléchargez un fichier lors de la correction des erreurs avec le nom de fichier 335850cc-6602-4AF0-ACFA-1d14d9128ca2. ABC. Ouvrez le fichier dans l’application native, copiez le texte, puis collez-le dans un nouveau fichier nommé 335850cc-6602-4AF0-ACFA-1d14d9128ca2. ABC. txt. Lorsque vous effectuez cette opération, veillez à supprimer le fichier d’origine dans le format natif de l’emplacement des fichiers corrigé sur votre ordinateur local avant de télécharger le fichier texte corrigé vers Advanced eDiscovery.

## <a name="what-happens-when-files-are-remediated"></a>Que se passe-t-il lorsque les fichiers sont convertis ?

Lorsque les fichiers résolus sont téléchargés, les métadonnées d’origine sont conservées, à l’exception des champs suivants : 

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Texte
- WordCount
- WorkingsetId

Pour obtenir une définition de tous les champs de métadonnées dans Advanced eDiscovery, consultez la rubrique [document Metadata Fields](document-metadata-fields.md).
