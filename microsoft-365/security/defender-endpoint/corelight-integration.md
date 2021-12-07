---
title: Activer l’intégration de Corelight dans Microsoft Defender pour endpoint
description: Activer l’intégration de Corelight pour obtenir une visibilité axée sur les appareils IoT/OT dans les zones du réseau où MDE n’est pas déployé
keywords: activer un connecteur siem, un siem, un connecteur, des informations de sécurité et des événements
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 62bddf15a041ef47df13bbbd036d10727c15d3d6
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2021
ms.locfileid: "61320838"
---
# <a name="enable-corelight-data-integration"></a>Activer l’intégration des données Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft s’est associé à [Corelight,](https://corelight.com/integrations/iot-security)fournisseur de la plateforme de détection et de réponse réseau ouverte (NDR) du secteur, pour vous aider à découvrir les appareils IoT/OT au sein de votre organisation. À l’aide de données envoyées à partir d’appliances réseau Corelight, Microsoft 365 Defender gagne en visibilité sur les activités réseau des appareils non utilisés, y compris la communication avec d’autres périphériques non utilisés ou des réseaux externes.

Avec cette source de données activée, tous les événements des appliances réseau Corelight sont envoyés Microsoft 365 Defender. Vous pouvez afficher ces activités dans la chronologie des appareils non utilisés, disponible dans l’inventaire des appareils Microsoft Defender for Endpoint. Pour plus d’informations, voir [Détection d’appareils.](device-discovery.md)

## <a name="enabling-the-corelight-integration"></a>Activation de l’intégration de Corelight

Pour activer l’intégration de Corelight, vous devez suivre les étapes suivantes :

[Étape 1 : Activer Corelight en tant que source de données](#step-1-turn-on-corelight-as-a-data-source)<br>
[Étape 2 : autoriser Corelight à envoyer des événements à Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Étape 1 : Activer Corelight en tant que source de données

1. Dans le volet de navigation du portail, sélectionnez Paramètres sources de données [https://security.microsoft.com](https://security.microsoft.com/)  \>  \> **de découverte d’appareils.**

    ![Image des sources de données](images/enable-corelight.png)

2. Sélectionnez **Envoyer les données Corelight à M365D** et sélectionnez **Enregistrer.**

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Étape 2 : autoriser Corelight à envoyer des événements à Microsoft 365 Defender

> [!NOTE]
> Vous devez être un administrateur global pour accorder à Corelight l’autorisation d’accéder aux ressources de votre organisation.

1. En tant qu’administrateur général du client, allez sur ce [lien](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) pour accorder l’autorisation.
2. Go to [https://security.microsoft.com](https://security.microsoft.com/) portal, select **Paramètres** \> **Microsoft 365 Defender**, and take note of the **Tenant ID**. Vous aurez besoin de ces informations lors de la configuration de votre appliance Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender

**S’applique** à : Corelight Sensor software v24.2 and later

> [!NOTE]
> Pour activer une version précédente qui prend en charge l’envoi de données, vous devez d’abord exécuter `corelight-client configuration update --enable.adfiot 1` :

> [!NOTE]
> Vous aurez besoin d’une connectivité Internet pour que votre capteur atteigne les services cloud Defender et Corelight pour que la solution fonctionne.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Activation dans l’interface graphique graphique du capteur Corelight

1. Dans la section configuration de  l’interface graphique du capteur Corelight, sélectionnez \> **Exporter le capteur.**
2. Dans la liste, sélectionnez **EXPORT TO CASKA** et sélectionnez le commutateur pour l’activer.

   ![Image de l’exportation de contrôle d’exportation](images/exporttokafka.png)

3. Ensuite, turn on **EXPORT TO AZURE DEFENDER FOR IOT** and enter your tenant ID, noted in Step 1, in the TENANT ID field.

   ![Image de l’exportation d’iot](images/exporttodiot.png)

4. Sélectionnez **Apply Changes** (Appliquer les modifications).

   ![Appliquer une image ](images/corelightapply.png)

> [!NOTE]
> Les options de configuration de Lasska (à l’exclusion des journaux et des filtres) ne doivent pas être modifiées. Toutes les modifications apportées seront ignorées.

#### <a name="enabling-in-the-corelight-client"></a>Activation dans corelight-client

Vous pouvez activer **l’EXPORTATION VERS CONTRÔLE D’ACCÈS ET** L’EXPORTATION VERS AZURE DEFENDER POUR **IOT** à l’aide de la commande suivante dans corelight-client :

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Si vous utilisez déjà l’exportation de Contrôleka, contactez le support Corelight pour une autre configuration.

Pour configurer uniquement l’envoi de l’ensemble minimal de journaux :

1. Dans l’interface graphique graphique du capteur Corelight, allez à la section
2. Go to **Zeek logs to exclude**
3. Sélectionner **tout**
4. Sélectionnez **ensuite x** à côté des journaux suivants pour vous assurer qu’ils continuent à circuler vers Microsoft :  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Sélectionnez **Appliquer les modifications**

La liste des journaux qui circulent vers Microsoft peut s’étendre au fil du temps.

## <a name="see-also"></a>Voir aussi

- [Forum aux questions sur la découverte d’appareils](device-discovery-faq.md)