---
title: Antivirus Microsoft Defender dans l'application Sécurité Windows
description: Avec l'Antivirus Microsoft Defender désormais inclus dans l'application Sécurité Windows, vous pouvez examiner, comparer et effectuer des tâches courantes.
keywords: wdav, antivirus, pare-feu, sécurité, fenêtres
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7635209c03dfc0367df16bfb650a4e52d2b2b3f8
ms.sourcegitcommit: 7a339c9f7039825d131b39481ddf54c57b021b11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2021
ms.locfileid: "51765322"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Antivirus Microsoft Defender dans l'application Sécurité Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Dans Windows 10, version 1703 et ultérieure, l'application Windows Defender fait partie de la sécurité Windows.

Les paramètres qui faisaient auparavant partie du client Windows Defender et des principaux paramètres Windows ont été combinés et déplacés vers la nouvelle application, installée par défaut dans le cadre de Windows 10, version 1703.

> [!IMPORTANT]
> La désactivation du service Centre de sécurité Windows ne désactive pas l'Antivirus Microsoft Defender [ou Windows Defender pare-feu.](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) Ceux-ci sont désactivés automatiquement lorsqu'un antivirus tiers ou un produit de pare-feu est installé et maintenu à jour.
>
> Si vous désactivez le service Centre de sécurité Windows ou si vous configurez ses paramètres de stratégie de groupe associés pour empêcher son démarrage ou son exécution, l'application Sécurité Windows peut afficher des informations obsolètes ou inexactes sur les produits antivirus ou pare-feu que vous avez installés sur l'appareil.
> Il peut également empêcher l'Antivirus Microsoft Defender de s'activer si vous avez un antivirus tiers ancien ou obsolète, ou si vous désinstallez des produits antivirus tiers que vous avez peut-être précédemment installés.
> Cela réduit considérablement la protection de votre appareil et peut entraîner une infection par des programmes malveillants.

Consultez [l'article Sécurité Windows](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) pour plus d'informations sur les autres fonctionnalités de sécurité Windows qui peuvent être surveillées dans l'application.

L'application Sécurité Windows est une interface client sur Windows 10, version 1703 et ultérieure. Ce n'est pas le portail web du Centre de sécurité Microsoft Defender qui est utilisé pour passer en revue et gérer [Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Passer en revue les paramètres de protection contre les virus et menaces dans l'application Sécurité Windows

![Capture d'écran de l'étiquette & protection contre les virus dans l'application Sécurité Windows](images/defender/wdav-protection-settings-wdsc.png)

1. Ouvrez l'application Sécurité Windows en cliquant sur l'icône de bouclier dans la barre des tâches ou en recherchant Defender dans le menu **Démarrer.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).
   
Les sections suivantes décrivent comment effectuer certaines des tâches les plus courantes lors de l'examen ou de l'interaction avec la protection contre les menaces fournie par l'Antivirus Microsoft Defender dans l'application Sécurité Windows.

> [!NOTE]
> Si ces paramètres sont configurés et déployés à l'aide de la stratégie de groupe, les paramètres décrits dans cette section sont grisés et ne peuvent pas être utilisés sur des points de terminaison individuels. Les modifications apportées via un objet de stratégie de groupe doivent d'abord être déployées sur des points de terminaison individuels avant que le paramètre ne soit mis à jour dans les paramètres Windows. La [rubrique Configurer l'interaction de l'utilisateur final avec l'Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) décrit comment configurer les paramètres de remplacement de stratégie locale.

## <a name="run-a-scan-with-the-windows-security-app"></a>Exécuter une analyse avec l'application Sécurité Windows

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu **Démarrer,** puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sélectionnez **Analyse rapide.** Ou, pour exécuter une analyse complète, sélectionnez **Options** d'analyse, puis sélectionnez une option, telle que **l'analyse complète**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Passer en revue la version de mise à jour de l'intelligence de la sécurité et télécharger les dernières mises à jour dans l'application Sécurité Windows

![Informations sur le numéro de version de l'intelligence de la sécurité](images/defender/wdav-wdsc-defs.png)

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu *Démarrer,* puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sélectionnez **les mises à jour & protection contre les virus contre les menaces.** La version actuellement installée s'affiche avec des informations sur le moment où elle a été téléchargée. Vous pouvez vérifier votre version actuelle par rapport à la dernière version disponible pour le téléchargement manuel ou consulter le journal des changements pour cette version. Consultez [les mises à jour de l'intelligence de sécurité pour l'Antivirus Microsoft Defender et d'autres logiciels anti-programme malveillant Microsoft.](https://www.microsoft.com/en-us/wdsi/defenderupdates)

4. Sélectionnez **Vérifier les mises à jour pour** télécharger les nouvelles mises à jour de la protection (le cas caser).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Vérifier que l'Antivirus Microsoft Defender est activé dans l'application Sécurité Windows

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu *Démarrer,* puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sélectionnez **les paramètres & protection contre les virus contre les menaces.**

4. Basculez le **commutateur de protection en temps** réel sur **Sur**.

    > [!NOTE]
    > Si vous **éteyez la protection en** temps réel, elle est automatiquement réaxion après un court délai. Cela permet de vous assurer que vous êtes protégé contre les programmes malveillants et les menaces.
    > Si vous installez un autre produit antivirus, l'Antivirus Microsoft Defender se désactive automatiquement et est indiqué en tant que tel dans l'application Sécurité Windows. Un paramètre s'affiche pour vous permettre d'activer [l'analyse périodique limitée.](limited-periodic-scanning-microsoft-defender-antivirus.md)

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Ajouter des exclusions pour l'Antivirus Microsoft Defender dans l'application Sécurité Windows

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu *Démarrer,* puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sous les **paramètres Gérer,** sélectionnez Paramètres de protection contre & virus et **menaces.**

4. Sous le **paramètre Exclusions,** **sélectionnez Ajouter ou supprimer des exclusions.** 

5. Sélectionnez l'icône plus ( **+** ) pour choisir le type et définir les options pour chaque exclusion. 

Le tableau suivant récapitule les types d'exclusion et ce qui se produit :

|Type d'exclusion  |Défini par  |Action exécutée  |
|---------|---------|---------|
|**Fichier** |Emplacement <br/>Exemple : `c:\sample\sample.test` |Le fichier spécifique est ignoré par l'Antivirus Microsoft Defender. |
|**Folder**    |Emplacement <br/>Exemple : `c:\test\sample`       |Tous les éléments du dossier spécifié sont ignorés par l'Antivirus Microsoft Defender.         |
|**Type de fichier**   |Extension de fichier <br/>Exemple : `.test` |Tous les fichiers avec `.test` l'extension n'importe où sur votre appareil sont ignorés par l'Antivirus Microsoft Defender.         |
|**Processus**     |Chemin d'accès au fichier exécutable <br>Exemple : `c:\test\process.exe`         |Le processus spécifique et tous les fichiers ouverts par ce processus sont ignorés par l'Antivirus Microsoft Defender.         |

Pour en savoir plus, consultez les ressources suivantes :
- [Configurer et valider des exclusions en fonction de l'extension de fichier et de l'emplacement du dossier](./configure-extension-file-exclusions-microsoft-defender-antivirus.md) 
- [Configurer des exclusions pour les fichiers ouverts par des processus](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-security-center-app"></a>Passer en revue l'historique de détection des menaces dans Windows Defender'application Centre de sécurité

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu *Démarrer,* puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sélectionnez **l'historique de la protection.** Tous les éléments récents sont répertoriés.

## <a name="set-ransomware-protection-and-recovery-options"></a>Définir les options de protection et de récupération des ransomware

1. Ouvrez l'application Sécurité Windows en recherchant sécurité dans le menu *Démarrer,* puis en sélectionnant **Sécurité Windows.**

2. Sélectionnez la **vignette & protection contre** les virus contre les menaces (ou l'icône de bouclier dans la barre de menus de gauche).

3. Sous Protection **contre les ransomware,** **sélectionnez Gérer la protection contre les ransomware.**

4. Pour modifier **les paramètres d'accès contrôlé aux** dossiers, voir Protéger les dossiers importants avec accès contrôlé aux [dossiers.](/microsoft-365/security/defender-endpoint/controlled-folders)

5. Pour configurer les options  de récupération  de ransomware, sélectionnez Configurer sous Récupération des données de ransomware et suivez les instructions pour lier ou configurer votre compte OneDrive afin de pouvoir facilement récupérer d'une attaque par ransomware.

## <a name="see-also"></a>Voir aussi
- [Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)