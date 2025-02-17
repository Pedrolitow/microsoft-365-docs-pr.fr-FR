---
title: BitLocker pour le chiffrement
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- purview-compliance
- tier3
- Strat_O365_Enterprise
description: Découvrez comment Office 365 utilise le chiffrement BitLocker, ce qui réduit le risque de vol de données en raison de la perte ou du vol d’ordinateurs et de disques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d72040d4cac4b76637877482e18a025a160d2484
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68620654"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>BitLocker et Distributed Key Manager (DKM) pour le chiffrement

Les serveurs Microsoft utilisent BitLocker pour chiffrer les lecteurs de disque contenant les données client au repos au niveau du volume. Le chiffrement BitLocker est une fonctionnalité de protection des données intégrée à Windows. BitLocker est l’une des technologies utilisées pour se protéger contre les menaces en cas de défaillances dans d’autres processus ou contrôles (par exemple, le contrôle d’accès ou le recyclage du matériel) qui pourraient entraîner l’obtention d’un accès physique à des disques contenant des données client. Dans ce cas, BitLocker élimine le risque de vol ou d’exposition de données en raison de la perte, du vol ou de la désaffectation inappropriée des ordinateurs et des disques.

BitLocker est déployé avec le chiffrement AES (Advanced Encryption Standard) 256 bits sur les disques contenant des données client dans Exchange Online, SharePoint Online et Skype Entreprise. Les secteurs de disque sont chiffrés avec une clé de chiffrement en volume complète (FVEK), qui est chiffrée avec la clé principale de volume (VMK), qui à son tour est liée au module de plateforme sécurisée (TPM) du serveur. La machine virtuelle protège directement le FVEK et, par conséquent, la protection de la machine virtuelle devient critique. La figure suivante illustre un exemple de chaîne de protection de clé BitLocker pour un serveur donné (dans ce cas, à l’aide d’un serveur Exchange Online).

Le tableau suivant décrit la chaîne de protection de clé BitLocker pour un serveur donné (dans ce cas, un serveur Exchange Online).

| PROTECTEUR DE CLÉ | GRANULARITÉ | COMMENT GÉNÉRÉ ? | OÙ EST-IL STOCKÉ ? | PROTECTION |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| Clé externe AES 256 bits | Par serveur | API BitLocker | TPM ou Secret Safe | Lockbox / Access Control |
|  |  |  | Registre du serveur de boîtes aux lettres | TPM chiffré |
| Mot de passe numérique à 48 chiffres | Par disque | API BitLocker | Active Directory | Lockbox / Access Control |
| Certificat X.509 en tant qu’agent de récupération de données (DRA) également appelé protecteur de clé publique | Environnement (par exemple, Exchange Online mutualisé) | Autorité de certification Microsoft | Générer un système | Aucun utilisateur n’a le mot de passe complet de la clé privée. Le mot de passe est sous protection physique. |


La gestion des clés BitLocker implique la gestion des clés de récupération utilisées pour déverrouiller/récupérer des disques chiffrés dans un centre de données Microsoft. Microsoft 365 stocke les clés principales dans un partage sécurisé, uniquement accessible aux personnes qui ont été filtrées et approuvées. Les informations d’identification des clés sont stockées dans un référentiel sécurisé pour les données de contrôle d’accès (ce que nous appelons un « magasin secret »), ce qui nécessite un niveau élevé d’approbations d’élévation et de gestion pour accéder à l’aide d’un outil d’élévation d’accès juste-à-temps.

BitLocker prend en charge les clés qui se trouvent dans deux catégories de gestion :

- Les clés gérées par BitLocker, qui sont généralement éphémères et liées à la durée de vie d’une instance de système d’exploitation installée sur un serveur ou sur un disque donné. Ces clés sont supprimées et réinitialisées pendant la réinstallation du serveur ou la mise en forme du disque.

- Clés de récupération BitLocker, qui sont gérées en dehors de BitLocker, mais utilisées pour le déchiffrement de disque. BitLocker utilise les clés de récupération pour le scénario dans lequel un système d’exploitation est réinstallé et les disques de données chiffrés existent déjà. Les clés de récupération sont également utilisées par les sondes de surveillance de la disponibilité gérée dans Exchange Online où un répondeur peut avoir besoin de déverrouiller un disque.

Les volumes protégés par BitLocker sont chiffrés avec une clé de chiffrement de volume complète, qui à son tour est chiffrée avec une clé principale de volume. BitLocker utilise des algorithmes compatibles FIPS pour s’assurer que les clés de chiffrement ne sont jamais stockées ou envoyées sur le câble en clair. L’implémentation Microsoft 365 de la protection des données client au repos ne diffère pas de l’implémentation par défaut de BitLocker.
