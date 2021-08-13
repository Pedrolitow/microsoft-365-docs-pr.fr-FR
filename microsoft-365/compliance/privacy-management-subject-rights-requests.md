---
title: Gérer les demandes de droits d’objet dans la gestion de la confidentialité Microsoft (prévisualisation)
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: La solution de demande de droits de l’objet dans la gestion de la confidentialité Microsoft vous permet de rechercher des données personnelles et de collaborer sur la révision de contenu et la création de rapports.
ms.openlocfilehash: 4db9c744468cd75fb09bc8ff45ef9f15d26684a7c2b446557914be9e26b45ccc
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53807683"
---
# <a name="manage-subject-rights-requests-in-privacy-management-preview"></a>Gérer les demandes de droits de l’objet dans la gestion de la confidentialité (aperçu)

Dans cet article : découvrez comment utiliser la  solution de demande de droits d’objet pour rechercher des données personnelles dans votre environnement, collaborer sur des **révisions,** créer des rapports et  **automatiser** des tâches clés.

## <a name="purpose-of-subject-rights-requests"></a>Objectif des demandes de droits d’objet

La gestion de la confidentialité offre de puissantes fonctionnalités de demandes de droits d’objet pour vous aider à gérer les demandes des personnes cherchant à gérer leurs données personnelles au sein de votre organisation. Ces demandes sont parfois également appelées demandes d’objet de données (DSR), demandes d’accès de la personne à la personne de données (DSAR) ou demandes de droits du consommateur. La gestion de la confidentialité permet au personnel responsable de la réalisation des demandes de droits de l’objet d’identifier facilement les personnes responsables des données et de trouver leurs informations personnelles parmi les données de votre organisation dans Exchange, SharePoint, OneDrive et Teams.

La gestion de la confidentialité est unique pour vous aider à hiérarchiser les éléments à réviser dans les données que vous collectez pour ces demandes. La solution est sensible aux étiquettes Protection des données Microsoft de confidentialité, qui indiquent le contenu potentiellement confidentiel et qui peuvent nécessiter une révision spéciale, et signale les éléments avec ces étiquettes. Pour plus d’informations sur les étiquettes de sensibilité, voir [En savoir plus sur les étiquettes de sensibilité.](sensitivity-labels.md) En outre, la gestion de la confidentialité peut détecter et indicateur des éléments contenant les données de plusieurs personnes, où vous devrez peut-être redacter le contenu avant de le fournir à la personne à l’objet de données.

Une fois les données collectées et évaluées, vous pouvez sélectionner les éléments les plus pertinents à inclure dans vos rapports et exportations, et collaborer en toute sécurité avec d’autres membres de l’équipe pour déplacer les demandes vers la fin.

## <a name="get-started-with-subject-rights-requests"></a>Mise en place des demandes de droits d’objet

La gestion de la confidentialité fournit un hub central pour vos administrateurs de confidentialité afin de gérer les demandes de droits d’objet reçues par votre organisation.

Pour commencer à gérer un nouveau cas de demande ou pour travailler sur une demande en cours, visitez la page principale des demandes **de droits de l’objet.** Il fournit une vue d’ensemble visuelle des cas que votre équipe a créés au sein de la gestion de la confidentialité, de leur état (actif, fermé ou en retard), ainsi que des types de demandes, ainsi qu’une liste filtrable de toutes les demandes. Cette page vous permet également d’ouvrir une nouvelle demande.

Pour afficher des détails sur les cas ouverts, sélectionnez n’importe quelle demande dans la liste et choisissez **Go to request details**. Pour plus d’informations, voir [Examiner et prendre des mesures sur les demandes.](#review-and-take-action-on-requests)

Pour ouvrir une nouvelle demande, voir [Créer une demande.](#create-a-request)

## <a name="create-a-request"></a>Créer une demande

Les administrateurs de la gestion des droits de l’objet peuvent utiliser l’Assistant de gestion de la confidentialité pour créer des demandes. L’Assistant vous guide tout au long du processus de recherche de données personnelles sur une objet de données et de traitement de leur demande.

Les quatre étapes principales sont les suivantes:

### <a name="identify-the-data-subject"></a>Identifier la sujet de données

Indiquez le nom de l’objet qui a effectué la demande et spécifiez leur relation avec votre société.

### <a name="select-the-request-type"></a>Sélectionner le type de requête

Choisissez un type de demande en fonction de ce que la personne à qui vous souhaitez faire des données. Si leur demande concerne un règlement spécifique sur la confidentialité des données, vous pouvez également la sélectionner dans une liste fournie pour ajouter davantage de contexte. La définition d’une échéance (obligatoire) permettra de trier facilement les demandes en retard ou d’approche et de les résoudre en temps voulu. Les types de requête sont les suivants :

- **Access**: fournit un résumé des informations personnelles de la sujet de données détenues par votre organisation dans Microsoft 365.
- **Export**: fournit un résumé et une exportation des informations personnelles de la sujet de données, telles que collectées et annotées lors de la révision.
- **Liste marquée pour le suivi**: génère un résumé des fichiers qui peuvent nécessiter une action supplémentaire en dehors de la gestion de la confidentialité. Un exemple de scénario peut être si vous devez faciliter la suppression des informations personnelles de la personne objet de données selon leur demande.

### <a name="confirm-the-request-name"></a>Confirmer le nom de la demande

Cette étape vous permet de confirmer le nom de cette demande et d’ajouter une description facultative pour référence.

### <a name="review-and-finish"></a>Vérifier et terminer

Résumé de ce que vous avez entré au cours des étapes précédentes. N’importe quel champ peut être modifié avant de sélectionner **Créer une demande.**

À ce niveau, certaines propriétés peuvent être modifiées après la création de la demande, notamment l’échéance, le nom de la demande et la description, mais les propriétés clés telles que l’identité de l’objet ne peuvent pas être modifiées. Pour modifier une demande existante, recherchez-la dans votre liste de demandes sur la page Des demandes de droits d’objet et utilisez l’action Modifier les **détails de la demande.**

## <a name="review-and-take-action-on-requests"></a>Examiner et prendre des mesures sur les demandes

Une fois qu’une demande a été ouverte, la gestion de la confidentialité commence à rechercher Microsoft 365 données pour rechercher des données sur votre sujet. Pour voir les résultats initiaux, sélectionnez cette demande dans la liste et choisissez **Go to request details**. Ici, vous pouvez en savoir plus sur les propriétés de la demande, les résultats de recherche et l’état de la demande. Cette page deviendra également votre hub pour travailler et collaborer sur la gestion des fichiers trouvés, la création de rapports et d’exportation et la réalisation de la demande.

Les vignettes de cette page sont les suivantes :

- **Détails :** détails principaux sur la demande, y compris son échéance et sa date de demande, sa description et la réglementation de confidentialité associée.
- **Progression**: chronologie indiquant les étapes terminées et les tâches à terminer.
- **Résumé des estimations de données**: vue d’ensemble des données évaluées dans votre recherche. Pour en savoir plus sur ces informations, voir Afficher et modifier les requêtes de recherche.
- Éléments de priorité à réviser : le cas échéant, cela affiche des informations sur les éléments importants que la gestion de la confidentialité a détectés pour vous, y compris les informations confidentielles portant déjà une étiquette de confidentialité Microsoft, ou les éléments avec des données sur plusieurs personnes qui peuvent nécessiter une action. Les éléments de priorité se trouvent sous Données collectées en filtrant par la colonne « Types de priorité ».

### <a name="monitor-progress-and-complete-requests"></a>Surveiller l’avancement et les demandes terminées

Les demandes de droits de l’objet sont soumises à plusieurs étapes en cours d’exécution. Certaines étapes progressent automatiquement à mesure que la gestion de la confidentialité effectue l’évaluation des données, tandis que d’autres avancent lorsque les administrateurs et les collaborateurs en matière de droits de l’objet effectuent les étapes essentielles telles que la révision, la sélection et la préparation des fichiers.

Étant donné que les demandes peuvent avoir besoin d’être travaillées au fil du temps ou par plusieurs collaborateurs, la gestion de la confidentialité fournit des mises à jour continues sur l’état d’une demande et des conseils sur les étapes suivantes à suivre. Ces mises à jour peuvent être vues sur la page de présentation de la demande de droits d’objet. Les étapes de progression sont les suivantes.

#### <a name="data-estimate"></a>Estimation des données

L’estimation des données est l’étape initiale de l’évaluation des données. Une fois qu’une demande est créée, la gestion de la confidentialité identifie le nombre d’éléments dans les données de votre organisation qui incluent des correspondances potentielles avec votre personne objet de données et prend note de l’endroit où se trouve ces éléments Microsoft 365. Une fois l’estimation des données effectuée, vous pouvez prévisualiser les résultats et examiner les détails de votre requête de recherche d’origine. Si vous souhaitez modifier votre requête de recherche, consultez les instructions sous Afficher et [modifier les requêtes de recherche.](#view-and-edit-search-queries) Si vos résultats initiaux semblent satisfaisants, vous pouvez continuer à récupérer **des données.**

- Jusqu’à 10 000 éléments individuels peuvent être récupérés à partir de n’importe quelle recherche. Les fichiers associés à un élément correspondant (par exemple, les pièces jointes d’un e-mail) peuvent être comptabilisés dans votre total. Si votre recherche dépasse le seuil de nombre de fichiers, essayez de la réviser pour affiner son étendue. Pour plus [d’informations, voir](#view-and-edit-search-queries) la section Afficher et modifier les requêtes de recherche. Vous ne pourrez pas modifier votre requête de recherche une fois que vous lancerez l’étape de récupération des données.

#### <a name="retrieve-data"></a>Récupérer des données

Cette étape indique que la gestion de la confidentialité est en cours de récupération de vos données. Une fois l’analyse terminée, elle avance automatiquement pour passer **en revue les données.**

#### <a name="review-data"></a>Examiner les données

À ce stade, vos collaborateurs doivent passer en revue les résultats sous l’onglet Données collectées. Les étapes essentielles sont les suivantes :

- Choisissez d’inclure les éléments identifiés dans vos résumés et/ou d’exporter. Si une correspondance signalée n’est pas requise dans l’exportation ou le rapport, sélectionnez l’option « Exclure ». Si le contenu semble être un faux positif, vous pouvez choisir « Ne correspond pas » pour exclure le fichier de vos rapports finals et pointer l’élément comme un élément qui n’aurait pas dû être choisi par la demande. Pour définir l’état d’un élément, utilisez le menu d’action (ellipses verticales) en dehors de son nom et sélectionnez le choix souhaité. Si vous y êtes invité, ajoutez une note de référence interne pour expliquer votre décision. Les remarques sont requises lors de l’exclusion de fichiers.
- Utilisez **l’option Appliquer des balises** pour vous aider à identifier les éléments qui doivent être à l’attention. Les balises disponibles incluent les options fournies par le système, par exemple le marquage d’un élément pour le suivi, et peuvent inclure des balises personnalisées telles que définies sous Paramètres.
- Utilisez **Annotate pour** créer des marques ou des actions en ligne sur un fichier sélectionné. Par exemple, si vous avez besoin d’inclure un fichier pour un individu qui contient également les informations personnelles d’autres personnes, vous pouvez utiliser l’action de zone **(sous** le bouton Dessin dans la barre de commandes) pour noircir toutes les informations qui ne concernent pas la personne qui a effectué la demande. Lorsque vos modifications sont terminées, sélectionnez Inclure pour ajouter le fichier rédigé à la demande. Notez que l’annotation crée une copie du fichier, de sorte que rien dans le fichier d’origine ne soit modifié et reste à son emplacement d’origine. La copie est stockée dans votre objet blob Azure et restera pendant toute la période de rétention des données. Pour plus d’informations, voir [Rétention des données ci-dessous.](#data-retention)
- Pour passer en revue les notes d’un élément, sélectionnez-le et sélectionnez l’onglet Notes de fichier. Vous pouvez également utiliser l’option Ajouter une note de fichier pour créer un commentaire. Pour passer en revue ou ajouter des notes à un niveau de cas global, allez dans l’onglet Notes principal ci-dessus et utilisez **ajouter une note de cas.** Ces notes sont visibles pour les utilisateurs qui travaillent sur la demande, mais ne sont pas incluses dans le rapport final ou partagées avec la sujet des données.

Une fois que tous les éléments ont  été révisés et que leur statut a été définie, sélectionnez Révision complète pour ouvrir un volet de passage en revue dans lequel vous pouvez passer en revue un résumé des données et ajouter des notes pertinentes. Ces notes sont pour la conservation d’enregistrement interne et ne sont pas partagées avec la sujet de données. Sélectionnez à nouveau Révision complète pour passer à l’étape suivante. Les résumés de vos décisions seront fournis ultérieurement sous l’onglet Rapports.

#### <a name="generate-reports"></a>Générer des rapports

Cette étape indique que vos rapports sont générés. Lorsque vous avez terminé, vous pouvez les trouver sous **l’onglet Rapports.** Vos fichiers terminés ici peuvent être exportés pour remise à la personne qui a effectué la demande.

#### <a name="close-the-request"></a>Fermer la demande

Lorsque vous avez effectué les actions nécessaires pour résoudre votre demande de droits d’objet, choisissez **Fermer la demande.** Cela crée le rapport final, qui sera chiffré et mis à disposition dans l’onglet **Rapports.** Cela peut prendre un certain temps en fonction du nombre de fichiers dans la demande.

### <a name="view-and-edit-search-queries"></a>Afficher et modifier des requêtes de recherche

Pour afficher des informations détaillées sur la recherche de données derrière une demande de droits d’objet, sélectionnez Afficher les **détails** de la requête de recherche dans la carte récapitulatif d’estimation des données. Cela ouvre un volet récapitulant la requête et affichant d’autres détails sur ce qui a été trouvé.

Vous aurez la possibilité  ici d’afficher un aperçu des résultats de recherche pour voir le type de contenu qui sera renvoyé pour cette requête. Si vous déterminez que vous souhaitez modifier les propriétés de cette recherche et que vous n’avez pas commencé la phase Récupérer les données, vous pouvez utiliser l’option Modifier la requête **de** recherche. Cet Assistant offre la possibilité de modifier ou d’ajouter des propriétés pour l’identification des sujets de données, vos filtres et conditions de recherche, ainsi que les emplacements dans lesquels rechercher des données (notamment Exchange, SharePoint, OneDrive et/ou Teams). Utilisez ces options pour atteindre le niveau de spécificité souhaité. Vous pouvez passer en revue la version finale de votre nouvelle requête avant d’atteindre **Enregistrer.**

Lorsque vous avez terminé de modifier votre requête de recherche, une nouvelle recherche s’exécute pour remplacer vos résultats de recherche précédents. Cela réinitialise votre état dans la section Progression à la première étape, **l’estimation des données.** La nouvelle recherche peut prendre jusqu’à 60 minutes. Une fois l’analyse effectuée, vous verrez les résultats mis à jour sur la page de détails de la demande.

### <a name="data-retention"></a>Rétention de données

Les rapports générés par le biais de cet outil et les données associées, telles que les fichiers annotés enregistrés dans Azure, sont stockés pendant une durée spécifiée. Cette durée est définie au niveau global **jusqu’Paramètres** dans la section **Périodes** de rétention des données, qui vous permet de choisir entre 30 et 90 jours. Pour en savoir plus, [consultez La prise en charge de la gestion de la confidentialité.](privacy-management-setup.md)

## <a name="collaborate-on-requests-with-teams"></a>Collaborer sur des demandes avec Teams

La gestion de la confidentialité prend en charge la collaboration Microsoft Teams pour permettre à votre groupe de travailler ensemble sur des demandes de droits d’objet. Lorsque vous créez une demande, un canal Teams est automatiquement créé et associé à votre demande par défaut. Ici, vous pouvez discuter de la demande et partager en toute sécurité les entrées et les contributions à mesure qu’elle se déplace vers l’achèvement. Pour participer à la conversation, ouvrez votre demande et utilisez l’option **Conversation avec des** collaborateurs. Cela vous ouvre Microsoft Teams et vous place dans le canal Général pour le site d’équipe de votre demande de droits d’objet.

Pour consulter la liste des collaborateurs actifs qui peuvent afficher et contribuer à votre site d’équipe, dans votre demande de droits d’objet, ouvrez **l’onglet** Collaborateurs. Pour ajouter des utilisateurs supplémentaires afin de collaborer sur cette demande, sélectionnez l’option Ajouter un collaborateur.

Pour modifier le comportement par défaut de la génération de sites Teams lors de la création d’une demande de droits d’objet, sélectionnez l’engrenage **Paramètres** dans le coin supérieur droit de la page de demande de droits d’objet et sélectionnez **Teams collaboration** pour modifier le paramètre.

Vous pouvez également  utiliser l’option Partager en haut à droite dans une demande de droits d’objet pour mettre en boucle des personnes par Teams ou par courrier électronique, ou pour copier le lien vers la page dans la gestion de la confidentialité. Le partage via Teams vous permet de sélectionner un site Teams existant disponible pour votre compte, et de sélectionner un canal spécifique au sein de ce site où il publiera le lien vers ce cas avec n’importe quel message que vous fournissez.

## <a name="automate-subject-rights-request-tasks"></a>Automatiser les tâches de demande de droits de l’objet

Microsoft Power Automate est un service de flux de travail qui automatise les actions entre les applications et les services. Lorsque vous activez Power Automate de gestion de la confidentialité, vous pouvez automatiser des tâches importantes pour les cas et les utilisateurs. Pour en savoir plus sur Power Automate, visitez leur [site de documentation.](/power-automate/getting-started)

Les clients ayant Microsoft 365 abonnements qui incluent la gestion de la confidentialité n’ont pas besoin d’une autre licence Power Automate pour utiliser les modèles de gestion de la confidentialité Power Automate recommandés. Ces modèles peuvent être personnalisés pour prendre en charge votre organisation et couvrir les principaux scénarios de gestion de la confidentialité. Si vous choisissez d’utiliser des fonctionnalités Power Automate premium dans ces modèles, de créer un modèle personnalisé à l’aide du connecteur de conformité Microsoft 365 ou d’utiliser des modèles Power Automate pour d’autres domaines de conformité dans Microsoft 365, vous aurez peut-être besoin de plus de licences Power Automate.

Les modèles de Power Automate suivants sont inclus dans la gestion de la confidentialité :

- **Créer un enregistrement pour un** cas de gestion de la confidentialité dans ServiceNow : ce modèle est conçu pour les organisations qui souhaitent utiliser leur solution ServiceNow pour suivre les cas de demande de droits de l’objet. Vous serez invité à entrer les détails de votre instance ServiceNow. Une fois connectés à votre instance, les administrateurs de demandes de droits d’objet pourront créer un enregistrement pour le cas dans ServiceNow et personnaliser ce que le modèle remplira dans les champs sélectionnés si nécessaire. Pour plus d’informations sur le connecteur, voir la page de [référence du connecteur ServiceNow.](/connectors/service-now/)
- **Créer un rappel de calendrier**: ce modèle permet de définir des rappels d’échéance dans votre calendrier Outlook pour les demandes de droits de l’objet. L’outil rense faudra remplir certains détails à votre place à partir des propriétés de la demande, telles que le nom de la demande et sa date d’échéance. Vous pouvez ajouter des détails descriptifs, spécifier des destinataires et ajuster d’autres paramètres avancés.

### <a name="create-a-new-power-automate-flow-from-a-template"></a>Créer un flux de Power Automate à partir d’un modèle

Pour commencer, ouvrez la demande de droits d’objet avec qui vous souhaitez travailler, sélectionnez **Automatiser,** puis sélectionnez Gérer **Power Automate flux.** Le volet de flux s’ouvre. Utilisez l’option Nouveau et choisissez le modèle que vous souhaitez utiliser parmi les options disponibles. À partir de là, suivez les invites pour terminer l’installation.

Après avoir enregistrez une instance du modèle, vous devez l’exécuter à partir de la page de détails de la demande de droits de l’objet afin que l’instance de flux dispose du contexte et de l’ID qui s’y rapportent. Ouvrez la demande, revenir au menu **Automatiser,** sélectionnez le modèle, puis **sélectionnez Exécuter le flux.** Vous pouvez voir vos activités passées en sélectionnant **Voir l’activité d’exécuter le flux.**

### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate de données

En partageant un flux Power Automate, vous pouvez ajouter un autre propriétaire et lui permettre de modifier, mettre à jour et supprimer le flux. Tous les propriétaires peuvent également accéder à l’historique d’exécuter et ajouter ou supprimer d’autres propriétaires. Pour partager un flux, ouvrez la demande de droits d’objet avec qui vous souhaitez travailler, sélectionnez **Automatiser,** puis gérez **Power Automate flux.** Dans ce volet, vous pouvez sélectionner un flux existant, puis utiliser l’option Partager pour ajouter un utilisateur ou un groupe.

Ce volet vous permet également de gérer les connexions incorporées aux services utilisés dans Power Automate flux. La modification de ces paramètres peut affecter votre capacité à exécuter le flux.

### <a name="edit-or-delete-power-automate-flow"></a>Modifier ou supprimer Power Automate flux

Pour ajuster les détails d’un flux Power Automate, ouvrez la demande de droits d’objet, sélectionnez **Automatiser** et sélectionnez Gérer **Power Automate flux.** Dans ce volet, vous pouvez sélectionner un flux existant pour afficher les détails. Utilisez Modifier dans n’importe quelle section pour modifier les propriétés, puis enregistrez.

Pour supprimer entièrement le flux, utilisez **l’option Supprimer.** Il supprime le flux pour tous les propriétaires et le désinstalle pour tous les utilisateurs. Les instances de flux précédentes continueront à s’exécuter pour éviter la perte de données. Vous pouvez confirmer votre choix avant la fin de la suppression.

## <a name="data-matching"></a>Correspondance de données

Grâce à la correspondance des données, les organisations peuvent activer la solution de gestion de la confidentialité pour identifier les personnes liées aux données en fonction des valeurs de données fournies exactes. Cela peut vous aider à améliorer la précision de la localisation du contenu de la sujet des données à la fois pour votre personnel interne et pour les utilisateurs externes avec qui vous interagissez. Il simplifie également la nécessité de fournir manuellement des champs lors de la création d’une demande de droits d’objet, et fournit du contexte dans les demandes de droits d’objet et pour la vignette Vue d’ensemble qui présente vos éléments avec le contenu de la personne ayant le plus de données. Pour en savoir plus sur cette vue, voir [Rechercher et visualiser vos données.](privacy-management-data-profile.md#items-with-the-most-data-subject-content)

Pour utiliser la fonctionnalité de correspondance de données, vous devez être membre du groupe de rôles Gestion de la confidentialité. Sélectionnez l’icône d’engrenage des paramètres dans le coin supérieur droit de la page principale des demandes de droits de l’objet, puis sélectionnez **Correspondance de données.** À partir de là, vous devrez définir le schéma de données personnelles et fournir un téléchargement de données personnelles, comme illustré ci-dessous. Notez que vous pouvez ajouter des éléments et supprimer des éléments que vous ajoutez via l’interface utilisateur. Toutefois, vous ne pouvez pas modifier un élément en place à partir de l’interface utilisateur pour le moment.

### <a name="prepare-for-data-import"></a>Préparer l’importation de données

Avant de définir le schéma ou de télécharger des données, vous devez identifier la source de vos informations de sujet de données. Le format de fichier requis est .csv, qui peut être lu par une application telle que Microsoft Excel. Structurez cette exportation de sorte que vos en-têtes de colonne apparaissent dans la première ligne. Ces en-têtes doivent inclure les noms des attributs de votre schéma de données personnelles. Vérifiez le format des données dans chaque champ. Si l’une des données contient des virgules, entourez ces valeurs de guillemets doubles pour vous assurer qu’elles ne seront pas séparées.

### <a name="define-the-personal-data-schema"></a>Définir le schéma de données personnelles

Le schéma de données personnelles décrit les attributs de vos sujets de données. Télécharger ce schéma sur le premier onglet de la zone des paramètres de correspondance de données. Les fichiers requis incluent un **fichier** XML de schéma de données personnelles et un fichier XML **de package** de règles.

#### <a name="personal-data-schema-xml"></a>XML de schéma de données personnelles

Le fichier de schéma de données personnelles est un fichier XML qui définit les noms de colonne attendus.

- Nommez ce fichier de *schémapdm.xml*.
- Définissez chaque nom de colonne à l’aide de la balise Nom du champ, comme dans l’exemple ci-dessous.
- Utilisez searchable = « true » pour les champs que vous souhaitez rechercher, jusqu’à un maximum de cinq champs. Au moins l’un de vos noms de champ doit pouvoir faire l’être. Exemple de syntaxe `\<Field name="" searchable=""/>` : .
- Le schéma de données personnelles possède une section de balise DataStore. Quatre champs obligatoires doivent être mappés à vos noms de champs : primaryKeyField, upnField, firstNameField, lastNameField.

Par exemple, le fichier XML suivant définit un exemple de schéma, avec cinq champs spécifiés comme utilisables dans une recherche : PatientID, MRN, SSN, Téléphone et DOB. Le champ primaryKeyField est mappé sur PatientID, upnField est mappé sur MRN, firstNameField est mappé sur FirstName et lastNameField est mappé sur LastName.

Vous pouvez copier, modifier et utiliser notre exemple.

 ```xml
<PdmSchema xmlns="http://schemas.microsoft.com/office/2020/pdm">
      <DataStore name="Patientrecords" description="Schema for patient records" version="1" primaryKeyField="PatientID" upnField="MRN" firstNameField="FirstName" lastNameField="LastName">
            <Field name="PatientID" searchable="true"/>
            <Field name="MRN" searchable="true" />
            <Field name="FirstName" />
            <Field name="LastName" />
            <Field name="SSN" searchable="true" />
            <Field name="Phone" searchable="true" />
            <Field name="DOB" searchable="true" />
            <Field name="Gender" />
            <Field name="Address" />
      </DataStore>
</PdmSchema>
 ```

#### <a name="rule-package-xml"></a>XML de package de règles

Lorsque vous définissez votre package de règles, veillez à référencer correctement votre fichier de schéma de données personnelles créé ci-dessus : pdm.xml. Dans l’exemple de package de règles XML suivant, les champs suivants doivent être personnalisés pour créer votre type sensible de correspondance de données :

- **RulePack id**  &  **ID PrivacyMatch**: utiliser new-GUID pour générer un GUID.
- **Datastore : ce** champ spécifie le magasin de données de recherche de correspondance de données personnelles à utiliser. Indiquez le nom datastore défini d’un schéma de données personnelles configuré.
- **idMatch**: ce champ pointe vers l’élément principal de la correspondance de données personnelles.
  - **Correspondances**: spécifie le champ à utiliser dans la recherche exacte. Fournissez un nom de champ utilisable dans une recherche à partir du schéma de données personnelles.
  - **Classification**: ce champ spécifie la correspondance de type sensible qui déclenche la recherche de correspondance de données personnelles. Vous pouvez fournir le nom ou le GUID d’un type d’informations sensibles intégré ou personnalisé. Afin d’éviter les problèmes de performances, si vous utilisez un type d’informations sensibles personnalisé comme élément classification dans la correspondance de données personnelles, n’utilisez pas un type d’informations sensibles personnalisé qui correspondra à un grand pourcentage de contenu (par exemple, « n’importe quel nombre » ou « tout mot de cinq lettres »). Nous vous recommandons d’ajouter des mots clés de prise en charge ou d’inclure la mise en forme dans la définition du type d’informations sensibles de classification personnalisé.
- **Correspondance**: ce champ pointe vers des preuves supplémentaires trouvées à proximité d’idMatch.
  - **Correspondances**: indiquez un nom de champ quelconque dans le schéma de données personnelles de DataStore.
- **Ressource**: cette section spécifie le nom et la description du type sensible dans plusieurs paramètres régionaux.
  - **idRef**: fournir un GUID pour l’ID ExactMatch.
  - **Nom & descriptions :** personnaliser selon les besoins.

Dans notre exemple de fichier XML de package de règles ci-dessous, nous faisons référence à l’exemple de fichier pdm.xml de l’étape précédente qui crée le fichier XML de schéma de données personnelles :

- **Datastore**: le nom de dataStore fait référence au fichier de schéma que nous avons créé précédemment : dataStore = « PatientRecords ».
- **idMatch**: la valeur idMatch fait référence à un champ utilisable dans une recherche répertorié dans le fichier pdm.xml que nous avons créé précédemment : idMatch correspond à = « SSN ».
  - **Classification**: la valeur de classification fait référence à un type d’informations sensibles existant ou personnalisé : classification = « Numéro de sécurité sociale (SSN) des États-Unis ». (en l’occurrence, nous utilisons le type d’informations sensibles existant pour le numéro de sécurité sociale aux États-Unis).

Créez un package de règles au format XML (avec codage Unicode), comme dans l’exemple de code suivant. Vous pouvez copier, modifier et utiliser cet exemple.

 ```xml
<RulePackage xmlns="http://schemas.microsoft.com/office/2020/pdm">
  <RulePack id="fd098e03-1796-41a5-8ab6-198c93c62b21">
    <Version build="0" major="2" minor="0" revision="0" />
    <Publisher id="eb553734-8306-44b4-9ad5-c388ad970528" />
    <Details defaultLangCode="en-us">
      <LocalizedDetails langcode="en-us">
        <PublisherName>IP DLP</PublisherName>
        <Name>Health Care PDM Rulepack</Name>
        <Description>This rule package contains the Personal Data Match sensitive type for health care sensitive types.</Description>
      </LocalizedDetails>
    </Details>
  </RulePack>
  <Rules>
    <PrivacyMatch id = "E1CC861E-3FE9-4A58-82DF-4BD259EAB381" patternsProximity = "300" dataStore ="PatientRecords" recommendedConfidence = "65" >
      <Pattern confidenceLevel="65">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
      </Pattern>
      <Pattern confidenceLevel="75">
        <idMatch matches = "SSN" classification = "U.S. Social Security Number (SSN)" />
        <Any minMatches ="3" maxMatches ="6">
          <match matches="PatientID" />
          <match matches="MRN"/>
          <match matches="FirstName"/>
          <match matches="LastName"/>
          <match matches="Phone"/>
          <match matches="DOB"/>
        </Any>
      </Pattern>
    </PrivacyMatch>
    <LocalizedStrings>
      <Resource idRef="E1CC861E-3FE9-4A58-82DF-4BD259EAB381">
        <Name default="true" langcode="en-us">Patient SSN Exact Match.</Name>
        <Description default="true" langcode="en-us">PDM Sensitive type for detecting Patient SSN.</Description>
      </Resource>
    </LocalizedStrings>
  </Rules>
</RulePackage>
 ```

### <a name="upload-personal-data"></a>Télécharger données personnelles
Après avoir défini le schéma de données  personnelles, vous pouvez effectuer le chargement des données personnelles sous le deuxième onglet de la page des paramètres de correspondance de données. Lorsque vous **sélectionnez Ajouter,** choisissez le schéma personnel que vous avez défini à la première étape, puis téléchargez le fichier contenant les données personnelles.

Vous pouvez charger ces données personnelles en choisissant un fichier local ou en fournissant une URL SAS à un emplacement Stockage Microsoft Azure existant contenant votre fichier de données personnelles.
Si vous avez préparé un fichier en tant que première étape de ce processus qui est conforme au schéma créé, vous pouvez utiliser ce fichier pour le chargement.
