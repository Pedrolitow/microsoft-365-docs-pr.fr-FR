---
title: Migration de serveurs de Microsoft Monitoring Agent vers la solution unifiée
description: Découvrez comment migrer des serveurs de bas niveau de Microsoft Monitoring Agent vers la nouvelle solution unifiée pas à pas à partir de cet article.
keywords: migrate server, server, 2012r2, 2016, server migration onboard Microsoft Defender pour point de terminaison servers, MECM, Microsoft Monitoring Agent, MMA, downlevel server, unified solution, UA
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: alekyaj
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fef1a5a7b8e47c4f97d36d4002ccf00401948d12
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2022
ms.locfileid: "66992064"
---
# <a name="migrating-servers-from-microsoft-monitoring-agent-to-the-unified-solution"></a>Migration de serveurs de Microsoft Monitoring Agent vers la solution unifiée

**S’applique à :**

- Windows Server 2012 R2
- Windows Server 2016

Cet article vous guide dans la migration de serveurs de bas niveau de Microsoft Monitoring Agent (MMA) vers la solution unifiée.

## <a name="prerequisites"></a>Configuration requise

- Microsoft Endpoint Configuration Manager (MECM) antérieur à 2207.
- Appareils de système d’exploitation de bas niveau dans votre environnement intégrés à Microsoft Monitoring Agent. Pour confirmer, vérifiez qu’il `MsSenseS.exe` est en cours d’exécution dans le Gestionnaire des tâches.
- Présence de l’agent MMA. Vous pouvez le vérifier en vérifiant si l’ID d’espace de travail approprié est présent dans le Panneau de configuration> Microsoft Monitoring Agent.
- Portail Microsoft 365 Defender actif avec les appareils intégrés.
- Une collection d’appareils contenant des serveurs de bas niveau tels que Windows Server 2012 R2 ou Windows Server 2016 à l’aide de l’agent MMA est configurée dans votre instance MECM.

Pour plus d’informations sur l’installation des prérequis répertoriés, consultez la section [rubriques connexes](#related-topics) .

## <a name="gather-required-files"></a>Collecter les fichiers requis

Copiez le package de solution unifié, le script d’intégration et le script de migration vers la même source de contenu que vous déployez d’autres applications avec MECM.

1. Téléchargez le script d’intégration et la solution unifiée à partir de [Microsoft 365 Defender page des paramètres](https://sip.security.microsoft.com/preferences2/onboarding).
      :::image type="content" source="images/onboarding-script.png" alt-text="Capture d’écran du script d’intégration et du téléchargement d’une solution unifiée." lightbox="images/onboarding-script.png":::
2. Téléchargez le script de migration à partir du document : [Scénarios de migration de serveur de la solution Microsoft Defender pour point de terminaison MMA précédente](server-migration.md). Ce script se trouve également sur GitHub : [GitHub - microsoft/mdefordownlevelserver](https://github.com/microsoft/mdefordownlevelserver).
3. Enregistrez les trois fichiers dans un dossier partagé utilisé par MECM comme source logicielle.
     :::image type="content" source="images/ua-migration.png" alt-text="Capture d’écran de l’enregistrement du dossier partagé par MECM.":::

## <a name="create-the-package-as-an-application"></a>Créer le package en tant qu’application

1. Dans la console MECM, procédez comme suit : **Bibliothèque de logiciels>Applications>Créer une application**.
2. Sélectionnez **Manuellement pour spécifier les informations de l’application**.
      :::image type="content" source="images/manual-application-information.png" alt-text="Capture d’écran de la spécification manuelle de la sélection des informations de l’application." lightbox="images/manual-application-information.png":::
3. Cliquez sur **Suivant** sur l’écran Centre logiciel de l’Assistant.
4. Dans les types de déploiement, cliquez sur **Ajouter**.
5. Sélectionnez **manuellement pour spécifier les informations de type de déploiement** , puis cliquez sur **Suivant**.
6. Donnez un nom à votre déploiement de script, puis cliquez sur **Suivant**.
     :::image type="content" source="images/manual-deployment-information.png" alt-text="Capture d’écran spécifiant les informations de déploiement de script.":::
7. Dans cette étape, copiez le chemin d’accès UNC où se trouve votre contenu. Exemple : `\\Cm1\h$\SOFTWARE_SOURCE\UAmigrate`.
     :::image type="content" source="images/deployment-type-wizard.png" alt-text="Capture d’écran montrant la copie du chemin UNC.":::
8. En outre, définissez ce qui suit comme programme d’installation :

     ```powershell
       Powershell.exe -ExecutionPolicy ByPass -File install.ps1 -Log -Etl -RemoveMMA 48594f03-7e66-4e15-8b60-d9da2f92d564 -OnboardingScript .\WindowsDefenderATP.onboarding
     ```

9. Cliquez sur **Suivant** , puis sur Ajouter une clause.
10. La clause recherche dans le Registre si la clé suivante est présente :  `HKEY_LOCAL_MACHINESOFTWARE\Classes\Installer\Products\63FAD065BFFD18F1926692665F704C6D`

     Fournissez les entrées suivantes :
     - Valeur : **ProductName**
     - Type de données : **String**
     - Cochez l’option : **ce paramètre de Registre doit se fermer sur le système cible pour indiquer la présence de cette application.**

     :::image type="content" source="images/detection-rule-wizard.png" alt-text="Capture d’écran montrant la détection de clé de Registre.":::

     >[!TIP]
     >Cette valeur de clé de Registre a été obtenue en exécutant la commande PowerShell suivante sur un appareil sur lequel la solution unifiée a été installée. D’autres méthodes créatives de détection peuvent également être utilisées. L’objectif est de déterminer si la solution unifiée a déjà été installée sur un appareil spécifique.

     ```powershell
     PowerShell Cmd:  get-wmiobject Win32_Product | Sort-Object -Property Name |Format-Table IdentifyingNumber, Name, LocalPackage -AutoSize
     ```

11. Dans la section **Expérience utilisateur** , vous pouvez choisir ce qui convient à votre environnement, puis cliquer sur **Suivant**. Pour la **visibilité du programme d’installation**, il est recommandé d’installer avec **une visibilité normale** pendant le test de phase, puis de la remplacer par **Réduire** pour le déploiement général.
     >[!TIP]
     > Le runtime maximal autorisé peut être réduit de 120 minutes (par défaut) à 30 minutes.

     :::image type="content" source="images/user-experience-in-deployment-type-wizard.png" alt-text="Capture d’écran montrant l’expérience utilisateur dans l’Assistant type de déploiement.":::

12. Cliquez sur **Suivant** sur Exigences.
13. Cliquez sur **Suivant** sur Dépendances.
14. Cliquez sur **Suivant** jusqu’à ce que l’écran d’achèvement s’affiche, puis **Fermez**.
15. Continuez à cliquer sur suivant jusqu’à la fin de l’Assistant Application. Vérifiez que tous les éléments ont été vérifiés en vert.
16. Fermez l’Assistant, cliquez avec le bouton droit sur l’application créée récemment et déployez-la dans votre collection de serveurs de bas niveau.
     :::image type="content" source="images/deploy-application.png" alt-text="Capture d’écran montrant le déploiement de l’application créée." lightbox="images/deploy-application.png":::
17. Vérifiez dans MECM>surveillance>déploiements l’état de cette migration.

      :::image type="content" source="images/deployment-status.png" alt-text="Capture d’écran montrant la vérification de l’état du déploiement." lightbox="images/deployment-status.png":::

## <a name="related-topics"></a>Voir aussi

- [Configuration de l'agent Microsoft Monitoring Agent](/services-hub/health/mma-setup)
- [Déployer des applications - Configuration Manager](/mem/configmgr/apps/deploy-use/deploy-applications)
- [Microsoft Defender pour point de terminaison - Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison](configure-server-endpoints.md)
- [Microsoft Defender pour point de terminaison : Défense Windows Server 2012 R2 et 2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/ba-p/2783292)
