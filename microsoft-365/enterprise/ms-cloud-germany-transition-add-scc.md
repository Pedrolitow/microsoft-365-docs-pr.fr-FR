---
title: Informations sur l’expérience eDiscovery lors de la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: 'Résumé : Étapes de migration eDiscovery pour la migration à partir de Microsoft Cloud Deutschland.'
ms.openlocfilehash: d73a0bccf870999e63f9d05eaff796e7066a90240c45c7b93208fd715a0d2baa
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53795073"
---
# <a name="information-about-the-ediscovery-experience-during-the-migration-from-microsoft-cloud-deutschland"></a>Informations sur l’expérience eDiscovery lors de la migration à partir de Microsoft Cloud Deutschland
Les sections suivantes fournissent des informations supplémentaires sur l’expérience eDiscovery lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) à des services Office 365 dans la nouvelle région de centres de données allemands.

## <a name="ediscovery-administration-until-phase-4"></a>Administration eDiscovery jusqu’à la phase 4
Jusqu’à la phase 4, le Centre de sécurité et conformité sera entièrement disponible. Tout le contenu reste dans Microsoft Cloud Germany et est gérable par le Centre de sécurité et conformité Microsoft Cloud Germany ( https://protection.office.de/) .

## <a name="ediscovery-experience-between-phase-4-until-the-the-end-of-phase-9"></a>Expérience eDiscovery entre la phase 4 et la fin de la phase 9
Depuis le début de la phase 4 jusqu’à la fin de la phase 9, les recherches de découverte électronique échouent ou retournent 0 résultat pour les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés.

> [!NOTE]
> Pendant la migration, les clients peuvent continuer à créer des cas, des obligations, des recherches et des exportations dans le Centre de sécurité [&](/microsoft-365/compliance/manage-legal-investigations)conformité, y compris la recherche [de contenu.](/microsoft-365/compliance/search-for-content) Toutefois, les recherches sur les emplacements SharePoint Online, OneDrive Entreprise et Exchange Online qui ont été migrés retournent 0 résultat ou produisent une erreur.

Dans le cas où une recherche renvoie zéro résultat ou une erreur lors de la migration, veuillez effectuer l’action suivante pour SharePoint Online :

- Téléchargez les sites directement à partir du site SharePoint Online ou OneDrive Entreprise en suivant les instructions dans Télécharger des fichiers et des [dossiers](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05)à partir de OneDrive ou SharePoint . Cette méthode nécessite des autorisations SharePoint’administrateur en ligne ou des autorisations en lecture seule sur le site.
- Si les limites sont dépassées, comme expliqué dans télécharger des fichiers et des dossiers à partir de OneDrive ou [de SharePoint,](https://support.office.com/article/download-files-and-folders-from-onedrive-or-sharepoint-5c7397b7-19c7-4893-84fe-d02e8fa5df05)les clients peuvent utiliser le client de synchronisation OneDrive Entreprise en suivant les instructions des SharePoint de synchronisation et des fichiers [Teams](https://support.office.com/article/sync-sharepoint-files-with-the-new-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88)avec votre ordinateur.

- Pour plus d’informations, [voir Découverte électronique in-place dans Exchange Server](/Exchange/policy-and-compliance/ediscovery/ediscovery).


## <a name="ediscovery-administration-after-phase-9"></a>Administration eDiscovery après la phase 9

**S’applique à :** Tous les clients utilisant eDiscovery

À la phase 9, les étapes finales de déplacement vers la nouvelle région de centres de données allemande seront terminées. Dans cette phase, tous les composants de service restants seront migrés.
Après la phase 9, l’utilisation du Centre de sécurité et conformité dans Microsoft Cloud Germany (protection.office.de) n’est plus prise en charge. Utilisez plutôt le nouveau [Centre de sécurité](https://security.microsoft.com/) ou [centre](https://compliance.microsoft.com/) de conformité. Toutes les données ont été migrées vers les nouveaux portails d’administration.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
|  Tous SharePoint en ligne, OneDrive Entreprise et Exchange Online ont été migrés avec le Centre de sécurité et conformité (SCC). | Toute l’activité eDiscovery doit être exécuté à partir du client international. Les recherches seront désormais réussies à 100 %. Les défaillances ou erreurs doivent suivre les canaux de support normaux. | Aucun |
||||

### <a name="ediscovery-retention-policy"></a>Stratégie de rétention eDiscovery
**S’applique à :**  Tous les clients qui ont appliqué une stratégie de rétention dans le cadre des étapes préalables à la migration

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant les étapes préalables à la migration | Les clients peuvent supprimer les stratégies de rétention à l’échelle de l’organisation qui ont été créées pendant le travail préalable à la migration des clients. | Aucun |
||||
