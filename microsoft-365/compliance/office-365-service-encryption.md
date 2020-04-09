---
title: Chiffrement du service Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 4/8/2020
localization_priority: None
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'Résumé : comprendre le chiffrement des données au niveau de la couche de service dans Microsoft Office 365.'
ms.openlocfilehash: a8faded033ade013924eeeab269aa213840430b4
ms.sourcegitcommit: 13f28aa762e467bab8ab1e95e1917b3ac28931da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "43193460"
---
# <a name="office-365-service-encryption"></a>Chiffrement du service Office 365

En plus de l’utilisation de BitLocker pour le chiffrement au niveau du volume, Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et teams utilisent également le chiffrement de service pour chiffrer les données client. Le chiffrement de service autorise deux options de gestion clés :

- Microsoft gère toutes les clés de chiffrement. Cette option est actuellement disponible dans les conversations SharePoint Online, OneDrive entreprise, Skype entreprise et Teams. Vos données sont chiffrées par défaut à l’aide de clés gérées Microsoft.

- Votre organisation fournit les clés racines. Vous gérez ces clés à l’aide du coffre de clés Azure. Cette option est appelée clé client. La clé client est actuellement disponible pour les fichiers Exchange Online, SharePoint Online, OneDrive entreprise, Skype entreprise et Teams. Si vous utilisez la clé client, ces clés remplacent les clés gérées Microsoft pour chiffrer vos données.

Quelle que soit l’option choisie, le chiffrement de service offre plusieurs avantages :

- Applique l’authentification de l’utilisateur pour récupérer et déchiffrer les données demandées par un utilisateur autorisé.

- Permet de séparer les administrateurs du système d’exploitation Windows de l’accès aux données client stockées ou traitées par le système d’exploitation.

- Améliore la capacité d’Office 365 à répondre aux exigences des clients qui ont des exigences de conformité concernant le chiffrement.

Pour en savoir plus sur la configuration de la clé client pour Office 365 pour Exchange Online, Skype entreprise, SharePoint Online, OneDrive entreprise et les fichiers Teams, consultez les articles suivants :

- [Chiffrement de service avec clé client dans Office 365](customer-key-overview.md)

- [Configurer la clé client pour Office 365](customer-key-set-up.md)

- [Gérer la clé client pour Office 365](customer-key-manage.md)

- [Faire pivoter ou faire pivoter une clé client ou une clé de disponibilité](customer-key-availability-key-roll.md)

- [Comprendre la clé de disponibilité](customer-key-availability-key-understand.md)
