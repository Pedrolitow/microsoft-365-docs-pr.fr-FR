---
title: Résoudre des problèmes de performance
description: Résolvez les problèmes d’utilisation élevée du processeur liés au service de protection en temps réel dans Microsoft Defender pour point de terminaison.
keywords: résolution des problèmes, performances, utilisation élevée de l’UC, utilisation élevée du processeur, erreur, correctif, conformité des mises à jour, oms, surveiller, rapport, Antivirus Microsoft Defender
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
ms.date: 10/19/2021
audience: ITPro
ms.topic: troubleshooting
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 01db84f3ddd4eae79cae2fa97400f4d3d78ba8da
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419745"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Résoudre les problèmes de performances liés à la protection en temps réel


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Si votre système rencontre des problèmes d’utilisation élevée du processeur ou de performances liés au service de protection en temps réel dans Microsoft Defender pour point de terminaison, vous pouvez envoyer un ticket au support Microsoft. Suivez les étapes décrites dans [Collecter Antivirus Microsoft Defender données de diagnostic](collect-diagnostic-data.md).

En tant qu’administrateur, vous pouvez également résoudre ces problèmes vous-même.

Tout d’abord, vous pouvez vérifier si le problème est dû à un autre logiciel. [Consultez Vérifier auprès du fournisseur les exclusions antivirus](#check-with-vendor-for-antivirus-exclusions).

Sinon, vous pouvez identifier les logiciels liés au problème de performances identifié en suivant les étapes décrites dans [Analyser le journal de protection Microsoft](#analyze-the-microsoft-protection-log).

Vous pouvez également fournir des journaux d’activité supplémentaires à votre soumission au support Microsoft en suivant les étapes ci-dessous :

- [Capturer les journaux de processus à l’aide du Moniteur de processus](#capture-process-logs-using-process-monitor)
- [Capturer les journaux de performances à l’aide de l’enregistreur de performances Windows](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Vérifier auprès du fournisseur les exclusions antivirus

Si vous pouvez facilement identifier les logiciels qui affectent les performances du système, accédez au base de connaissances ou au centre de support du fournisseur de logiciels. Recherchez s’ils ont des recommandations sur les exclusions antivirus. Si le site web du fournisseur ne les a pas, vous pouvez ouvrir un ticket de support avec lui et lui demander d’en publier un.

Nous recommandons aux éditeurs de logiciels de suivre les différentes instructions en [matière de partenariat avec l’industrie afin de réduire les faux positifs](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/). Le fournisseur peut envoyer son logiciel via le [portail Renseignement de sécurité Microsoft](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper).

## <a name="analyze-the-microsoft-protection-log"></a>Analyser le journal de protection Microsoft

Dans **MPLog-xxxxxxxx-xxxxxx.log**, vous pouvez trouver les informations d’impact sur les performances estimées de l’exécution de logiciels *en tant qu’EstimatedImpact* :

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Nom du champ|Description|
|---|---|
|ProcessImageName|Nom de l’image de processus|
|TotalTime|Durée cumulée en millisecondes consacrée aux analyses des fichiers consultés par ce processus|
|Compte|Nombre de fichiers analysés accessibles par ce processus|
|MaxTime|Durée en millisecondes de l’analyse unique la plus longue d’un fichier accessible par ce processus|
|MaxTimeFile|Chemin d’accès au fichier par ce processus pour lequel l’analyse la plus longue de `MaxTime` la durée a été enregistrée|
|EstimatedImpact|Pourcentage de temps passé dans les analyses pour les fichiers consultés par ce processus hors de la période pendant laquelle ce processus a connu une activité d’analyse|
|

Si l’impact sur les performances est élevé, essayez d’ajouter le processus aux exclusions path/process en suivant les étapes [décrites dans Configurer et valider les exclusions pour Antivirus Microsoft Defender analyses](collect-diagnostic-data.md).

Si l’étape précédente ne résout pas le problème, vous pouvez collecter plus d’informations via le [Moniteur de processus](#capture-process-logs-using-process-monitor) ou [l’enregistreur de performances Windows](#capture-performance-logs-using-windows-performance-recorder) dans les sections suivantes.

## <a name="capture-process-logs-using-process-monitor"></a>Capturer les journaux de processus à l’aide du Moniteur de processus

Process Monitor (ProcMon) est un outil de supervision avancé qui peut afficher des processus en temps réel. Vous pouvez l’utiliser pour capturer le problème de performances tel qu’il se produit.

1. Téléchargez [Process Monitor v3.60](/sysinternals/downloads/procmon) dans un dossier comme `C:\temp`.

2. Pour supprimer la marque du fichier du web :
    1. Cliquez avec le bouton droit sur **ProcessMonitor.zip** et sélectionnez **Propriétés**.
    1. Sous l’onglet *Général* , recherchez *Sécurité*.
    1. Cochez la case à côté **de Débloquer**.
    1. Sélectionnez **Appliquer**.

    :::image type="content" source="images/procmon-motw.png" alt-text="Page Supprimer MOTW" lightbox="images/procmon-motw.png":::

3. Décompressez le fichier afin `C:\temp` que le chemin d’accès du dossier soit `C:\temp\ProcessMonitor`.

4. Copiez **ProcMon.exe** sur le client Windows ou le serveur Windows que vous résolvez.

5. Avant d’exécuter ProcMon, assurez-vous que toutes les autres applications non liées au problème d’utilisation élevée du processeur sont fermées. Cela permet de réduire le nombre de processus à vérifier.

6. Vous pouvez lancer ProcMon de deux manières.
    1. Cliquez avec le bouton droit sur **ProcMon.exe** et **sélectionnez Exécuter en tant qu’administrateur**.

        Étant donné que la journalisation démarre automatiquement, sélectionnez l’icône de loupe pour arrêter la capture actuelle ou utilisez le raccourci clavier **Ctrl+E**.

        :::image type="content" source="images/procmon-magglass.png" alt-text="Icône de loupe" lightbox="images/procmon-magglass.png":::

        Pour vérifier que vous avez arrêté la capture, vérifiez si l’icône de loupe apparaît maintenant avec un X rouge.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="Barre oblique rouge" lightbox="images/procmon-magglass-stop.png":::

        Ensuite, pour effacer la capture précédente, sélectionnez l’icône gomme.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="Icône Effacer" lightbox="images/procmon-eraser-clear.png":::

        Vous pouvez également utiliser le raccourci clavier **Ctrl+X**.

    2. La deuxième consiste à exécuter la **ligne de commande** en tant qu’administrateur, puis à partir du chemin d’accès du Moniteur de processus, exécutez :

       :::image type="content" source="images/cmd-procmon.png" alt-text="Le procmon cmd" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > Rendez la fenêtre ProcMon aussi petite que possible lors de la capture de données afin de pouvoir facilement démarrer et arrêter la trace.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="Page affichant un Procmon de réduction" lightbox="images/procmon-minimize.png":::

7. Après avoir suivi l’une des procédures de l’étape 6, vous verrez ensuite une option pour définir des filtres. Sélectionnez **OK**. Vous pouvez toujours filtrer les résultats une fois la capture terminée.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="Page sur laquelle l’exclusion système est choisie comme nom de processus de filtrage" lightbox="images/procmon-filter-options.png":::

8. Pour démarrer la capture, sélectionnez à nouveau l’icône de loupe.

9. Reproduisez le problème.

    > [!TIP]
    > Attendez que le problème soit entièrement reproduit, puis prenez note de l’horodatage au démarrage de la trace.

10. Une fois que vous avez deux à quatre minutes d’activité de processus pendant la condition d’utilisation élevée du processeur, arrêtez la capture en sélectionnant l’icône de loupe.

11. Pour enregistrer la capture avec un nom unique et au format .pml, sélectionnez **Fichier**, puis **sélectionnez Enregistrer...**. Veillez à sélectionner les cases d’option **Tous les événements** et **format PML (Native Process Monitor Format).**

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="Page Enregistrer les paramètres" lightbox="images/procmon-savesettings1.png":::

12. Pour un meilleur suivi, remplacez le chemin par défaut par `C:\temp\ProcessMonitor\LogFile.PML` l’emplacement `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` suivant :
    - `%ComputerName%` est le nom de l’appareil
    - `MMDDYEAR` est le mois, le jour et l’année
    - `Repro_of_issue` est le nom du problème que vous essayez de reproduire

    > [!TIP]
    > Si vous disposez d’un système fonctionnel, vous souhaiterez peut-être obtenir un exemple de journal à comparer.

13. Compressez le fichier .pml et envoyez-le au support Microsoft.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Capturer les journaux de performances à l’aide de l’enregistreur de performances Windows

Vous pouvez utiliser Windows’enregistreur de performances (WPR) pour inclure des informations supplémentaires dans votre soumission au support Microsoft. WPR est un outil d’enregistrement puissant qui crée le suivi d’événements pour les enregistrements Windows.

WPR fait partie du kit de déploiement et d’évaluation Windows (Windows ADK) et peut être téléchargé à partir du [téléchargement et de l’installation du Windows ADK](/windows-hardware/get-started/adk-install). Vous pouvez également le télécharger dans le cadre du kit de développement logiciel Windows 10 sur [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/).

Vous pouvez utiliser l’interface utilisateur WPR en suivant les [étapes de capture des journaux de performances à l’aide de l’interface utilisateur WPR](#capture-performance-logs-using-the-wpr-ui).

Vous pouvez également utiliser l’outil en ligne de commande *wpr.exe*, qui est disponible dans Windows 8 et versions ultérieures en suivant les [étapes décrites dans les journaux de performances de capture à l’aide de l’interface CLI WPR](#capture-performance-logs-using-the-wpr-cli).

### <a name="capture-performance-logs-using-the-wpr-ui"></a>Capturer les journaux de performances à l’aide de l’interface utilisateur WPR

> [!TIP]
> Si plusieurs appareils rencontrent ce problème, utilisez celui qui a le plus de RAM.

1. Téléchargez et installez WPR.

2. Sous *Windows Kits*, cliquez avec le bouton droit sur **Windows’enregistreur de performances**.

   :::image type="content" source="images/wpr-01.png" alt-text="Le menu Démarrer" lightbox="images/wpr-01.png":::

    Sélectionnez **Plus**. Sélectionnez **Exécuter en tant qu’administrateur**.

3. Lorsque la boîte de dialogue Contrôle de compte d’utilisateur s’affiche, sélectionnez **Oui**.

   :::image type="content" source="images/wpt-yes.png" alt-text="Page UAC" lightbox="images/wpt-yes.png":::

4. Ensuite, téléchargez le profil [d’analyse Microsoft Defender pour point de terminaison](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) et enregistrez `MDAV.wprp` dans un dossier comme `C:\temp`.

5. Dans la boîte de dialogue WPR, sélectionnez **Autres options**.

   :::image type="content" source="images/wpr-03.png" alt-text="Page sur laquelle vous pouvez sélectionner d’autres options" lightbox="images/wpr-03.png":::


6. Sélectionnez **Ajouter des profils...** puis accédez au chemin d’accès du `MDAV.wprp` fichier.

7. Après cela, vous devriez voir un nouveau profil défini sous *mesures personnalisées nommées* *Microsoft Defender pour point de terminaison analyse* en dessous.

   :::image type="content" source="images/wpr-infile.png" alt-text="Dans le fichier" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > Si votre serveur Windows a 64 Go de RAM ou plus, utilisez la mesure `Microsoft Defender for Endpoint analysis for large servers` personnalisée au lieu de `Microsoft Defender for Endpoint analysis`. Sinon, votre système peut consommer une grande quantité de mémoire ou de mémoire tampon de pool non pagagée, ce qui peut entraîner une instabilité du système. Vous pouvez choisir les profils à ajouter en développant **l’analyse des ressources**.
    Ce profil personnalisé fournit le contexte nécessaire pour une analyse approfondie des performances.

8. Pour utiliser la mesure personnalisée Microsoft Defender pour point de terminaison profil d’analyse détaillée dans l’interface utilisateur WPR :

    1. Assurez-vous qu’aucun profil n’est sélectionné dans les groupes *De triage de premier niveau*, *Analyse des ressources* et *Analyse de scénario* .
    2. Sélectionnez **Mesures personnalisées**.
    3. Sélectionnez **Microsoft Defender pour point de terminaison analyse**.
    4. Sélectionnez **Détaillé** sous *Niveau de détail* .
    5. Sélectionnez **Fichier** ou **Mémoire** en mode Journalisation.

    > [!IMPORTANT]
    > Vous devez sélectionner *Fichier* pour utiliser le mode de journalisation des fichiers si le problème de performances peut être reproduit directement par l’utilisateur. La plupart des problèmes appartiennent à cette catégorie. Toutefois, si l’utilisateur ne peut pas reproduire directement le problème, mais qu’il peut facilement le remarquer une fois le problème rencontré, il doit sélectionner *Mémoire* pour utiliser le mode de journalisation de la mémoire. Cela garantit que le journal de suivi ne se gonflera pas excessivement en raison du temps de longue durée.

9. Vous êtes maintenant prêt à collecter des données. Quittez toutes les applications qui ne sont pas pertinentes pour reproduire le problème de performances. Vous pouvez sélectionner **Masquer les options** pour limiter l’espace occupé par la fenêtre WPR.

   :::image type="content" source="images/wpr-08.png" alt-text="Options Masquer" lightbox="images/wpr-08.png":::

    > [!TIP]
    > Essayez de démarrer la trace en quelques secondes entières. Par exemple, 01:30:00. Cela facilite l’analyse des données. Essayez également de suivre l’horodatage du moment où le problème est reproduit.

10. Sélectionnez **Démarrer**.

    :::image type="content" source="images/wpr-09.png" alt-text="Page d’informations sur le système d’enregistrement" lightbox="images/wpr-09.png":::

11. Reproduisez le problème.

    > [!TIP]
    > Conservez la collecte de données au maximum cinq minutes. Deux à trois minutes sont une bonne plage, car beaucoup de données sont collectées.

12. Sélectionnez **Enregistrer**.

    :::image type="content" source="images/wpr-10.png" alt-text="Option Enregistrer" lightbox="images/wpr-10.png":::

13. Renseignez **Type dans une description détaillée du problème :** avec des informations sur le problème et la façon dont vous avez reproduit le problème.

    :::image type="content" source="images/wpr-12.png" alt-text="Volet dans lequel vous remplissez" lightbox="images/wpr-12.png":::

    1. Sélectionnez **Nom de fichier :** pour déterminer où votre fichier de trace sera enregistré. Par défaut, il est enregistré dans `%user%\Documents\WPR Files\`.
    1. Sélectionnez **Enregistrer**.

14. Attendez que la trace soit fusionnée.

    :::image type="content" source="images/wpr-13.png" alt-text="Collecte de la trace générale WPR" lightbox="images/wpr-13.png":::

15. Une fois la trace enregistrée, sélectionnez **Ouvrir le dossier**.

    :::image type="content" source="images/wpr-14.png" alt-text="Page affichant la notification indiquant que la trace WPR a été enregistrée" lightbox="images/wpr-14.png":::

    Incluez le fichier et le dossier dans votre soumission à Support Microsoft.

    :::image type="content" source="images/wpr-15.png" alt-text="Détails du fichier et du dossier" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>Capturer les journaux de performances à l’aide de l’interface CLI WPR

L’outil en ligne de commande *wpr.exe* fait partie du système d’exploitation en commençant par Windows 8. Pour collecter une trace WPR à l’aide de l’outil en ligne de commande wpr.exe :

1. Téléchargez **[Microsoft Defender pour point de terminaison profil d’analyse](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** pour les traces de performances dans un fichier nommé `MDAV.wprp` dans un répertoire local tel que `C:\traces`.

2. Cliquez avec le bouton droit sur l’icône **Menu Démarrer**, puis sélectionnez **Windows PowerShell (Administrateur)** ou **Invite de commandes (Administrateur)** pour ouvrir une fenêtre d’invite de commandes Administrateur.

3. Lorsque la boîte de dialogue Contrôle de compte d’utilisateur s’affiche, sélectionnez **Oui**.

4. À l’invite avec élévation de privilèges, exécutez la commande suivante pour démarrer une trace de performances Microsoft Defender pour point de terminaison :

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Si votre serveur Windows dispose d’au moins 64 Go de RAM, utilisez des profils `WDForLargeServers.Light` et`WDForLargeServers.Verbose`, respectivement, plutôt que des profils `WD.Light` `WD.Verbose`. Sinon, votre système peut consommer une grande quantité de mémoire ou de mémoire tampon de pool non pagagée, ce qui peut entraîner une instabilité du système.

5. Reproduisez le problème.

    > [!TIP]
    > Conservez la collecte de données au maximum cinq minutes. Selon le scénario, deux à trois minutes sont une bonne plage, car beaucoup de données sont collectées.

6. À l’invite avec élévation de privilèges, exécutez la commande suivante pour arrêter la trace des performances, en veillant à fournir des informations sur le problème et la façon dont vous avez reproduit le problème :

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. Attendez que la trace soit fusionnée.

8. Incluez à la fois le fichier et le dossier dans votre soumission au support Microsoft.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

- [Collecter Antivirus Microsoft Defender données de diagnostic](collect-diagnostic-data.md)
- [Configurer et valider les exclusions pour les analyses Antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md)
