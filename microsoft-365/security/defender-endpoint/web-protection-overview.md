---
title: Protection Web
description: Découvrez la protection web dans Microsoft Defender pour point de terminaison et comment elle peut protéger votre organisation
keywords: protection web, protection contre les menaces web, navigation web, sécurité, hameçonnage, programmes malveillants, exploit, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web, sites web malveillants
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 07/25/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 886ed68514235669d72fe260cacc9b150d9a04d3
ms.sourcegitcommit: ecc04b5b8f84b34255a2d5e90b5ab596af0d16c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2022
ms.locfileid: "67497777"
---
# <a name="web-protection"></a>Protection Web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

## <a name="about-web-protection"></a>À propos de la protection web

La protection web dans Microsoft Defender pour point de terminaison est une fonctionnalité constituée de protection contre les [menaces web](web-threat-protection.md), de [filtrage de contenu web](web-content-filtering.md) et [d’indicateurs personnalisés](manage-indicators.md). La protection web vous permet de sécuriser vos appareils contre les menaces web et vous aide à réglementer le contenu indésirable. Vous pouvez trouver des rapports de protection Web dans le portail Microsoft 365 Defender en accédant à **Rapports > Protection Web**.

:::image type="content" source="images/web-protection.png" alt-text="Les cartes de protection web" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>Protection contre les menaces web

Les cartes qui composent la protection contre les **menaces web sont les détections de menaces web au fil du temps** et le **récapitulatif des menaces web**.

La protection contre les menaces web comprend :

- Visibilité complète des menaces web qui affectent votre organisation.
- Fonctionnalités d’investigation sur l’activité des menaces liées au web par le biais d’alertes et de profils complets d’URL et des appareils qui accèdent à ces URL.
- Un ensemble complet de fonctionnalités de sécurité qui suivent les tendances générales d’accès aux sites web malveillants et indésirables.

> [!NOTE]
> Pour les processus autres que Microsoft Edge et Internet Explorer, les scénarios de protection web tirent parti de la protection réseau pour l’inspection et l’application :
>
> - L’adresse IP est prise en charge pour les trois protocoles (TCP, HTTP et HTTPS (TLS).
> - Seules les adresses IP uniques sont prises en charge (pas de blocs CIDR ou de plages d’adresses IP) dans les indicateurs personnalisés.
> - Les URL chiffrées (chemin d’accès complet) ne peuvent être bloquées que sur les navigateurs internes (Internet Explorer, Edge).
> - Les URL chiffrées (FQDN uniquement) peuvent être bloquées dans des navigateurs tiers (c’est-à-dire autres qu’Internet Explorer, Edge).
> - Des blocs de chemin d’URL complets peuvent être appliqués pour les URL non chiffrées.
>
> Il peut y avoir jusqu’à 2 heures de latence (généralement moins) entre le moment où l’action est effectuée et l’URL et l’adresse IP bloquées.

Pour plus d’informations, consultez [la protection contre les menaces web](web-threat-protection.md).

### <a name="custom-indicators"></a>Indicateurs personnalisés

Les détections d’indicateurs personnalisés sont également résumées dans les rapports de menaces web de vos organisations sous **détections de menaces web au fil du temps** et **récapitulatif des menaces web**.

L’indicateur personnalisé inclut :

- Possibilité de créer des indicateurs d’adresse IP et d’URL de compromission pour protéger votre organisation contre les menaces.
- Fonctionnalités d’investigation sur les activités liées à vos profils IP/URL personnalisés et aux appareils qui accèdent à ces URL.
- Possibilité de créer des stratégies d’autorisation, de blocage et d’avertissement pour les adresses IP et les URL.

Pour plus d’informations, consultez [Créer des indicateurs pour les adresses IP et les URL/domaines](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>Filtrage du contenu web

Le filtrage de contenu web inclut **l’activité web par catégorie**, le **résumé du filtrage de contenu Web** et le **résumé de l’activité web**.

Le filtrage de contenu web inclut :

- Les utilisateurs ne peuvent pas accéder aux sites web dans des catégories bloquées, qu’ils naviguent localement ou en déplacement.
- Vous pouvez déployer facilement des stratégies variées sur différents ensembles d’utilisateurs à l’aide des groupes d’appareils définis dans les [Microsoft Defender pour point de terminaison paramètres de contrôle d’accès en fonction du rôle](/microsoft-365/security/defender-endpoint/rbac).
- Vous pouvez accéder aux rapports web au même emplacement central, avec une visibilité sur les blocs réels et l’utilisation du web.

Pour plus d’informations, consultez [le filtrage de contenu Web](web-content-filtering.md).

## <a name="order-of-precedence"></a>Ordre de priorité

La protection web est constituée des composants suivants, répertoriés par ordre de priorité. Chacun de ces composants est appliqué par le client SmartScreen dans Microsoft Edge et par le client De protection réseau dans tous les autres navigateurs et processus.

- Indicateurs personnalisés (adresse IP/URL, stratégies de Microsoft Defender for Cloud Apps)
  - Autoriser
  - Avertir
  - Bloquer

- Menaces web (programmes malveillants, hameçonnage)
  - SmartScreen Intel, y compris Exchange Online Protection (EOP)
  - Escalades

- Filtrage de contenu web (WCF)

> [!NOTE]
> Microsoft Defender for Cloud Apps génère actuellement des indicateurs uniquement pour les URL bloquées.

L’ordre de priorité est lié à l’ordre des opérations par lequel une URL ou une adresse IP est évaluée. Par exemple, si vous disposez d’une stratégie de filtrage de contenu web, vous pouvez créer des exclusions par le biais d’indicateurs d’ADRESSE IP/URL personnalisés. Les indicateurs personnalisés de compromission (IoC) sont plus élevés dans l’ordre de priorité que les blocs WCF.

De même, lors d’un conflit entre les indicateurs, autorise toujours la priorité sur les blocs (logique de remplacement). Cela signifie qu’un indicateur d’autorisation gagnera tout indicateur de bloc présent.

Le tableau ci-dessous récapitule certaines configurations courantes qui présenteraient des conflits au sein de la pile de protection web. Il identifie également les déterminations résultantes en fonction de la priorité indiquée ci-dessus.

<br>

****

|Stratégie d’indicateur personnalisé|Stratégie de menace web|Stratégie WCF|Stratégie Defender pour Cloud Apps|Résultat|
|---|---|---|---|---|
|Autoriser|Bloquer|Bloquer|Bloquer|Autoriser (remplacement de la protection web)|
|Autoriser|Autoriser|Bloquer|Bloquer|Autoriser (exception WCF)|
|Avertir|Bloquer|Bloquer|Bloquer|Avertir (remplacer)|
|

Les adresses IP internes ne sont pas prises en charge par les indicateurs personnalisés. Pour une stratégie d’avertissement lorsqu’elle est contournée par l’utilisateur final, le site est débloqué pendant 24 heures pour cet utilisateur par défaut. Cette période peut être modifiée par le Administration et transmise par le service cloud SmartScreen. La possibilité de contourner un avertissement peut également être désactivée dans Microsoft Edge à l’aide du fournisseur de solutions Cloud pour les blocs de menaces web (programmes malveillants/hameçonnage). Pour plus d’informations, consultez [Paramètres SmartScreen de Microsoft Edge](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>Protéger les navigateurs

Dans tous les scénarios de protection web, SmartScreen et Network Protection peuvent être utilisés ensemble pour garantir la protection entre les navigateurs et processus internes et tiers. SmartScreen est intégré directement à Microsoft Edge, tandis que la protection réseau surveille le trafic dans les navigateurs et processus tiers. Le diagramme ci-dessous illustre ce concept. Ce diagramme des deux clients travaillant ensemble pour fournir plusieurs couvertures de navigateur/d’application est précis pour toutes les fonctionnalités de la protection web (indicateurs, menaces web, filtrage de contenu).

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="L’utilisation de smartScreen et de la protection réseau conjointement" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>Résoudre les problèmes liés aux blocs de points de terminaison

Les réponses du cloud SmartScreen sont normalisées. Des outils tels que Fiddler peuvent être utilisés pour inspecter la réponse du service cloud, ce qui vous aidera à déterminer la source du bloc.

Lorsque le service cloud SmartScreen répond avec une réponse d’autorisation, de blocage ou d’avertissement, une catégorie de réponse et un contexte de serveur sont relayés au client. Dans Microsoft Edge, la catégorie de réponse est utilisée pour déterminer la page de blocs appropriée à afficher (malveillant, hameçonnage, stratégie organisationnelle).

Le tableau ci-dessous présente les réponses et leurs fonctionnalités corrélées.

<br>

****

|ResponseCategory|Fonctionnalité responsable du bloc|
|---|---|
|CustomPolicy|Wcf|
|CustomBlockList|Indicateurs personnalisés|
|CasbPolicy|Defender for Cloud Apps|
|Malveillant|Menaces web|
|Hameçonnage|Menaces web|
|||

## <a name="advanced-hunting-for-web-protection"></a>Repérage avancé pour la protection web

Les requêtes Kusto dans la chasse avancée peuvent être utilisées pour résumer les blocs de protection web dans votre organisation pendant 30 jours maximum. Ces requêtes utilisent les informations répertoriées ci-dessus pour faire la distinction entre les différentes sources de blocs et les résumer de manière conviviale. Par exemple, la requête ci-dessous répertorie tous les blocs WCF provenant de Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomPolicy"
```

De même, vous pouvez utiliser la requête ci-dessous pour répertorier tous les blocs WCF provenant de la protection réseau (par exemple, un bloc WCF dans un navigateur tiers). Notez que l’ActionType a été mis à jour et que « Experience » a été remplacé par « ResponseCategory ».

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

Pour répertorier les blocs qui sont dus à d’autres fonctionnalités (comme les indicateurs personnalisés), reportez-vous au tableau ci-dessus qui présente chaque fonctionnalité et sa catégorie de réponse respective. Ces requêtes peuvent également être modifiées pour rechercher des données de télémétrie liées à des machines spécifiques de votre organisation. Notez que l’ActionType indiqué dans chaque requête ci-dessus affiche uniquement les connexions qui ont été bloquées par une fonctionnalité de protection web, et pas tout le trafic réseau.

## <a name="user-experience"></a>Expérience utilisateur

Si un utilisateur visite une page web qui présente un risque de programmes malveillants, de hameçonnage ou d’autres menaces web, Microsoft Edge déclenche une page de blocage indiquant « Ce site a été signalé comme dangereux », ainsi que des informations relatives à la menace.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="Page bloquée par Microsoft Edge" lightbox="../../media/web-protection-malicious-block.png":::

S’il est bloqué par WCF ou un indicateur personnalisé, une page de blocs s’affiche dans Microsoft Edge qui indique à l’utilisateur que ce site est bloqué par son organisation.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="Page bloquée par votre organisation" lightbox="../../media/web-protection-indicator-blockpage.png":::

Dans tous les cas, aucune page de blocs n’est affichée dans les navigateurs tiers, et l’utilisateur voit une page « Échec de connexion sécurisée » avec une notification toast. Selon la stratégie responsable du bloc, un utilisateur voit un autre message dans la notification toast. Par exemple, le filtrage de contenu web affiche le message « Ce contenu est bloqué ».

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="Page bloquée par WCF" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>Signaler des faux positifs

Pour signaler un faux positif pour les sites jugés dangereux par SmartScreen, utilisez le lien qui apparaît sur la page de blocs dans Microsoft Edge (comme indiqué ci-dessus).

Pour WCF, vous pouvez contester la catégorie d’un domaine. Accédez à l’onglet **Domaines** des rapports WCF, puis cliquez sur **Erreur de** rapport. Un menu volant s’ouvre. Définissez la priorité de l’incident et fournissez des détails supplémentaires, tels que la catégorie suggérée. Pour plus d’informations sur l’activation de WCF et sur la façon de contester les catégories, consultez [le filtrage de contenu Web](web-content-filtering.md).

Pour plus d’informations sur la façon d’envoyer des faux positifs/négatifs, consultez [Address false positives/negatives in Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>Informations connexes

<br>

****

|Rubrique|Description|
|---|---|
|[Protection contre les menaces web](web-threat-protection.md) | Arrêtez l’accès aux sites de hameçonnage, aux vecteurs de programmes malveillants, aux sites d’exploitation, aux sites non approuvés ou à faible réputation et aux sites que vous avez bloqués.|
|[Filtrage du contenu web](web-content-filtering.md) | Suivez et réglementez l’accès aux sites web en fonction de leurs catégories de contenu.|
|
