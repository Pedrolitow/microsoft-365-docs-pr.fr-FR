---
title: Créer des indicateurs basés sur des certificats
ms.reviewer: ''
description: Créez des indicateurs basés sur des certificats qui définissent la détection, la prévention et l’exclusion des entités.
keywords: ioc, certificat, certificats, gérer, autorisé, bloqué, bloquer, nettoyer, malveillant, hachage de fichier, adresse IP, url, domaine
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
ms.openlocfilehash: 0e74fd5a0ffc62d077f9110b014af5d3b0813afd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60154841"
---
# <a name="create-indicators-based-on-certificates"></a>Créer des indicateurs basés sur des certificats

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Vous pouvez créer des indicateurs pour les certificats. Voici quelques cas d’utilisation courants :

- Scénarios dans le cas où vous devez déployer [](controlled-folders.md) des technologies de blocage, telles que les règles de réduction de la [surface](attack-surface-reduction.md) d’attaque et l’accès contrôlé aux dossiers, mais qui doivent autoriser les comportements des applications signées en ajoutant le certificat dans la liste d’autorisations.
- Blocage de l’utilisation d’une application signée spécifique au sein de votre organisation. En créant un indicateur pour bloquer le certificat de l’application, l’antivirus Windows Defender empêchera les exécutions de fichiers (blocage et correction) et les examens et corrections automatisés se comporteront de la même manière.

## <a name="before-you-begin"></a>Avant de commencer

Il est important de comprendre les exigences suivantes avant de créer des indicateurs pour les certificats :

- Cette fonctionnalité est disponible si votre organisation utilise Antivirus Windows Defender protection basée sur le cloud est activée. Pour plus d’informations, [voir Gérer la protection basée sur le cloud.](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus)
- La version du client anti-programme malveillant doit être 4.18.1901.x ou version ultérieure.
- Pris en charge sur les ordinateurs Windows 11, Windows 10, version 1703 ou ultérieure, Windows server 2016, 2019 et Windows Server 2022.
- Les définitions de protection contre les virus et menaces doivent être à jour.
- Cette fonctionnalité prend actuellement en charge l’entrée. CER ou . Extensions de fichier PEM.

> [!IMPORTANT]
>
> - Un certificat feuille valide est un certificat de signature qui possède un chemin de certification valide et doit être chaîné à l’autorité de certification racine (CA) approuvé par Microsoft. Sinon, un certificat personnalisé (auto-signé) peut être utilisé tant qu’il est approuvé par le client (le certificat de l’autorité de certification racine est installé sous l’ordinateur local « Autorités de certification racines de confiance »).
> - Les enfants ou le parent des IOC de certificats d’autorisation/de blocage ne sont pas inclus dans la fonctionnalité autoriser/bloquer les IoC, seuls les certificats feuille sont pris en charge.
> - Les certificats signés par Microsoft ne peuvent pas être bloqués.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>Créez un indicateur pour les certificats à partir de la page paramètres :

> [!IMPORTANT]
> La création et la suppression d’un certificat IoC peuvent prendre jusqu’à 3 heures.

1. Dans le volet de navigation, sélectionnez **Paramètres** \> **indicateurs de points** de \> **terminaison** (sous **Règles).**

2. Sélectionnez **Ajouter un indicateur**.

3. Spécifiez les détails suivants :
   - Indicateur : spécifiez les détails de l’entité et définissez l’expiration de l’indicateur.
   - Action : spécifiez l’action à prendre et fournissez une description.
   - Étendue : définir l’étendue du groupe d’ordinateurs.

4. Consultez les détails de l’onglet Résumé, puis cliquez sur **Enregistrer.**

## <a name="related-topics"></a>Rubriques connexes

- [Créer des indicateurs](manage-indicators.md)
- [Créer des indicateurs pour les fichiers](indicator-file.md)
- [Créer des indicateurs pour les IP et URL/domaines](indicator-ip-domain.md)
- [Gérer des indicateurs](indicator-manage.md)
