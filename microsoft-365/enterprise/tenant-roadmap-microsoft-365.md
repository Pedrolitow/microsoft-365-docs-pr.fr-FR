---
title: Feuille de route du client pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Feuille de route pour configurer vos locataires pour Microsoft 365.
ms.openlocfilehash: d041c87e12bfb3025592cb14cda5413c805dc880
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58354211"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Feuille de route du client pour Microsoft 365

Votre Microsoft 365 client est l’ensemble des services affectés à votre organisation. En règle générale, ce client est associé à un ou plusieurs de vos noms de domaine DNS publics et agit comme un conteneur central et isolé pour différents abonnements et les licences que vous attribuez aux comptes d’utilisateurs. Pour plus d’informations, voir [Subscriptions, licenses, accounts, and tenants for Microsoft’s cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Lorsque vous créez un Microsoft 365 client, vous l’affectez à un emplacement géographique spécifique. Vous pouvez également avoir un client avec plusieurs emplacements géographiques et déplacer votre client d’un emplacement à un autre.

Pour préparer votre client pour les utilisateurs, les groupes, les licences et les applications cloud, il est essentiel de planifier et d’exécuter avec soin votre configuration client.

## <a name="set-up-your-microsoft-365-tenant"></a>Configurer votre client Microsoft 365

Après vous être assuré que votre réseau est optimisé pour l’accès à Microsoft 365 pour les travailleurs locaux et distants, vos prochaines tâches importantes sont la planification et la configuration de votre client Microsoft 365 pour les noms de domaine DNS, les services communs et pour cette infrastructure d’identités qui prend en charge la connectez-vous utilisateur sécurisée.

### <a name="plan"></a>Prévision

Pour planifier l’implémentation de votre client :

- [Comprendre les abonnements, les licences et les Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Comprendre comment utiliser des certificats SSL tiers](plan-for-third-party-ssl-certificates.md)
- [Comprendre la façon dont un client Microsoft 365 est intégré aux services Azure AD](integrated-apps-and-azure-ads.md)
- [Planifier la prise en charge des applications clientes](microsoft-365-client-support-certificate-based-authentication.md)
- [Déterminer comment utiliser l’authentification moderne hybride](hybrid-modern-auth-overview.md)
- [Planifier les mises Office 2007 et Office 2010](plan-upgrade-previous-versions-office.md)
- [Comprendre l’isolation du client](/compliance/assurance/microsoft-365-isolation-controls)

### <a name="deploy"></a>Déployer

Pour déployer votre client : 

- Ajoutez [les domaines DNS](../admin/setup/add-domain.md) pour votre organisation.
- Utilisez les [guides d’installation du Centre d’administration Microsoft 365](setup-guides-for-microsoft-365.md).
- Créez votre [infrastructure d’identité](identity-roadmap-microsoft-365.md) [et sécurisation de vos utilisateurs.](microsoft-365-secure-sign-in.md)

### <a name="move-a-tenants-geographic-locations"></a>Déplacer les emplacements géographiques d’un client

Microsoft continue d’ouvrir de nouveaux emplacements géographiques de centre de données (Microsoft 365 services). Ces nouvelles géos de centres de données ajoutent de la capacité et des ressources de calcul pour prendre en charge la demande des clients et la croissance de l’utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Pour plus d’informations, voir Déplacement de données principales vers [de nouvelles Microsoft 365 de centres de données.](moving-data-to-new-datacenter-geos.md)


## <a name="deploy-microsoft-365-multi-geo"></a>Déployer Microsoft 365 multigéogé

Avec Microsoft 365 Multi-Geo, votre organisation peut étendre sa présence Microsoft 365 à plusieurs régions ou pays au sein de votre client existant.

Pour en savoir plus, consultez [Microsoft 365 Multigéographie](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Gérer plusieurs Microsoft 365 client 

Bien qu’il soit idéal d’avoir un seul client pour votre oganisation, vous pouvez être l’une des nombreuses organisations qui ont plusieurs locataires. Les raisons peuvent inclure des fusions et des acquisitions, une isolation administrative ou une administration décentralisée.

Si vous avez plusieurs Microsoft 365 client, consultez les articles suivants pour plus d’informations sur :

- [Collaboration inter-clients](microsoft-365-inter-tenant-collaboration.md)
- [Migration de boîtes aux lettres inter-clients](cross-tenant-mailbox-migration.md)
- [Migrations client vers client](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Étape suivante

Démarrez la planification de votre client [avec des abonnements, des licences, des comptes et des locataires.](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)