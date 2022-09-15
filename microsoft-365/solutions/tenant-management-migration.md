---
title: Étape 4. Migration pour votre Microsoft 365 pour les locataires d’entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Migrez vos appareils Windows, vos applications clientes Office et vos serveurs Office pour vos locataires Microsoft 365.
ms.openlocfilehash: b0c08bb17edba7e19639c48829724457643b02cb
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730768"
---
# <a name="step-4-migration-for-your-microsoft-365-for-enterprise-tenants"></a>Étape 4. Migration pour votre Microsoft 365 pour les locataires d’entreprise

La plupart des organisations d’entreprise ont un environnement hétérogène qui inclut plusieurs versions de systèmes d’exploitation, de logiciels clients et de logiciels serveur. Microsoft 365 pour entreprise inclut les versions les plus sécurisées des composants clés de votre infrastructure informatique. Il inclut également des fonctionnalités de productivité conçues pour tirer parti des technologies cloud.

Pour optimiser la valeur métier de la suite intégrée de produits Microsoft 365 for enterprise, commencez à planifier et à implémenter une stratégie pour migrer ces versions :

| De | À |
|:-------|:-----|
| Windows 7 et Windows 8.1 | Windows 10 Entreprise |
| Produits clients Office installés sur les appareils de votre worker | Applications Microsoft 365 pour les entreprises |
| Produits serveur Office installés sur des serveurs locaux | Leurs services cloud équivalents dans Microsoft 365 |
|  |  |

## <a name="migrating-to-windows-10"></a>Migration vers Windows 10

Chaque licence Microsoft 365 pour entreprise inclut une licence pour Windows 10 Entreprise. Pour migrer vos appareils qui exécutent Windows 7 ou Windows 8.1, vous pouvez effectuer une mise à niveau sur place. La prise en charge de Windows 7 a pris fin le *14 janvier 2020*. 

Pour obtenir des méthodes supplémentaires d’installation de Windows 10 Entreprise au-delà d’une mise à niveau sur place, consultez [Windows 10 scénarios de déploiement](/windows/deployment/windows-10-deployment-scenarios). Vous pouvez également [planifier le déploiement de Windows 10](/windows/deployment/planning/) par vous-même.

## <a name="migrating-to-microsoft-365-apps-for-enterprise"></a>Migration vers Applications Microsoft 365 pour les grandes entreprises

Microsoft 365 pour entreprise inclut Applications Microsoft 365 pour les grandes entreprises, une version des produits clients Office (Word, PowerPoint, Excel et Outlook) installés et mis à jour à partir du cloud Microsoft. Pour plus d’informations, consultez [À propos de Applications Microsoft 365 pour les grandes entreprises](/deployoffice/about-microsoft-365-apps).

Plutôt que de maintenir vos ordinateurs à jour pour Office 2019 ou les versions antérieures, procédez comme suit :

1. Obtenez et attribuez une licence Microsoft 365 pour vos utilisateurs.
2. Désinstallez Office 2013 ou Office 2016 sur leurs ordinateurs.
3. Installez Applications Microsoft 365 pour les grandes entreprises, individuellement ou pendant un déploiement informatique. Pour plus d’informations, consultez le [Guide de déploiement de Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Applications Microsoft 365 pour les grandes entreprises installe automatiquement les mises à jour de sécurité et les nouvelles fonctionnalités et peut tirer parti des services cloud de Microsoft 365 pour améliorer la sécurité et la productivité.

## <a name="migrating-on-premises-servers-and-data-to-microsoft-365"></a>Migration de serveurs et de données locaux vers Microsoft 365

Microsoft 365 pour entreprise inclut des versions cloud des services serveur Office qui utilisent certains des mêmes outils que les versions locales du logiciel serveur Office, telles que les navigateurs web et le client Outlook. Ces services cloud sont automatiquement mis à jour pour des raisons de sécurité et de nouvelles fonctionnalités. Après la migration, votre service informatique peut gagner du temps pour gérer et mettre à jour des serveurs locaux.

Utilisez les ressources suivantes pour plus d’informations sur la migration des utilisateurs et des données pour des charges de travail Microsoft 365 spécifiques :

- [Déplacer des boîtes aux lettres d’Exchange Server locales vers Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Migrer des données SharePoint de SharePoint Server vers SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Migrer Skype Entreprise Online vers Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

## <a name="transition-your-entire-organization"></a>Transition de l'ensemble de votre organisation

Pour obtenir une meilleure image de la façon de déplacer l’ensemble de votre organisation vers les produits et services dans Microsoft 365 pour les entreprises, téléchargez cette affiche de transition :

[![Image montrant l’affiche Transition vers Microsoft 365.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Cette affiche de deux pages est un moyen rapide d'inventorier vos infrastructures existantes. Utilisez-le pour obtenir des conseils pour passer à un produit ou un service dans Microsoft 365 pour les entreprises. Il présente les produits Windows et Office, ainsi que d’autres éléments d’infrastructure et de sécurité tels que la gestion des appareils, la protection des identités et des menaces, ainsi que la protection et la conformité des informations.

## <a name="results-of-step-4"></a>Résultats de l’étape 4

Pour la migration de votre locataire Microsoft 365, vous avez déterminé :

- Les appareils qui exécutent Windows 7 ou Windows 8.1 et le plan de mise à jour vers Windows 10 Entreprise.
- Les appareils qui exécutent les applications clientes Office et le plan de mise à jour vers les applications Microsoft 365 pour les entreprises.
- Quels services serveur Office locaux doivent être migrés vers leur équivalent Microsoft 365 et le plan pour les migrer, ainsi que leurs données.

Voici un exemple de locataire avec une migration terminée de serveurs locaux.

![Exemple de locataire avec une migration terminée de serveurs locaux.](../media/tenant-management-overview/tenant-management-tenant-build-step4.png)

Dans cette illustration, l’organisation a :

- Migré ses boîtes aux lettres Exchange Server locales vers Exchange Online.
- Migré ses sites et données SharePoint Server locaux vers SharePoint dans Microsoft 365.

## <a name="ongoing-maintenance-for-migration"></a>Maintenance en cours pour la migration

De façon continue, vous devrez peut-être :

- En fonction de l’état de la migration de votre boîte aux lettres Exchange, continuez à effectuer la transition vers Exchange Online vers votre organisation.
- Selon l’état de la migration de votre site SharePoint local, poursuivez la transition vers SharePoint dans Microsoft 365 vers votre organisation.

## <a name="next-step"></a>Étape suivante

[![Étape 5. Déployez la gestion des appareils et des applications.](../media/tenant-management-overview/tenant-management-step-grid-device-mgmt.png)](tenant-management-device-management.md)

Poursuivez avec [la gestion des appareils et des applications](tenant-management-device-management.md) pour déployer la gestion des appareils et des applications.