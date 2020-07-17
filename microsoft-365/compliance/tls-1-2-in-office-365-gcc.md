---
title: Dépréciation des protocoles TLS 1,0 et 1,1 dans Office 365 GCC High et DoD
description: Explique comment Microsoft déplace la date de fin à la prise en charge de TLS 1,1 et 1,0 dans les environnements GCC High et DoD dans Office 365 et la préparation à l’utilisation de TLS 1,2.
author: workshay
manager: laurawi
localization_priority: Normal
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: shmehta
appliesto:
- Office 365 Business
ms.openlocfilehash: 76e9b203e58ba7fa23942ea42810456e3bee377d
ms.sourcegitcommit: 42b618231e9f608f3ae7226a313b0366601d0ea2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "45158879"
---
# <a name="deprecating-tls-10-and-11-in-office-365-gcc-high-and-dod"></a>Dépréciation des protocoles TLS 1,0 et 1,1 dans Office 365 GCC High et DoD

## <a name="summary"></a>Résumé

Afin de se conformer aux dernières normes de conformité pour le programme fédéral de gestion des risques et d’autorisations (FedRAMP), nous déprécions les versions 1,1 et 1,0 de Transport Layer Security (TLS) dans Microsoft Office 365 pour les environnements GCC High et DoD. Cette modification a été précédemment annoncée via le support Microsoft dans [la préparation de l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

La sécurité de vos données est importante et nous nous engageons à la transparence des modifications susceptibles d’affecter l’utilisation du service.

Bien que l' [implémentation de Microsoft TLS 1,0](https://support.microsoft.com/help/3117336) ne présente pas de failles de sécurité connues, nous nous contenterons de respecter les normes de conformité FedRAMP. Par conséquent, nous allons déprécier les protocoles TLS 1,1 et 1,0 dans Office 365 dans les environnements GCC High et DoD commençant le 15 janvier 2020. Pour plus d’informations sur la suppression des dépendances TLS 1,1 et 1,0, voir le livre blanc suivant :

[Résolution du problème 1,0 TLS](https://www.microsoft.com/download/details.aspx?id=55266)

Lors de la préparation de cette modification pour TLS 1,1 et 1,0, nous vous recommandons d’utiliser à la place TLS version 1,2. Pour plus d’informations, consultez [la rubrique préparation de l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="more-information"></a>Plus d’informations

À partir du 15 janvier 2020, Office 365 dans les environnements GCC High et DoD déprécieront TLS 1,1 et 1,0.

D’ici le 15 janvier 2020, toutes les combinaisons de serveurs clients et de serveurs d’exploration doivent utiliser le protocole TLS 1,2 (ou une version ultérieure) pour s’assurer que toutes les connexions peuvent être établies sans problèmes aux services Office 365. Cela peut nécessiter des mises à jour de certaines combinaisons de serveurs clients et de serveurs d’exploration.

Si vous ne procédez pas à la mise à jour vers la version 1,2 (ou une version ultérieure) pour le 15 janvier 2020, vous rencontrez des problèmes lorsque vous essayez de vous connecter à Office 365. En outre, vous devez effectuer une mise à jour vers TLS 1,2 (ou une version ultérieure) dans le cadre de la résolution.

Nous connaissons que les clients suivants ne peuvent pas utiliser TLS 1,2 :

- Android 4.3 et versions antérieures
- Firefox 5.0 et versions antérieures
- Internet Explorer 8 à 10 sur Windows 7 et versions antérieures
- Internet Explorer 10 sur Windows Phone 8,0
- Safari 6.0.4/OS X 10.8.4 et versions antérieures

Nous vous recommandons de mettre à jour vos clients afin de garantir un accès ininterrompu à Office 365 GCC High et DoD.

Bien que l’analyse actuelle des connexions aux services Microsoft Online indique que la plupart des services et points de terminaison voient l’utilisation de TLS 1,1 et 1,0 très peu, nous fournissons un avis de cette modification afin que vous puissiez mettre à jour les clients ou serveurs concernés, le cas échéant, avant la prise en charge de TLS 1,1 et 1,0. Si vous utilisez une infrastructure locale pour des scénarios hybrides ou AD FS (Active Directory Federation Services), assurez-vous que l’infrastructure peut prendre en charge à la fois les connexions entrantes et sortantes qui utilisent TLS 1,2 (ou une version ultérieure).

Outre les pannes que vous pouvez vous produire si vous utilisez les clients énumérés qui ne peuvent pas utiliser le protocole TLS 1,2, la suppression des protocoles TLS 1,1 et 1,0 vous empêchera d’utiliser le produit Microsoft suivant :

- Lync Phone

## <a name="references"></a>Références

L’article suivant du support technique fournit des conseils et des références pour vous aider à vous assurer que vos clients utilisent TLS 1,2 :

[Préparation de l’utilisation obligatoire de TLS 1,2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)
