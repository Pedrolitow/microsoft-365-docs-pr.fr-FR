---
title: Création de rapports de pare-feu d’hôte dans Microsoft Defender pour point de terminaison
description: Hébergez et affichez les rapports de pare-feu dans Microsoft 365 Defender portail.
keywords: windows defender, pare-feu
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 41fa5aece6f8c18ef16dbf624f90a1ead25b45f5
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174901"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Création de rapports de pare-feu d’hôte dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Si vous êtes administrateur général ou de sécurité, vous pouvez désormais héberger des rapports de pare-feu sur le [portail Microsoft 365 Defender](https://security.microsoft.com). Cette fonctionnalité vous permet d’afficher les rapports de pare-feu Windows 10, Windows 11, Windows Server 2019 et Windows Server 2022 à partir d’un emplacement centralisé.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez exécuter Windows 10 ou Windows 11, ou Windows Server 2019 ou Windows Server 2022.
- Pour intégrer des appareils au service Microsoft Defender pour point de terminaison, voir [ici](onboard-configure.md).
- Pour <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">que Microsoft 365 Defender portail</a> commence à recevoir les données, vous devez activer **les événements d’audit** pour Windows Defender Pare-feu avec Advanced Security :
  - [Audit Filtering Platform Packet Drop](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Auditer la connexion à la plateforme de filtrage](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Activez ces événements à l’aide de l’éditeur d’objets stratégie de groupe, de la stratégie de sécurité locale ou des commandes auditpol.exe. Pour plus d’informations, voir [ici](/windows/win32/fwp/auditing-and-logging).
  - Les deux commandes PowerShell sont les suivantes :
    - **auditpol /set /subcategory:"Filtering Platform Packet Drop » /failure:enable**
    - **auditpol /set /subcategory:"Filtering Platform Connection » /failure:enable**

## <a name="the-process"></a>Le processus

> [!NOTE]
> Veillez à suivre les instructions de la section ci-dessus et à configurer correctement vos appareils pour la participation en préversion anticipée.

- Après avoir activé les événements, Microsoft 365 Defender commence à surveiller les données.
  - Adresse IP distante, port distant, port local, adresse IP locale, nom de l’ordinateur, traiter entre les connexions entrantes et sortantes.
- Les administrateurs peuvent maintenant voir Windows activité de pare-feu hôte [ici](https://security.microsoft.com/firewall).
  - Des rapports supplémentaires peuvent être facilités en téléchargeant le [script de création de rapports personnalisés](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) pour surveiller les activités de pare-feu Windows Defender à l’aide de Power BI.
  - Jusqu’à 12 heures peuvent être nécessaires avant que les données ne se reflètent.

## <a name="supported-scenarios"></a>Scénarios pris en charge

Les scénarios suivants sont pris en charge pendant la préversion ring0.

### <a name="firewall-reporting"></a>Création de rapports de pare-feu

Voici quelques exemples de pages de rapport de pare-feu. Vous trouverez ici un résumé de l’activité entrante, sortante et d’application. Vous pouvez accéder directement à cette page en accédant à <https://security.microsoft.com/firewall>.

:::image type="content" source="images/host-firewall-reporting-page.png" alt-text="Page de création de rapports du pare-feu hôte" lightbox="\images\host-firewall-reporting-page.png":::

Ces rapports sont également accessibles en accédant à **ReportsSecurity** >  **ReportDevices** >  (section) situé en bas de la carte **Connexions entrantes bloquées par le pare-feu**.

### <a name="from-computers-with-a-blocked-connection-to-device"></a>De « Ordinateurs avec une connexion bloquée » à l’appareil

Les cartes prennent en charge les objets interactifs. Vous pouvez explorer l’activité d’un appareil en cliquant sur le nom de l’appareil, qui lancera le portail Microsoft 365 Defender dans un nouvel onglet et vous amènera directement à l’onglet **Chronologie** de l’appareil.

:::image type="content" source="images/firewall-reporting-blocked-connection.png" alt-text="Les ordinateurs avec une page de connexion bloquée" lightbox="\images\firewall-reporting-blocked-connection.png":::

Vous pouvez maintenant sélectionner l’onglet **Chronologie** , qui vous donne la liste des événements associés à cet appareil.

Après avoir cliqué sur le bouton **Filtres** dans le coin supérieur droit du volet d’affichage, sélectionnez le type d’événement souhaité. Dans ce cas, sélectionnez **Événements de pare-feu** et le volet est filtré sur les événements de pare-feu.

:::image type="content" source="images/firewall-reporting-filters-button.png" alt-text="Bouton Filtres" lightbox="\images\firewall-reporting-filters-button.png":::

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Explorer la chasse avancée (actualisation en préversion)

Les rapports de pare-feu prennent en charge l’exploration de la carte directement dans **La chasse avancée** en cliquant sur le bouton **Ouvrir la chasse avancée** . La requête sera préremplie.

:::image type="content" source="images/firewall-reporting-advanced-hunting.png" alt-text="Bouton Ouvrir la chasse avancée" lightbox="\images\firewall-reporting-advanced-hunting.png":::

La requête peut maintenant être exécutée et tous les événements de pare-feu associés des 30 derniers jours peuvent être explorés.

Pour des rapports supplémentaires ou des modifications personnalisées, la requête peut être exportée dans Power BI pour une analyse plus approfondie. Vous pouvez faciliter la création de rapports personnalisés en téléchargeant le [script de création de rapports personnalisés](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) pour surveiller les activités de pare-feu Windows Defender à l’aide de Power BI.
