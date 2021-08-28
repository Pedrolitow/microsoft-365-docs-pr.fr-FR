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
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 125e622b39b6ec868cb6dffaf30eb8d64a346759
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58571434"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Examiner et corriger les alertes de conformité des communications

Une fois que vous avez configuré vos stratégies de conformité des communications, vous commencez à recevoir des alertes dans le Centre de conformité Microsoft 365 pour les problèmes de message qui correspondent à vos conditions de stratégie. Suivez les instructions de flux de travail ici pour examiner et corriger les problèmes d’alerte.

## <a name="investigate-alerts"></a>Examiner les alertes

La première étape pour examiner les problèmes détectés par vos stratégies consiste à examiner les alertes de conformité des communications dans le Centre de conformité Microsoft 365. Il existe plusieurs domaines dans la zone de solution de conformité des communications pour vous aider à examiner rapidement les alertes, selon la façon dont vous préférez afficher le regroupement d’alertes :

- **Page** Stratégie de conformité des communications : lorsque vous vous connectez à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365, sélectionnez Conformité des communications pour afficher la page Stratégie de conformité [https://compliance.microsoft.com](https://compliance.microsoft.com) des communications.   Cette page affiche les stratégies de conformité des communications configurées pour votre organisation Microsoft 365 et des liens vers les modèles de stratégie recommandés. Chaque stratégie répertoriée inclut le nombre d’alertes qui doivent être revue, le nombre d’éléments résordés et résolus, l’état de la stratégie et la date et l’heure de la dernière analyse de stratégie. La sélection d’une stratégie affiche toutes les alertes en attente pour les correspondances à la stratégie, une alerte spécifique pour lancer la page de détails de la stratégie et démarrer les actions de correction.
- **Alertes :** accédez aux **alertes** de conformité des communications pour afficher les 30 derniers jours d’alertes regroupées  >   par correspondances de stratégie. Cet affichage vous permet de voir rapidement les stratégies de conformité des communications qui génèrent la plupart des alertes classées par gravité. Pour démarrer les actions de correction, sélectionnez la stratégie associée à l’alerte pour lancer la page **détails de la stratégie.** À partir de la page **Détails** de la stratégie, vous pouvez consulter un résumé des activités de la **page** Vue d’ensemble, examiner et agir sur les messages d’alerte sur la **page** En attente, ou passer en revue l’historique des alertes fermées sur la page **Résolu.**
- **Rapports :** accédez aux rapports **de conformité des communications** pour afficher les widgets de rapport  >   de conformité des communications. Chaque widget fournit une vue d’ensemble des activités et des états de conformité des communications, y compris l’accès à des informations plus approfondies sur les correspondances de stratégie et les actions de correction.

### <a name="using-filters"></a>Utilisation de filtres

L’étape suivante consiste à trier les messages de sorte qu’il soit plus facile de rechercher des alertes. Dans la page **Détails** de la stratégie, la conformité des communications prend en charge le filtrage à plusieurs niveaux pour plusieurs champs de message pour vous aider à examiner rapidement les messages avec des correspondances de stratégie. Le filtrage est disponible pour les éléments en attente et résolus pour chaque stratégie configurée. Vous pouvez configurer des requêtes de filtrage pour une stratégie ou configurer et enregistrer des requêtes de filtrage personnalisées et par défaut à utiliser dans chaque stratégie spécifique. Une fois que vous avez configuré les champs d’un filtre, les champs de filtre affichés en haut de la file d’attente de messages d’alerte peuvent être configurés pour des valeurs de filtre spécifiques.

Pour obtenir la liste complète des filtres et des détails des champs, voir [Filtres](communication-compliance-feature-reference.md#filters) dans l’article de référence des fonctionnalités.

#### <a name="to-configure-a-filter"></a>Pour configurer un filtre

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications.**

3. Sélectionnez **l’onglet** Stratégies, puis sélectionnez une stratégie pour l’examen, double-cliquez pour ouvrir la page **Stratégie.**

4. Dans la page **Stratégie,** sélectionnez  l’onglet **En** attente ou Résolu pour afficher les éléments à filtrer.

5. Sélectionnez **le contrôle Filtres** pour ouvrir la page **Détails** filtres.

6. Activez une ou plusieurs case à cocher pour activer des filtres pour ces alertes. Vous pouvez choisir parmi de nombreux filtres, notamment *Date,* *Expéditeur,* *Objet/Titre,* *Classifieurs,* *Langue,* etc.

7. Si vous souhaitez enregistrer le filtre sélectionné comme filtre par défaut, **sélectionnez Enregistrer par défaut.** Si vous souhaitez utiliser ce filtre en tant que filtre enregistré, sélectionnez **Terminé**.

8. Si vous souhaitez enregistrer les filtres sélectionnés en  tant que requête de filtre, sélectionnez Enregistrer le contrôle de requête après avoir configuré au moins une valeur de filtre. Entrez un nom pour la requête de filtre, puis sélectionnez **Enregistrer.** Ce filtre est disponible uniquement pour cette stratégie et est répertorié dans la **section** Requêtes de filtre enregistrées de la page **Détails** des filtres.

    ![Contrôles détaillés du filtre de conformité des communications.](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Utilisation de l’analyse de doublons proche et exacte

Les stratégies de conformité des communications analysent et pré-groupent automatiquement les doublons de messages proches et exacts sans étapes de configuration supplémentaires. Cette vue vous permet d’agir rapidement sur des messages similaires un par un ou en tant que groupe, ce qui réduit la charge d’examen des messages pour les réviseurs. Au fur et à mesure que des doublons sont détectés, les contrôles **Doublons proches** et/ou les contrôles **Doublons exacts** sont affichés dans la barre d’outils action de correction. Cet affichage n’est pas disponible si des doublons proches ou exacts sont in trouvés.

#### <a name="to-remediate-duplicates"></a>Pour corriger les doublons

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications.**

3. Sélectionnez **l’onglet** Stratégies, puis sélectionnez une stratégie pour l’examen, double-cliquez pour ouvrir la page **Stratégie.**

4. Dans la page **Stratégie,** sélectionnez  l’onglet **En attente** ou Résolu pour afficher les messages en double.

5. Sélectionnez les **contrôles Doublons proches** ou **Doublons exacts** pour ouvrir la page de détails des doublons.

6. Sélectionnez un ou plusieurs messages pour les contrôles d’action de correction de ces messages.

7. Sélectionnez **Résoudre,** **Avertir,** **Réamorcer** ou **Télécharger** pour appliquer l’action aux messages en double sélectionnés comme filtre par défaut.

8. Sélectionnez **Fermer** après avoir terminé les actions de correction sur les messages.

    ![Contrôles dupliqués exacts de conformité des communications.](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Corriger les alertes

Quel que soit l’endroit où vous commencez à réviser les alertes ou le filtrage que vous configurez, l’étape suivante consiste à prendre des mesures pour résoudre le problème. Démarrez la correction des alertes à l’aide du flux de travail suivant dans les pages **Stratégie** **ou Alertes.**

### <a name="step-1-examine-the-message-basics"></a>Étape 1 : Examiner les principes de base des messages

 Il est parfois évident, d’après la source ou l’objet, qu’un message peut être corrigé immédiatement. Il se peut que le message soit insérable ou qu’il corresponde incorrectement à une stratégie et qu’il soit résolu comme incorrectement classé. Sélectionnez **le rapport comme** contrôle mal classé pour partager du contenu mal classé avec Microsoft, résoudre immédiatement l’alerte et supprimer de la file d’attente des alertes en attente. À partir de la source ou de l’expéditeur, vous savez peut-être déjà comment le message doit être routé ou géré dans ces circonstances. Envisagez d’utiliser les contrôles **Baliser comme** ou **Réaffectation** afin d’affecter une balise aux messages applicables ou d’envoyer des messages à un réviseur désigné.

![Contrôles de correction de la conformité des communications.](../media/communication-compliance-remediation-controls.png)

### <a name="step-2-examine-the-message-details"></a>Étape 2 : Examiner les détails du message

Après avoir examiné les informations de base du message, il est temps d’ouvrir un message pour examiner les détails et déterminer d’autres actions de correction. Sélectionnez un message pour afficher l’ensemble des informations d’en-tête et de corps du message. Plusieurs options et vues différentes sont disponibles pour vous aider à déterminer la bonne action :

- **Pièces jointes**: cette option vous permet d’examiner les pièces jointes modernes qui correspondent aux conditions de stratégie. Le contenu des pièces jointes modernes est extrait sous forme de texte et est consultable dans le tableau de bord Des alertes en attente pour une stratégie. Pour plus d’informations, voir la référence de la fonctionnalité [de conformité des communications.](/microsoft-365/compliance/communication-compliance-feature-reference#supported-communication-types)
- **Source**: cet affichage est l’affichage de message standard couramment utilisé dans la plupart des plateformes de messagerie web. Les informations d’en-tête sont formatées dans le style normal et le corps du message prend en charge les fichiers graphiques imbedded et le texte wrapped word. Si la reconnaissance optique de caractères [(OCR)](communication-compliance-feature-reference.md#optical-character-recognition-ocr) est activée pour la stratégie, les images contenant du texte imprimé ou manuscrit qui correspondent à la condition de stratégie sont vues comme un élément enfant pour le message associé dans cette vue.
- Texte simple : le mode Texte affiche une vue texte numéroée uniquement du message et inclut la mise en surbrillance des mots clés dans les messages et les pièces jointes pour les termes de type d’informations sensibles ou les mots clés mis en correspondance dans la stratégie de conformité des communications associée. La mise en surbrillance des mots clés peut vous aider à analyser rapidement les longs messages et pièces jointes pour le domaine d’intérêt. Dans certains cas, le texte mis en surbrillante peut être uniquement dans les pièces jointes pour les messages correspondant aux conditions de stratégie. La mise en surbrillance des mots clés n’est pas prise en charge pour les termes identifiés par les classifieurs intégrés affectés à une stratégie. Les fichiers incorporés ne sont pas affichés et la ligne numérotant cet affichage est utile pour faire référence à des détails pertinents parmi plusieurs relecteurs.
- **Annoter**: cette vue permet aux réviseurs d’ajouter des annotations directement sur le message qui sont enregistrées dans l’affichage du message. Si [l’ocr](communication-compliance-feature-reference.md#optical-character-recognition-ocr) est activé pour la stratégie, les images contenant du texte imprimé ou manuscrit qui correspondent à la condition de stratégie sont vues comme un élément enfant pour le message associé dans cet affichage et peuvent être annotées.
- **Conversation (aperçu)**: disponible pour les messages de conversation Microsoft Teams, cet affichage affiche jusqu’à cinq messages avant et après un message d’alerte pour aider les réviseurs à afficher l’activité dans le contexte de conversation. Ce contexte permet aux réviseurs d’évaluer rapidement les messages et de prendre des décisions de résolution des messages plus éclairées. Les ajouts de messages en temps réel aux conversations s’affichent, y compris toutes les images en ligne, les emojis et les autocollants disponibles dans Teams. Les pièces jointes d’image ou de texte à des messages ne sont pas affichées. Les notifications s’affichent automatiquement pour les messages qui ont été modifiés ou pour les messages qui ont été supprimés de la fenêtre de conversation. Lorsqu’un message est résolu, les messages de conversation associés ne sont pas conservés avec le message résolu. Les messages de conversation sont disponibles pendant 60 jours après l’identification du message d’alerte.
- **Historique des utilisateurs** : le mode historique des utilisateurs affiche toutes les autres alertes générées par une stratégie de conformité des communications pour l’utilisateur qui envoie le message.
- **Notification de modèle détectée :** de nombreuses actions d’harcèlement et d’agresseur au fil du temps et impliquent la récurration d’instances du même comportement par un utilisateur. La notification *de modèle détecté* s’affiche dans les détails de l’alerte et attirer l’attention sur l’alerte. La détection des modèles se fait par stratégie et évalue le comportement au cours des 30 derniers jours lorsqu’au moins deux messages sont envoyés au même destinataire par un expéditeur. Les enquêteurs et les réviseurs peuvent utiliser cette notification pour identifier le comportement répété afin d’évaluer l’alerte selon le cas.
- **Traduction**: cet affichage convertit automatiquement le texte du  message d’alerte en la langue configurée dans le paramètre de langue Affichée dans l’abonnement Microsoft 365 pour chaque réviseur. *L’affichage Traduction* permet d’élargir la prise en charge de l’examen pour les organisations avec des utilisateurs multilingues et élimine la nécessité d’autres services de traduction en dehors du processus de révision de la conformité des communications. À l’aide  des services de traduction Microsoft, l’affichage Traduction peut être allumé et désactivé selon les besoins et prend en charge un large éventail de langues. Pour obtenir la liste complète des langues pris en charge, [voir Traducteur Microsoft Langues.](https://www.microsoft.com/translator/business/languages/) Les langues répertoriées dans la *liste Traducteur langues* sont pris en charge dans *l’affichage* Traduction.

### <a name="step-3-decide-on-a-remediation-action"></a>Étape 3 : Décider d’une action de correction

Maintenant que vous avez examiné les détails du message pour l’alerte, vous pouvez choisir plusieurs actions de correction :

- **Résoudre**: la sélection du contrôle **Résoudre** supprime immédiatement le message de la file d’attente des **alertes** en attente et aucune autre action ne peut être prise sur le message. En sélectionnant **Résoudre,** vous avez essentiellement fermé l’alerte sans classification supplémentaire et elle ne peut pas être rouverte pour d’autres actions. Tous les messages résolus sont affichés dans **l’onglet Résolu.**
- **Signaler une erreur de classification (aperçu)**: vous pouvez toujours résoudre un message comme mal classé à tout moment pendant le flux de travail de révision du message. Une classification incorrecte signifie que l’alerte ne peut pas être actionnable ou que l’alerte a été générée de manière incorrecte par le processus d’alerte et tous les classifieurs entraisables. La résolution de l’élément comme étant mal classé envoie le contenu du message, les pièces jointes et l’objet du message (y compris les métadonnées) à Microsoft afin d’améliorer les classifieurs entraisables. Les données envoyées à Microsoft ne contiennent pas d’informations qui peuvent identifier ou être utilisées pour identifier les utilisateurs de votre organisation. D’autres actions ne peuvent pas être prises sur le message et tous les messages mal classés sont affichés dans **l’onglet Résolu.**
- **Power Automate (aperçu)**: utilisez un flux Power Automate pour automatiser les tâches de traitement d’un message d’alerte. Par défaut, la conformité des communications inclut le gestionnaire notify lorsqu’un utilisateur dispose d’un modèle de flux d’alerte de conformité des *communications* que les réviseurs peuvent utiliser pour automatiser le processus de notification pour les utilisateurs avec des alertes de message. Pour plus d’informations sur la création et la gestion des flux Power Automate conformité des communications, consultez l’article de référence de la fonctionnalité de conformité [des](communication-compliance-feature-reference.md#power-automate-flows) communications.
- **Marquez le** message comme étant *conforme,* *non* conforme ou aussi *discutable* en ce qui concerne les stratégies et les normes de votre organisation. L’ajout de balises et de commentaires de marquage vous permet de filtrer les alertes de stratégie de micro-filtrage pour les escalades ou dans le cadre d’autres processus de révision interne. Une fois le marquage terminé, vous pouvez également choisir de résoudre le message pour le déplacer hors de la file d’attente de révision.
- **Notifier**: vous pouvez utiliser le contrôle **Notify** pour affecter un modèle de notification personnalisé à l’alerte et pour envoyer une notification d’avertissement à l’utilisateur. Choisissez le modèle d’avis approprié configuré dans  la zone **Paramètres** de conformité des communications, puis sélectionnez Envoyer un rappel par courrier électronique à l’utilisateur qui a envoyé le message et résoudre le problème.
- **Escalade :** à l’aide  du contrôle Réamorcer, vous pouvez choisir les autres membres de votre organisation qui doivent examiner le message. Choisissez parmi une liste de réviseurs configurés dans la stratégie de conformité des communications pour envoyer une notification par courrier électronique demandant une révision supplémentaire de l’alerte de message. Le réviseur sélectionné peut utiliser un lien figurant dans la notification par courrier électronique pour accéder directement aux éléments qui y sont réaffectés pour révision.
- **Escalate for investigation**: à l’aide du contrôle **Escalate for investigation,** vous pouvez créer un Advanced eDiscovery [pour](overview-ediscovery-20.md) un ou plusieurs messages. Vous devez fournir un nom et des notes pour le nouveau cas, et l’utilisateur qui a envoyé le message correspondant à la stratégie est automatiquement affecté en tant que dépositaire de cas. Vous n’avez pas besoin d’autorisations supplémentaires pour gérer le cas. La création d’un cas ne résout pas ou ne crée pas de balise pour le message. Vous pouvez sélectionner un total de 100 messages lors de la création d’un Advanced eDiscovery au cours du processus de correction. Les messages dans tous les canaux de communication surveillés par la conformité des communications sont pris en charge. Par exemple, vous pouvez sélectionner 50 conversations Microsoft Teams, 25 messages électroniques Exchange Online et 25 messages Yammer lorsque vous ouvrez un nouveau cas Advanced eDiscovery pour un utilisateur.
- Supprimer un message dans **Teams**: à l’aide du contrôle Supprimer le message dans **Teams,** vous pouvez bloquer les messages inappropriés et le contenu identifiés dans les alertes à partir de canaux Microsoft Teams et de conversations 1:1 et de groupe. Les messages et le contenu supprimés sont remplacés par un conseil de stratégie qui explique qu’il est bloqué et la stratégie qui s’applique à sa suppression de l’affichage. Un lien est fourni aux destinataires dans le conseil de stratégie pour en savoir plus sur la stratégie applicable et le processus de révision. L’expéditeur reçoit un conseil de stratégie pour le message et le contenu bloqués, mais peut examiner les détails du message bloqué et du contenu pour le contexte concernant la suppression.

    ![Supprimez un message de Microsoft Teams.](../media/communication-compliance-remove-teams-message.png)

### <a name="step-4-determine-if-message-details-should-be-archived-outside-of-communication-compliance"></a>Étape 4 : Déterminer si les détails des messages doivent être archivés en dehors de la conformité des communications

Les détails des messages peuvent être exportés ou téléchargés si vous avez besoin d’archiver les messages dans une solution de stockage distincte. La sélection du contrôle **Télécharger** ajoute automatiquement les messages sélectionnés à un fichier .ZIP qui peut être sauvegardé en dehors de Microsoft 365.
