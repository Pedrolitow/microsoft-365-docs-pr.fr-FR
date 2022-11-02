---
title: Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/31/2022
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- purview-compliance
description: 'Outre le Centre de gestion de la confidentialité Microsoft qui fournit des informations sur la sécurité, la confidentialité et la conformité pour Microsoft 365, découvrez comment Microsoft aide à protéger les secrets que vous stockez dans ses centres de données. '
ms.openlocfilehash: e46788c763e7b930c79abc918a9f4706b896ff23
ms.sourcegitcommit: a66b30765efc0ea0eca865f08a62d45047a90246
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68828051"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>Procédure de sécurisation des informations confidentielles dans votre courrier électronique dans Exchange Online

Cet article décrit la façon dont Microsoft protège les informations confidentielles figurant dans vos courriers électroniques dans ses centres de données.
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-we-secure-secret-information-provided-by-you"></a>Comment nous sécurrons les informations secrètes que vous nous avez fournies

En plus du Centre de gestion de la confidentialité Office 365 qui fournit des informations sur la [sécurité, la confidentialité et la conformité pour Office 365](./get-started-with-service-trust-portal.md), nous utilisons une technologie appelée Distributed Key Manager (DKM).
  
[Distributed Key Manager](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) (DKM) est une technologie côté client qui utilise un ensemble de clés secrètes pour chiffrer et déchiffrer les informations. Seuls les membres d’un groupe de sécurité spécifiques dans les services de domaine Active Directory peuvent accéder à ces clés dans le but de déchiffrer les données chiffrées par le Gestionnaire de clés distribuées. Dans Exchange Online, seuls certains comptes de service sous lesquels les processus Exchange sont exécutés font partie de ce groupe de sécurité. Aucun humain ne reçoit d’informations d’identification qui font partie de ce groupe de sécurité et, par conséquent, aucun humain n’a accès aux clés qui peuvent déchiffrer ces secrets.
  
À des fins de débogage, de résolution des problèmes ou d’audit, un administrateur de centre de données doit demander un accès élevé pour obtenir des informations d’identification temporaires qui font partie du groupe de sécurité. Ce processus requiert plusieurs niveaux d’approbation juridique. Si l’accès est accordé, toutes les activités font l’objet d’une journalisation et d’un audit. L’accès n’est accordé que pendant un intervalle défini après lequel il expire automatiquement.
  
Pour une protection supplémentaire, la technologie DKM inclut l’archivage et la substitution de clé automatisés. La substitution et l’archivage automatisés garantissent que vous pouvez continuer à accéder à votre contenu plus ancien sans avoir à vous appuyer indéfiniment sur la même clé.
  
## <a name="where-exchange-online-uses-dkm"></a>Où Exchange Online utilise DKM

Microsoft utilise [Distributed Key Manager](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) pour chiffrer vos secrets dans Exchange Online centres de données. Par exemple :
  
- Email informations d’identification de compte pour les comptes connectés. Les comptes connectés sont des comptes tiers tels que Hotmail, Gmail et Yahoo! comptes de messagerie.

- Clé client. Si vous utilisez [le chiffrement de service avec la clé client Microsoft Purview](customer-key-overview.md), vous utiliserez [Azure Key Vault](/azure/key-vault/key-vault-whatis) pour protéger vos secrets.

## <a name="related-articles"></a>Articles connexes

[Chiffrement dans Office 365](encryption.md)
  
[Détails techniques de référence sur le chiffrement](technical-reference-details-about-encryption.md)
  
[Assurance du service dans le portail de conformité Microsoft Purview](./service-assurance.md)
