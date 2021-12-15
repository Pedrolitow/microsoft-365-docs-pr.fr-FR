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
ms.openlocfilehash: b5aaad7363b42e18a0ca21e4d56d118218cec1a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531797"
---
# <a name="host-firewall-reporting-in-microsoft-defender-for-endpoint"></a>Création de rapports de pare-feu d’hôte dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Si vous êtes un administrateur, vous pouvez désormais héberger des rapports de pare-feu sur [le portail Microsoft 365 Defender.](https://security.microsoft.com) Cette fonctionnalité vous permet d’afficher les rapports de pare-feu Windows 10, Windows 11, Windows Server 2019 et Windows Server 2022 à partir d’un emplacement centralisé.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être en Windows 10 ou Windows 11, Windows Server 2019 ou Windows Server 2022.
- Pour intégrer des appareils au service Microsoft Defender for Endpoint, voir [ici.](onboard-configure.md)
- Pour <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail de</a> réception des données, vous devez activer les événements d’audit pour Windows Defender pare-feu avec fonctions avancées de sécurité : 
  - [Auditer le drop de paquets de plateforme de filtrage](/windows/security/threat-protection/auditing/audit-filtering-platform-packet-drop)
  - [Auditer la connexion à la plateforme de filtrage](/windows/security/threat-protection/auditing/audit-filtering-platform-connection)
- Activez ces événements à l’aide de l’Éditeur d’objets de stratégie de groupe, de la stratégie de sécurité locale ou auditpol.exe commandes. Pour plus d’informations, voir [ici.](/windows/win32/fwp/auditing-and-logging)
  - Les deux commandes PowerShell sont :
    - **auditpol /set /subcategory:"Filtering Platform Packet Drop » /failure:enable**
    - **auditpol /set /subcategory:"Filtering Platform Connection » /failure:enable**

## <a name="the-process"></a>Processus

> [!NOTE]
> Veillez à suivre les instructions de la section ci-dessus et à configurer correctement vos appareils pour la participation à la prévisualisation.

- Après l’activation des événements, Microsoft 365 Defender commence à surveiller les données.
  - Adresse IP distante, port distant, port local, adresse IP locale, nom de l’ordinateur, processus entre les connexions entrantes et sortantes.
- Les administrateurs peuvent désormais voir Windows activité de pare-feu [hôte ici.](https://security.microsoft.com/firewall)
  - La création de rapports supplémentaires peut être facilitée en téléchargeant le [script](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) de création de rapports personnalisé pour surveiller les activités du pare-feu Windows Defender à l’aide de Power BI.
  - La réflexion des données peut prendre jusqu’à 12 heures.

## <a name="supported-scenarios"></a>Scénarios pris en charge

Les scénarios suivants sont pris en charge pendant ring0 Preview.

### <a name="firewall-reporting"></a>Rapports de pare-feu

Voici quelques exemples de pages de rapport de pare-feu. Vous y trouverez un résumé de l’activité entrante, sortante et des applications. Vous pouvez accéder à cette page directement en accédant à <https://security.microsoft.com/firewall> .

> [!div class="mx-imgBorder"]
> ![Page de rapports du pare-feu hôte.](\images\host-firewall-reporting-page.png)

Ces rapports sont également accessibles en accédant à la section Périphériques de rapport de sécurité des rapports située en bas de la carte Connexions entrantes bloquées du  >    >   **pare-feu.**

### <a name="from-computers-with-a-blocked-connection-to-device"></a>De « Ordinateurs avec une connexion bloquée » à l’appareil

Les cartes supportent les objets interactifs. Vous pouvez vous lancer dans l’activité d’un appareil en cliquant sur le nom de l’appareil,  ce qui lance le portail Microsoft 365 Defender dans un nouvel onglet et vous dirige directement vers l’onglet Chronologie de l’appareil.

> [!div class="mx-imgBorder"]
> ![Ordinateurs avec une connexion bloquée.](\images\firewall-reporting-blocked-connection.png)

Vous pouvez maintenant sélectionner **l’onglet** Chronologie, qui vous donne la liste des événements associés à cet appareil.

Après avoir cliqué sur le bouton **Filtres** dans le coin supérieur droit du volet d’affichage, sélectionnez le type d’événement de votre choix. Dans ce cas, sélectionnez **événements de** pare-feu et le volet sera filtré en événements de pare-feu.

> [!div class="mx-imgBorder"]
> ![Bouton Filtres.](\images\firewall-reporting-filters-button.png)

### <a name="drill-into-advanced-hunting-preview-refresh"></a>Recherche avancée (actualisation de l’aperçu)

Les rapports de pare-feu  prendre en charge l’exploration à partir de la carte directement dans la recherche avancée en cliquant sur le **bouton Ouvrir le chasse** avancé. La requête sera pré-remplie.

> [!div class="mx-imgBorder"]
> ![Ouvrez le bouton de recherche avancée.](\images\firewall-reporting-advanced-hunting.png)

La requête peut maintenant être exécutée et tous les événements de pare-feu associés des 30 derniers jours peuvent être explorer.

Pour des rapports supplémentaires ou des modifications personnalisées, la requête peut être exportée dans Power BI pour une analyse plus approfondie. La création de rapports personnalisés peut être facilitée en téléchargeant le [script](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Firewall) de création de rapports personnalisé pour surveiller les activités du pare-feu Windows Defender à l’aide de Power BI.
