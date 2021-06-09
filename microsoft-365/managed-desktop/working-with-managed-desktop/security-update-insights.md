---
title: Perspectives sur la mise à jour de sécurité Windows
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b3b1f43217b3be285f20925065bf9710a38f9606
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52739796"
---
# <a name="windows-security-update-insights"></a>Perspectives sur la mise à jour de sécurité Windows
Cette vue fournit une vue d’ensemble de l’état des mises à jour de sécurité pour Bureau géré Microsoft appareils mobiles. 

Pour afficher les données d’utilisation, sélectionnez <strong>l Windows onglet Mises à jour de sécurité.</strong>

![Volet des mises à jour de sécurité Windows : graphiques à barres de l’état de l’appareil et de la version de mise à jour dans la colonne de gauche, mise à jour de l’avancement du déploiement dans la colonne centrale et pourcentage d’appareils actifs par groupe de déploiement, ainsi que le nombre de jours pris pour atteindre la cible de déploiement de 95 % dans la colonne de droite.](../../media/update-insights.jpg)

## <a name="device-status"></a>État de l’appareil

Pour que les appareils soient mis à jour par Windows Update, ils doivent être connectés à Internet et ne pas mettre en veille prolongée pendant au moins six heures, dont deux doivent être en continu. Bien qu’il soit possible qu’un appareil qui ne réponde pas à ces exigences soit mis à jour, les appareils qui les répondent ont la plus grande probabilité d’être mis à jour. 

Nous classons l’activité de l’appareil dans le contexte Windows mise à jour avec les termes ci-après :

- <strong>Actif :</strong> Appareils qui ont satisfait aux critères d’activité minimale (six heures, deux en continu) pour la dernière version de mise à jour de sécurité et qui ont été enregistrés avec Microsoft Intune au moins tous les cinq jours
- <strong>Synchronisé :</strong> Appareils qui ont été enregistrés avec Intune au cours des 28 derniers jours
- <strong>Synchronisation non synchronisée :</strong> Appareils qui <i>n’ont</i> pas été enregistrés avec Intune au cours des 28 derniers jours




## <a name="update-version-status"></a>Mettre à jour l’état de la version

Microsoft publie des mises à jour de sécurité tous les deux mardis du mois. Chaque version ajoute des mises à jour importantes pour les vulnérabilités de sécurité connues. Bureau géré Microsoft garantit que 95 % de ses appareils gérés sont mis à jour avec la dernière mise à jour de sécurité disponible tous les mois. Les mises à jour de sécurité sont parfois publiées à d’autres moments pour répondre de manière urgente aux nouvelles menaces. Bureau géré Microsoft déploie ces mises à jour de la même manière.

Nous classons l’état des versions de mise à jour de sécurité avec les termes ci-après :

- <strong>Actuel :</strong> Appareils exécutant la mise à jour publiée au cours du mois en cours
- <strong>Précédent :</strong> Appareils exécutant la mise à jour publiée le mois précédent
- <strong>Plus ancien :</strong> Appareils exécutant une mise à jour de sécurité publiée avant le mois précédent

Vous devriez voir peu <strong></strong> d’appareils dans la catégorie Plus ancienne , une population importante ou croissante indique probablement un problème d’ampleur que vous devez signaler à Bureau géré Microsoft afin que nous pouvons l’examiner.


## <a name="deployment-progress"></a>Progression du déploiement

Au début de chaque cycle de publication des mises à jour de sécurité, Bureau géré Microsoft prend un instantané de la population d’appareils et définit sa cible de déploiement à 95 % de cette population. La <strong>zone d’avancement</strong> du déploiement présente une tendance historique, mise à jour quotidiennement, qui suit la proximité du déploiement de mise à jour avec cette cible pour chaque version. Ce graphique affiche uniquement les appareils dont l’état est actif.

Vous pouvez afficher ces données pour les cycles de mise à jour précédents à l’aide du menu déroulant dans le coin supérieur droit. La période que vous sélectionnez dans ce menu s’applique à toutes les informations de la page entière.

Les <strong>appareils actifs mis</strong> à jour par zone de groupe de déploiement offrent une vue différente en affichant la progression de l’installation de la mise à jour pour chacun des groupes Bureau géré Microsoft déploiement.

Le <strong>nombre de jours pour atteindre</strong> la zone cible affiche le temps qu’il a fallu pour que 95 % du nombre total d’appareils soient mis à jour avec la mise à jour de sécurité actuelle. Pendant le déploiement, cette zone <strong></strong> affiche Toujours la mise à jour jusqu’à ce que la cible de 95 % soit atteinte pour la mise à jour sélectionnée.

## <a name="device-details-area"></a>Zone de détails de l’appareil

Le bas du tableau de bord est un tableau [](#device-status) affichant des informations détaillées sur vos appareils, notamment l’état de l’appareil et l’état de la version de mise [à jour.](#update-version-status) Vous pouvez effectuer une recherche dans cette liste ou la filtrer selon n’importe quelle valeur répertoriée.


![Tableau des détails de l’appareil montrant les colonnes pour le nom de l’appareil, l’utilisateur affecté, l’état de l’appareil, la version de mise à jour, la version du système d’exploitation et la date de la dernière synchronisation de l’appareil.](../../media/security-update-insights-device-table-sterile.png)
