---
title: Configurer et valider les connexions réseau à un antivirus Microsoft Defender
description: Configurez et testez votre connexion au service de protection cloud Antivirus Microsoft Defender.
keywords: antivirus, Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, défenseur, cloud, agressivité, niveau de protection
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/03/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 70360ac3b9ade0e6039239fe257d83c7ba3a2db0
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787601"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Configurer et valider les connexions réseau à un antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Pour vous assurer que Antivirus Microsoft Defender protection fournie par le cloud fonctionne correctement, votre équipe de sécurité doit configurer votre réseau pour autoriser les connexions entre vos points de terminaison et certains serveurs Microsoft. Cet article répertorie les connexions qui doivent être autorisées à utiliser les règles de pare-feu. Il fournit également des instructions pour valider votre connexion. La configuration correcte de votre protection garantit que vous recevez la meilleure valeur de vos services de protection fournis par le cloud.

> [!IMPORTANT]
> Cet article contient des informations sur la configuration des connexions réseau uniquement pour Antivirus Microsoft Defender. Si vous utilisez Microsoft Defender pour point de terminaison (qui inclut Antivirus Microsoft Defender), consultez [Configurer le proxy d’appareil et les paramètres de connectivité Internet pour Defender pour point de terminaison](configure-proxy-internet.md).


> [!NOTE]
> Le site de démonstration Defender pour point de terminaison sur demo.wd.microsoft.com est déconseillé et sera supprimé à l’avenir.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Autoriser les connexions au service cloud Antivirus Microsoft Defender

Le service cloud Antivirus Microsoft Defender offre une protection rapide et forte pour vos points de terminaison. Il est facultatif d’activer le service de protection fourni par le cloud. Antivirus Microsoft Defender service cloud est recommandé, car il offre une protection importante contre les programmes malveillants sur vos points de terminaison et votre réseau. Pour plus d’informations, consultez [Activer la protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) pour activer le service avec des Intune, des Microsoft Endpoint Configuration Manager, des stratégie de groupe, des applets de commande PowerShell ou des clients individuels dans l’application Sécurité Windows.

Une fois que vous avez activé le service, vous devez configurer votre réseau ou pare-feu pour autoriser les connexions entre le réseau et vos points de terminaison. Étant donné que votre protection est un service cloud, les ordinateurs doivent avoir accès à Internet et atteindre les services cloud Microsoft. N’excluez pas l’URL `*.blob.core.windows.net` d’un type d’inspection réseau.

> [!NOTE]
> Le service cloud Antivirus Microsoft Defender fournit une protection mise à jour à votre réseau et à vos points de terminaison. Le service cloud ne doit pas être considéré comme une protection uniquement pour vos fichiers stockés dans le cloud ; Au lieu de cela, le service cloud utilise des ressources distribuées et le Machine Learning pour fournir une protection pour vos points de terminaison à un rythme plus rapide que les mises à jour traditionnelles du renseignement de sécurité.

## <a name="services-and-urls"></a>Services et URL

Le tableau de cette section répertorie les services et leurs adresses de site web associées ( URL).

Assurez-vous qu’il n’existe aucune règle de filtrage réseau ni de pare-feu ni de refus d’accès à ces URL. Sinon, vous devez créer une règle d’autorisation spécifique pour ces URL (à l’exception de l’URL `*.blob.core.windows.net`). Les URL du tableau suivant utilisent le port 443 pour la communication.

<br/><br/>

|Service et description|URL|
|---|---|
|Antivirus Microsoft Defender service de protection fourni dans le cloud est appelé Microsoft Active Protection Service (MAPS).<p> Le Antivirus Microsoft Defender utilise le service MAPS pour fournir une protection fournie par le cloud.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) et Windows Update Service (WU) <p>Ces services permettront des mises à jour des produits et des informations de sécurité.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Pour plus d’informations, consultez [Points de terminaison de connexion pour Windows Update](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Mise à jour du renseignement de sécurité - Autre emplacement de téléchargement (ADL)<p>Il s’agit d’un autre emplacement pour Antivirus Microsoft Defender mises à jour du renseignement de sécurité, si le renseignement de sécurité installé est obsolète (sept jours ou plus de retard).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Stockage de soumission de programmes malveillants <p>Il s’agit d’un emplacement de chargement pour les fichiers envoyés à Microsoft via le formulaire d’envoi ou l’exemple de soumission automatique.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Liste de révocation de certificats (CRL) <p> Windows utiliser cette liste lors de la création de la connexion SSL à MAPS pour mettre à jour la liste de révocation de certificats.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Magasin de symboles <p>Antivirus Microsoft Defender utiliser le magasin de symboles pour restaurer certains fichiers critiques pendant les flux de correction.|`https://msdl.microsoft.com/download/symbols`|
|Client RGPD universel <p> Windows utiliser ce client pour envoyer les données de diagnostic client. <p> Antivirus Microsoft Defender utilise le Règlement général sur la protection des données à des fins de qualité des produits et de surveillance.|La mise à jour utilise SSL (port TCP 443) pour télécharger des manifestes et charger des données de diagnostic vers Microsoft qui utilise les points de terminaison DNS suivants : <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Valider les connexions entre votre réseau et le cloud

Après avoir autorisé les URL répertoriées, testez si vous êtes connecté au service cloud Antivirus Microsoft Defender. Testez que les URL signalent et reçoivent correctement des informations pour vous assurer que vous êtes entièrement protégé.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Utiliser l’outil de ligne de commande pour valider la protection fournie par le cloud

Utilisez l’argument suivant avec l’utilitaire de ligne de commande Antivirus Microsoft Defender (`mpcmdrun.exe`) pour vérifier que votre réseau peut communiquer avec le service cloud Antivirus Microsoft Defender :

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Ouvrez l’invite de commandes en tant qu’administrateur. Cliquez avec le bouton droit sur l’élément dans le menu **Démarrer** , cliquez sur **Exécuter en tant qu’administrateur** , puis cliquez sur **Oui** à l’invite d’autorisations. Cette commande fonctionne uniquement sur Windows 10, version 1703 ou ultérieure, ou Windows 11.

Pour plus d’informations, consultez [Gérer les Antivirus Microsoft Defender avec l’outil de ligne de commande mpcmdrun.exe](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Tentative de téléchargement d’un fichier de logiciels malveillants factice à partir de Microsoft

Vous pouvez télécharger un exemple de fichier que Antivirus Microsoft Defender détectera et bloquera si vous êtes correctement connecté au cloud. Visitez cette page [https://aka.ms/ioavtest](https://aka.ms/ioavtest) pour télécharger le fichier.

> [!NOTE]
> Le fichier téléchargé n’est pas exactement un programme malveillant. Il s’agit d’un faux fichier conçu pour tester si vous êtes correctement connecté au cloud.

Si vous êtes correctement connecté, un avertissement Antivirus Microsoft Defender notification s’affiche.

Si vous utilisez Microsoft Edge, un message de notification s’affiche :

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Notification indiquant que des programmes malveillants ont été détectés dans Edge" lightbox="../../media/wdav-bafs-edge.png":::

Un message similaire se produit si vous utilisez Internet Explorer :

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Notification microsoft Defender AV indiquant que des programmes malveillants ont été détectés" lightbox="../../media/wdav-bafs-ie.png":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Afficher la détection de logiciels malveillants factices dans votre application Sécurité Windows

1. Dans la barre des tâches, sélectionnez l’icône Bouclier, puis ouvrez l’application **Sécurité Windows**. Vous pouvez également rechercher la *sécurité* dans le **menu Démarrer**.

2. Sélectionnez **Virus & protection contre les menaces**, puis sélectionnez **Historique de protection**.

3. Dans la section **Menaces mises en quarantaine** , sélectionnez **Afficher l’historique complet** pour voir les logiciels malveillants détectés.

   > [!NOTE]
   > Les versions de Windows 10 antérieures à la version 1703 ont une interface utilisateur différente. Consultez [Antivirus Microsoft Defender dans l’application Sécurité Windows](microsoft-defender-security-center-antivirus.md).

   Le journal des événements Windows affiche également [Windows Defender ID d’événement client 1116](troubleshoot-microsoft-defender-antivirus.md).

    > [!TIP]
    > Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
    > - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
    > - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
    > - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
    > - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
    > - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
    > - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
    > - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)


## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres de proxy d’appareil et de connectivité Internet pour Microsoft Defender pour point de terminaison](configure-proxy-internet.md)
- [Utiliser stratégie de groupe paramètres pour configurer et gérer Antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [Modifications importantes apportées au point de terminaison Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 