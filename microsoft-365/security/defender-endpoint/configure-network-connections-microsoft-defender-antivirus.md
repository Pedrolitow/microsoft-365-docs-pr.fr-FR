---
title: Configurer et valider les connexions réseau à un antivirus Microsoft Defender
description: Configurez et testez votre connexion au service Antivirus Microsoft Defender protection contre le cloud.
keywords: antivirus, Antivirus Microsoft Defender, antimalware, sécurité, défenseur, cloud, agressivité, niveau de protection
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 05/17/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: ef5a9ffdf45a2f8e7f262ae7f969cd19e848b7a5
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572524"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Configurer et valider les connexions réseau à un antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Pour vous Antivirus Microsoft Defender protection fournie par le cloud fonctionne correctement, vous devez configurer votre réseau pour permettre des connexions entre vos paramètres et certains serveurs Microsoft. Cet article répertorie les connexions qui doivent être autorisées, par exemple en utilisant les règles de pare-feu, et fournit des instructions pour valider votre connexion. Configurer correctement votre protection vous permet de bénéficier de la meilleure valeur de vos services de protection fournis par le cloud.

Voir le billet de blog [Modifications importantes au point de terminaison microsoft Active Protection Services](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) pour plus de détails sur la connectivité réseau.

> [!TIP]
> Vous pouvez également visiter le site Web de démonstration Microsoft Defender for Endpoint [à demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour confirmer que les fonctionnalités suivantes fonctionnent :
>
> - Protection fournie par le cloud
> - Apprentissage rapide (y compris bloc à première vue)
> - Blocage d’applications potentiellement indésirable

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Autoriser les connexions au service Antivirus Microsoft Defender cloud

Le service Antivirus Microsoft Defender cloud offre une protection rapide et solide pour vos points de terminaison. L’activation du service de protection livré dans le cloud est facultative, mais elle est fortement recommandée car elle offre une protection importante contre les logiciels malveillants sur vos points de terminaison et sur l’ensemble de votre réseau.

> [!NOTE]
> Le service Antivirus Microsoft Defender cloud est un mécanisme permettant d’offrir une protection mise à jour à votre réseau et à vos points de terminaison. Bien qu’il soit appelé un service cloud, il ne s’agit pas simplement de protection pour les fichiers stockés dans le cloud, mais plutôt d’utiliser des ressources distribuées et l’apprentissage automatique pour fournir une protection à vos points de terminaison à un rythme beaucoup plus rapide que les mises à jour traditionnelles de renseignement de sécurité.

Consultez [la protection fournie par le cloud pour](enable-cloud-protection-microsoft-defender-antivirus.md) plus de détails sur l’activation du service avec Intune, Microsoft Endpoint Configuration Manager, Group Policy, PowerShell cmdlets, ou sur les clients individuels dans l’application Sécurité Windows. 

Une fois que vous avez activé le service, vous devrez peut-être configurer votre réseau ou pare-feu pour autoriser les connexions entre lui et vos paramètres.

Étant donné que votre protection est un service cloud, les ordinateurs doivent avoir accès à Internet et atteindre le Microsoft Defender pour obtenir des services Office 365'apprentissage automatique. N’excluez pas l’URL `*.blob.core.windows.net` de toute forme d’inspection réseau. 

Le tableau ci-dessous répertorie les services et leurs URL associées. Assurez-vous qu’il n’y a pas de règles de filtrage pare-feu ou réseau niant l’accès à ces URL, ou vous devrez peut-être créer une règle d’autoriser spécifiquement pour eux (à l’exclusion de `*.blob.core.windows.net` l’URL). Ci-dessous mentionner URL utilisent le port 443 pour la communication.


| **Service**| **Description** |**URL** |
| :--: | :-- | :-- |
| Antivirus Microsoft Defender service de protection fourni par le cloud, également appelé Microsoft Active Protection Service (MAPS)|Utilisé par Antivirus Microsoft Defender pour fournir une protection fournie par le cloud|`*.wdcp.microsoft.com` <br/> `*.wdcpalt.microsoft.com` <br/> `*.wd.microsoft.com`|
| Service de mise à jour Microsoft (MU) <br/> Windows Service de mise à jour (WU)|  Renseignements de sécurité et mises à jour de produits   |`*.update.microsoft.com` <br/> `*.delivery.mp.microsoft.com`<br/> `*.windowsupdate.com` <br/><br/> Pour plus de [détails, consultez les paramètres de connexion pour Windows mise à jour](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Mises à jour de renseignement de sécurité Emplacement de téléchargement alternatif (ADL)|   Autre emplacement pour les Antivirus Microsoft Defender de renseignement de sécurité si les renseignements de sécurité installés sont obsolètes (7 jours ou plus de retard)|    `*.download.microsoft.com`  </br> `*.download.windowsupdate.com`</br>  `go.microsoft.com`</br> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
| Stockage de soumission de logiciels malveillants|Télécharger emplacement des fichiers soumis à Microsoft via le formulaire de soumission ou la soumission automatique de l’échantillon    | `ussus1eastprod.blob.core.windows.net` <br/>    `ussus2eastprod.blob.core.windows.net` <br/>    `ussus3eastprod.blob.core.windows.net` <br/>    `ussus4eastprod.blob.core.windows.net` <br/>    `wsus1eastprod.blob.core.windows.net` <br/>    `wsus2eastprod.blob.core.windows.net` <br/>    `ussus1westprod.blob.core.windows.net` <br/>    `ussus2westprod.blob.core.windows.net` <br/>    `ussus3westprod.blob.core.windows.net` <br/>    `ussus4westprod.blob.core.windows.net` <br/>    `wsus1westprod.blob.core.windows.net` <br/>    `wsus2westprod.blob.core.windows.net` <br/>    `usseu1northprod.blob.core.windows.net` <br/>    `wseu1northprod.blob.core.windows.net` <br/>    `usseu1westprod.blob.core.windows.net` <br/>    `wseu1westprod.blob.core.windows.net` <br/>    `ussuk1southprod.blob.core.windows.net` <br/>    `wsuk1southprod.blob.core.windows.net` <br/>    `ussuk1westprod.blob.core.windows.net` <br/>    `wsuk1westprod.blob.core.windows.net` |
| Liste de révocation des certificats (CRL)|Utilisé par Windows lors de la création de la connexion SSL à MAPS pour la mise à jour du CRL   | `http://www.microsoft.com/pkiops/crl/` <br/> `http://www.microsoft.com/pkiops/certs` <br/>   `http://crl.microsoft.com/pki/crl/products` <br/> `http://www.microsoft.com/pki/certs` |
| Magasin de symboles|Utilisé par Antivirus Microsoft Defender restaurer certains fichiers critiques pendant les flux d’assainissement  | `https://msdl.microsoft.com/download/symbols` |
| Client de télémétrie universelle| Utilisé par Windows pour envoyer des données diagnostiques aux clients; Antivirus Microsoft Defender télémétrie à des fins de surveillance de la qualité des produits   | La mise à jour utilise SSL (TCP Port 443) pour télécharger des manifestes et télécharger des données diagnostiques vers Microsoft qui utilise les paramètres DNS suivants :   `vortex-win.data.microsoft.com` <br/>   `settings-win.data.microsoft.com`|

## <a name="validate-connections-between-your-network-and-the-cloud"></a>Valider les connexions entre votre réseau et le cloud

Après avoir autorisé les URL énumérées ci-dessus, vous pouvez tester si vous êtes connecté au service cloud Antivirus Microsoft Defender et si vous signalez et recevez correctement des informations pour vous assurer d’être entièrement protégé.

**Utilisez l’outil cmdline pour valider la protection fournie par le cloud :**

Utilisez l’argument suivant avec l’utilitaire Antivirus Microsoft Defender ligne de commande () pour vérifier `mpcmdrun.exe` que votre réseau peut communiquer avec le service Antivirus Microsoft Defender cloud :

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Vous devez ouvrir une version de l’invite de commande au niveau de l’administrateur. Cliquez à droite sur l’élément dans le menu Démarrer, cliquez sur **Exécuter en tant qu’administrateur** et **cliquez oui** à l’invite autorisations. Cette commande ne fonctionnera que sur Windows 10, version 1703 ou plus.

Pour plus d’informations, [consultez Manage Antivirus Microsoft Defender l’outil mpcmdrun.exe de commande.](command-line-arguments-microsoft-defender-antivirus.md)

**Essayez de télécharger un faux fichier malware de Microsoft:**

Vous pouvez télécharger un fichier d’Antivirus Microsoft Defender qui détectera et bloquera si vous êtes correctement connecté au cloud.

Téléchargez le fichier en visitant [https://aka.ms/ioavtest](https://aka.ms/ioavtest) .

> [!NOTE]
> Ce fichier n’est pas un morceau réel de malware. Il s’agit d’un faux fichier qui est conçu pour tester si vous êtes correctement connecté au cloud.

Si vous êtes correctement connecté, vous verrez un avertissement et une notification Antivirus Microsoft Defender’avertissement.

Si vous utilisez Microsoft Edge, vous verrez également un message de notification :

![Microsoft Edge l’utilisateur que des logiciels malveillants ont été trouvés](images/defender/wdav-bafs-edge.png)

Un message similaire se produit si vous utilisez Internet Explorer :

![Antivirus Microsoft Defender notification informant l’utilisateur que des logiciels malveillants ont été trouvés](images/defender/wdav-bafs-ie.png)

Vous verrez également une détection sous menaces mises en **quarantaine dans la** section Historique de **l’analyse** dans l’application Sécurité Windows suivante :

1. Ouvrez l Sécurité Windows application en cliquant sur l’icône bouclier dans la barre des tâches ou en recherchant le menu de démarrage pour **la sécurité**.

2. Sélectionnez **Virus & protection contre les menaces,** puis sélectionnez Historique de **protection**.

3. Dans la section **Menaces mises en** quarantaine, sélectionnez Voir **l’historique complet** pour voir le faux malware détecté.

   > [!NOTE]
   > Les versions Windows 10 avant la version 1703 ont une interface utilisateur différente. Voir [Antivirus Microsoft Defender dans l’application Sécurité Windows.](microsoft-defender-security-center-antivirus.md)

   Le journal Windows’événement affichera également [l’Windows Defender client ID 1116](troubleshoot-microsoft-defender-antivirus.md).

## <a name="related-articles"></a>Articles connexes

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)

- [Protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md)

- [Arguments de ligne de commande](command-line-arguments-microsoft-defender-antivirus.md)

- [Modifications importantes apportées au point de terminaison des services de protection active Microsoft](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006)
