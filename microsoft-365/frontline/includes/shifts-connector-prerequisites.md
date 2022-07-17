---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: ab375a876eb62e5f41e5dd7cda3743d4010b95ff
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822436"
---
Avant de commencer, assurez-vous d'avoir les prérequis suivants :

- Blue Yonder WFM version 2020.3, 2021.1 ou 2021.2.

    > [!NOTE]
    > Si vous disposez de l'URL Blue Yonder WFM 2020.3 ou 2021.1, appliquez le correctif 2020.3.0.4 ou 2021.1.0.3. Ce correctif résout un problème où les utilisateurs reçoivent un message d'erreur persistant dans Shifts. Il résout également un problème qui empêche les utilisateurs de mettre à jour leur disponibilité dans Shifts.

- Le nom et le mot de passe de votre compte de service Blue Yonder WFM et les URL de service ::

    - URL d’authentification fédérée
    - URL d'authentification de cookie
    - URL de libre-service pour les employés
    - URL de l'API Web de vente au détail
    - URL de l’API du gestionnaire de site
    - URL de l’API d’administration

    Si vous ne disposez pas de ces informations, contactez le support Blue Yonder. Le compte est créé au niveau racine de l'entreprise par un administrateur d'entreprise Blue Yonder. Il doit disposer d'un accès API, d'un administrateur client et d'un accès Store Manager. Le compte et le mot de passe sont requis pour créer une connexion.
- L'authentification SSO fédérée est activée dans votre environnement Blue Yonder WFM. Contactez l'assistance Blue Yonder pour vous assurer que l'authentification unique fédérée est activée. Ils auront besoin des informations suivantes :

    - federatedSSOValidationService : `https://wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` où {tenantId} est votre client
     - proxyHeader : X-MS-AuthToken

- Au moins une équipe est configurée dans Teams.
- Vous avez ajouté votre compte système Microsoft 365 en tant que propriétaire d'équipe à toutes les équipes que vous souhaitez mapper.</br> [Créez ce compte dans Microsoft 365](/microsoft-365/admin/add-users/add-users) et attribuez-lui une licence Microsoft 365. Ensuite, ajoutez le compte en tant que propriétaire d'équipe à toutes les équipes que vous souhaitez mapper. Le connecteur Shifts utilise ce compte lors de la synchronisation des modifications Shifts à partir de Blue Yonder WFM.

    Nous vous recommandons de créer un compte spécifiquement à cet effet et de ne pas utiliser votre compte utilisateur.