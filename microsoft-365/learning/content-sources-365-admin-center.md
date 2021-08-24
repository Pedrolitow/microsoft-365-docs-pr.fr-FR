---
title: Configurer des sources de contenu d’apprentissage Apprentissage Microsoft Viva (prévisualisation) dans le Centre d’administration Microsoft 365
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: ''
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer des sources de contenu d’apprentissage pour Apprentissage Microsoft Viva (prévisualisation) dans le Centre d’administration Microsoft 365.
ms.openlocfilehash: 977589a9b9500f062edbd962ada895436c9b2c96
ms.sourcegitcommit: b05b107774e8bca36c9ee19fdc4719d17e302f11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2021
ms.locfileid: "58483378"
---
# <a name="configure-learning-content-sources-for-microsoft-viva-learning-preview-in-the-microsoft-365-admin-center"></a>Configurer des sources de contenu d’apprentissage Apprentissage Microsoft Viva (prévisualisation) dans le Centre d’administration Microsoft 365

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. 

Les administrateurs de l’Centre d’administration Microsoft 365, soit par eux-mêmes, soit en attribuant le rôle d’administrateur des connaissances à des personnes sélectionnées dans votre organisation, peuvent gérer les paramètres liés à La Learning (prévisualisation) et configurer les sources de contenu d’apprentissage.

L’administrateur sélectionne les autres sources de contenu d’apprentissage (par exemple, SharePoint ou les sources de fournisseurs de contenu tierces pris en charge) qui seront disponibles pour les utilisateurs de Learning (Prévisualisation). L’administrateur configure ensuite ces sources pour s’assurer que le contenu est disponible pour la recherche et la découverte et qu’il peut être consulté par les employés qui utilisent Le Learning (Prévisualisation).

> [!NOTE]
>  Les utilisateurs se connectent à des utilisateurs non-Microsoft et LinkedIn Learning Pro des connaissances dans un navigateur ou une visionneuse incorporée. Cette formation configurée est soumise aux termes distincts de licence, de confidentialité et de service entre votre organisation et le tiers, et non aux termes de l’Learning (prévisualisation). Avant de sélectionner ce type d’apprentissage, vérifiez que vous avez un contrat en place pour votre organisation et les utilisateurs.

## <a name="assign-the-knowledge-admin-role-optional"></a>Attribuer le rôle d’administrateur de connaissances (facultatif)

Vous devez être un administrateur Microsoft 365 général pour effectuer ces tâches.

> [!TIP]
> L’administrateur du savoir doit être modérément technique et avoir des informations d’identification d’administrateur SharePoint existantes, de préférence une personne qui connaît bien l’éducation, l’apprentissage, la formation ou l’expérience des employés dans l’organisation.

### <a name="add-a-knowledge-admin"></a>Ajouter un administrateur de connaissances

Pour ajouter un administrateur de connaissances à Learning (prévisualisation), suivez les étapes suivantes :

1. Dans le navigation gauche de la Centre d’administration Microsoft 365, allez à **Rôles**.

2. Dans la page **Rôles,** sous **l’onglet Azure AD,** sélectionnez **Administrateur de la connaissance.**
 
3. Dans le **panneau Administrateur des** connaissances, sélectionnez **Administrateurs affectés,** puis **ajoutez**.

     ![Page Rôles dans la Centre d’administration Microsoft 365 le panneau Administrateur de connaissances pour ajouter un utilisateur.](../media/learning/learning-add-knowledge-admin-1.png)

3. Dans le **panneau Ajouter des administrateurs,** sélectionnez la personne que vous choisissez pour le rôle, puis sélectionnez **Ajouter.**

     ![Page Rôles dans la Centre d’administration Microsoft 365 le panneau Ajouter des administrateurs pour ajouter un utilisateur.](../media/learning/learning-add-knowledge-admin-2.png)

### <a name="remove-a-knowledge-admin"></a>Supprimer un administrateur de connaissances

Pour supprimer un administrateur de connaissances pour Learning (prévisualisation), suivez les étapes suivantes :

1. Dans le navigation gauche de la Centre d’administration Microsoft 365, allez à **Rôles**.

2. Dans la page **Rôles,** sous **l’onglet Azure AD,** puis sélectionnez **Administrateur de connaissances.**
 
3. Dans le **panneau Administrateur des** connaissances, sous l’onglet **Administrateurs affectés,** sélectionnez **Supprimer,** puis sélectionnez la personne que vous souhaitez supprimer du rôle. Pour confirmer, sélectionnez **Supprimer.**

     ![Page Rôles dans la Centre d’administration Microsoft 365 le panneau Administrateurs affectés pour supprimer un utilisateur.](../media/learning/learning-remove-knowledge-admin-1.png)

## <a name="configure-settings-for-the-learning-content-sources"></a>Configurer les paramètres pour les sources de contenu d’apprentissage

Vous devez être administrateur général Microsoft 365 administrateur général ou administrateur du savoir pour effectuer ces tâches.

Pour configurer les paramètres des sources de contenu d’apprentissage dans Learning, suivez les étapes suivantes :

1. Dans le navigation de gauche de la Centre d’administration Microsoft 365, Paramètres  >  **paramètres de l’organisation.**

2. Dans la page **Paramètres de l’organisation,** sous l’onglet **Services,** **sélectionnez Learning (Aperçu).**

     ![Paramètres page du Centre d’administration Microsoft 365 affichant l’application Learning répertoriée.](../media/learning/learning-sharepoint-configure1.png)

3. Dans le **panneau Learning (Prévisualisation),** sélectionnez les sources de contenu d’apprentissage que vous souhaitez configurer pour l’organisation, puis sélectionnez **Enregistrer.**

     ![Learning panneau de la Centre d’administration Microsoft 365 des options de sources de contenu.](../media/learning/learning-sharepoint-configure2.png)

Parmi toutes les sources d’apprentissage existantes, certaines seront activées par défaut. Ces sources d’apprentissage sont les suivantes :

- LinkedIn Learning (contenu gratuit)
- Microsoft Learn
- Microsoft 365 Formation

> [!NOTE]
> Le contenu gratuit LinkedIn est fourni aux utilisateurs dans le cadre des politiques de confidentialité et du contrat utilisateur LinkedIn. LinkedIn recevra l’adresse IP de l’utilisateur, tous les cookies précédemment définies par LinkedIn, et définira un nouveau cookie pour suivre l’utilisation du contenu gratuit. Les utilisateurs n’ont pas besoin de se connecter avec LinkedIn pour recevoir du contenu gratuit.<br><br>
Pour le contenu Premium LinkedIn, votre organisation a besoin d’un abonnement pour que votre équipe accède à ce contenu. Les utilisateurs devront se connecter à LinkedIn pour accéder à cette formation, qui est fournie dans les conditions d’utilisation et les conditions de votre organisation avec LinkedIn.<br><br> Pour le contenu non-Microsoft (à l’exception du contenu LinkedIn gratuit), assurez-vous que votre organisation dispose d’un abonnement pour que vos utilisateurs accèdent à ce contenu à l’aide d’un compte de travail avant de le connecter à Learning (Prévisualisation). Les abonnements personnels des utilisateurs à des fournisseurs d’apprentissage non-Microsoft ne seront pas intégrés à l’Learning (Prévisualisation). Les utilisateurs se connectent à des utilisateurs non-Microsoft et LinkedIn Learning Pro des connaissances dans un navigateur ou une visionneuse incorporée. Si les utilisateurs naviguent vers du contenu dans lequel ils n’ont pas d’abonnement professionnel, ils peuvent voir une page de fournisseur dans laquelle ils peuvent s’inscrire à un abonnement individuel. Tous les apprentissages non-Microsoft sont fournis dans le cadre des termes du fournisseur non-Microsoft et non dans le cadre de Learning. 

Pour activer ou désactiver une source de contenu d’apprentissage, activez la case à cocher en regard de la source. Si une source est activée, une coche est visible.

## <a name="third-party-content-providers"></a>Fournisseurs de contenu tiers 

L’ensemble des fournisseurs d’apprentissage connectés disponibles peut changer à tout moment. D’autres fournisseurs rejoignent le programme au fil de l’expansion du programme. Les fournisseurs disponibles peuvent également choisir d’interrompre leur connexion avec Learning (Prévisualisation).

### <a name="skillsoft-as-a-content-source"></a>Skillsoft en tant que source de contenu  

Pour l’Learning De Domaine (Prévisualisation), les utilisateurs qui ont Activé Compétences et qui choisissent d’afficher du contenu Skillsoft seront redép[s] sur une page Percipio qui leur demande d’entrer le nom du site Percipio de votre organisation. Une fois que les utilisateurs ont indiqué le nom du site de votre organisation, ils sont dirigés vers la page pour se connecter au site Percipio de votre organisation. Les utilisateurs se connectent à l’aide de leurs informations d’identification existantes et voient le contenu qu’ils ont initialement sélectionné. Les utilisateurs ne seront invités à saisir le nom du site Percipio qu’une seule fois, jusqu’à ce que leur cache de navigateur soit effacé. Pour simplifier cette expérience pour vos utilisateurs, nous vous recommandons d’inclure votre nom de site Percipio dans les communications internes que vous envoyez à propos de Learning (prévisualisation).

Il s’agit d’une expérience temporaire pour la prévisualisation, et nous travaillons avec Skillsoft pour permettre une intégration propre au client pour la disponibilité générale, ce qui contournera l’étape qui oblige les utilisateurs à fournir le nom du site Percipio de votre organisation. 

### <a name="details-on-microsoft-substrate"></a>Détails sur le substrat Microsoft  

Pour les données que vous copiez dans Le Learning (Prévisualisation) à partir d’un service non-Microsoft (fournisseur d’apprentissage ou système de gestion de l’apprentissage), vous ne pouvez pas extraire, corriger ou supprimer directement ces données dans Le Learning de Contrôle d’apprentissage (Prévisualisation). Nous actualisons rapidement les données que vous importez à partir de fournisseurs non-Microsoft pour refléter les modifications et suppressions dans les données sources autres que Microsoft.

Vous devez travailler avec le fournisseur du service non-Microsoft pour accéder, corriger, supprimer ou extraire des données sous la licence, le service ou les conditions de confidentialité du service non-Microsoft. Les modifications apportées seront reflétées dans les données traitées pour votre utilisation dans Le Learning (Prévisualisation) à la fin des cycles de mise à jour des données du service non-Microsoft et de Learning (prévisualisation). Si vous dés désactiver la connexion entre Le Learning (Prévisualisation) et un service non-Microsoft, toutes les données que vous avez précédemment importées à partir de ce service seront supprimées. 

## <a name="next-step"></a>Étape suivante

[Configurer SharePoint comme source de contenu d’apprentissage pour Apprentissage Microsoft Viva (aperçu)](configure-sharepoint-content-source.md)