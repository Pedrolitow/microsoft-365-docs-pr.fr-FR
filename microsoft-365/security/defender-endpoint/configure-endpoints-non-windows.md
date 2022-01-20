---
title: Intégrer des appareils non Windows au service Microsoft Defender for Endpoint
description: Configurez les appareils non Windows afin qu’ils peuvent envoyer des données de capteur au service Microsoft Defender for Endpoint.
keywords: intégrer des appareils non Windows, macos, linux, gestion des appareils, configurer Microsoft Defender pour les appareils Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 231adb590bc737c646566417db1891ac96fdb455
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2022
ms.locfileid: "62156471"
---
# <a name="onboard-non-windows-devices"></a>Intégrer des appareils non Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**Plateformes**
- macOS
- Linux

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

Defender for Endpoint offre une expérience d’opérations de sécurité centralisée pour les plateformes Windows et non Windows de sécurité. Vous pourrez voir les alertes de différents systèmes d’exploitation pris en charge dans Microsoft 365 Defender et mieux protéger le réseau de votre organisation.

Vous devez connaître les versions exactes de Linux et macOS compatibles avec Defender for Endpoint pour que l’intégration fonctionne. Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Microsoft Defender pour point de terminaison sur la demande système Linux](microsoft-defender-endpoint-linux.md#system-requirements)
- [Microsoft Defender pour point de terminaison sur macOS system requirements](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>Intégration d’appareils non Windows intégrés

Pour intégrer des appareils non Windows, vous devez suivre les étapes suivantes :

1. Sélectionnez votre méthode d’intégration préférée :

   - Pour les appareils macOS, vous pouvez choisir d’intégrer via Microsoft Defender pour endpoint ou via une solution tierce. Pour plus d’informations, [voir Microsoft Defender pour endpoint sur Mac.](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac)

   - Pour les autres appareils non Windows choisissez Intégrer des appareils non Windows par le biais **d’une intégration tierce.**
    1. Dans le volet de navigation, sélectionnez **Partenaires et API** Applications \> **partenaires.** Assurez-vous que la solution tierce est répertoriée.
    2. Dans la page **Applications** partenaires, sélectionnez le partenaire qui prend en charge vos appareils Windows non connectés.
    3. Cliquez **sur Afficher** pour ouvrir la page du partenaire. Suivez les instructions fournies sur la page.
    4. Après avoir créé un compte ou vous être abonné à la solution partenaire, vous devez passer à une étape où un administrateur global client de votre organisation est invité à accepter une demande d’autorisation de l’application partenaire. Lisez attentivement la demande d’autorisation pour vous assurer qu’elle est alignée sur le service dont vous avez besoin.

2. Exécutez un test de détection en suivant les instructions de la solution tierce.

## <a name="offboard-non-windows-devices"></a>Appareils non-Windows par carte

Pour les appareils macOS et Linux, vous pouvez choisir de passer par Microsoft Defender for Endpoint. Dans le volet de navigation, sélectionnez **Paramètres** Horsboard Sélectionner le système d’exploitation pour démarrer le processus \>  \> **deboarding.**

Vous pouvez également désinserrez les appareils Windows en désactivant l’intégration tierce. Activer la couverture pour les appareils exécutant des plateformes Windows en intégrant des [solutions tierces.](https://security.microsoft.com/interoperability/partners)

## <a name="related-topics"></a>Voir aussi
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Serveurs intégrés](configure-server-endpoints.md)
- [Configurer les paramètres de proxy et de connectivité Internet](configure-proxy-internet.md)
- [Résolution des problèmes d’intégration de Microsoft Defender pour les points de terminaison](troubleshoot-onboarding.md)
