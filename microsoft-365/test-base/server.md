---
title: Windows Test d’application serveur
description: Procédure de validation avec les tests d’application windows server
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
ms.openlocfilehash: 38e20e1eae61236c35c6e4783702e8e87ec02e56
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53648698"
---
# <a name="windows-server-application-testing"></a>Windows Test des applications serveur

Avec Test Base for Microsoft 365, vous pouvez désormais valider vos applications par rapport à Windows Server 2016 2019, y compris Server Core !

Pour commencer à valider vos applications téléchargées par rapport aux mises à jour de pré-publication pour les systèmes d’exploitation Windows Server 2016 et 2019 sur la base de test pour Microsoft 365, respectez les étapes suivantes :

1. Connectez-vous à notre portail d’intégration en libre-service. Dans le menu de navigation de gauche, `Upload new package` sélectionnez sous `Package catalogue` et remplissez les détails du test.

2. Sélectionnez `Security updates` le type de mise à jour du système d’exploitation :

   ![Sélectionner les mises à jour de sécurité](Media/selecting-security-updates.png)

3. Sous les versions de système d’exploitation à tester, sélectionnez les versions de système d’exploitation applicables. Vous pouvez sélectionner Windows versions du système d’exploitation du serveur ou une combinaison de versions de serveur et de système d’exploitation client.

   ![Sélectionner la version du système d’exploitation](Media/selecting-OS-versions.png)

4. Fournissez d’autres informations requises, examinez les détails fournis et téléchargez votre package d’application. Après le chargement, vous pouvez afficher l’état du package sous l’onglet De menu Gérer les packages.

5. Pour afficher les résultats des tests et les informations de la validation de votre application par rapport aux mises à jour de sécurité pré-publiées pour Windows Server 2016 et 2019, consultez la page récapitulatif du test ou la page des résultats de la mise à jour de sécurité.

   ![Afficher les résultats des tests](Media/access-test-results.png)

Passer à l’article suivant pour commencer les tests **fonctionnels**
> [!div class="nextstepaction"]
> [Étape suivante](functional.md)
