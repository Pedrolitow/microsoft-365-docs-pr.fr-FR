---
title: Utiliser le partage d’audit dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- BCS160
- MET150
ms.collection:
- M365-security-compliance
- SPO_Content
ms.assetid: 50bbf89f-7870-4c2a-ae14-42635e0cfc01
description: Administration pouvez apprendre à utiliser l’audit de partage dans le journal d’audit Microsoft 365 pour identifier les ressources partagées avec des utilisateurs extérieurs à leur organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1eb780f79d0dc5beaab3afcc52261bf9a4ccc25b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625960"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Utiliser le partage d’audit dans le journal d’audit

Le partage est une activité clé dans SharePoint Online et OneDrive Entreprise, et il est largement utilisé dans les organisations. Les administrateurs peuvent utiliser l’audit de partage dans le journal d’audit pour déterminer comment le partage est utilisé dans leur organisation. 
  
## <a name="the-sharepoint-sharing-schema"></a>Schéma de partage SharePoint

Les événements de partage (sans inclure les événements liés à la stratégie de partage et aux liens de partage) sont différents des événements liés aux fichiers et aux dossiers d’une manière principale : un utilisateur effectue une action qui a un effet sur un autre utilisateur. Par exemple, lorsqu’un utilisateur de ressource A donne à l’utilisateur B l’accès à un fichier. Dans cet exemple, l’utilisateur A est  *l’utilisateur agissant et l’utilisateur*  B est l’utilisateur  *cible*. Dans le schéma de fichier SharePoint, l’action de l’utilisateur agissant affecte uniquement le fichier lui-même. Lorsque l’utilisateur A ouvre un fichier, les seules informations nécessaires dans l’événement **FileAccessed** sont l’utilisateur agissant. Pour résoudre cette différence, il existe un schéma distinct, appelé schéma de  *partage SharePoint*, qui capture plus d’informations sur le partage d’événements. Cela garantit que les administrateurs ont une visibilité sur qui a partagé une ressource et l’utilisateur avec lequel la ressource a été partagée. 
  
Le schéma de partage fournit deux champs supplémentaires dans un enregistrement d’audit lié au partage d’événements : 
  
- **TargetUserOrGroupType :** Identifie si l’utilisateur ou le groupe cible est membre, invité, SharePointGroup, SecurityGroup ou partenaire.

- **TargetUserOrGroupName :** Stocke l’UPN ou le nom de l’utilisateur ou du groupe cible avec lequel une ressource a été partagée (utilisateur B dans l’exemple précédent). 

Ces deux champs, en plus d’autres propriétés du schéma du journal d’audit, telles que Utilisateur, Opération et Date, peuvent raconter l’histoire complète de  *l’utilisateur qui*  a partagé  *la*  ressource avec  *qui*  et  *quand*. 
  
Il existe une autre propriété de schéma qui est importante pour l’histoire de partage. Lorsque vous exportez les résultats de la recherche dans le journal d’audit, la colonne **AuditData** dans le fichier CSV exporté stocke des informations sur le partage d’événements. Par exemple, lorsqu’un utilisateur partage un site avec un autre utilisateur, cela s’effectue en ajoutant l’utilisateur cible à un groupe SharePoint. La colonne **AuditData** capture ces informations pour fournir un contexte aux administrateurs. Consultez [l’étape 2](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) pour obtenir des instructions sur l’analyse des informations dans la colonne **AuditData** .

## <a name="sharepoint-sharing-events"></a>Événements de partage SharePoint

Le partage est défini par le moment où un utilisateur (l’utilisateur *agissant* ) souhaite partager une ressource avec un autre utilisateur (l’utilisateur *cible* ). Les enregistrements d’audit liés au partage d’une ressource avec un utilisateur externe (un utilisateur en dehors de votre organisation et qui n’a pas de compte invité dans Azure Active Directory de votre organisation) sont identifiés par les événements suivants, qui sont enregistrés dans le journal d’audit :

- **SharingInvitationCreated :** Un utilisateur de votre organisation a essayé de partager une ressource (probablement un site) avec un utilisateur externe. Cela entraîne l’envoi d’une invitation de partage externe à l’utilisateur cible. Aucun accès à la ressource n’est accordé à ce stade.

- **SharingInvitationAccepted :** L’utilisateur externe a accepté l’invitation de partage envoyée par l’utilisateur agissant et a maintenant accès à la ressource.

- **AnonymousLinkCreated :** Un lien anonyme (également appelé lien « Tout le monde ») est créé pour une ressource. Étant donné qu’un lien anonyme peut être créé puis copié, il est raisonnable de supposer que n’importe quel document ayant un lien anonyme a été partagé avec un utilisateur cible.

- **AnonymousLinkUsed :** Comme son nom l’indique, cet événement est journalisé lorsqu’un lien anonyme est utilisé pour accéder à une ressource. 

- **SecureLinkCreated :** Un utilisateur a créé un « lien de personnes spécifiques » pour partager une ressource avec une personne spécifique. Cet utilisateur cible peut être une personne externe à votre organisation. La personne avec laquelle la ressource est partagée est identifiée dans l’enregistrement d’audit de l’événement **AddedToSecureLink** . Les horodatages de ces deux événements sont presque identiques.

- **AddedToSecureLink :** Un utilisateur a été ajouté à un lien de personnes spécifique. Utilisez le champ **TargetUserOrGroupName** dans cet événement pour identifier l’utilisateur ajouté au lien de personnes spécifique correspondant. Cet utilisateur cible peut être une personne externe à votre organisation.

## <a name="sharing-auditing-work-flow"></a>Partage du flux de travail d’audit
  
Lorsqu’un utilisateur (l’utilisateur agissant) souhaite partager une ressource avec un autre utilisateur (l’utilisateur cible), SharePoint (ou OneDrive Entreprise) vérifie d’abord si l’adresse e-mail de l’utilisateur cible est déjà associée à un compte d’utilisateur dans l’annuaire de l’organisation. Si l’utilisateur cible se trouve dans le répertoire (et a un compte d’utilisateur invité correspondant), SharePoint effectue les opérations suivantes :
  
-  Affecte immédiatement aux utilisateurs cibles les autorisations d’accès à la ressource en ajoutant l’utilisateur cible au groupe SharePoint approprié, puis journalise un événement **AddedToGroup** . 
    
- Envoie une notification de partage à l’adresse e-mail de l’utilisateur cible.
    
- Journalise un événement **SharingSet** . Cet événement porte le nom convivial « Fichier partagé, dossier ou site » sous Activités de **demande de partage et d’accès** dans le sélecteur d’activités de l’outil de recherche de journal d’audit. Voir la capture d’écran de [l’étape 1](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Si un compte d’utilisateur pour l’utilisateur cible n’est pas dans le répertoire, SharePoint effectue les opérations suivantes : 
    
   - Enregistre l’un des événements suivants, en fonction de la façon dont la ressource est partagée :
   
      - **AnonymousLinkCreated**
   
      - **SecureLinkCreated**
   
      - **AddedToSecureLink** 

      - **SharingInvitationCreated** (cet événement est journalisé uniquement lorsque la ressource partagée est un site)
    
   - Lorsque l’utilisateur cible accepte l’invitation de partage qui lui est envoyée (en cliquant sur le lien dans l’invitation), SharePoint journalise un événement **SharingInvitationAccepted** et attribue aux utilisateurs cibles les autorisations d’accès à la ressource. Si un lien anonyme est envoyé à l’utilisateur cible, l’événement **AnonymousLinkUsed est journalisé** après que l’utilisateur cible a utilisé le lien pour accéder à la ressource. Pour les liens sécurisés, un événement **FileAccessed est journalisé** lorsqu’un utilisateur externe utilise le lien pour accéder à la ressource.

Des informations supplémentaires sur l’utilisateur cible sont également consignées, telles que l’identité de l’utilisateur à qui l’invitation est envoyée et l’utilisateur qui accepte l’invitation. Dans certains cas, ces utilisateurs (ou adresses e-mail) peuvent être différents. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Comment identifier les ressources partagées avec des utilisateurs externes

Une exigence courante pour les administrateurs consiste à créer une liste de toutes les ressources qui ont été partagées avec des utilisateurs extérieurs à l’organisation. En utilisant l’audit de partage dans Office 365, les administrateurs peuvent générer cette liste. Voici comment procéder.
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>Étape 1 : Rechercher des événements de partage et exporter les résultats dans un fichier CSV

La première étape consiste à rechercher des événements de partage dans le journal d’audit. Pour plus d’informations (y compris les autorisations requises) sur la recherche dans le journal d’audit, consultez [Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md).
  
1. Accédez à <https://compliance.microsoft.com>.

2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.

3. Dans le volet gauche de l’portail de conformité Microsoft Purview, cliquez sur **Audit**.

    La page **Audit** s’affiche.

4. Sous **Activités**, cliquez sur **Partage et demande d’accès** pour rechercher des événements liés au partage. 

    ![Sous Activités, sélectionnez Activités de partage et demande d’accès.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Sélectionnez une plage de dates et d’heures pour rechercher les événements de partage qui se sont produits au cours de cette période. 

6. Cliquez sur **Rechercher** pour exécuter la recherche. 

7. Lorsque la recherche est terminée et que les résultats sont affichés, cliquez sur **Exporter les résultats** \> **Télécharger tous les résultats**.

    Une fois que vous avez sélectionné l’option d’exportation, un message en bas de la fenêtre vous invite à ouvrir ou enregistrer le fichier CSV.

8. Cliquez sur **Enregistrer** \> **sous** et enregistrez le fichier CSV dans un dossier sur votre ordinateur local. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>Étape 2 : Utiliser l’éditeur PowerQuery pour mettre en forme le journal d’audit exporté

L’étape suivante consiste à utiliser la fonctionnalité de transformation JSON dans le Éditeur Power Query dans Excel pour fractionner chaque propriété de la colonne **AuditData** (qui se compose d’un objet JSON à plusieurs propriétés) en sa propre colonne. Cela vous permet de filtrer les colonnes pour afficher les enregistrements liés au partage

Pour obtenir des instructions détaillées, consultez « Étape 2 : mise en forme du journal d’audit exporté à l’aide de l’Éditeur Power Query » dans [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>Étape 3 : Filtrer le fichier CSV pour les ressources partagées avec des utilisateurs externes

L’étape suivante consiste à filtrer le fichier CSV pour les différents événements liés au partage précédemment décrits dans la section [Événements de partage SharePoint](#sharepoint-sharing-events) . Vous pouvez également filtrer la colonne **TargetUserOrGroupType** pour afficher tous les enregistrements où la valeur de cette propriété est **Guest**. 

Après avoir suivi les instructions de l’étape précédente pour préparer le fichier CSV à l’aide de l’éditeur PowerQuery, procédez comme suit :
    
1. Ouvrez le fichier Excel que vous avez créé à l’étape 2. 

2. Sous l’onglet **Accueil** , cliquez sur **Trier & Filtre**, puis sur **Filtrer**.
    
3. Dans la liste déroulante **Trier & Filtre** sur la colonne **Opérations** , effacez toutes les sélections, sélectionnez un ou plusieurs événements liés au partage suivants, puis cliquez sur **Ok**.
 
   - **SharingInvitationCreated**
   
   - **AnonymousLinkCreated**
   
   - **SecureLinkCreated**
   
   - **AddedToSecureLink** 
    
    Excel affiche les lignes des événements que vous avez sélectionnés.
    
4. Accédez à la colonne nommée **TargetUserOrGroupType** et sélectionnez-la. 
    
5. Dans la liste déroulante **Trier & filtre** , effacez toutes les sélections, sélectionnez **TargetUserOrGroupType:Guest**, puis cliquez sur **Ok**.
    
    Excel affiche désormais les lignes pour le partage d’événements ET où l’utilisateur cible se trouve en dehors de votre organisation, car les utilisateurs externes sont identifiés par la valeur **TargetUserOrGroupType:Guest**. 
  
> [!TIP]
> Pour les enregistrements d’audit affichés, la colonne **ObjectId** identifie la ressource qui a été partagée avec l’utilisateur cible ; par exemple  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`.
