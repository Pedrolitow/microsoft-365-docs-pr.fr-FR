---
title: Vue d’ensemble
description: Présentation de la base de test
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 13eaea1e62dd030f86e08d885ad743d673d6142c
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231690"
---
# <a name="what-is-test-base-for-microsoft-365"></a>Qu’est-ce que la base de test pour Microsoft 365 ?

Test Base est un service Azure qui permet des tests d’application pilotés par les données tout en fournissant à l’utilisateur l’accès à des tests intelligents à partir de n’importe où dans le monde.

Les entités suivantes sont encouragées à intégrer leurs applications, fichiers binaires et scripts de test sur la base de test pour Microsoft 365 service : éditeurs de logiciels indépendants (ISV), intégrateurs système (SIS) pour valider leurs applications et professionnels de l’informatique qui souhaitent valider leurs applications métier par le biais de l’intégration à Microsoft Intune.

## <a name="why-test-your-application-with-test-base"></a>Pourquoi tester votre application avec Test Base ?

La base de test pour Microsoft 365 service peut prendre en charge l’expansion de votre matrice de test si nécessaire afin que vous ayez confiance en l’intégrité, la compatibilité et la facilité d’utilisation de vos applications.

La base de test permet à votre application de continuer à fonctionner comme prévu, même si les dépendances de plateforme varient et que de nouvelles mises à jour sont appliquées par le service de mise à jour Windows. Avec la base de test, vous pouvez éviter l’aggravation, les engagements de temps prolongés et les dépenses liées à la configuration et à la maintenance d’un environnement de laboratoire complexe pour tester vos applications.

En outre, vous pouvez tester automatiquement la compatibilité avec les mises à jour de sécurité et de fonctionnalités pour Windows à l’aide de machines virtuelles sécurisées tout en obtenant l’accès à des informations de classe mondiale pour tester vos applications. Vous pouvez également tester la compatibilité de vos applications par rapport aux mises à jour de sécurité windows en préversion en envoyant une demande d’accès.

## <a name="how-does-test-base-work"></a>Comment fonctionne la base de test ?

Pour vous inscrire au service De base de test, consultez [Créer un compte de base de test](createAccount.md).

Une fois qu’un client s’est inscrit au service De base de test, il est simple de commencer à charger des packages d’application à des fins de test.

Après un chargement réussi, les packages sont testés sur Windows mises à jour en préversion.

Une fois les tests initiaux terminés, le client peut effectuer une exploration approfondie avec des insights sur les performances et l’analyse de régression pour détecter si les mises à jour de contenu préversion ont détérioré les performances de l’application de quelque manière que ce soit.

Toutefois, si le package a échoué à un test, le client peut également tirer parti de Informations de la mémoire ou des régressions de l’UC pour corriger l’échec, puis mettre à jour le package si nécessaire.

Avec la base de test, le client peut utiliser un emplacement unique pour gérer tous les packages testés, ce qui peut également faciliter le chargement et la mise à jour des packages pour générer de nouvelles versions d’application en fonction des besoins.

> [!NOTE]
> **Pour que les clients puissent tirer parti du contenu de mise à jour en préversion, ils doivent demander spécifiquement l’accès à celui-ci. Une fois votre demande d’accès aux mises à jour en préversion approuvée, vos packages chargés sont automatiquement planifiés pour être testés par rapport aux mises à jour Windows préversion pour les versions du système d’exploitation sélectionnées lors de l’intégration**.

Ensuite, à mesure que de nouvelles mises à jour Windows préversion deviennent disponibles, les packages d’application sont automatiquement testés avec le nouveau contenu en préversion. Par la suite, une série supplémentaire d’insights peut être nécessaire. Si les clients ne demandent pas spécifiquement l’accès, les packages d’application sont testés uniquement sur la version actuelle de Windows.

Une fois les packages testés avec succès, les clients peuvent les remettre à leurs clients logiciels et aux utilisateurs finaux avec confiance et l’assurance que Test Base a fait son travail.

## <a name="next-steps"></a>Étapes suivantes

Suivre le lien pour commencer
> [!div class="nextstepaction"]
> [Créer un compte de base de test | Microsoft Docs](createaccount.md)
