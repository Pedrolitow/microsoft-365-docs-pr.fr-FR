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
ms.openlocfilehash: 006f81ee5b17baca4f42a78c5a87a59e8e90648f
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50166439"
---
# <a name="disabling-tls-10-and-11-in-office-365-gcc-high-and-dod"></a>Désactivation de TLS 1.0 et 1.1 dans Office 365 GCC High et DoD

## <a name="summary"></a>Résumé

Afin de se conformer aux dernières normes de conformité pour le Programme de gestion des risques et d’autorisations (FedRAMP), nous désactivons les versions TLS 1.1 et 1.0 dans Microsoft 365 pour les environnements GCC High et DoD. Cette modification a été précédemment annoncée via le Support Microsoft dans la préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365.](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

La sécurité de vos données est importante et nous nous engageons à assurer la transparence des modifications qui pourraient affecter votre utilisation du service.

Bien que [l’implémentation de Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) ne présente aucune vulnérabilité de sécurité connue, nous nous engageons à respecter les normes de conformité FedRAMP. Par conséquent, nous avons désactivé TLS 1.1 et 1.0 dans Office 365 dans les environnements GCC High et DoD le 15 janvier 2020. Pour plus d’informations sur la suppression des dépendances TLS 1.1 et 1.0, consultez le livre blanc suivant :

[Résolution du problème TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

Vous devez utiliser TLS version 1.2 à la place. Pour plus d’informations, voir Préparation de l’utilisation obligatoire de [TLS 1.2 dans Office 365.](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)

Pour SharePoint et OneDrive, vous devez mettre à jour et configurer .NET pour prendre en charge TLS 1.2. Pour plus d’informations, [voir Comment activer TLS 1.2 sur les clients](https://docs.microsoft.com/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>Plus d’informations

À compter du 15 janvier 2020, Office 365 dans les environnements GCC High et DoD sera supprimé de TLS 1.1 et 1.0.

D’ici le 15 janvier 2020, toutes les combinaisons de serveurs clients et de serveurs de navigateur doivent utiliser TLS version 1.2 (ou version ultérieure) pour s’assurer que toutes les connexions peuvent être réalisées sans problème avec les services Office 365. Cela peut nécessiter des mises à jour de certaines combinaisons de serveurs clients et de serveurs de navigateur.

Si vous ne mettez pas à jour la version 1.2 de TLS (ou une version ultérieure) d’ici le 15 janvier 2020, vous serez face à des problèmes lorsque vous tenterez de vous connecter à Office 365. En outre, vous devez mettre à jour vers TLS 1.2 (ou une version ultérieure) dans le cadre de la résolution.

Nous savons que les clients suivants ne peuvent pas utiliser TLS 1.2 :

- Android 4.3 et versions antérieures
- Firefox 5.0 et versions antérieures
- Internet Explorer 8 à 10 sur Windows 7 et versions antérieures
- Internet Explorer 10 sur Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 et versions antérieures

Nous vous recommandons de mettre à jour vos clients pour vous assurer que vous conservez un accès ininterrompu à Office 365 GCC High et DoD.

Bien que l’analyse actuelle des connexions aux services Microsoft Online indique que la plupart des services et des points de terminaison voient très peu d’utilisation de TLS 1.1 et 1.0, nous fournissons une notification de cette modification afin que vous pouvez mettre à jour les clients ou serveurs concernés si nécessaire avant la fin de la prise en charge de TLS 1.1 et 1.0. Si vous utilisez une infrastructure locale pour des scénarios hybrides ou des services AD FS (Active Directory Federation Services), assurez-vous que l’infrastructure peut prendre en charge les connexions entrantes et sortantes qui utilisent TLS 1.2 (ou une version ultérieure).

En plus des pannes que vous pouvez connaître si vous utilisez les clients répertoriés qui ne peuvent pas utiliser TLS 1.2, la suppression de TLS 1.1 et 1.0 vous empêchera d’utiliser le produit Microsoft suivant :

- Téléphone Lync

## <a name="references"></a>Références

L’article de support suivant décrit des conseils et des références pour vous assurer que vos clients utilisent TLS 1.2 :

[Préparation de l’utilisation obligatoire de TLS 1.2 dans Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365)
