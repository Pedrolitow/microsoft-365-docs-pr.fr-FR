---
title: Isolation du client dans Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Cet article contient un résumé de la façon dont Microsoft applique l’isolation des clients dans les services cloud tels que Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c9af522c71f3b089c8f2f198f861bcac8a0011a2
ms.sourcegitcommit: 11d1044c6600b1f568b6dc8a53db9b07f2f0ad1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "48384939"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Isolation du client dans Microsoft 365

L’un des principaux avantages du cloud computing est le concept d’une infrastructure commune partagée à de nombreux clients simultanément, ce qui conduit à une échelle. Ce concept est appelé *« location multiple*». Microsoft travaille continuellement pour s’assurer que les architectures mutualisées de nos services Cloud prennent en charge les normes de sécurité, de confidentialité, de respect de la vie privée, d'intégrité et de disponibilité au niveau de l'entreprise.

Sur la base des investissements et [](https://www.microsoft.com/trust-center) de l’expérience importants collectés par l’informatique de confiance et le cycle de vie du développement de la [sécurité,](https://www.microsoft.com/securityengineering/sdl/)les services cloud de Microsoft ont été conçus en présupposant que tous les clients sont potentiellement présomptioneux pour tous les autres clients, et nous avons implémenté des mesures de sécurité pour empêcher les actions d’un client d’affecter la sécurité ou le service d’un autre client, ou d’accéder au contenu d’un autre client.

Les deux principaux objectifs de la maintenance de l’isolation des locataires dans un environnement à plusieurs locataires sont les autres :

1.    prévention de la fuite de contenu client ou d’un accès non autorisé au contenu client entre les clients ; et
2.    Empêcher les actions d’un client d’affecter le service pour un autre client

Plusieurs formes de protection ont été implémentées dans Microsoft 365 pour empêcher les clients de compromettre les services ou applications Microsoft 365 ou d’obtenir un accès non autorisé aux informations d’autres clients ou au système Microsoft 365 lui-même, notamment :

- L’isolation logique du contenu client au sein de chaque client pour les services Microsoft 365 est obtenue via l’autorisation Azure Active Directory et le contrôle d’accès basé sur les rôles.
- SharePoint Online fournit des mécanismes d’isolation des données au niveau du stockage.
- Microsoft utilise une sécurité physique rigoureuse, un filtrage des antécédents et une stratégie de chiffrement à plusieurs couches pour protéger la confidentialité et l’intégrité du contenu des clients. Tous les centres de données Microsoft 365 ont des contrôles d’accès biométrique, la plupart nécessitant des impressions de paume pour obtenir un accès physique. En outre, tous les employés de Microsoft basés aux États-Unis doivent réussir une vérification des antécédents standard dans le cadre du processus d’embauche. Pour plus d’informations sur les contrôles utilisés pour l’accès administratif dans Microsoft 365, voir Contrôles d’accès administratif [Microsoft 365.](microsoft-365-administrative-access-controls-overview.md)
- Microsoft 365 utilise des technologies côté service qui chiffrent le contenu client au repos et en transit, notamment BitLocker, le chiffrement par fichier, TLS (Transport Layer Security) et IPsec (Internet Protocol Security). Pour plus d’informations sur le chiffrement dans Microsoft 365, voir Technologies de chiffrement de [données dans Microsoft 365.](../compliance/office-365-encryption-in-the-microsoft-cloud-overview.md)

Ensemble, les protections répertoriées ci-dessus fournissent des contrôles d’isolation logique robustes qui fournissent une protection contre les menaces et une atténuation équivalentes à celle fournie par l’isolation physique seule.

## <a name="related-links"></a>Liens connexes

- [Isolation et contrôle d’accès dans Azure Active Directory](microsoft-365-isolation-in-azure-active-directory.md)
- [Isolation du client dans Office Graph et Delve](microsoft-365-isolation-in-graph-and-delve.md)
- [Isolation du client dans Microsoft 365 Search](microsoft-365-isolation-in-microsoft-365-search.md)
- [Isolation du client dans Office 365 Video](microsoft-365-isolation-in-microsoft-365-video.md)
- [Limites de ressources](microsoft-365-resource-limits.md)
- [Surveillance et test des limites du client](microsoft-365-monitoring-and-testing.md)
- [Isolation et contrôle d’accès dans Microsoft 365](microsoft-365-isolation-in-microsoft-365.md)
