---
title: Configuration des expériences de rubrique dans Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment configurer des expériences de rubrique dans Microsoft 365
ms.openlocfilehash: 3ff822d863e99f7e52089d3efde3d597df9957c7
ms.sourcegitcommit: 806536f859ac864228797f1f2f23b8f41040a6b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/28/2020
ms.locfileid: "49735809"
---
# <a name="set-up-topic-experiences-in-microsoft-365"></a>Configuration des expériences de rubrique dans Microsoft 365

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Li0E]  

</br>

Vous pouvez utiliser le centre d’administration Microsoft 365 pour installer et configurer des [expériences de rubrique](topic-experiences-overview.md). 

Il est important de planifier la meilleure façon de configurer et de configurer des rubriques dans votre environnement. Avant de commencer les procédures décrites dans cet article, lisez [plan topic Experiences](plan-topic-experiences.md) .

Vous devez être un administrateur général ou un administrateur SharePoint pour accéder au centre d’administration Microsoft 365 et configurer des expériences de rubrique.

## <a name="set-up-topic-experiences"></a>Configurer les expériences de sujets

Pour configurer des expériences de rubrique dans Microsoft 365

1. Dans le [Centre d’administration Microsoft 365](https://admin.microsoft.com), sélectionnez **configuration**, puis affichez la section **fichiers et contenu** .
2. Dans la section **fichiers et contenu** , cliquez sur **connecter des personnes à la connaissance**.

    ![Connecter des personnes aux connaissances](../media/admin-org-knowledge-options.png) 

3. Sur la page **connecter des personnes au** niveau de connaissances, cliquez sur **prise en main** pour vous guider tout au long du processus de configuration.

    ![Prise en main](../media/k-get-started.png) 

4. Sur la page **choisir comment le réseau de connaissances peut trouver des rubriques** , vous allez configurer la découverte de rubrique. Dans la section **Sélectionner les sources des rubriques SharePoint** , sélectionnez les sites SharePoint qui seront analysés en tant que sources pour vos rubriques lors de la découverte. Choisissez parmi les autorisations suivantes :
    - **Tous les sites**: tous les sites SharePoint de votre organisation. Cela inclut les sites actuels et futurs.
    - **Tout, à l’exception des sites sélectionnés**: saisissez les noms des sites à exclure.  Vous pouvez également télécharger une liste de sites que vous souhaitez exclure de la découverte. Les sites créés à l’avenir seront inclus en tant que sources pour la découverte des rubriques. 
    - **Sites sélectionnés uniquement**: saisissez les noms des sites que vous souhaitez inclure. Vous pouvez également télécharger une liste de sites. Les sites créés à l’avenir ne seront pas inclus en tant que sources pour la découverte des rubriques.
    - **Aucun site**: n’inclut aucun site SharePoint.

    ![Choisir comment rechercher des rubriques](../media/ksetup1.png) 
   
5. Dans la section **exclure des rubriques par nom** , vous pouvez ajouter les noms des rubriques que vous souhaitez exclure de la découverte de rubrique. Utilisez ce paramètre pour empêcher que des informations sensibles soient incluses en tant que rubriques. Les options disponibles sont les suivantes :
    - **Ne pas exclure les rubriques** 
    - **Exclure les rubriques par nom**

    ![Exclure des rubriques](../media/topics-excluded-by-name.png) 

    (Les gestionnaires de connaissances peuvent également exclure des rubriques dans le Centre des rubriques après la découverte.)

    #### <a name="how-to-exclude-topics-by-name"></a>Procédure exclure des rubriques par nom    

    Si vous devez exclure des rubriques, après avoir sélectionné **exclure les rubriques par nom**, sélectionnez Télécharger le modèle. csv et mettez-le à jour à l’aide de la liste des rubriques que vous souhaitez exclure de vos résultats de découverte.

    ![Exclure les rubriques du modèle CSV](../media/exclude-topics-csv.png) 

    Dans le modèle CSV, entrez les informations suivantes sur les rubriques à exclure :

    - **Nom**: tapez le nom de la rubrique à exclure. Vous pouvez procéder de deux manières :
        - Correspondance exacte : vous pouvez inclure le nom exact ou un acronyme (par exemple, *contoso* ou *ATL*).
        - Correspondance partielle : vous pouvez exclure toutes les rubriques qui contiennent un mot spécifique.  Par exemple, *arc* exclut toutes les rubriques contenant le mot *arc* , comme un *cercle arc*, un *soudage* à l’arc de plasma ou un *arc de formation*. Notez qu’il n’exclura pas les rubriques dans lesquelles le texte est inclus dans un mot, tel que *architecture*.
    - **Abréviation de (facultatif)**: Si vous souhaitez exclure un acronyme, tapez les mots de l’acronyme.
    - **MatchType-exacte/partielle**: spécifiez si le nom que vous avez entré est un type de correspondance *exacte* ou *partielle* .

    Une fois que vous avez terminé et enregistré votre fichier. csv, sélectionnez **Parcourir** pour le localiser et le sélectionner.
    
    Sélectionnez **Suivant**.

6. Sur la page **qui peut voir les rubriques et où les afficher** , vous allez configurer la visibilité des rubriques. Dans le paramètre **qui peut voir les rubriques du paramètre de réseau de connaissances** , vous choisissez les utilisateurs qui auront accès aux détails de la rubrique, comme les rubriques en surbrillance, les fiches de rubrique, les réponses aux questions dans la recherche et les pages de rubrique. Vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Uniquement les personnes ou les groupes de sécurité sélectionnés**
    - **Personne**

    ![Qui peut voir les rubriques](../media/ksetup2.png)  

 > [!Note] 
 > Bien que ce paramètre vous permette de sélectionner un utilisateur de votre organisation, seuls les utilisateurs disposant d’une rubrique sur laquelle des licences ont été attribuées pourront consulter les rubriques.

7. Dans la page **autorisations pour la rubrique gestion des** rubriques, choisissez qui pourra créer, modifier ou gérer des rubriques. Dans la section **qui peut créer et modifier des rubriques** , vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Uniquement les personnes ou les groupes de sécurité sélectionnés**
    - **Personne**

    ![Autorisations pour la gestion des rubriques, qui peut créer et modifier des rubriques](../media/ksetup3.png) 

8. Dans la section **qui peut gérer les rubriques** , vous pouvez sélectionner :
    - **Tous les membres de mon organisation**
    - **Uniquement les personnes ou les groupes de sécurité sélectionnés**

    ![Autorisations pour la gestion des rubriques](../media/km-setup-create-edit-topics.png) 

    Sélectionnez **Suivant**.

9. Sur la page **créer un centre de rubriques** , vous pouvez créer votre site Centre de rubrique dans lequel les pages de rubrique peuvent être affichées et les rubriques peuvent être gérées. Dans la zone **nom du site** , tapez un nom pour le centre de la rubrique. Vous pouvez éventuellement taper une brève description dans la zone **Description** . 

Sélectionnez **Suivant**.

   ![Créer un centre de connaissances](../media/ksetup4.png)  

10. À la page **Examiner et finaliser**, vous pouvez consulter le paramètre sélectionné, puis choisir d’apporter des modifications. Si vos sélections vous conviennent, sélectionnez **Activer**.

11. La page **activation du réseau de connaissances** s’affiche, confirmant que le système commence à analyser les sites sélectionnés pour les rubriques et la création du site Centre de connaissances. Sélectionnez **Terminé**.

12. Vous serez redirigé vers la page **connecter des personnes à la page de connaissances** . Dans cette page, vous pouvez sélectionner **Gérer** pour modifier vos paramètres de configuration. 

    ![Paramètres appliqués](../media/ksetup7.png)    

## <a name="assign-licenses"></a>Attribuer des licences

Une fois que vous avez configuré les expériences de rubrique, vous devez attribuer des licences aux utilisateurs qui utiliseront des expériences de rubrique. Seuls les utilisateurs disposant d’une licence peuvent consulter des informations sur des sujets tels que des mises en évidence, des fiches de rubrique, des pages de rubrique et le Centre des rubriques. 

Pour attribuer des licences :

1. Dans le Centre d’administration Microsoft 365, sous **Utilisateurs**, cliquez sur **Utilisateurs actifs**.

2. Sélectionnez les utilisateurs auxquels attribuer une licence, puis cliquez sur **Gérer les licences de produits**.

3. Sélectionnez **Attribuer plus**.

4. Sous **licences**, sélectionnez **expériences**.

5. Sous **applications**, assurez-vous que les **connecteurs graphiques de recherche avec index** et les **expériences de rubrique** sont tous deux sélectionnés.

    > [!div class="mx-imgBorder"]
    > ![Licences SharePoint Syntex dans le Centre d’administration Microsoft 365.](../media/topic-experiences-licenses.png)

6. Cliquez sur **Enregistrer les modifications**.

## <a name="manage-topic-experiences"></a>Gérer les expériences de rubrique

Une fois que vous avez configuré les expériences de rubrique, vous pouvez modifier les paramètres que vous avez choisis lors de l’installation dans le [Centre d’administration 365 de Microsoft](https://admin.microsoft.com/AdminPortal#/featureexplorer/csi/KnowledgeManagement). Consultez les références suivantes :

- [Gestion de la découverte de rubrique dans Microsoft 365](topic-experiences-discovery.md)
- [Gestion de la visibilité des rubriques dans Microsoft 365](topic-experiences-knowledge-rules.md)
- [Gérer les autorisations de rubrique dans Microsoft 365](topic-experiences-user-permissions.md)
- [Modifier le nom du centre de rubrique dans Microsoft 365](topic-experiences-administration.md)

## <a name="see-also"></a>Voir aussi

[Présentation des expériences](topic-experiences-overview.md)
