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
ms.assetid: null
ms.collection:
  - M365-security-compliance
  - m365initiative-m365-defender
ms.custom:
  - seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser la formation sur la simulation d’attaques pour exécuter des attaques par hameçonnage simulé et par mot de passe dans leurs organisations Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.prod: m365-security
---

# <a name="get-started-using-attack-simulation-training-in-defender-for-office-365"></a>Commencer à utiliser la formation sur la simulation d’attaques dans Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Si votre organisation Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, qui inclut des fonctionnalités d’investigation et de réponse aux menaces[, vous](office-365-ti.md) pouvez utiliser une formation sur la simulation d’attaques dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes dans votre organisation. Ces attaques simulées peuvent vous aider à identifier et à trouver des utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre ligne de bas de page. Pour en savoir plus, lisez cet article.

> [!NOTE]
> La formation à la simulation d’attaque remplace l’ancienne expérience du Simulateur d’attaques v1 qui  \> était disponible dans le Centre de sécurité & conformité au simulateur d’attaques de gestion **des menaces** ou <https://protection.office.com/attacksimulator>.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>. Une formation sur la simulation d’attaques est disponible dans **la formation sur la simulation** d’attaques de messagerie **électronique et de collaboration**\>. Pour passer directement à la formation sur la simulation d’attaques, utilisez <https://security.microsoft.com/attacksimulator>.

- Pour plus d’informations sur la disponibilité de la formation sur la simulation d’attaques dans différents abonnements Microsoft 365, voir [Microsoft Defender pour obtenir la description Office 365 service](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

- Des autorisations doivent vous être attribuées **Azure Active Directory** avant de pouvoir suivre les procédures de cet article. Plus précisément, vous devez être membre de l’un des rôles suivants :
  - **Administrateur général**
  - **Administrateur de la sécurité**
  - **Administrateurs de simulation d’attaque :**<sup>\*</sup> créez et gérez tous les aspects des campagnes de simulation d’attaques.
  - **Auteur de la charge utile d’attaque**<sup>\*</sup> : créez des charges utiles d’attaque qu’un administrateur peut lancer ultérieurement.

  <sup>\*</sup>L’ajout d’utilisateurs à ce rôle dans Microsoft 365 Defender portail n’est actuellement pas pris en compte.

  Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender ou](permissions-microsoft-365-security-center.md) [à propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Il n’existe aucune cmdlet PowerShell correspondante pour la formation à la simulation d’attaques.

- Les données associées à la simulation d’attaque et à la formation sont stockées avec d’autres données client pour Microsoft 365 services. Pour plus d’informations, [Microsoft 365 emplacements de données.](../../enterprise/o365-data-locations.md) La simulation d’attaque est disponible dans les régions suivantes : NAM, APC, EUR, IND, CAN, AUS, FRA, GBR, JPN, KOR, LAM, CHE, NOR, ZAF, ARE et DEU.

  > [!NOTE]
  > NOR, ZAF, ARE et DEU sont les derniers ajouts. Toutes les fonctionnalités, à l’exception de la télémétrie de courrier signalé, seront disponibles dans ces régions. Nous travaillons à l’activer et avertirons nos clients dès que la télémétrie de courrier électronique signalée sera disponible.

- Depuis le 15 juin 2021, la formation sur la simulation d’attaques est disponible Cloud de la communauté du secteur public. Si votre organisation Office 365 Cloud de la communauté du secteur public G5 ou Microsoft Defender pour Office 365 (Plan 2) pour le gouvernement, vous pouvez utiliser une formation sur la simulation d’attaques dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes dans votre organisation, comme décrit dans cet article. La formation à la simulation d’attaques n’est pas encore disponible Cloud de la communauté du secteur public environnements Élevé ou DoD.

> [!NOTE]
> La formation à la simulation d’attaques offre un sous-ensemble de fonctionnalités aux clients E3 en tant qu’essai. L’offre d’évaluation offre la possibilité d’utiliser une charge utile de la campagne de données d’identification et la possibilité de sélectionner des expériences de formation « ISA Phishing » ou « Hameçonnage de marché de masse ». Aucune autre fonctionnalité ne fait partie de l’offre d’essai E3.

## <a name="simulations"></a>Simulations

Le *Hameçonnage* est un terme générique qui décrit les attaques par courrier électronique tentant d’accéder à des informations sensibles par le biais de messages qui paraissent provenir d’expéditeurs légitimes ou approuvés. *Le hameçonnage* fait partie d’un sous-ensemble de techniques que nous classons en _tant qu’ingénierie sociale_.

Dans la formation à la simulation d’attaques, plusieurs types de techniques d’ingénierie sociale sont disponibles :

- **Informations d’identification** : une personne malveillante envoie au destinataire un message contenant une URL. Lorsque le destinataire clique sur l’URL, il est redéliqué sur un site web qui affiche généralement une boîte de dialogue qui demande à l’utilisateur son nom d’utilisateur et son mot de passe. En règle générale, la page de destination est un site web connu pour créer une relation d’confiance avec l’utilisateur.

- **Pièce jointe malveillante** : une personne malveillante envoie au destinataire un message contenant une pièce jointe. Lorsque le destinataire ouvre la pièce jointe, du code arbitraire (par exemple, une macro) est exécuté sur l’appareil de l’utilisateur pour permettre à l’attaquant d’installer du code supplémentaire ou de s’en empêcher.

- **Lien dans la pièce** jointe : il s’agit d’un hybride de la saisie des informations d’identification. Une personne malveillante envoie au destinataire un message contenant une URL à l’intérieur d’une pièce jointe. Lorsque le destinataire ouvre la pièce jointe et clique sur l’URL, il est redéliqué sur un site web qui affiche généralement une boîte de dialogue qui demande à l’utilisateur son nom d’utilisateur et son mot de passe. En règle générale, la page de destination est un site web connu pour créer une relation d’confiance avec l’utilisateur.

- **Lien vers** un programme malveillant : une personne malveillante envoie au destinataire un message contenant un lien vers une pièce jointe sur un site de partage de fichiers connu (par exemple, SharePoint Online ou Dropbox). Lorsque le destinataire clique sur l’URL, la pièce jointe s’ouvre et un code arbitraire (par exemple, une macro) est exécuté sur l’appareil de l’utilisateur pour aider l’attaquant à installer du code supplémentaire ou à s’en aller.

- **Lecteur par URL** : une personne malveillante envoie au destinataire un message contenant une URL. Lorsque le destinataire clique sur l’URL, il est dirigé vers un site web qui tente d’exécuter du code d’arrière-plan. Ce code en arrière-plan tente de collecter des informations sur le destinataire ou de déployer du code arbitraire sur son appareil. En règle générale, le site web de destination est un site web connu compromis ou un clone d’un site web connu. La connaissance du site web permet de convaincre l’utilisateur que le lien peut être cliqué en toute sécurité. Cette technique est également connue sous le nom d’attaque par trous _d’eau_.

> [!NOTE]
> Vérifiez la disponibilité de l’URL de hameçonnage simulé dans vos navigateurs web pris en charge avant d’utiliser l’URL dans une campagne de hameçonnage. Bien que nous travaillions avec de nombreux fournisseurs de réputation d’URL pour toujours autoriser ces URL de simulation, nous n’avons pas toujours une couverture complète (par exemple, Google Coffre Navigation). La plupart des fournisseurs fournissent des conseils qui vous permettent de toujours autoriser des URL spécifiques (par exemple, <https://support.google.com/chrome/a/answer/7532419>).

Les URL utilisées par la formation à la simulation d’attaque sont décrites dans la liste suivante :

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

Pour obtenir des instructions détaillées sur la création et l’envoi d’une nouvelle simulation, voir [Simulation d’une attaque par hameçonnage](attack-simulation-training.md).

### <a name="create-a-payload"></a>Créer une charge utile

Pour obtenir des instructions détaillées sur la création d’une charge utile à utiliser dans une simulation, voir Créer une charge utile personnalisée pour la formation à la [simulation d’attaques](attack-simulation-training-payloads.md).

### <a name="gaining-insights"></a>Obtenir des informations

Pour obtenir des instructions détaillées sur la façon d’obtenir des informations sur les rapports, voir Obtenir des informations [par le biais d’une formation sur la simulation d’attaques](attack-simulation-training-insights.md).

> [!NOTE]
> Le Simulateur d’attaques utilise des liens Coffre dans Defender pour Office 365 pour suivre en toute sécurité les données de clic pour l’URL du message de charge utile envoyé aux destinataires ciblés d’une campagne de hameçonnage, même si le paramètre Ne pas suivre les clics de l’utilisateur dans les **stratégies** de liens Coffre est allumé.
