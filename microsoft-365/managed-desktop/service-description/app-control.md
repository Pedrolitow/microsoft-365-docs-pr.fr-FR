---
title: Contrôle des applications
description: Comment utiliser le contrôle d’application et la relation d’confiance avec les applications
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 108c4d3d64f503d2221aed9df9724faee85b2998
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825468"
---
# <a name="app-control"></a>Contrôle des applications

Le contrôle d’application est une pratique de sécurité facultative Microsoft Manged Desktop qui limite l’exécution du code sur les appareils clients.

Ce contrôle atténue les risques de programmes malveillants ou de scripts malveillants. Le contrôle requiert que seuls les codes signés par une liste d’éditeurs approuvés par le client peuvent s’exécuter. Ce contrôle a de nombreux avantages en matière de sécurité, mais il vise principalement à protéger les données et l’identité contre les exploitations basées sur le client.

Microsoft Manged Desktop simplifie la gestion des stratégies de contrôle des applications en créant une stratégie de base qui permet des scénarios de productivité principaux. Vous pouvez étendre la confiance à d’autres signataires spécifiques aux applications et aux scripts de votre environnement.

Toute technologie de sécurité nécessite un équilibre entre l’expérience utilisateur, la sécurité et les coûts. Le contrôle d’application réduit les menaces de logiciels malveillants dans votre environnement, mais il en a des conséquences pour l’utilisateur et d’autres actions pour votre administrateur informatique.

| Sécurité et responsabilités supplémentaires | Description |
| ------ | ------ |
| Sécurité supplémentaire | L’exécution des applications ou des scripts non fiables par la stratégie de contrôle d’application est bloquée sur les appareils. |
| Vos responsabilités supplémentaires | <ul><li>Vous êtes responsable du test de vos applications pour déterminer si elles seraient bloquées par la stratégie de contrôle d’application.</li><li>Si une application est (ou serait) bloquée, vous êtes responsable de l’identification des détails requis du signataire. Vous devez demander une modification via le portail d’administration.</li></ul>
| Microsoft Manged Desktop responsabilités | <ul><li>Microsoft Manged Desktop maintient la stratégie de base qui active les principaux produits Microsoft tels que Microsoft 365 Apps, Windows, Teams, OneDrive, etc.</li><li>Microsoft Manged Desktop insère vos signataires de confiance et déploie la stratégie mise à jour sur vos appareils.</li></ul>

## <a name="managing-trust-in-applications"></a>Gestion de l’confiance dans les applications

Microsoft Manged Desktop une stratégie de base qui fait confiance aux principaux composants des technologies Microsoft. Vous *ajoutez ensuite l’confiance* pour vos propres applications et scripts en Microsoft Manged Desktop les applications et les scripts que vous avez déjà confiance.

### <a name="base-policy"></a>Stratégie de base

Microsoft Manged Desktop, en collaboration avec des experts en cybersécurité Microsoft, crée et maintient une stratégie standard. Cette stratégie standard :

- Active la plupart des applications déployées via Microsoft Intune.
- Bloque les activités dangereuses telles que la compilation de code ou l’exécution de fichiers nontrus.

La stratégie de base prend l’approche suivante pour restreindre l’exécution des logiciels :

- Les fichiers exécutés par les administrateurs seront autorisés à s’exécuter.
- Les fichiers des emplacements qui ne *sont* pas accessibles en création par l’utilisateur sont autorisés à s’exécuter.
- Les fichiers sont signés par un signataire [approuvé](#signer-requests).
- La plupart des fichiers signés par Microsoft s’exécutent, mais certains d’entre eux sont bloqués pour empêcher les actions à haut risque telles que la compilation du code.

Si un utilisateur, autre qu’un administrateur, aurait pu ajouter une application ou un script à un appareil (c’est-à-dire, dans un répertoire accessible en écriture par l’utilisateur), nous ne l’autoriserons pas à s’exécuter. Nous autoriserons l’exécution si l’application ou le script a déjà été autorisé par un administrateur.

Notre stratégie arrête l’exécution des applications dans les scénarios suivants :

- Si un utilisateur est tenté d’installer un programme malveillant.
- En cas de vulnérabilité dans une application, l’utilisateur tente d’installer un programme malveillant.
- Si un utilisateur tente intentionnellement d’exécuter une application ou un script non autorisé.

### <a name="signer-requests"></a>Demandes des signataires

Vous nous informez des applications fournies par les éditeurs de logiciels que vous faites confiance en classant une demande *de signataire*. En ce faisant, nous :

- Ajoutez ces informations d’confiance à la stratégie de contrôle d’application de référence.
- Autorisez les logiciels signés avec le certificat de cet éditeur à s’exécuter sur vos appareils.

## <a name="audit-and-enforced-policies"></a>Stratégies d’audit et appliquées

Microsoft Manged Desktop utilise Microsoft Intune stratégies pour fournir un contrôle d’application :

### <a name="audit-policy"></a>Stratégie d’audit

Cette stratégie crée des journaux pour enregistrer si une application ou un script est bloqué par la stratégie Appliquée.

Les stratégies d’audit n’appliquent pas les règles de contrôle d’application. Elles sont destinées à des fins de test afin d’identifier si une application nécessitera une exemption d’éditeur. Il enregistre les avertissements (événements 8003 ou 8006) dans l’Observateur d’événements au lieu de bloquer l’exécution ou l’installation d’applications ou de scripts spécifiés.

### <a name="enforced-policy"></a>Stratégie appliquée

Cette stratégie empêche l’exécution d’applications et de scripts non confiances et crée des journaux chaque fois qu’une application ou un script est bloqué. Les stratégies appliquées empêchent les utilisateurs standard d’exécuter des applications ou des scripts stockés dans des répertoires accessibles en écriture par l’utilisateur.

Une stratégie d’audit est appliquée aux appareils du groupe test pour vérifier si des applications provoqueront des problèmes. Tous les autres groupes (First, Fast et Broad) utilisent une stratégie appliquée. Les utilisateurs de ces groupes ne pourront pas exécuter d’applications ou de scripts non confiance.
