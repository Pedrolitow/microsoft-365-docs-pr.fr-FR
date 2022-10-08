---
title: Feuille de route du locataire pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- m365initiative-coredeploy
ms.custom: it-pro
description: Feuille de route pour configurer vos locataires pour Microsoft 365.
ms.openlocfilehash: 2dc0a6ba5c85fb7866789381ca170e324b834f24
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68178556"
---
# <a name="tenant-roadmap-for-microsoft-365"></a>Feuille de route du locataire pour Microsoft 365

Votre locataire Microsoft 365 est l’ensemble des services affectés à votre organisation. En règle générale, ce locataire est associé à un ou plusieurs de vos noms de domaine DNS publics et agit comme un conteneur central et isolé pour différents abonnements et les licences qu’ils contiennent que vous affectez aux comptes d’utilisateur. Pour plus [d’informations, consultez Abonnements, licences, comptes et locataires pour les offres cloud de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

Lorsque vous créez un locataire Microsoft 365, vous l’affectez à un emplacement géographique spécifique. Vous pouvez également avoir un locataire avec plusieurs emplacements géographiques et déplacer votre locataire d’un emplacement à un autre.

Pour préparer votre locataire pour les utilisateurs, les groupes, les licences et les applications cloud, il est essentiel de planifier et d’exécuter soigneusement la configuration de votre locataire.

## <a name="set-up-your-microsoft-365-tenant"></a>Configurer votre client Microsoft 365

Après avoir vérifié que votre mise en réseau est optimisée pour l’accès à Microsoft 365 pour les travailleurs locaux et distants, vos prochaines grandes tâches sont en cours de planification et de configuration de votre locataire Microsoft 365 pour les noms de domaine DNS, les services courants et pour cette infrastructure d’identité qui prend en charge la connexion utilisateur sécurisée.

### <a name="plan"></a>Planification

Pour planifier l’implémentation de votre locataire :

- [Comprendre les abonnements, les licences et les locataires Azure Active Directory (Azure AD)](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md)
- [Comprendre comment utiliser des certificats SSL tiers](plan-for-third-party-ssl-certificates.md)
- [Comprendre comment un locataire Microsoft 365 est intégré aux services Azure AD](integrated-apps-and-azure-ads.md)
- [Planifier la prise en charge des applications clientes](microsoft-365-client-support-certificate-based-authentication.md)
- [Déterminer comment utiliser l’authentification moderne hybride](hybrid-modern-auth-overview.md)
- [Planifier les mises à niveau d’Office 2007 et Office 2010](plan-upgrade-previous-versions-office.md)
- [Comprendre l’isolation des locataires](/compliance/assurance/assurance-microsoft-365-isolation-controls#tenant-isolation)

### <a name="deploy"></a>Déployer

Pour déployer votre locataire : 

- Ajoutez les [domaines DNS](../admin/setup/add-domain.md) pour votre organisation.
- Utilisez les [repères d’installation dans le Centre d'administration Microsoft 365](setup-guides-for-microsoft-365.md).
- Créez votre [infrastructure d’identité](deploy-identity-solution-overview.md).

### <a name="move-a-tenants-geographic-locations"></a>Déplacer les emplacements géographiques d’un locataire

Microsoft continue d’ouvrir de nouveaux emplacements géographiques de centre de données (géos) pour les services Microsoft 365. Ces nouvelles zones géographiques de centre de données ajoutent de la capacité et des ressources de calcul pour prendre en charge la demande des clients et la croissance de l’utilisation. En outre, les nouvelles régions de centre de données permettent d'héberger des données dans la région pour les données client essentielles.

Pour plus d’informations, consultez [Déplacement de données de base vers de nouvelles zones géographiques de centre de données Microsoft 365](moving-data-to-new-datacenter-geos.md).


## <a name="deploy-microsoft-365-multi-geo"></a>Déployer Microsoft 365 multigéographique

Avec Microsoft 365 Multi-Geo, votre organisation peut étendre sa présence Microsoft 365 à plusieurs régions ou pays au sein de votre client existant.

Pour en savoir plus, consultez [Microsoft 365 Multigéographie](microsoft-365-multi-geo.md).

## <a name="manage-multiple-microsoft-365-tenants"></a>Gérer plusieurs locataires Microsoft 365 

Bien qu’il soit idéal d’avoir un seul locataire pour votre organisation, vous pouvez être l’une des nombreuses organisations qui ont plusieurs locataires. Il peut s’agir de fusions et d’acquisitions, d’une isolation administrative ou d’une informatique décentralisée.

Si vous avez plusieurs locataires Microsoft 365, consultez ces articles pour plus d’informations sur les éléments suivants :

- [Collaboration inter-clients](microsoft-365-inter-tenant-collaboration.md)
- [Migration de boîtes aux lettres inter-clients](cross-tenant-mailbox-migration.md)
- [Migrations client vers client](microsoft-365-tenant-to-tenant-migrations.md)

## <a name="next-step"></a>Étape suivante

Démarrez la planification de votre locataire avec [des abonnements, des licences, des comptes et des locataires](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
