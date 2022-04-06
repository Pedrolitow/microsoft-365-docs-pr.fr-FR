---
title: Activer l’intégration de Corelight dans Microsoft Defender pour point de terminaison
description: Activer l’intégration corelight pour obtenir une visibilité axée sur les appareils IoT/OT dans les zones du réseau où MDE n’est pas déployé
keywords: activer le connecteur siem, siem, connecteur, informations de sécurité et événements
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
ms.openlocfilehash: bf3095b9178b4ff2e71d4ee5f652d9316f233746
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664587"
---
# <a name="enable-corelight-data-integration"></a>Permettre l'intégration des données Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft s’est associé à [Corelight](https://corelight.com/integrations/iot-security), fournisseur de la première plateforme de détection et de réponse réseau ouverte (NDR) du secteur, pour vous aider à découvrir les appareils IoT/OT au sein de votre organisation. À l’aide de données envoyées à partir d’appliances réseau Corelight, Microsoft 365 Defender bénéficie d’une visibilité accrue sur les activités réseau des appareils non gérés, y compris la communication avec d’autres appareils non gérés ou des réseaux externes.

Une fois cette source de données activée, tous les événements des appliances réseau Corelight sont envoyés à Microsoft 365 Defender. Vous pouvez afficher ces activités dans la chronologie des appareils non managés, disponible dans l’inventaire des appareils Microsoft Defender pour point de terminaison. Pour plus d’informations, consultez [Découverte d’appareils](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Activation de l’intégration corelight

Pour activer l’intégration de Corelight, vous devez effectuer les étapes suivantes :

[Étape 1 : Activer Corelight en tant que source de données](#step-1-turn-on-corelight-as-a-data-source)<br>
[Étape 2 : Autoriser Corelight à envoyer des événements à Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Étape 1 : Activer Corelight en tant que source de données

1. Dans le volet de navigation du [https://security.microsoft.com](https://security.microsoft.com/) portail, sélectionnez **Paramètres** \> **Sources de données** de **découverte** \> d’appareil.

   :::image type="content" source="images/enable-corelight.png" alt-text="Page Sources de données dans le portail Microsoft 365 Defender" lightbox="images/enable-corelight.png":::

2. Sélectionnez **Envoyer des données Corelight à M365D** , puis **Enregistrez**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Étape 2 : Autoriser Corelight à envoyer des événements à Microsoft 365 Defender

> [!NOTE]
> Vous devez être un administrateur général pour accorder à Corelight l’autorisation d’accéder aux ressources de votre organisation.

1. En tant qu’administrateur général de locataire, accédez à ce [lien](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) pour accorder l’autorisation.
2. Accédez au [https://security.microsoft.com](https://security.microsoft.com/) portail, sélectionnez **Paramètres** \> **Microsoft 365 Defender** et prenez note de **l’ID de locataire**. Vous aurez besoin de ces informations lors de la configuration de votre appliance Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender

> [!NOTE]
>  L’intégration sera publique dans le logiciel Corelight Sensor v24 et versions ultérieures. 

Pour afficher un aperçu dans v23 ou v22.1, vous devez `corelight-client configuration update --enable.adfiot 1` exécuter pour activer la section de configuration dans l’interface graphique utilisateur.

En outre, la validation de l’interface utilisateur utilisateur nécessite qu’un répartiteur soit configuré dans la section de configuration sur toutes les versions v23.  Le répartiteur que vous fournissez est obligatoire, mais ne sera pas réellement utilisé. Entrez `127.0.0.1:1234` dans le champ _broker kafka_ pour garantir la réussite de la validation avant de suivre les étapes ci-dessous pour permettre l’envoi de données à Microsoft 365 Defender.

> [!NOTE]
> Vous aurez besoin d’une connectivité Internet pour que votre capteur atteigne les services cloud Defender et Corelight pour que la solution fonctionne.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Activation dans l’interface graphique utilisateur du capteur Corelight

1. Dans la section configuration de l’interface utilisateur utilisateur du capteur Corelight, sélectionnez **Exportation** de **capteur**\>.
2. Dans la liste, accédez à **EXPORT TO KAFKA** et sélectionnez le commutateur pour l’activer.

   :::image type="content" source="images/exporttokafka.png" alt-text="Exportation kafka" lightbox="images/exporttokafka.png":::

3. Ensuite, activez **EXPORT TO AZURE DEFENDER FOR IOT** et entrez votre ID de locataire, indiqué à l’étape 1, dans le champ ID de locataire.

   :::image type="content" source="images/exporttodiot.png" alt-text="Exportation iot" lightbox="images/exporttodiot.png":::

4. Sélectionnez **Apply Changes** (Appliquer les modifications).

   :::image type="content" source="images/corelightapply.png" alt-text="Icône Appliquer les modifications" lightbox="images/corelightapply.png":::

> [!NOTE]
> Les options de configuration dans Kafka (à l’exception de l’exclusion de journal et des filtres) ne doivent pas être modifiées. Toutes les modifications apportées seront ignorées.

#### <a name="enabling-in-the-corelight-client"></a>Activation dans corelight-client

Vous pouvez activer **EXPORT TO KAFKA** et **EXPORT TO AZURE DEFENDER FOR IOT** à l’aide de la commande suivante dans corelight-client :

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Si vous utilisez déjà l’exportation Kafka, contactez le support Corelight pour une autre configuration.

Pour configurer uniquement l’envoi du jeu minimal de journaux :

1. Dans l’interface graphique utilisateur du capteur Corelight, accédez à la section Kafka
2. Accéder aux **journaux Zeek à exclure**
3. Sélectionner **tout**
4. Sélectionnez ensuite **x** en regard des journaux suivants pour vous assurer qu’ils continuent à circuler vers Microsoft :  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Sélectionnez **Appliquer les modifications**

La liste des journaux d’activité qui circulent vers Microsoft peut s’étendre au fil du temps.

## <a name="see-also"></a>Voir aussi

- [Forum aux questions sur la découverte d’appareils](device-discovery-faq.md)
