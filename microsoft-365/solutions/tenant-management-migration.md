---
title: Étape 4. Migration de vos Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Migrez vos Windows, Office applications clientes et Office serveurs d’Microsoft 365 client.
ms.openlocfilehash: 1892ae3da900f1c940866a2b2a3c70c1d6cb5db3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62524248"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 4. Migration de vos Microsoft 365 pour les locataires d’entreprise

La plupart des organisations d’entreprise ont un environnement hétérogène qui inclut plusieurs sorties de systèmes d’exploitation, de logiciels clients et de logiciels serveur. Microsoft 365 entreprise inclut les versions les plus sécurisées des composants clés de votre infrastructure informatique. Il inclut également des fonctionnalités de productivité conçues pour tirer parti des technologies cloud.

Pour optimiser la valeur commerciale de la Microsoft 365 pour la suite intégrée de produits d’entreprise, commencez à planifier et implémenter une stratégie pour migrer ces produits :

| De | À |
|:-------|:-----|
| Windows 7 et Windows 8.1 | Windows 10 Entreprise |
| Office clients installés sur les appareils de vos travailleurs | Applications Microsoft 365 for entreprise |
| Office serveurs installés sur des serveurs locaux | Leurs services cloud équivalents dans Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>Migration vers Windows 10

Chaque Microsoft 365 licence d’entreprise inclut une licence pour Windows 10 Entreprise. Pour migrer vos appareils qui exécutent Windows 7 ou Windows 8.1, vous pouvez mettre à niveau sur place. Le support a pris fin Windows 7 janvier *2020*. 

Pour d’autres méthodes d’installation Windows 10 Entreprise au-delà d’une mise à niveau sur place, voir [Windows 10 scénarios de déploiement](/windows/deployment/windows-10-deployment-scenarios). Vous pouvez également [planifier le déploiement de Windows 10](/windows/deployment/planning/) par vous-même.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>Migration vers Applications Microsoft 365 pour les grandes entreprises

Microsoft 365 entreprise inclut Applications Microsoft 365 pour les grandes entreprises, une version des produits clients Office (Word, PowerPoint, Excel et Outlook ) qui est installé et mis à jour à partir du cloud Microsoft. Pour plus d’informations, voir [À propos Applications Microsoft 365 pour les grandes entreprises](/deployoffice/about-microsoft-365-apps).

Au lieu de maintenir vos ordinateurs à jour Office 2019 ou versions antérieures, prenez les mesures suivantes :

1. Obtenez et attribuez une licence Microsoft 365 pour vos utilisateurs.
2. Désinstallez Office 2013 ou Office 2016 sur leurs ordinateurs.
3. Installez Applications Microsoft 365 pour les grandes entreprises, individuellement ou pendant un déploiement. Pour plus d’informations, consultez le [Guide de déploiement de Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Applications Microsoft 365 pour les grandes entreprises installe automatiquement les mises à jour de sécurité et les nouvelles mises à jour de fonctionnalités et peut tirer parti des services basés sur le cloud dans Microsoft 365 pour améliorer la sécurité et la productivité.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>Migration de serveurs et de données locaux vers des Microsoft 365

Microsoft 365 entreprise inclut des versions cloud des services serveur Office qui utilisent certains des mêmes outils que les versions sur site des logiciels serveur Office, tels que les navigateurs web et le client Outlook. Ces services basés sur le cloud sont automatiquement mis à jour pour la sécurité et les nouvelles fonctionnalités. Après la migration, votre service informatique peut gagner du temps pour la maintenance et la mise à jour des serveurs locaux.

Utilisez les ressources suivantes pour plus d’informations sur la migration des utilisateurs et des données pour Microsoft 365 charges de travail spécifiques :

- [Déplacer des boîtes aux lettres de l’Exchange Server vers Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Migrer SharePoint données de SharePoint Server vers SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Migrer Skype Entreprise Online vers Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>Transition de l'ensemble de votre organisation

Pour obtenir une meilleure image de la façon de déplacer l’ensemble de votre organisation vers les produits et services Microsoft 365 entreprise, téléchargez cette affiche de transition :

[![Image montrant l’affiche Transition vers Microsoft 365 projet.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Cette affiche de deux pages est un moyen rapide d'inventorier vos infrastructures existantes. Utilisez-le pour obtenir des conseils pour passer à un produit ou un service Microsoft 365 entreprise. Il présente les produits Windows et Office, ainsi que d’autres éléments d’infrastructure et de sécurité tels que la gestion des appareils, la protection des identités et des menaces, ainsi que la protection et la conformité des informations.

## <a name="results-of-step-4"></a>Résultats de l’étape 4

Pour la migration de votre Microsoft 365 client, vous avez déterminé :

- Les appareils qui exécutent Windows 7 ou Windows 8.1 et le plan de mise à jour vers Windows 10 Entreprise.
- Quels appareils exécutent les applications Office client et envisagez de les mettre à jour Microsoft 365 applications pour entreprise.
- Les services de serveur Office locaux doivent être migrés vers leur équivalent Microsoft 365 et le plan de migration de ces services et de leurs données.

Voici un exemple de client avec une migration terminée de serveurs locaux.

![Exemple de client avec une migration terminée de serveurs locaux.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

Dans cette illustration, l’organisation a :

- Migration de ses boîtes aux lettres Exchange Server en local vers Exchange Online.
- Migration de ses données et sites SharePoint server locaux vers SharePoint dans Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>Maintenance continue pour la migration

Régulièrement, vous devrez peut-être :

- En fonction de l’état de votre migration Exchange boîtes aux lettres, continuez à déployer la transition Exchange Online vers votre organisation.
- En fonction de l’état de votre migration SharePoint site local, continuez à déployer la transition vers SharePoint dans Microsoft 365 votre organisation.

## <a name="next-step"></a>Étape suivante

[![Étape 5. Déployer la gestion des appareils et des applications.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

Poursuivez la [gestion des appareils et des applications](tenant-management-device-management.md) pour déployer la gestion des appareils et des applications.