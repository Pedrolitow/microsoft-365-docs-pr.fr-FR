---
title: Vue d’ensemble des fonctionnalités protection évolutive des points de terminaison
ms.reviewer: ''
description: En savoir plus sur les fonctionnalités de protection évolutive des points de terminaison dans Microsoft Defender pour point de terminaison
keywords: Microsoft Defender pour point de terminaison, protection évolutive des points de terminaison, réponse, détection, cybersécurité, protection
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 78f05c9e366d2f8b4d5b4d7697961f0d702581f8
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438523"
---
# <a name="overview-of-endpoint-detection-and-response"></a>Vue d’ensemble de la détection et de la réponse des points de terminaison

**S’applique à :**
- [Plans 1 et 2 de Microsoft Defender pour points de terminaison](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Les fonctionnalités de protection évolutive des points de terminaison defender pour point de terminaison fournissent des détections d’attaque avancées qui sont quasiment en temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces.

Lorsqu’une menace est détectée, les alertes sont créées dans le système à des fins d’analyse par un analyste. Les alertes présentant les mêmes techniques d’attaque ou attribuées au même agresseur sont regroupées dans une entité appelée _incident_. Ce regroupement d’alertes permet plus facilement aux analystes d’étudier les menaces collectivement et d’y répondre.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

> [!IMPORTANT]
> [Defender pour point de terminaison Plan 1](defender-endpoint-plan-1.md) et [Microsoft Defender pour les PME](../defender-business/mdb-overview.md) inclure uniquement les actions de réponse manuelle suivantes :
> - Exécuter une analyse antivirus
> - Isoler l’appareil
> - Arrêter et mettre en quarantaine un fichier
> - Ajouter un indicateur pour bloquer ou autoriser un fichier

Inspiré par la mentalité de « violation supposée », Defender pour point de terminaison collecte en permanence les données de cybermétrie comportementales. Cela englobe les informations des processus, les activités réseau, l’inspection approfondie du noyau et du gestionnaire de mémoire, les activités de connexion utilisateur, les modifications du Registre et du système de fichiers, etc. Les informations sont conservées pendant six mois, ce qui permet à un analyste de remonter au début d’une attaque. Il peut alors analyser différents axes et adopter une approche d’investigation via plusieurs vecteurs.

Les fonctionnalités de réponse vous offrent la possibilité de remédier rapidement aux menaces en agissant sur les entités affectées.

## <a name="related-topics"></a>Voir aussi

- [Tableau de bord des opérations de sécurité](security-operations-dashboard.md)
- [File d’attente des incidents](view-incidents-queue.md)
- [File d’attente des alertes](alerts-queue.md)
- [Liste des appareils](machines-view-overview.md)
