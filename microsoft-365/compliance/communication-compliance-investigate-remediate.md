---
title: Examiner et corriger les alertes de conformité des communications
description: Examinez et corrigez les alertes de conformité des communications dans Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
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
ms.openlocfilehash: 39a30b7fcc853ac96d14df4fa04f9e727f98628c
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2022
ms.locfileid: "66686028"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Examiner et corriger les alertes de conformité des communications

Une fois que vous avez configuré vos stratégies de conformité des communications, vous commencerez à recevoir des alertes dans le portail de conformité Microsoft Purview pour les problèmes de message qui correspondent à vos conditions de stratégie. Suivez les instructions de flux de travail ici pour examiner et corriger les problèmes d’alerte.

## <a name="investigate-alerts"></a>Examiner des alertes

La première étape pour examiner les problèmes détectés par vos stratégies consiste à examiner les alertes de conformité des communications dans le portail de conformité Microsoft Purview. Il existe plusieurs domaines dans le domaine de la solution de conformité des communications pour vous aider à examiner rapidement les alertes, selon la façon dont vous préférez afficher le regroupement d’alertes :

- **Page** stratégie de conformité des communications : lorsque vous vous connectez au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365, sélectionnez **Conformité des communications** pour afficher la page **stratégie** de conformité des communications. Cette page affiche les stratégies de conformité des communications configurées pour votre organisation Microsoft 365 et des liens vers les modèles de stratégie recommandés. Chaque stratégie répertoriée inclut le nombre d’alertes qui doivent être examinées, le nombre d’éléments escaladés et résolus, l’état de la stratégie et la date et l’heure de la dernière analyse de stratégie. La sélection d’une stratégie affiche toutes les alertes en attente pour les correspondances à la stratégie, une alerte spécifique pour lancer la page de détails de la stratégie et démarrer les actions de correction.
- **Alertes** : accédez aux **alertes** de **conformité** >  des communications pour afficher les 30 derniers jours d’alertes regroupées par correspondances de stratégie. Cet affichage vous permet de voir rapidement les stratégies de conformité des communications qui génèrent la plupart des alertes classées par gravité. Pour démarrer les actions de correction, sélectionnez la stratégie associée à l’alerte pour lancer la page **de détails** de la stratégie. À partir de la page **Détails** de la stratégie, vous pouvez consulter un résumé des activités sur la page **Vue d’ensemble** , examiner et agir sur les messages d’alerte sur la page **En attente** , ou consulter l’historique des alertes fermées sur la page **Résolu** .
- **Rapports** : accédez aux rapports de **conformité** > **des** communications pour afficher les widgets de rapport de conformité des communications. Chaque widget fournit une vue d’ensemble des activités et des états de conformité des communications, y compris l’accès à des informations plus approfondies sur les correspondances de stratégie et les actions de correction.

### <a name="using-filters"></a>Utilisation de filtres

L’étape suivante consiste à trier les messages de sorte qu’il soit plus facile de rechercher des alertes. Dans la page Détails de la stratégie, la conformité **des** communications prend en charge le filtrage multiniveaux pour plusieurs champs de messages afin de vous aider à examiner et à examiner rapidement les messages avec des correspondances de stratégie. Le filtrage est disponible pour les éléments en attente et résolus pour chaque stratégie configurée. Vous pouvez configurer des requêtes de filtrage pour une stratégie ou configurer et enregistrer des requêtes de filtrage personnalisées et par défaut à utiliser dans chaque stratégie spécifique. Une fois que vous avez configuré les champs d’un filtre, les champs de filtre affichés en haut de la file d’attente de messages d’alerte peuvent être configurés pour des valeurs de filtre spécifiques.

Pour le filtre de dates, la date et l’heure des événements sont répertoriées en temps universel coordonné (UTC). Lors du filtrage des messages pour les affichages, la date/heure locale de l’utilisateur demandeur détermine les résultats en fonction de la conversion de la date/heure locale de l’utilisateur en UTC. Par exemple, si un utilisateur de l’heure d’été du Pacifique (PDT) filtre un rapport du 30/08/2021 au 31/08/2021 à 00:00, le rapport inclut des messages du 30/08/2021 de 07:00 UTC au 31/08/2021 07:00 UTC. Si le même utilisateur se trouvait à l’heure d’été de l’Est des États-Unis (EDT) lors du filtrage à 00:00, le rapport inclut les messages du 30/08/2021 04:00 UTC au 31/08/2021 04:00 UTC.

#### <a name="filter-details"></a>Détails du filtre

Les filtres de conformité des communications vous permettent de filtrer et de trier les messages d’alerte pour accélérer les actions d’investigation et de correction. Le filtrage est disponible sous les onglets **En attente** et **Résolu** pour chaque stratégie. Pour enregistrer un filtre ou un ensemble de filtres en tant que requête de filtre enregistrée, une ou plusieurs valeurs doivent être configurées en tant que sélections de filtre.

Le tableau suivant décrit les détails du filtre :

|**Filtre**|**Détails**|
|:-----|:-----|
| **Date** | Date à laquelle le message a été envoyé ou reçu par un utilisateur de votre organisation. Pour filtrer une seule journée, sélectionnez une plage de dates qui commence par le jour pour lequel vous souhaitez obtenir des résultats et se termine par le jour suivant. Par exemple, si vous souhaitez filtrer les résultats pour le 20/09/2020, vous devez choisir une plage de dates de filtre du 20/09/2020 au 21/09/2020.|
| **Classe de fichier** | Classe du message en fonction du type de message, *message* ou *pièce jointe*. |
| **A une pièce jointe** | Présence de pièce jointe dans le message. |
| **Classe Item** | Source du message en fonction du type de message, de l’e-mail, de la conversation d’équipe Microsoft, de Bloomberg, etc. Pour plus d’informations sur les types d’éléments courants et les classes de message, consultez [Types d’éléments et Classes de message](/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Domaines de destinataire** | Domaine vers lequel le message a été envoyé. Ce domaine est normalement votre domaine d’abonnement Microsoft 365 par défaut. |
| **Destinataire** | Utilisateur auquel le message a été envoyé. |
| **Sender** | Personne qui a envoyé le message. |
| **Domaine de l’expéditeur** | Domaine qui a envoyé le message. |
| **Size** | Taille du message en Ko. |
| **Objet/titre** | Objet du message ou titre de conversation. |
| **Tags** | Balises affectées à un message, *contestable*, *conforme* ou *non conforme*. |
| **Language** | Langue de texte détectée dans le message. Le message est classé en fonction de la langue de la majorité du texte du message. Par exemple, pour un message contenant à la fois du texte allemand et italien, mais la majorité du texte est allemand, le message est classé en allemand (DE). Pour obtenir la liste des langues prises en charge, consultez [En savoir plus sur les classifieurs pouvant être formés](/microsoft-365/compliance/classifier-learn-about). <br><br> Vous pouvez également filtrer par plusieurs langues. Par exemple, pour filtrer les messages classés en allemand et en italien, entrez « DE, IT » (codes de langue à 2 chiffres) dans la zone de recherche Filtre de langue. Pour afficher la classification de langue détectée pour un message, sélectionnez un message, sélectionnez Afficher les détails du message, puis faites défiler jusqu’au champ *EmailDetectedLanguage* . |
| **Remonté vers** | Nom d’utilisateur de la personne incluse dans le cadre d’une action d’escalade de messages. |
| **Classificateurs** | Nom des classifieurs intégrés et personnalisés qui s’appliquent au message. Parmi les exemples, citons *le harcèlement ciblé*, *les profanations*, les *menaces*, etc.

#### <a name="to-configure-a-filter"></a>Pour configurer un filtre

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, accédez à **La conformité des communications**.

3. Sélectionnez l’onglet **Stratégies** , puis sélectionnez une stratégie à examiner, double-cliquez pour ouvrir la page **Stratégie** .

4. Dans la page **Stratégie** , sélectionnez l’onglet **En attente** ou **Résolu** pour afficher les éléments à filtrer.

5. Sélectionnez le contrôle **Filtres** pour ouvrir la page **Détails des filtres** .

6. Cochez une ou plusieurs cases à cocher pour activer les filtres de ces alertes. Vous pouvez choisir parmi de nombreux filtres, notamment *Date*, *Sender*, *Subject/Title*, *Classifieurs*, *Language*, etc.

7. Si vous souhaitez enregistrer le filtre sélectionné comme filtre par défaut, **sélectionnez Enregistrer par défaut**. Si vous souhaitez utiliser ce filtre comme filtre enregistré, sélectionnez **Terminé**.

8. Si vous souhaitez enregistrer les filtres sélectionnés en tant que requête de filtre, **sélectionnez Enregistrer le** contrôle de requête après avoir configuré au moins une valeur de filtre. Entrez un nom pour la requête de filtre, puis **sélectionnez Enregistrer**. Ce filtre est disponible uniquement pour cette stratégie et est répertorié dans la section Requêtes de **filtre enregistrées** de la page **Détails des filtres** .

    ![Contrôles détaillés du filtre de conformité des communications.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Utilisation de l’analyse de doublons proche et exacte

Les stratégies de conformité des communications analysent et pré-groupent automatiquement les doublons de messages proches et exacts sans étapes de configuration supplémentaires. Cette vue vous permet d’agir rapidement sur des messages similaires un par un ou en tant que groupe, ce qui réduit la charge d’examen des messages pour les réviseurs. Au fur et à mesure que des doublons sont détectés, les contrôles **Doublons proches** et/ou les contrôles **Doublons exacts** sont affichés dans la barre d’outils action de correction. Cette vue n’est pas disponible si des doublons proches ou exacts sont introuvables.

#### <a name="to-remediate-duplicates"></a>Pour corriger les doublons

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, accédez à **La conformité des communications**.

3. Sélectionnez l’onglet **Stratégies** , puis sélectionnez une stratégie à examiner, double-cliquez pour ouvrir la page **Stratégie** .

4. Dans la page **Stratégie** , sélectionnez l’onglet **En attente** ou **Résolu** pour afficher les messages en double.

5. Sélectionnez les **contrôles Near Duplicates** ou **Exact Duplicates** pour ouvrir la page des détails des doublons.

6. Sélectionnez un ou plusieurs messages pour corriger les contrôles d’action pour ces messages.

7. Sélectionnez **Résoudre**, **Notifier**, **Escalader** ou **Télécharger** pour appliquer l’action aux messages en double sélectionnés comme filtre par défaut.

8. Sélectionnez **Fermer** après avoir effectué les actions de correction sur les messages.

## <a name="remediate-alerts"></a>Corriger les alertes

Quel que soit l’endroit où vous commencez à réviser les alertes ou le filtrage que vous configurez, l’étape suivante consiste à prendre des mesures pour résoudre le problème. Démarrez votre correction d’alerte à l’aide du flux de travail suivant dans les pages **Stratégie** ou **Alertes** .

### <a name="step-1-examine-the-message-basics"></a>Étape 1 : Examiner les principes de base du message

 Parfois, il est évident à partir de la source ou du sujet qu’un message peut être immédiatement corrigé. Il se peut que le message soit faux ou qu’il corresponde incorrectement à une stratégie et qu’il doit être résolu comme mal classé. Sélectionnez le **rapport comme contrôle mal classé** pour partager du contenu mal classé avec Microsoft, résolvez immédiatement l’alerte et supprimez-le de la file d’attente d’alerte en attente. À partir de la source ou de l’expéditeur, vous savez peut-être déjà comment le message doit être routé ou géré dans ces circonstances. Envisagez d’utiliser les contrôles **Baliser comme** ou **Réaffectation** afin d’affecter une balise aux messages applicables ou d’envoyer des messages à un réviseur désigné.

![Contrôles de correction de la conformité des communications.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Étape 2 : Examiner les détails du message

Après avoir examiné les principes de base du message, il est temps d’ouvrir un message pour examiner les détails et déterminer d’autres actions de correction. Sélectionnez un message pour afficher l’ensemble des informations d’en-tête et de corps du message. Plusieurs options et vues différentes sont disponibles pour vous aider à déterminer le bon plan d’action :

- **Pièces jointes** : cette option vous permet d’examiner les pièces jointes modernes qui correspondent aux conditions de stratégie. Le contenu des pièces jointes modernes est extrait sous forme de texte et peut être consulté dans le tableau de bord Des alertes en attente pour une stratégie. Pour plus d’informations, consultez la [référence des fonctionnalités de conformité des communications](/microsoft-365/compliance/communication-compliance-channels).
- **Source** : cette vue est la vue de message standard couramment observée dans la plupart des plateformes de messagerie web. Les informations d’en-tête sont mises en forme dans le style normal et le corps du message prend en charge les fichiers graphiques imbeddés et le texte encapsulé dans le mot. Si la [reconnaissance optique de caractères (OCR)](/microsoft-365/compliance/communication-compliance-policies#optical-character-recognition-ocr) est activée pour la stratégie, les images contenant du texte imprimé ou manuscrit qui correspondent à la condition de stratégie sont considérées comme un élément enfant pour le message associé dans cette vue.
- **Texte brut** : l’affichage texte affiche une vue de texte numérotée en ligne uniquement du message et inclut la mise en surbrillance des mots clés dans les messages et pièces jointes pour les termes ou mots clés de type d’informations sensibles correspondant à la stratégie de conformité de communication associée. La mise en surbrillance des mots clés peut vous aider à analyser rapidement les longs messages et pièces jointes pour la zone d’intérêt. Dans certains cas, le texte mis en surbrillance peut se trouver uniquement dans les pièces jointes pour les messages correspondant aux conditions de stratégie. La mise en surbrillance des mots clés n’est pas prise en charge pour les termes identifiés par les classifieurs intégrés affectés à une stratégie. Les fichiers incorporés ne sont pas affichés et la numérotation de ligne de cet affichage est utile pour référencer des détails pertinents parmi plusieurs réviseurs.
- **Conversation (préversion)** : disponible pour les messages de conversation Microsoft Teams, cette vue affiche jusqu’à cinq messages avant et après un message d’alerte pour aider les réviseurs à afficher l’activité dans le contexte conversationnel. Ce contexte permet aux réviseurs d’évaluer rapidement les messages et de prendre des décisions de résolution de messages plus éclairées. Les ajouts de messages en temps réel aux conversations sont affichés, y compris toutes les images incluses, emojis et autocollants disponibles dans Teams. Les pièces jointes d’image ou de fichier texte aux messages ne sont pas affichées. Les notifications sont automatiquement affichées pour les messages qui ont été modifiés ou pour les messages qui ont été supprimés de la fenêtre de conversation. Lorsqu’un message est résolu, les messages conversationnels associés ne sont pas conservés avec le message résolu. Les messages de conversation sont disponibles jusqu’à 60 jours après l’identification du message d’alerte.
- **Historique des utilisateurs** : le mode historique des utilisateurs affiche toutes les autres alertes générées par une stratégie de conformité des communications pour l’utilisateur qui envoie le message.
- **Notification détectée par le modèle** : de nombreuses actions de harcèlement et d’intimidation au fil du temps et impliquent la récurrence d’instances du même comportement par un utilisateur. La notification *détectée par le modèle* s’affiche dans les détails de l’alerte et attire l’attention sur l’alerte. La détection des modèles est effectuée par stratégie et évalue le comportement au cours des 30 derniers jours quand au moins deux messages sont envoyés au même destinataire par un expéditeur. Les enquêteurs et les réviseurs peuvent utiliser cette notification pour identifier le comportement répété afin d’évaluer l’alerte comme il convient.
- **Traduction** : cette vue convertit automatiquement le texte du message d’alerte en la langue configurée dans le paramètre *de langue Affiché* dans l’abonnement Microsoft 365 pour chaque réviseur. La *vue traduction* permet d’élargir la prise en charge des enquêtes pour les organisations avec des utilisateurs multilingues et élimine la nécessité de services de traduction supplémentaires en dehors du processus d’examen de la conformité des communications. À l’aide des services de traduction Microsoft, la vue *Traduction* peut être activée et désactivée en fonction des besoins et prend en charge un large éventail de langues. Pour obtenir la liste complète des langues prises en charge, consultez [Microsoft Translator Languages](https://www.microsoft.com/translator/business/languages/). Les langues répertoriées dans la *liste des langues translatores* sont prises en charge dans la vue *Traduction* .

### <a name="step-3-decide-on-a-remediation-action"></a>Étape 3 : Décider d’une action de correction

Maintenant que vous avez examiné les détails du message pour l’alerte, vous pouvez choisir plusieurs actions de correction :

- **Résoudre** : la sélection du contrôle **Résoudre** supprime immédiatement le message de la file d’attente **d’alertes en attente** et aucune autre action ne peut être effectuée sur le message. En sélectionnant **Résoudre**, vous avez essentiellement fermé l’alerte sans classification supplémentaire. Tous les messages résolus sont affichés sous l’onglet **Résolu** .
- **Signaler comme étant mal classé** : vous pouvez toujours résoudre un message comme mal classé à tout moment pendant le flux de travail de révision des messages. Une classification incorrecte signifie que l’alerte n’était pas actionnable ou que l’alerte a été générée de manière incorrecte par le processus d’alerte et tous les classifieurs pouvant être formés. La résolution de l’élément comme mal classé envoie le contenu du message, les pièces jointes et l’objet du message (y compris les métadonnées) à Microsoft pour aider à améliorer les classifieurs pouvant être formés. Les données envoyées à Microsoft ne contiennent pas d’informations susceptibles d’identifier ou d’être utilisées pour identifier les utilisateurs de votre organisation. D’autres actions ne peuvent pas être effectuées sur le message et tous les messages mal classés sont affichés sous l’onglet **Résolu** .
- **Power Automate (préversion)** : utilisez un flux Power Automate pour automatiser les tâches de processus pour un message d’alerte. Par défaut, la conformité des communications inclut le *gestionnaire de notifications lorsqu’un utilisateur dispose d’un* modèle de flux d’alerte de conformité des communications que les réviseurs peuvent utiliser pour automatiser le processus de notification pour les utilisateurs avec des alertes de message. Pour plus d’informations sur la création et la gestion de flux Power Automate dans la conformité des communications, consultez **l’étape 5 : Prendre en compte les flux Power Automate** dans cet article.
- **Balisez** le message comme *étant conforme*, *non conforme* ou *contestable* en ce qui concerne les stratégies et les normes de votre organisation. L’ajout de balises et de commentaires d’étiquetage vous permet de microfiltrer les alertes de stratégie pour les escalades ou dans le cadre d’autres processus de révision internes. Une fois le balisage terminé, vous pouvez également choisir de résoudre le message pour le déplacer hors de la file d’attente de révision en attente.
- **Notifier** : vous pouvez utiliser le contrôle **Notify** pour affecter un modèle d’avis personnalisé à l’alerte et envoyer un avis d’avertissement à l’utilisateur. Choisissez le modèle d’avis approprié configuré dans la zone **Paramètres de conformité des** communications, puis sélectionnez **Envoyer** pour envoyer un rappel à l’utilisateur qui a envoyé le message et résoudre le problème.
- **Escalade** : à l’aide du contrôle **Escalate** , vous pouvez choisir qui d’autre dans votre organisation doit passer en revue le message. Choisissez parmi une liste de réviseurs configurés dans la stratégie de conformité des communications pour envoyer une notification par e-mail demandant une révision supplémentaire de l’alerte de message. Le réviseur sélectionné peut utiliser un lien figurant dans la notification par courrier électronique pour accéder directement aux éléments qui y sont réaffectés pour révision.
- **Escalade pour investigation** : à l’aide de **l’instruction Escalate pour le contrôle d’investigation** , vous pouvez créer un [cas eDiscovery (Premium)](/microsoft-365/compliance/overview-ediscovery-20) pour les messages uniques ou multiples. Vous fournirez un nom et des notes pour le nouveau cas, et l’utilisateur qui a envoyé le message correspondant à la stratégie est automatiquement affecté en tant que consignateur de cas. Vous n’avez pas besoin d’autorisations supplémentaires pour gérer le cas. La création d’un cas ne résout pas ou ne crée pas de balise pour le message. Vous pouvez sélectionner un total de 100 messages lors de la création d’un cas eDiscovery (Premium) pendant le processus de correction. Les messages dans tous les canaux de communication surveillés par la conformité des communications sont pris en charge. Par exemple, vous pouvez sélectionner 50 conversations Microsoft Teams, 25 e-mails Exchange Online et 25 messages Yammer lorsque vous ouvrez un nouveau cas eDiscovery (Premium) pour un utilisateur.
- **Supprimer un message dans Teams** : à l’aide du **contrôle Supprimer le message dans le contrôle Teams** , vous pouvez bloquer les messages et le contenu inappropriés identifiés dans les alertes provenant des canaux Microsoft Teams et des conversations de groupe et 1:1. Cela inclut les messages de conversation Teams signalés par les utilisateurs et les messages de conversation détectés à l’aide de stratégies de conformité de communication basées sur le machine learning et le classifieur. Les messages et le contenu supprimés sont remplacés par un conseil de stratégie qui explique qu’il est bloqué et la stratégie qui s’applique à sa suppression de la vue. Un lien est fourni aux destinataires dans le conseil de stratégie pour en savoir plus sur la stratégie applicable et le processus de révision. L’expéditeur reçoit un conseil de stratégie pour le message bloqué et le contenu, mais peut passer en revue les détails du message bloqué et du contenu pour le contexte concernant la suppression.

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Étape 4 : Déterminer si les détails du message doivent être archivés en dehors de la conformité des communications

Les détails des messages peuvent être exportés ou téléchargés si vous devez archiver les messages dans une solution de stockage distincte. La sélection du contrôle **Télécharger** ajoute automatiquement les messages sélectionnés à un fichier .ZIP qui peut être sauvegardé en dehors de Microsoft 365.

### <a name="step-5-consider-power-automate-flows"></a>Étape 5 : Prendre en compte les flux Power Automate

[Microsoft Power Automate](/power-automate/getting-started) est un service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux à partir de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez les flux Power Automate pour la conformité des communications, vous pouvez automatiser les tâches importantes pour les alertes et les utilisateurs. Vous pouvez configurer des flux Power Automate pour avertir les gestionnaires lorsque les utilisateurs ont des alertes de conformité des communications et d’autres applications.

Les clients disposant d’abonnements Microsoft 365 qui incluent la conformité des communications n’ont pas besoin de licences Power Automate supplémentaires pour utiliser le modèle Power Automate de conformité des communications par défaut recommandé. Le modèle par défaut peut être personnalisé pour prendre en charge votre organisation et couvrir les principaux scénarios de conformité des communications. Si vous choisissez d’utiliser des fonctionnalités Power Automate Premium dans ces modèles, créez un modèle personnalisé à l’aide du connecteur Microsoft Purview ou utilisez des modèles Power Automate pour d’autres zones de conformité dans Microsoft Purview, vous aurez peut-être besoin de licences Power Automate supplémentaires.

> [!IMPORTANT]
> Recevez-vous des invites pour une validation de licence supplémentaire lors du test des flux Power Automate ? Votre organisation n’a peut-être pas encore reçu de mises à jour de service pour cette fonctionnalité en préversion. Des mises à jour sont en cours de déploiement et toutes les organisations disposant d’abonnements Microsoft 365 qui incluent la conformité des communications doivent disposer d’une prise en charge des licences pour les flux créés à partir des modèles Power Automate recommandés d’ici le 30 octobre 2020.

![Conformité des communications Power Automate.](../media/communication-compliance-power-automate.png)

Le modèle Power Automate suivant est fourni aux clients pour prendre en charge l’automatisation des processus pour les alertes de conformité des communications :

- **Avertir le gestionnaire lorsqu’un utilisateur a une alerte de conformité des communications** : certaines organisations peuvent avoir besoin d’une notification de gestion immédiate lorsqu’un utilisateur a une alerte de conformité des communications. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur de cas reçoit un e-mail contenant les informations suivantes sur toutes les alertes :
  - Stratégie applicable pour l’alerte
  - Date/heure de l’alerte
  - Niveau de gravité de l’alerte

#### <a name="create-a-power-automate-flow"></a>Créer un flux Power Automate

Pour créer un flux Power Automate à partir d’un modèle par défaut recommandé, vous allez utiliser l’option **Gérer les flux Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans une alerte. Pour créer un flux Power Automate avec **Gérer les flux Power Automate**, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Effectuez les étapes suivantes pour créer un flux Power Automate à partir d’un modèle par défaut :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez aux **stratégies** de **conformité** >  des communications et sélectionnez la stratégie avec l’alerte que vous souhaitez examiner.
2. Dans la stratégie, sélectionnez l’onglet **En attente** , puis sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Power Automate** , sélectionnez un modèle par défaut dans les **modèles de conformité des communications que vous pouvez utiliser** dans la page.
5. Le flux répertorie les connexions incorporées nécessaires au flux et s’affiche si les états de connexion sont disponibles. Si nécessaire, mettez à jour les connexions qui ne sont pas affichées comme étant disponibles. Cliquez sur **Continuer**.
6. Par défaut, les flux recommandés sont préconfigurés avec la conformité de communication recommandée et les champs de données de service Microsoft 365 nécessaires pour effectuer la tâche affectée pour le flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle **Afficher les options avancées** et configurez les propriétés disponibles pour le composant de flux.
7. Si nécessaire, ajoutez des étapes supplémentaires au flux en sélectionnant le bouton **Nouvelle étape** . Dans la plupart des cas, cette modification ne doit pas être nécessaire pour les modèles par défaut recommandés.
8. Sélectionnez **Enregistrer le brouillon** pour enregistrer le flux pour une configuration ultérieure, ou **sélectionnez Enregistrer** pour terminer la configuration du flux.
9. Sélectionnez **Fermer** pour revenir à la page de flux Power Automate. Le nouveau modèle est répertorié sous la forme d’un flux sous l’onglet **Mes flux** et est automatiquement disponible à partir du contrôle Power Automate pour l’utilisateur qui a créé le flux lors de l’utilisation des alertes de conformité des communications.

#### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate

Par défaut, les flux Power Automate créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que les autres utilisateurs de conformité des communications aient accès à un flux et l’utilisent, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous allez utiliser le contrôle **Power Automate** lorsque vous travaillez directement dans une alerte.

Pour partager un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.
Effectuez les étapes suivantes pour partager un flux Power Automate :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez aux **stratégies** de **conformité** >  des communications et sélectionnez la stratégie avec l’alerte que vous souhaitez examiner.
2. Dans la stratégie, sélectionnez l’onglet **En attente** , puis sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **Flux Power Automate** , sélectionnez l’onglet **Mes flux** ou **Flux d’équipe** .
5. Sélectionnez le flux à partager, puis sélectionnez **Partager** dans le menu des options de flux.
6. Dans la page de partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire du flux.
7. Dans la boîte de dialogue **Connexion utilisée** , sélectionnez **OK** pour confirmer que l’utilisateur ou le groupe ajouté aura un accès complet au flux.

#### <a name="edit-a-power-automate-flow"></a>Modifier un flux Power Automate

Si vous devez modifier un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillez directement dans une alerte. Pour modifier un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Effectuez les étapes suivantes pour modifier un flux Power Automate :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez aux **stratégies** de **conformité** >  des communications et sélectionnez la stratégie avec l’alerte que vous souhaitez examiner.
2. Dans la stratégie, sélectionnez l’onglet **En attente** , puis sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **flux Power Automate** , sélectionnez flux à modifier. Sélectionnez **Modifier** dans le menu du contrôle de flux.
5. Sélectionnez les **paramètres de** >  points de suspension pour modifier un paramètre de composant de flux ou supprimer **des** >  points de suspension **pour supprimer** un composant de flux.
6. Sélectionnez **Enregistrer** , puis **Fermer** pour terminer la modification du flux.

#### <a name="delete-a-power-automate-flow"></a>Supprimer un flux Power Automate

Si vous devez supprimer un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillez directement dans une alerte. Pour supprimer un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Effectuez les étapes suivantes pour supprimer un flux Power Automate :

1. Dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez aux **stratégies** de **conformité** >  des communications et sélectionnez la stratégie avec l’alerte que vous souhaitez examiner.
2. Dans la stratégie, sélectionnez l’onglet **En attente** , puis sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate** dans le menu d’action d’alerte.
4. Dans la page **flux Power Automate** , sélectionnez flux à supprimer. Sélectionnez **Supprimer** dans le menu de contrôle de flux.
5. Dans la boîte de dialogue de confirmation de suppression, **sélectionnez Supprimer** pour supprimer le flux ou sélectionnez **Annuler** pour quitter l’action de suppression.

### <a name="step-6-consider-creating-notice-templates"></a>Étape 6 : Envisagez de créer des modèles d’avis

Vous pouvez créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par e-mail pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse e-mail de l’utilisateur associée à la correspondance de stratégie qui a généré l’alerte spécifique à corriger. Lorsque vous sélectionnez un modèle d’avis à appliquer à une violation de stratégie dans le cadre du flux de travail de correction, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou de remplacer les champs en fonction des besoins.

Les modèles de notifications sont des modèles de courrier personnalisés dans lesquels vous pouvez définir les champs de message suivants dans la zone **Paramètres de conformité des** communications :

|**Champ**|**Obligatoire**| **Détails** |
|:-----|:-----|:-----|
|**Nom du modèle** | Oui | Le nom convivial du modèle d’avis que vous allez sélectionner dans le flux de travail de notification pendant la correction prend en charge les caractères texte. |
| **Adresse de l’expéditeur** | Oui | Adresse d’un ou plusieurs utilisateurs ou groupes qui envoient le message à l’utilisateur avec une correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement. |
| **Adresses CC et CCI** | Non | Utilisateurs ou groupes facultatifs à notifier de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement. |
| **Sujet** | Oui | Les informations qui apparaissent dans la ligne d’objet du message prennent en charge les caractères texte. |
| **Corps du message** | Oui | Les informations qui apparaissent dans le corps du message prennent en charge le texte ou les valeurs HTML. |

### <a name="html-for-notices"></a>HTML pour les avis

Si vous souhaitez créer plus qu’un simple message électronique textuel pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle d’avis. L’exemple suivant fournit le format de corps du message pour un modèle de notification par e-mail HTML de base :

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
> L’implémentation d’attribut href HTML dans les modèles de notification de conformité des communications prend actuellement en charge uniquement les guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="unresolve-messages-preview"></a>Messages unresolve (préversion)

Lorsque les messages sont résolus, ils sont supprimés de l’affichage onglet **En attente** et affichés dans l’affichage **Onglet Résolu** . Les actions d’investigation et de correction ne sont pas disponibles pour les messages en mode *Résolu* . Toutefois, il peut arriver que vous deviez prendre des mesures supplémentaires sur un message qui a été résolu par erreur ou qui nécessite une investigation plus approfondie après la résolution initiale. Vous pouvez utiliser la fonctionnalité de commande unresolve pour déplacer un ou plusieurs messages de l’affichage *Résolu* vers la vue *En attente* .

Pour annuler l’exécution des messages, effectuez les étapes suivantes :

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un utilisateur affecté aux groupes de *rôles Analyste de conformité des communications* ou *Enquêteur de conformité des communications* dans votre organisation Microsoft 365.
2. Dans le portail de conformité Microsoft Purview, accédez à **La conformité des communications**.
3. Sélectionnez l’onglet **Stratégies** , puis sélectionnez une stratégie qui contient le message d’alerte résolu, double-cliquez pour ouvrir la page **Stratégie** .
4. Dans la page **Stratégie** , sélectionnez l’onglet **Résolu** .
5. Sous l’onglet **Résolu** , sélectionnez un ou plusieurs messages pour revenir à *En attente*.
6. Dans la barre de commandes, sélectionnez **Unresolve**.
7. Dans le volet **Élément Unresolve** , ajoutez tous les commentaires applicables à l’action unresolve et **sélectionnez Enregistrer** pour rétablir l’élément *En attente*.
8. Sélectionnez l’onglet **En attente** pour vérifier que les éléments sélectionnés sont affichés.
