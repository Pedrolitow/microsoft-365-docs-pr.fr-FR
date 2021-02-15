---
title: Feuille de route du client pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Feuille de route pour configurer vos clients pour Microsoft 365.
ms.openlocfilehash: d2640a036eedda0b0962a15a03dcf0211ea0209b
ms.sourcegitcommit: c84cceb07e748969723a31b350e37f3ec79255ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "48948396"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Feuille de route du client pour Microsoft 365

Votre client Microsoft 365 est l’ensemble des services affectés à votre organisation. En règle générale, ce client est associé à un ou plusieurs de vos noms de domaine DNS publics et agit comme un conteneur central et isolé pour différents abonnements et les licences que vous attribuez aux comptes d’utilisateurs. Pour plus d’informations, voir [Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Lorsque vous créez un client Microsoft 365, vous l’affectez à un emplacement géographique spécifique. Vous pouvez également avoir un client avec plusieurs emplacements géographiques et déplacer votre client d’un emplacement à un autre.

Pour préparer votre client pour les utilisateurs, les groupes, les licences et les applications cloud, il est essentiel de planifier et d’exécuter avec soin la configuration de votre client.

## <a name="set-up-your-microsoft-365-tenant"></a>Configurer votre client Microsoft 365

Une fois que vous vous êtes assuré que votre réseau est optimisé pour l’accès à Microsoft 365 pour les travailleurs locaux et distants, vos prochaines tâches importantes sont la planification et la configuration de votre client Microsoft 365 pour les noms de domaine DNS, les services communs et pour cette infrastructure d’identité qui prend en charge la connectez-vous utilisateur sécurisée.

### <a name="plan"></a>Planification

Pour planifier l’implémentation de votre client :

- [Comprendre les abonnements, les licences et les locataires Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Comprendre comment utiliser des certificats SSL tiers](plan-for-third-party-ssl-certificates.md)
- [Comprendre la façon dont un client Microsoft 365 est intégré aux services Azure AD](integrated-apps-and-azure-ads.md)
- [Planifier la prise en charge des applications clientes](microsoft-365-client-support-certificate-based-authentication.md)
- [Déterminer comment utiliser l’authentification moderne hybride](hybrid-modern-auth-overview.md)
- [Planifier les mises à niveau d’Office 2007 et d’Office 2010](plan-upgrade-previous-versions-office.md)
- [Comprendre l’isolation du client](microsoft-365-tenant-isolation-overview.md)

### <a name="deploy"></a>Déployer

Pour déployer votre client : 

- Ajoutez [les domaines DNS](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) pour votre organisation.
- Utilisez les [guides de configuration dans le Centre d’administration Microsoft 365.](setup-guides-for-microsoft-365.md)
- Créez votre [infrastructure d’identité](identity-roadmap-microsoft-365.md) [et sécurisation de vos utilisateurs.](microsoft-365-secure-sign-in.md)

### <a name="move-a-tenants-geographic-locations"></a>Déplacer les emplacements géographiques d’un client

Microsoft continue d’ouvrir de nouveaux emplacements géographiques de centres de données (régions) pour les services Microsoft 365. Ces nouvelles géos de centres de données ajoutent de la capacité et des ressources de calcul pour prendre en charge la demande des clients et la croissance de l’utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Pour plus d’informations, voir Déplacement de données principales vers de nouvelles géos de centres de données [Microsoft 365.](moving-data-to-new-datacenter-geos.md)


## <a name="deploy-microsoft-365-multi-geo"></a>Déployer Microsoft 365 Multi-Géo

Avec Microsoft 365 Multi-Geo, votre organisation peut étendre sa présence Microsoft 365 à plusieurs régions ou pays au sein de votre client existant.

Pour en savoir plus, consultez [Microsoft 365 Multigéographie](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Gérer plusieurs clients Microsoft 365 

Bien qu’il soit idéal d’avoir un seul client pour votre oganisation, vous pouvez être l’une des nombreuses organisations qui ont plusieurs locataires. Les raisons peuvent inclure des fusions et des acquisitions, une isolation administrative ou une administration décentralisée.

Si vous avez plusieurs clients Microsoft 365, consultez ces articles pour plus d’informations sur :

- [Collaboration inter-clients](microsoft-365-inter-tenant-collaboration.md)
- [Migration de boîtes aux lettres inter-clients](cross-tenant-mailbox-migration.md)
- [Migrations client vers client](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Étape suivante

Commencez la planification de votre client [avec des abonnements, des licences, des comptes et des locataires.](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
