---
title: Perspectives sur la mise à jour de sécurité Windows
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 772d1d52e977a067ff9bc3517de9cb2ae6c8c9a3
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47950366"
---
# <a name="windows-security-update-insights"></a>Perspectives sur la mise à jour de sécurité Windows
Cet affichage fournit une vue d’ensemble de l’état des mises à jour de sécurité pour vos appareils de bureau gérés par Microsoft. 

Pour afficher les données d’utilisation, sélectionnez l’onglet <strong>mises à jour de sécurité Windows</strong> .

![Volet mises à jour de sécurité Windows : graphiques à barres de l’état du périphérique et de la version de mise à jour dans la colonne de gauche, mise à jour de l’avancement du déploiement dans le temps dans le centre et pourcentage d’appareils actifs par groupe de déploiement, ainsi que le nombre de jours pris pour atteindre la cible de déploiement de 95% dans la colonne de droite.](../../media/update-insights.jpg)

## <a name="device-status"></a>État de l’appareil

Pour que les appareils soient mis à jour par Windows Update, ils doivent être connectés à Internet et ne pas être mis en veille prolongée pendant une durée minimale de six heures, dont deux doivent être continus. Tant qu’un appareil est connecté et qu’il n’est pas mis en veille prolongée, il est considéré comme étant « en cours d’utilisation ». Bien qu’il soit possible qu’un appareil qui ne répond pas à ces exigences soit mis à jour, les appareils qui les satisfont ont la plus grande probabilité d’être mis à jour. 

Nous catégoriserons l’activité de l’appareil dans le contexte de Windows Update selon les termes suivants :

- <strong>Actif :</strong> Appareils ayant satisfait aux critères d’utilisation minimaux (six heures, deux en continu) pour la version la plus récente de la mise à jour de sécurité et qui ont archivé avec Microsoft Intune au moins tous les cinq jours
- <strong>Synchronisés :</strong> Appareils ayant archivé avec Intune au cours des 28 derniers jours
- <strong>Désynchronisation :</strong> Appareils qui <i>n’ont pas</i> archivé avec Intune au cours des 28 derniers jours




## <a name="update-version-status"></a>Mettre à jour l’état de version

Microsoft publie les mises à jour de sécurité chaque deuxième mardi du mois. Chaque version ajoute des mises à jour importantes pour les failles de sécurité connues. Microsoft Managed Desktop garantit que 95% de ses appareils gérés sont mis à jour avec la dernière mise à jour de sécurité disponible tous les mois. Les mises à jour de sécurité sont parfois publiées à d’autres moments pour résoudre les nouvelles menaces de façon urgente. Microsoft Managed Desktop déploie ces mises à jour de la même manière.

Nous catégoriserons l’état des versions de mise à jour de sécurité avec les termes suivants :

- <strong>Actuel :</strong> Appareils qui exécutent la mise à jour publiée dans le mois en cours
- <strong>Précédent :</strong> Appareils exécutant la mise à jour publiée au cours du mois précédent
- <strong>Plus ancien :</strong> Périphériques exécutant une mise à jour de sécurité publiée avant le mois précédent

Vous devriez voir peu de périphériques dans l' <strong>ancienne</strong> catégorie--un grand nombre ou une population croissante indique probablement un problème système que vous devez signaler à Microsoft Managed Desktop afin que nous puissions examiner.


## <a name="deployment-progress"></a>Progression du déploiement

Au début de chaque cycle de publication des mises à jour de sécurité, le bureau géré Microsoft prend un instantané de la population du périphérique et définit sa cible de déploiement à 95% de ce remplissage. La zone de <strong>progression du déploiement</strong> affiche une tendance historique, mise à jour quotidiennement, qui effectue le suivi de la différence entre le déploiement de la mise à jour et la cible de cette cible pour chaque version. Ce graphique affiche uniquement les appareils dont le statut est actif.

Vous pouvez afficher ces données pour les cycles de mise à jour précédents à l’aide du menu déroulant dans le coin supérieur droit. La période que vous sélectionnez dans ce menu s’applique à toutes les informations sur la page entière.

La zone de <strong>groupe périphériques actifs mis à jour par le groupe de déploiement</strong> offre une vue différente en indiquant la progression de l’installation de la mise à jour pour chacun des groupes de déploiement de bureau géré Microsoft.

La zone des <strong>jours pour atteindre la cible</strong> affiche le temps nécessaire pour 95% du nombre total d’appareils à mettre à jour avec la mise à jour de sécurité actuelle. Lorsque le déploiement est en cours, cette zone affiche <strong>toujours la mise à jour</strong> jusqu’à ce que la cible 95% soit atteinte pour la mise à jour sélectionnée.

## <a name="device-details-area"></a>Zone Détails sur l’appareil

Le bas du tableau de bord contient des informations détaillées sur vos appareils, dont l’état de l' [appareil](#device-status) et l’état de la [version de mise à jour](#update-version-status). Vous pouvez effectuer une recherche dans cette liste ou la filtrer par n’importe quelle valeur répertoriée.


![Tableau détails de l’appareil avec des colonnes pour le nom de l’appareil, l’état de l’appareil affecté, l’état de la mise à jour, la version du système d’exploitation et la date de la dernière synchronisation de l’appareil.](../../media/security-update-insights-device-table-sterile.png)
