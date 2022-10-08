---
title: Flux de courriers dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: Administration pouvez en savoir plus sur les options de configuration du flux de messagerie et du routage dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.collection: m365-security
search.appverid: met150
ms.openlocfilehash: e95a0afe2cafdcf26c1adf51fb96922eba7250ff
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091936"
---
# <a name="mail-flow-in-eop"></a>Flux de courriers dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, tous les messages envoyés à votre organisation passent par EOP avant que les utilisateurs ne les voient. Vous avez des options sur la façon de router les messages qui passent par EOP pour le traitement avant qu’ils ne soient routées vers des boîtes aux lettres utilisateur.

## <a name="working-with-messages-and-message-access-options"></a>Utilisation des messages et des options d’accès aux messages

EOP offre une flexibilité dans la façon dont vos messages sont routées. Les rubriques suivantes expliquent les étapes composant le processus de flux de messages.

[Utiliser le blocage edge basé sur l’annuaire pour rejeter les messages envoyés à des destinataires non valides](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Décrit la fonctionnalité de blocage de périphérie basée sur l’annuaire qui vous permet de rejeter les messages pour les destinataires non valides au niveau du périmètre du réseau de service.

[Afficher ou modifier des domaines acceptés dans EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) décrit comment gérer les domaines associés à votre service EOP.

Si vous ajoutez des sous-domaines dans votre organisation, votre service EOP peut vous aider à les gérer aussi. Pour en savoir plus sur les sous-domaines, consultez [Activer le flux de courrier pour les sous-domaines dans Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[La configuration du flux de messagerie à l’aide de connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) présente les connecteurs et montre comment les utiliser pour personnaliser le routage du courrier. Les scénarios décrivent la procédure pour assurer une communication sécurisée avec une organisation partenaire et configurer un hôte actif.

[Le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) décrit comment configurer des connecteurs si votre courrier est routée vers un service ou un appareil avant EOP.

Dans les environnements hybrides où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de messagerie (également appelées règles de transport) dans Exchange local. Ces règles de flux de courrier traduisent le verdict de filtrage du courrier indésirable EOP afin que la règle de courrier indésirable dans la boîte aux lettres puisse déplacer le message vers le dossier Courrier indésirable Email. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). Si vous ne souhaitez pas déplacer de messages vers le dossier Junk Email de chaque utilisateur, vous pouvez choisir une autre action en modifiant vos stratégies anti-courrier indésirable (également appelées stratégies de filtre de contenu). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Vérifier le flux de messagerie

To verify that your EOP setup, including your connector configuration, is working correctly, see the "How do you know this task worked?" section in [Set up your EOP service](/exchange/standalone-eop/set-up-your-eop-service).

[Tester le flux de messagerie en validant vos connecteurs Microsoft 365](/exchange/mail-flow-best-practices/test-mail-flow) fournit des instructions pour tester que votre flux de messagerie est correctement configuré.
