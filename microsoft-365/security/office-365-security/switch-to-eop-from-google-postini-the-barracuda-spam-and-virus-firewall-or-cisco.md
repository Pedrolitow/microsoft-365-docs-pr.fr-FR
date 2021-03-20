---
title: Basculer vers EOP à partir d’un autre service de protection
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 81b75194-3b04-48da-8b81-951afbabedde
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez apprendre à passer à Exchange Online Protection (EOP) à partir d’un équipement d’hygiène de messagerie local ou d’un service de protection en nuage.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a09b64d45d79c81ed95981c20bf75dcb43366d07
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50916477"
---
# <a name="switch-to-eop-from-google-postini-the-barracuda-spam-and-virus-firewall-or-cisco-ironport"></a>Basculer vers EOP depuis Google Postini, Barracuda Spam and Virus Firewall, ou Cisco IronPort

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

 Le but de cette rubrique est de vous aider à comprendre le processus de passage d'un équipement de protection de messagerie électronique local ou d'un service de protection dans le nuage à Exchange Online Protection (EOP), puis de vous fournir les ressources d'aide nécessaires pour commencer à l'utiliser. Il existe de nombreuses solutions de filtrage du courrier indésirable, mais le processus de passage à EOP est généralement similaire.

Si vous débutez avec EOP et que vous souhaitez lire une vue d’ensemble de ses fonctionnalités avant de décider de basculer, commencez par la rubrique vue d’ensemble [d’Exchange Online Protection.](exchange-online-protection-overview.md)

Avant de passer à EOP, il est important que vous déterminiez si vous voulez héberger vos boîtes aux lettres protégées par EOP dans le nuage avec Exchange Online, localement ou dans un scénario hybride (hybride signifie que certaines boîtes aux lettres sont hébergées localement, et d'autres avec Exchange Online). Chacun de ces scénarios d'hébergement (en nuage, local et hybride) est possible, mais les étapes de configuration peuvent varier. Voici quelques considérations pour vous aider à choisir le déploiement approprié :

- Protection EOP avec boîtes aux lettres **locales**: ce scénario est approprié si vous avez une infrastructure d’hébergement de messagerie existante que vous souhaitez utiliser, ou si vous avez des exigences professionnelles pour conserver des boîtes aux lettres locales et que vous souhaitez utiliser EOP comme protection de messagerie en nuage. Pour plus d'informations sur ce scénario, consultez la rubrique [Passage à EOP autonome](#switch-to-eop-standalone).

- **Protection EOP avec boîtes aux** lettres Exchange Online : ce scénario est approprié si vous souhaitez une protection EOP et toutes vos boîtes aux lettres hébergées dans le cloud. Il peut s'avérer plus simple, car il ne nécessite pas le maintien de serveurs de messagerie locaux. La rubrique [Passage à Exchange Online](#switch-to-exchange-online) décrit ce scénario.

- **Protection EOP avec boîtes** aux lettres hybrides : vous souhaitez peut-être des boîtes aux lettres cloud, mais vous devez conserver des boîtes aux lettres pour certains utilisateurs en local. Ce scénario est approprié si vous voulez conserver certaines boîtes aux lettres localement, et héberger les autres avec Exchange Online. [Passage à une solution hybride](#switch-to-a-hybrid-solution) décrit ce scénario.

## <a name="switch-to-eop-standalone"></a>Passage à EOP autonome

Si vous hébergez actuellement vos boîtes aux lettres localement et utilisez un équipement de protection local ou un service de protection de messagerie dans le nuage, vous pouvez passer à EOP pour bénéficier de ses fonctionnalités de protection et sa disponibilité. Pour configurer EOP dans un scénario autonome, c'est-à-dire consistant à héberger vos boîtes aux lettres localement et à utiliser EOP pour assurer la protection du courrier électronique, vous pouvez procéder de la manière décrite dans la rubrique [Configurer votre service EOP](set-up-your-eop-service.md). Cette rubrique décrit les étapes de configuration de la protection EOP, qui incluent l'inscription, l'ajout de votre domaine et la configuration de votre flux de messagerie avec des connecteurs.

## <a name="switch-to-exchange-online"></a>Passage à Exchange Online

Vous disposez peut-être de boîtes aux lettres sur site protégées par une appliance sur site et vous souhaitez passer à des boîtes aux lettres Exchange Online hébergées dans le cloud et à la protection EOP pour tirer parti des fonctionnalités de protection et de messagerie cloud de Microsoft 365. Pour commencer, vous pouvez vous inscrire à Microsoft 365 et ajouter votre domaine. Ce scénario ne nécessite pas la mise en place de connecteurs, car il n’existe aucun routage vers les boîtes aux lettres sur site. Commencez par obtenir les dernières fonctionnalités avancées [de Microsoft 365](https://www.microsoft.com/microsoft-365/business/compare-more-office-365-for-business-plans) pour vous inscrire et vous familiariser avec ses fonctionnalités.

Pendant le processus d’installation de Microsoft 365, vous allez créer vos utilisateurs de boîte aux lettres en nuage.

## <a name="switch-to-a-hybrid-solution"></a>Passage à une solution hybride

Il se peut que vous vouliez déplacer uniquement une partie de vos boîtes aux lettres vers le nuage en raison d'exigences propres à votre organisation ou de considérations réglementaires. Lorsque vous déployez un scénario hybride, vous pouvez déplacer des boîtes aux lettres vers le nuage conformément aux exigences de votre organisation. Une migration vers un environnement hybride avec protection EOP est plus compliquée qu'un scénario de déplacement complet dans le nuage. Toutefois, Microsoft offre une prise en charge complète du scénario hybride et de nombreuses ressources pour faciliter le déplacement hybride.

Le meilleur endroit pour commencer, si vous envisagez un déploiement hybride, est [Exchange Server déploiements hybrides.](/exchange/exchange-hybrid) En outre, il est important de comprendre différentes façons d’router le courrier électronique dans un scénario hybride. [Le routage de transport dans les déploiements hybrides Exchange](/exchange/transport-routing) explique chaque type, afin que vous pouvez choisir le meilleur scénario de routage, en fonction des besoins de votre entreprise.

## <a name="migration-planning"></a>Planification de la migration

Si vous décidez de passer à EOP, soyez particulièrement attentif aux aspects suivants :

- Règles de filtrage personnalisées : si vous avez des règles de filtrage ou de stratégie d’entreprise personnalisées pour capturer des courriers indésirables spécifiques, nous vous recommandons d’essayer EOP avec les paramètres par défaut pendant un certain temps avant de migrer vos règles. EOP offre une protection contre le courrier indésirable au niveau de l’entreprise avec les paramètres par défaut. Il se peut que vous n’avez pas besoin de migrer certaines de vos règles vers EOP. Bien entendu, si vous avez mis en place des règles qui appliquent des stratégies d’entreprise personnalisées spécifiques, vous pouvez les créer. [Les règles de flux de messagerie (règles de transport)](mail-flow-rules-transport-rules-0.md) dans Exchange Online Protection fournissent des instructions détaillées pour la création de règles de flux de messagerie dans EOP.

- **Listes** d’adresses IP et listes d’adresses IP bloqués : si vous avez des listes d’adresses ip et des listes d’adresses IP bloqués par utilisateur, laissez le temps de copier les listes dans EOP dans le cadre de votre processus de configuration. Pour plus d’informations sur la liste d’adresses IP permises et la liste d’adresses IP bloqués, voir [Configurer la stratégie de filtrage des connexions.](configure-the-connection-filter-policy.md)

- **Communication sécurisée**: si vous avez un partenaire qui nécessite une messagerie chiffrée, nous vous recommandons de le configurer dans le Centre d’administration Exchange. Pour configurer ce scénario, voir Configurer des connecteurs pour un flux [de messagerie sécurisé avec une organisation partenaire.](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

> [!TIP]
> Lorsque vous passez d'un équipement local à EOP, vous pouvez conserver votre équipement ou un serveur pour effectuer les contrôles de règle d'entreprise. Par exemple, si votre appliance effectue un filtrage personnalisé sur le courrier sortant et que vous souhaitez qu’elle continue de le faire, vous pouvez configurer EOP pour qu’il envoie des messages directement à l’appliance pour un filtrage supplémentaire, avant qu’il ne soit acheminé vers Internet.