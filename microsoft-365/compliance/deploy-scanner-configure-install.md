---
title: Installer et configurer le scanneur Protection des données Microsoft Purview
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
description: Découvrez comment installer et configurer le scanneur Protection des données Microsoft Purview pour découvrir, classifier et protéger des fichiers sur des magasins de données.
ms.openlocfilehash: 69d8d337f78fab74f35955ad15bd2d2e013a436c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68623908"
---
# <a name="configuring-and-installing-the-information-protection-scanner"></a>Configuration et installation du scanneur de protection des informations

> [!NOTE]
> Le scanneur Protection des données Microsoft Purview était auparavant nommé Azure Information Protection scanneur d’étiquetage unifié, ou scanneur local. La configuration est passée de la Portail Azure à la portail de conformité Microsoft Purview.

Cet article explique comment configurer et installer le scanneur Protection des données Microsoft Purview, anciennement nommé Azure Information Protection scanneur d’étiquetage unifié, ou le scanneur local.

> [!TIP]
> Bien que la plupart des clients effectuent ces procédures dans le portail d’administration, vous devrez peut-être travailler uniquement dans PowerShell.
>
> Par exemple, si vous travaillez dans un environnement sans accès au portail d’administration, tel que les [serveurs de scanneur Azure China 21Vianet](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection#manage-azure-information-protection-content-scan-jobs), suivez les instructions fournies dans [Utiliser PowerShell pour configurer le scanneur](#use-powershell-to-configure-the-scanner).
>

## <a name="overview"></a>Vue d’ensemble

Avant de commencer, vérifiez que votre système est conforme aux [prérequis requis](deploy-scanner-prereqs.md).

Ensuite, procédez comme suit pour configurer et installer le scanneur :

1. [Configurer les paramètres du scanneur](#configure-the-scanner-settings)

2. [Installer le scanneur](#install-the-scanner)

3. [Obtenir un jeton Azure AD pour le scanneur](#get-an-azure-ad-token-for-the-scanner)

4. [Configurer le scanneur pour appliquer la classification et la protection](#configure-the-scanner-to-apply-classification-and-protection)

Ensuite, effectuez les procédures de configuration suivantes en fonction des besoins de votre système :

|Procedure  |Description  |
|---------|---------|
|[Modifier les types de fichiers à protéger](#change-which-file-types-to-protect) |Vous souhaiterez peut-être analyser, classifier ou protéger différents types de fichiers par rapport à la valeur par défaut. Pour plus d’informations, consultez [Le processus d’analyse](deploy-scanner.md#the-scanning-process). |
|[Mise à niveau de votre scanneur](#upgrade-your-scanner) | Mettez à niveau votre scanneur pour utiliser les dernières fonctionnalités et améliorations.|
|[Modification des paramètres du référentiel de données en bloc](#edit-data-repository-settings-in-bulk)| Utilisez les options d’importation et d’exportation pour apporter des modifications en bloc à plusieurs référentiels de données.|
|[Utiliser le scanneur avec d’autres configurations](#use-the-scanner-with-alternative-configurations)| Utiliser le scanneur sans configurer d’étiquettes avec des conditions |
|[Optimiser les performances](#optimize-scanner-performance)| Conseils pour optimiser les performances de votre scanneur|

Si vous n’avez pas accès aux pages du scanneur dans le portail de conformité, configurez uniquement les paramètres du scanneur dans PowerShell. Pour plus d’informations, consultez [Utiliser PowerShell pour configurer le scanneur et les](#use-powershell-to-configure-the-scanner) [applets de commande PowerShell prises en charge](#supported-powershell-cmdlets).


## <a name="configure-the-scanner-settings"></a>Configurer les paramètres du scanneur

Avant d’installer le scanneur ou de le mettre à niveau à partir d’une version plus ancienne de la disponibilité générale, configurez ou vérifiez vos paramètres de scanneur.

**Pour configurer votre scanneur dans le portail de conformité Microsoft Purview :**

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) avec l’un des rôles suivants :

    - **Administrateur de conformité**
    - **Administrateur de conformité des données**
    - **Administrateur de sécurité**
    - **Administrateur général**

    Accédez ensuite au volet **Paramètres** .

    Dans le volet **Paramètres** , sélectionnez **Le scanneur de protection des informations**.

2. [Créez un cluster d’analyseur](#create-a-scanner-cluster). Ce cluster définit votre scanneur et est utilisé pour identifier l’instance du scanneur, par exemple pendant l’installation, les mises à niveau et d’autres processus.

3. [Créez un travail d’analyse de contenu](#create-a-content-scan-job) pour définir les référentiels que vous souhaitez analyser.

### <a name="create-a-scanner-cluster"></a>Créer un cluster d’analyseur

**Pour créer un cluster d’analyseur dans le portail de conformité Microsoft Purview :**

1. Dans les onglets de la page **analyseur de protection des informations** , sélectionnez **Clusters**.

2. Sous l’onglet **Clusters** , sélectionnez **Ajouter** ![une icône Ajouter](../media/i-add.png "ajouter une icône").

3. Dans le volet **Nouveau cluster** , entrez un nom explicite pour le scanneur et une description facultative.

    Le nom du cluster est utilisé pour identifier les configurations et les référentiels du scanneur. Par exemple, vous pouvez entrer en **Europe** pour identifier les emplacements géographiques des référentiels de données que vous souhaitez analyser.

    Vous utiliserez ce nom ultérieurement pour identifier l’emplacement où vous souhaitez installer ou mettre à niveau votre scanneur.

4. Sélectionnez **Enregistrer** pour enregistrer vos modifications.

### <a name="create-a-content-scan-job"></a>Créer un travail d’analyse de contenu

Explorez en détail votre contenu pour analyser des référentiels spécifiques à la recherche de contenu sensible.

**Pour créer votre travail d’analyse de contenu sur le portail de conformité Microsoft Purview :**

1. Dans les onglets de la page **analyseur de protection des informations** , sélectionnez **Tâches d’analyse de contenu**.

2. Dans le volet **Tâches d’analyse** de contenu, sélectionnez **Ajouter** ![une icône.](../media/i-add.png "icône enregistrer")

3. Pour cette configuration initiale, configurez les paramètres suivants, puis **sélectionnez Enregistrer**.

    |Setting  |Description  |
    |---------|---------|
    |**Paramètres du travail d’analyse de contenu**     |    - **Planification** : conserver la valeur par défaut de **Manuel** <br />- **Types d’informations à découvrir** : Passer à la **stratégie uniquement**
    |**Stratégie DLP** | Si vous utilisez une stratégie de protection contre la perte de données, **définissez activer les règles DLP** **sur Activé**. Pour plus d’informations, consultez [Utiliser une stratégie DLP](#use-a-dlp-policy). |
    |**Stratégie de confidentialité**     | - **Appliquer la stratégie d’étiquetage de confidentialité** : **Sélectionner désactivé** <br />- **Étiqueter des fichiers en fonction du contenu** : conserver la valeur par défaut **on** <br />- **Étiquette par défaut** : Conserver la valeur par défaut de la **stratégie par défaut** <br />- **Relabel files**: Keep the default of **Off**        |
    |**Configurer les paramètres de fichier**     | - **Conserver « Date modifiée », « Dernière modification » et « Modifié par »** : conservez la valeur par défaut **activée** <br />- **Types de fichiers à analyser** : conserver les types de fichiers par défaut pour **Exclude** <br />- **Propriétaire par défaut** : conserver la valeur par défaut du **compte scanneur**  <br /> - **Définir le propriétaire du référentiel** : utilisez cette option uniquement lors de [l’utilisation d’une stratégie DLP](#use-a-dlp-policy). |
    | | |


4. Ouvrez le travail d’analyse de contenu qui a été enregistré, puis sélectionnez l’onglet **Référentiels** pour spécifier les magasins de données à analyser. 

    Spécifiez des chemins UNC et des URL SharePoint Server pour les dossiers et les bibliothèques de documents SharePoint locaux.

    > [!NOTE]
    > SharePoint Server 2019, SharePoint Server 2016 et SharePoint Server 2013 sont pris en charge pour SharePoint. SharePoint Server 2010 est également pris en charge lorsque vous avez [étendu la prise en charge de cette version de SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010).
    >
    Pour ajouter votre premier magasin de données, sous l’onglet **Référentiels** :

    1. Dans le volet **Référentiels** , sélectionnez **Ajouter** :

    2. Dans le volet **Référentiel** , spécifiez le chemin du référentiel de données, puis **sélectionnez Enregistrer**.


        - Pour un partage réseau, utilisez `\\Server\Folder`.
        - Pour une bibliothèque SharePoint, utilisez `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
        - Pour un chemin local : `C:\Folder`
        - Pour un chemin UNC : `\\Server\Folder`

    > [!NOTE]
    > Les caractères génériques ne sont pas pris en charge et les emplacements WebDav ne sont pas pris en charge.
    >

    Si vous ajoutez un chemin SharePoint pour **les documents partagés** :
    - Spécifiez **documents partagés** dans le chemin d’accès lorsque vous souhaitez analyser tous les documents et tous les dossiers à partir de documents partagés.
    Par exemple : `http://sp2013/SharedDocuments`
    - Spécifiez **Documents** dans le chemin d’accès lorsque vous souhaitez analyser tous les documents et tous les dossiers à partir d’un sous-dossier sous Documents partagés.
    Par exemple : `http://sp2013/Documents/SalesReports`
    - Vous pouvez également spécifier uniquement le **nom** de domaine complet de votre sharepoint, par exemple `http://sp2013` pour [découvrir et analyser tous les sites et sous-sites SharePoint sous une URL](deploy-scanner-prereqs.md#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url) et des sous-titres spécifiques sous cette URL. Accordez aux **vérificateurs** de site du scanneur des droits d’auditeur pour l’activer.
    >


    Pour les paramètres restants dans ce volet, ne les modifiez pas pour cette configuration initiale, mais conservez-les comme **tâche d’analyse de contenu par défaut**. Le paramètre par défaut signifie que le référentiel de données hérite des paramètres du travail d’analyse de contenu.

    Utilisez la syntaxe suivante lors de l’ajout de chemins SharePoint :

    |Path  |Syntaxe  |
    |---------|---------|
    |**Chemin d’accès racine**     | `http://<SharePoint server name>` <br /><br />Analyse tous les sites, y compris les collections de sites autorisées pour l’utilisateur du scanneur. <br />Nécessite [des autorisations supplémentaires](deploy-scanner-prereqs.md#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url) pour découvrir automatiquement le contenu racine        |
    |**Sous-site ou collection SharePoint spécifique**     | Un des éléments suivants : <br />- `http://<SharePoint server name>/<subsite name>` <br />- `http://SharePoint server name>/<site collection name>/<site name>` <br /><br />Nécessite [des autorisations supplémentaires](deploy-scanner-prereqs.md#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url) pour découvrir automatiquement le contenu de la collection de sites         |
    |**Bibliothèque SharePoint spécifique**     | Un des éléments suivants : <br />- `http://<SharePoint server name>/<library name>` <br />- `http://SharePoint server name>/.../<library name>`       |
    |**Dossier SharePoint spécifique**     | `http://<SharePoint server name>/.../<folder name>`        |
    | | |

5. Répétez les étapes précédentes pour ajouter autant de référentiels que nécessaire.

Vous êtes maintenant prêt à installer le scanneur avec le travail de scanneur de contenu que vous avez créé. Continuez avec [l’installation du scanneur](#install-the-scanner).

## <a name="install-the-scanner"></a>Installer le scanneur

Une fois que vous avez [configuré le scanneur](#configure-the-scanner-settings), effectuez les étapes suivantes pour installer le scanneur. Cette procédure est entièrement exécutée dans PowerShell.

1. Connectez-vous à l’ordinateur Windows Server qui exécutera le scanneur. Utilisez un compte disposant de droits d’administrateur local et disposant des autorisations nécessaires pour écrire dans la base de données master SQL Server.

    > [!IMPORTANT]
    > Le client d’étiquetage unifié AIP doit être installé sur votre ordinateur avant d’installer le scanneur.
    >
    > Pour plus d’informations, consultez [Prérequis pour l’installation et le déploiement du scanneur de protection des informations](deploy-scanner-prereqs.md).
    >

2. Ouvrez une session Windows PowerShell avec l’option **Exécuter en tant qu’administrateur**.

3. Exécutez l’applet de commande [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), en spécifiant votre instance SQL Server sur laquelle créer une base de données pour le scanneur Azure Information Protection et le nom du cluster de scanneur que vous avez [spécifié dans la section précédente](#create-a-scanner-cluster) :

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    Exemples, à l’aide du nom du cluster scanner de **l’Europe** :

    - Pour une instance par défaut : `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Cluster Europe`

    - Pour une instance nommée : `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Cluster Europe`

    - Pour SQL Server Express :`Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Cluster Europe`

    Lorsque vous y êtes invité, fournissez les informations d’identification Active Directory pour le compte de service de scanneur.

    Utilisez la syntaxe suivante : `\<domain\user name>`. Par exemple : `contoso\scanneraccount`

4. Vérifiez que le service est maintenant installé à l’aide des **services** **Outils** >  d’administration.

    Le service installé est nommé **Azure Information Protection Scanner** et est configuré pour s’exécuter à l’aide du compte de service de scanneur que vous avez créé.

Maintenant que vous avez installé le scanneur, vous devez [obtenir un jeton Azure AD pour que le compte de service de scanneur](#get-an-azure-ad-token-for-the-scanner) s’authentifie, afin que le scanneur puisse s’exécuter sans assistance.

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Obtenir un jeton Azure AD pour le scanneur

Un jeton Azure AD permet au scanneur de s’authentifier auprès du service Azure Information Protection, ce qui permet au scanneur de s’exécuter de manière non interactive.

Pour plus d’informations, consultez [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

**Pour obtenir un jeton Azure AD** :

1. Ouvrez le [Portail Azure](https://portal.azure.com/) pour créer une application Azure AD afin de spécifier un jeton d’accès pour l’authentification.

2. À partir de l’ordinateur Windows Server, si votre compte de service de scanneur a reçu l’ouverture de session **localement** pour l’installation, connectez-vous avec ce compte et démarrez une session PowerShell.

    [Exécutez Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), en spécifiant les valeurs que vous avez copiées à l’étape précédente :

    ```PowerShell
    Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
    ```

    Par exemple :

    ```PowerShell
    $pscreds = Get-Credential CONTOSO\scanner
    Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
    Acquired application access token on behalf of CONTOSO\scanner.
    ```

    > [!TIP]
    > Si votre compte de service de scanneur ne peut pas se voir accorder l’ouverture de session **localement** pour l’installation, utilisez le paramètre *OnBehalfOf* avec [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), comme décrit dans [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    >

Le scanneur dispose désormais d’un jeton pour s’authentifier auprès d’Azure AD. Ce jeton est valide pendant un an, deux ans ou jamais, en fonction de votre configuration de la clé secrète client **d’application web/API** dans Azure AD. Lorsque le jeton expire, vous devez répéter cette procédure.

Continuez à utiliser l’une des étapes suivantes, selon que vous utilisez le portail de conformité pour configurer votre scanneur ou PowerShell uniquement :

# <a name="admin-portal-only"></a>[portail Administration uniquement](#tab/azure-portal-only)

Vous êtes maintenant prêt à exécuter votre première analyse en mode de découverte. Pour plus d’informations, consultez [Exécuter un cycle de découverte et afficher les rapports pour le scanneur](deploy-scanner-manage.md#run-a-discovery-cycle-and-view-reports-for-the-scanner).

Une fois que vous avez exécuté votre analyse de découverte initiale, [continuez avec Configurer le scanneur pour appliquer la classification et la protection](#configure-the-scanner-to-apply-classification-and-protection).

# <a name="powershell-only"></a>[PowerShell uniquement](#tab/powershell-only)

Si vous configurez et installez votre scanneur à l’aide de PowerShell au lieu des pages du scanneur dans le portail de conformité, passez à l’étape 5 de l’utilisation de [PowerShell pour configurer le scanneur](#powershell).

Ensuite :

- [Exécuter un cycle de découverte et afficher les rapports pour le scanneur](deploy-scanner-manage.md#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Utiliser PowerShell pour configurer le scanneur pour appliquer la classification et la protection](#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Utiliser PowerShell pour configurer une stratégie DLP avec le scanneur](#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

---

> [!NOTE]
> Pour plus d’informations, consultez [Comment étiqueter des fichiers de manière non interactive pour Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection)



## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Configurer le scanneur pour appliquer la classification et la protection

Les paramètres par défaut configurent le scanneur pour qu’il s’exécute une seule fois et en mode de création de rapports uniquement. Pour modifier ces paramètres, modifiez le travail d’analyse de contenu.

> [!TIP]
> Si vous travaillez uniquement dans PowerShell, consultez [Configurer le scanneur pour appliquer la classification et la protection - PowerShell uniquement](#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection).
>

**Pour configurer le scanneur de manière à appliquer la classification et la protection dans le portail de conformité Microsoft Purview** :

1. Dans le portail de conformité Microsoft Purview, sous l’onglet **Tâches d’analyse** de contenu, sélectionnez un travail d’analyse de contenu spécifique pour le modifier.

2. Sélectionnez le travail d’analyse de contenu, modifiez ce qui suit, puis **sélectionnez Enregistrer** :

   - Dans la section **Travail d’analyse de contenu** : Remplacer la **planification** par **Toujours**
   - Dans la section Appliquer la stratégie **d’étiquetage de confidentialité** : remplacez la case d’option **par Activé**

3. Assurez-vous qu’un nœud pour le travail d’analyse de contenu est en ligne, puis redémarrez le travail d’analyse de contenu en sélectionnant **Analyser maintenant**. Le bouton **Analyser maintenant** s’affiche uniquement lorsqu’un nœud pour le travail d’analyse de contenu sélectionné est en ligne. 

Le scanneur est maintenant planifié pour s’exécuter en continu. Lorsque le scanneur parcourt tous les fichiers configurés, il démarre automatiquement un nouveau cycle afin que tous les fichiers nouveaux et modifiés soient découverts.

## <a name="use-a-dlp-policy"></a>Utiliser une stratégie DLP

L’utilisation d’une stratégie de protection contre la perte de données permet au scanneur de détecter les fuites de données potentielles en mettant en correspondance les règles DLP avec les fichiers stockés dans les partages de fichiers et SharePoint Server.

- **Activez les règles DLP dans votre travail d’analyse de contenu** pour réduire l’exposition des fichiers qui correspondent à vos stratégies DLP. Lorsque vos règles DLP sont activées, le scanneur peut réduire l’accès aux fichiers aux propriétaires de données uniquement, ou réduire l’exposition aux groupes à l’échelle du réseau, tels que **tout le monde**, **les utilisateurs authentifiés** ou **les utilisateurs de domaine**.

- **Dans le portail de conformité Microsoft Purview**, déterminez si vous testez simplement votre stratégie DLP ou si vous souhaitez que vos règles soient appliquées et que vos autorisations de fichier soient modifiées en fonction de ces règles. Pour plus d’informations, consultez [Activer une stratégie DLP](create-test-tune-dlp-policy.md#turn-on-a-dlp-policy).

Les stratégies DLP sont configurées dans le portail de conformité Microsoft Purview. Pour plus d’informations sur les licences DLP, consultez [Prise en main du scanneur local de protection contre la perte de données](dlp-on-premises-scanner-get-started.md).

> [!TIP]
> L’analyse de vos fichiers, même lors du test de la stratégie DLP, crée également des rapports d’autorisation de fichier. Interrogez ces rapports pour examiner des expositions de fichiers spécifiques ou explorer l’exposition d’un utilisateur spécifique aux fichiers analysés.
>
> Pour utiliser PowerShell uniquement, consultez [Utiliser une stratégie DLP avec le scanneur - PowerShell uniquement](#use-powershell-to-configure-a-dlp-policy-with-the-scanner).
>

**Pour utiliser une stratégie DLP avec le scanneur dans le portail de conformité Microsoft Purview** :

1. Dans le portail de conformité Microsoft Purview, accédez à l’onglet **Tâches d’analyse** de contenu et sélectionnez un travail d’analyse de contenu spécifique. Pour plus d’informations, consultez [Créer un travail d’analyse de contenu](#create-a-content-scan-job).

2. Sous **Activer les règles de stratégie DLP**, définissez la case d’option **sur Activé**.
    
    > [!IMPORTANT]
    > Ne définissez pas **activer les règles DLP** **sur Activé** , sauf si vous disposez réellement d’une stratégie DLP configurée dans Microsoft 365.
    >
    >L’activation de cette fonctionnalité sans stratégie DLP entraîne la génération d’erreurs par le scanneur.

3. (Facultatif) Définissez le **propriétaire du référentiel** **sur Activé** et définissez un utilisateur spécifique en tant que propriétaire du référentiel.
    
    Cette option permet au scanneur de réduire l’exposition des fichiers trouvés dans ce référentiel, qui correspondent à la stratégie DLP, au propriétaire du référentiel défini.

### <a name="dlp-policies-and-make-private-actions"></a>Stratégies DLP et *actions privées*

Si vous utilisez une stratégie DLP avec une action *make private* et que vous envisagez également d’utiliser le scanneur pour étiqueter automatiquement vos fichiers, nous vous recommandons de définir également le paramètre avancé [**UseCopyAndPreserveNTFSOwner**](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#preserve-ntfs-owners-during-labeling-public-preview) du client d’étiquetage unifié.

Ce paramètre garantit que les propriétaires d’origine conservent l’accès à leurs fichiers.

Pour plus d’informations, consultez [Créer un travail d’analyse de contenu](#create-a-content-scan-job) et  [appliquer automatiquement une étiquette de confidentialité au contenu](apply-sensitivity-label-automatically.md).

## <a name="change-which-file-types-to-protect"></a>Modifier les types de fichiers à protéger

Par défaut, le scanneur protège uniquement les types de fichiers Office et les fichiers PDF.

Utilisez les commandes PowerShell pour modifier ce comportement en fonction des besoins, par exemple pour configurer le scanneur afin de protéger tous les types de fichiers, comme le client le fait, ou pour protéger des types de fichiers spécifiques supplémentaires.

Pour une stratégie d’étiquette qui s’applique au compte d’utilisateur téléchargeant des étiquettes pour le scanneur, spécifiez un paramètre avancé PowerShell nommé **PFileSupportedExtensions**.

Pour un scanneur qui a accès à Internet, ce compte d’utilisateur est le compte que vous spécifiez pour le paramètre *DelegatedUser* avec la commande Set-AIPAuthentication.

**Exemple 1** : Commande PowerShell pour le scanneur afin de protéger tous les types de fichiers, où votre stratégie d’étiquette est nommée « Scanneur » :

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions="*"}
```

**Exemple 2** : commande PowerShell pour le scanneur afin de protéger les fichiers .xml et les fichiers .tiff en plus des fichiers Office et PDF, où votre stratégie d’étiquette est nommée « Scanneur » :

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions=ConvertTo-Json(".xml", ".tiff")}
```

Pour plus d’informations, consultez [Modifier les types de fichiers à protéger](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#change-which-file-types-to-protect).

## <a name="upgrade-your-scanner"></a>Mettre à niveau votre scanneur

Si vous avez déjà installé le scanneur et souhaitez effectuer une mise à niveau, suivez les instructions décrites dans [Mettre à niveau le scanneur de protection des informations](/previous-versions/azure/information-protection/rms-client/client-admin-guide#upgrading-the-azure-information-protection-scanner).

Ensuite, [configurez](deploy-scanner-configure-install.md) et [utilisez votre scanneur](deploy-scanner-manage.md) comme d’habitude, en ignorant les étapes d’installation de votre scanneur.

## <a name="edit-data-repository-settings-in-bulk"></a>Modifier les paramètres du référentiel de données en bloc

Utilisez les boutons **Exporter** et **Importer** pour apporter des modifications à votre scanneur dans plusieurs référentiels.

De cette façon, vous n’avez pas besoin d’apporter les mêmes modifications plusieurs fois, manuellement, dans le Portail Azure ou portail de conformité Microsoft Purview.

Par exemple, si vous avez un nouveau type de fichier sur plusieurs référentiels de données SharePoint, vous pouvez mettre à jour les paramètres de ces référentiels en bloc.

**Pour apporter des modifications en bloc dans les référentiels du portail de conformité Microsoft Purview :**

1. Dans le portail de conformité Microsoft Purview, sélectionnez un travail d’analyse de contenu spécifique et accédez à l’onglet **Référentiels** dans le volet. Sélectionnez l’option **Exporter** .

2. Modifiez manuellement le fichier exporté pour apporter votre modification.

3. Utilisez l’option **Importer** sur la même page pour importer les mises à jour dans vos référentiels.

## <a name="use-the-scanner-with-alternative-configurations"></a>Utiliser le scanneur avec d’autres configurations

Le scanneur recherche généralement les conditions spécifiées pour vos étiquettes afin de classer et de protéger votre contenu en fonction des besoins.

Dans les scénarios suivants, le scanneur est également en mesure d’analyser votre contenu et de gérer les étiquettes, sans aucune condition configurée :

- [Appliquer une étiquette par défaut à tous les fichiers d’un référentiel de données](#apply-a-default-label-to-all-files-in-a-data-repository)
- [Supprimer des étiquettes existantes de tous les fichiers d’un référentiel de données](#remove-existing-labels-from-all-files-in-a-data-repository)
- [Identifier toutes les conditions personnalisées et les types d’informations sensibles connus](#identify-all-custom-conditions-and-known-sensitive-information-types)

### <a name="apply-a-default-label-to-all-files-in-a-data-repository"></a>Appliquer une étiquette par défaut à tous les fichiers d’un référentiel de données

Dans cette configuration, tous les fichiers non étiquetés dans le référentiel sont étiquetés avec l’étiquette par défaut spécifiée pour le dépôt ou le travail d’analyse de contenu. Les fichiers sont étiquetés sans inspection.

Configurez les paramètres suivants :

|Setting  |Description  |
|---------|---------|
|**Étiqueter des fichiers en fonction du contenu**    |Définir sur **Désactivé**         |
|**Étiquette par défaut**     | Définir sur **Personnalisé**, puis sélectionner l’étiquette à utiliser       |
|**Appliquer l’étiquette par défaut**     | Sélectionnez cette option pour que l’étiquette par défaut soit appliquée à tous les fichiers, même s’ils sont déjà étiquetés en activant **Relabel files** et **Enforce default label** on        |

### <a name="remove-existing-labels-from-all-files-in-a-data-repository"></a>Supprimer des étiquettes existantes de tous les fichiers d’un référentiel de données

Dans cette configuration, toutes les étiquettes existantes sont supprimées, y compris la protection, si la protection a été appliquée avec l’étiquette. La protection appliquée indépendamment d’une étiquette est conservée.

Configurez les paramètres suivants :

|Setting  |Description  |
|---------|---------|
|**Étiqueter des fichiers en fonction du contenu**    |Définir sur **Désactivé**         |
|**Étiquette par défaut**     | Définir sur **Aucun**  |
|**Réétiqueter des fichiers** | Défini **sur Activé**, avec l’étiquette **Appliquer par défaut** définie **sur Activé**|

### <a name="identify-all-custom-conditions-and-known-sensitive-information-types"></a>Identifier toutes les conditions personnalisées et les types d’informations sensibles connus

Cette configuration vous permet de rechercher des informations sensibles que vous ne réalisez peut-être pas, au détriment des taux d’analyse du scanneur.

Définissez les **types d’informations à découvrir sur** **Tous**.

Pour identifier les conditions et les types d’informations pour l’étiquetage, le scanneur utilise tous les types d’informations sensibles personnalisés spécifiés, ainsi que la liste des types d’informations sensibles intégrés disponibles pour la sélection, comme défini dans votre centre de gestion de l’étiquetage.

## <a name="optimize-scanner-performance"></a>Optimiser les performances du scanneur

> [!NOTE]
> Si vous cherchez à améliorer la réactivité de l’ordinateur du scanneur plutôt que les performances du scanneur, utilisez un paramètre client avancé pour [limiter le nombre de threads utilisés par le scanneur](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#limit-the-number-of-threads-used-by-the-scanner).

Utilisez les options et conseils suivants pour vous aider à optimiser les performances du scanneur :

|Option  |Description  |
|---------|---------|
|**Disposer d’une connexion réseau rapide et fiable entre l’ordinateur du scanneur et le magasin de données analysé**     |  Par exemple, placez l’ordinateur du scanneur dans le même réseau local, ou de préférence, dans le même segment réseau que le magasin de données analysé. <br /><br />La qualité de la connexion réseau affecte les performances du scanneur, car, pour inspecter les fichiers, le scanneur transfère le contenu des fichiers à l’ordinateur exécutant le service de scanneur. <br /><br />La réduction ou l’élimination des tronçons réseau nécessaires au déplacement des données réduit également la charge sur votre réseau.      |
|**Assurez-vous que l’ordinateur du scanneur dispose des ressources de processeur disponibles**     | L’inspection du contenu des fichiers et le chiffrement et le déchiffrement des fichiers sont des actions nécessitant beaucoup de processeurs. <br /><br />Surveillez les cycles d’analyse classiques de vos magasins de données spécifiés pour déterminer si un manque de ressources de processeur affecte négativement les performances du scanneur.        |
|**Installer plusieurs instances du scanneur** | Le scanneur prend en charge plusieurs bases de données de configuration sur la même instance SQL Server lorsque vous spécifiez un nom de cluster personnalisé pour le scanneur. <br /><br />**Conseil** : plusieurs scanneurs peuvent également partager le même cluster, ce qui accélère les temps d’analyse. Si vous envisagez d’installer le scanneur sur plusieurs ordinateurs avec la même instance de base de données et que vous souhaitez que vos scanneurs s’exécutent en parallèle, vous devez installer tous vos scanneurs avec le même nom de cluster.|
|**Vérifier l’utilisation de votre autre configuration** |Le scanneur s’exécute plus rapidement lorsque vous utilisez [l’autre configuration](#use-the-scanner-with-alternative-configurations) pour appliquer une étiquette par défaut à tous les fichiers, car le scanneur n’inspecte pas le contenu du fichier. <br/><br />Le scanneur s’exécute plus lentement lorsque vous utilisez [l’autre configuration](#use-the-scanner-with-alternative-configurations) pour identifier toutes les conditions personnalisées et les types d’informations sensibles connus.|

### <a name="additional-factors-that-affect-performance"></a>Facteurs supplémentaires qui affectent les performances

Les facteurs supplémentaires qui affectent les performances du scanneur sont les suivants :

|Facteur  |Description  |
|---------|---------|
|**Temps de chargement/réponse**     |Les temps de chargement et de réponse actuels des magasins de données qui contiennent les fichiers à analyser affecteront également les performances du scanneur.         |
|**Mode Scanneur** (découverte/application)    | Le mode de découverte a généralement un taux d’analyse plus élevé que le mode d’application. <br /><br />La découverte nécessite une seule action de lecture de fichier, tandis que le mode d’application nécessite des actions de lecture et d’écriture.        |
|**Modifications de stratégie**     |Les performances de votre scanneur peuvent être affectées si vous avez apporté des modifications à l’étiquetage automatique dans la stratégie d’étiquette. <br /><br />Votre premier cycle d’analyse, lorsque le scanneur doit inspecter chaque fichier, prend plus de temps que les cycles d’analyse suivants qui, par défaut, inspectent uniquement les fichiers nouveaux et modifiés. <br /><br />Si vous modifiez les conditions ou les paramètres d’étiquetage automatique, tous les fichiers sont analysés à nouveau. Pour plus d’informations, consultez [Rescanning files](deploy-scanner-manage.md#rescanning-files).|
|**Constructions Regex**    | Les performances du scanneur sont affectées par la façon dont vos expressions regex pour les conditions personnalisées sont construites. <br /><br /> Pour éviter une consommation importante de mémoire et le risque de délais d’expiration (15 minutes par fichier), passez en revue vos expressions regex pour obtenir une correspondance de modèle efficace. <br /><br />Par exemple : <br />- Éviter les [quantificateurs gourmands](/dotnet/standard/base-types/quantifiers-in-regular-expressions) <br />- Utiliser des groupes de non-capture tels que `(?:expression)``(expression)`    |
|**Niveau du journal**     |  Les options de niveau journal incluent **Débogage**, **Informations**, **Erreur** et **Désactivé** pour les rapports du scanneur.<br /><br />- **Les résultats désactivés** donnent les meilleures performances <br />- **Le débogage** ralentit considérablement le scanneur et ne doit être utilisé que pour la résolution des problèmes. <br /><br />Pour plus d’informations, consultez le paramètre *ReportLevel* pour l’applet de commande [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) .       |
|**Fichiers analysés**     |- À l’exception des fichiers Excel, les fichiers Office sont analysés plus rapidement que les fichiers PDF. <br /><br />- Les fichiers non protégés sont plus rapides à analyser que les fichiers protégés. <br /><br />- Les fichiers volumineux prennent évidemment plus de temps à analyser que les petits fichiers.         |

## <a name="use-powershell-to-configure-the-scanner"></a>Utiliser PowerShell pour configurer le scanneur

Cette section décrit les étapes requises pour configurer et installer le scanneur lorsque vous n’avez pas accès aux pages du scanneur dans le portail de conformité Microsoft Purview et que vous devez utiliser PowerShell uniquement.

> [!IMPORTANT]
> - Certaines étapes nécessitent Que PowerShell soit en mesure d’accéder aux pages du scanneur dans le portail de conformité et soient identiques. Pour ces étapes, consultez les instructions précédentes de cet article, comme indiqué.
>
> - Si vous utilisez le scanneur pour Azure China 21Vianet, des étapes supplémentaires sont nécessaires en plus des instructions détaillées ici. Pour plus d’informations, consultez la [prise en charge d’Azure Information Protection pour les Office 365 gérées par 21Vianet](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection).

Pour plus d’informations, consultez les [applets de commande PowerShell prises en charge](#supported-powershell-cmdlets).

**Pour configurer et installer votre scanneur** :

1. Commencez par la fermeture de PowerShell. Si vous avez déjà installé le client et le scanneur AIP, assurez-vous que le service **AIPScanner** est arrêté.

2. Ouvrez une session Windows PowerShell avec l’option **Exécuter en tant qu’administrateur**.

3. Exécutez la commande [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) pour installer votre scanneur sur votre instance SQL Server, avec le paramètre **cluster** pour définir le nom de votre cluster.

    Cette étape est identique, que vous puissiez ou non accéder aux pages du scanneur dans le portail de conformité. Pour plus d’informations, consultez les instructions précédentes de cet article : [Installer le scanneur](#install-the-scanner)

4. Obtenez un jeton Azure à utiliser avec votre scanneur, puis réauthenticatez. 

    Cette étape est identique, que vous puissiez ou non accéder aux pages du scanneur dans le portail de conformité. Pour plus d’informations, consultez les instructions précédentes de cet article : [Obtenir un jeton Azure AD pour le scanneur](#get-an-azure-ad-token-for-the-scanner).

5. <a name="powershell"></a>Exécutez l’applet de commande [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) pour définir le scanneur pour qu’il fonctionne en mode hors connexion. Courir:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

6. Exécutez l’applet [de commande Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) pour créer un travail d’analyse de contenu par défaut.

    Le seul paramètre requis dans l’applet de commande **Set-AIPScannerContentScanJob** est **Enforce**. Toutefois, vous pouvez définir d’autres paramètres pour votre travail d’analyse de contenu pour le moment. Par exemple :

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    La syntaxe ci-dessus configure les paramètres suivants pendant que vous poursuivez la configuration :

    - Maintient manuellement la *planification de* l’exécution du scanneur
    - Définit les types d’informations à découvrir en fonction de la stratégie d’étiquette de confidentialité
    - *N’applique pas* de stratégie d’étiquette de confidentialité
    - Étiquettes automatiques des fichiers en fonction du contenu, à l’aide de l’étiquette par défaut définie pour la stratégie d’étiquette de confidentialité
    - Ne permet *pas* de réétiqueter des fichiers
    - Conserve les détails du fichier lors de l’analyse et de l’étiquetage automatique, y compris la *date de modification*, *la dernière modification* et *la modification par* les valeurs
    - Définit le scanneur pour exclure les fichiers .msg et .tmp lors de l’exécution
    - Définit le propriétaire par défaut sur le compte que vous souhaitez utiliser lors de l’exécution du scanneur

7. Utilisez l’applet de commande [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) pour définir les référentiels que vous souhaitez analyser dans votre travail d’analyse de contenu. Par exemple, exécutez :

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```

    Utilisez l’une des syntaxes suivantes, selon le type de référentiel que vous ajoutez :

    - Pour un partage réseau, utilisez `\\Server\Folder`.
    - Pour une bibliothèque SharePoint, utilisez `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - Pour un chemin local : `C:\Folder`
    - Pour un chemin UNC : `\\Server\Folder`

    > [!NOTE]
    > Les caractères génériques ne sont pas pris en charge et les emplacements WebDav ne sont pas pris en charge.
    >
    > Pour modifier le référentiel ultérieurement, utilisez plutôt l’applet de commande [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) . 

    Si vous ajoutez un chemin SharePoint pour **les documents partagés** :
    - Spécifiez **documents partagés** dans le chemin d’accès lorsque vous souhaitez analyser tous les documents et tous les dossiers à partir de documents partagés.
    Par exemple : `http://sp2013/SharedDocuments`
    - Spécifiez **Documents** dans le chemin d’accès lorsque vous souhaitez analyser tous les documents et tous les dossiers à partir d’un sous-dossier sous Documents partagés.
    Par exemple : `http://sp2013/Documents/SalesReports`
    - Vous pouvez également spécifier uniquement le **nom** de domaine complet de votre sharepoint, par exemple `http://sp2013` pour [découvrir et analyser tous les sites et sous-sites SharePoint sous une URL](deploy-scanner-prereqs.md#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url) et des sous-titres spécifiques sous cette URL. Accordez aux **vérificateurs** de site du scanneur des droits d’auditeur pour l’activer.


    Utilisez la syntaxe suivante lors de l’ajout de chemins SharePoint :

    |Path  |Syntaxe  |
    |---------|---------|
    |**Chemin d’accès racine**     | `http://<SharePoint server name>` <br /><br />Analyse tous les sites, y compris les collections de sites autorisées pour l’utilisateur du scanneur. <br />Nécessite [des autorisations supplémentaires](/previous-versions/azure/information-protection/quickstart-findsensitiveinfo#permission-users-to-scan-sharepoint-repositories) pour découvrir automatiquement le contenu racine        |
    |**Sous-site ou collection SharePoint spécifique**     | Un des éléments suivants : <br />- `http://<SharePoint server name>/<subsite name>` <br />- `http://SharePoint server name>/<site collection name>/<site name>` <br /><br />Nécessite [des autorisations supplémentaires](/previous-versions/azure/information-protection/quickstart-findsensitiveinfo#permission-users-to-scan-sharepoint-repositories) pour découvrir automatiquement le contenu de la collection de sites         |
    |**Bibliothèque SharePoint spécifique**     | Un des éléments suivants : <br />- `http://<SharePoint server name>/<library name>` <br />- `http://SharePoint server name>/.../<library name>`       |
    |**Dossier SharePoint spécifique**     | `http://<SharePoint server name>/.../<folder name>`        |

Suivez les étapes suivantes en fonction des besoins :

- [Configuration pour les clients en Chine](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection)
- [Exécuter un cycle de découverte et afficher les rapports pour le scanneur](deploy-scanner-manage.md#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Utiliser PowerShell pour configurer le scanneur pour appliquer la classification et la protection](#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Utiliser PowerShell pour configurer une stratégie DLP avec le scanneur](#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

### <a name="use-powershell-to-configure-the-scanner-to-apply-classification-and-protection"></a>Utiliser PowerShell pour configurer le scanneur pour appliquer la classification et la protection

1. Exécutez l’applet de commande [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) pour mettre à jour votre travail d’analyse de contenu afin de définir votre planification de manière à toujours appliquer votre stratégie de confidentialité.

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Always -Enforce On
    ```

    > [!TIP]
    > Vous pouvez modifier d’autres paramètres dans ce volet, par exemple si les attributs de fichier sont modifiés et si le scanneur peut réétiqueter des fichiers. Pour plus d’informations sur les paramètres disponibles, consultez la [documentation PowerShell](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) complète.

2. Exécutez l’applet [de commande Start-AIPScan](/powershell/module/azureinformationprotection/start-aipscan) pour exécuter votre travail d’analyse de contenu :

    ```PowerShell
    Start-AIPScan
    ```

Le scanneur est maintenant planifié pour s’exécuter en continu. Lorsque le scanneur parcourt tous les fichiers configurés, il démarre automatiquement un nouveau cycle afin que tous les fichiers nouveaux et modifiés soient découverts.

### <a name="use-powershell-to-configure-a-dlp-policy-with-the-scanner"></a>Utiliser PowerShell pour configurer une stratégie DLP avec le scanneur

Exécutez à nouveau l’applet de commande [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) avec le paramètre **-EnableDLP** défini **sur Activé** et un propriétaire de référentiel spécifique défini.

Par exemple :

```powershell
Set-AIPScannerContentScanJob -EnableDLP On -RepositoryOwner 'domain\user'
```

## <a name="supported-powershell-cmdlets"></a>Applets de commande PowerShell prises en charge

Cette section répertorie les applets de commande PowerShell prises en charge pour le scanneur de protection des informations et les instructions de configuration et d’installation du scanneur avec PowerShell uniquement.

Les applets de commande prises en charge pour le scanneur sont les suivantes :

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository)

- [Export-AIPLogs](/powershell/module/azureinformationprotection/Export-AIPLogs)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Get-MIPNetworkDiscoveryConfiguration](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryConfiguration)

- [Get-MIPNetworkDiscoveryJobs](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryJobs)

- [Get-MIPNetworkDiscoveryStatus](/powershell/module/azureinformationprotection/Get-MIPNetworkDiscoveryStatus)

- Get-MIPScannerContentScanJob

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository)

- [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration)

- [Set-MIPNetworkDiscovery](/powershell/module/azureinformationprotection/set-mipnetworkdiscovery)

- [Import-MIPNetworkDiscoveryConfiguration](/powershell/module/azureinformationprotection/Import-MIPNetworkDiscoveryConfiguration)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Install-MIPNetworkDiscovery](/powershell/module/azureinformationprotection/Install-MIPNetworkDiscovery)

- Remove-MIPScannerContentScanJob

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob)

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository)

- [Set-MIPNetworkDiscoveryConfiguration](/powershell/module/azureinformationprotection/Set-MIPNetworkDiscoveryConfiguration)

- Set-MIPScannerContentScanJob

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Start-AIPScanDiagnostics](/powershell/module/azureinformationprotection/Start-AIPScannerDiagnostics)

- [Start-MIPNetworkDiscovery](/powershell/module/azureinformationprotection/Start-MIPNetworkDiscovery)

- [Stop-AIPScan](/powershell/module/azureinformationprotection/Stop-AIPScan)

- [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Uninstall-MIPNetworkDiscovery](/powershell/module/azureinformationprotection/Uninstall-MIPNetworkDiscovery)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez installé et configuré votre scanneur, commencez à [analyser vos fichiers](deploy-scanner-manage.md).