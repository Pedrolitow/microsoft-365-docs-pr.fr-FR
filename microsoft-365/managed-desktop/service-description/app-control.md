---
title: Contrôle des applications
description: Comment utiliser le contrôle d’application et la relation d’confiance avec les applications
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 6f5cc923b5a18b1f45dd186e88228db8c3a891cc
ms.sourcegitcommit: 83a40facd66e14343ad3ab72591cab9c41ce6ac0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "49841302"
---
# <a name="app-control"></a>Contrôle des applications

Le contrôle d’application est une pratique de sécurité facultative dans le Bureau géré Microsoft qui limite l’exécution du code sur les appareils clients. Ce contrôle atténue les risques de programmes malveillants ou de scripts malveillants en exigeant que seul le code signé par une liste d’éditeurs approuvés par le client puisse s’exécuter. Ce contrôle a de nombreux avantages en matière de sécurité, mais il vise principalement à protéger les données et l’identité contre les exploitations basées sur le client.

Bureau géré Microsoft simplifie la gestion des stratégies de contrôle des applications en créant une stratégie de base qui permet des scénarios de productivité principaux. Vous pouvez étendre la confiance à d’autres signataires spécifiques aux applications et aux scripts de votre environnement. 


Toute technologie de sécurité nécessite un équilibre entre l’expérience utilisateur, la sécurité et les coûts. Le contrôle d’application réduit les menaces de logiciels malveillants dans votre environnement, mais il en a des conséquences pour l’utilisateur et d’autres actions pour votre administrateur informatique.

**Sécurité supplémentaire :**

L’exécution des applications ou des scripts non fiables par la stratégie de contrôle d’application est bloquée sur les appareils.

**Vos responsabilités supplémentaires :**

- Vous êtes responsable du test de vos applications pour déterminer si elles seraient bloquées par la stratégie de contrôle d’application.
- Si une application est (ou serait) bloquée, vous êtes responsable de l’identification des détails nécessaires du signataire et de la demande de modification via le portail d’administration.

**Responsabilités du Bureau géré Microsoft :**

- Bureau géré Microsoft gère la stratégie de base qui active les principaux produits Microsoft tels que les applications M365, Windows, Teams, OneDrive, etc.
- Bureau géré Microsoft insère vos signataires de confiance et déploie la stratégie mise à jour sur vos appareils.


## <a name="managing-trust-in-applications"></a>Gestion de l’confiance dans les applications

Bureau géré Microsoft organise une stratégie de base qui fait confiance aux principaux composants des technologies Microsoft. Vous pouvez *ensuite ajouter* une relation d’confiance pour vos propres applications et scripts en informant Microsoft Managed Desktop des applications que vous avez déjà confiance.

### <a name="base-policy"></a>Stratégie de base

Bureau géré Microsoft, en collaboration avec des experts en cybersécurité Microsoft, crée et gère une stratégie standard qui permet à la plupart des applications déployées via Microsoft Intune de bloquer les activités dangereuses telles que la compilation de code ou l’exécution de fichiers non confiance.

La stratégie de base prend l’approche suivante pour restreindre l’exécution des logiciels :

- Les fichiers exécutés par les administrateurs seront autorisés à s’exécuter.
- Les fichiers des emplacements qui ne *sont* pas accessibles en création par l’utilisateur sont autorisés à s’exécuter.
- Les fichiers sont signés par un [signataire approuvé.](#signer-requests)
- La plupart des fichiers signés par Microsoft s’exécutent, mais certains d’entre eux sont bloqués pour empêcher les actions à haut risque telles que la compilation du code.


Si un utilisateur autre qu’un administrateur aurait pu ajouter une application ou un script à un appareil (c’est-à-dire, dans un répertoire accessible en écriture par l’utilisateur), nous ne l’autoriserons pas à s’exécuter, sauf s’il a déjà été spécifiquement autorisé par un administrateur. Si un utilisateur est tenté d’installer un programme malveillant, si une vulnérabilité dans une application l’utilisateur tente d’installer un programme malveillant, ou si un utilisateur tente intentionnellement d’exécuter une application ou un script non autorisé, notre stratégie arrête l’exécution.

### <a name="signer-requests"></a>Demandes des signataires

Vous nous informez des applications fournies par les éditeurs de logiciels que vous faites confiance en classant une demande *de signataire.* En ce faisant, nous ajoutons ces informations d’autorisation à la stratégie de contrôle d’application de référence et permettons à tout logiciel signé avec le certificat de cet éditeur de s’exécuter sur vos appareils.

## <a name="audit-and-enforced-policies"></a>Stratégies d’audit et appliquées

Bureau géré Microsoft utilise deux stratégies Microsoft Intune pour fournir un contrôle d’application :

### <a name="audit-policy"></a>Stratégie d’audit
Cette stratégie crée des journaux pour enregistrer si une application ou un script est bloqué par la stratégie Appliquée. Les stratégies d’audit n’appliquent pas de règles de contrôle d’application et sont destinées à des fins de test afin d’identifier si une application nécessitera une exemption d’éditeur. Il enregistre les avertissements (événements 8003 ou 8006) dans l’Observateur d’événements au lieu de bloquer l’exécution ou l’installation d’applications ou de scripts spécifiés.

### <a name="enforced-policy"></a>Stratégie appliquée
Cette stratégie empêche l’exécution d’applications et de scripts non confiances et crée des journaux chaque fois qu’une application ou un script est bloqué. Les stratégies appliquées empêchent les utilisateurs standard d’exécuter des applications ou des scripts stockés dans des répertoires accessibles en écriture par l’utilisateur.

Une stratégie d’audit est appliquée aux appareils du groupe test afin que vous pouvez les utiliser pour vérifier si des applications provoqueront des problèmes. Tous les autres groupes (First, Fast et Broad) utilisent une stratégie appliquée, afin que les utilisateurs de ces groupes ne puissent pas exécuter d’applications ou de scripts non confiance.







