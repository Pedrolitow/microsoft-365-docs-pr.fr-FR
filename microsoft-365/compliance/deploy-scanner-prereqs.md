---
title: Prise en main du scanneur Protection des données Microsoft Purview
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
description: Répertorie les conditions préalables à l’installation et au déploiement du scanneur Protection des données Microsoft Purview.
ms.openlocfilehash: cf8daa62709c557d771a76889b9c277c124cadbc
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68638981"
---
# <a name="get-started-with-the-information-protection-scanner"></a>Prise en main du scanneur de protection des informations

Avant d’installer le scanneur à partir de Protection des données Microsoft Purview, assurez-vous que votre système est conforme aux [exigences d’Azure Information Protection](/azure/information-protection/requirements) de base.

En outre, les exigences suivantes sont spécifiques pour le scanneur :

- [Configuration requise pour Windows Server](#windows-server-requirements)
- [Configuration requise pour le compte de service](#service-account-requirements)
- [Configuration requise pour SQL Server](#sql-server-requirements)
- [Exigences du client Azure Information Protection](#azure-information-protection-client-requirements)
- [Configuration requise pour les étiquettes](#label-configuration-requirements)
- [Configuration requise pour SharePoint](#sharepoint-requirements)
- [Conditions requises pour Microsoft Office](#microsoft-office-requirements)
- [Configuration requise pour le chemin d’accès au fichier](#file-path-requirements)

Si vous ne pouvez pas répondre à toutes les exigences répertoriées pour le scanneur, car elles sont interdites par les stratégies de votre organisation, consultez la section [autres configurations](#deploying-the-scanner-with-alternative-configurations) .

Lorsque vous déployez le scanneur en production ou testez les performances de plusieurs scanneurs, consultez [les exigences de stockage et la planification de la capacité pour SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

Lorsque vous êtes prêt à commencer à installer et déployer votre scanneur, poursuivez la [configuration et l’installation du scanneur de protection des informations](deploy-scanner-configure-install.md).

## <a name="windows-server-requirements"></a>Configuration requise pour Windows Server

Vous devez disposer d’un ordinateur Windows Server pour exécuter le scanneur, qui a les spécifications système suivantes :

|Spécification  |Détails  |
|---------|---------|
|**Processeur**     |4 processeurs de base         |
|**Mémoire RAM**     |8 Go         |
|**Espace disque**     |Espace libre de 10 Go (moyenne) pour les fichiers temporaires. </br></br>Le scanneur nécessite suffisamment d’espace disque pour créer des fichiers temporaires pour chaque fichier qu’il analyse, quatre fichiers par cœur. </br></br>L’espace disque recommandé de 10 Go permet à 4 processeurs principaux d’analyser 16 fichiers dont chacun a une taille de fichier de 625 Mo.
|**Système d’exploitation**     |Versions 64 bits de : <br><br>- Windows Server 2019 </br>- Windows Server 2016 </br>- Windows Server 2012 R2 </br></br>**Remarque** : à des fins de test ou d’évaluation dans un environnement hors production, vous pouvez également utiliser n’importe quel système d’exploitation Windows [pris en charge par le client Azure Information Protection](/azure/information-protection/requirements#client-devices).
|**Connectivité réseau**     | Votre ordinateur scanneur peut être un ordinateur physique ou virtuel avec une connexion réseau rapide et fiable aux magasins de données à analyser. </br></br> Si la connectivité Internet n’est pas possible en raison des stratégies de votre organisation, consultez [Déploiement du scanneur avec d’autres configurations](#deploying-the-scanner-with-alternative-configurations). </br></br>Sinon, assurez-vous que cet ordinateur dispose d’une connectivité Internet qui autorise les URL suivantes sur HTTPS (port 443) :</br><br />-  \*.aadrm.com <br />-  \*.azurerms.com<br />-  \*.informationprotection.azure.com <br /> - informationprotection.hosting.portal.azure.net <br /> - \*.aria.microsoft.com <br />-  \*.protection.outlook.com |
|**Partages NFS** |Pour prendre en charge les analyses sur les partages NFS, les services pour NFS doivent être déployés sur l’ordinateur du scanneur. <br><br>Sur votre ordinateur, accédez à la boîte de dialogue **Fonctionnalités Windows (activer ou désactiver les fonctionnalités Windows),** puis sélectionnez les éléments suivants : Services pour les **outils d’administration** **NFS** >  et **Client pour NFS**. |
| **Microsoft Office iFilter** |Lorsque votre scanneur est installé sur un ordinateur windows server, vous devez également installer Microsoft Office iFilter afin d’analyser .zip fichiers à la recherche de types d’informations sensibles. <br><br>Pour plus d’informations, consultez le [site de téléchargement Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=17062).|

## <a name="service-account-requirements"></a>Configuration requise pour le compte de service

Vous devez disposer d’un compte de service pour exécuter le service de scanneur sur l’ordinateur Windows Server, ainsi que vous authentifier auprès d’Azure AD et télécharger la stratégie du scanneur.

Votre compte de service doit être un compte Active Directory et synchronisé avec Azure AD.

Si vous ne pouvez pas synchroniser ce compte en raison des stratégies de votre organisation, consultez [Déploiement du scanneur avec d’autres configurations](#deploying-the-scanner-with-alternative-configurations).

Ce compte de service a les exigences suivantes :

|Conditions requises  |Détails  |
|---------|---------|
|**Se connecter à l’attribution** de droits d’utilisateur localement     |Requis pour installer et configurer le scanneur, mais pas pour exécuter des analyses.  </br></br>Une fois que vous avez confirmé que le scanneur peut détecter, classifier et protéger des fichiers, vous pouvez supprimer ce droit du compte de service.  </br></br>Si l’octroi de ce droit même pendant une courte période n’est pas possible en raison des stratégies de votre organisation, consultez [Déploiement du scanneur avec d’autres configurations](#deploying-the-scanner-with-alternative-configurations).         |
|**Connectez-vous en tant qu’affectation** de droit d’utilisateur de service.     |  Ce droit est automatiquement accordé au compte de service pendant l’installation du scanneur et ce droit est requis pour l’installation, la configuration et le fonctionnement du scanneur.        |
|**Autorisations sur les référentiels de données**     |- **Partages de fichiers ou fichiers locaux** : accordez des autorisations **de lecture**, **d’écriture** et de **modification** pour analyser les fichiers, puis appliquer la classification et la protection comme configurés.  <br /><br />- **SharePoint** : vous devez accorder des autorisations **de contrôle total** pour analyser les fichiers, puis appliquer la classification et la protection aux fichiers qui remplissent les conditions de la stratégie Azure Information Protection.  <br /><br />- **Mode de découverte** : pour exécuter le scanneur en mode de découverte uniquement, l’autorisation **de lecture** est suffisante.         |
|**Pour les étiquettes qui reprotégent ou suppriment la protection**     | Pour vous assurer que le scanneur a toujours accès aux fichiers chiffrés, faites de ce compte un [super utilisateur](/azure/information-protection/configure-super-users) pour Azure Information Protection et assurez-vous que la fonctionnalité de super utilisateur est activée. </br></br>En outre, si vous avez implémenté [des contrôles d’intégration](/azure/information-protection/activate-service#configuring-onboarding-controls-for-a-phased-deployment) pour un déploiement par phases, assurez-vous que le compte de service est inclus dans les contrôles d’intégration que vous avez configurés.|
|**Analyse au niveau de l’URL spécifique** |Pour analyser et découvrir des sites et des sous-sites [sous une URL spécifique](#deploying-the-scanner-with-alternative-configurations), **accordez des droits d’auditeur de collecteur** de sites au compte de scanneur au niveau de la batterie de serveurs.|
|**Licence pour la protection des informations** | Requis pour fournir des fonctionnalités de classification, d’étiquetage ou de protection des fichiers au compte de service du scanneur. <br><br>Pour plus d’informations, consultez les [conseils microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-sensitivity-labeling). |

## <a name="sql-server-requirements"></a>Configuration requise pour SQL Server

Pour stocker les données de configuration du scanneur, utilisez un serveur SQL server avec les exigences suivantes :

- **Instance locale ou distante.**

    Nous vous recommandons d’héberger le serveur SQL et le service de scanneur sur différentes machines, sauf si vous travaillez avec un petit déploiement. En outre, nous vous recommandons d’avoir une instance SQL dédiée qui sert uniquement la base de données du scanneur et qui n’est pas partagée avec d’autres applications.

    Si vous travaillez sur un serveur partagé, assurez-vous que le [nombre de cœurs recommandé](#windows-server-requirements) est gratuit pour que la base de données du scanneur fonctionne.

    SQL Server 2016 est la version minimale pour les éditions suivantes :

    - SQL Server Enterprise

    - SQL Server Standard

    - SQL Server Express (recommandé pour les environnements de test uniquement)

- **Un compte avec le rôle Sysadmin pour installer le scanneur.**

    Le rôle Sysadmin permet au processus d’installation de créer automatiquement la base de données de configuration du scanneur et d’accorder le rôle **de db_owner** requis au compte de service qui exécute le scanneur.

    Si vous ne pouvez pas recevoir le rôle Sysadmin ou si les stratégies de votre organisation nécessitent la création et la configuration manuelles des bases de données, consultez [Déploiement du scanneur avec d’autres configurations](#deploying-the-scanner-with-alternative-configurations).

- **Capacité.** Pour obtenir des conseils sur la capacité, consultez [les exigences de stockage et la planification de la capacité pour SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

- **[Classement non sensible à la casse](/sql/relational-databases/collations/collation-and-unicode-support).**

> [!NOTE]
> Plusieurs bases de données de configuration sur le même serveur SQL sont prises en charge lorsque vous spécifiez un nom de cluster personnalisé pour le scanneur ou lorsque vous utilisez la préversion du scanneur.

### <a name="storage-requirements-and-capacity-planning-for-sql-server"></a>Exigences de stockage et planification de la capacité pour SQL Server

La quantité d’espace disque nécessaire à la base de données de configuration du scanneur et la spécification de l’ordinateur exécutant SQL Server peuvent varier pour chaque environnement. Nous vous encourageons donc à effectuer vos propres tests. Utilisez les conseils suivants comme point de départ.

Pour plus d’informations, consultez [Optimisation des performances du scanneur](deploy-scanner-configure-install.md#optimize-scanner-performance).

La taille de disque de la base de données de configuration du scanneur varie pour chaque déploiement. Utilisez l’équation suivante comme conseils :

```cli
100 KB + <file count> *(1000 + 4* <average file name length>)
```

Par exemple, pour analyser 1 million de fichiers dont la longueur moyenne du nom de fichier est de 250 octets, allouez 2 Go d’espace disque.

Pour plusieurs scanneurs :

- **Jusqu’à 10 scanneurs**, utilisez :

    - 4 processeurs de base
    - 8 Go de RAM recommandés

- **Plus de 10 scanneurs** (maximum 40) utilisent :
    - 8 processus principaux
    - 16 Go de RAM recommandés

## <a name="azure-information-protection-client-requirements"></a>Exigences du client Azure Information Protection

La [version de disponibilité générale actuelle](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history) du client Azure Information Protection doit être installée sur l’ordinateur Windows Server.

Pour plus d’informations, consultez le [guide d’administrateur du client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide#installing-the-azure-information-protection-scanner).

> [!IMPORTANT]
> Vous devez installer le client complet pour le scanneur. N’installez pas le client uniquement avec le module PowerShell.
>

## <a name="label-configuration-requirements"></a>Configuration requise pour les étiquettes

Vous devez avoir au moins une étiquette de confidentialité configurée dans le portail de conformité Microsoft Purview pour le compte de scanneur, afin d’appliquer la classification et, éventuellement, le chiffrement.

Le *compte de scanneur* est le compte que vous allez spécifier dans le paramètre **DelegatedUser** de l’applet de commande [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) , exécuté lors de la configuration de votre scanneur. 

Si vos étiquettes n’ont pas de conditions d’étiquetage automatique, consultez les [instructions pour les autres configurations ci-dessous](#restriction-your-labels-do-not-have-auto-labeling-conditions) .

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [Appliquer automatiquement une étiquette de confidentialité à du contenu](apply-sensitivity-label-automatically.md)
- [Restreindre l’accès au contenu à l’aide du chiffrement dans les étiquettes de niveau de confidentialité](encryption-sensitivity-labels.md)
- [Configuration et installation du scanneur de protection des informations](deploy-scanner-configure-install.md)

## <a name="sharepoint-requirements"></a>Configuration requise pour SharePoint

Pour analyser les bibliothèques et dossiers de documents SharePoint, assurez-vous que votre serveur SharePoint est conforme aux exigences suivantes :

|Conditions requises  |Description  |
|---------|---------|
|**Versions prises en charge** | Les versions prises en charge sont les suivantes : SharePoint 2019, SharePoint 2016 et SharePoint 2013. <br> Les autres versions de SharePoint ne sont pas prises en charge pour le scanneur.     |
|**Contrôle de version**     |  Lorsque vous utilisez le [contrôle de version](/sharepoint/governance/versioning-content-approval-and-check-out-planning), le scanneur inspecte et étiquette la dernière version publiée. <br><br>Si le scanneur étiquette un fichier et qu’une [approbation de contenu](/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) est requise, ce fichier étiqueté doit être approuvé pour être disponible pour les utilisateurs.       |
|**Grandes batteries de serveurs SharePoint** |Pour les batteries de serveurs SharePoint volumineuses, vérifiez si vous devez augmenter le seuil d’affichage de liste (par défaut, 5 000) pour que le scanneur accède à tous les fichiers. <br><br>Pour plus d’informations, consultez [Gérer les listes et bibliothèques volumineuses dans SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server). |
|**Chemins de fichiers longs**  |Si vous avez des chemins de fichiers longs dans SharePoint, vérifiez que la valeur [httpRuntime.maxUrlLength](/dotnet/api/system.web.configuration.httpruntimesection.maxurllength) de votre serveur SharePoint est supérieure aux 260 caractères par défaut. <br><br>Pour plus d’informations, consultez [Éviter les délais d’expiration du scanneur dans SharePoint](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#avoid-scanner-timeouts-in-sharepoint). | 

## <a name="microsoft-office-requirements"></a>Conditions requises pour Microsoft Office

Pour analyser des documents Office, vos documents doivent se trouver dans l’un des formats suivants :

- Microsoft Office 97-2003
- Formats Office Open XML pour Word, Excel et PowerPoint

Pour plus d’informations, consultez [Les types de fichiers pris en charge par le client d’étiquetage unifié Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-file-types).

## <a name="file-path-requirements"></a>Configuration requise pour le chemin d’accès au fichier

Par défaut, pour analyser les fichiers, vos chemins d’accès doivent comporter un maximum de 260 caractères.

Pour analyser des fichiers avec des chemins d’accès de fichiers de plus de 260 caractères, installez le scanneur sur un ordinateur avec l’une des versions windows suivantes et configurez l’ordinateur en fonction des besoins :

|Version de Windows  |Description  |
|---------|---------|
|**Windows 2016 ou version ultérieure**     |   Configurer l’ordinateur pour prendre en charge les chemins longs      |
|**Windows 10 ou Windows Server 2016**     | Définissez le [paramètre de stratégie de groupe](/archive/blogs/jeremykuhne/net-4-6-2-and-long-paths-on-windows-10) suivant : Modèles **d’administration** >  de configuration  >  de l’ordinateur de stratégie **d’ordinateur** >  local **Tous les paramètres****activent les chemins longs** >  Win32.    </br></br>Pour plus d’informations sur la prise en charge des chemins d’accès longs dans ces versions, consultez la section Limitation de longueur maximale du [chemin d’accès](/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) de la documentation Windows 10 développeur.    |
|**Windows 10, version 1607 ou ultérieure**     |  Optez pour la fonctionnalité **de MAX_PATH** mise à jour. Pour plus d’informations, consultez [Activer les chemins longs dans Windows 10 versions 1607 et ultérieures](/windows/win32/fileio/naming-a-file#enable-long-paths-in-windows-10-version-1607-and-later).      |

## <a name="deploying-the-scanner-with-alternative-configurations"></a>Déploiement du scanneur avec d’autres configurations

Les conditions préalables répertoriées ci-dessus sont les exigences par défaut pour le déploiement du scanneur, et recommandées, car elles prennent en charge la configuration de scanneur la plus simple.

Les exigences par défaut doivent être adaptées aux tests initiaux, afin que vous puissiez vérifier les fonctionnalités du scanneur.

Toutefois, dans un environnement de production, les stratégies de votre organisation peuvent être différentes des exigences par défaut. Le scanneur peut prendre en charge les modifications suivantes avec une configuration supplémentaire :

- [Découvrir et analyser tous les sites et sous-sites sous une URL spécifique](#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url)

- [Restriction : Le serveur de scanneur ne peut pas avoir de connectivité Internet](#restriction-the-scanner-server-cannot-have-internet-connectivity)

- [Restriction : le compte de service de scanneur ne peut pas être synchronisé avec Azure Active Directory, mais le serveur dispose d’une connectivité Internet](#restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity)

- [Restriction : le compte de service du scanneur ne peut pas être autorisé à ouvrir une **session localement** à droite](#restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right)

- [Restriction : Sysadmin ne peut pas vous être accordé ou les bases de données doivent être créées et configurées manuellement](#restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually)

- [Restriction : vos étiquettes n’ont pas de conditions d’étiquetage automatique](#restriction-your-labels-do-not-have-auto-labeling-conditions)

### <a name="discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url"></a>Découvrir et analyser tous les sites et sous-sites Sharepoint sous une URL spécifique

Le scanneur peut découvrir et analyser tous les sites et sous-sites Sharepoint sous une URL spécifique avec la configuration suivante :

1. Démarrez **l’Administration centrale de SharePoint**.

1. Sur le site web **Administration centrale de SharePoint** , dans la section **Gestion des** applications, cliquez sur **Gérer les applications web**.

1. Cliquez pour mettre en surbrillance l’application web dont vous souhaitez gérer le niveau de stratégie d’autorisation.

1. Choisissez la batterie de serveurs appropriée, puis **sélectionnez Gérer les niveaux de stratégie d’autorisation**.

1. Sélectionnez **l’auditeur de collection** de sites dans les options **Autorisations de collection** de sites, puis accordez **afficher les pages d’application** dans la liste des autorisations, puis nommez le nouvel **auditeur et la visionneuse de collection de sites du scanneur AIP** au niveau de la stratégie.

1. Ajoutez votre utilisateur de scanneur à la nouvelle stratégie et accordez **la collection de sites** dans la liste des autorisations.

1. Ajoutez une URL de SharePoint qui héberge des sites ou des sous-sites qui doivent être analysés. Pour plus d’informations, consultez [Configurer les paramètres du scanneur](/azure/information-protection/deploy-scanner-configure-install#configure-the-scanner-settings).

Pour en savoir plus sur la gestion de vos niveaux de stratégie SharePoint, consultez la section [Gérer les stratégies d’autorisation pour une application web](/sharepoint/administration/manage-permission-policies-for-a-web-application).

### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Restriction : Le serveur de scanneur ne peut pas avoir de connectivité Internet

Bien que le client d’étiquetage unifié ne puisse pas appliquer le chiffrement sans connexion Internet, le scanneur peut toujours appliquer des étiquettes en fonction des stratégies importées.

Pour prendre en charge un ordinateur déconnecté, utilisez l’une des méthodes suivantes :

- [Utiliser le Portail Azure](#use-the-azure-portal-with-a-disconnected-computer) (recommandé si possible)

- [Utiliser PowerShell](#use-powershell-with-a-disconnected-computer)

#### <a name="use-the-azure-portal-with-a-disconnected-computer"></a>Utiliser le Portail Azure avec un ordinateur déconnecté

Pour prendre en charge un ordinateur déconnecté du Portail Azure, effectuez les étapes suivantes :

1.  Configurez les étiquettes dans votre stratégie, puis utilisez la [procédure pour prendre en charge les ordinateurs déconnectés](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#support-for-disconnected-computers) afin d’activer la classification et l’étiquetage hors connexion.

1. Activez la gestion hors connexion pour les travaux de contenu comme suit :

    **Activez la gestion hors connexion pour les travaux d’analyse de contenu** :

    1. Définissez le scanneur pour qu’il fonctionne en mode **hors connexion** à l’aide de l’applet de commande [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) .

    1. Configurez le scanneur dans le portail de conformité en créant un cluster de scanneur. Pour plus d’informations, consultez [Configurer les paramètres du scanneur](deploy-scanner-configure-install.md#configure-the-scanner-settings).

    1. Exportez votre travail de contenu à partir du volet **Informations de protection - Tâches d’analyse de contenu** à l’aide de l’option **Exporter** .

    1. Importez la stratégie à l’aide de l’applet [de commande Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/import-aipscannerconfiguration) .

    Les résultats des travaux d’analyse de contenu hors connexion se trouvent dans : **%localappdata%\Microsoft\MSIP\Scanner\Reports**

#### <a name="use-powershell-with-a-disconnected-computer"></a>Utiliser PowerShell avec un ordinateur déconnecté

Effectuez la procédure suivante pour prendre en charge un ordinateur déconnecté à l’aide de PowerShell uniquement.

> [!IMPORTANT]
> Les administrateurs des [serveurs de scanneur Azure China 21Vianet](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection#manage-azure-information-protection-content-scan-jobs) *doivent* utiliser cette procédure pour gérer leurs travaux d’analyse de contenu.
>

**Gérez vos travaux d’analyse de contenu à l’aide de PowerShell uniquement** :

1. Définissez le scanneur pour qu’il fonctionne en mode **hors connexion** à l’aide de l’applet de commande [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) .

1. Créez un travail d’analyse de contenu à l’aide de l’applet de commande [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) , en veillant à utiliser le paramètre obligatoire `-Enforce On` .

1. Ajoutez vos référentiels à l’aide de l’applet de commande [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) , avec le chemin d’accès au référentiel que vous souhaitez ajouter.

    > [!TIP]
    > Pour empêcher le référentiel d’hériter des paramètres de votre travail d’analyse de contenu, ajoutez le `OverrideContentScanJob On` paramètre, ainsi que des valeurs pour des paramètres supplémentaires.
    >
    > Pour modifier les détails d’un référentiel existant, utilisez la commande [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) .
    >
 
1. Utilisez les applets de commande [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) et [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) pour retourner des informations sur les paramètres actuels de votre travail d’analyse de contenu. 

1. Utilisez la commande [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) pour mettre à jour les détails d’un référentiel existant.

1. Exécutez votre travail d’analyse de contenu immédiatement si nécessaire, à l’aide de l’applet de commande [Start-AIPScan](/powershell/module/azureinformationprotection/start-aipscan) . 

    Les résultats des travaux d’analyse de contenu hors connexion se trouvent dans : **%localappdata%\Microsoft\MSIP\Scanner\Reports**

1. Si vous devez supprimer un référentiel ou un travail d’analyse de contenu entier, utilisez les applets de commande suivantes :

    - [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob)
    - [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)

### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Restriction : Sysadmin ne peut pas vous être accordé ou les bases de données doivent être créées et configurées manuellement

Utilisez les procédures suivantes pour créer manuellement des bases de données et accorder le rôle **db_owner** , si nécessaire.

- [Procédure pour la base de données du scanneur](#manually-create-a-database-and-user-for-the-scanner-and-grant-db_owner-rights)

Si vous pouvez recevoir le rôle Sysadmin *temporairement* pour installer le scanneur, vous pouvez supprimer ce rôle une fois l’installation du scanneur terminée.

Effectuez l’une des opérations suivantes, en fonction des exigences de votre organisation :

|Restriction  |Description  |
|---------|---------|
|**Vous pouvez avoir le rôle Sysadmin temporairement**     |  Si vous disposez temporairement du rôle Sysadmin, la base de données est automatiquement créée pour vous et le compte de service du scanneur reçoit automatiquement les autorisations requises. <br><br>Toutefois, le compte d’utilisateur qui configure le scanneur nécessite toujours le rôle **db_owner** pour la base de données de configuration du scanneur. Si vous avez uniquement le rôle Sysadmin jusqu’à ce que l’installation du scanneur soit terminée, accordez le rôle **db_owner** au compte d’utilisateur manuellement.       |
|**Vous ne pouvez pas avoir le rôle Sysadmin du tout**     |  Si vous ne pouvez pas recevoir le rôle Sysadmin même temporairement, vous devez demander à un utilisateur disposant des droits Sysadmin de créer manuellement une base de données avant d’installer le scanneur. <br><br>Pour cette configuration, le rôle **db_owner** doit être attribué aux comptes suivants : <br>- Compte de service pour le scanneur<br>- Compte d’utilisateur pour l’installation du scanneur<br>- Compte d’utilisateur pour la configuration du scanneur <br><br>En règle générale, vous utiliserez le même compte d’utilisateur pour installer et configurer le scanneur. Si vous utilisez des comptes différents, ils nécessitent tous les deux le rôle **db_owner** pour la base de données de configuration du scanneur. Créez cet utilisateur et les droits nécessaires. Si vous spécifiez votre propre nom de cluster, la base de données de configuration est nommée **AIPScannerUL_<cluster_name>**.  |

De plus :

- Vous devez être un administrateur local sur le serveur qui exécutera le scanneur
- Le compte de service qui exécutera le scanneur doit disposer d’autorisations de contrôle total sur les clés de Registre suivantes :

    - `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\Server`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server`

Si, après avoir configuré ces autorisations, vous voyez une erreur lorsque vous installez le scanneur, l’erreur peut être ignorée et vous pouvez démarrer manuellement le service de scanneur.

#### <a name="manually-create-a-database-and-user-for-the-scanner-and-grant-db_owner-rights"></a>Créez manuellement une base de données et un utilisateur pour le scanneur et accordez db_owner droits

Si vous devez créer manuellement votre base de données de scanneur et/ou créer un utilisateur et accorder **db_owner** droits sur la base de données, demandez à votre Sysadmin d’effectuer les étapes suivantes :

1. Créez une base de données pour le scanneur :

    ```sql
    **CREATE DATABASE AIPScannerUL_[clustername]**

    **ALTER DATABASE AIPScannerUL_[clustername] SET TRUSTWORTHY ON**
    ```

2. Accordez des droits à l’utilisateur qui exécute la commande d’installation et est utilisé pour exécuter des commandes de gestion du scanneur. Utilisez le script suivant :

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE DBName IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END
    ```

3. Accordez des droits au compte de service de scanneur. Utilisez le script suivant :

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    ```

### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Restriction : le compte de service du scanneur ne peut pas être autorisé à ouvrir une **session localement** à droite

Si les stratégies de votre organisation interdisent l’ouverture de session **localement** pour les comptes de service, utilisez le paramètre *OnBehalfOf* avec Set-AIPAuthentication.

Pour plus d’informations, consultez [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Restriction : le compte de service de scanneur ne peut pas être synchronisé avec Azure Active Directory, mais le serveur dispose d’une connectivité Internet

Vous pouvez avoir un compte pour exécuter le service scanner et utiliser un autre compte pour vous authentifier auprès d’Azure Active Directory :

- **Pour le compte de service de scanneur**, utilisez un compte Windows local ou un compte Active Directory.

- **Pour le compte Azure Active Directory**, spécifiez l’utilisateur AAD dans [l’applet de commande Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) , dans le paramètre *DelegatedUser* . 

    Si vous exécutez l’analyse sous un utilisateur autre que le compte de scanneur, veillez également à spécifier le compte de scanneur dans le paramètre *OnBehalfOf* . 

    Pour plus d’informations, consultez [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

### <a name="restriction-your-labels-do-not-have-auto-labeling-conditions"></a>Restriction : vos étiquettes n’ont pas de conditions d’étiquetage automatique

Si vos étiquettes n’ont pas de conditions d’étiquetage automatique, envisagez d’utiliser l’une des options suivantes lors de la configuration de votre scanneur :

|Option  |Description  |
|---------|---------|
|**Découvrir tous les types d’informations**     |  Dans votre [travail d’analyse de contenu](deploy-scanner-configure-install.md#create-a-content-scan-job), définissez l’option **Informations à découvrir** sur **Tous**. </br></br>Cette option définit le travail d’analyse de contenu pour analyser votre contenu pour tous les types d’informations sensibles.      |
|**Utiliser l’étiquetage recommandé**     |  Dans votre [travail d’analyse de contenu](deploy-scanner-configure-install.md#create-a-content-scan-job), **définissez l’étiquetage recommandé treat comme option automatique** **sur Activé**.</br></br> Ce paramètre configure le scanneur pour appliquer automatiquement toutes les étiquettes recommandées sur votre contenu.      |
|**Définir une étiquette par défaut**     |   Définissez une étiquette par défaut dans votre [stratégie](sensitivity-labels.md#what-label-policies-can-do), [votre travail d’analyse de contenu](deploy-scanner-configure-install.md#create-a-content-scan-job) ou [votre référentiel](deploy-scanner-configure-install.md#apply-a-default-label-to-all-files-in-a-data-repository). </br></br>Dans ce cas, le scanneur applique l’étiquette par défaut sur tous les fichiers trouvés.       |

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez confirmé que votre système est conforme aux prérequis du scanneur, poursuivez la [configuration et l’installation du scanneur de protection des informations](deploy-scanner-configure-install.md).

Pour obtenir une vue d’ensemble du scanneur, consultez [En savoir plus sur le scanneur de protection des informations](deploy-scanner.md).