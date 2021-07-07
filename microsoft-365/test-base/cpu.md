---
title: Analyse de la régression du processeur
description: Comprendre les résultats et les mesures de régression pour la consommation du processeur
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
localization_priority: Normal
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: bc28c128902ae353fb35c3b6010856ade934a436
ms.sourcegitcommit: b0f464b6300e2977ed51395473a6b2e02b18fc9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2021
ms.locfileid: "53322718"
---
# <a name="intelligent-cpu-regression-analysis"></a>Analyse intelligente de la régression du processeur

L’utilisation du processeur peut indiquer si une application est affectée par une mise à jour du système d’exploitation. 

La Base de test pour Microsoft 365 fournit aux développeurs de logiciels un aperçu des régressions des performances du processeur qui se produisent lorsque leur application s’exécute sur différentes versions d’une mise à jour du système d’exploitation Windows à venir. 

Ces régressions du processeur permettent aux développeurs de détecter et de résoudre les problèmes d’application (et les échecs potentiels) avant le déploiement de la mise à jour du système d’exploitation à grande étendue, empêchant ainsi une mauvaise expérience pour l’utilisateur final.


### <a name="how-cpu-regression-analysis-works"></a>Fonctionnement de l’analyse de la régression du processeur ###

En tant qu’utilisateur de base de test, vous pouvez télécharger les fichiers binaires de votre application (dans un seul fichier .zip), ainsi que les scripts de test associés et sélectionner la version du système d’exploitation Windows par rapport à laquelle vous souhaitez tester votre application sur le portail de base de test sur Azure. 

Le service de base de test exécute ensuite les scripts de test et effectue l’analyse de régression **de l’UC.** 

Le service vérifie si l’utilisation du processeur pour l’application sur la version pré-publiée de la mise à jour du système d’exploitation cible est conforme à l’utilisation du processeur pour la version finale du système d’exploitation. 

L’utilisation du processeur n’est pas une comparaison comparable à 100 %, car les processus en cours d’exécution sur les deux versions du système d’exploitation peuvent ou ne pas correspondre exactement en raison de différentes versions du système d’exploitation . toutefois, l’analyse effectuée par la base de test peut vous montrer si l’utilisation du processeur pour votre application est impactée par une prochaine mise à jour du système d’exploitation et spécifiquement les processus qui ont régressé par rapport aux précédentes séries de tests.

Dans la capture instantanée ci-dessous, il existe deux version du système d’exploitation par rapport à laquelle les utilisations processeur sont comparées pour la même application. 
-   L’onglet Utilisation du processeur affiche respectivement les limites supérieure et inférieure de l’utilisation pour les deux sorties au 90e et au 10e centile. 
-   Les graphiques indiquent la série de temps d’utilisation du processeur ainsi que l’utilisation moyenne. 

Les clients peuvent désormais utiliser cette fonctionnalité pour déterminer si l’utilisation processeur de leur application est impactée par les mises à jour du système d’exploitation et plus précisément les processus qui ont régressé par rapport à leur exécution précédente.


![Analyse de la régression du processeur](Media/cpu-regression-analysis.jpg)

### <a name="relevant-process-identification"></a>Identification de processus pertinente ###

Ici, nous abordons comment identifier les processus régressés dans l’application. 

L’analyse de la régression des performances nécessite le suivi de différents types de compteurs de performance pour chaque processus exécuté sur une machine virtuelle pendant l’exécution du test. 

Cette analyse capture un grand nombre de variables pour un grand nombre de processus pour une application donnée. Tous les processus ne sont pas associés à une application ou à une application. Pour contourner ce problème, un algorithme de classement des informations mutuelle utilisant la probabilité et la théorie de l’information est appliqué pour déterminer les processus les plus pertinents pour une application donnée. 

Une application peut être considérée comme un type de variable aléatoire discrète tandis qu’un processus est considéré comme un autre type de variable aléatoire discrète. L’association des deux variables aléatoires est mesurée à l’aide de probabilités conditionnelles pour la pertinence. 

Les processus sont ensuite affichés dans l’ordre de leur pertinence pour chaque application. Vous pouvez également favori un sous-ensemble de processus qui peuvent être surveillés, par défaut, ainsi que des processus pertinents pour l’analyse de la régression du processeur. Une fois qu’une régression est détectée, vous pouvez télécharger la boîte à outils de l’analyseur de performances Windows et analyser les raisons de la régression des performances du processeur. 

L Windows Performance Analyzer prend le journal de suivi des événements (ETL) comme entrées et ces fichiers .etl sont disponibles dans les fichiers journaux téléchargeables pour les tests s’exécutent sur le portail. Si vous souhaitez en savoir plus sur le débogage des performances du processeur, consultez la documentation Windows Performance Analyzer.

