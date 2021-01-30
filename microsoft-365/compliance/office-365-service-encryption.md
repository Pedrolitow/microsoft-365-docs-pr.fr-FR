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
description: 'Résumé : Comprendre la résilience des données dans Microsoft Office 365.'
ms.openlocfilehash: 89f3fbcc90cee0ad822156014ee4ac9e04fe3371
ms.sourcegitcommit: 50f10d83fa21db8572adab90784146e5231e3321
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2021
ms.locfileid: "50058547"
---
# <a name="service-encryption"></a>Chiffrement de service

En plus d’utiliser le chiffrement au niveau du volume, Exchange Online, Microsoft Teams, SharePoint Online et OneDrive Entreprise utilisent également le chiffrement de service pour chiffrer les données client. Le chiffrement de service offre deux options de gestion des clés :

## <a name="microsoft-managed-keys"></a>Clés gérées par Microsoft
Microsoft gère toutes les clés de chiffrement, y compris les clés racines pour le chiffrement de service. Cette option est actuellement activée par défaut pour Exchange Online, SharePoint Online, OneDrive Entreprise. Les clés gérées par Microsoft fournissent le chiffrement de service par défaut, sauf si vous décidez d’intégrer à l’aide de la clé client. Si, à une date ultérieure, vous décidez d’arrêter d’utiliser la clé client sans suivre le chemin de purge des données, vos données restent chiffrées à l’aide des clés gérées par Microsoft. Vos données sont toujours chiffrées à ce niveau par défaut au minimum. 

## <a name="customer-key"></a>Clé client
Vous fournissez les clés racine utilisées avec le chiffrement de service et vous les gérez à l’aide d’Azure Key Vault. Microsoft gère toutes les autres clés. Cette option, appelée clé client, est actuellement disponible pour Exchange Online, SharePoint Online et OneDrive Entreprise. (Précédemment appelé chiffrement avancé avec BYOK. Voir Amélioration de la transparence et du contrôle pour les clients [Office 365](https://blogs.office.com/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) pour l’annonce d’origine.)

Le chiffrement de service offre plusieurs avantages :

- Fournit une couche de protection supplémentaire sur BitLocker.

- Permet de séparer les administrateurs du système d’exploitation Windows de l’accès aux données d’application stockées ou traitées par le système d’exploitation.

- Inclut une option de clé client qui permet aux services multi-clients de fournir une gestion des clés par client.

- Améliore la capacité de Microsoft 365 à répondre aux demandes des clients qui ont des exigences de conformité spécifiques en matière de chiffrement.

À l’aide de la clé client, vous pouvez générer vos propres clés de chiffrement à l’aide d’un module de service matériel (HSM) local ou d’Azure Key Vault (AKV). Quelle que soit la façon dont vous générez la clé, vous utilisez AKV pour contrôler et gérer les clés de chiffrement utilisées par Office 365. Une fois que vos clés sont stockées dans AKV, elles peuvent être utilisées comme racine de l’un des chaînes de clés qui chiffre les données ou fichiers de votre boîte aux lettres.

Un autre avantage de la clé client est le contrôle que vous avez sur la capacité de Microsoft à traiter vos données. Si vous souhaitez supprimer des données d’Office 365, par exemple si vous souhaitez mettre fin au service avec Microsoft ou supprimer une partie de vos données stockées dans le cloud, vous pouvez le faire et utiliser la clé client comme contrôle technique. La suppression de données garantit que personne, y compris Microsoft, ne peut accéder aux données ni les traiter. La clé client est en plus et complémentaire de Customer Lockbox que vous utilisez pour contrôler l’accès à vos données par le personnel Microsoft.

Pour découvrir comment configurer la clé client pour Microsoft 365 pour Exchange Online, Microsoft Teams, SharePoint Online, y compris les sites d’équipe et OneDrive Entreprise, consultez les articles suivants :

- [Chiffrement du service avec la clé client](customer-key-overview.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)

- [Comprendre la clé de disponibilité](customer-key-availability-key-understand.md)
