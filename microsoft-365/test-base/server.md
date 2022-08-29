---
title: Test d’application Windows Server
description: Comment valider avec les tests d’application windows server
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
ms.openlocfilehash: 5d111b680105628ab1351a2cc45eeba01c41aa68
ms.sourcegitcommit: eb81b49205cbc66b021326b8e2c00a8336b4a2fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/11/2022
ms.locfileid: "67316005"
---
# <a name="windows-server-application-testing"></a>Test d’application Windows Server

Avec la base de test pour Microsoft 365, vous pouvez désormais valider vos applications par rapport à Windows Server 2016 et 2019, y compris Server Core !

Pour commencer à valider vos applications chargées par rapport aux mises à jour préversion pour les systèmes d’exploitation Windows Server 2016 et 2019 sur la base de test pour Microsoft 365, procédez comme suit :

1. Connectez-vous à notre portail d’intégration en libre-service. Dans le menu de navigation de gauche, sélectionnez `Upload new package` sous `Package catalogue` et renseignez les détails du test.

2. Sélectionnez `Security updates` le type de mise à jour du système d’exploitation :

   ![Sélectionnez mises à jour de sécurité.](Media/selecting-security-updates.png)

3. Sous versions du système d’exploitation à tester, sélectionnez les versions de système d’exploitation applicables. Vous pouvez sélectionner les versions du système d’exploitation Windows Server ou une combinaison de versions de système d’exploitation serveur et client.

   ![Sélectionnez la version du système d’exploitation.](Media/selecting-OS-versions.png)

4. Fournissez d’autres informations requises, passez en revue les détails fournis et chargez votre package d’application. Après le chargement, vous pouvez afficher l’état du package sous l’onglet de menu Gérer les packages.

5. Pour afficher les résultats des tests et les insights de la validation de votre application par rapport aux mises à jour de sécurité en préversion pour Windows Server 2016 et 2019, accédez à la page résumé des tests ou à la page des résultats de la mise à jour de sécurité.

   ![Afficher les résultats des tests.](Media/access-test-results.png)

Passer à l’article suivant pour bien démarrer avec les **tests fonctionnels**
> [!div class="nextstepaction"]
> [Étape suivante](functional.md)
