---
title: Chiffrement de service
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 10/3/2019
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'Résumé : comprendre la résilience des données dans Microsoft Office 365.'
ms.openlocfilehash: 1c31c0d5524370fd417460fbacf3695df4fa0102
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43632239"
---
# <a name="service-encryption"></a>Chiffrement de service

En plus de l’utilisation du chiffrement au niveau du volume, Exchange Online, Skype entreprise, SharePoint Online et OneDrive entreprise utilisent également le chiffrement de service pour chiffrer les données client. Le chiffrement de service autorise deux options de gestion clés :

- Microsoft gère toutes les clés de chiffrement. (Cette option est actuellement disponible dans SharePoint Online, OneDrive entreprise et Skype entreprise.)

- Votre organisation fournit les clés racines. Vous gérez ces clés à l’aide du coffre de clés Azure. Cette option est appelée clé client. La clé client est actuellement disponible pour les fichiers Exchange Online, SharePoint Online, OneDrive entreprise, Skype entreprise et Teams. Si vous utilisez la clé client, ces clés remplacent les clés gérées par Microsoft pour chiffrer vos données.

Le chiffrement de service offre plusieurs avantages. Par exemple, clé client :

- Fournit des fonctionnalités de protection et de gestion des droits en plus de la protection de chiffrement élevée.

- Inclut une option de clé de client qui permet aux services mutualisés de fournir une gestion des clés par client.

- Permet de séparer les administrateurs du système d’exploitation Windows de l’accès aux données client stockées ou traitées par le système d’exploitation.

- Améliore la capacité de Microsoft 365 à répondre aux exigences des clients qui ont des exigences de conformité concernant le chiffrement.

## <a name="customer-key"></a>Clé client

À l’aide de la clé client, vous pouvez générer vos propres clés de chiffrement à l’aide d’un module de service matériel (HSM) local ou d’un coffre-fort de clés Azure (AKV). Quelle que soit la façon dont vous générez la clé, vous utilisez AKV pour contrôler et gérer les clés de chiffrement utilisées par Office 365. Une fois que vos clés sont stockées dans AKV, elles peuvent être utilisées comme racine de l’une des clés qui chiffre les données ou les fichiers de votre boîte aux lettres.

Un autre avantage de la clé client est le contrôle dont vous disposez sur la capacité de Microsoft à traiter vos données. Si vous souhaitez supprimer des données d’Office 365, par exemple si vous souhaitez terminer le service auprès de Microsoft ou supprimer une partie de vos données stockées dans le Cloud, vous pouvez le faire et utiliser la clé client comme un contrôle technique. Cela permet de s’assurer que personne, y compris Microsoft, ne peut accéder aux données ou les traiter. La clé client est en outre et complémentaire du référentiel sécurisé du client que vous utilisez pour contrôler l’accès à vos données par le personnel de Microsoft.

Pour en savoir plus sur la configuration de la clé client pour Microsoft 365 pour Exchange Online, Skype entreprise, SharePoint Online, y compris les sites d’équipe et OneDrive entreprise, consultez les articles suivants :

- [Chiffrement de service avec clé client](customer-key-overview.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)

- [Comprendre la clé de disponibilité](customer-key-availability-key-understand.md)
 
