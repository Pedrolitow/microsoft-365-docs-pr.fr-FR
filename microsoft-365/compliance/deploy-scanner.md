---
title: En savoir plus sur le scanneur Protection des données Microsoft Purview
f1.keywords: ''
ms.author: libarson
author: libarson
manager: aashishr
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- purview-compliance
- tier3
description: Découvrez comment le scanneur de Protection des données Microsoft Purview peut découvrir, classifier et protéger des fichiers sur des magasins de données.
ms.openlocfilehash: 624abb6e989612098c7ac47eb2ef15e48af1479b
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68647598"
---
# <a name="learn-about-the-information-protection-scanner"></a>En savoir plus sur le scanneur de protection des informations

Utilisez les informations de cette section pour en savoir plus sur le scanneur de protection des informations Microsoft Purview, puis comment installer, configurer, exécuter et, si nécessaire, résoudre les problèmes.

Le scanneur s’exécute en tant que service sur Windows Server et vous permet de découvrir, classifier et protéger des fichiers sur les magasins de données suivants :

- **Chemins UNC pour les partages** réseau qui utilisent les protocoles SMB ou NFS (préversion).

- **Bibliothèques de documents et dossiers SharePoint** pour SharePoint Server 2019 via SharePoint Server 2013.

Pour classifier et protéger vos fichiers, le scanneur utilise des [étiquettes de confidentialité](sensitivity-labels.md) configurées dans le portail de conformité Microsoft Purview.

## <a name="overview-of-the-scanner"></a>Vue d’ensemble du scanneur

Le scanneur de protection des informations peut inspecter tous les fichiers que Windows peut indexer. Si vous avez configuré des étiquettes de confidentialité pour appliquer la classification automatique, le scanneur peut étiqueter les fichiers découverts pour appliquer cette classification et éventuellement appliquer ou supprimer la protection. 

L’image suivante montre l’architecture du scanneur, où le scanneur découvre des fichiers sur vos serveurs locaux et SharePoint.

:::image type="content" source="../media/ul-scanner-arch.png" alt-text="architecture du scanneur Protection des données Microsoft Purview":::

Pour inspecter vos fichiers, le scanneur utilise des IFilters installés sur l’ordinateur. Pour déterminer si les fichiers doivent être étiquetés, le scanneur utilise des types d’informations sensibles et la détection de modèle, ou des modèles d’expression régulière.

Le scanneur utilise le client Azure Information Protection et peut classifier et protéger les mêmes types de fichiers que le client. Pour plus d’informations, consultez [Les types de fichiers pris en charge par le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types).

Effectuez l’une des opérations suivantes pour configurer vos analyses en fonction des besoins :

- **Exécutez le scanneur en mode de découverte uniquement** pour créer des rapports qui vérifient ce qui se passe lorsque vos fichiers sont étiquetés.
- **Exécutez le scanneur pour découvrir les fichiers avec des informations sensibles**, sans configurer d’étiquettes qui appliquent la classification automatique.
- **Exécutez le scanneur automatiquement** pour appliquer des étiquettes comme configuré. 
- **Définissez une liste de types de fichiers** pour spécifier des fichiers spécifiques à analyser ou à exclure.

> [!NOTE]
> Le scanneur ne découvre pas et ne l’étiquette pas en temps réel. Il analyse systématiquement les fichiers des magasins de données que vous spécifiez. Configurez ce cycle pour qu’il s’exécute une seule fois ou à plusieurs reprises.

> [!TIP]
> Le scanneur prend en charge les clusters de scanneur avec plusieurs nœuds, ce qui permet à votre organisation d’effectuer un scale-out, d’obtenir des temps d’analyse plus rapides et une étendue plus large. 
> 
> Déployez plusieurs nœuds dès le début, ou commencez par un cluster à un seul nœud et ajoutez des nœuds supplémentaires ultérieurement à mesure que vous augmentez. Déployez plusieurs nœuds en utilisant le même nom de cluster et la même base de données pour l’applet de commande **Install-AIPScanner** .
> 

## <a name="the-scanning-process"></a>Processus d’analyse

Lors de l’analyse des fichiers, le scanneur de protection des informations effectue les étapes suivantes :

[1. Déterminer si les fichiers sont inclus ou exclus pour l’analyse](#1-determine-whether-files-are-included-or-excluded-for-scanning)

[2. Inspecter et étiqueter les fichiers](#2-inspect-and-label-files)

[3. Étiqueter les fichiers qui ne peuvent pas être inspectés](#3-label-files-that-cant-be-inspected) 

Pour plus d’informations, consultez [Fichiers non étiquetés par le scanneur](#files-not-labeled-by-the-scanner).

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. Déterminer si les fichiers sont inclus ou exclus pour l’analyse 

Le scanneur ignore automatiquement les fichiers exclus de la classification et de la protection, tels que les fichiers exécutables et les fichiers système. Pour plus d’informations, consultez [Types de fichiers exclus de la classification et de la protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types#file-types-excluded-from-classification-and-protection).

Le scanneur prend également en compte les listes de fichiers explicitement définies pour analyser ou exclure de l’analyse. Les listes de fichiers s’appliquent par défaut à tous les référentiels de données et peuvent également être définies pour des référentiels spécifiques uniquement.

Pour définir des listes de fichiers à des fins d’analyse ou d’exclusion, utilisez les **types de fichiers pour analyser** le paramètre dans le travail d’analyse de contenu. Par exemple :

![Configurer les types de fichiers à analyser dans le portail de conformité Purview](../media/scanner-file-types-purview.png)

Pour plus d’informations, consultez [Déploiement du scanneur pour classifier et protéger automatiquement les fichiers](deploy-scanner-configure-install.md).

### <a name="2-inspect-and-label-files"></a>2. Inspecter et étiqueter les fichiers

Après avoir identifié les fichiers exclus, le scanneur de protection des informations filtre à nouveau pour identifier les fichiers pris en charge pour l’inspection.

Ces filtres sont les mêmes que ceux utilisés par le système d’exploitation pour la recherche et l’indexation Windows, et ne nécessitent aucune configuration supplémentaire. Windows IFilter est également utilisé pour analyser les types de fichiers utilisés par Word, Excel et PowerPoint, ainsi que pour les documents PDF et les fichiers texte.

Pour obtenir la liste complète des types de fichiers pris en charge pour l’inspection et d’autres instructions pour la configuration des filtres afin d’inclure des fichiers .zip et .tiff, consultez [les types de fichiers pris en charge pour l’inspection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types#file-types-supported-for-inspection).

Après inspection, les types de fichiers pris en charge sont étiquetés à l’aide des conditions spécifiées pour vos étiquettes. Si vous utilisez le mode de découverte, ces fichiers peuvent être signalés comme contenant les conditions spécifiées pour vos étiquettes ou signalés comme contenant tous les types d’informations sensibles connus.

#### <a name="stopped-scanner-processes"></a>Processus de scanneur arrêtés

Si le scanneur s’arrête et n’effectue pas d’analyse pour un grand nombre de fichiers dans votre référentiel, vous devrez peut-être augmenter le nombre de ports dynamiques pour le système d’exploitation hébergeant les fichiers.

Par exemple, le renforcement du serveur pour SharePoint est l’une des raisons pour lesquelles le scanneur dépasse le nombre de connexions réseau autorisées et s’arrête donc.

Pour vérifier si le renforcement du serveur pour SharePoint est la cause de l’arrêt du scanneur, recherchez le message d’erreur suivant dans les journaux du scanneur à **%localappdata%\Microsoft\MSIP\Logs\MSIPScanner.iplog** (plusieurs journaux sont compressés dans un fichier zip) :

`Unable to connect to the remote server ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted IP:port`

Pour plus d’informations sur la façon d’afficher la plage de ports actuelle et de l’augmenter si nécessaire, consultez [Paramètres qui peuvent être modifiés pour améliorer les performances réseau](/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

> [!TIP]
> Pour les grandes batteries de serveurs SharePoint, vous devrez peut-être augmenter le seuil d’affichage de liste, qui a une valeur par défaut de **5 000**.
>
> Pour plus d’informations, consultez [Gérer les grandes listes et bibliothèques dans SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).
>

### <a name="3-label-files-that-cant-be-inspected"></a>3. Étiqueter les fichiers qui ne peuvent pas être inspectés

Pour tous les types de fichiers qui ne peuvent pas être inspectés, le scanneur applique l’étiquette par défaut à partir de sa stratégie d’étiquette de confidentialité ou de l’étiquette par défaut configurée pour le scanneur.

### <a name="files-not-labeled-by-the-scanner"></a>Fichiers non étiquetés par le scanneur
Le scanneur ne peut pas étiqueter les fichiers dans les circonstances suivantes :

- Lorsque l’étiquette applique la classification, mais pas la protection, et que le type de fichier ne prend pas en charge la classification uniquement par le client. Pour plus d’informations, consultez [les types de fichiers pris en charge pour la classification uniquement](/azure/information-protection/rms-client/clientv2-admin-guide-file-types#file-types-supported-for-classification-only).

- Lorsque l’étiquette applique la classification et la protection, mais que le scanneur ne prend pas en charge le type de fichier.
  
    Par défaut, le scanneur protège uniquement les types de fichiers Office et les fichiers PDF lorsqu’ils sont protégés à l’aide de la norme ISO pour le chiffrement PDF. 

    D’autres types de fichiers peuvent être ajoutés pour la protection lorsque vous [modifiez les types de fichiers à protéger](deploy-scanner-configure-install.md#change-which-file-types-to-protect).

**Exemple** : Après avoir inspecté .txt fichiers, le scanneur ne peut pas appliquer une étiquette configurée uniquement pour la classification, car le type de fichier .txt ne prend pas en charge la classification uniquement. 

Toutefois, si l’étiquette est configurée pour la classification et la protection, et que le type de fichier .txt est inclus pour le scanneur à protéger, le scanneur peut étiqueter le fichier.

## <a name="next-steps"></a>Prochaines étapes

Pour plus d’informations sur le déploiement du scanneur, consultez les articles suivants :

- [Conditions préalables au déploiement du scanneur](deploy-scanner-prereqs.md)
- [Configuration et installation du scanneur](deploy-scanner-configure-install.md)
- [Exécution d’analyses à l’aide du scanneur](deploy-scanner-manage.md)

**Pour plus d’informations** :

- [Regardez notre vidéo de démonstration de bout en bout du scanneur !](https://www.youtube.com/watch?v=f1gy1KalSts) Regardez un examen pas à pas de l’architecture, de l’architecture, de la recommandation, de l’installation et de la configuration du scanneur.

- Consultez notre blog sur les meilleures pratiques pour le scanneur : [Meilleures pratiques pour le déploiement et l’utilisation du scanneur UL AIP](https://aka.ms/AIPScannerBestPractices)

- Vous vous intéressez à la façon dont l’équipe d’ingénierie et d’opérations core Services de Microsoft a implémenté ce scanneur ?  Lisez l’étude de cas technique : [Automatisation de la protection des données avec Azure Information Protection scanneur](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vous pouvez également utiliser PowerShell pour classifier et protéger de manière interactive les fichiers de votre ordinateur de bureau. Pour plus d’informations sur ce problème et d’autres scénarios qui utilisent PowerShell, consultez [Utilisation de PowerShell avec le client d’étiquetage unifié Azure Information Protection](./
- .md).
