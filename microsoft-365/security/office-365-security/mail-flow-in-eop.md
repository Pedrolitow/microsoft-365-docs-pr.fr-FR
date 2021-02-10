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
localization_priority: Normal
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: L’administrateur peut en savoir plus sur les options de configuration du flux de messagerie et du routage dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cd07c4448d9b30c90c97c7bc89c787b2fdc08cdd
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50167238"
---
# <a name="mail-flow-in-eop"></a>Flux de courriers dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](https://go.microsoft.com/fwlink/?linkid=2148611)
- [Microsoft Defender pour Office 365 plan 1 et plan 2](https://go.microsoft.com/fwlink/?linkid=2148715)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Dans les organisations Microsoft 365 avec boîtes aux lettres Exchange Online ou les organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, tous les messages envoyés à votre organisation passent par EOP avant que vos employés les voient. Vous avez des options pour router les messages qui passent par EOP pour traitement avant qu’ils ne soient acheminés vers vos boîtes de réception de travail.

## <a name="working-with-messages-and-message-access-options"></a>Utilisation des messages et des options d’accès aux messages

EOP offre une flexibilité dans la façon dont vos messages sont acheminés. Les rubriques suivantes expliquent les étapes composant le processus de flux de messages.

[Utiliser le blocage du service Edge basé sur l’annuaire pour rejeter les messages envoyés à des destinataires non valides](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Décrit la fonctionnalité de blocage du périmètre basé sur l’annuaire qui vous permet de rejeter les messages pour les destinataires non valides au niveau du périmètre du réseau de service.

La rubrique [View or Edit Managed Domains in EOP](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) décrit la façon de gérer les domaines associés à votre service EOP.

Si vous ajoutez des sous-domaines dans votre organisation, votre service EOP peut vous aider à les gérer aussi. En savoir plus sur les sous-domaine dans l’outil Activer le flux de messagerie pour les [sous-domaine dans Exchange Online.](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains)

[Configure mail flow using connectors](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) introduces connectors and shows how you can use them to customize mail routing. Les scénarios décrivent la procédure pour assurer une communication sécurisée avec une organisation partenaire et configurer un hôte actif.

[Le filtrage amélioré pour les connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) décrit comment configurer des connecteurs si votre courrier est acheminé vers un service ou un périphérique avant EOP.

Dans les organisations EOP autonomes, vous devez effectuer quelques étapes de configuration pour vous assurer que le courrier indésirable est correctement acheminé vers le dossier courrier indésirable de chaque utilisateur. Ceux-ci sont détaillés dans Configurer EOP autonome pour remettre le courrier indésirable dans le dossier Courrier indésirable dans les [environnements hybrides.](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md) Si vous ne souhaitez pas déplacer des messages vers le dossier courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en éditant vos stratégies anti-courrier indésirable (également appelées stratégies de filtrage de contenu). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Vérifier le flux de messagerie

Pour vérifier que votre configuration d'EOP, y compris celle de votre connecteur, fonctionne correctement, consultez la section « Comment savoir si cette tâche a fonctionné ? » dans la rubrique [Configurer votre service EOP](set-up-your-eop-service.md).

[Tester le flux de messagerie en validant vos connecteurs Microsoft 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow) fournit des instructions pour tester que votre flux de messagerie est correctement installé.
