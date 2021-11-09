---
title: Protection Web
description: En savoir plus sur la protection web dans Microsoft Defender pour point de terminaison et sur la façon dont elle peut protéger votre organisation
keywords: protection web, protection contre les menaces web, navigation web, sécurité, hameçonnage, programmes malveillants, attaque, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web, sites web malveillants
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 6f8a9d27566ea3f6fcf43ad2b8f183c6800bb8aa
ms.sourcegitcommit: e09ced3e3628bf2ccb84d205d9699483cbb4b3b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2021
ms.locfileid: "60883712"
---
# <a name="web-protection"></a>Protection Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>À propos de la protection web

La protection web dans Microsoft Defender pour point de terminaison est une fonctionnalité de protection contre les menaces [web,](web-threat-protection.md)de filtrage de contenu [Web](web-content-filtering.md)et [d’indicateurs personnalisés.](manage-indicators.md) La protection web vous permet de sécuriser vos appareils contre les menaces web et de contrôler le contenu indésirable. Vous pouvez trouver des rapports de protection Web dans le portail Microsoft 365 Defender en allant à **Rapports > protection Web.**

:::image type="content" alt-text="Image de toutes les cartes de protection web." source="images/web-protection.png" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Protection contre les menaces web

Les cartes qui font la protection contre les menaces web sont les détections de **menaces Web** au fil du temps et le résumé **des menaces Web.**

La protection contre les menaces web inclut :

- Visibilité complète des menaces web qui affectent votre organisation.
- Fonctionnalités d’investigation sur l’activité des menaces liées au web par le biais d’alertes et de profils complets d’URL et des appareils qui accèdent à ces URL.
- Ensemble complet de fonctionnalités de sécurité qui s’y rapportent pour suivre les tendances générales d’accès aux sites web malveillants et indésirables.

Pour plus d’informations, voir [Protection contre les menaces web.](web-threat-protection.md)

### <a name="custom-indicators"></a>Indicateurs personnalisés

Les détections d’indicateurs personnalisés sont également résumées dans les rapports sur les menaces web de votre organisation sous détections de **menaces Web** au fil du temps et résumé **des menaces Web.**

L’indicateur personnalisé inclut :

- Possibilité de créer des indicateurs de compromission basés sur l’ADRESSE IP et l’URL pour protéger votre organisation contre les menaces.
- Fonctionnalités d’investigation sur les activités liées à vos profils IP/URL personnalisés et sur les appareils qui accèdent à ces URL.
- Possibilité de créer des stratégies d’autoriser, de bloquer et d’avertir pour les adresses IP et les URL.

Pour plus d’informations, voir [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrage du contenu web

Le filtrage de contenu **Web inclut l’activité Web par catégorie,** le résumé du filtrage de contenu **Web** et le résumé **des activités Web.**

Le filtrage de contenu Web inclut :

- Les utilisateurs ne peuvent pas accéder aux sites web dans les catégories bloquées, qu’ils naviguent en local ou en de suite.
- Vous pouvez facilement déployer des stratégies variées sur différents ensembles d’utilisateurs à l’aide des groupes d’appareils définis dans les paramètres de contrôle d’accès basés sur les rôles Microsoft Defender for [Endpoint.](/microsoft-365/security/defender-endpoint/rbac)
- Vous pouvez accéder aux rapports web dans le même emplacement central, avec une visibilité sur les blocs réels et l’utilisation du web.

Pour plus d’informations, voir [filtrage de contenu Web.](web-content-filtering.md)

## <a name="order-of-precedence"></a>Ordre de priorité

La protection Web est composé des composants suivants, répertoriés par ordre de priorité. Chacun de ces composants est appliqué par le client SmartScreen dans Microsoft Edge et par le client Protection du réseau dans tous les autres navigateurs et processus.

- Indicateurs personnalisés (IP/URL, Microsoft Cloud App Security (MCAS)
  - Autoriser
  - Avertir
  - Bloquer

- Menaces web (programmes malveillants, hameçonnage)
  - SmartScreen Intel, y compris Exchange Online Protection (EOP)
  - Escalades

- Web Content Filtering (WCF)

> [!NOTE]
> Microsoft Cloud App Security (MCAS) génère actuellement des indicateurs uniquement pour les URL bloquées.

L’ordre de priorité est lié à l’ordre des opérations par lequel une URL ou une adresse IP est évaluée. Par exemple, si vous avez une stratégie de filtrage de contenu web, vous pouvez créer des exclusions par le biais d’indicateurs IP/URL personnalisés. Les indicateurs de compromis personnalisés (IoC) sont plus élevés dans l’ordre de priorité que les blocs WCF.

De même, lors d’un conflit entre les indicateurs, permet de toujours être prioritaire sur les blocs (logique de remplacement). Cela signifie qu’un indicateur d’autoriser l’utilisateur l’emporte sur n’importe quel indicateur de blocage présent.

Le tableau ci-dessous récapitule certaines configurations courantes qui présenteraient des conflits au sein de la pile de protection web. Il identifie également les déterminations résultantes en fonction de la priorité répertoriée ci-dessus.

<br>

****

|Stratégie d’indicateur personnalisé|Stratégie contre les menaces web|Stratégie WCF|Stratégie MCAS|Résultat|
|---|---|---|---|---|
|Autoriser|Bloquer|Bloquer|Bloquer|Allow (remplacement de la protection Web)|
|Autoriser|Autoriser|Bloquer|Bloquer|Autoriser (exception WCF)|
|Avertir|Bloquer|Bloquer|Bloquer|Avertir (remplacer)|
|

Les adresses IP internes ne sont pas pris en charge par les indicateurs personnalisés. Pour une stratégie d’avertissement lorsqu’elle est contourné par l’utilisateur final, le site est débloqué pendant 24 heures pour cet utilisateur par défaut. Cette période peut être modifiée par l’administrateur et transmise par le service cloud SmartScreen. La possibilité de contourner un avertissement peut également être désactivée dans Microsoft Edge l’aide du programme CSP pour les blocs de menaces web (programmes malveillants/hameçonnage). Pour plus d’informations, [voir Microsoft Edge SmartScreen Paramètres](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Protéger les navigateurs

Dans tous les scénarios de protection web, SmartScreen et la Protection du réseau peuvent être utilisés ensemble pour assurer la protection des navigateurs et processus internes et tiers. SmartScreen est intégré directement à Microsoft Edge, tandis que la Protection du réseau surveille le trafic dans les navigateurs et processus tiers. Le diagramme ci-dessous illustre ce concept. Ce diagramme des deux clients travaillant ensemble pour fournir plusieurs couvertures de navigateur/d’application est précis pour toutes les fonctionnalités de protection web (indicateurs, menaces web, filtrage de contenu).

:::image type="content" alt-text="Utilisation de SmartScreen et de la Protection du réseau ensemble." source="../../media/web-protection-protect-browsers.png" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Résoudre les problèmes de blocs de points de terminaison

Les réponses du cloud SmartScreen sont normalisées. Des outils tels que Fiddler peuvent être utilisés pour inspecter la réponse du service cloud, ce qui permet de déterminer la source du bloc.

Lorsque le service cloud SmartScreen répond avec une réponse d’avertissement, de blocage ou d’avertissement, une catégorie de réponse et un contexte de serveur sont relayés au client. Dans Microsoft Edge, la catégorie de réponse est utilisée pour déterminer la page de blocage appropriée à afficher (malveillant, hameçonnage, stratégie d’organisation).

Le tableau ci-dessous présente les réponses et leurs fonctionnalités corrélées.

<br>

****

|ResponseCategory|Fonctionnalité responsable du bloc|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|Indicateurs personnalisés|
|CasbPolicy|MCAS|
|Malveillant|Menaces web|
|Hameçonnage|Menaces web|
|||

## <a name="advanced-hunting-for-web-protection"></a>Recherche avancée pour la protection web

Les requêtes Kusto dans le hunting avancé peuvent être utilisées pour résumer les blocs de protection web de votre organisation pendant 30 jours. Ces requêtes utilisent les informations répertoriées ci-dessus pour faire la distinction entre les différentes sources de blocs et les résumer de manière conviviale. Par exemple, la requête ci-dessous répertorie tous les blocs WCF provenant de Microsoft Edge.

```kusto
DeviceEvents 
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomPolicy"
```

De même, vous pouvez utiliser la requête ci-dessous pour lister tous les blocs WCF provenant de la Protection du réseau (par exemple, un bloc WCF dans un navigateur tiers). Notez que ActionType a été mis à jour et que « Experience » a été changé en « ResponseCategory ».

```kusto
DeviceEvents 
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Pour lister les blocs qui sont dus à d’autres fonctionnalités (comme les indicateurs personnalisés), reportez-vous au tableau ci-dessus en décrivant chaque fonctionnalité et leur catégorie de réponse respective. Ces requêtes peuvent également être modifiées pour rechercher des données de télémétrie relatives à des ordinateurs spécifiques de votre organisation. Notez que l’action ActionType indiquée dans chaque requête ci-dessus n’affiche que les connexions bloquées par une fonctionnalité de protection web, et non l’ensemble du trafic réseau.

## <a name="user-experience"></a>Expérience utilisateur

Si un utilisateur visite une page web qui présente un risque de programmes malveillants, d’hameçonnage ou d’autres menaces web, Microsoft Edge déclenche une page de blocage qui indique « Ce site a été signalé comme non sécurisé » avec des informations relatives à la menace.

> [!div class="mx-imgBorder"]
> ![Page bloquée par Microsoft Edge.](../../media/web-protection-malicious-block.png)

Si elle est bloquée par WCF ou un indicateur personnalisé, une page de blocage s’affiche dans Microsoft Edge qui indique à l’utilisateur que ce site est bloqué par son organisation.

> [!div class="mx-imgBorder"]
> ![Page bloquée par votre organisation.](../../media/web-protection-indicator-blockpage.png)

Dans tous les cas, aucune page de blocage n’est affichée dans les navigateurs tiers et l’utilisateur voit une page « Échec de connexion sécurisée » avec une notification toast. Selon la stratégie responsable du blocage, un utilisateur voit un autre message dans la notification toast. Par exemple, le filtrage de contenu web affiche le message « Ce contenu est bloqué ».

> [!div class="mx-imgBorder"]
> ![Page bloquée par WCF.](../../media/web-protection-np-block.png)

## <a name="report-false-positives"></a>Signaler les faux positifs

Pour signaler un faux positif pour les sites qui ont été considérés comme dangereux par SmartScreen, utilisez le lien qui apparaît sur la page de blocage dans Microsoft Edge (comme illustré ci-dessus).

Pour WCF, vous pouvez être en conflit avec la catégorie d’un domaine. Accédez à **l’onglet Domaines** des rapports WCF, puis cliquez sur **Report Inaccuracy**. Un volant s’ouvre. Définissez la priorité de l’incident et fournissez des détails supplémentaires, tels que la catégorie suggérée. Pour plus d’informations sur la façon d’activer WCF et de disputer des catégories, voir [filtrage de contenu Web.](web-content-filtering.md)

Pour plus d’informations sur la soumission de faux positifs/négatifs, voir [Adresse faux positifs/négatifs dans Microsoft Defender pour point de terminaison.](defender-endpoint-false-positives-negatives.md)

## <a name="related-information"></a>Informations connexes

<br>

****

|Rubrique|Description|
|---|---|
|[Protection contre les menaces web](web-threat-protection.md) | Arrêtez l’accès aux sites d’hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites nontrus ou à faible réputation et aux sites que vous avez bloqués.|
|[Filtrage du contenu web](web-content-filtering.md) | Suivre et contrôler l’accès aux sites web en fonction de leurs catégories de contenu.|
|
