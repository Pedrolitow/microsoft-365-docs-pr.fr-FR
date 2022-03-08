---
title: Examiner et corriger les alertes de conformité des communications
description: Examiner et corriger les alertes de conformité des communications dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: fc236ea646e9da487c5e2e1178ddf9ca460cb4ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325136"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Examiner et corriger les alertes de conformité des communications

Une fois que vous avez configuré vos stratégies de conformité des communications, vous commencez à recevoir des alertes dans le Centre de conformité Microsoft 365 pour les problèmes de message qui correspondent à vos conditions de stratégie. Suivez les instructions de flux de travail ici pour examiner et corriger les problèmes d’alerte.

## <a name="investigate-alerts"></a>Examiner des alertes

La première étape pour examiner les problèmes détectés par vos stratégies consiste à examiner les alertes de conformité des communications dans le Centre de conformité Microsoft 365. Il existe plusieurs domaines dans le domaine de la solution de conformité des communications pour vous aider à examiner rapidement les alertes, selon la façon dont vous préférez afficher le regroupement d’alertes :

- **Page** Stratégie de conformité des communications : lorsque vous vous connectez au [Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365, sélectionnez Conformité des communications pour afficher **la page Stratégie** de conformité des communications. Cette page affiche les stratégies de conformité des communications configurées pour Microsoft 365 organisation et des liens vers les modèles de stratégie recommandés. Chaque stratégie répertoriée inclut le nombre d’alertes qui doivent être revue, le nombre d’éléments résordés et résolus, l’état de la stratégie et la date et l’heure de la dernière analyse de stratégie. La sélection d’une stratégie affiche toutes les alertes en attente pour les correspondances à la stratégie, une alerte spécifique pour lancer la page de détails de la stratégie et démarrer les actions de correction.
- **Alertes :** accédez à **Communication** **complianceAlerts** >  pour afficher les 30 derniers jours d’alertes regroupées par correspondances de stratégie. Cet affichage vous permet de voir rapidement les stratégies de conformité des communications qui génèrent la plupart des alertes classées par gravité. Pour démarrer les actions de correction, sélectionnez la stratégie associée à l’alerte pour lancer la page **détails de la stratégie** . À partir de la page **Détails** de la stratégie, vous pouvez consulter un résumé des activités de **la page Vue** d’ensemble, examiner et agir sur les messages d’alerte sur **la page En** attente, ou passer en revue l’historique des alertes fermées sur la page **Résolu** .
- **Rapports :** accédez à **Communications** **complianceReports** >  pour afficher les widgets de rapport de conformité des communications. Chaque widget fournit une vue d’ensemble des activités et des états de conformité des communications, y compris l’accès à des informations plus approfondies sur les correspondances de stratégie et les actions de correction.

### <a name="using-filters"></a>Utilisation de filtres

L’étape suivante consiste à trier les messages de sorte qu’il soit plus facile de rechercher des alertes. Dans la page **Détails** de la stratégie, la conformité des communications prend en charge le filtrage à plusieurs niveaux pour plusieurs champs de message pour vous aider à examiner rapidement les messages avec des correspondances de stratégie. Le filtrage est disponible pour les éléments en attente et résolus pour chaque stratégie configurée. Vous pouvez configurer des requêtes de filtrage pour une stratégie ou configurer et enregistrer des requêtes de filtrage personnalisées et par défaut à utiliser dans chaque stratégie spécifique. Une fois que vous avez configuré les champs d’un filtre, les champs de filtre affichés en haut de la file d’attente de messages d’alerte peuvent être configurés pour des valeurs de filtre spécifiques.

Pour le filtre de date, la date et l’heure des événements sont répertoriées au temps universel coordonné (UTC). Lors du filtrage des messages pour les affichages, la date/l’heure locale de l’utilisateur demandeur détermine les résultats en fonction de la conversion de la date/heure locale de l’utilisateur en heure UTC. Par exemple, si un utilisateur de l’heure d’été pacifique (PDT) des États-Unis filtre un rapport du 30/08/2021 au 31/08/2021 à 00:00, le rapport inclut les messages du 30/08/2021 07:00 UTC au 31/08/2021 07:00 UTC. Si le même utilisateur se trouvait à l’heure d’été est (EDT) des États-Unis lors du filtrage à 00:00, le rapport inclut les messages du 30/08/2021 04:00 UTC au 31/08/2021 04:00 UTC.

#### <a name="filter-details"></a>Détails du filtre

Les filtres de conformité des communications vous permettent de filtrer et de trier les messages d’alerte pour des actions d’investigation et de correction plus rapides. Le filtrage est disponible sous les **onglets En** **attente et** Résolu pour chaque stratégie. Pour enregistrer un filtre ou un ensemble de filtres en tant que requête de filtre enregistrée, une ou plusieurs valeurs doivent être configurées en tant que sélections de filtre.

Le tableau suivant présente les détails du filtre :

|**Filter**|**Détails**|
|:-----|:-----|
| **Date** | Date à laquelle le message a été envoyé ou reçu par un utilisateur de votre organisation. Pour filtrer un jour unique, sélectionnez une plage de dates qui commence par le jour où vous souhaitez obtenir des résultats et se termine par le jour suivant. Par exemple, si vous souhaitez filtrer les résultats pour le 20/09/2020, choisissez une plage de dates de filtre du 20/09/2020 au 21/09/2020.|
| **Classe de fichier** | Classe du message en fonction du type de message, *message ou* *pièce jointe*. |
| **A une pièce jointe** | Présence de la pièce jointe dans le message. |
| **Classe d’élément** | Source du message en fonction du type de message, du courrier électronique, de la conversation de Microsoft Team, de Bloomberg, etc. Pour plus d’informations sur les types d’éléments courants et les classes de messages, voir [Types d’éléments et Classes de messages](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Domaines des destinataires** | Domaine auquel le message a été envoyé. Ce domaine est normalement votre domaine Microsoft 365 abonnement par défaut. |
| **Destinataire** | Utilisateur auquel le message a été envoyé. |
| **Sender** | La personne qui a envoyé le message. |
| **Domaine de l’expéditeur** | Domaine qui a envoyé le message. |
| **Taille** | Taille du message en Ko. |
| **Objet/Titre** | Objet du message ou titre de la conversation. |
| **Tags** | Balises affectées à un message, qu’il s’agit *d’une balise discutable*, *conforme* ou *non conforme*. |
| **Language** | Langue détectée du texte dans le message. Le message est classé en fonction de la langue de la majorité du texte du message. Par exemple, pour un message contenant du texte allemand et italien, mais que la majorité du texte est allemand, le message est classé comme allemand (DE). Les langues suivantes sont pris en charge : chinois (simplifié - ZH), anglais (EN), français (FR), allemand (DE), italien (IT), japonais (JP), portugais (PT) et espagnol (ES). Par exemple, pour filtrer les messages classés comme étant allemands et italien, entrez « DE,IT » (codes de langue à 2 chiffres) dans la zone de recherche du filtre de langue. Pour afficher la classification de langue détectée pour un message, sélectionnez un message, sélectionnez Afficher les détails du message et faites défiler jusqu’au champ EmailDetectedLanguage. |
| **Escalated To** | Nom d’utilisateur de la personne incluse dans le cadre d’une action d’escalade de message. |
| **Classifieurs** | Nom des classifieurs intégrés et personnalisés qui s’appliquent au message. Certains exemples *incluent le harcèlement* ciblé, *la blasphémité*, *les menaces*, etc.

#### <a name="to-configure-a-filter"></a>Pour configurer un filtre

1. Connectez-vous [au Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications**.

3. Sélectionnez **l’onglet** Stratégies, puis sélectionnez une stratégie pour l’examen, double-cliquez pour ouvrir la page **Stratégie** .

4. Dans la page **Stratégie**, sélectionnez l’onglet **En** attente ou Résolu pour afficher les éléments à filtrer.

5. Sélectionnez **le contrôle Filtres** pour ouvrir la page **Détails** des filtres.

6. Activez une ou plusieurs case à cocher pour activer des filtres pour ces alertes. Vous pouvez choisir parmi de nombreux filtres, notamment *Date*, *Expéditeur*, *Objet/Titre*, *Classifieurs*, *Langue*, etc.

7. Si vous souhaitez enregistrer le filtre sélectionné comme filtre par défaut, **sélectionnez Enregistrer par défaut**. Si vous souhaitez utiliser ce filtre en tant que filtre enregistré, sélectionnez **Terminé**.

8. Si vous souhaitez enregistrer les filtres sélectionnés en tant que requête de filtre, sélectionnez Enregistrer le contrôle de requête après avoir configuré au moins une valeur de filtre. Entrez un nom pour la requête de filtre, puis sélectionnez **Enregistrer**. Ce filtre n’est disponible que pour cette stratégie et est répertorié dans **la section Requêtes** de filtre enregistrées de la page **Détails** des filtres.

    ![Contrôles détaillés du filtre de conformité des communications.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Utilisation de l’analyse de doublons proche et exacte

Les stratégies de conformité des communications analysent et pré-groupent automatiquement les doublons de messages proches et exacts sans étapes de configuration supplémentaires. Cette vue vous permet d’agir rapidement sur des messages similaires un par un ou en tant que groupe, ce qui réduit la charge d’examen des messages pour les réviseurs. Au fur et à mesure que des doublons sont détectés, les contrôles **Doublons proches** et/ou les contrôles **Doublons exacts** sont affichés dans la barre d’outils action de correction. Cet affichage n’est pas disponible si des doublons proches ou exacts ne sont pas trouvés.

#### <a name="to-remediate-duplicates"></a>Pour corriger les doublons

1. Connectez-vous [au Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications**.

3. Sélectionnez **l’onglet** Stratégies, puis sélectionnez une stratégie pour l’examen, double-cliquez pour ouvrir la page **Stratégie** .

4. Dans la page **Stratégie** , sélectionnez l’onglet **En** attente ou **Résolu** pour afficher les messages en double.

5. Sélectionnez les **contrôles Doublons proches** ou Doublons **exacts** pour ouvrir la page de détails des doublons.

6. Sélectionnez un ou plusieurs messages pour les contrôles d’action de correction de ces messages.

7. **Sélectionnez Résoudre**, **Avertir**, **Réamorcer** ou **Télécharger** pour appliquer l’action aux messages en double sélectionnés comme filtre par défaut.

8. **Sélectionnez Fermer** après avoir terminé les actions de correction sur les messages.

    ![Contrôles dupliqués exacts de conformité des communications.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Corriger les alertes

Quel que soit l’endroit où vous commencez à réviser les alertes ou le filtrage que vous configurez, l’étape suivante consiste à prendre des mesures pour résoudre le problème. Démarrez la correction des alertes à l’aide du flux de travail suivant dans les pages **Stratégie** **ou Alertes** .

### <a name="step-1-examine-the-message-basics"></a>Étape 1 : Examiner les principes de base des messages

 Il est parfois évident, d’après la source ou l’objet, qu’un message peut être corrigé immédiatement. Il se peut que le message soit insérable ou mal mis en correspondance avec une stratégie et qu’il soit résolu comme incorrectement classé. Sélectionnez **le rapport comme** contrôle mal classé pour partager du contenu mal classé avec Microsoft, résoudre immédiatement l’alerte et supprimer de la file d’attente des alertes en attente. À partir de la source ou de l’expéditeur, vous savez peut-être déjà comment le message doit être routé ou géré dans ces circonstances. Envisagez d’utiliser les contrôles **Baliser comme** ou **Réaffectation** afin d’affecter une balise aux messages applicables ou d’envoyer des messages à un réviseur désigné.

![Contrôles de correction de la conformité des communications.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Étape 2 : Examiner les détails du message

Après avoir examiné les informations de base du message, il est temps d’ouvrir un message pour examiner les détails et déterminer d’autres actions de correction. Sélectionnez un message pour afficher l’ensemble des informations d’en-tête et de corps du message. Plusieurs options et vues différentes sont disponibles pour vous aider à déterminer le bon plan d’action :

- **Pièces jointes** : cette option vous permet d’examiner les pièces jointes modernes qui correspondent aux conditions de stratégie. Le contenu des pièces jointes modernes est extrait sous forme de texte et est consultable dans le tableau de bord Des alertes en attente pour une stratégie. Pour plus d’informations, voir la référence de la [fonctionnalité de conformité des communications](/microsoft-365/compliance/communication-compliance-channels).
- **Source** : cet affichage est l’affichage de message standard couramment utilisé dans la plupart des plateformes de messagerie web. Les informations d’en-tête sont formatées dans le style normal et le corps du message prend en charge les fichiers graphiques imbedded et le texte wrapped word. Si la reconnaissance optique de caractères [(OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) est activée pour la stratégie, les images contenant du texte imprimé ou manuscrit qui correspondent à la condition de stratégie sont vues comme un élément enfant pour le message associé dans cette vue.
- Texte simple : le mode Texte affiche une vue texte numéroée uniquement du message et inclut la mise en surbrillance des mots clés dans les messages et les pièces jointes pour les termes ou mots clés de type d’informations sensibles mis en correspondance dans la stratégie de conformité des communications associée. La mise en surbrillance des mots clés peut vous aider à analyser rapidement les longs messages et pièces jointes pour le domaine d’intérêt. Dans certains cas, le texte mis en surbrillante peut être uniquement dans les pièces jointes pour les messages correspondant aux conditions de stratégie. La mise en surbrillance des mots clés n’est pas prise en charge pour les termes identifiés par les classifieurs intégrés affectés à une stratégie. Les fichiers incorporés ne sont pas affichés et la ligne numérotant cet affichage est utile pour faire référence à des détails pertinents parmi plusieurs relecteurs.
- **Conversation (aperçu)** : disponible pour les messages de conversation Microsoft Teams, cet affichage affiche jusqu’à cinq messages avant et après un message d’alerte pour aider les réviseurs à afficher l’activité dans le contexte de conversation. Ce contexte permet aux réviseurs d’évaluer rapidement les messages et de prendre des décisions de résolution des messages plus éclairées. Les ajouts de messages en temps réel aux conversations sont affichés, y compris toutes les images inline, emojis et autocollants disponibles dans Teams. Les pièces jointes d’image ou de texte à des messages ne sont pas affichées. Les notifications s’affichent automatiquement pour les messages qui ont été modifiés ou pour les messages qui ont été supprimés de la fenêtre de conversation. Lorsqu’un message est résolu, les messages de conversation associés ne sont pas conservés avec le message résolu. Les messages de conversation sont disponibles pendant 60 jours après l’identification du message d’alerte.
- **Historique des utilisateurs** : le mode historique des utilisateurs affiche toutes les autres alertes générées par une stratégie de conformité des communications pour l’utilisateur qui envoie le message.
- **Notification de modèle détectée :** de nombreuses actions d’harcèlement et d’agresseur au fil du temps et impliquent la récurration d’instances du même comportement par un utilisateur. La notification *de modèle détecté* s’affiche dans les détails de l’alerte et attirer l’attention sur l’alerte. La détection des modèles se fait par stratégie et évalue le comportement au cours des 30 derniers jours lorsqu’au moins deux messages sont envoyés au même destinataire par un expéditeur. Les enquêteurs et les réviseurs peuvent utiliser cette notification pour identifier le comportement répété afin d’évaluer l’alerte selon le cas.
- **Traduction** : cet affichage convertit automatiquement le texte du message d’alerte en la langue configurée dans le paramètre de langue Affichée dans l’abonnement Microsoft 365 pour chaque réviseur. *L’affichage* Traduction permet d’élargir la prise en charge de l’examen pour les organisations avec des utilisateurs multilingues et élimine la nécessité d’autres services de traduction en dehors du processus de révision de la conformité des communications. À l’aide des services  de traduction Microsoft, l’affichage Traduction peut être allumé et désactivé selon les besoins et prend en charge un large éventail de langues. Pour obtenir la liste complète des langues pris en charge, [voir Traducteur Microsoft Languages](https://www.microsoft.com/translator/business/languages/). Les langues répertoriées dans la *liste Traducteur langues* sont pris en charge dans *l’affichage* Traduction.

### <a name="step-3-decide-on-a-remediation-action"></a>Étape 3 : Décider d’une action de correction

Maintenant que vous avez examiné les détails du message pour l’alerte, vous pouvez choisir plusieurs actions de correction :

- **Résoudre** : la sélection du contrôle **Résoudre** supprime immédiatement le message de la file d’attente des **alertes** en attente et aucune autre action ne peut être prise sur le message. En sélectionnant **Résoudre**, vous avez essentiellement fermé l’alerte sans classification supplémentaire. Tous les messages résolus sont affichés dans **l’onglet Résolu** .
- **Signaler une erreur de classification (aperçu)** : vous pouvez toujours résoudre un message comme mal classé à tout moment pendant le flux de travail de révision du message. Une classification incorrecte signifie que l’alerte ne peut pas être actionnable ou que l’alerte a été générée de manière incorrecte par le processus d’alerte et tous les classifieurs entraisables. La résolution de l’élément comme étant mal classé envoie le contenu du message, les pièces jointes et l’objet du message (y compris les métadonnées) à Microsoft afin d’améliorer les classifieurs entraisables. Les données envoyées à Microsoft ne contiennent pas d’informations qui peuvent identifier ou être utilisées pour identifier les utilisateurs de votre organisation. D’autres actions ne peuvent pas être prises sur le message et tous les messages mal classés sont affichés dans **l’onglet Résolu** .
- **Power Automate (aperçu)** : utilisez un flux Power Automate pour automatiser les tâches de traitement d’un message d’alerte. Par défaut, la conformité des communications inclut le gestionnaire de notifications lorsqu’un utilisateur dispose d’un modèle de flux d’alerte de conformité des *communications* que les réviseurs peuvent utiliser pour automatiser le processus de notification pour les utilisateurs avec des alertes de message. Pour plus d’informations sur la création et la gestion Power Automate flux de communication en conformité, consultez la section Étape 5 : Power Automate **flux** de travail dans cet article.
- **Marquez le** message comme étant *conforme,* *non* conforme ou aussi *discutable* en ce qui concerne les stratégies et les normes de votre organisation. L’ajout de balises et de commentaires de marquage vous permet de micro-filtrer les alertes de stratégie pour les escalades ou dans le cadre d’autres processus de révision interne. Une fois le marquage terminé, vous pouvez également choisir de résoudre le message pour le déplacer hors de la file d’attente de révision.
- **Notifier** : vous pouvez utiliser le contrôle **Notify** pour affecter un modèle de notification personnalisé à l’alerte et pour envoyer une notification d’avertissement à l’utilisateur. Choisissez le modèle d’avis approprié configuré dans la zone **Paramètres** de conformité des  communications, puis sélectionnez Envoyer un rappel par courrier électronique à l’utilisateur qui a envoyé le message et résoudre le problème.
- **Escalade :** à **l’aide du** contrôle Escalade, vous pouvez choisir les autres membres de votre organisation qui doivent examiner le message. Choisissez parmi une liste de réviseurs configurés dans la stratégie de conformité des communications pour envoyer une notification par courrier électronique demandant une révision supplémentaire de l’alerte de message. Le réviseur sélectionné peut utiliser un lien figurant dans la notification par courrier électronique pour accéder directement aux éléments qui y sont réaffectés pour révision.
- **Escalate for investigation**: Using the **Escalate for investigation** control, you can create a new [Advanced eDiscovery case](overview-ediscovery-20.md) for single or multiple messages. Vous devez fournir un nom et des notes pour le nouveau cas, et l’utilisateur qui a envoyé le message correspondant à la stratégie est automatiquement affecté en tant que dépositaire de cas. Vous n’avez pas besoin d’autorisations supplémentaires pour gérer le cas. La création d’un cas ne résout pas ou ne crée pas de balise pour le message. Vous pouvez sélectionner un total de 100 messages lors de la création d’un Advanced eDiscovery au cours du processus de correction. Les messages dans tous les canaux de communication surveillés par la conformité des communications sont pris en charge. Par exemple, vous pouvez sélectionner 50 conversations Microsoft Teams, 25 messages électroniques Exchange Online et 25 messages Yammer lorsque vous ouvrez un nouveau cas Advanced eDiscovery pour un utilisateur.
- Supprimer un **message dans Teams** : à l’aide du contrôle Supprimer le **message dans Teams**, vous pouvez bloquer les messages inappropriés et le contenu identifiés dans les alertes à partir de canaux Microsoft Teams et de conversations 1:1 et de groupe. Les messages et le contenu supprimés sont remplacés par un conseil de stratégie qui explique qu’il est bloqué et la stratégie qui s’applique à sa suppression de l’affichage. Un lien est fourni aux destinataires dans le conseil de stratégie pour en savoir plus sur la stratégie applicable et le processus de révision. L’expéditeur reçoit un conseil de stratégie pour le message et le contenu bloqués, mais peut examiner les détails du message bloqué et du contenu pour le contexte concernant la suppression.

    ![Supprimez un message de Microsoft Teams.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Étape 4 : Déterminer si les détails des messages doivent être archivés en dehors de la conformité des communications

Les détails des messages peuvent être exportés ou téléchargés si vous avez besoin d’archiver les messages dans une solution de stockage distincte. La sélection du contrôle **Télécharger** ajoute automatiquement les messages sélectionnés à un fichier .ZIP qui peut être sauvegardé en dehors de Microsoft 365.

### <a name="step-5-consider-power-automate-flows"></a>Étape 5 : prendre en compte Power Automate flux

[Microsoft Power Automate](/power-automate/getting-started) est un service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux à partir de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez Power Automate pour la conformité des communications, vous pouvez automatiser des tâches importantes pour les alertes et les utilisateurs. Vous pouvez configurer des flux Power Automate pour avertir les responsables lorsque les utilisateurs ont des alertes de conformité des communications et d’autres applications.

Les clients  titulaires Microsoft 365 abonnements qui incluent la conformité des communications n’ont pas besoin de licences Power Automate supplémentaires pour utiliser le modèle de conformité des communications par Power Automate par défaut recommandé. Le modèle par défaut peut être personnalisé pour prendre en charge votre organisation et couvrir les principaux scénarios de conformité des communications. Si vous choisissez d’utiliser des fonctionnalités Power Automate premium dans ces modèles, de créer un modèle personnalisé à l’aide du connecteur de conformité Microsoft 365 ou d’utiliser des modèles Power Automate pour d’autres domaines de conformité dans Microsoft 365, vous devrez peut-être des Power Automate licences.

> [!IMPORTANT]
> Recevez-vous des invites pour une validation de licence supplémentaire lors du test Power Automate flux ? Votre organisation n’a peut-être pas encore reçu de mises à jour de service pour cette fonctionnalité d’aperçu. Des mises à jour sont déployées et toutes les organisations  titulaires d’abonnements Microsoft 365 qui incluent la conformité des communications doivent avoir une prise en charge des licences pour les flux créés à partir des modèles Power Automate recommandés d’ici le 30 octobre 2020.

![Stratégie de conformité des Power Automate.](../media/communication-compliance-power-automate.png)

Le modèle de Power Automate suivant est fourni aux clients pour prendre en charge l’automatisation des processus pour les alertes de conformité des communications :

- **Avertir le responsable lorsqu’un utilisateur** a une alerte de conformité des communications : certaines organisations peuvent avoir besoin d’une notification de gestion immédiate lorsqu’un utilisateur a une alerte de conformité des communications. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur du cas est envoyé un message électronique avec les informations suivantes sur toutes les alertes :
  - Stratégie applicable pour l’alerte
  - Date/heure de l’alerte
  - Niveau de gravité de l’alerte

#### <a name="create-a-power-automate-flow"></a>Créer un flux Power Automate de données

Pour créer un flux Power Automate à partir d’un modèle par défaut recommandé, vous devez utiliser l’option Gérer les flux **Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans une alerte. Pour créer un flux Power Automate flux de gestion des **Power Automate, vous** devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour créer un flux de Power Automate à partir d’un modèle par défaut, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Conformité** >  des communications et sélectionnez la stratégie avec l’alerte à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Power Automate**, sélectionnez un modèle par défaut dans les **modèles** de conformité des communications que vous souhaitez peut-être dans la section de la page.
5. Le flux affiche la liste des connexions incorporées nécessaires au flux et s’affiche si les états de connexion sont disponibles. Si nécessaire, mettez à jour les connexions qui ne sont pas affichées comme disponibles. Cliquez sur **Continuer**.
6. Par défaut, les flux recommandés sont pré-configurés avec la conformité de communication recommandée et les champs de données de service Microsoft 365 requis pour effectuer la tâche affectée au flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle Afficher les **options** avancées et en configurant les propriétés disponibles pour le composant de flux.
7. Si nécessaire, ajoutez des étapes supplémentaires au flux en sélectionnant le **bouton Nouvelle étape** . Dans la plupart des cas, cette modification ne doit pas être nécessaire pour les modèles par défaut recommandés.
8. **Sélectionnez Enregistrer le** brouillon pour enregistrer le flux pour une configuration ultérieure, ou sélectionnez **Enregistrer** pour terminer la configuration du flux.
9. **Sélectionnez Fermer** pour revenir à la page Power Automate flux. Le nouveau modèle est répertorié sous la forme d’un flux  sous l’onglet Mes flux et est automatiquement disponible à partir du contrôle Power Automate pour l’utilisateur qui a créé le flux lors de l’utilisation des alertes de conformité des communications.

#### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate de données

Par défaut, les flux Power Automate créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que d’autres utilisateurs de conformité des communications ont accès et utilisent un flux, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous devez utiliser le contrôle **Power Automate** lorsque vous travaillez directement dans une alerte.

Pour partager un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.
Pour partager un flux de Power Automate, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Conformité** >  des communications et sélectionnez la stratégie avec l’alerte à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Power Automate flux**, sélectionnez **l’onglet Mes flux ou** **Flux d’équipe**.
5. Sélectionnez le flux à partager, puis **sélectionnez Partager dans** le menu options de flux.
6. Sur la page de partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire du flux.
7. Dans la **boîte de dialogue Connexion utilisée** , sélectionnez **OK** pour reconnaître que l’utilisateur ou le groupe ajouté aura un accès total au flux.

#### <a name="edit-a-power-automate-flow"></a>Modifier un flux Power Automate de données

Si vous devez modifier un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillerez directement dans une alerte. Pour modifier un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour modifier un flux de Power Automate, complétez les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Conformité** >  des communications et sélectionnez la stratégie avec l’alerte à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Power Automate flux**, sélectionnez flux à modifier. **Sélectionnez Modifier** dans le menu du contrôle de flux.
5. Sélectionnez **les Paramètres** >  **pour modifier** un paramètre de composant de flux ou **ellipsisDelete** >  pour supprimer un composant de flux.
6. **Sélectionnez Enregistrer**, **puis Fermez** pour terminer la modification du flux.

#### <a name="delete-a-power-automate-flow"></a>Supprimer un flux Power Automate de données

Si vous devez supprimer un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillerez directement dans une alerte. Pour supprimer un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour supprimer un flux de Power Automate, vous devez effectuer les étapes suivantes :

1. Dans la [Centre de conformité Microsoft 365](https://compliance.microsoft.com), sélectionnez **Conformité** >  des communications et sélectionnez la stratégie avec l’alerte à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Power Automate flux**, sélectionnez flux à supprimer. **Sélectionnez Supprimer** dans le menu du contrôle de flux.
5. Dans la boîte de dialogue de confirmation de suppression, sélectionnez **Supprimer** pour supprimer le flux ou sélectionnez **Annuler** pour quitter l’action de suppression.

### <a name="step-6-consider-creating-notice-templates"></a>Étape 6 : Envisagez de créer des modèles d’avis

Vous pouvez créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’utilisateur associée à la correspondance de stratégie qui a généré l’alerte spécifique pour la correction. Lorsque vous sélectionnez un modèle d’avis à appliquer à une violation de stratégie dans le cadre du flux de travail de correction, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou d’en faire le choix.

Les modèles d’avis sont des modèles de courrier personnalisés dans lequel vous pouvez définir les champs de message **suivants dans la zone Paramètres de conformité des communications** :

|**Field**|**Obligatoire**| **Détails** |
|:-----|:-----|:-----|
|**Nom du modèle** | Oui | Le nom convivial du modèle d’avis que vous sélectionnerez dans le flux de travail d’notification lors de la correction prend en charge les caractères de texte. |
| **Adresse de l’expéditeur** | Oui | Adresse d’un ou de plusieurs utilisateurs ou groupes qui envoient le message à l’utilisateur avec une correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement. |
| **Adresses CC et Cci** | Non | Utilisateurs ou groupes facultatifs à notifiés de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement. |
| **Sujet** | Oui | Les informations qui apparaissent dans la ligne d’objet du message, prend en charge les caractères de texte. |
| **Corps du message** | Oui | Les informations qui apparaissent dans le corps du message, prend en charge les valeurs texte ou HTML. |

### <a name="html-for-notices"></a>HTML pour les notifications

Si vous souhaitez créer plus qu’un simple message électronique texte pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle d’avis. L’exemple suivant fournit le format du corps du message pour un modèle de notification par courrier électronique html de base :

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

> [!NOTE]
> L’implémentation d’attribut href HTML dans les modèles de notification de conformité des communications ne permet actuellement de ne pas utiliser de guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="unresolve-messages-preview"></a>Messages non résolus (aperçu)

Lorsque les messages sont résolus, ils sont supprimés de  l’affichage Onglet En attente et affichés dans **l’affichage Onglet** Résolu. Les actions d’investigation et de correction ne sont pas disponibles pour les messages en *affichage* Résolu. Toutefois, dans certains cas, vous devrez prendre des mesures supplémentaires sur un message qui a été résolu par erreur ou qui doit faire l’objet d’un examen plus approfondie après la résolution initiale. Vous pouvez utiliser la fonctionnalité de commande non résolue pour déplacer un ou plusieurs messages  de l’affichage Résolu vers *l’affichage En* attente.

Pour non-résolu les messages, effectuer les étapes suivantes :

1. Connectez-vous au [Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un utilisateur affecté  aux groupes de rôles Analyste de conformité des communications ou Enquêteur de conformité des communications dans Microsoft 365 organisation.
2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications**.
3. Sélectionnez **l’onglet** Stratégies, puis sélectionnez une stratégie qui contient le message d’alerte résolu, double-cliquez pour ouvrir la page **Stratégie** .
4. Dans la page **Stratégie** , sélectionnez **l’onglet Résolu** .
5. Sous **l’onglet Résolu** , sélectionnez un ou plusieurs messages pour revenir *à En attente*.
6. Dans la barre de commandes, sélectionnez **Non résolu**.
7. Dans le **volet Éléments** non résolus, ajoutez tous les commentaires applicables à l’action de non-résolu et sélectionnez **Enregistrer** pour déplacer l’élément vers *En attente*.
8. Sélectionnez **l’onglet En** attente pour vérifier que les éléments sélectionnés sont affichés.