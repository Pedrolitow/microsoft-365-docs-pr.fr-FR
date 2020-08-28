---
title: Contrôle des applications
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
audience: ITpro
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 32ed3f95ebb4299796c5ad3eb71802c949701b65
ms.sourcegitcommit: abf63669daf12993ad3353e4b578f41c8910b20f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2020
ms.locfileid: "47289126"
---
# <a name="app-control"></a>Contrôle des applications

Le contrôle d’application est une pratique de sécurité facultative dans Microsoft Managed Desktop qui limite l’exécution du code sur les appareils clients. Ce contrôle réduit le risque de programmes malveillants ou de scripts malveillants en exigeant que seul le code signé par une liste d’éditeurs approuvés par le client puisse s’exécuter. Ce contrôle présente de nombreux avantages en matière de sécurité, mais il vise principalement à protéger les données et l’identité des attaques basées sur les clients.

Microsoft Managed Desktop simplifie la gestion des stratégies de contrôle d’application en créant une stratégie de base qui active les scénarios de productivité principaux. Vous pouvez étendre l’approbation à des signataires supplémentaires spécifiques aux applications et aux scripts de votre environnement. 


Toute technologie de sécurité nécessite un équilibre entre l’expérience utilisateur, la sécurité et les coûts. Le contrôle d’application réduit la menace de logiciels malveillants dans votre environnement, mais il y a des conséquences pour l’utilisateur et des actions supplémentaires pour votre administrateur informatique.

**Sécurité supplémentaire :**

Les applications ou les scripts qui ne sont pas approuvés par la stratégie de contrôle d’application ne sont pas exécutés sur les appareils.

**Vos responsabilités supplémentaires :**

- Vous êtes chargé de tester vos applications afin de déterminer si elles seraient bloquées par la stratégie de contrôle d’application.
- Si une application est bloquée (ou serait), vous devez identifier les informations de signataire nécessaires et demander une modification via le portail d’administration.

**Responsabilités du bureau géré Microsoft :**

- Microsoft Managed Desktop gère la stratégie de base qui permet les principaux produits Microsoft tels que les applications M365, Windows, teams, OneDrive, etc.
- Le bureau géré Microsoft insère vos signataires approuvés et déploie la stratégie mise à jour sur vos appareils.


## <a name="managing-trust-in-applications"></a>Gestion de l’approbation dans les applications

Microsoft Managed Desktop organise une stratégie de base qui approuve les principaux composants des technologies Microsoft. Vous pouvez ensuite *Ajouter* une approbation pour vos propres applications et scripts en informant le bureau géré Microsoft, dont vous avez déjà confiance.

### <a name="base-policy"></a>Stratégie de base

Microsoft Managed Desktop, en collaboration avec les experts Microsoft Cybersecurity, crée et gère une stratégie standard qui permet le déploiement de la plupart des applications déployées via Microsoft Intune tout en bloquant les activités dangereuses telles que la compilation du code ou l’exécution de fichiers non approuvés.

La stratégie de base adopte l’approche suivante pour limiter l’exécution des logiciels :

- Les fichiers exécutés par les administrateurs sont autorisés à s’exécuter.
- Les fichiers dans les emplacements qui *ne sont pas* dans les répertoires accessibles par l’utilisateur sont autorisés à s’exécuter.
- Les fichiers sont signés par un [signataire approuvé](#signer-requests).
- La plupart des fichiers signés par Microsoft s’exécuteront, mais certains sont bloqués pour empêcher les actions à haut risque telles que la compilation du code.


Si un utilisateur autre qu’un administrateur peut avoir ajouté une application ou un script à un périphérique (c’est-à-dire s’il se trouve dans un répertoire accessible aux utilisateurs), nous ne l’autorisons pas à s’exécuter, sauf s’il a déjà été spécifiquement autorisé par un administrateur. Si un utilisateur est amené à essayer d’installer des programmes malveillants, si une vulnérabilité dans une application exécutée par l’utilisateur tente de procéder à des tentatives d’installation de programmes malveillants, ou si un utilisateur tente intentionnellement d’exécuter une application ou un script non autorisé, notre stratégie arrête l’exécution.

### <a name="signer-requests"></a>Demandes de signataires

Vous nous indiquez quelles applications sont fournies par des fournisseurs de logiciels que vous approuvez en *désignant une demande de signataire*. En procédant ainsi, nous ajoutons ces informations d’approbation dans la stratégie de contrôle d’application de référence et autorisons tout logiciel signé avec le certificat de cet éditeur à s’exécuter sur vos appareils.

## <a name="audit-and-enforced-policies"></a>Stratégies d’audit et appliquées

Microsoft Managed Desktop utilise deux stratégies Microsoft Intune pour fournir le contrôle de l’application :

### <a name="audit-policy"></a>Stratégie d’audit
Cette stratégie crée des journaux pour enregistrer le blocage ou non d’une application ou d’un script par la stratégie appliquée. Les stratégies d’audit n’appliquent pas de règles de contrôle d’application et sont destinées à des fins de test pour déterminer si une application requiert une exemption de publication. Il consigne les avertissements (événements 8003 ou 8006) dans l’observateur d’événements au lieu de bloquer l’exécution ou l’installation d’applications ou de scripts spécifiés.

### <a name="enforced-policy"></a>Stratégie appliquée
Cette stratégie empêche les applications et les scripts non approuvés de s’exécuter et crée des journaux chaque fois qu’une application ou un script est bloqué. Les stratégies appliquées empêchent les utilisateurs standard d’exécuter des applications ou des scripts stockés dans des répertoires accessibles par l’utilisateur.

Les périphériques du groupe de test ont une stratégie d’audit appliquée afin que vous puissiez les utiliser pour vérifier si des applications génèrent des problèmes. Tous les autres groupes (First, Fast et large) utilisent une stratégie appliquée, de sorte que les utilisateurs de ces groupes ne puissent pas exécuter des applications ou des scripts non approuvés.







