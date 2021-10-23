---
title: Configurer Le nom d’une source de contenu pour Apprentissage Microsoft Viva
ms.author: daisyfeller
author: daisyfell
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 10/07/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: medium
description: Découvrez comment configurer Telle source de contenu d’apprentissage pour Apprentissage Microsoft Viva.
ROBOTS: NOINDEX
ms.openlocfilehash: 26af97604b071e621794937d45882c98fdef0d31
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556814"
---
# <a name="configure-saba-as-a-content-source-for-microsoft-viva-learning"></a>Configurer Le nom d’une source de contenu pour Apprentissage Microsoft Viva

Cet article vous montre comment configurer Lasa comme source de contenu d’apprentissage tierce pour Apprentissage Microsoft Viva. Pour effectuer ces étapes, vous devez être administrateur système ou super utilisateur du système.

>[!NOTE]
>Le contenu accessible par le biais de Learning est soumis à des conditions autres que celles de Microsoft Product Terms. Le contenu de Domaine et les services associés sont soumis aux conditions de confidentialité et de service de Saby.

## <a name="clients-host-url"></a>URL hôte du client

1. Identifiez votre URL cloud Principale (par exemple, « org ».sabacloud.com). Si l’URL du tableau de bord de votre API org-api.sabacloud.com, votre URL d’hôte sera org.sabacloud.com.

2. Identifiez l’URL de votre tableau de bord d’API en allant à **Cloud**  >  **Admin**  >  **System Admin Manage**  >  **Integrations** API  >  **Dashboard**. Recherchez l’URL du tableau de bord de l’API, puis supprimez « https:// » et « -api » pour obtenir votre URL d’hôte.

<!--![Image of the API dashboard.](../media/learning/saba-1.png)-->

## <a name="client-id-and-client-secret"></a>ID client et secret client

1. Sur le même écran que l’URL hôte, copiez l’ID client et la secret client s’ils ont déjà été générés.

2. Si la question secrète client n’existe pas encore, sélectionnez le **bouton GÉNÉRER** pour la générer.

    <!--![Image of the button to generate the Client secret.](../media/learning/saba-2.png)-->

## <a name="username-and-password"></a>Nom d'utilisateur et mot de passe

Fournissez le nom d’utilisateur et le mot de passe d’un compte d’administration pour Microsoft Viva à utiliser pour tirer des cours, des achèvements et des informations connexes à partir du Cloud Cloud De Cloud Cloud via l’API REST. Dans l’idéal, ce compte doit être un super utilisateur. Si le compte n’est pas un super utilisateur **Learning,** il doit au moins avoir des rôles Admin - Catalog Builder et **Human Capital Admin** (ou des rôles de sécurité personnalisés équivalents) dans Catalog.

## <a name="last-steps"></a>Dernières étapes

Vous devez terminer la configuration dans votre Centre d'administration Microsoft 365.

1. Connectez-vous à [votre Centre d'administration Microsoft 365](https://admin.microsoft.com).
2. Accédez **à Paramètres,** puis **aux paramètres org.** Sélectionnez Contrôle Learning et activez Cloud Dans le panneau.
3. Remplissez les détails que vous avez obtenus à partir de votre portail DeNte.
    >[!NOTE]
    >Le nom complet est le nom du carrousel sous lequel le contenu d’apprentissage de Contrôle apparaîtra pour les utilisateurs de votre organisation dans Le Learning. Si vous n’entrez pas de nouveau nom, il affiche le nom par défaut « Cloud Cloud ».

    <!--![Image of where you post configuration details in the admin center.](../media/learning/saba-3.png)-->

4. Sélectionnez **Enregistrer** pour activer le contenu Cloud de Cloud dans Apprentissage Microsoft Viva. L’affichage du contenu dans Le Learning peut prendre jusqu’à 24 heures.

> [!Note]
> Pour l’intégration de Cloud Cloud, vous devez avoir un domaine sabacloud.com dans votre URL d’hôte. Si vous avez un autre nom de domaine, vous devez lever un ticket de support pour autoriser votre nom de domaine.

## <a name="data-residency"></a>Résidence de données

Les métadonnées du client sont stockées de manière centralisée dans nos magasins de données et non dans des magasins de données spécifiques à la région.

## <a name="roles-and-permissions"></a>Rôles et autorisations

Actuellement, tous les utilisateurs au sein d’une organisation pourront découvrir tous les cours spécifiques au client. Toutefois, ils pourront uniquement utiliser les cours qui leur sont accessibles. La découverte de contenu propre à l’utilisateur (basée sur les rôles et les autorisations) est prévue pour être déployée à l’avenir.
