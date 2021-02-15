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
description: Découvrez comment utiliser la correction des erreurs pour corriger les problèmes de données dans Advanced eDiscovery qui pourraient empêcher un traitement correct du contenu.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c6ef1076e44fca0d060d766fc85a435550c40059
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49750797"
---
# <a name="error-remediation-when-processing-data"></a>Correction d’erreur lors du traitement des données

La correction des erreurs permet aux administrateurs eDiscovery de corriger les problèmes de données qui empêchent Advanced eDiscovery de traiter correctement le contenu. Par exemple, les fichiers protégés par mot de passe ne peuvent pas être traitées, car ils sont verrouillés ou chiffrés. À l’aide de la correction des erreurs, les administrateurs eDiscovery peuvent télécharger des fichiers avec ces erreurs, supprimer la protection par mot de passe, puis télécharger les fichiers corrigés.

Utilisez le flux de travail suivant pour corriger les fichiers avec des erreurs dans les cas Advanced eDiscovery.

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>Créer une session de correction des erreurs pour corriger les fichiers avec des erreurs de traitement

>[!NOTE]
>Si l’Assistant Correction des erreurs est fermé à tout moment au cours  de la procédure suivante,  vous pouvez revenir à la session de correction d’erreur à partir de l’onglet Traitement en sélectionnant **Corrections** dans le menu déroulant Affichage.

1. Sous **l’onglet** Traitement du cas Advanced eDiscovery, sélectionnez Erreurs dans le menu déroulant  Affichage, puis sélectionnez un jeu à réviser ou l’intégralité du cas dans le menu déroulant Étendue.   Cette section affiche toutes les erreurs provenant du cas ou de l’erreur d’un jeu à réviser spécifique.

   ![Correction des erreurs](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Sélectionnez les erreurs que vous souhaitez corriger en cliquant sur la bouton d’radio en haut du type d’erreur ou du type de fichier.  Dans l’exemple suivant, nous remédions à un fichier protégé par mot de passe.

3. Cliquez sur **Nouvelle correction d’erreur.**

    Le flux de travail de correction des erreurs commence par une phase de préparation dans laquelle les fichiers avec des erreurs sont copiés dans un emplacement de stockage Azure fourni par Microsoft afin que vous pouvez les télécharger sur votre ordinateur local pour corriger.

    ![Préparation de la correction des erreurs](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Une fois la préparation terminée, cliquez sur **Suivant : Télécharger les fichiers** pour continuer le téléchargement.

    ![Télécharger des fichiers](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Pour télécharger des fichiers, spécifiez le **Chemin d’accès destination pour le téléchargement**. Il s'agit d'un chemin d'accès au dossier parent sur votre ordinateur local où le fichier sera téléchargé.  Le chemin d’accès par défaut, %USERPROFILE%\Downloads\errors, pointe vers le dossier de téléchargements de l’utilisateur connecté. Vous pouvez modifier ce chemin d’accès si vous le souhaitez. Si vous le modifiez, nous vous recommandons d’utiliser un chemin d’accès au fichier local pour de meilleures performances. N’utilisez pas de chemin d’accès réseau distant. Par exemple, vous pouvez utiliser le chemin **d’accès C:\Remediation**. 

   Le chemin d’accès au dossier parent est automatiquement ajouté à la commande AzCopy (en tant que valeur du **paramètre /Dest).**

6. Copiez la commande prédéfinie en cliquant sur **Copier dans le presse-papiers**. Ouvrez une invite de commandes Windows, collez la commande AzCopy, puis appuyez sur **Entrée**.  

    ![Préparer la correction des erreurs](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)    

    > [!NOTE]
    > Vous devez utiliser AzCopy v8.1 pour utiliser correctement la commande fournie dans la page Télécharger **les fichiers.** Vous devez également utiliser AzCopy v8.1 pour télécharger les fichiers à l’étape 10. Pour installer cette version d’AzCopy, voir Transférer des données avec [AzCopy v8.1 sur Windows.](https://docs.microsoft.com/previous-versions/azure/storage/storage-use-azcopy) Si la commande AzCopy fournie échoue, consultez Résoudre les problèmes [d’AzCopy dans Advanced eDiscovery](troubleshooting-azcopy.md).

    Les fichiers que vous avez sélectionnés sont téléchargés à l’emplacement que vous avez spécifié à l’étape 5. Dans le dossier parent (par exemple, **C:\Remediation**), la structure de sous-dossiers suivante est créée automatiquement :

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *Le sous-dossier 1* est nommé avec l’ID du cas ou du jeu à réviser, en fonction de l’étendue que vous avez sélectionnée à l’étape 1.

    - *Sous-dossier 2* se nomme avec l’ID de fichier du fichier téléchargé.

    - Le fichier téléchargé se trouve dans *Sous-dossier 2* et est également nommé avec l’ID de fichier.

    Voici un exemple du chemin d’accès au dossier et du nom du fichier d’erreur créés lorsque les éléments sont téléchargés dans le dossier parent **C:\Remediation** :

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Si plusieurs fichiers sont téléchargés, chacun d’eux est téléchargé vers un sous-dossier nommé avec l’ID de fichier.

    > [!IMPORTANT]
    > Lorsque vous chargez des fichiers aux étapes 9 et 10, les fichiers corrigés doivent avoir le même nom de fichier et se trouver dans la même structure de sous-dossiers. Les noms de sous-dossier et de fichier sont utilisés pour associer le fichier corrigé au fichier d’erreur d’origine. Si la structure de dossiers ou les noms de fichiers sont modifiés, vous recevrez l’erreur suivante `Cannot apply Error Remediation to the current Workingset` : Pour éviter tout problème, nous vous recommandons de conserver les fichiers corrigés dans la même structure de sous-dossiers et de dossiers parents.

7. Après avoir téléchargé les fichiers, vous pouvez les corriger à l’aide d’un outil approprié. Pour les fichiers protégés par mot de passe, vous pouvez utiliser plusieurs outils de déchiffrage de mot de passe. Si vous connaissez les mots de passe des fichiers, vous pouvez les ouvrir et supprimer la protection par mot de passe.

8. Revenir à Advanced eDiscovery et à l’Assistant de correction des erreurs, puis cliquez sur **Suivant : Charger des fichiers**.  Cette opération vous permet de passer à la page suivante dans laquelle vous pouvez maintenant télécharger les fichiers.

    ![Télécharger des fichiers](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Spécifiez le dossier parent où se trouvent les fichiers corrigés dans la zone de texte **Chemin d’accès à l’emplacement des fichiers**. Là encore, le dossier parent doit avoir la même structure de sous-dossiers que celle créée lors du téléchargement des fichiers.

    Le chemin d’accès au dossier parent est automatiquement ajouté à la commande AzCopy (en tant que valeur du **paramètre /Source).**

10. Copiez la commande prédéfinie en cliquant sur **Copier dans le presse-papiers**. Ouvrez une invite de commandes Windows, collez la commande AzCopy, puis appuyez sur **Entrée**. charger les fichiers.

    ![Résultats du chargement réussi des fichiers corrigés dans Azcopy](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. Après avoir exécuté la commande AzCopy, cliquez sur **Suivant : Traiter les fichiers**.

    Une fois le traitement terminé, vous pouvez passer au jeu à réviser et afficher les fichiers corrigés. 

## <a name="remediating-errors-in-container-files"></a>Correction des erreurs dans les fichiers conteneur

Dans les situations où le contenu d’un fichier conteneur (tel qu’un fichier .zip) ne peut pas être extrait par Advanced eDiscovery, les conteneurs peuvent être téléchargés et le contenu étendu dans le dossier dans lequel réside le conteneur d’origine. Les fichiers développés sont attribués au conteneur parent comme s’il était initialement développé par Advanced eDiscovery. Le processus fonctionne comme décrit ci-dessus, à l’exception du téléchargement d’un fichier unique en tant que fichier de remplacement.  Lorsque vous chargez des fichiers corrigés, n’incluez pas le fichier conteneur d’origine.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Correction des erreurs en chargeant le texte extrait

Il est parfois impossible de corriger un fichier au format natif que Advanced eDiscovery peut interpréter. Mais vous pouvez remplacer le fichier d’origine par un fichier texte qui contient le texte d’origine du fichier natif (dans un processus appelé *superposition de texte).* Pour ce faire, suivez les étapes décrites dans cet article, mais au lieu de corriger le fichier d’origine dans le format natif, vous créez un fichier texte qui contient le texte extrait du fichier d’origine, puis téléchargez le fichier texte à l’aide du nom de fichier d’origine qui est suivi d’un suffixe .txt. Par exemple, vous téléchargez un fichier pendant la correction des erreurs avec le nom de fichier 335850cc-6602-4af0-acfa-1d14d9128ca2.abc. Vous ouvrez le fichier dans l’application native, copiez le texte, puis collez-le dans un nouveau fichier nommé 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt. Lorsque vous faites cela, veillez à supprimer le fichier d’origine au format natif de l’emplacement du fichier corrigé sur votre ordinateur local avant de télécharger le fichier texte corrigé dans Advanced eDiscovery.

## <a name="what-happens-when-files-are-remediated"></a>Que se passe-t-il lorsque des fichiers sont corrigés ?

Lorsque des fichiers corrigés sont chargés, les métadonnées d’origine sont conservées à l’exception des champs suivants : 

- ExtractedTextSize
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Texte
- WordCount
- WorkingsetId

Pour obtenir une définition de tous les champs de métadonnées dans Advanced eDiscovery, voir Champs de [métadonnées de document.](document-metadata-fields-in-advanced-ediscovery.md)
