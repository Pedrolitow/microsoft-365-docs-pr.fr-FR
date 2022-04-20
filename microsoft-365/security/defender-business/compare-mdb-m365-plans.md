---
title: Comparer les fonctionnalités de sécurité dans Microsoft 365 plans pour les petites et moyennes entreprises
description: Comprendre les différences entre Defender entreprise et Defender pour point de terminaison. Savoir ce qui est inclus dans chaque plan peut vous aider à prendre une décision éclairée pour votre entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 04/18/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: e32018f52f3a45624fcf07ae03e44c662a594297
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916312"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer Microsoft Defender pour les PME à Microsoft 365 Business Premium

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement aux clients et aux partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
>
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici.

Microsoft offre un large éventail de solutions et de services cloud, y compris plusieurs plans différents pour les petites et moyennes entreprises. Par exemple, [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) inclut des fonctionnalités de sécurité et de gestion des appareils, ainsi que des fonctionnalités de productivité, comme Office applications. Cet article est conçu pour aider à clarifier les fonctionnalités de sécurité, telles que la protection des appareils, qui sont incluses dans Microsoft 365 Business Premium, Microsoft Defender pour les PME et Microsoft Defender pour point de terminaison.

Microsoft Defender pour les PME est disponible sous forme d’offre autonome ou dans le cadre de Microsoft 365 Business Premium (à compter du 1er mars 2022).

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

**Utilisez cet article pour** :

- [Comparer Microsoft Defender pour les PME (autonome) à Microsoft 365 Business Premium](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Comparer Defender entreprise (autonome) à Microsoft Defender pour point de terminaison offres d’entreprise](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**Vous n’avez pas besoin d’un abonnement Microsoft 365 pour acheter et utiliser Microsoft Defender pour les PME.** Microsoft Defender pour les PME est inclus dans Microsoft 365 Business Premium, et il est disponible en tant que solution de sécurité autonome pour les petites et moyennes entreprises. Si vous avez déjà Microsoft 365 Business Basic ou Standard, envisagez d’ajouter une mise à niveau vers Microsoft 365 Business Premium ou d’ajouter des Microsoft Defender pour les PME pour obtenir plus de fonctionnalités de protection contre les menaces.

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer les fonctionnalités de sécurité dans Microsoft Defender pour les PME à Microsoft 365 Business Premium

> [!NOTE]
> Cet article est destiné à fournir une vue d’ensemble générale des fonctionnalités de protection contre les menaces incluses dans Microsoft Defender pour les PME (en tant que plan autonome) et Microsoft 365 Business Premium (qui inclut Defender entreprise). Cet article n’est pas destiné à servir de description de service ou de document de contrat de licence. Pour plus d’informations, consultez [Microsoft 365 conseils de gestion des licences pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

**À compter du 1er mars 2022, Defender entreprise démarrera le déploiement dans le cadre de Microsoft 365 Business Premium. Defender for Business en tant qu’offre autonome est toujours en préversion.**

Le tableau suivant compare les fonctionnalités de sécurité dans Defender entreprise (autonome) à Microsoft 365 Business Premium.

|Fonctionnalité/fonctionnalité|[Microsoft Defender pour les PME](mdb-overview.md)<br/>(autonome ; actuellement en préversion)|[Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(inclut Defender entreprise)|
|---|---|---|
|Protection par e-mail|Oui <br/>- [Analyse des e-mails avec Antivirus Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)|Oui <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [Analyse des e-mails avec Antivirus Microsoft Defender](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Protection antispam|Oui <br/>- Pour les appareils|Oui <br/>- Pour les appareils<br/>- Pour Microsoft 365 contenu d’e-mail, tel que les messages et les pièces jointes|
|Protection anti-programme malveillant|Oui<br/>- Pour les appareils|Oui <br/>- Pour les appareils<br/>- Pour Microsoft 365 contenu d’e-mail, tel que les messages et les pièces jointes|
|[Protection de nouvelle génération](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (protection antivirus et anti-programme malveillant)|Oui<br/>- Antivirus Microsoft Defender est inclus dans Windows 10 et versions ultérieures|Oui <br/>- Antivirus Microsoft Defender est inclus dans Windows 10 et versions ultérieures<br/>- Stratégies de protection de nouvelle génération pour les appareils intégrés|
|[Réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(Règles ASR dans Windows 10 ou version ultérieure et protection pare-feu)|Oui|Oui|
|[Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(détection basée sur le comportement et actions de réponse manuelles)|Oui|Oui|
|[Examen et réponse automatisés](../defender-endpoint/automated-investigations.md)|Oui|Oui|
|[Gestion des menaces et des vulnérabilités](../defender-endpoint/tvm-dashboard-insights.md)|Oui|Oui|
|Gestion et création de rapports centralisées|Oui|Oui|
|[API](../defender-endpoint/apis-intro.md) <br/>(pour l’intégration à des applications personnalisées ou à des solutions de création de rapports)|Oui|Oui|

## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Comparer Microsoft Defender pour les PME à Microsoft Defender pour point de terminaison Plans 1 et 2

Defender entreprise offre des fonctionnalités de niveau entreprise de Defender pour point de terminaison aux petites et moyennes entreprises.

Le tableau suivant compare les fonctionnalités et fonctionnalités de sécurité de Defender entreprise aux offres d’entreprise, Microsoft Defender pour point de terminaison Plans 1 et 2.

|Fonctionnalité/fonctionnalité|[Défenseur des affaires](mdb-overview.md)<br/>(autonome ; actuellement en préversion)|[Defender pour Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md)<br/>(pour les clients d’entreprise) |[Defender pour point de terminaison Plan 2](../defender-endpoint/microsoft-defender-endpoint.md)<br/>(pour les clients d’entreprise) |
|---|---|---|---|
|[Gestion centralisée](../defender-endpoint/manage-atp-post-migration.md) |Oui <sup>[[1](#fn1)]</sup>|Oui|Oui|
|[Configuration du client simplifiée](mdb-simplified-configuration.md)|Oui|Non|Non|
|[Gestion des menaces et des vulnérabilités](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)|Oui|Non|Oui|
|[Fonctionnalités de réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md)|Oui|Oui|Oui|
|[Protection de nouvelle génération](../defender-endpoint/next-generation-protection.md)|Oui|Oui|Oui|
|[Détection et réponse du point de terminaison](../defender-endpoint/overview-endpoint-detection-response.md)|Oui <sup>[[2](#fn2)]</sup>|Non|Oui|
|[Examen et réponse automatisés](../defender-endpoint/automated-investigations.md)|Oui <sup>[[3](#fn3)]</sup>|Non|Oui|
|[Repérage des menaces](../defender-endpoint/advanced-hunting-overview.md) et six mois de conservation des données |Non <sup>[[4](#fn4)]</sup>|Non|Oui|
|[Analyses de menaces](../defender-endpoint/threat-analytics.md)|Oui <sup>[[5](#fn5)]</sup>|Non|Oui|
|[Prise en charge multiplateforme](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS et Android OS)|Oui <sup>[[6](#fn6)]</sup>|Oui|Oui|
|[Spécialistes des menaces Microsoft](../defender-endpoint/microsoft-threat-experts.md)|Non|Non|Oui|
|API partenaires|Oui|Oui|Oui|
|[intégration Microsoft 365 Lighthouse](../../lighthouse/m365-lighthouse-overview.md) <br/>(Pour afficher les incidents de sécurité entre les locataires des clients)|Oui|Non|Non|

(<a id="fn1">1</a>) Intégrer et gérer des appareils dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou avec Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) Les fonctionnalités de détection et de réponse des points de terminaison (PEPT) dans Defender entreprise incluent la détection basée sur le comportement et les quatre types d’actions de réponse manuelles suivants : 
- Exécuter une analyse antivirus
- Isoler l’appareil
- Arrêter et mettre en quarantaine un fichier
- Ajouter un indicateur pour bloquer ou autoriser un fichier

(<a id="fn3">3</a>) Dans Defender pour Entreprises, l’investigation et la réponse automatisées sont activées par défaut, à l’échelle du client. Si vous désactivez l’investigation et la réponse automatisées, cela affecte la protection en temps réel. Consultez [Les paramètres de révision pour les fonctionnalités avancées](mdb-configure-security-settings.md#review-settings-for-advanced-features).  

(<a id="fn4">4</a>) Il n’existe aucune vue de chronologie dans Defender entreprise.

(<a id="fn5">5</a>) Dans Defender entreprise, l’analytique des menaces est optimisée pour les petites et moyennes entreprises.

(<a id="fn6">6</a>) Pendant le programme en préversion, Windows appareils clients sont pris en charge pour l’intégration dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Vous pouvez utiliser la méthode de script local. Consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).

## <a name="next-steps"></a>Prochaines étapes

- [Consultez les conditions requises pour Microsoft Defender pour les PME](mdb-requirements.md)
- [Obtenir Microsoft Defender pour les PME](get-defender-business.md)
- [Découvrez comment configurer et configurer Microsoft Defender pour les PME](mdb-setup-configuration.md)
