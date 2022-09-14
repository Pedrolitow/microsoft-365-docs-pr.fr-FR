---
title: Intégrer des appareils non Windows au service Microsoft Defender pour point de terminaison
description: Configurez des appareils non Windows afin qu’ils puissent envoyer des données de capteur au service Microsoft Defender pour point de terminaison.
keywords: intégrer des appareils non Windows, macos, linux, gestion des appareils, configurer des appareils Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 95ed620bf8b5af456174c232d90e05e6fbd547fd
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67680392"
---
# <a name="onboard-non-windows-devices"></a>Intégrer des appareils non Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

Defender pour point de terminaison offre une expérience d’opérations de sécurité centralisée pour les plateformes Windows et non Windows. Vous pourrez voir les alertes provenant de différents systèmes d’exploitation pris en charge dans Microsoft 365 Defender et mieux protéger le réseau de votre organisation.

Vous devez connaître les distributions Linux et les versions macOS exactes compatibles avec Defender pour point de terminaison pour que l’intégration fonctionne. Pour plus d’informations, consultez l’article suivant :

- [Microsoft Defender pour point de terminaison sur la configuration requise pour Linux](microsoft-defender-endpoint-linux.md#system-requirements)
- [Microsoft Defender pour point de terminaison sur la configuration système requise pour macOS](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Intégration d’appareils non Windows

Vous devez effectuer les étapes suivantes pour intégrer des appareils non Windows :

1. Sélectionnez votre méthode d’intégration préférée :

   - Pour les appareils macOS, vous pouvez choisir d’intégrer via Microsoft Defender pour point de terminaison ou par le biais d’une solution tierce. Pour plus d’informations, consultez [Microsoft Defender pour point de terminaison sur Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac).

   - Pour les autres appareils non Windows, choisissez **Intégrer des appareils non Windows via une intégration tierce**.
    1. Dans le volet de navigation, sélectionnez **Partenaires et API** \> **Applications partenaires** . Vérifiez que la solution tierce est répertoriée.
    2. Dans la page **Applications partenaires** , sélectionnez le partenaire qui prend en charge vos appareils non Windows.
    3. Cliquez sur **Affichage** pour ouvrir la page du partenaire. Suivez les instructions fournies sur la page.
    4. Après avoir créé un compte ou vous être abonné à la solution partenaire, vous devez passer à une étape où un client Global Administration de votre organisation est invité à accepter une demande d’autorisation de l’application partenaire. Lisez attentivement la demande d’autorisation pour vous assurer qu’elle est alignée sur le service dont vous avez besoin.

2. Exécutez un test de détection en suivant les instructions de la solution tierce.

## <a name="offboard-non-windows-devices"></a>Désintégrage des appareils non Windows

Pour les appareils macOS et Linux, vous pouvez choisir de vous déconnecter via Microsoft Defender pour point de terminaison. Dans le volet de navigation, sélectionnez **Paramètres** \> **hors-bord** \> **Sélectionner le système d’exploitation pour démarrer le processus de désintégrage**.

Vous pouvez également déconnecter des appareils non Windows en désactivant l’intégration tierce. Activez la couverture pour les appareils exécutant des plateformes non Windows [en intégrant des solutions tierces](https://security.microsoft.com/interoperability/partners).

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Intégrer des serveurs](configure-server-endpoints.md)
- [Configurer les paramètres de proxy et de connectivité Internet](configure-proxy-internet.md)
- [Résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
