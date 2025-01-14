---
title: Activer l’intégration de Corelight dans Microsoft Defender pour point de terminaison
description: Activer l’intégration corelight pour obtenir une visibilité axée sur les appareils IoT/OT dans les zones du réseau où MDE n’est pas déployé
keywords: activer le connecteur siem, siem, connecteur, informations de sécurité et événements
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: fac3ff549e4ac18fa7af4c65ffa724ad5a7c4164
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68635749"
---
# <a name="enable-corelight-data-integration"></a>Permettre l'intégration des données Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft s’est associé à [Corelight](https://corelight.com/integrations/iot-security), fournisseur de la première plateforme de détection et de réponse réseau ouverte (NDR) du secteur, pour vous aider à découvrir les appareils IoT/OT au sein de votre organisation. À l’aide de données envoyées à partir d’appliances réseau Corelight, Microsoft 365 Defender bénéficie d’une visibilité accrue sur les activités réseau des appareils non gérés, y compris la communication avec d’autres appareils non gérés ou des réseaux externes.

Une fois cette source de données activée, tous les événements des appliances réseau Corelight sont envoyés à Microsoft 365 Defender. Vous pouvez afficher ces activités dans la chronologie des appareils non managés, disponible dans l’inventaire des appareils Microsoft Defender pour point de terminaison. Pour plus d’informations, consultez [Découverte d’appareils](device-discovery.md).

## <a name="prerequisites"></a>Configuration requise

1. Pour configurer l’intégration des données Corelight, l’utilisateur doit avoir les rôles suivants :
   - Administrateur général du locataire dans Azure Active Directory
   - Administrateur de sécurité pour l’abonnement Azure qui sera utilisé pour la Microsoft Defender pour l’intégration IoT
2. Un plan Defender pour IoT intégré. Pour plus d’informations, consultez [Intégration Microsoft Defender pour IoT avec Microsoft Defender pour point de terminaison](enable-microsoft-defender-for-iot-integration.md).

## <a name="enabling-the-corelight-integration"></a>Activation de l’intégration corelight

Pour activer l’intégration de Corelight, vous devez effectuer les étapes suivantes :

[Étape 1 : Activer Corelight en tant que source de données](#step-1-turn-on-corelight-as-a-data-source)<br>
[Étape 2 : Autoriser Corelight à envoyer des événements à Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Étape 1 : Activer Corelight en tant que source de données

1. Dans le volet de navigation du [https://security.microsoft.com](https://security.microsoft.com/) portail, sélectionnez **Paramètres Sources** \> de **données** **de découverte** \> d’appareil.

   :::image type="content" source="../../media/defender-endpoint/enable-corelight.png" alt-text="Page Sources de données dans le portail Microsoft 365 Defender" lightbox="../../media/defender-endpoint/enable-corelight.png":::

2. Sélectionnez **Envoyer des données Corelight à M365D** , puis **Enregistrez**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Étape 2 : Autoriser Corelight à envoyer des événements à Microsoft 365 Defender

> [!NOTE]
> Vous devez être un administrateur général pour accorder à Corelight l’autorisation d’accéder aux ressources de votre organisation.

1. En tant qu’administrateur général de locataire, accédez à ce [lien](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) pour accorder l’autorisation.
2. Accédez au [https://security.microsoft.com](https://security.microsoft.com/) portail, sélectionnez **Paramètres** \> **Microsoft 365 Defender** et prenez note de **l’ID de locataire**. Vous aurez besoin de ces informations lors de la configuration de votre appliance Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Étape 3 : Configurer votre appliance Corelight pour envoyer des données à Microsoft 365 Defender

> [!NOTE]
> L’intégration est disponible dans corelight Sensor software v25 et versions ultérieures.
> 
> Vous aurez besoin d’une connectivité Internet pour que votre capteur atteigne les services cloud Defender et Corelight pour que la solution fonctionne.

#### <a name="enable-the-integration-in-the-corelight-web-interface"></a>Activer l’intégration dans l’interface web Corelight

1. Dans l’interface web Corelight, accédez à **Sensor** \> **Export**.

   :::image type="content" source="images/exporttodefender.png" alt-text="Exportation kafka" lightbox="images/exporttodefender.png":::

2. Activer **l’exportation pour Microsoft Defender**.
3. Entrez votre ID de locataire Microsoft 356 Defender.
4. Si vous le souhaitez, vous pouvez :
    - définissez les **journaux Zeek sur Exclure**. L’ensemble minimal de journaux que vous devez inclure est : dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp et notice.
    - choisissez de créer un **filtre de journal Microsoft Defender**.
5. Sélectionnez **Apply Changes** (Appliquer les modifications).

#### <a name="enable-the-integration-in-the-corelight-client"></a>Activer l’intégration dans corelight-client

1. Activez **Exporter pour Microsoft Defender** à l’aide de la commande suivante dans corelight-client :

    ``` command
    corelight-client configuration update \
    --bro.export.defender.enable True
    ```

2. Définir votre ID de locataire

3. Si vous le souhaitez, vous pouvez utiliser la commande suivante pour exclure certains journaux ou créer un filtre de journal Microsoft Defender. L’ensemble minimal de journaux que vous devez inclure est : dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp et notice.

   ``` command
     corelight-client configuration update \
    --bro.export.defender.exclude=<logs_to_exclude> \
    --bro.export.defender.filter=<logs_to_filter>
   ```

## <a name="see-also"></a>Voir aussi

- [Forum aux questions sur la découverte d’appareils](device-discovery-faq.md)
