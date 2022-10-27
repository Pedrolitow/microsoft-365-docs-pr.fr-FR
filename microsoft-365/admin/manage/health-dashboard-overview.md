---
title: Tableau de bord d’intégrité Microsoft 365
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
description: Obtenez une vue d’ensemble du tableau de bord Intégrité de Microsoft 365 et de son rôle pour vous tenir informé de l’intégrité de votre organisation Microsoft 365.
ms.openlocfilehash: 63537fc7b9f371062a020dd126d13988f1e5c3a1
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68731808"
---
# <a name="microsoft-365-health-dashboard"></a>Tableau de bord Intégrité Microsoft 365

En tant qu’administrateur de votre organisation, vous êtes chargé de maintenir le bon fonctionnement de nombreux services et applications avec un temps limité. Nous avons créé le tableau de bord Intégrité de Microsoft 365 pour vous aider à comprendre l’exécution des applications et des services dans votre organisation.

Le tableau de bord Intégrité est conçu pour vous donner un instantané de l’intégrité globale de votre environnement. Vous pouvez voir dans quelle mesure votre organisation maintient les logiciels de bureau à jour, en suivant les bonnes pratiques en matière de sécurité et en utilisant les produits et services pour lesquels vous avez payé.

> [!NOTE]
> Le tableau de bord Intégrité de Microsoft 365 est en préversion publique et n’est peut-être pas disponible pour tous les clients.

## <a name="health-dashboard-in-the-microsoft-365-admin-center"></a>Tableau de bord Intégrité dans le Centre d'administration Microsoft 365

1. Connectez-vous au Centre d’administration, puis accédez à l’URL suivante : https://admin.microsoft.com/AdminPortal/Home?#/healthoverview.

Vous devez être membre du rôle d’administrateur général ou de lecteur global pour accéder au tableau de bord d’intégrité.

:::image type="content" source="../../media/health-dashboard-view.png" alt-text="Tableau de bord d’état d’intégrité":::

En haut du tableau de bord, vous verrez des alertes critiques concernant les problèmes qui nécessitent votre attention.  Deux types de notifications s’affichent ici :

- Incidents de service général.

- Problèmes de facturation susceptibles d’entraîner des problèmes futurs, comme un abonnement expiré.

En l’absence d’alertes, une bannière verte vous indique que le tableau de bord d’intégrité n’a détecté aucun problème.

### <a name="service-health-and-usage"></a>État des services et utilisation

Au centre de la page, vous verrez l’état d’intégrité du service actuel de vos applications et services principaux. Il s’agit d’une vue sélectionnée des principaux produits. Si vous souhaitez afficher la liste de tous vos produits, vous pouvez suivre le lien pour afficher la liste complète. Cette section vous montre également l’utilisation quotidienne moyenne et une vue de l’utilisation des licences. Cela vous permet de comprendre comment les produits sont utilisés dans votre organisation.

:::image type="content" source="../../media/service-health-usage.png" alt-text="Capture d’écran : Intégrité et utilisation du service du tableau de bord d’intégrité":::

### <a name="microsoft-365-app-updates"></a>Mises à jour des applications Microsoft 365

Pour vous aider à vous tenir informé des mises à jour logicielles, cette section du tableau de bord vous indique en un coup d’œil si les applications de bureau Microsoft 365 comme Word, Excel et PowerPoint sont à jour. Si certains appareils ont pris du retard, vous verrez une liste d’appareils et de vulnérabilités pour vous aider à comprendre le risque. Ces informations sont alimentées par la page Software Mises à jour, à laquelle vous pouvez accéder pour plus d’informations.

:::image type="content" source="../../media/app-updates.png" alt-text="Capture d’écran : Informations de mise à jour de l’application du tableau de bord d’intégrité":::

### <a name="recommended-actions"></a>Actions recommandées

En bas du tableau de bord, vous verrez des recommandations sur ce que vous pouvez faire pour améliorer l’intégrité de votre organisation :

- **Activer l’authentification multifacteur** : consultez un résumé du nombre de comptes actuellement activés pour l’authentification multifacteur (MFA) et un lien vers l’Assistant Installation de l’authentification multifacteur.

- **Activer les mises à jour mensuelles pour Office** : vérifiez si la fréquence des mises à jour Office de votre organisation est définie afin que vous receviez des mises à jour plusieurs fois tous les six mois.

- **Partager la formation OneDrive** : encouragez les utilisateurs à stocker des fichiers dans OneDrive pour faciliter la récupération en cas de ransomware ou de défaillance d’appareil. Envoyez-leur une vue d’ensemble de la vidéo pour les aider à configurer et à utiliser OneDrive.

## <a name="note-for-microsoft-enterprise-customers"></a>Remarque pour les clients d’entreprise Microsoft

La version initiale du tableau de bord Intégrité se concentre sur les petites équipes informatiques, où il est courant qu’une seule personne gère Microsoft 365. Nous avons l’intention de faire évoluer le tableau de bord pour répondre aux besoins d’un plus grand nombre de rôles informatiques et d’organisations plus importantes au fil du temps.
