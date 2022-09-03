---
title: Comparer les fonctionnalités de sécurité dans les plans Microsoft 365 pour les petites et moyennes entreprises
description: Comment Defender entreprise se compare-t-il à Defender pour point de terminaison et Microsoft 365 Business Premium ? Découvrez ce qui est inclus dans chaque plan afin que vous puissiez prendre une décision plus éclairée pour votre entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/30/2022
ms.reviewer: shlomiakirav
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
f1.keywords: NOCSH
ms.openlocfilehash: 622b1ab33ea2168ee7da050d0ad6a06ff7bf5ba0
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67598150"
---
# <a name="compare-security-features-in-microsoft-365-plans-for-small-and-medium-sized-businesses"></a>Comparer les fonctionnalités de sécurité dans les plans Microsoft 365 pour les petites et moyennes entreprises

Microsoft offre un large éventail de solutions et de services cloud, notamment des plans pour les petites et moyennes entreprises. Par exemple, [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) inclut des fonctionnalités de sécurité et de gestion des appareils, ainsi que des fonctionnalités de productivité telles que les applications Office. Cet article décrit les fonctionnalités de sécurité dans Microsoft 365 Business Premium, Microsoft Defender pour entreprises et [Microsoft Defender pour point de terminaison](../defender-endpoint/microsoft-defender-endpoint.md).


**Utilisez cet article pour** :

- [Comparez Microsoft Defender pour entreprises à Microsoft 365 Business Premium](#compare-microsoft-defender-for-business-to-microsoft-365-business-premium).
- [Comparez Defender entreprise (autonome) aux offres d’entreprise Defender pour point de terminaison](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> [!TIP]
> Defender entreprise est disponible en tant que solution de sécurité autonome pour les petites et moyennes entreprises. Defender entreprise est désormais inclus dans Microsoft 365 Business Premium. Si vous avez déjà Microsoft 365 Business Basic ou Standard, envisagez d’effectuer une mise à niveau vers Microsoft 365 Business Premium ou d’ajouter Defender Entreprise à votre abonnement actuel afin d’obtenir plus de fonctionnalités de protection contre les menaces pour vos appareils.

## <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>Comparer Microsoft Defender pour entreprises à Microsoft 365 Business Premium

> [!NOTE]
> Cet article fournit une vue d’ensemble générale des fonctionnalités et fonctionnalités incluses dans Microsoft Defender pour entreprises (en tant que plan autonome) et Microsoft 365 Business Premium (qui inclut Defender entreprise). Il ne s’agit pas d’une description de service ou d’un document de contrat de licence. Pour plus d’informations, consultez les [instructions relatives aux licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

| Planification | Description |
|:---|:---|
| **[Defender for Business](mdb-overview.md)** (autonome) | **Protection antivirus, anti-programme malveillant et ransomware pour les appareils**<ul><li>[Protection de nouvelle génération (protection](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) antivirus/anti-programme malveillant sur les appareils avec protection cloud)</li><li>[Réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md) (règles de protection réseau, de pare-feu et de réduction de la surface <sup>[d’attaque](#fna)) [a]</sup></li><li>[Détection et réponse](../defender-endpoint/overview-endpoint-detection-response.md) des points de terminaison (détection basée sur le comportement et actions de réponse manuelle)</li><li>[Investigation et réponse automatisées](../defender/m365d-autoir.md) (avec autoréparation pour les menaces détectées)</li><li>[Gestion des vulnérabilités Microsoft Defender](mdb-view-tvm-dashboard.md) (afficher les appareils exposés et les recommandations)</li><li>[Prise en charge multiplateforme pour les appareils](mdb-onboard-devices.md) (Windows, Mac, iOS et Android) <sup>[[b](#fnb)]</sup></li><li>[Gestion et création de rapports centralisées](mdb-get-started.md) (portail Microsoft 365 Defender)</li><li>[API pour l’intégration](../defender-endpoint/management-apis.md) (pour les partenaires Microsoft ou vos outils et applications personnalisés)</li></ul> |
| **[Microsoft 365 Business Premium](../../business-premium/index.md)** | **Fonctionnalités de Defender entreprise, ainsi que des fonctionnalités de productivité et de sécurité supplémentaires**<ul><li>[Microsoft 365 Business Standard](../../admin/admin-overview/what-is-microsoft-365-for-business.md) (applications et services Office et Microsoft Teams)</li><li>[Activation d’ordinateur partagé](/deployoffice/overview-shared-computer-activation) (pour le déploiement de Microsoft 365 Apps)</li><li>[Windows 10/11 Business](../../business-premium/m365bp-upgrade-windows-10-pro.md) (mise à niveau à partir des versions précédentes de Windows Pro)</li><li>[Windows Autopilot](/mem/autopilot/windows-autopilot) (pour la configuration et la configuration des appareils Windows)</li><li>[Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) (anti-hameçonnage, antispam, logiciel anti-programme malveillant et usurpation d’identité pour le courrier électronique)</li><li>[Microsoft Defender pour Office 365 Plan 1](../office-365-security/overview.md) (anti-hameçonnage avancé, détections en temps réel, pièces jointes sécurisées, liens fiables)</li><li>[Extension automatique de l’archivage](../../compliance/autoexpanding-archiving.md) (pour l’e-mail)</li><li>[Azure Active Directory Premium Plan 1](/azure/active-directory/fundamentals/active-directory-whatis) (gestion des identités)</li><li>[Microsoft Intune](/mem/intune/fundamentals/what-is-intune) (intégration et gestion des appareils)</li><li>[Azure Information Protection Premium Plan 1](/azure/information-protection/what-is-information-protection) (protection des informations sensibles)</li><li>[Azure Virtual Desktop](/azure/virtual-desktop/overview) (machines virtuelles gérées de manière centralisée et sécurisées dans le cloud)</li></ul> |

  
<a id="fna">a)</a> Microsoft Intune est nécessaire pour modifier ou personnaliser les règles de réduction de la surface d’attaque. Intune est inclus dans Microsoft 365 Business Premium.

<a id="fnb">b</a>) Microsoft Intune est nécessaire pour intégrer des appareils iOS et Android. Consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).

## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>Comparer Microsoft Defender pour entreprises à Microsoft Defender pour point de terminaison Plans 1 et 2

Defender entreprise apporte les fonctionnalités de niveau entreprise de Defender pour point de terminaison aux petites et moyennes entreprises. Le tableau suivant compare les fonctionnalités et fonctionnalités de sécurité de Defender entreprise aux offres d’entreprise, Microsoft Defender pour point de terminaison Plans 1 et 2.

|Fonctionnalité/fonctionnalité|[Défenseur des affaires](mdb-overview.md)<br/>(autonome)|[Defender pour Endpoint Plan 1](../defender-endpoint/defender-endpoint-plan-1.md)<br/>(pour les clients d’entreprise) |[Defender pour point de terminaison Plan 2](../defender-endpoint/microsoft-defender-endpoint.md)<br/>(pour les clients d’entreprise) |
|---|---|---|---|
|[Gestion centralisée](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | :::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Configuration du client simplifiée](mdb-simplified-configuration.md)|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::| | |
|[Gestion des vulnérabilités Microsoft Defender](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::| |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Fonctionnalités de réduction de la surface d’attaque](../defender-endpoint/overview-attack-surface-reduction.md)|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Protection de nouvelle génération](../defender-endpoint/next-generation-protection.md)|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Détection et réponse](../defender-endpoint/overview-endpoint-detection-response.md) des points de terminaison <sup>[[2](#fn2)]</sup>|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: | |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Investigation et réponse automatisées](../defender-endpoint/automated-investigations.md) <sup>[[3](#fn3)]</sup>|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: ||:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Repérage des menaces](../defender-endpoint/advanced-hunting-overview.md) et six mois de conservation des données <sup>[[4](#fn4)]</sup> | | |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Analyse des menaces](../defender-endpoint/threat-analytics.md) <sup>[[5](#fn5)]</sup>|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: | |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Prise en charge multiplateforme](../defender-endpoint/minimum-requirements.md) <br/>(Système d’exploitation Windows, Mac, iOS et Android) <sup>[[6](#fn6)]</sup>|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[Spécialistes des menaces Microsoft](../defender-endpoint/microsoft-threat-experts.md)| | |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|API partenaires|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included":::|
|[intégration Microsoft 365 Lighthouse](../../lighthouse/m365-lighthouse-overview.md) <br/>(Pour afficher les incidents de sécurité entre les locataires des clients) <sup>[[7](#fn7)]</sup>|:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: |:::image type="content" source="../../media/d238e041-6854-4a78-9141-049224df0795.png" alt-text="Included"::: |

(<a id="fn1">1</a>) Intégrer et gérer des appareils dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ou à l’aide de Microsoft Intune, géré dans le Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

(<a id="fn2">2</a>) Les fonctionnalités de détection et de réponse des points de terminaison (EDR) dans Defender for Business incluent la détection basée sur le comportement et les actions de réponse manuelles suivantes : 
- Exécuter une analyse antivirus
- Isoler l’appareil
- Arrêter et mettre en quarantaine un fichier
- Ajouter un indicateur pour bloquer ou autoriser un fichier

(<a id="fn3">3</a>) Dans Defender pour Entreprises, l’investigation et la réponse automatisées sont activées par défaut, à l’échelle du client. La désactivation de l’investigation et de la réponse automatisées affecte la protection en temps réel. Consultez [Les paramètres de révision pour les fonctionnalités avancées](mdb-configure-security-settings.md#review-settings-for-advanced-features).  

(<a id="fn4">4</a>) Il n’existe aucune vue de chronologie dans Defender entreprise.

(<a id="fn5">5</a>) Dans Defender entreprise, l’analytique des menaces est optimisée pour les petites et moyennes entreprises.

(<a id="fn6">6</a>) Consultez [Intégrer des appareils à Microsoft Defender pour entreprises](mdb-onboard-devices.md).

(<a id="fn7">7</a>) La possibilité d’afficher les incidents entre locataires à l’aide de Defender pour point de terminaison est une nouveauté !

Consultez également [Comparer les plans de sécurité des points de terminaison Microsoft](../defender-endpoint/defender-endpoint-plan-1-2.md).

## <a name="next-steps"></a>Prochaines étapes

- [Consultez la configuration requise pour Microsoft Defender pour entreprises](mdb-requirements.md)
- [Obtenir Microsoft Defender pour entreprises](get-defender-business.md)
- [Découvrez comment configurer et configurer Microsoft Defender pour entreprises](mdb-setup-configuration.md)
