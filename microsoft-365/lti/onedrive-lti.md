---
title: Utiliser l Microsoft OneDrive Learning opérabilité des outils de gestion
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
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Créez et classez des devoirs, créez et organisez du contenu de cours et collaborez sur des fichiers en temps réel avec la nouvelle application d’interopérabilité Microsoft OneDrive Learning Tools.
ms.openlocfilehash: e67e772ce8ef460075729b34bc7da86d486c51e9
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59181150"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Intégrer Microsoft OneDrive LTI à Canvas

> [!IMPORTANT]
> Certaines informations concernent un produit pré-commercialisé, qui peut être considérablement modifié avant sa commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

L’intégration Microsoft OneDrive LTI à Canvas est un processus en deux étapes. La première étape active la Microsoft OneDrive canvas, et la deuxième étape rend l’Microsoft OneDrive LTI disponible dans les cours Canvas.

## <a name="recommended-browser-settings"></a>Paramètres de navigateur recommandés

- Les cookies doivent être activés pour Microsoft OneDrive.
- Les fenêtres pop-up ne doivent pas être bloquées Microsoft OneDrive.

> [!NOTE]
> - Les cookies ne sont pas activés par défaut dans le navigateur Chrome en modecognito et doivent être activés.
> - Microsoft OneDrive LTI fonctionne en mode privé dans Microsoft Edge navigateur. Assurez-vous que vous n’avez pas bloqué les cookies (qui sont activés par défaut).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Activer Microsoft OneDrive LTI dans Canvas

> [!IMPORTANT]
> La personne qui effectue cette intégration doit être administrateur de Canvas et administrateur du client Microsoft 365 client.

1. Connectez-vous <a href="https://onedrivelti.microsoft.com/admin" target="_blank">au Microsoft OneDrive d’inscription LTI</a>
1. Sélectionnez le **bouton Consentement de l’administrateur** et acceptez les autorisations.

> [!CAUTION]
> Si cette étape n’est pas effectuée, l’étape suivante vous donnera une erreur et vous ne pourrez pas effectuer cette étape pendant une heure une fois que vous aurez obtenu l’erreur.

3. Sélectionnez **le bouton Créer un client LTI.** Dans la page Inscription LTI, sélectionnez **Canvas** dans la liste et entrez l’URL de base de votre instance de canvas.

> [!NOTE]
> Si votre instance de canvas est, par exemple, https://contoso.test.instructure.com ]( https://contoso.test.instructure.com) , l’URL complète doit être entrée.

:::image type="content" source="media/OneDrive-LTI-07.png" alt-text="Page d’administration du client LTI, avec un champ de liste liste pour choisir la plateforme grand public LTI et un champ de texte d’URL.":::

4. Copiez le JSON en sélectionnant le bouton **Copier** (icône à droite qui affiche deux pages l’une sur l’autre). Cette clé sera utilisée pour générer la clé dans Canvas.

:::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Image montrant le bouton copier qui copie le texte JSON affiché et le rend disponible pour la génération de touches dans Canvas.":::

5. Connectez-vous à votre instance  de canvas en tant qu’administrateur et sélectionnez Clés de développeur dans le menu sur le côté gauche de la page. Dans la dernière page, créez une clé de développeur en choisissant **Clé LTI** dans la partie supérieure droite de la page.

:::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Capture d’écran montrant la barre de navigation de gauche avec les clés de développeur sélectionnées, et l’entrée de clé LTI sélectionnée dans une dropdown à droite de la page.":::

6. Dans la page Configurer,  dans la zone de texte Méthode, sélectionnez Coller **JSON** comme méthode et collez le texte JSON que vous avez copié à l’étape 5 dans le champ de texte qui s’affiche.
7. Enregistrez la clé et elle devient disponible dans Canvas dans un **état Off.** Activer la clé **et** copier la clé donnée dans la colonne **Détails** à utiliser à l’étape suivante.

:::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Page Canvas avec la touche définie dans un état « off ». Elle doit être allumée et la clé doit être copiée à partir de la colonne de détails de cette page.":::

8. Revenir au portail Microsoft OneDrive inscription LTI et collez la clé dans le champ **ID client** canvas. Sélectionnez **Suivant** lorsque vous êtes prêt.

:::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Page d’inscription du client LTI, qui affiche le texte JSON et la zone de texte dans laquelle la clé doit être copiée.":::

9. Examinez et enregistrez vos modifications. Un message s’affiche lors de l’inscription réussie.
10. Vous pouvez également examiner vos détails d’inscription en sélectionnant le bouton Afficher les locataires **LTI** sur la page d’accueil.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Activer Microsoft OneDrive LTI dans les cours de canevas

Un administrateur canvas peut activer Microsoft OneDrive LTI pour tous les cours. Si Microsoft OneDrive LTI est nécessaire dans un cours spécifique (et pas dans tous les cours), l’enseignant du cours doit suivre les mêmes étapes dans les paramètres du cours.

1. Connectez-vous en tant qu’administrateur et Paramètres **section.**
2. Go to the **Apps** section and select the **View App Configurations** button.
3. Sélectionnez le **bouton Ajouter une** application.
4. Dans la **liste finale Type de configuration,** choisissez l’option Par **ID** client.
5. Collez la valeur de la clé de développeur générée précédemment dans le champ **ID client,** puis sélectionnez **le bouton** Envoyer.

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Page Ajouter une application, affichant l’option Par ID client sous le menu déroulant Type de configuration.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Collaboration Paramètres for Microsoft OneDrive LTI in Canvas Courses

> [!NOTE]
> Pour que la collaboration fonctionne pour les enseignants et les étudiants, vous ne devez pas activer le paramètre de collaboration. Pour vous assurer que le paramètre n’est pas activé, suivez les étapes ci-dessous.

1. Connectez-vous en tant qu’administrateur et Paramètres **section.**
1. Go to **Feature Options** section, and then go to the **Course** section.
1. Définissez **la fonctionnalité outil collaborations externes** comme non activée.

> [!NOTE]
> La collaboration peut être affectée à des étudiants individuels et à des groupes d’étudiants. L’affectation à des étudiants individuels fonctionne par défaut. Pour être en mesure d’affecter la collaboration à un groupe d’étudiants, suivez les étapes suivantes :

1. Connectez-vous en tant qu’administrateur et allez à la section **Clés de** développeur.
1. Recherchez la clé avec la valeur 170000000000710 et définissez-la sur **On**.
