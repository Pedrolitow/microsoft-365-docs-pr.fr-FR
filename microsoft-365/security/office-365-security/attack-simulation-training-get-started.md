---
title: Commencer à utiliser la formation à la simulation d’attaque
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser la formation de simulation d’attaque pour exécuter des attaques par hameçonnage et par mot de passe simulées dans leurs organisations Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 255d0f40cd360f2b4b3e5084f84989bdbe643319
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415615"
---
# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Démarrage à l’aide de l’entraînement de simulation d’attaque dans Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Si votre organisation a Microsoft 365 E5 ou Microsoft Defender pour Office 365 plan 2, qui inclut [des fonctionnalités d’investigation et de réponse aux menaces](office-365-ti.md), vous pouvez utiliser la formation de simulation d’attaque dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes dans votre Organisation. Ces attaques simulées peuvent vous aider à identifier et à trouver des utilisateurs vulnérables avant qu’une attaque réelle n’affecte votre résultat net. Pour en savoir plus, lisez cet article.

Regardez cette courte vidéo pour en savoir plus sur la formation à la simulation d’attaque.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWMhvB]

> [!NOTE]
> L’entraînement de simulation d’attaque remplace l’ancienne expérience de simulateur d’attaque v1 qui était disponible dans le Centre de sécurité & conformité au **simulateur d’attaque** de **gestion des** \> menaces ou <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>. Une formation sur la simulation d’attaque est disponible à l’entraînement de **simulation d’attaque** **par e-mail et de collaboration**\>. Pour accéder directement à l’entraînement de simulation d’attaque, utilisez <https://security.microsoft.com/attacksimulator>.

- Pour plus d’informations sur la disponibilité de l’entraînement de simulation d’attaque dans différents abonnements Microsoft 365, consultez [Microsoft Defender pour Office 365 description du service](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Vous devez disposer d’autorisations dans **Azure Active Directory** avant de pouvoir effectuer les procédures décrites dans cet article. Plus précisément, vous devez être membre de l’un des rôles suivants :
  - **Administrateur général**
  - **Administrateur de sécurité**
  - **Administrateurs de simulation d’attaque**<sup>\*</sup> : créez et gérez tous les aspects des campagnes de simulation d’attaque.
  - Auteur <sup>\*</sup>**de charge utile** d’attaque : créez des charges utiles d’attaque qu’un administrateur peut lancer ultérieurement.

  <sup>\*</sup>L’ajout d’utilisateurs à ce rôle dans le portail Microsoft 365 Defender n’est actuellement pas pris en charge.

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) ou [à propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Il n’existe pas d’applets de commande PowerShell correspondantes pour l’entraînement de simulation d’attaque.

- Les données relatives à la simulation d’attaque et à l’entraînement sont stockées avec d’autres données client pour Microsoft 365 services. Pour plus d’informations, consultez [Microsoft 365 emplacements de données](../../enterprise/o365-data-locations.md). La simulation d’attaque est disponible dans les régions suivantes : NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, BRA, LAM, CHE, NOR, ZAF, ARE et DEU.

  > [!NOTE]
  > NOR, ZAF, ARE et DEU sont les derniers ajouts. Toutes les fonctionnalités, à l’exception des données de télémétrie de messagerie signalées, seront disponibles dans ces régions. Nous nous efforçons d’activer cette fonctionnalité et informerons nos clients dès que les données de télémétrie de messagerie signalées seront disponibles.

- À compter du 15 juin 2021, la formation à la simulation d’attaque est disponible dans Cloud de la communauté du secteur public. Si votre organisation a Office 365 Cloud de la communauté du secteur public G5 ou Microsoft Defender pour Office 365 (Plan 2) pour le gouvernement, vous pouvez utiliser la formation de simulation d’attaque dans le Microsoft 365 Defender  pour exécuter des scénarios d’attaque réalistes dans votre organisation, comme décrit dans cet article. L’entraînement de simulation d’attaque n’est pas encore disponible dans Cloud de la communauté du secteur public environnements High ou DoD.

> [!NOTE]
> L’entraînement de simulation d’attaque offre un sous-ensemble de fonctionnalités aux clients E3 en tant qu’essai. L’offre d’essai offre la possibilité d’utiliser une charge utile de collecte des informations d’identification et la possibilité de sélectionner des expériences de formation « Hameçonnage ISA » ou « Hameçonnage sur le marché de masse ». Aucune autre fonctionnalité ne fait partie de l’offre d’essai E3.

## <a name="simulations"></a>Simulations

Le *Hameçonnage* est un terme générique qui décrit les attaques par courrier électronique tentant d’accéder à des informations sensibles par le biais de messages qui paraissent provenir d’expéditeurs légitimes ou approuvés. *L’hameçonnage* fait partie d’un sous-ensemble de techniques que nous classons en tant _qu’ingénierie sociale_.

Dans la formation à la simulation d’attaque, plusieurs types de techniques d’ingénierie sociale sont disponibles :

- **Collecte des informations d’identification** : un attaquant envoie au destinataire un message contenant une URL. Lorsque le destinataire clique sur l’URL, il est redispilé vers un site web qui affiche généralement une boîte de dialogue qui demande à l’utilisateur son nom d’utilisateur et son mot de passe. En règle générale, la page de destination est thématique pour représenter un site web connu afin de créer une confiance dans l’utilisateur.

- **Pièce jointe à un programme malveillant** : un attaquant envoie au destinataire un message contenant une pièce jointe. Lorsque le destinataire ouvre la pièce jointe, du code arbitraire (par exemple, une macro) est exécuté sur l’appareil de l’utilisateur pour aider l’attaquant à installer du code supplémentaire ou à s’ancrer davantage.

- **Lien dans la pièce jointe** : il s’agit d’un hybride d’une collecte d’informations d’identification. Un attaquant envoie au destinataire un message qui contient une URL à l’intérieur d’une pièce jointe. Lorsque le destinataire ouvre la pièce jointe et clique sur l’URL, il accède à un site web qui affiche généralement une boîte de dialogue qui demande à l’utilisateur son nom d’utilisateur et son mot de passe. En règle générale, la page de destination est thématique pour représenter un site web connu afin de créer une confiance dans l’utilisateur.

- **Lien vers un programme malveillant** : un attaquant envoie au destinataire un message contenant un lien vers une pièce jointe sur un site de partage de fichiers connu (par exemple, SharePoint Online ou Dropbox). Lorsque le destinataire clique sur l’URL, la pièce jointe s’ouvre et le code arbitraire (par exemple, une macro) est exécuté sur l’appareil de l’utilisateur pour aider l’attaquant à installer du code supplémentaire ou à s’ancrer davantage.

- **Lecteur par URL** : un attaquant envoie au destinataire un message qui contient une URL. Lorsque le destinataire clique sur l’URL, il est dirigé vers un site web qui tente d’exécuter du code d’arrière-plan. Ce code d’arrière-plan tente de recueillir des informations sur le destinataire ou de déployer du code arbitraire sur son appareil. En règle générale, le site web de destination est un site web connu qui a été compromis ou un clone d’un site web connu. La connaissance du site web permet de convaincre l’utilisateur que le lien est sûr de cliquer. Cette technique est également connue sous le nom _d’attaque de trou d’eau_.

> [!NOTE]
> Vérifiez la disponibilité de l’URL de hameçonnage simulée dans vos navigateurs web pris en charge avant d’utiliser l’URL dans une campagne de hameçonnage. Bien que nous travaillions avec de nombreux fournisseurs de réputation d’URL pour toujours autoriser ces URL de simulation, nous n’avons pas toujours une couverture complète (par exemple, Google Coffre Navigation). La plupart des fournisseurs fournissent des conseils qui vous permettent d’autoriser toujours des URL spécifiques (par exemple, <https://support.google.com/chrome/a/answer/7532419>).

Les URL utilisées par l’entraînement de simulation d’attaque sont décrites dans la liste suivante :

- <https://www.mcsharepoint.com>
- <https://www.attemplate.com>
- <https://www.doctricant.com>
- <https://www.mesharepoint.com>
- <https://www.officence.com>
- <https://www.officenced.com>
- <https://www.officences.com>
- <https://www.officentry.com>
- <https://www.officested.com>
- <https://www.prizegives.com>
- <https://www.prizemons.com>
- <https://www.prizewel.com>
- <https://www.prizewings.com>
- <https://www.shareholds.com>
- <https://www.sharepointen.com>
- <https://www.sharepointin.com>
- <https://www.sharepointle.com>
- <https://www.sharesbyte.com>
- <https://www.sharession.com>
- <https://www.sharestion.com>
- <https://www.templateau.com>
- <https://www.templatent.com>
- <https://www.templatern.com>
- <https://www.windocyte.com>

### <a name="create-a-simulation"></a>Créer une simulation

Pour obtenir des instructions pas à pas sur la création et l’envoi d’une simulation, consultez [Simuler une attaque par hameçonnage](attack-simulation-training.md).

### <a name="create-a-payload"></a>Créer une charge utile

Pour obtenir des instructions pas à pas sur la création d’une charge utile à utiliser dans une simulation, consultez [Créer une charge utile personnalisée pour l’entraînement de simulation d’attaque](attack-simulation-training-payloads.md).

### <a name="gaining-insights"></a>Obtenir des insights

Pour obtenir des instructions pas à pas sur la façon d’obtenir des insights avec la création de rapports, consultez [Obtenir des insights via l’entraînement de simulation d’attaque](attack-simulation-training-insights.md).

> [!NOTE]
> Le simulateur d’attaques utilise Coffre Liens dans Defender pour Office 365 pour suivre en toute sécurité les données de clic de l’URL dans le message de charge utile envoyé aux destinataires ciblés d’une campagne de hameçonnage, même si le paramètre **Suivre les clics de l’utilisateur** dans Coffre Stratégies liens est désactivé.
