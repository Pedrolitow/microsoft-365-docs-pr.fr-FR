---
title: Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2019
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 989ba10c-f73f-4efb-ad1b-af3322e5f376
ms.collection:
- M365-security-compliance
description: Outre le Centre de gestion de la confidentialité Office 365 qui fournit des informations sur la sécurité, la confidentialité et la conformité pour Microsoft 365, vous voudrez peut-être savoir comment Microsoft contribue à protéger les secrets que vous stockez dans ses centres de données. Nous utilisons une technologie appelée Gestionnaire de clés distribuées (DKM).
ms.openlocfilehash: 2f6e51b7fe9cd75cbd265c3135050a08130f34d8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50906960"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online

Cet article décrit la façon dont Microsoft protège les informations confidentielles figurant dans vos courriers électroniques dans ses centres de données.
  
## <a name="how-do-we-secure-secret-information-provided-by-you"></a>Comment sécurisons-nous les informations confidentielles que vous indiquez ?

Outre le Centre de gestion de la confidentialité Office 365 qui fournit des informations sur la sécurité, la confidentialité et la conformité pour [Office 365,](./get-started-with-service-trust-portal.md)vous souhaitez peut-être savoir comment Microsoft contribue à protéger les secrets que vous fournissez dans ses centres de données. Nous utilisons une technologie appelée Gestionnaire de clés distribuées (DKM).
  
[Le Gestionnaire de clés](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) distribuées (DKM) est une fonctionnalité côté client qui utilise un ensemble de clés secrètes pour chiffrer et déchiffrer des informations. Seuls les membres d’un groupe de sécurité spécifiques dans les services de domaine Active Directory peuvent accéder à ces clés dans le but de déchiffrer les données chiffrées par le Gestionnaire de clés distribuées. Dans Exchange Online, seuls certains comptes de service sous lesquels les processus Exchange sont exécutés font partie de ce groupe de sécurité. Dans le cadre de la procédure opérationnelle standard dans le centre de données, les informations d’identification qui font partie de ce groupe de sécurité ne sont communiquées à aucun être humain, et par conséquent aucun être humain n’a accès aux clés qui peuvent déchiffrer les informations confidentielles.
  
À des fins de débogage, de résolution des problèmes ou d’audit, un administrateur de centre de données doit demander un accès élevé pour obtenir des informations d’identification temporaires qui font partie du groupe de sécurité. Ce processus requiert plusieurs niveaux d’approbation juridique. Si l’accès est accordé, toutes les activités font l’objet d’une journalisation et d’un audit. En outre, l’accès est accordé uniquement pour un intervalle de temps défini suite auquel il expire automatiquement.
  
Pour une protection supplémentaire, la technologie DKM inclut l’archivage et la substitution de clé automatisés. Ainsi, vous pouvez continuer à accéder à votre contenu plus ancien sans devoir utiliser la même clé indéfiniment.
  
## <a name="where-does-exchange-online-make-use-of-dkm"></a>Où le Gestionnaire de clés distribuées est-il utilisé dans Exchange Online ?

Microsoft utilise [le Gestionnaire de clés distribuées](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) pour chiffrer vos secrets dans les centres de données Exchange Online. Par exemple :
  
- Informations d’identification de compte de messagerie pour les comptes connectés. Les comptes connectés sont des comptes tiers tels que Hotmail, Gmail et Yahoo! comptes de messagerie.

- Clé client. Si vous utilisez le [chiffrement de service avec](customer-key-overview.md)la clé client, vous utiliserez [Azure Key Vault](/azure/key-vault/key-vault-whatis) pour protéger vos secrets.

## <a name="related-topics"></a>Rubriques connexes

[Chiffrement dans Office 365](encryption.md)
  
[Détails techniques de référence sur le chiffrement](technical-reference-details-about-encryption.md)
  
[Assurance de service dans le Centre de &amp; conformité de la sécurité](./service-assurance.md)
