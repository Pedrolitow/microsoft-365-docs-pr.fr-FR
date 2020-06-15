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
ms.openlocfilehash: e69d35f08070e1fe092ca8a9b4aef6d179711121
ms.sourcegitcommit: f80c6c52e5b08290f74baec1d64c4070046c32e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44717345"
---
# <a name="service-encryption"></a>Chiffrement de service

En plus de l’utilisation du chiffrement au niveau du volume, Exchange Online, Skype entreprise, SharePoint Online et OneDrive entreprise utilisent également le chiffrement de service pour chiffrer les données client. Le chiffrement de service autorise deux options de gestion clés :

## <a name="microsoft-managed-keys"></a>Clés gérées Microsoft : 
Microsoft gère toutes les clés de chiffrement, y compris les clés racines pour le chiffrement de service. Cette option est actuellement disponible dans SharePoint Online et OneDrive entreprise. Cette option est actuellement déployée pour Exchange Online. Les clés gérées Microsoft fournissent le chiffrement de service par défaut, sauf si vous décidez d’utiliser la clé client. Si, par la suite, vous décidez de cesser d’utiliser la clé client sans suivre le chemin de purge des données, vos données resteront chiffrées à l’aide des clés gérées Microsoft. Vos données sont toujours chiffrées à ce niveau par défaut au minimum. 

## <a name="customer-key"></a>Clé client : 
Vous fournissez des clés racines utilisées avec le chiffrement de service et vous gérez ces clés à l’aide du coffre de clés Azure. Microsoft gère toutes les autres clés. Cette option est appelée clé client et elle est actuellement disponible pour Exchange Online, SharePoint Online et OneDrive entreprise. (Précédemment appelé chiffrement avancé avec BYOK. Consultez la rubrique amélioration de la [transparence et du contrôle pour les clients Office 365](https://blogs.office.com/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) pour l’annonce d’origine.)

Le chiffrement de service offre plusieurs avantages. Par exemple, clé client :

- Fournit des fonctionnalités de protection et de gestion des droits en plus de la protection de chiffrement élevée.

- Inclut une option de clé de client qui permet aux services mutualisés de fournir une gestion des clés par client.

- Permet de séparer les administrateurs du système d’exploitation Windows de l’accès aux données client stockées ou traitées par le système d’exploitation.

- Améliore la capacité de Microsoft 365 à répondre aux exigences des clients qui ont des exigences de conformité concernant le chiffrement.

À l’aide de la clé client, vous pouvez générer vos propres clés de chiffrement à l’aide d’un module de service matériel (HSM) local ou d’un coffre-fort de clés Azure (AKV). Quelle que soit la façon dont vous générez la clé, vous utilisez AKV pour contrôler et gérer les clés de chiffrement utilisées par Office 365. Une fois que vos clés sont stockées dans AKV, elles peuvent être utilisées comme racine de l’une des clés qui chiffre les données ou les fichiers de votre boîte aux lettres.

Un autre avantage de la clé client est le contrôle dont vous disposez sur la capacité de Microsoft à traiter vos données. Si vous souhaitez supprimer des données d’Office 365, par exemple si vous souhaitez terminer le service auprès de Microsoft ou supprimer une partie de vos données stockées dans le Cloud, vous pouvez le faire et utiliser la clé client comme un contrôle technique. Cela permet de s’assurer que personne, y compris Microsoft, ne peut accéder aux données ou les traiter. La clé client est en outre et complémentaire du référentiel sécurisé du client que vous utilisez pour contrôler l’accès à vos données par le personnel de Microsoft.

Pour en savoir plus sur la configuration de la clé client pour Microsoft 365 pour Exchange Online, Skype entreprise, SharePoint Online, y compris les sites d’équipe et OneDrive entreprise, consultez les articles suivants :

- [Chiffrement de service avec clé client](customer-key-overview.md)

- [Configurer la clé client](customer-key-set-up.md)

- [Gérer la clé client](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)

- [Comprendre la clé de disponibilité](customer-key-availability-key-understand.md)

