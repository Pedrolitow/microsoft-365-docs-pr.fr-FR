---
title: Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 09/18/2020
audience: ITPro
ms.topic: overview
localization_priority: Normal
ms.assetid: 1270a65f-ddc3-4430-b500-4d3a481efb1e
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment Exchange Online Protection (EOP) peut vous aider à protéger votre organisation de messagerie sur site dans des environnements autonomes et hybrides.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ce90f1429e2c54f413ae54172a6d2f663ef6a358
ms.sourcegitcommit: 686f192e1a650ec805fe8e908b46ca51771ed41f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52624735"
---
# <a name="exchange-online-protection-overview"></a>Vue d’ensemble d’Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) est le service de filtrage informatique qui contribue à protéger votre organisation contre le courrier indésirable, les programmes malveillants et d’autres menaces de courrier électronique. EOP est inclus dans toutes les organisations Microsoft 365 avec Exchange Online boîtes aux lettres.

Le reste de cet article explique comment fonctionne EOP.

> [!NOTE]
> EOP est également disponible seul pour protéger les boîtes aux lettres sur site et dans les environnements hybrides afin de protéger les boîtes aux lettres Exchange sur site. Pour plus d’informations, [voir Exchange Online Protection](/exchange/standalone-eop/standaonline-eop).

## <a name="how-eop-works"></a>Fonctionnement d'EOP

Pour comprendre le fonctionnement d'EOP, il est utile devoir comment le courrier entrant est traité :

:::image type="content" source="../../media/tp_emailprocessingineopt3.png" alt-text="Graphique du courrier électronique provenant d’Internet ou des commentaires des clients passant dans EOP et via la connexion, la protection contre les programmes malveillants, le filtrage des règles de flux de messagerie et la stratégie de contenu, avant le verdict de courrier indésirable ou de mise en quarantaine, ou la remise du courrier de l’utilisateur final.":::

- Lorsqu’un message entrant entre dans EOP, il passe initialement par le filtrage des connexions, qui vérifie la réputation de l’expéditeur. La majorité du courrier indésirable est arrêté à ce stade et rejeté par EOP. Pour plus d’informations, consultez [Configuration du filtrage des connexions](configure-the-connection-filter-policy.md).

- Le message est ensuite inspecté à la recherche de programmes malveillants. Si un programme malveillant est détecté dans le message ou la ou les pièces jointes, le message est acheminé vers une mise en quarantaine de l’administrateur uniquement. Pour en savoir plus sur la protection contre les programmes malveillants, consultez la [protection contre les programmes malveillants dans EOP.](anti-malware-protection.md)

- Les messages continuent par le filtrage des stratégies, où ils sont évalués par rapport aux règles de flux de messagerie personnalisées (également appelées règles de transport) que vous créez ou appliquez à partir d’un modèle. Par exemple, vous pouvez avoir une règle qui envoie une notification à un responsable lorsque le courrier arrive à partir d’un expéditeur spécifique. Les vérifications de protection contre la perte de données (DLP) se produisent également à ce stade (Exchange Enterprise cal avec Services).

- Ensuite, le message passe par le filtrage anti-courrier indésirable dans lequel il recherche le courrier indésirable, le hameçonnage ou le courrier électronique en masse. Les messages détectés peuvent être mis en quarantaine, ou le dossier Courrier indésirable d’un utilisateur, entre autres options. Pour plus d’informations, [voir Configure anti-spam policies](configure-your-spam-filter-policies.md) and [Configure anti-phishing policies](configure-anti-phishing-policies-eop.md).

Tout message qui transmet toutes ces couches de protection est remis au destinataire.

Pour plus d’informations, voir [Ordre et priorité de la protection de la messagerie.](how-policies-and-protections-are-combined.md)

## <a name="eop-plans-and-features-for-on-premises-email-organizations"></a>Plans et fonctionnalités EOP pour les organisations de messagerie locales

Les plans d’abonnement EOP disponibles sont les :

- **EOP autonome :** vous vous inscrivez dans EOP pour protéger votre organisation de messagerie sur site.

- **Fonctionnalités EOP** dans Exchange Online : tout abonnement qui inclut Exchange Online (autonome ou dans le cadre de Microsoft 365) utilise EOP pour protéger vos boîtes aux lettres Exchange Online de messagerie.

- **Exchange Enterprise licence** d’accès avec services : si vous avez une organisation Exchange sur site dans laquelle vous avez acheté une licence d’accès Exchange Enterprise supplémentaire avec licences Services, EOP fait partie des services inclus.

Pour plus d’informations sur les exigences, les limites importantes et la disponibilité des fonctionnalités dans tous les plans d’abonnement EOP, voir la [description Exchange Online Protection service.](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)

> [!NOTE]
> Si vous avez un abonnement Microsoft 365 ou Office 365 qui inclut Exchange Online boîtes aux lettres, vous avez EOP. Pour savoir comment configurer les fonctionnalités de sécurité EOP dans votre abonnement et obtenir des informations sur la sécurité ajoutée qu’un abonnement Microsoft Defender pour Office 365 peut vous fournir, consultez la fonctionnalité de protection contre les [menaces.](protect-against-threats.md) Les paramètres recommandés pour la fonctionnalité EOP pour l’installation se trouvent dans les [paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour Office 365 sécurité.

## <a name="setting-up-eop-for-on-premises-email-organizations"></a>Configuration d’EOP pour les organisations de messagerie locales

La configuration d'EOP peut être simple, en particulier dans le cas d'une organisation de taille modeste appliquant un nombre restreint de règles de conformité. En revanche, si votre organisation est de grande taille, avec plusieurs domaines, des règles de conformité personnalisées ou un flux de messagerie hybride, la configuration peut nécessiter plus de temps et de travail de planification.

Si vous avez déjà acheté EOP, consultez la rubrique [Configurer votre service EOP](/exchange/standalone-eop/set-up-your-eop-service) pour être certain d'accomplir toutes les étapes nécessaires à la configuration d'EOP pour la protection de votre environnement de messagerie.

### <a name="eop-datacenters"></a>Centres de données EOP

EOP s’exécute sur un réseau mondial de centres de données conçus pour offrir une disponibilité optimale. Par exemple, si un centre de données devient indisponible, les courriers électroniques sont automatiquement routés vers un autre centre de données sans interruption du service. Les serveurs de chaque centre de données acceptent des messages en votre nom, ce qui fournit une couche de séparation entre votre organisation et Internet, réduisant ainsi la charge sur vos serveurs. Grâce à ce réseau à haut niveau de disponibilité, Microsoft peut garantir que le courrier atteint votre organisation en temps opportun.

EOP effectue l'équilibrage de charge entre les centres de données, mais uniquement au sein d'une région. Si votre système est mis en service dans une région, tous vos messages seront traités sur la base du routage de courrier propre à cette région. La liste suivante présente le fonctionnement du routage de courrier régional pour les centres de données EOP :

- En Europe, au Moyen-Orient et en Afrique (région EMEA), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données EMEA et tous les messages sont routés via des centres de données EMEA pour le filtrage EOP.
- Dans Asia-Pacific (APAC), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données APAC et les messages sont actuellement acheminés via des centres de données APAC pour le filtrage EOP.
- En Amérique, les services sont distribués aux emplacements suivants :
  - Amérique du Sud : Exchange Online boîtes aux lettres sont situées dans des centres de données au Brésil et au Chili. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
  - Canada : Exchange Online boîtes aux lettres sont situées dans des centres de données au Canada. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
  - États-Unis : Exchange Online boîtes aux lettres sont situées dans des centres de données américains. Tous les messages sont acheminés via des centres de données locaux pour le filtrage EOP. Les messages mis en quarantaine sont stockés dans le centre de données où se trouve le client.
- En ce qui concerne le nuage communautaire propre aux gouvernements (CCG), toutes les boîtes aux lettres Exchange Online sont situées dans des centres de données américains et tous les messages sont routés via ces centres de données pour le filtrage EOP.

## <a name="eop-help-for-admins"></a>Aide EOP pour les administrateurs

Le contenu de l’aide pour les administrateurs d’EOP se compose des catégories de niveau supérieur suivantes :

- [Configurez EOP, jour 1,](protect-against-threats.md)pour microsoft Defender pour les administrateurs Office 365 : configuration des outils de protection et de détection EOP au cœur de Microsoft Defender pour Office 365.

- [Fonctionnalités EOP](eop-features.md): fournit une liste des fonctionnalités disponibles dans EOP.

- [Configurer votre service EOP : fournit](/exchange/standalone-eop/set-up-your-eop-service)les étapes de configuration de votre service EOP et des liens vers des informations supplémentaires.

- Basculez vers EOP à partir de [Google Postini, barracuda Spam and Virus Firewall ou Cisco IronPort](switch-to-eop-from-google-postini-the-barracuda-spam-and-virus-firewall-or-cisco.md): décrit le processus de passage à EOP à partir d’un autre produit de protection de messagerie.

- [Gérer les destinataires dans EOP autonome](/exchange/standalone-eop/manage-recipients-in-eop): décrit comment gérer les utilisateurs et les groupes de messagerie dans EOP autonome.

- Flux de messagerie dans [EOP](mail-flow-in-eop.md): décrit comment configurer des scénarios de flux de messagerie personnalisés à l’aide de connecteurs, comment gérer les domaines associés au service et comment activer la fonctionnalité de blocage du périphérie basé sur l’annuaire (DBEB).

- [Paramètres recommandés](recommended-settings-for-eop-and-office365.md)pour EOP et Microsoft Defender pour la sécurité Office 365 : décrit les paramètres de configuration recommandés et les éléments à prendre en compte après avoir installé et mis en service votre service.

- [Rapports d’audit Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports): décrit comment utiliser les rapports d’audit pour suivre les modifications de configuration apportées au service.

- [Protection contre le](anti-spam-and-anti-malware-protection.md)courrier indésirable et les programmes malveillants dans EOP : décrit le filtrage du courrier indésirable et le filtrage des programmes malveillants et montre comment les personnaliser pour répondre au mieux aux besoins de votre organisation. Décrit également les tâches que les administrateurs et les utilisateurs finaux peuvent effectuer sur les messages en quarantaine.

- [Rapports et suivi des messages dans Exchange Online Protection](reporting-and-message-trace-in-exchange-online-protection.md): décrit les rapports et les outils de dépannage disponibles.

- [Exchange](/exchange/exchange-admin-center) centre d’administration dans le Centre d’administration Exchange Online ou Exchange dans [EOP](/exchange/standalone-eop/exchange-admin-center-eop)autonome : décrit comment accéder à l’interface de gestion du Centre d’administration Exchange (CAE) et y naviguer afin de gérer les fonctionnalités EOP associées.

- [Exchange Online Protection PowerShell](/powershell/exchange/exchange-online-protection-powershell): fournit des informations sur PowerShell à distance, ce qui vous permet de gérer votre service EOP à partir de la ligne de commande.

- [Aide et support pour EOP](help-and-support-for-eop.md) Fournit des informations sur la manière d'obtenir de l'aide et un support technique.