---
title: Flux de messagerie dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: L’administrateur peut en savoir plus sur les options de configuration du flux de messagerie et du routage dans Exchange Online Protection (EOP).
ms.openlocfilehash: cb2ae7370d50fe32802ad5c279cc2170eb35f581
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208329"
---
# <a name="mail-flow-in-eop"></a>Flux de messagerie dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online ou des organisations Exchange Online (EOP) autonomes sans boîtes aux lettres Exchange Online, tous les messages envoyés à votre organisation passent par EOP avant que les utilisateurs ne les voient. Vous disposez d’options sur la façon de router les messages qui transitent par EOP pour les traiter avant de les acheminer vers vos boîtes de réception.

## <a name="working-with-messages-and-message-access-options"></a>Utilisation des messages et des options d’accès aux messages

EOP offre une grande flexibilité dans le mode d’acheminement de vos messages. Les rubriques suivantes expliquent les étapes composant le processus de flux de messages.

[Utiliser le blocage du périmètre basé sur l’annuaire pour rejeter les messages envoyés à des destinataires non valides](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) Décrit la fonctionnalité de blocage du périmètre basée sur l’annuaire, qui vous permet de rejeter les messages pour les destinataires non valides au niveau du périmètre réseau du service.

La rubrique [View or Edit Managed Domains in EOP](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) décrit la façon de gérer les domaines associés à votre service EOP.

Si vous ajoutez des sous-domaines dans votre organisation, votre service EOP peut vous aider à les gérer aussi. Pour en savoir plus sur les sous-domaines, consultez la rubrique [Enable mail Flow for subdomains in Exchange Online](https://docs.microsoft.com/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[Configurer le flux de messagerie à l’aide de connecteurs](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) présente les connecteurs et explique comment vous pouvez les utiliser pour personnaliser le routage du courrier. Les scénarios décrivent la procédure pour assurer une communication sécurisée avec une organisation partenaire et configurer un hôte actif.

[Enhanced Filtering for Connectors](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) indique comment configurer des connecteurs si votre courrier est acheminé vers un service ou un périphérique avant EOP.

Dans les organisations EOP autonomes, vous devez effectuer quelques opérations de configuration pour vous assurer que le courrier indésirable est correctement routé vers le dossier de courrier indésirable de chaque utilisateur. Ces éléments sont détaillés dans [la configuration d’EOP autonome pour la remise du courrier indésirable dans le dossier courrier indésirable dans des environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md). Si vous ne souhaitez pas déplacer les messages vers le dossier de courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en modifiant vos stratégies de blocage du courrier indésirable (également appelées stratégies de filtrage de contenu). Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>Vérifier le flux de messagerie

Pour vérifier que votre configuration d'EOP, y compris celle de votre connecteur, fonctionne correctement, consultez la section « Comment savoir si cette tâche a fonctionné ? » dans la rubrique [Configurer votre service EOP](set-up-your-eop-service.md).

[Test du flux de messagerie en validant vos connecteurs Microsoft 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow) fournit des instructions pour vérifier que votre flux de messagerie est correctement configuré.
