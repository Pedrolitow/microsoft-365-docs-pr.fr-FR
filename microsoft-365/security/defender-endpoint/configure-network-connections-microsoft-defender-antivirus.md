---
title: Configurer et valider les connexions réseau à un antivirus Microsoft Defender
description: Configurez et testez votre connexion au service Antivirus Microsoft Defender protection cloud.
keywords: antivirus, Antivirus Microsoft Defender, logiciel anti-programme malveillant, sécurité, defender, cloud, aggressiveness, niveau de protection
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
ms.openlocfilehash: f29cf5f77acd52a4ff3ccc8384f3c64861e48b64
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62806035"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Configurer et valider les connexions réseau à un antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Pour garantir Antivirus Microsoft Defender protection assurée par le cloud fonctionne correctement, votre équipe de sécurité doit configurer votre réseau pour autoriser les connexions entre vos points de terminaison et certains serveurs Microsoft. Cet article répertorie les connexions qui doivent être autorisées pour l’utilisation des règles de pare-feu. Il fournit également des instructions pour valider votre connexion. En configurant correctement votre protection, vous bénéficiez de la meilleure valeur de vos services de protection cloud.

> [!IMPORTANT]
> Cet article contient des informations sur la configuration des connexions réseau uniquement pour Antivirus Microsoft Defender. Si vous utilisez Microsoft Defender pour endpoint (qui inclut Antivirus Microsoft Defender), voir Configurer les paramètres de proxy d’appareil et de connectivité [Internet pour Defender pour Endpoint](configure-proxy-internet.md).


> [!NOTE]
> Le site de démonstration Defender for Endpoint demo.wd.microsoft.com est supprimé et sera supprimé à l’avenir.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Autoriser les connexions au service Antivirus Microsoft Defender cloud

Le Antivirus Microsoft Defender cloud fournit une protection rapide et forte pour vos points de terminaison. Il est facultatif d’activer le service de protection cloud. Antivirus Microsoft Defender service cloud est recommandé, car il offre une protection importante contre les programmes malveillants sur vos points de terminaison et votre réseau. Pour plus d’informations, voir Activer la [protection](enable-cloud-protection-microsoft-defender-antivirus.md) cloud pour activer le service avec Intune, Microsoft Endpoint Configuration Manager, la stratégie de groupe, les cmdlets PowerShell ou des clients individuels dans l’application Sécurité Windows.

Après avoir activé le service, vous devez configurer votre réseau ou votre pare-feu pour autoriser les connexions entre le réseau et vos points de terminaison. Étant donné que votre protection est un service cloud, les ordinateurs doivent avoir accès à Internet et accéder aux services cloud de Microsoft. N’excluez pas l’URL `*.blob.core.windows.net` d’un type d’inspection réseau.

> [!NOTE]
> Le Antivirus Microsoft Defender cloud fournit une protection mise à jour à votre réseau et points de terminaison. Le service cloud ne doit pas être considéré comme une protection uniquement pour vos fichiers stockés dans le cloud . Au lieu de cela, le service cloud utilise des ressources distribuées et l’apprentissage automatique pour fournir la protection de vos points de terminaison à un taux plus rapide que les mises à jour d’intelligence de sécurité traditionnelles.

## <a name="services-and-urls"></a>Services et URL

Le tableau de cette section répertorie les services et leurs adresses web associées (URL).

Assurez-vous qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuse l’accès à ces URL. Dans le cas contraire, vous devez créer une règle d’autoriser spécifiquement pour ces URL (à l’exclusion de l’URL `*.blob.core.windows.net`). Les URL du tableau suivant utilisent le port 443 pour la communication.

<br/><br/>

|Service et description|URL|
|---|---|
|Antivirus Microsoft Defender service de protection cloud est appelé Microsoft Active Protection Service (MAPS).<p> Le Antivirus Microsoft Defender utilise le service MAPS pour fournir une protection fournie par le cloud.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) et Windows Update Service (WU) <p>Ces services permettent d’assurer la veille sur la sécurité et les mises à jour des produits.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Pour plus d’informations, voir [Points de terminaison de connexion pour Windows update](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Security intelligence updates Alternate Download Location (ADL)<p>Il s’agit d’un autre emplacement pour Antivirus Microsoft Defender mises à jour de l’intelligence de sécurité, si l’intelligence de sécurité installée est hors service (au moins sept jours après).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Stockage de soumission de programmes malveillants <p>Il s’agit d’un emplacement de téléchargement pour les fichiers envoyés à Microsoft via le formulaire de soumission ou l’envoi automatique d’exemples.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Liste de révocation de certificats (CRL) <p> Windows cette liste lors de la création de la connexion SSL à MAPS pour la mise à jour de la liste de liste de niveau de service.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Magasin de symboles <p>Antivirus Microsoft Defender utiliser le magasin de symboles pour restaurer certains fichiers critiques pendant les flux de correction.|`https://msdl.microsoft.com/download/symbols`|
|Client R GDPR universel <p> Windows ce client pour envoyer les données de diagnostic client. <p> Antivirus Microsoft Defender utilise le Règlement général sur la protection des données à des fins de qualité et de surveillance des produits.|La mise à jour utilise SSL (port TCP 443) pour télécharger des manifestes et charger des données de diagnostic vers Microsoft qui utilise les points de terminaison DNS suivants : <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Valider les connexions entre votre réseau et le cloud

Après avoir permis aux URL répertoriées, testez si vous êtes connecté au service Antivirus Microsoft Defender cloud. Testez que les URL sont correctement des rapports et la réception d’informations pour vous assurer que vous êtes entièrement protégé.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Utiliser l’outil cmdline pour valider la protection cloud

Utilisez l’argument suivant avec l Antivirus Microsoft Defender de ligne de commande (`mpcmdrun.exe`) pour vérifier que votre réseau peut communiquer avec Antivirus Microsoft Defender service cloud :

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Ouvrez l’invite de commandes en tant qu’administrateur. Cliquez avec le bouton droit sur l’élément dans le menu **Démarrer** , cliquez sur Exécuter **en** tant qu’administrateur et cliquez sur **Oui** à l’invite d’autorisations. Cette commande ne fonctionne que sur Windows 10 version 1703 ou supérieure, ou sur Windows 11.

Pour plus d’informations, [voir Gérer Antivirus Microsoft Defender’aide de lmpcmdrun.exe de ligne de commande.](command-line-arguments-microsoft-defender-antivirus.md)

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Tentative de téléchargement d’un fichier de programmes malveillants factices à partir de Microsoft

Vous pouvez télécharger un exemple de fichier Antivirus Microsoft Defender détecter et bloquer si vous êtes correctement connecté au cloud. Visitez [https://aka.ms/ioavtest](https://aka.ms/ioavtest) le site pour télécharger le fichier.

> [!NOTE]
> Le fichier téléchargé n’est pas exactement un programme malveillant. Il s’agit d’un fichier factice conçu pour tester si vous êtes correctement connecté au cloud.

Si vous êtes correctement connecté, un avertissement s’Antivirus Microsoft Defender notification.

Si vous utilisez Microsoft Edge, vous verrez également un message de notification :

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Capture d’écran de la notification de détection de programmes malveillants Azure IoT Edge.":::

Un message similaire se produit si vous utilisez Internet Explorer :

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Notification De Microsoft Defender AV que des programmes malveillants ont été détectés.":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Afficher la détection de programmes malveillants factices dans Sécurité Windows application

1. Dans la barre des tâches, sélectionnez l’icône Bouclier, ouvrez **l’Sécurité Windows** app. Sinon, recherchez **l’exemple Démarrer** pour *la sécurité*.

2. **Sélectionnez Virus & protection contre les** menaces, puis sélectionnez **Historique de la protection**.

3. Sous la section **Menaces en quarantaine** , **sélectionnez Consulter l’historique complet** pour voir les programmes malveillants factices détectés.

   > [!NOTE]
   > Les versions Windows 10 antérieures à la version 1703 ont une interface utilisateur différente. Voir [Antivirus Microsoft Defender dans l’application Sécurité Windows’application.](microsoft-defender-security-center-antivirus.md)

   Le Windows journal des événements affiche également [Windows Defender’ID d’événement client 1116](troubleshoot-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Voir aussi

- [Configurer les paramètres de proxy d’appareil et de connectivité Internet pour Microsoft Defender pour le point de terminaison](configure-proxy-internet.md)
- [Utiliser les paramètres de stratégie de groupe pour configurer et gérer les Antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md)
- [Modifications importantes apportées au point de terminaison Microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 