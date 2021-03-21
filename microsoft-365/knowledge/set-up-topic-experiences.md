---
title: Configurer Les rubriques microsoft
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Découvrez comment configurer les rubriques microsoft
ms.openlocfilehash: 629008e083d71e09632b05e21eaefb011d7d9ce2
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929443"
---
# <a name="set-up-microsoft-viva-topics"></a>Configurer Les rubriques microsoft

Vous pouvez utiliser le Centre d’administration Microsoft 365 pour configurer les [rubriques.](topic-experiences-overview.md) 

Il est important de planifier la meilleure façon de configurer des rubriques dans votre environnement. Avant de commencer les procédures de cet article, veillez à lire les rubriques Planifier pour [Microsoft Topics.](plan-topic-experiences.md)

Vous devez être abonné à [Rubriques Et](https://www.microsoft.com/microsoft-viva/topics) être administrateur général ou administrateur SharePoint pour accéder au Centre d’administration Microsoft 365 et configurer Rubriques.

Si vous avez configuré SharePoint pour exiger [des](/sharepoint/control-access-from-unmanaged-devices)appareils gérés, assurez-vous de configurer les rubriques à partir d’un appareil géré.

## <a name="video-demonstration"></a>Démonstration vidéo

Cette vidéo montre le processus de configuration des rubriques dans Microsoft 365.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Li0E]  

<br>

## <a name="set-up-topics"></a>Configurer les rubriques

Pour configurer des rubriques

1. Dans le [Centre d’administration Microsoft 365,](https://admin.microsoft.com)sélectionnez **Installation,** puis affichez la section Fichiers **et** contenu.
2. Dans la section **Fichiers et contenu,** cliquez **sur Connecter des personnes aux connaissances.**

    ![Connecter les personnes aux connaissances](../media/admin-org-knowledge-options.png) 

3. Dans la page **Connecter des personnes aux connaissances,** cliquez sur **Commencer** pour vous aider dans le processus de configuration.

    ![Prise en main](../media/k-get-started.png) 

4. Dans la page **Choisir la façon dont Rubriques peut trouver des rubriques,** vous allez configurer la découverte de rubriques. Dans la section Sélectionner des sources de rubrique **SharePoint,** sélectionnez les sites SharePoint qui seront analyser en tant que sources pour vos rubriques lors de la découverte. Choisissez parmi les autorisations suivantes :
    - **Tous les sites**: tous les sites SharePoint de votre organisation. Cela inclut les sites actuels et futurs.
    - **Tous, sauf les sites sélectionnés**: tapez les noms des sites que vous souhaitez exclure.  Vous pouvez également charger une liste de sites que vous souhaitez refuser de découvrir. Les sites créés à l’avenir seront inclus en tant que sources pour la découverte de rubriques. 
    - **Seuls les sites** sélectionnés : tapez les noms des sites que vous souhaitez inclure. Vous pouvez également charger une liste de sites. Les sites créés à l’avenir ne seront pas inclus en tant que sources de découverte de sujet.
    - **Aucun site**: n’incluez aucun site SharePoint.

    ![Choisir comment rechercher des rubriques](../media/ksetup1.png) 
   
5. Dans la section **Exclure les rubriques par** nom, vous pouvez ajouter des noms de rubriques que vous souhaitez exclure de la découverte de rubriques. Utilisez ce paramètre pour empêcher que des informations sensibles ne figurent dans les rubriques. Les options disponibles sont les suivantes :
    - **N’exclure aucune rubrique** 
    - **Exclure des rubriques par nom**

    ![Exclure des rubriques](../media/topics-excluded-by-name.png) 

    (Les gestionnaires de connaissances peuvent également exclure des rubriques dans le centre de rubriques après la découverte.)

    #### <a name="how-to-exclude-topics-by-name"></a>Comment exclure des rubriques par nom    

    Si vous devez exclure des rubriques, après avoir sélectionné Exclure les **rubriques** par nom, téléchargez le modèle .csv et mettez-le à jour avec la liste des rubriques que vous souhaitez exclure de vos résultats de découverte.

    ![Exclure des rubriques dans le modèle CSV](../media/exclude-topics-csv.png) 

    Dans le modèle CSV, entrez les informations suivantes sur les rubriques que vous souhaitez exclure :

    - **Nom**: tapez le nom de la rubrique que vous souhaitez exclure. Vous pouvez procéder de deux manières :
        - Correspondance exacte : vous pouvez inclure le nom exact ou l’acronyme (par exemple, *Contoso* ou *ATL*).
        - Correspondance partielle : vous pouvez exclure toutes les rubriques qui ont un mot spécifique.  Par exemple, *arc exclura* toutes les rubriques avec le mot *arc* dans celui-ci, telles que le cercle *d’arc,* *l’arc de Pierre ou* *l’arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans le cadre d’un mot, comme *Architecture*.
    - **Signifie (facultatif)**: si vous souhaitez exclure un acronyme, tapez les mots qu’il signifie.
    - **MatchType-Exact/Partial**: tapez si le nom que vous avez entré était un type de correspondance *exacte* *ou* partielle.

    Une fois que vous avez terminé et enregistré votre fichier .csv, sélectionnez **Parcourir** pour le localiser et le sélectionner.
    
    Sélectionnez **Suivant**.

6. Dans la page **Qui peut voir les rubriques** et où peuvent-ils les voir, vous allez configurer la visibilité des rubriques. Dans le paramètre Qui peut voir les **rubriques,** vous choisissez les personnes qui auront accès aux détails des rubriques, telles que les rubriques mises en évidence, les fiches de rubrique, les réponses aux rubriques dans la recherche et les pages de rubriques. Vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Personnes ou groupes de sécurité sélectionnés uniquement**
    - **Personne**

    ![Personnes qui peuvent voir les rubriques](../media/ksetup2.png)  

    > [!Note] 
    > Bien que ce paramètre vous permet de sélectionner n’importe quel utilisateur de votre organisation, seuls les utilisateurs qui ont des licences Expériences des rubriques qui leur sont attribuées pourront afficher les rubriques.

7. Dans la page **Autorisations pour la** gestion des rubriques, vous choisissez qui sera en mesure de créer, modifier ou gérer des rubriques. Dans la section **Qui peut créer et modifier des rubriques,** vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Personnes ou groupes de sécurité sélectionnés uniquement**
    - **Personne**

    ![Autorisations pour la gestion des rubriques, qui peut créer et modifier des rubriques](../media/ksetup3.png) 

8. Dans la section **Qui peut gérer les rubriques,** vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Personnes ou groupes de sécurité sélectionnés uniquement**

    ![Autorisations pour la gestion des rubriques](../media/km-setup-create-edit-topics.png) 

    Sélectionnez **Suivant**.

9. Dans la page **Créer un** centre de rubriques, vous pouvez créer votre site de centre de rubriques dans lequel les pages de rubriques peuvent être vues et les rubriques peuvent être gérées. Dans la **zone Nom du site,** tapez un nom pour votre centre de rubriques. Vous pouvez éventuellement taper une brève description dans la **zone Description.** 

   Sélectionnez **Suivant**.

   ![Créer un Centre de connaissances](../media/ksetup4.png)  

10. À la page **Examiner et finaliser**, vous pouvez consulter le paramètre sélectionné, puis choisir d’apporter des modifications. Si vos sélections vous conviennent, sélectionnez **Activer**.

11. La page **Activée rubriques** s’affiche, confirmant que le système va maintenant commencer à analyser les sites sélectionnés pour les rubriques et à créer le site centre de rubriques. Sélectionnez **Terminé**.

12. Vous serez renvoyé à votre page De **connexion des personnes à la** base de connaissances. Dans cette page, vous pouvez sélectionner **Gérer** pour modifier vos paramètres de configuration. 

    ![Paramètres appliqués](../media/ksetup7.png)    

Notez que la première fois que la découverte de rubrique est activée, l’affichage Gérer les rubriques peut prendre jusqu’à deux semaines pour que toutes les rubriques suggérées apparaissent. La découverte de rubriques se poursuit à mesure que de nouveaux contenus ou mises à jour du contenu sont effectués. Il est normal d’avoir des variations dans le nombre de rubriques suggérées dans votre organisation, car Rubriques de Rubriques évalue de nouvelles informations.

## <a name="assign-licenses"></a>Attribuer les licences

Une fois que vous avez configuré les expériences de rubrique, vous devez attribuer des licences pour les utilisateurs qui utiliseront Rubriques. Seuls les utilisateurs titulaires d’une licence peuvent voir des informations sur des sujets tels que les points forts, les fiches de rubrique, les pages de rubriques et le centre de rubriques. 

Pour attribuer des licences :

1. Dans le Centre d’administration Microsoft 365, sous **Utilisateurs**, cliquez sur **Utilisateurs actifs**.

2. Sélectionnez les utilisateurs dont vous souhaitez obtenir une licence, puis cliquez **sur Licences et applications.**

3. Sous **Licences,** **sélectionnez Rubriques Titre.**

4. Sous **Applications,** assurez-vous **que les rubriques Recherche des connecteurs Graph avec index (Rubriques)** et **Rubriques De** la sélection sont toutes les deux sélectionnées.

   > [!div class="mx-imgBorder"]
   > ![Licences Rubriques Microsoft dans le Centre d’administration Microsoft 365](../media/topic-experiences-licenses.png)

5. Cliquez sur **Enregistrer les modifications**.

## <a name="manage-topic-experiences"></a>Gérer les expériences de rubrique

Une fois que vous avez configuré Rubriques, vous pouvez modifier les paramètres que vous avez choisis lors de l’installation dans le Centre d’administration [Microsoft 365.](https://admin.microsoft.com/AdminPortal#/featureexplorer/csi/KnowledgeManagement) Si vous souhaitez en savoir plus, veuillez consulter les références suivantes :

- [Gérer la découverte de rubriques dans les rubriques microsoft](topic-experiences-discovery.md)
- [Gérer la visibilité des rubriques dans les rubriques microsoft](topic-experiences-knowledge-rules.md)
- [Gérer les autorisations des rubriques dans les rubriques microsoft](topic-experiences-user-permissions.md)
- [Modifier le nom du centre de rubriques dans Rubriques microsoft](topic-experiences-administration.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des expériences de rubrique](topic-experiences-overview.md)
