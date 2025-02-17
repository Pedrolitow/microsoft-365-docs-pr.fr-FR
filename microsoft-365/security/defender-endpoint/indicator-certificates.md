---
title: Créer des indicateurs basés sur des certificats
ms.reviewer: ''
description: Créez des indicateurs basés sur des certificats qui définissent la détection, la prévention et l’exclusion des entités.
keywords: ioc, certificate, certificates, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
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
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6d1662a948d0f8cd8298aa0f5226f374db661ead
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68646284"
---
# <a name="create-indicators-based-on-certificates"></a>Créer des indicateurs basés sur des certificats

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Vous pouvez créer des indicateurs pour les certificats. Voici quelques cas d’usage courants :

- Scénarios où vous devez déployer des technologies bloquantes, telles que [les règles de réduction de la surface d’attaque](attack-surface-reduction.md) et l’accès [contrôlé aux dossiers](controlled-folders.md) , mais devez autoriser les comportements des applications signées en ajoutant le certificat dans la liste verte.
- Blocage de l’utilisation d’une application signée spécifique au sein de votre organisation. En créant un indicateur pour bloquer le certificat de l’application, Windows Defender AV empêche les exécutions de fichiers (bloquer et corriger) et l’investigation et la correction automatisées se comportent de la même façon.

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les exigences suivantes avant de créer des indicateurs pour les certificats :

- Cette fonctionnalité est disponible si votre organisation utilise Microsoft Defender protection antivirus et cloud est activée. Pour plus d’informations, consultez [Gérer la protection basée sur le cloud](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
- La version du client Antimalware doit être 4.18.1901.x ou ultérieure.
- Pris en charge sur les machines sur Windows 10, version 1703 ou ultérieure, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 et Windows Server 2022.
    
    >[!NOTE]
    >Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne. 

- Les définitions de virus et de protection contre les menaces doivent être à jour.
- Cette fonctionnalité prend actuellement en charge l’entrée . CER ou . Extensions de fichier PEM.

> [!IMPORTANT]
>
> - Un certificat feuille valide est un certificat de signature qui a un chemin de certification valide et qui doit être chaîné à l’autorité de certification racine approuvée par Microsoft. Vous pouvez également utiliser un certificat personnalisé (auto-signé) tant qu’il est approuvé par le client (le certificat d’autorité de certification racine est installé sous l’ordinateur local « Autorités de certification racines approuvées »).
> - Les enfants ou le parent des E/S par certificat d’autorisation/bloc ne sont pas inclus dans la fonctionnalité IoC d’autorisation/bloc. Seuls les certificats feuille sont pris en charge.
> - Les certificats signés par Microsoft ne peuvent pas être bloqués.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>Créez un indicateur pour les certificats à partir de la page paramètres :

> [!IMPORTANT]
> La création et la suppression d’un IoC de certificat peuvent prendre jusqu’à 3 heures.

1. Dans le volet de navigation, sélectionnez **Paramètres** \> Points de **terminaison Indicateurs** \> (sous **Règles**).

2. Sélectionnez **Ajouter un indicateur**.

3. Spécifiez les détails suivants :
   - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
   - Action : spécifiez l’action à entreprendre et fournissez une description.
   - Étendue : définissez l’étendue du groupe d’ordinateurs.

4. Passez en revue les détails sous l’onglet Résumé, puis cliquez sur **Enregistrer**.

## <a name="related-topics"></a>Voir aussi

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Gérer des indicateurs](indicator-manage.md)
