---
title: Antivirus Microsoft Defender dans l’application Sécurité Windows
description: L’Antivirus Microsoft Defender étant désormais inclus dans l’application Sécurité Windows, vous pouvez passer en revue, comparer et effectuer des tâches courantes.
keywords: wdav, antivirus, pare-feu, sécurité, windows, antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: e661667802f5d170261c51bd6bc706eddfdcbf42
ms.sourcegitcommit: d09eb780dc41a01796eb8137fbe9267231af6746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2022
ms.locfileid: "67387416"
---
# <a name="microsoft-defender-antivirus-in-the-windows-security-app"></a>Antivirus Microsoft Defender dans l’application Sécurité Windows

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Dans Windows 10, version 1703 et ultérieure, l’application Windows Defender fait partie du Sécurité Windows.

Les paramètres qui faisaient auparavant partie du client Windows Defender et des paramètres Windows principaux ont été combinés et déplacés vers la nouvelle application, qui est installée par défaut dans le cadre de Windows 10 version 1703.

> [!IMPORTANT]
> La désactivation du service d’application Sécurité Windows ne désactive pas l’antivirus Microsoft Defender ni [le pare-feu Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Ceux-ci sont désactivés automatiquement lorsqu’un antivirus ou un produit de pare-feu tiers est installé et mis à jour.
> Si vous désactivez le service d’application Sécurité Windows ou configurez ses paramètres de stratégie de groupe associés pour l’empêcher de démarrer ou de s’exécuter, l’application Sécurité Windows peut afficher des informations obsolètes ou inexactes sur les produits antivirus ou de pare-feu que vous avez installés sur l’appareil.
> Cela peut également empêcher l’antivirus Microsoft Defender de s’activer si vous disposez d’un antivirus tiers ancien ou obsolète, ou si vous désinstallez des produits antivirus tiers que vous avez peut-être déjà installés.
> Cela réduit considérablement la protection de votre appareil et peut entraîner une infection par des programmes malveillants.

Consultez [l’article Sécurité Windows](/windows/threat-protection/windows-defender-security-center/windows-defender-security-center) pour plus d’informations sur les autres fonctionnalités de sécurité Windows qui peuvent être surveillées dans l’application.

L’application Sécurité Windows est une interface cliente sur Windows 10, version 1703 et ultérieure. Ce n’est pas le portail web Microsoft 365 Defender qui est utilisé pour examiner et gérer [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint).

## <a name="review-virus-and-threat-protection-settings-in-the-windows-security-app"></a>Examiner les paramètres de protection contre les virus et les menaces dans l’application Sécurité Windows

:::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Paramètres de protection contre les virus et les menaces dans Sécurité Windows application" lightbox="../../media/wdav-protection-settings-wdsc.png":::

1. Ouvrez l’application Sécurité Windows en cliquant sur l’icône du bouclier dans la barre des tâches ou en recherchant **Sécurité Windows** dans le menu démarrer.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

Les sections suivantes décrivent comment effectuer certaines des tâches les plus courantes lors de l’examen ou de l’interaction avec la protection contre les menaces fournie par l’Antivirus Microsoft Defender dans l’application Sécurité Windows.

> [!NOTE]
> Si ces paramètres sont configurés et déployés à l’aide de stratégie de groupe, les paramètres décrits dans cette section seront grisés et indisponibles pour une utilisation sur des points de terminaison individuels. Les modifications apportées via un objet de stratégie de groupe doivent d’abord être déployées vers les points de terminaison individuels avant que le paramètre soit mis à jour dans les Paramètres Windows. La rubrique [Configurer l’interaction de l’utilisateur final avec l’Antivirus Microsoft Defender](configure-end-user-interaction-microsoft-defender-antivirus.md) décrit comment configurer les paramètres de remplacement de stratégie locale.

## <a name="run-a-scan-with-the-windows-security-app"></a>Exécuter une analyse avec l’application Sécurité Windows

1. Ouvrez l’application Sécurité Windows en recherchant **la sécurité** dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sélectionnez **Analyse rapide**. Ou, pour exécuter une analyse complète, sélectionnez **Options** d’analyse, puis sélectionnez une option, telle que **l’analyse complète**.

## <a name="review-the-security-intelligence-update-version-and-download-the-latest-updates-in-the-windows-security-app"></a>Passez en revue la version de la mise à jour du renseignement de sécurité et téléchargez les dernières mises à jour dans l’application Sécurité Windows

:::image type="content" source="../../media/wdav-wdsc-defs.png" alt-text="Numéro de version du renseignement de sécurité" lightbox="../../media/wdav-wdsc-defs.png":::

1. Ouvrez l’application Sécurité Windows en recherchant *la sécurité* dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sélectionnez **Virus & mises à jour de la protection contre les menaces**. La version actuellement installée s’affiche avec des informations sur le moment où elle a été téléchargée. Vous pouvez vérifier votre version actuelle par rapport à la dernière version disponible pour téléchargement manuel ou consulter le journal des modifications pour cette version. Consultez [les mises à jour du renseignement de sécurité pour l’antivirus Microsoft Defender et d’autres logiciels anti-programme malveillant Microsoft](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

4. Sélectionnez **Rechercher les mises à jour** pour télécharger les nouvelles mises à jour de protection (le cas échéant).

## <a name="ensure-microsoft-defender-antivirus-is-enabled-in-the-windows-security-app"></a>Vérifier que l’antivirus Microsoft Defender est activé dans l’application Sécurité Windows

1. Ouvrez l’application Sécurité Windows en recherchant *la sécurité* dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sélectionnez **Virus & paramètres de protection contre les menaces**.

4. Basculez le commutateur de **protection en temps réel** **sur Activé**.

    > [!NOTE]
    > Si vous désactivez la **protection en temps réel** , elle s’active automatiquement après un court délai. Cela vous permet de vous assurer que vous êtes protégé contre les programmes malveillants et les menaces.
    > Si vous installez un autre produit antivirus, l’antivirus Microsoft Defender se désactive automatiquement et est indiqué comme tel dans l’application Sécurité Windows. Un paramètre s’affiche pour vous permettre d’activer [l’analyse périodique limitée](limited-periodic-scanning-microsoft-defender-antivirus.md).

## <a name="add-exclusions-for-microsoft-defender-antivirus-in-the-windows-security-app"></a>Ajouter des exclusions pour l’antivirus Microsoft Defender dans l’application Sécurité Windows

1. Ouvrez l’application Sécurité Windows en recherchant *la sécurité* dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sous **Paramètres de protection contre les virus et les menaces**, sélectionnez **Gérer les paramètres**.

4. Sous **Exclusions**, **sélectionnez Ajouter ou supprimer des exclusions**.

5. Sélectionnez l’icône plus (**+**) pour choisir le type et définir les options pour chaque exclusion.

Le tableau suivant récapitule les types d’exclusion et ce qui se passe :

|Type d’exclusion|Défini par|Action exécutée|
|---|---|---|
|**Fichier**|Emplacement <br/>Exemple : `c:\sample\sample.test`|Le fichier spécifique est ignoré par l’Antivirus Microsoft Defender.|
|**Folder**|Emplacement <br/>Exemple : `c:\test\sample`|Tous les éléments du dossier spécifié sont ignorés par l’antivirus Microsoft Defender.|
|**Type de fichier**|Extension de fichier <br/>Exemple : `.test`|Tous les fichiers avec l’extension n’importe `.test` où sur votre appareil sont ignorés par l’antivirus Microsoft Defender.|
|**Processus**|Chemin du fichier exécutable <br>Exemple : `c:\test\process.exe`|Le processus spécifique et tous les fichiers ouverts par ce processus sont ignorés par l’Antivirus Microsoft Defender.|

Pour en savoir plus, consultez les ressources suivantes :

- [Configurer et valider des exclusions en fonction de l’extension de fichier et de l’emplacement du dossier](./configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Configurer des exclusions pour les fichiers ouverts par des processus](./configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="review-threat-detection-history-in-the-windows-defender-for-cloud-app"></a>Passer en revue l’historique de détection des menaces dans le Windows Defender pour l’application cloud

1. Ouvrez l’application Sécurité Windows en recherchant *la sécurité* dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sélectionnez **Historique de protection**. Tous les éléments récents sont répertoriés.

## <a name="set-ransomware-protection-and-recovery-options"></a>Définir les options de protection et de récupération des ransomware

1. Ouvrez l’application Sécurité Windows en recherchant *la sécurité* dans le menu Démarrer, puis en sélectionnant **Sécurité Windows**.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche).

3. Sous **Protection contre les rançongiciels**, **sélectionnez Gérer la protection contre les ransomware**.

4. Pour modifier les paramètres **d’accès contrôlé aux dossiers** , consultez [Protéger les dossiers importants avec accès contrôlé aux dossiers](/microsoft-365/security/defender-endpoint/controlled-folders).

5. Pour configurer les options de récupération de ransomware, sélectionnez **Configurer** sous **Récupération des données ransomware** et suivez les instructions de liaison ou de configuration de votre compte OneDrive afin de pouvoir facilement récupérer après une attaque par ransomware.

## <a name="see-also"></a>Voir aussi

- [Antivirus Microsoft Defender](microsoft-defender-antivirus-in-windows-10.md)
