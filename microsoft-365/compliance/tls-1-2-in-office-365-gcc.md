---
title: Désactivation de TLS 1.0 et 1.1 dans Office 365 GCC High et DoD
description: Explique comment Microsoft désactive la prise en charge de TLS 1.1 et 1.0 dans les environnements GCC High et DoD dans Microsoft 365.
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
ms.openlocfilehash: a0b1fecc9991cd7ba4ac915d3d684d43714014af
ms.sourcegitcommit: a62ac3c01ba700a51b78a647e2301f27ac437c5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2021
ms.locfileid: "50233750"
---
# <a name="disabling-tls-10-and-11-in-office-365-gcc-high-and-dod"></a>Désactivation de TLS 1.0 et 1.1 dans Office 365 GCC High et DoD

## <a name="summary"></a>Résumé

Afin de se conformer aux dernières normes de conformité pour le programme fedramp (Federal Risk and Authorization Management Program), nous désactivons les versions 1.1 et 1.0 de Transport Layer Security (TLS) dans Microsoft 365 pour les environnements GCC High et DoD. Cette modification a été annoncée précédemment par le biais du Support Microsoft dans la préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365.](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

La sécurité de vos données est importante et nous nous engageons à assurer la transparence des modifications qui pourraient affecter votre utilisation du service.

Bien que [l’implémentation de Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) ne présente aucune vulnérabilité de sécurité connue, nous nous engageons à respecter les normes de conformité FedRAMP. Par conséquent, nous avons désactivé TLS 1.1 et 1.0 dans Office 365 dans les environnements GCC High et DoD le 15 janvier 2020. Pour plus d’informations sur la suppression des dépendances TLS 1.1 et 1.0, voir le livre blanc suivant :

[Résolution du problème TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>Plus d’informations

À compter du 15 janvier 2020, Office 365 dans les environnements GCC High et DoD sera supprimé de TLS 1.1 et 1.0.

D’ici le 15 janvier 2020, toutes les combinaisons de serveurs clients et de serveurs de navigateur doivent utiliser TLS version 1.2 (ou version ultérieure) pour s’assurer que toutes les connexions peuvent être réalisées sans problème avec les services Office 365. Cela peut nécessiter des mises à jour de certaines combinaisons de serveurs clients et de serveurs de navigateur.

Si vous ne mettez pas à jour la version 1.2 de TLS (ou une version ultérieure) d’ici le 15 janvier 2020, vous serez face à des problèmes lorsque vous tenterez de vous connecter à Office 365. En outre, vous devez mettre à jour vers TLS 1.2 (ou une version ultérieure) dans le cadre de la résolution.

Vous devez mettre à jour vos ordinateurs clients pour vous assurer que vous conservez un accès ininterrompu à Office 365 GCC High et DoD.

Vous devez mettre à jour les applications qui appellent les API Microsoft 365 sur TLS 1.0 ou TLS 1.1 pour utiliser TLS 1.2. Par défaut, .NET 4.5 est TLS 1.1. Pour mettre à jour votre configuration .NET, voir [Comment activer TLS (Transport Layer Security) 1.2 sur les clients.](https://docs.microsoft.com/mem/configmgr/core/plan-design/security/enable-tls-1-2-client) Pour plus d’informations, voir Préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365.](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

Nous savons que les applications clientes suivantes ne peuvent pas utiliser TLS 1.2 :

- Android 4.3 et versions antérieures
- Firefox 5.0 et versions antérieures
- Internet Explorer 8 à 10 sur Windows 7 et versions antérieures
- Internet Explorer 10 sur Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 et versions antérieures

Bien que l’analyse actuelle des connexions aux services Microsoft Online indique que la plupart des services et points de terminaison voient très peu d’utilisation de TLS 1.1 et 1.0, nous fournissons une notification de cette modification afin que vous pouvez mettre à jour les clients ou serveurs concernés si nécessaire avant la fin de la prise en charge de TLS 1.1 et 1.0. Si vous utilisez une infrastructure locale pour des scénarios hybrides ou des services AD FS (Active Directory Federation Services), assurez-vous que l’infrastructure peut prendre en charge les connexions entrantes et sortantes qui utilisent TLS 1.2 (ou une version ultérieure).

En plus des pannes que vous pouvez connaître si vous utilisez les clients répertoriés qui ne peuvent pas utiliser TLS 1.2, la suppression de TLS 1.1 et 1.0 vous empêchera d’utiliser le produit Microsoft suivant :

- Téléphone Lync

## <a name="references"></a>Références

L’article de support suivant décrit des conseils et des références pour vous assurer que vos clients utilisent TLS 1.2 :

[Préparation de l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)
