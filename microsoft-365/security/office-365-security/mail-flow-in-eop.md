---
title: Flux de messagerie dans EOP
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
description: L’administrateur peut en savoir plus sur les options de configuration du flux de messagerie et du routage dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 56d6d29d92b97f1a85718d9b77c9e0a41c87b9f8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197880"
---
# <a name="mail-flow-in-eop"></a>Flux de courriers dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, tous les messages envoyés à votre organisation passent par EOP avant que vos employés ne les voient. Vous avez des options pour router les messages qui passent par EOP pour traitement avant qu’ils ne soient acheminés vers vos boîtes de réception de travail.

## <a name="working-with-messages-and-message-access-options"></a>Utilisation des messages et des options d’accès aux messages

EOP offre une flexibilité dans la façon dont vos messages sont acheminés. Les rubriques suivantes expliquent les étapes composant le processus de flux de messages.

[Utiliser le blocage du service Edge basé sur l’annuaire pour rejeter les messages envoyés à des destinataires non valides](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Décrit la fonctionnalité de blocage du périmètre basé sur l’annuaire qui vous permet de rejeter les messages pour les destinataires non valides au niveau du périmètre du réseau de service.

[L’affichage ou](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) la modification de domaines acceptés dans EOP décrit comment gérer les domaines associés à votre service EOP.

Si vous ajoutez des sous-domaines dans votre organisation, votre service EOP peut vous aider à les gérer aussi. En savoir plus sur les sous-domaine dans [l’adresse Enable mail flow for subdomains in Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Configure mail flow using connectors](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) introduces connectors and shows how you can use them to customize mail routing. Les scénarios décrivent la procédure pour assurer une communication sécurisée avec une organisation partenaire et configurer un hôte actif.

[Le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) décrit comment configurer des connecteurs si votre courrier est acheminé vers un service ou un périphérique avant EOP.

Dans les environnements hybrides où Exchange Online Protection protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local pour traduire le verdict de filtrage de courrier indésirable Exchange Online Protection de sorte que la règle de courrier indésirable puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). Si vous ne souhaitez pas déplacer des messages vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en éditant vos stratégies anti-courrier indésirable (également appelées stratégies de filtrage de contenu). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Vérifier le flux de messagerie

Pour vérifier que votre configuration d'EOP, y compris celle de votre connecteur, fonctionne correctement, consultez la section « Comment savoir si cette tâche a fonctionné ? » dans la rubrique [Configurer votre service EOP](/exchange/standalone-eop/set-up-your-eop-service).

[Testez le flux de messagerie en validant Microsoft 365 connecteurs](/exchange/mail-flow-best-practices/test-mail-flow) de messagerie fournit des instructions pour tester que votre flux de messagerie est correctement installé.
