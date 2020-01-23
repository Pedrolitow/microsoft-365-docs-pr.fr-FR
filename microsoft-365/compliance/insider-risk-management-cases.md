---
title: Cas d’Insider de gestion des risques (aperçu)
description: En savoir plus sur les cas de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: e6fd3dd08ff5170a3b0e2afcd97ec788c2aebd93
ms.sourcegitcommit: 3dca80f268006658a0b721aa4f6df1224c7964dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "41259866"
---
# <a name="insider-risk-management-cases-preview"></a>Cas d’Insider de gestion des risques (aperçu)

Les cas sont le cœur de la gestion des risques initiés et vous permettent d’approfondir et de prendre des mesures sur les problèmes générés par les indicateurs de risque définis dans vos stratégies. Les incidents sont créés manuellement à partir d’alertes dans les situations où une autre action est nécessaire pour résoudre un problème lié à la conformité pour un employé. Chaque cas est limité à un seul employé et plusieurs alertes peuvent être ajoutées à un incident existant ou à un autre cas. Après avoir examiné les détails d’un cas, vous pouvez prendre une mesure en envoyant un avis à l’employé, en le résolvant comme inoffensif ou en effectuant une enquête sur les données ou les employés.

## <a name="case-dashboard"></a>Tableau de bord de cas

Le **tableau de bord des cas** de gestion des risques Insiders vous permet d’afficher et de prendre des mesures dans les cas. Chaque widget de rapport du tableau de bord affiche des informations pour les 30 derniers jours.

- **Cas actifs**: nombre total de cas actifs en cours d’enquête.
- **Cas au cours des 30 derniers jours**: nombre total de cas créés, triés par état *actif* et *fermé* .
- **Statistics**: durée moyenne des cas actifs, indiquée en heures, jours ou mois.

La file d’attente de cas répertorie tous les dossiers actifs et fermés de votre organisation, en plus de l’état actuel des attributs case suivants :

- **Nom**de la casse : nom de l’incident, défini lorsqu’une alerte est confirmée et que le cas est créé.  
- **Status**: état *actif* ou *fermé*.
- **User**: employé pour le cas.
- **Date/heure d’ouverture**: temps écoulé depuis l’ouverture du cas.
- **Total des alertes de stratégie**: nombre de correspondances de stratégie incluses dans le cas. Ce nombre peut augmenter si de nouvelles alertes sont ajoutées à l’incident.
- **Dernière mise à jour**: le temps écoulé depuis qu’il y a eu une remarque de cas ajoutée ou modifié dans l’état du cas.
- **Dernière mise à jour par**: le nom de l’analyste ou de l’investigateur de gestion des risques Insiders qui a mis à jour le cas.

![Tableau de bord des cas de gestion des risques Insiders](media/insider-risk-cases-dashboard.png)

Utilisez le contrôle de **recherche** pour rechercher des noms de cas spécifiques et utilisez le filtre de cas pour trier les cas par les attributs suivants :

- Statut
- Cas d’ouverture, date de début et date de fin de l’heure
- Date de dernière mise à jour, date de début et date de fin

## <a name="investigate-a-case"></a>Examiner un cas

Une enquête approfondie sur les alertes de gestion des risques initiés est essentielle pour prendre des mesures correctives appropriées. Les cas d’Insider de gestion des risques constituent l’outil de gestion centralisée pour approfondir l’historique des activités relatives aux risques des employés et les détails des alertes, et pour explorer le contenu et les messages exposés aux risques. Les analystes et les enquêteurs de risques utilisent également des cas pour centraliser les commentaires et les notes et traiter la résolution des incidents. 

La sélection d’un cas ouvre les outils de gestion de cas et permet aux analystes et aux enquêteurs d’approfondir les détails des cas.

### <a name="case-overview"></a>Présentation de l’incident

L’onglet de **Présentation du cas** résume l’activité d’alerte et l’historique des niveaux de risque pour le cas. Le widget **alertes** affiche la correspondance de stratégie pour le cas, y compris l’état de l’alerte, la gravité du risque d’alerte et le moment où l’alerte a été détectée. Le graphique de l' **historique des niveaux de risques** affiche le niveau de risque de l’utilisateur au cours des 30 derniers jours. Le graphique en courbes permet aux analystes et aux investigateurs de voir rapidement la tendance du risque global de l’utilisateur au fil du temps. Le widget **contenu d’activité des risques** résume les types de données et le contenu des alertes ajoutées au cas. Ce widget offre une vue complète de l’ensemble des données et du contenu en risque dans le cas.

Le volet de **Détails des cas** est disponible sur tous les onglets de gestion des dossiers et récapitule les détails de l’incident pour les analystes et les investigateurs de risque. Elle comprend les éléments suivants :

- **Nom**de la casse : nom de l’incident, préfixé avec un numéro de séquence de casse généré automatiquement et le nom du risque associé au modèle de stratégie correspondant à la première alerte confirmée. 
- **État**de la demande de devis : état *actif* ou *fermé*.
- **Note de risque de l’utilisateur**: niveau de risque calculé actuel de l’utilisateur pour le cas. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur.
- **Alertes confirmées**: liste des alertes pour l’utilisateur confirmée pour le cas.
- **Contenu à risque**: liste de contenu, triée par sources et types de contenu. Par exemple, pour le contenu d’alerte case dans SharePoint Online, vous pouvez voir des noms de dossier ou de fichier répertoriés qui sont associés à l’activité risque pour les alertes dans le cas.

![Détails des cas d’Insider gestion des risques](media/insider-risk-case-details.png)

### <a name="alerts"></a>Alertes

L’onglet **alertes** résume les alertes actuelles incluses dans le cas. De nouvelles alertes peuvent être ajoutées à un cas existant et elles seront ajoutées à la file d’attente d' **alerte** à mesure qu’elles sont affectées. Les attributs d’alerte suivants sont répertoriés dans la file d’attente :

- Statut
- Gravité
- Heure de détection

Sélectionnez une alerte dans la file d’attente pour afficher la page Détails de l' **alerte** .

Utilisez le contrôle de recherche pour rechercher des noms d’alerte pour un texte spécifique et utilisez le filtre d’alerte pour trier les cas par les attributs suivants :

- Statut
- Gravité
- Heure de détection, date de début et date de fin

### <a name="user-activity"></a>Activité utilisateur

L’onglet activité de l' **utilisateur** est l’un des outils les plus puissants pour l’analyse et l’enquête sur les risques internes pour les cas de la solution de gestion des risques Insiders. Cet onglet est conçu pour permettre un examen rapide d’un incident, notamment une chronologie historique de toutes les alertes, les détails de toutes les alertes, le score de risque actuel de l’utilisateur dans le cas et des contrôles permettant d’appliquer les risques dans le cas.

![Activité des utilisateurs de gestion des risques Insiders](media/insider-risk-user-activities.png)

1. **Filtres date et heure**de la fenêtre : par défaut, les six derniers mois d’alertes confirmées dans le cas s’affichent dans le graphique d’activité de l’utilisateur. Vous pouvez facilement filtrer l’affichage graphique avec les contrôles de curseur aux deux extrémités de la fenêtre de graphique ou en définissant des dates de début et de fin spécifiques dans le contrôle de filtre de graphique.
2. **Activité et détails de l’alerte de risque**: les activités de risque s’affichent visuellement sous forme de bulles colorées dans le graphique d’activité de l’utilisateur. Les bulles sont créées pour différentes catégories de risques et la taille des bulles est proportionnelle au nombre d’activités à risque pour la catégorie. Sélectionnez une bulle pour afficher les détails de chaque activité de risque. Les détails sont les suivants :
    - **Date** de l’activité de risque.
    - Catégorie de l' **activité de risque**. Par exemple, des *courriers électroniques avec des pièces jointes envoyées à l’extérieur de l’organisation* ou des *fichiers téléchargés à partir de SharePoint Online*.
    - **Score de risque** de l’alerte. Ce score est le score numérique du niveau de gravité des risques d’alerte.
    - Nombre de **fichiers** ou d' **e-mails** associés à l’alerte. Des liens vers chaque fichier ou courrier électronique associé à l’activité de risque sont également disponibles.
3. **Légende**de l’activité des risques : dans la partie inférieure du graphique d’activité de l’utilisateur, une légende de couleur vous permet de déterminer rapidement la catégorie de risque pour chaque alerte.
4. **Chronologie**de l’activité des risques : la chronologie complète de toutes les alertes de risque associées à l’incident est répertoriée, y compris tous les détails disponibles dans la bulle d’alerte correspondante.
5. **Actions de cas**: les options de résolution de l’incident figurent dans la barre d’outils action de l’incident. Vous pouvez résoudre un incident, envoyer une notification par courrier électronique à l’employé ou escalader le cas à une enquête sur les données ou les employés.

### <a name="content-explorer"></a>Explorateur de contenu

L’onglet **Explorateur de contenu** permet aux analystes et aux enquêteurs de vérifier les copies de tous les fichiers et messages électroniques associés à des alertes de risque. Par exemple, si une alerte est créée lorsqu’un employé télécharge des centaines de fichiers à partir de SharePoint Online vers un périphérique USB et que l’activité déclenche une alerte de stratégie, tous les fichiers téléchargés pour l’alerte sont capturés et copiés dans le cas de la gestion des risques inSided à partir de sources de stockage d’origine.

L’Explorateur de contenu est un outil puissant doté de fonctionnalités de recherche et de filtrage de base et avancées. Pour en savoir plus sur l’utilisation de l’Explorateur de contenu, reportez-vous à l' [Insider Risk Management content Explorer](insider-risk-management-content-explorer.md).

![Explorateur de contenu de cas de gestion des risques Insiders](media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Notes de cas

L’onglet **Remarques** dans le cas correspond à l’endroit où les analystes et les investigateurs des risques partagent des commentaires, des commentaires et des informations sur leur travail pour le cas. Les notes sont des ajouts permanents à un cas et ne peuvent pas être modifiées ou supprimées après l’enregistrement de la note. Lorsqu’un cas est créé à partir d’une alerte, les commentaires entrés dans la boîte de dialogue **confirmer l’alerte et créer un cas de risque Insider** sont automatiquement ajoutés en tant que note de cas.

Le tableau de bord des notes de cas affiche des notes par l’utilisateur qui a créé la note et le temps écoulé depuis l’enregistrement de la note. Pour rechercher un mot clé spécifique dans le champ de texte note de cas, utilisez le bouton **Rechercher** du tableau de bord de cas et entrez un mot clé spécifique.

Pour ajouter une note à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez l’onglet **notes de cas** .
3. Sélectionnez **Ajouter une note de cas**.
4. Dans la boîte de dialogue **Ajouter une note de cas** , tapez votre remarque pour le cas. Sélectionnez **Enregistrer** pour ajouter la note au cas ou sélectionnez **Annuler** fermer sans enregistrer la note dans le cas.

### <a name="contributors"></a>Collaborateurs

L’onglet **collaborateurs** dans le cas est l’endroit où les analystes et les enquêteurs peuvent ajouter d’autres réviseurs au cas. Par défaut, tous les utilisateurs auxquels sont affectés les rôles **analystes de gestion des risques Insider** et **inSided Management investigations** sont répertoriés en tant que contributeurs pour chaque cas actif et fermé.

Tous les cas de gestion des risques initiaux doivent être gérés avec les contrôles d’accès appropriés en place afin de préserver la confidentialité et l’intégrité de l’enquête. Pour faciliter le contrôle d’accès des cas, les utilisateurs sont affectés à l’un des deux types d’accès aux cas suivants :

- **Accès permanent**: l’accès permanent est automatiquement accordé aux utilisateurs avec les rôles des **analystes de gestion des risques internes** et des **investigateurs de gestion des risques Insiders** lorsque le cas est créé à partir d’une alerte. L’accès permanent accorde le contrôle total de l’incident pendant la durée de vie du cas et permet d’ajouter d’autres contributeurs de cas.
- **Accès temporaire**: l’accès temporaire est accordé uniquement aux utilisateurs par des collaborateurs qui disposent d’un accès permanent pour le cas. En règle générale, ce niveau d’accès est accordé à l’utilisateur qui doit ajouter des notes à un cas. Les contributeurs disposant d’un accès temporaire disposent du contrôle de gestion des dossiers sauf :
    - Autorisation de confirmer ou d’ignorer les alertes
    - Autorisation de modifier les collaborateurs pour les cas
    - Autorisation d’afficher les fichiers et les messages dans l’Explorateur de contenu

Pour ajouter un collaborateur à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez l’onglet **collaborateurs** .
3. Sélectionnez **Ajouter un collaborateur**.
4. Dans la boîte de dialogue **Ajouter un collaborateur** , commencez à taper le nom de l’utilisateur que vous souhaitez ajouter, puis sélectionnez l’utilisateur dans la liste des utilisateurs suggérés. Cette liste est générée à partir de l’Azure Active Directory de votre abonnement client.
5. Dans la boîte de dialogue **Ajouter un collaborateur** , sélectionnez le niveau d’accès du collaborateur. Vous pouvez sélectionner **permanent** ou **temporaire**.
6. Sélectionnez **Ajouter** pour ajouter l’utilisateur en tant que collaborateur ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans ajouter l’utilisateur en tant que collaborateur.

## <a name="case-actions"></a>Actions de cas

Les analystes et les enquêteurs de risques peuvent agir sur un cas selon l’une des différentes méthodes, selon la gravité du cas, l’historique des risques et les recommandations de votre organisation. Dans certains cas, il se peut que vous deviez transmettre un cas à un employé ou à une enquête de données pour collaborer avec d’autres domaines de votre organisation et approfondir les activités à risque. La gestion des risques initiés est étroitement intégrée aux autres fonctionnalités de conformité de Microsoft 365 pour vous aider à gérer la résolution de bout en bout.

### <a name="send-a-notice"></a>Envoyer une notification

Dans la plupart des cas, les actions de l’employé qui créent des alertes de correspondance de stratégie sont involontaires ou accidentelles. L’envoi d’un avis de rappel à l’employé par courrier électronique est une méthode efficace pour documenter l’examen et l’action des cas, ainsi qu’une méthode pour rappeler les employés des stratégies d’entreprise ou pour les diriger vers la formation de réactualisation. Les notifications sont générées à partir de [modèles de notification que vous créez](insider-risk-management-notices.md) pour votre infrastructure de gestion des risques Insiders.

N’oubliez pas que l’envoi d’une notification à un employé ***ne*** résout pas le cas comme étant *fermé*. Dans certains cas, vous souhaiterez peut-être laisser un cas ouvert après l’envoi d’une notification à un employé afin de rechercher des activités à risque supplémentaires sans ouvrir de nouveau cas. Si vous souhaitez résoudre un incident après avoir envoyé un avis, vous devez sélectionner l’option **résoudre l’incident** comme une étape de suivi après l’envoi d’une notification.

Pour envoyer une notification à l’employé affecté à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **Envoyer une notification par courrier électronique** sur la barre d’outils action de cas.
3. Dans la boîte de dialogue **Envoyer une notification par courrier électronique** , sélectionnez le modèle de liste déroulante **choisir un modèle d’avis** pour sélectionner le modèle d’avertissement de l’avis. Cette sélection pré-remplit les autres champs de l’avis.
4. Examinez les champs notice et mettez à jour le cas échéant. Les valeurs entrées ici remplaceront les valeurs du modèle.
5. Sélectionnez **Envoyer** pour envoyer l’avis à l’employé ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans envoyer l’avis à l’employé. Toutes les notifications envoyées sont ajoutées à la file d’attente de notes dans le tableau de bord **Notes** de cas.

### <a name="escalate-for-investigation"></a>Escalade de l’enquête

Escaladez le cas à l’enquête d’un employé dans des situations où un examen juridique supplémentaire est nécessaire pour l’activité des risques de l’employé. Cette escalade ouvre un nouveau cas eDiscovery avancé dans votre organisation Microsoft 365. Advanced eDiscovery fournit un flux de travail de bout en bout pour conserver, collecter, examiner, analyser et exporter du contenu réactif aux enquêtes juridiques internes et externes de votre organisation. Il permet également à votre équipe juridique de gérer l’ensemble du flux de travail de notification de suspension légale pour communiquer avec les dépositaires impliqués dans un cas. L’affectation d’un relecteur en tant que dépositaire dans un cas avancé eDiscovery créé à partir d’un cas de gestion des risques Insiders permet à votre équipe juridique de prendre les mesures appropriées et de gérer la conservation du contenu. Pour en savoir plus sur les cas avancés de découverte électronique, consultez la rubrique [vue d’ensemble de l’EDsicovery avancé dans Microsoft 365](overview-ediscovery-20.md).

Pour escalader un cas à une enquête d’un employé :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **escalader pour l’enquête** sur la barre d’outils action de cas.
3. Dans la boîte de dialogue **escalade de l’enquête** , entrez un nom pour la nouvelle enquête de l’employé. Si nécessaire, entrez des remarques sur le cas et sélectionnez **escalade**.
5. Sélectionnez **confirmer** pour créer le cas d’enquête des employés ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans créer de cas d’enquête d’employé.

Une fois que le cas de gestion des risques initiés a été remonté vers un nouveau cas d’enquête chez les employés, vous pouvez passer en revue le nouveau cas dans la zone**avancé** de **découverte électronique** > dans le centre de conformité Microsoft 365.

### <a name="resolve-the-case"></a>Résoudre le cas

Une fois que les analystes et les enquêteurs ont terminé leur examen et leur enquête, un cas peut être résolu afin de prendre des mesures sur toutes les alertes actuellement incluses dans le cas. La résolution d’un cas ajoute une classification de résolution, le statut de la case à *fermeture*et les motifs d’action de résolution sont automatiquement ajoutés à la file d’attente de notes dans le tableau de bord **Notes** de cas. Les cas sont résolus comme suit :

- **Bénigne**: la classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme faible risque, non sérieux ou faux positif.
- **Violation de stratégie confirmée**: classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme risquées, graves ou le résultat d’un but malveillant.

Pour résoudre un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **résoudre le cas** dans la barre d’outils action de cas.
3. Dans la boîte de dialogue **résoudre l’incident** , sélectionnez le contrôle **résoudre en tant que** liste déroulante pour sélectionner la classification de résolution pour le cas. Les options sont **inoffensives** ou une **violation de stratégie confirmée**.
4. Dans la boîte de dialogue **résoudre l’incident** , entrez les motifs de la classification de résolution dans le champ texte de l' **action effectuée** .
5. Sélectionnez **résoudre** pour fermer le cas ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans résoudre le cas.
