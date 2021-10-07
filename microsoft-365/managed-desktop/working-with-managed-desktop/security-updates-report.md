---
title: Rapport des mises à jour de sécurité Windows
description: Explique les informations présentées dans ce rapport
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 747cfe06ef69703a9baf7bd360935c364b3c7832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213180"
---
# <a name="windows-security-updates-report"></a>Rapport des mises à jour de sécurité Windows

Ce rapport fournit une vue d’ensemble de l’avancement du déploiement d’une mise à jour Windows sécurité pour vos appareils Microsoft Manged Desktop données. Au début de chaque cycle de publication des mises à jour de sécurité, Microsoft Manged Desktop prend un instantané de tous les appareils dont l’état est **Actif** et définit sa cible de déploiement à 95 % de cette population. Le graphique indique l’avancement de votre déploiement pour une date de publication sélectionnée par rapport à la Microsoft Manged Desktop moyenne. Bien que nous nous concentrions sur la population active, vous pouvez également faire pivoter ce rapport pour afficher vos populations d’appareils **actives +** synchronisées et **non** synchronisées. Vous pouvez afficher l’avancement du déploiement pour les versions précédentes en modifiant les filtres disponibles, mais les détails au niveau de l’appareil sont disponibles uniquement pour la version actuelle. Les informations d’appareil consultables dans le tableau suivant le graphique sont également exportables pour l’analyse hors connexion.

:::image type="content" source="../../media/mmd-security-updates.png" alt-text="Rapport montrant la progression de l’installation de la mise à jour dans le temps en haut à gauche, filtre dans le coin supérieur droit avec un bouton pour générer le rapport et tableau des détails du rapport le long du bas":::

En règle générale, Microsoft publie des mises à jour de sécurité tous les deux mardis du mois, même si elles peuvent être publiées à d’autres moments lorsque cela est nécessaire. Chaque version ajoute des mises à jour importantes pour les vulnérabilités de sécurité connues. Microsoft Manged Desktop s’assure que 95 % de ses appareils actifs sont mis à jour avec la dernière mise à jour de sécurité disponible tous les mois. Lorsque des mises à jour de sécurité sont publiées à d’autres moments pour traiter de manière urgente de nouvelles menaces, Microsoft Manged Desktop déploie ces mises à jour de la même manière. Nous classons l’état des versions de mise à jour de sécurité avec les termes ci-après : 

- **Actuel**: appareils qui exécutent la mise à jour publiée au cours du mois en cours 
- **Précédent**: appareils exécutant la mise à jour publiée au cours du mois précédent 
- **Plus ancien**: appareils exécutant une mise à jour de sécurité publiée avant le mois précédent 

Il ne doit y avoir que quelques appareils dans la **catégorie Plus** ancien. Une population  plus ancienne ou plus importante indique probablement un problème d’ampleur que vous devez signaler à Microsoft Manged Desktop afin que nous pouvons l’examiner. 