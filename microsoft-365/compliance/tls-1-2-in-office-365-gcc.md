---
title: Désactivation de TLS 1.0 et 1.1 dans Microsoft 365 GCC High et DoD
description: Explique comment Microsoft désactive la prise en charge de TLS 1.1 et 1.0 dans les environnements GCC High et DoD dans Microsoft 365.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.collection:
- tier2
- purview-compliance
ms.openlocfilehash: c2ef3d59c6d6264b64628622f4883c09778aa91e
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68628398"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>Désactivation de TLS 1.0 et 1.1 dans Microsoft 365 GCC High et DoD

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="summary"></a>Résumé

Pour nous conformer aux dernières normes de conformité du Programme fédéral de gestion des risques et des autorisations (FedRAMP), nous désactivons les versions 1.1 et 1.0 de TLS (Transport Layer Security) dans Microsoft 365 pour les environnements GCC High et DoD. Ce changement a été annoncé précédemment par le biais de Support Microsoft de [préparation de l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

La sécurité de vos données est importante et nous nous engageons à assurer la transparence des modifications susceptibles d’affecter votre utilisation du service.

Bien que [l’implémentation de Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) n’ait pas de failles de sécurité connues, nous restons attachés aux normes de conformité FedRAMP. Par conséquent, nous avons désactivé TLS 1.1 et 1.0 dans Microsoft 365 dans les environnements GCC High et DoD le 15 janvier 2020. Pour plus d’informations sur la suppression des dépendances TLS 1.1 et 1.0, consultez le livre blanc suivant :

[Résolution du problème TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Plus d’informations

À compter du 15 janvier 2020, Microsoft 365 dans les environnements GCC High et DoD désactive TLS 1.1 et 1.0.

D’ici le 15 janvier 2020, toutes les combinaisons de serveurs clients et de serveurs de navigateur doivent utiliser TLS version 1.2 (ou une version ultérieure) pour s’assurer que toutes les connexions peuvent être établies sans problème avec Microsoft 365. Cela peut nécessiter des mises à jour de certaines combinaisons de serveurs clients et de serveurs de navigateur.

Pour SharePoint et OneDrive, vous devez mettre à jour et configurer .NET pour prendre en charge TLS 1.2. Pour plus d’informations, consultez [Comment activer TLS 1.2 sur les clients](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

Vous devez mettre à jour vos ordinateurs clients pour vous assurer que vous conservez un accès ininterrompu à Office 365 GCC High et DoD.

Vous devez mettre à jour les applications qui appellent des API Microsoft 365 sur TLS 1.0 ou TLS 1.1 pour utiliser TLS 1.2. .NET 4.5 est défini par défaut sur TLS 1.1. Pour mettre à jour votre configuration .NET, consultez [Comment activer TLS (Transport Layer Security) 1.2 sur les clients](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). Pour plus d’informations, consultez [Préparation à l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

Nous savons que les applications clientes suivantes ne peuvent pas utiliser TLS 1.2 :

- Android 4.3 et versions antérieures
- Firefox 5.0 et versions antérieures
- Internet Explorer 8 à 10 dans Windows 7 et versions antérieures
- Internet Explorer 10 sur Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 et versions antérieures

Bien que l’analyse actuelle des connexions aux services Microsoft Online indique que la plupart des services et des points de terminaison ne voient que peu d’utilisation de TLS 1.1 et 1.0, nous vous informons de cette modification afin que vous puissiez mettre à jour les clients ou serveurs affectés en fonction des besoins avant la fin de la prise en charge de TLS 1.1 et 1.0. Si vous utilisez une infrastructure locale pour des scénarios hybrides ou des Services ADFS (AD FS), assurez-vous que l’infrastructure peut prendre en charge les connexions entrantes et sortantes qui utilisent TLS 1.2 (ou une version ultérieure).

Outre les pannes que vous pouvez rencontrer si vous utilisez les clients répertoriés qui ne peuvent pas utiliser TLS 1.2, la suppression de TLS 1.1 et 1.0 vous empêchera d’utiliser le produit Microsoft suivant :

- Téléphone Lync

## <a name="references"></a>References

Pour obtenir des conseils et des références pour vous assurer que vos clients utilisent TLS 1.2, consultez [Préparation à l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
