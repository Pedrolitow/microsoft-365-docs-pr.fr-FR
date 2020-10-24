---
title: Feuille de route de client pour Microsoft 365
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
description: La feuille de route pour configurer vos clients pour Microsoft 365.
ms.openlocfilehash: 038d9b0d94b84d184f0d9d9b250d0ee4d2c19de9
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48753965"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Feuille de route de client pour Microsoft 365

Votre client Microsoft 365 est l’ensemble des services affectés à votre organisation. En règle générale, ce client est associé à un ou plusieurs de vos noms de domaine DNS publics et agit comme un conteneur central et isolé pour les différents abonnements et les licences que vous affectez aux comptes d’utilisateur. Pour plus d’informations, consultez [la rubrique abonnements, licences, comptes et clients pour les offres Cloud de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Lorsque vous créez un client Microsoft 365, affectez-le à un emplacement géographique spécifique. Vous pouvez également disposer d’un client disposant de plusieurs emplacements géographiques et déplacer votre client d’un emplacement à un autre.

Pour que votre client soit prêt pour les utilisateurs, les groupes, les licences et les applications Cloud, il est essentiel de planifier et d’exécuter soigneusement votre configuration client.

## <a name="set-up-your-microsoft-365-tenant"></a>Configurer votre client Microsoft 365

Une fois que vous avez vérifié que votre réseau est optimisé pour l’accès à Microsoft 365 pour les travailleurs locaux et distants, vos tâches importantes suivantes envisagent de planifier et de configurer votre client Microsoft 365 pour les noms de domaine DNS, les services courants et pour cette infrastructure d’identité qui prend en charge la connexion des utilisateurs sécurisés.

### <a name="plan"></a>Prévision

Pour planifier l’implémentation de votre client, procédez comme suit :

- [Comprendre les abonnements, les licences et les clients Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Comprendre comment utiliser des certificats SSL tiers](plan-for-third-party-ssl-certificates.md)
- [Comprendre comment un client Microsoft 365 est intégré à Azure AD services](integrated-apps-and-azure-ads.md)
- [Planifier la prise en charge des applications clientes](microsoft-365-client-support-certificate-based-authentication.md)
- [Déterminer comment utiliser l’authentification moderne hybride](hybrid-modern-auth-overview.md)
- [Planifier les mises à niveau d’Office 2007 et d’Office 2010](plan-upgrade-previous-versions-office.md)
- [Comprendre l’isolation du client](microsoft-365-tenant-isolation-overview.md)

### <a name="deploy"></a>Déployer

Pour déployer votre client : 

- Ajoutez les [domaines DNS](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) de votre organisation.
- Utilisez les [guides de configuration dans le centre d’administration Microsoft 365](setup-guides-for-microsoft-365.md).
- Créez votre [infrastructure d’identité](identity-roadmap-microsoft-365.md) et [Sécurisez vos connexions utilisateur](microsoft-365-secure-sign-in.md).

### <a name="move-a-tenants-geographic-locations"></a>Déplacer les emplacements géographiques d’un client

Microsoft continue d’ouvrir les nouveaux emplacements géographiques des centres de régions centres (Centre de ressources) pour les services Microsoft 365. Ces nouveaux centres de régions centres ajoutent de la capacité et des ressources de calcul afin de prendre en charge la demande des clients et la croissance de l’utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Pour plus d’informations, consultez la rubrique [Moving Data Core to New Microsoft 365 Datacenter régions centres](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Déployer Microsoft 365 multi-géo

Avec Microsoft 365 Multi-Geo, votre organisation peut étendre sa présence Microsoft 365 à plusieurs régions ou pays au sein de votre client existant.

Pour plus d’informations, consultez la rubrique [Microsoft 365 multi-géo](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenant"></a>Gérer plusieurs clients Microsoft 365 

Bien que le fait d’avoir un seul client pour votre Oganization soit idéal, il peut s’agir de l’une des nombreuses organisations qui ont plusieurs locataires. Il peut s’agir de fusions et d’acquisitions, mais également d’une isolation administrative ou d’une décentralisation.

Si vous avez plusieurs clients Microsoft 365, consultez les articles suivants pour plus d’informations sur :

- [Collaboration inter-clients](microsoft-365-inter-tenant-collaboration.md)
- [Migration de boîtes aux lettres inter-clients](cross-tenant-mailbox-migration.md)
- [Migrations client vers client](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Étape suivante

Démarrez votre planification client avec des [abonnements, des licences, des comptes et des clients](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
