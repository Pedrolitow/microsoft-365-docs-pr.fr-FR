---
title: Analyse de régression de l’UC
description: Présentation des résultats et des métriques de régression pour la consommation d’UC
search.appverid: MET150
author: mansipatel-usl
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: test-base
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: tinachen
f1.keywords: NOCSH
ms.openlocfilehash: 59038c1bd13299587ef0ed75f446e405ed64bba5
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67315874"
---
# <a name="intelligent-cpu-regression-analysis"></a>Analyse intelligente de la régression de l’UC

L’utilisation du processeur peut indiquer si une application est affectée par une mise à jour du système d’exploitation. 

La base de test pour Microsoft 365 fournit aux développeurs de logiciels un aperçu des régressions des performances de l’UC qui se produisent lorsque leur application s’exécute sur différentes versions d’une prochaine mise à jour du système d’exploitation Windows. 

Ces régressions de l’UC permettent aux développeurs de détecter et de résoudre les problèmes d’application (et les défaillances potentielles) avant le déploiement général de la mise à jour du système d’exploitation, évitant ainsi une mauvaise expérience pour l’utilisateur final.


### <a name="how-cpu-regression-analysis-works"></a>Fonctionnement de l’analyse de régression de l’UC ###

En tant qu’utilisateur de base de test, vous pouvez charger les fichiers binaires de votre application (dans un seul fichier .zip), ainsi que les scripts de test associés et sélectionner la version du système d’exploitation Windows sur laquelle vous souhaitez tester votre application sur le portail de base de test sur Azure. 

Le service De base de test exécute ensuite les scripts de test et effectue **l’analyse de régression de l’UC**. 

Le service vérifie si l’utilisation du processeur pour l’application sur la version préliminaire de la mise à jour du système d’exploitation cible est conforme à l’utilisation du processeur pour la version publiée du système d’exploitation. 

L’utilisation du processeur n’est pas une comparaison similaire à 100 %, car les processus qui s’exécutent sur les deux versions du système d’exploitation peuvent ou non correspondre exactement en raison de versions de système d’exploitation différentes ; Toutefois, l’analyse effectuée par Test Base peut vous montrer si l’utilisation du processeur pour votre application est affectée par une prochaine mise à jour du système d’exploitation et plus précisément par les processus qui ont régressé par rapport aux exécutions de test précédentes.

Dans l’instantané ci-dessous, il existe deux versions du système d’exploitation par rapport auxquelles les utilisations du processeur sont comparées pour la même application. 
-   L’onglet Utilisation du processeur affiche les limites supérieures et inférieures de l’utilisation pour les deux versions, respectivement au 90e et au 10e centiles. 
-   Les graphiques montrent les séries chronologiques d’utilisation de l’UC, ainsi que l’utilisation moyenne. 

Les clients peuvent désormais utiliser cette fonctionnalité pour déterminer si l’utilisation du processeur de leur application est affectée par les mises à jour du système d’exploitation et, plus précisément, les processus qui ont régressé par rapport à leur exécution précédente.


![Analyse de régression de l’UC.](Media/cpu-regression-analysis.jpg)

### <a name="relevant-process-identification"></a>Identification des processus pertinents ###

Ici, nous expliquons comment identifier les processus régressés dans l’application. 

L’analyse de la régression des performances nécessite le suivi de différents types de compteurs de performances pour chaque processus en cours d’exécution sur une machine virtuelle pendant la série de tests. 

Cette analyse capture un grand nombre de variables pour un grand nombre de processus pour une application donnée. Tous les processus ne sont pas associés à une exécution ou à une application. Pour contourner ce défi, un algorithme de classement des informations mutuelles utilisant la théorie des probabilités et des informations est appliqué pour déterminer les processus les plus pertinents pour une application donnée. 

Une application peut être considérée comme un type de variable aléatoire discrète, tandis qu’un processus est considéré comme un autre type de variable aléatoire discrète. L’association des deux variables aléatoires est mesurée à l’aide de probabilités conditionnelles pour la pertinence. 

Les processus sont ensuite affichés dans l’ordre de leur pertinence pour chaque application. Vous pouvez également favoriser un sous-ensemble de processus qui peuvent être surveillés, par défaut, ainsi que les processus pertinents pour l’analyse de régression de l’UC. Une fois qu’une régression est détectée, vous pouvez télécharger le kit de ressources Windows Analyseur de performances et analyser les raisons de régressions des performances de l’UC. 

Windows Analyseur de performances prend le journal de suivi des événements (ETL) comme entrées et ces fichiers .etl sont disponibles dans les fichiers journaux téléchargeables pour les exécutions de test sur le portail. Si vous souhaitez en savoir plus sur le débogage des performances de l’UC, consultez la documentation windows Analyseur de performances.

