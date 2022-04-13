---
title: Intégrer Microsoft OneDrive LTI à Canvas
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Créez et classez des affectations, créez et organisez du contenu de cours, et collaborez sur des fichiers en temps réel avec la nouvelle application d’interopérabilité Microsoft OneDrive Learning Tools pour Canvas.
ms.openlocfilehash: 5de027c9d7606ebe546a8dc8e087b91da7f0400e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824561"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Intégrer Microsoft OneDrive LTI à Canvas

L’intégration de Microsoft OneDrive LTI à Canvas est un processus en deux étapes. La première étape active Microsoft OneDrive dans Canvas, et la deuxième étape rend le Microsoft OneDrive LTI disponible dans les cours Canvas.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être activés pour Microsoft OneDrive.
- Les fenêtres contextuelles ne doivent pas être bloquées pour Microsoft OneDrive.

> [!NOTE]
>
> - Les cookies ne sont pas activés par défaut dans le mode incognito du navigateur Chrome et doivent être activés.
> - Microsoft OneDrive LTI fonctionne en mode privé dans Microsoft Edge navigateur. Vérifiez que vous n’avez pas bloqué les cookies (qui sont activés par défaut).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Activer Microsoft OneDrive LTI dans Canvas

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être un administrateur de Canvas et un administrateur du locataire Microsoft 365.

1. Se connecter au <a href="https://onedrivelti.microsoft.com/admin" target="_blank">portail d’inscription Microsoft OneDrive LTI</a>
2. Sélectionnez le bouton **Consentement de l’administrateur** et acceptez les autorisations.

   > [!CAUTION]
   > Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur, et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous aurez obtenu l’erreur.

3. Sélectionnez le bouton **Créer un locataire LTI** . Dans la page Inscription LTI, sélectionnez **Canvas** dans la liste déroulante et entrez l’URL de base de votre instance canvas.

   > [!NOTE]
   > Si votre instance canvas est, par exemple, , `https://contoso.test.instructure.com`l’URL complète doit être entrée.

   :::image type="content" source="media/OneDrive-LTI-07.png" alt-text="La page d’administration du locataire LTI, avec un champ déroulant pour le choix de la plateforme grand public LTI et un champ de texte URL.":::

4. Copiez le JSON en sélectionnant le bouton **Copier** (icône à droite qui affiche deux pages l’une sur l’autre). Cette option sera utilisée pour générer la clé dans Canvas.

   :::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Image montrant le bouton Copier qui copie le texte JSON affiché et le rend disponible pour la génération de clé dans Canvas.":::

5. Connectez-vous à votre instance Canvas en tant qu’administrateur et sélectionnez **Clés** de développement dans le menu sur le côté gauche de la page. Dans la liste déroulante, créez une clé de développeur en choisissant **la clé LTI** dans la liste déroulante située en haut à droite de la page.

   :::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Capture d’écran montrant la barre de navigation de gauche avec les clés de développement sélectionnées et l’entrée de clé LTI sélectionnée dans une liste déroulante à droite de la page.":::

6. Dans la page Configurer, dans la liste déroulante **Méthode** , sélectionnez **Coller JSON** comme méthode et collez le texte JSON que vous avez copié à l’étape 4 dans le champ de texte qui s’affiche.

    > [!TIP]
    > **Étape facultative :** Si les enseignants de votre établissement scolaire souhaitent contrôler eux-mêmes les liens qui apparaissent dans la navigation de leurs cours, vous pouvez modifier le ``default`` paramètre dans le JSON copié. Le ``default`` paramètre est défini ``enabled`` automatiquement ; toutefois, la modification du ``default`` paramètre permet aux ``disabled`` enseignants de choisir la navigation de leurs propres cours.
    >
    > Pour plus d’informations sur la façon dont les enseignants peuvent modifier leurs liens de navigation de cours, consultez [Comment faire gérer les liens de navigation des cours ?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Enregistrez la clé et elle devient disponible dans Canvas dans un état **Désactivé** . Activez **la clé et** copiez la clé donnée dans la colonne **Détails** à utiliser à l’étape suivante.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Page Canevas avec la clé définie dans un état désactivé. Elle doit être activée et la clé doit être copiée à partir de la colonne détails de cette page.":::

8. Revenez au portail d’inscription Microsoft OneDrive LTI et collez la clé dans le champ **ID client canvas**. Sélectionnez **Suivant** lorsque vous êtes prêt.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Page d’inscription du locataire LTI, qui affiche le texte JSON et la zone de texte dans laquelle la clé doit être copiée.":::

9. Passez en revue et enregistrez vos modifications. Un message s’affiche lors de l’inscription réussie.
10. Vous pouvez également consulter les détails de votre inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Activer Microsoft OneDrive LTI dans les cours canevas

Un administrateur de canevas peut activer Microsoft OneDrive LTI pour tous les cours. Si Microsoft OneDrive LTI est nécessaire dans un cours spécifique (et pas tous les cours), l’enseignant du cours doit suivre les mêmes étapes dans les paramètres du cours.

1. Connectez-vous en tant qu’administrateur et accédez à la section **Paramètres**.
2. Accédez à la section **Applications** et sélectionnez le bouton **Afficher les configurations d’application** .
3. Sélectionnez le bouton **Ajouter une application** .
4. Dans la liste déroulante **Type de configuration** , choisissez l’option **Par ID client** .
5. Collez la valeur de la clé de développeur générée précédemment dans le champ **ID client** , puis sélectionnez le bouton **Envoyer** .

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Page Ajouter une application, montrant l’option Par ID client sous le menu déroulant Type de configuration.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Paramètres de collaboration pour Microsoft OneDrive LTI dans les cours canvas

> [!NOTE]
> Pour que la collaboration fonctionne pour les enseignants et les étudiants, vous ne devez pas activer le paramètre de collaboration. Pour vous assurer que le paramètre n’est pas activé, suivez les étapes ci-dessous.

1. Connectez-vous en tant qu’administrateur et accédez à la section **Paramètres**.
1. Accédez à la section **Options** de fonctionnalités, puis à la section **Cours** .
1. Définissez la fonctionnalité Outil **collaborations externes** pour qu’elle ne soit pas activée.

> [!NOTE]
> La collaboration peut être attribuée à des étudiants individuels et à des groupes d’étudiants. L’affectation à des étudiants individuels fonctionne par défaut. Pour pouvoir affecter la collaboration à un groupe d’étudiants, procédez comme suit :

1. Connectez-vous en tant qu’administrateur et accédez à la section **Clés du développeur** .
1. Recherchez la clé avec la valeur 170000000000710 et définissez-la **sur Activé**.
