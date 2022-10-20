---
title: Configurer Microsoft Defender pour point de terminaison déploiement
description: Découvrez comment configurer le déploiement pour Microsoft Defender pour point de terminaison
keywords: déployer, configurer, validation des licences, configuration du locataire, configuration réseau
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-endpointprotect
- m365solution-scenario
- highpri
- tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 5369f6a359602166b3b2302bd268a7fa4e8b3c4e
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637659"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Configurer Microsoft Defender pour point de terminaison déploiement

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le déploiement de Defender pour point de terminaison est un processus en trois phases :

|[![phase de déploiement : préparez-vous.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Phase 1 : préparation](prepare-deployment.md) | ![phase de déploiement - configuration](images/phase-diagrams/setup.png#lightbox)<br>Phase 2 : configuration | [![phase de déploiement - intégration](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Phase 3 : intégration](onboarding.md)|
|---|---|---|
||*Vous êtes là !*||

Vous êtes actuellement en phase de configuration.

Dans ce scénario de déploiement, vous serez guidé dans les étapes suivantes :

- Validation des licences
- Configuration du locataire
- Configuration réseau

> [!NOTE]
> Pour vous guider tout au long d’un déploiement classique, ce scénario couvre uniquement l’utilisation de Microsoft Endpoint Configuration Manager. Defender pour point de terminaison prend en charge l’utilisation d’autres outils d’intégration, mais ne couvre pas ces scénarios dans le guide de déploiement. Pour plus d’informations, consultez [Intégrer des appareils à Microsoft Defender pour point de terminaison](onboard-configure.md).

## <a name="check-license-state"></a>Vérifier l’état de la licence

Vous pouvez vérifier l’état de la licence et vérifier si elle a été correctement approvisionnée par le biais du Centre d’administration ou du **Portail Azure Microsoft**.

1. Pour afficher vos licences, accédez à **Microsoft Portail Azure** et accédez à la [section licence Microsoft Portail Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Page Licences Azure" lightbox="images/atp-licensing-azure-portal.png":::

1. Vous pouvez également accéder aux **abonnements** de **facturation** \> dans le Centre d’administration.

    À l’écran, vous verrez toutes les licences approvisionnées et leur **état** actuel.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Page licences de facturation" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Validation du fournisseur de services cloud

Pour accéder aux licences approvisionnées dans votre entreprise et vérifier l’état des licences, accédez au centre d’administration.

1. Dans le **portail partenaire**, sélectionnez **Administrer les services > Office 365**.

2. Si vous cliquez sur le lien **du portail partenaire**, vous ouvrez l’option **Administration pour le compte** et vous donne accès au Centre d’administration du client.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Portail d’administration Office 365" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Configuration du locataire

L’intégration à Microsoft Defender pour point de terminaison est facile. Dans le menu de navigation, sélectionnez n’importe quel élément sous la section Points de terminaison ou toute fonctionnalité Microsoft 365 Defender telle que Incidents, Repérage, Centre d’actions ou Analyse des menaces pour lancer le processus d’intégration.

À partir d’un navigateur web, accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

## <a name="data-center-location"></a>Emplacement du centre de données
Microsoft Defender pour point de terminaison stocke et traite les données au [même emplacement que celui utilisé par Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Si Microsoft 365 Defender n’a pas encore été activé, l’intégration à Microsoft Defender pour point de terminaison active également Microsoft 365 Defender et un nouvel emplacement de centre de données est automatiquement sélectionné en fonction de l’emplacement de sécurité Microsoft 365 actif Services. L’emplacement du centre de données sélectionné s’affiche à l’écran.

## <a name="network-configuration"></a>Configuration réseau

Si l’organisation n’exige pas que les points de terminaison utilisent un proxy pour accéder à Internet, ignorez cette section.

Le capteur Microsoft Defender pour point de terminaison requiert Microsoft Windows HTTP (WinHTTP) pour signaler les données du capteur et communiquer avec le service Microsoft Defender pour point de terminaison. Le capteur incorporé Microsoft Defender pour point de terminaison s’exécute dans le contexte système à l’aide du compte LocalSystem. Le capteur utilise les services Microsoft Windows HTTP Services (WinHTTP) pour activer la communication avec le service Cloud Microsoft Defender pour point de terminaison. Le paramètre de configuration WinHTTP est indépendant des paramètres de proxy de navigation Internet Windows Internet (WinINet) et peut uniquement découvrir un serveur proxy à l’aide des méthodes de découverte suivantes :

- **Méthodes de découverte automatique** :
  - Proxy transparent
  - Protocole WPAD (Web Proxy Auto-Discovery Protocol)

  Si un proxy transparent ou WPAD a été implémenté dans la topologie de réseau, il n’est pas nécessaire de définir des paramètres de configuration spéciaux. Pour plus d’informations sur Microsoft Defender pour point de terminaison exclusions d’URL dans le proxy, consultez la section [URL du service](production-deployment.md#proxy-service-urls) proxy dans ce document pour connaître la liste verte des URL ou sur [configurer les paramètres de connectivité Internet et proxy d’appareil](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **Configuration manuelle du proxy statique** :
  - Configuration basée sur le registre
  - WinHTTP configuré à l’aide de la commande netsh

    Convient uniquement aux bureaux d’une topologie stable (par exemple, un bureau dans un réseau d’entreprise derrière le même proxy).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Configurer le serveur proxy manuellement en utilisant un proxy statique basé sur le registre

Configurez un proxy statique basé sur le Registre pour autoriser uniquement Microsoft Defender pour point de terminaison capteur à signaler les données de diagnostic et à communiquer avec Microsoft Defender pour point de terminaison services si un ordinateur n’est pas autorisé à se connecter à Internet. Le proxy statique est configurable via une stratégie de groupe. La stratégie de groupe se trouve sous :

- Modèles d’administration \> - Collecte de données des composants \> Windows et builds \> en préversion - Configurer l’utilisation du proxy authentifié pour le service d’expérience utilisateur connectée et de télémétrie
- Définissez-le sur **Activé** et sélectionnez **Désactiver l’utilisation du proxy authentifié**

1. Ouvrez la console de gestion des stratégies de groupe.
2. Créez une stratégie ou modifiez une stratégie existante en fonction des pratiques organisationnelles.
3. Modifiez le stratégie de groupe et accédez à La **collecte de données des composants \> \> Windows modèles d’administration et aux builds \> d’aperçu configurez l’utilisation du proxy authentifié pour le service d’expérience utilisateur connectée et de télémétrie**.

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Options liées à la configuration de la stratégie d’utilisation" lightbox="images/atp-gpo-proxy1.png":::

4. Sélectionnez **Activé**.
5. Sélectionnez **Désactiver l’utilisation du proxy authentifié**.
6. Accédez à **Modèles d’administration \> Collecte de données des composants \> Windows et versions préliminaires Configurez les \> expériences utilisateur connectées et la télémétrie**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Options liées à la configuration de l’expérience utilisateur connectée et de la télémétrie" lightbox="images/atp-gpo-proxy2.png":::

7. Sélectionnez **Activé**.
8. Entrez le **nom du serveur proxy**.

La stratégie définit deux valeurs de registre `TelemetryProxyServer` comme REG_SZ et `DisableEnterpriseAuthProxy` comme REG_DWORD sous la clé de registre `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

La valeur `TelemetryProxyServer` du Registre prend le format de chaîne suivant :

```text
<server name or ip>:<port>
```

Par exemple, 10.0.0.6:8080

Cette valeur de registre `DisableEnterpriseAuthProxy` doit être égale à 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Configurer le serveur proxy manuellement à l’aide de la commande netsh

Utiliser netsh pour configurer un proxy statique à l’échelle du système.

> [!NOTE]
>
> - Cela affectera toutes les applications, y compris les services Windows qui utilisent WinHTTP avec un proxy par défaut.
> - Les ordinateurs portables qui changent de topologie (par exemple, d’un bureau à l’autre) ne fonctionnent pas correctement avec netsh. Utiliser la configuration statique du proxy basée sur le registre.

1. Ouvrez une invite de commandes avec élévation de privilèges :
    1. Accéder à **Démarrer** et taper **cmd**.
    1. Cliquez avec le bouton droit sur **Invite de commandes** et sélectionnez **Exécuter en tant qu'administrateur**.

2. Entrez la commande suivante et appuyez sur **Entrée** :

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Par exemple : netsh winhttp initialiser proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Configuration du proxy pour les appareils de bas niveau

Down-Level appareils incluent des stations de travail Windows 7 SP1 et Windows 8.1 ainsi que Windows Server 2008 R2 et d’autres systèmes d’exploitation serveur qui ont été intégrés précédemment à l’aide de Microsoft Monitoring Agent. Le proxy de ces systèmes d’exploitation sera configuré dans le cadre de Microsoft Management Agent pour gérer la communication entre le point de terminaison et Azure. Reportez-vous au Guide de déploiement rapide de Microsoft Management Agent pour plus d’informations sur la configuration d’un proxy sur ces appareils.

### <a name="proxy-service-urls"></a>URL du service proxy

Les URL qui incluent la version 20 ne sont nécessaires que si vous avez des appareils Windows 10, version 1803 ou Windows 11. Par exemple, `us-v20.events.data.microsoft.com` n’est nécessaire que si l’appareil est sur Windows 10, version 1803 ou Windows 11.

Si un proxy ou un pare-feu bloque le trafic anonyme, comme Microsoft Defender pour point de terminaison capteur se connecte à partir du contexte système, assurez-vous que le trafic anonyme est autorisé dans les URL répertoriées.

La feuille de calcul téléchargeable suivante répertorie les services et leurs URL associées auxquelles votre réseau doit pouvoir se connecter. Vérifiez qu’il n’existe aucune règle de pare-feu ou de filtrage réseau qui refuserait l’accès à ces URL, ou vous devrez peut-être créer une règle *d’autorisation* spécifique pour ces URL.

<br>

****


|Feuille de calcul de la liste des domaines| Description|
|---|---|
|liste d’URL Microsoft Defender pour point de terminaison pour les clients commerciaux| Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation des clients commerciaux. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender pour point de terminaison liste d’URL pour Gov/GCC/DoD | Feuille de calcul d’enregistrements DNS spécifiques pour les emplacements de service, les emplacements géographiques et le système d’exploitation pour les clients Gov/GCC/DoD. <p> [Téléchargez la feuille de calcul ici.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Étape suivante

[![**Phase 3 : Intégration**.](images/onboard.png#lightbox)] <br> [Phase 3 : Intégrer](onboarding.md) : intégrer des appareils au service afin que le service Microsoft Defender pour point de terminaison puisse obtenir des données de capteur à partir de ces derniers.
