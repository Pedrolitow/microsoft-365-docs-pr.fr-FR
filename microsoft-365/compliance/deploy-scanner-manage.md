---
title: Exécution du scanneur Protection des données Microsoft Purview
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
description: Instructions d’exécution du scanneur à partir de Protection des données Microsoft Purview pour découvrir, classifier et protéger des fichiers sur des magasins de données.
ms.openlocfilehash: e1e8ab8fcfe2e156d2602a2c5d72511ebf769040
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68631290"
---
# <a name="running-the-information-protection-scanner"></a>Exécution du scanneur de protection des informations

Une fois que vous avez confirmé la [configuration système requise](deploy-scanner-prereqs.md) et [configuré et installé votre scanneur](deploy-scanner-configure-install.md), [exécutez une analyse de découverte](#run-a-discovery-cycle-and-view-reports-for-the-scanner) pour commencer.

Utilisez d’autres étapes détaillées ci-dessous pour gérer vos analyses à l’avenir.

- [Arrêter une analyse](#stopping-a-scan)
- [Rescanning files](#rescanning-files)

Pour plus d’informations, consultez [En savoir plus sur le scanneur Protection des données Microsoft Purview](deploy-scanner.md).

> [!TIP]
> Bien que la plupart des clients effectuent ces procédures dans le portail d’administration, vous devrez peut-être travailler uniquement dans PowerShell.
>
> Par exemple, si vous travaillez dans un environnement sans accès à la Portail Azure, comme les serveurs de [scanneur Azure China 21Vianet](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection#manage-azure-information-protection-content-scan-jobs), authentifiez-vous auprès du module [PowerShell AzureInformationProtection](/powershell/module/azureinformationprotection), puis suivez les instructions de cet article pour PowerShell uniquement.
>
## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Exécuter un cycle de découverte et afficher les rapports pour le scanneur

Utilisez la procédure suivante après avoir [configuré et installé votre scanneur](deploy-scanner-configure-install.md) pour obtenir une compréhension initiale de votre contenu.

Effectuez à nouveau ces étapes en fonction des besoins lorsque votre contenu change.

1. Démarrez une analyse sur votre travail d’analyse de contenu.

    Effectuez l’une des opérations suivantes pour démarrer un travail d’analyse de contenu :

    - **Utilisez la portail de conformité Microsoft Purview.**  Dans le volet **Analyseur de protection des informations - Tâches d’analyse** de contenu, sélectionnez vos travaux d’analyse de contenu, puis sélectionnez l’option **Analyser maintenant** . L’option **Analyser maintenant** n’apparaît qu’une fois qu’un travail d’analyse de contenu est sélectionné. 
        
    - **Utilisez une commande PowerShell.** Exécutez cette opération `Start-AIPScan` pour démarrer l’analyse.

1. Attendez que le scanneur termine son cycle. L’analyse se termine lorsque le scanneur a analysé tous les fichiers des magasins de données spécifiés.

    Effectuez l’une des opérations suivantes pour surveiller la progression du scanneur :

    - **Utilisez la portail de conformité Microsoft Purview.**  Dans le volet **Analyseur information - Tâches d’analyse de contenu** , sélectionnez **Actualiser**.

        Attendez que vous voyiez les valeurs de la colonne **LAST SCAN RESULTS** et de la colonne **LAST SCAN (END TIME).**
        
    - **Utilisez une commande PowerShell.** Exécutez cette commande `Get-AIPScannerStatus` pour surveiller le changement d’état.

1. Une fois l’analyse terminée, passez en revue les rapports stockés dans le **% répertoire *localappdata*%\Microsoft\MSIP\Scanner\Reports**.

    - Les fichiers récapitulatifs .txt incluent le temps nécessaire à l’analyse, le nombre de fichiers analysés et le nombre de fichiers correspondant aux types d’informations.

    - Les fichiers .csv ont plus de détails pour chaque fichier. Ce dossier stocke jusqu’à 60 rapports pour chaque cycle d’analyse et tous les rapports sauf le plus récent sont compressés pour réduire l’espace disque requis. 

        Une fois l’analyse terminée, un `Summary_<x>.txt` fichier est créé avec le résumé de l’analyse.

> [!NOTE]
> Les scanneurs envoient les informations de données collectées à Protection des données Microsoft Purview toutes les cinq minutes, afin que vous puissiez afficher les résultats en quasi-temps réel à partir du portail d’administration. Pour plus d’informations, consultez [Analytique et rapports centraux pour Azure Information Protection](/azure/information-protection/reports-aip).
>
> Le portail d’administration affiche uniquement des informations sur la dernière analyse. Si vous devez voir les résultats des analyses précédentes, revenez aux rapports stockés sur l’ordinateur du scanneur, dans le dossier %*localappdata*%\Microsoft\MSIP\Scanner\Reports.
>

[Les configurations initiales](deploy-scanner-configure-install.md#configure-the-scanner-settings) vous indiquent de définir les **types d’informations à découvrir** **sur Stratégie uniquement**. Cette configuration signifie que seuls les fichiers qui remplissent les conditions que vous avez configurées pour la classification automatique sont inclus dans les rapports détaillés.

Si aucune étiquette n’est appliquée, vérifiez que votre configuration d’étiquette inclut une classification automatique plutôt que recommandée, ou **activez traiter l’étiquetage recommandé comme automatique** (disponible dans la version 2.7.x.x et ultérieure du scanneur).

Si les résultats ne sont toujours pas comme prévu, vous devrez peut-être reconfigurer les conditions que vous avez spécifiées pour vos étiquettes. Si c’est le cas, reconfigurez les conditions en fonction des besoins et répétez cette procédure jusqu’à ce que vous soyez satisfait des résultats. Ensuite, mettez à jour votre configuration automatiquement et éventuellement la protection.

### <a name="changing-log-levels-or-locations"></a>Modification des niveaux ou des emplacements du journal

Modifiez le niveau de journalisation à l’aide du paramètre *ReportLevel* avec [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration).

L’emplacement ou le nom du dossier de rapport ne peut pas être modifié. Si vous souhaitez stocker des rapports à un autre emplacement, envisagez d’utiliser une jonction de répertoire pour le dossier.

Par exemple, utilisez la commande [Mklink](/windows-server/administration/windows-commands/mklink) : `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`

Si vous avez effectué ces étapes après une configuration et une installation initiales, [continuez avec Configurer le scanneur pour appliquer la classification et la protection](deploy-scanner-configure-install.md#configure-the-scanner-to-apply-classification-and-protection).

## <a name="stopping-a-scan"></a>Arrêt d’une analyse

Pour arrêter une analyse en cours d’exécution avant sa fin, utilisez l’une des méthodes suivantes :

- **portail de conformité Microsoft Purview.** Sélectionnez **Arrêter l’analyse** :

- **Exécutez une commande PowerShell.** Exécutez la commande suivante :

    ```PowerShell
    Stop-AIPScan
    ```

## <a name="rescanning-files"></a>Rescanning files

Pour le [premier cycle d’analyse](#run-a-discovery-cycle-and-view-reports-for-the-scanner), le scanneur inspecte tous les fichiers des magasins de données configurés. Pour les analyses suivantes, seuls les fichiers nouveaux ou modifiés sont inspectés.

Il est utile d’inspecter à nouveau tous les fichiers lorsque vous souhaitez que les rapports incluent tous les fichiers, lorsque vous avez des modifications que vous souhaitez appliquer à tous les fichiers et lorsque le scanneur s’exécute en mode de découverte.

**Pour exécuter manuellement une nouvelle analyse complète dans le portail de conformité Microsoft Purview** :

1. Accédez au **scanneur de protection des informations - Volet Tâches d’analyse de contenu** dans le portail de conformité Microsoft Purview.

2. Sélectionnez votre travail d’analyse de contenu dans la liste, puis sélectionnez l’option **Rescan all files** :

Une fois l’analyse complète terminée, le type d’analyse passe automatiquement à incrémentiel afin que, pour les analyses suivantes, seuls les fichiers nouveaux ou modifiés soient analysés à nouveau.

> [!TIP]
> Si vous avez apporté des modifications à votre [travail d’analyse de contenu](deploy-scanner-configure-install.md#create-a-content-scan-job), le portail de conformité vous invite à ignorer une nouvelle analyse complète. Pour vous assurer que votre nouvelle analyse se produit, veillez à sélectionner **Non** dans l’invite qui s’affiche.
>

### <a name="trigger-a-full-rescan-by-modifying-your-settings"></a>Déclencher une nouvelle analyse complète en modifiant vos paramètres

Les versions antérieures du scanneur scannent tous les fichiers chaque fois que le scanneur détecte des paramètres nouveaux ou modifiés pour l’étiquetage automatique et recommandé. Le scanneur actualisait automatiquement la stratégie toutes les quatre heures.

Dans les versions 2.8.85.0 ou ultérieures du scanneur de protection des informations, le scanneur de protection des informations ignore la rescan complète des paramètres mis à jour pour garantir des performances cohérentes. Veillez à [exécuter une nouvelle analyse complète manuellement](#rescanning-files) en fonction des besoins.

Par exemple, si vous avez modifié les paramètres de stratégie de **confidentialité** de **Enforce = Off** to **Enforce = On**, veillez à exécuter une nouvellecan complète pour appliquer vos étiquettes à votre contenu.

> [!NOTE]
> Dans la version [2.7.101.0](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history#general-availability-versions-that-are-no-longer-supported) et ultérieure du scanneur, vous souhaiterez peut-être actualiser la stratégie plus tôt que toutes les quatre heures, par exemple lors du test. Dans ce cas, supprimez manuellement le contenu du répertoire **%LocalAppData%\Microsoft\MSIP\mip\<processname>\mip** et redémarrez le service Azure Information Protection.
>
> Si vous avez également modifié les paramètres de chiffrement de vos étiquettes de confidentialité, patientez 15 minutes supplémentaires à partir du moment où vous avez enregistré les paramètres de chiffrement mis à jour avant de redémarrer le service Azure Information Protection.
>

## <a name="next-steps"></a>Prochaines étapes

Vous pouvez également utiliser PowerShell pour classifier et protéger de manière interactive les fichiers de votre ordinateur de bureau. Pour plus d’informations sur ce problème et d’autres scénarios qui utilisent PowerShell, consultez [Utilisation de PowerShell avec le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell).
