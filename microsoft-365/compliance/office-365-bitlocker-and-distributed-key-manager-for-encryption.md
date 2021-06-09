---
title: BitLocker chiffrement
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Découvrez comment Office 365 le chiffrement BitLocker, ce qui réduit le risque de vol de données en raison de la perte ou du vol d’ordinateurs et de disques.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cc329a053544ba6cf1753ae07caac642546cad11
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44033622"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>BitLocker et Distributed Key Manager (DKM) pour le chiffrement

Les serveurs Microsoft utilisent BitLocker chiffrer les lecteurs de disque contenant les données client au repos au niveau du volume. BitLocker chiffrement est une fonctionnalité de protection des données intégrée à Windows. BitLocker est l’une des technologies utilisées pour se protéger contre les menaces en cas de défaillances dans d’autres processus ou contrôles (par exemple, le contrôle d’accès ou le recyclage du matériel) qui pourraient conduire à une personne à accéder physiquement aux disques contenant des données client. Dans ce cas, BitLocker risque de vol ou d’exposition de données en raison de la perte, du vol ou de la désaffectation inappropriée d’ordinateurs et de disques.

BitLocker est déployé avec le chiffrement 256 bits AES (Advanced Encryption Standard) sur les disques contenant des données client dans Exchange Online, SharePoint Online et Skype Entreprise. Les secteurs de disque sont chiffrés avec une clé de chiffrement de volume complet (FVEK), qui est chiffrée avec la clé principale de volume (VMK), qui est à son tour liée au module de plateforme approuvé (TPM) sur le serveur. Le VMK protège directement le FVEK et, par conséquent, la protection du VMK devient critique. La figure suivante illustre un exemple de la chaîne BitLocker protection de clé pour un serveur donné (dans ce cas, à l’aide d’Exchange Online serveur).

Le tableau suivant décrit la chaîne BitLocker de protection de clé pour un serveur donné (dans ce cas, un Exchange Online serveur).

| PROTECTEUR DE CLÉ | GRANULARITY | COMMENT GÉNÉRÉ ? | OÙ EST-IL STOCKÉ ? | PROTECTION |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| Clé externe AES 256 bits | Par serveur | BitLocker API | TPM ou secret-safe | Lockbox/Access Control |
|  |  |  | Registre du serveur de boîtes aux lettres | TPM chiffré |
| Mot de passe numérique à 48 chiffres | Par disque | BitLocker API | Active Directory | Lockbox/Access Control |
| Certificat X.509 en tant qu’agent de récupération de données (DRA) également appelé protecteur de clé publique | Environnement (par exemple, Exchange Online plusieurs) | Microsoft CA | Système de build | Aucun utilisateur n’a le mot de passe complet pour la clé privée. Le mot de passe est sous protection physique. |


BitLocker gestion des clés implique la gestion des clés de récupération utilisées pour déverrouiller/récupérer des disques chiffrés dans un centre de données Microsoft. Microsoft 365 stocke les clés principales dans un partage sécurisé, uniquement accessible aux personnes qui ont été filtrées et approuvées. Les informations d’identification des clés sont stockées dans un référentiel sécurisé pour les données de contrôle d’accès (ce que nous appelons un « magasin secret »), ce qui nécessite un niveau élevé d’approbations d’élévation et de gestion pour accéder à l’aide d’un outil d’élévation d’accès juste-à-temps.

BitLocker prend en charge les clés qui se trouvent dans deux catégories de gestion :

- Les clés gérées par BitLocker, qui sont généralement éphémères et liées à la durée de vie d’une instance de système d’exploitation installée sur un serveur ou sur un disque donné. Ces clés sont supprimées et réinitialisées pendant la réinstallation du serveur ou la mise en forme du disque.

- BitLocker de récupération, qui sont gérées en dehors des BitLocker mais utilisées pour le déchiffrement du disque. BitLocker utilise les clés de récupération pour le scénario dans lequel un système d’exploitation est réinstallé et les disques de données chiffrés existent déjà. Les clés de récupération sont également utilisées par les sondes de surveillance de la disponibilité gérée dans Exchange Online où un répondeur peut avoir besoin de déverrouiller un disque.

BitLocker volumes protégés sont chiffrés avec une clé de chiffrement de volume complète, qui est à son tour chiffrée avec une clé principale de volume. BitLocker utilise des algorithmes conformes à la norme FIPS pour s’assurer que les clés de chiffrement ne sont jamais stockées ou envoyées sur le réseau en clair. L’implémentation Microsoft 365 de la protection des données client au repos ne diffère pas de l’implémentation par défaut de BitLocker.
