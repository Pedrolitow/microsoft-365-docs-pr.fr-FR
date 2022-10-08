---
title: Intégrer Microsoft OneDrive LTI à Canvas
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Créez et classez des devoirs, générez et organisez du contenu de cours, et collaborez sur des fichiers en temps réel avec Microsoft OneDrive LTI pour Canvas.
ms.openlocfilehash: 405a47ee9ff510e452fa632eaef52b07aba2876b
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68203901"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Intégrer Microsoft OneDrive LTI à Canvas

Cet article s’adresse aux administrateurs informatiques de l’éducation qui doivent configurer Microsoft OneDrive LTI pour Canvas.

Pour obtenir des instructions pour les enseignants sur l’utilisation de l’interface LTI OneDrive dans Canvas, consultez [Utiliser Microsoft OneDrive avec votre LMS](https://support.microsoft.com/topic/use-microsoft-onedrive-with-your-lms-c2ddeb48-f695-4267-94f2-14f7ff1b7bdd).

L’intégration de Microsoft OneDrive LTI à Canvas est un processus en deux étapes. La première étape active Microsoft OneDrive dans Canvas, et la deuxième étape rend microsoft OneDrive LTI disponible dans les cours Canvas.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être activés pour Microsoft OneDrive.
- Les fenêtres contextuelles ne doivent pas être bloquées pour Microsoft OneDrive.

> [!NOTE]
>
> - Les cookies ne sont pas activés par défaut dans le mode incognito du navigateur Chrome et doivent être activés.
> - Microsoft OneDrive LTI fonctionne en mode privé dans le navigateur Microsoft Edge. Vérifiez que vous n’avez pas bloqué les cookies (qui sont activés par défaut).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Activer Microsoft OneDrive LTI dans Canvas

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être un administrateur de Canvas et un administrateur du locataire Microsoft 365.

1. Se connecter au <a href="https://onedrivelti.microsoft.com/admin" target="_blank">portail d’inscription LTI Microsoft OneDrive</a>
2. Sélectionnez le bouton **Administration Consentement** et acceptez les autorisations.

   > [!CAUTION]
   > Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur, et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous aurez obtenu l’erreur.

3. Sélectionnez le bouton **Créer un locataire LTI** . Dans la page Inscription LTI, sélectionnez **Canvas** dans la liste déroulante et entrez l’URL de base de votre instance Canvas.

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

7. Ensuite, développez la liste déroulante **Paramètres supplémentaires** et **définissez le niveau de confidentialité** sur **Public**. 
  
   La définition du **niveau de confidentialité** sur **Public** permet aux noms des membres du cours d’apparaître à d’autres membres pour la collaboration.

8. Enregistrez la clé et elle devient disponible dans Canvas dans un état **Désactivé** . Activez **la clé et** copiez la clé donnée dans la colonne **Détails** à utiliser à l’étape suivante.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Page Canevas avec la clé définie dans un état désactivé. Elle doit être activée et la clé doit être copiée à partir de la colonne détails de cette page.":::

9. Revenez au portail d’inscription Microsoft OneDrive LTI et collez la clé dans le champ **ID client canvas** . Sélectionnez **Suivant** lorsque vous êtes prêt.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Page d’inscription du locataire LTI, qui affiche le texte JSON et la zone de texte dans laquelle la clé doit être copiée.":::

10. Passez en revue et enregistrez vos modifications. Un message s’affiche lors de l’inscription réussie.

11. Vous pouvez également consulter les détails de votre inscription en sélectionnant le bouton **Afficher les locataires LTI** sur la page d’accueil.

Les versions ultérieures peuvent nécessiter un consentement administrateur supplémentaire. Dans ce cas, vous devez répéter uniquement les étapes 1 et 2.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Activer Microsoft OneDrive LTI dans les cours canevas

Un administrateur de canevas peut activer Microsoft OneDrive LTI pour tous les cours. Si Microsoft OneDrive LTI est nécessaire dans un cours spécifique (et pas tous les cours), l’enseignant du cours doit suivre les mêmes étapes dans les paramètres du cours.

1. Connectez-vous en tant qu’administrateur et accédez à la section **Paramètres** .
2. Accédez à la section **Applications** et sélectionnez le bouton **Afficher les configurations d’application** .
3. Sélectionnez le bouton **Ajouter une application** .
4. Dans la liste déroulante **Type de configuration** , choisissez l’option **Par ID client** .
5. Collez la valeur de la clé de développeur générée précédemment dans le champ **ID client** , puis sélectionnez le bouton **Envoyer** .

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Page Ajouter une application, montrant l’option Par ID client sous le menu déroulant Type de configuration.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Paramètres de collaboration pour Microsoft OneDrive LTI dans les cours canevas

Pour que OneDrive Collaborations fonctionne pour les enseignants et les étudiants, assurez-vous que le paramètre **Outils de collaboration externe** est désactivé. Pour désactiver le paramètre **Outil Collaborations externes** , suivez les étapes ci-dessous.

1. Connectez-vous à Canvas en tant qu’administrateur et accédez à la section **Paramètres** .
1. Accédez à la section **Options** de fonctionnalités, puis à la section **Cours** .
1. Définissez le bouton bascule **Collaborations externes** sur la position désactivée.

Les collaborations peuvent être attribuées à des étudiants individuels et à des groupes d’étudiants dans un cours. Les collaborations dans les groupes de canevas ne sont actuellement pas prises en charge.

L’affectation à des étudiants individuels fonctionne par défaut. Pour affecter la collaboration à des groupes d’étudiants, procédez comme suit :

1. Connectez-vous à Canvas en tant qu’administrateur et accédez à la section **Clés du développeur** .
1. Recherchez la clé avec une valeur `170000000000710` et définissez-la **sur Activé**.
