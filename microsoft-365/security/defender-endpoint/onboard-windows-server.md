---
title: Intégration de Defender pour point de terminaison à Windows Server
description: Intégrer Windows Server à Microsoft Defender pour point de terminaison.
keywords: intégration, Microsoft Defender pour point de terminaison intégration, sccm, stratégie de groupe, mdm, script local, test de détection
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
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: 6bc6bfa6848d613b23fab0bf00d137d3c62b80e3
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585617"
---
# <a name="defender-for-endpoint-onboarding-windows-server"></a>Intégration de Defender pour point de terminaison à Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 et versions ultérieures
- Windows Server 2019 Core Edition
- Windows Server 2022
- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https:%2F%2Faka.ms%2FMDEp2OpenTrial)

Vous devez parcourir la section d’intégration du portail Defender pour point de terminaison pour intégrer l’un des appareils pris en charge. Selon l’appareil, vous serez guidé avec les étapes appropriées et les options d’outils de gestion et de déploiement fournies pour l’appareil.

Defender pour point de terminaison étend la prise en charge pour inclure également le système d’exploitation Windows Server. Cette prise en charge fournit des fonctionnalités avancées de détection des attaques et d’investigation en toute transparence via la console Microsoft 365 Defender. La prise en charge de Windows Server fournit des informations plus approfondies sur les activités du serveur, la couverture de la détection des attaques de noyau et de mémoire, et permet des actions de réponse.

Cette rubrique explique comment intégrer des serveurs Windows spécifiques à Microsoft Defender pour point de terminaison.

Pour obtenir des conseils sur le téléchargement et l’utilisation de Sécurité Windows bases de référence pour les serveurs Windows, consultez [Sécurité Windows Lignes de base.](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-baselines)

## <a name="license-requirement"></a>Condition requise pour la licence

Pour pouvoir acheter Microsoft Defender pour point de terminaison référence SKU server, vous devez avoir déjà acheté un minimum combiné de l’une des licences d’abonnement suivantes : Windows E5/A5, Microsoft 365 E5/A5 ou Microsoft 365 E5 Sécurité. Pour plus d’informations sur les licences, consultez les [termes du produit](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

## <a name="windows-server-onboarding-overview"></a>Vue d’ensemble de l’intégration de Windows Server

Vous devez suivre les étapes générales suivantes pour intégrer correctement les serveurs 2008 R2, 2012 R2, 2016, 2019, 2022.

:::image type="content" source="images/server-onboarding.png" alt-text="Intégration de serveur" lightbox="images/server-onboarding.png":::

### <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 et Windows Server 2016
- Téléchargez les packages d’installation et d’intégration.
- Appliquez le package d’installation.
- Suivez les étapes d’intégration de l’outil correspondant.

### <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019"></a>Windows Server Semi-Annual Enterprise Channel et Windows Server 2019
- Téléchargez le package d’intégration.
- Suivez les étapes d’intégration de l’outil correspondant.

## <a name="offboard-windows-servers"></a>Désintégrage des serveurs Windows

Vous pouvez déconnecter Windows Server 2012 édition R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 et Windows Server 2019 Core avec la même méthode disponible pour Windows 10 appareils clients.

- [Désins border des appareils à l’aide de Configuration Manager](/microsoft-365/security/defender-endpoint/configure-endpoints-sccm#offboard-devices-using-configuration-manager)
- [Désinstégez et surveillez les appareils à l’aide des outils de Gestion des appareils mobile](/microsoft-365/security/defender-endpoint/configure-endpoints-mdm#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [Désintégrage des appareils à l’aide de stratégie de groupe](/microsoft-365/security/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [Désintégrage des appareils à l’aide d’un script local](/microsoft-365/security/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)

Après la désintégration, vous pouvez procéder à la désinstallation du package de solution unifié sur Windows Server 2012 R2 et Windows Server 2016.

Pour les autres versions de serveur Windows, vous avez deux options pour déconnecter les serveurs Windows du service :
- Désinstaller l’agent MMA
- Supprimer la configuration de l’espace de travail Defender pour point de terminaison

> [!NOTE]
> Ces instructions de désintégrage pour d’autres versions de serveur Windows s’appliquent également si vous exécutez les Microsoft Defender pour point de terminaison précédentes pour Windows Server 2016 et Windows Server 2012 R2 qui nécessite le MMA. Les instructions pour migrer vers la nouvelle solution unifiée se trouvent [dans les scénarios de migration de serveur dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Voir aussi

- [Intégrer des appareils Windows à l’aide de Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Intégrer des appareils Windows à l’aide d’une stratégie de groupe](configure-endpoints-gp.md)
- [Intégrer les ordinateurs virtuels d’infrastructure de bureau (VDI) non persistants](configure-endpoints-vdi.md)
