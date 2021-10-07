---
title: Créer et gérer des stratégies dans la gestion de la confidentialité Microsoft (aperçu)
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: Découvrez comment créer et gérer des stratégies de gestion des données personnelles de votre organisation dans Microsoft 365, répondre aux alertes et résoudre les problèmes.
ms.openlocfilehash: dec7fd3692330dc267bace22451f1dc65ccd8fd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60179018"
---
# <a name="create-and-manage-policies-in-privacy-management-preview"></a>Créer et gérer des stratégies dans la gestion de la confidentialité (aperçu)

Les stratégies vous permettent de définir les types de risques de confidentialité à rechercher dans les données Microsoft 365 de votre entreprise et d’établir les résultats préférés pour les scénarios où des correspondances sont trouvées. Votre organisation peut travailler à partir des alertes qui en résultent pour examiner les données correspondantes et résoudre les problèmes, à partir de la solution de gestion de la confidentialité.

La gestion de la confidentialité fournit des modèles qui vous permettent de commencer facilement la création de stratégies et vous permet d’affiner votre approche par le biais d’options de personnalisation étendues. Les principaux scénarios couverts par les modèles de gestion de la confidentialité sont les suivants :

- **Surexpossure des données**: détecte les données personnelles surexposées et invite les utilisateurs à les sécuriser.
- **Transfert de données :** spots et aide à limiter les transferts de données personnelles entre départements ou frontières régionales.
- **Réduction des données**: permet aux utilisateurs d’identifier et de réduire la quantité de données personnelles inutilisées.

Pour en savoir plus sur les fonctionnalités de chaque modèle, voir ci-dessous.

## <a name="policy-types"></a>Les types de stratégies

### <a name="data-overexposure"></a>Surexposure des données

La gestion de la confidentialité peut vous aider à détecter et gérer les situations dans lesquelles les données que vous avez stockées ne sont pas suffisamment sécurisées. Par exemple, si l’accès à un site interne est ouvert à un groupe trop large ou si vos paramètres d’autorisation n’ont pas été tenus à jour, les données personnelles stockées sur ce site peuvent être vulnérables à une violation. Vous pouvez utiliser le modèle de stratégie de données de la gestion de la confidentialité pour évaluer vos données et vous avertir des problèmes potentiels.

### <a name="data-transfer"></a>Transfert de données

Le transfert de données entre départements ou frontières régionales peut augmenter le risque d’exposition des données, par exemple si elles sont envoyées via des e-mails non chiffrés ou à des destinataires non autorisés. De telles actions peuvent avoir un impact réglementaire ou aller à l’encontre des pratiques établies en matière de confidentialité. L’utilisation du modèle de transfert de données pour créer des stratégies de gestion de la confidentialité peut repérer et limiter ces transferts.

> [!NOTE]
> Pendant la prévisualisation publique, certains clients exécutant des stratégies de transfert de données pour détecter les transferts entre régions peuvent rencontrer des problèmes de synchronisation qui ont un impact sur la visibilité des correspondances de stratégie dans les données Exchange et Teams données. Nous vous recommandons de vous concentrer sur SharePoint données OneDrive lors de l’aperçu de ce type de stratégie.

### <a name="data-minimization"></a>Réduction des données

Au fil du temps, les entreprises peuvent collecter de grandes quantités de données personnelles auprès de clients ou d’employés. Cela inclut parfois des données qui ont été collectées au-delà des besoins, ou qui sont autrement inutilisées et qui doivent être réduites pour limiter les risques de confidentialité liés à ces informations. Le modèle de réduction des données peut être utilisé pour traiter les risques de ce type.

## <a name="get-started-with-default-templates"></a>Mise en place des modèles par défaut

La gestion de la confidentialité vous aidera à lancer votre processus d’évaluation des données en créant trois stratégies avec des paramètres par défaut, à l’aide des modèles de réduction des données, de surexposation des données et de transferts de données. Ces stratégies sont en cours d’application par défaut, mais ne déclenchent pas automatiquement les messages de notification ou les invites de correction. Après votre configuration initiale, vous pouvez continuer à créer et personnaliser vos propres stratégies.

## <a name="create-a-privacy-management-policy"></a>Créer une stratégie de gestion de la confidentialité

Il existe deux chemins d’accès pour créer des stratégies de gestion de la confidentialité. La première option consiste à choisir parmi l’ensemble de modèles prédéfin définis. Vous pouvez également personnaliser votre propre stratégie, en utilisant l’un de ces modèles comme point de départ.

### <a name="create-a-policy-from-a-template"></a>Créer une stratégie à partir d’un modèle

Pour commencer immédiatement avec une stratégie, sélectionnez l’un des trois types de stratégie pré-définies. Pour passer en revue les détails de l’un d’eux, vous pouvez sélectionner les paramètres d’affichage pour afficher les propriétés spécifiques qui sont à l’origine de la stratégie, y compris les types de données, les emplacements de données et les conditions qui déclenchent des correspondances de stratégie.

Lorsque vous créez une stratégie directement à partir d’un modèle, de nombreux paramètres sont automatiquement choisis. Cela inclut l’option d’option par défaut de la stratégie. Si vous souhaitez afficher un aperçu de la stratégie en action avant de l’activer entièrement, recherchez-la dans votre liste après sa création, modifiez la stratégie et basculez-la en mode test. Pour plus d’informations, voir [Tester votre stratégie.](#test-your-policy)

### <a name="create-custom-policy"></a>Créer une stratégie personnalisée

Pour prendre un contrôle granulaire des paramètres d’une stratégie, vous pouvez créer une stratégie personnalisée à l’aide de l’un des modèles existants comme base de référence. La gestion de la confidentialité fournit un Assistant pour vous guider tout au long de ces étapes.

Les propriétés personnalisables sont les suivantes :

- **Name and type**: Choose the template to build your policy on, then name and describe your version.
- **Données à surveiller :** sélectionnez le type de données personnelles que votre stratégie surveillera. Choisissez parmi les groupes de classification disponibles ou dans la liste des types d’informations sensibles individuels. Pour en savoir plus, consultez les options d’analyse des données ci-dessous.
- **Utilisateurs**: sélectionnez si cette stratégie s’applique à tous les utilisateurs ou aux utilisateurs sélectionnés. Si vous choisissez la deuxième option, vous pouvez sélectionner jusqu’à 300 utilisateurs de votre choix dans la liste fournie.
- **Emplacements**: choisissez les emplacements dans Microsoft 365 que votre stratégie doit couvrir, tels que les données de SharePoint ou Exchange de votre organisation.
- **Conditions**: sélectionnez les conditions pertinentes pour votre type de stratégie. Par exemple, vous pouvez spécifier les types de transferts qu’une stratégie de transfert de données doit rechercher ou les données récemment utilisées pour une stratégie de réduction des données.
- **Résultats :** définissez les résultats lorsqu’une correspondance de stratégie est détectée. Vos options dépendent du type de stratégie que vous débutez. Les résultats possibles sont les suivants :
  - **Notifications par courrier électronique**: ce paramètre vous permet de déclencher des notifications par courrier électronique digest, y compris des liens vers des formations connexes. Pour plus d’informations, voir Définir les notifications par courrier électronique de l’utilisateur ci-dessous.
  - **Teams**: donnez aux utilisateurs Teams conseils et recommandations de stratégie, ainsi que des liens vers des formations connexes. Cette option est disponible pour les stratégies de transfert de données.
- **Alertes :** déterminez la fréquence des alertes pour les administrateurs lorsqu’une correspondance de stratégie est détectée. Les options ne comprennent pas d’alertes, d’alertes pour chaque correspondance de stratégie ou d’alertes lorsqu’un seuil spécifique est atteint. Si vous choisissez l’option de seuil, définissez les paramètres souhaités.
- **Mode**: déterminez s’il faut d’abord exécuter une stratégie en mode test ou l’activer immédiatement. Pour plus d’informations, voir Tester votre stratégie.
Une fois que vous avez passé en revue tous les paramètres de l’Assistant, examinez vos paramètres, modifiez-les si nécessaire, puis enregistrez votre stratégie.

#### <a name="choose-data-monitoring-options"></a>Choisir les options d’analyse des données

Lors de la configuration d’une stratégie personnalisée, vous serez invité à sélectionner les types de données que votre stratégie doit surveiller. Les options sont les suivantes :

- **Groupes de classification**: liste d’ensembles de données utilisables dans une recherche en fonction des principales réglementations en matière de confidentialité, telles que le R GDPR ou la LOI AMÉRICAINE. Afficher les détails d’un groupe pour voir les types d’informations sensibles qu’il couvre. Sélectionnez un ou plusieurs de ces ensembles pour les utiliser tels qu’ils sont. Les groupes actuellement disponibles sont les suivants :
  - Australia Health Records Act (HRIP Act) Enhanced
  - Amélioration de la loi sur la protection de la vie privée en Australie
  - (UE) Règlement général sur la protection des données (R GDPR) amélioré
  - Amélioration des données d’informations d’identification personnelle (PII) au Japon
  - Protection améliorée des informations personnelles au Japon
  - U.S. Gramm-Leach-Bliley Act (GLBA) Enhanced
  - U.S. Health Insurance Act (HIPAA) Enhanced
  - U.S. Patriot Act Enhanced
  - Données d’informations d’identification personnelle (PII) améliorées pour les États-Unis
  - U.S. State Breach Notification Laws Enhanced
- Types d’informations sensibles individuels : en choisissant vous-même des types d’informations sensibles spécifiques, tels que des numéros de sécurité sociale ou des informations de permis de conduire, vous pouvez personnaliser votre propre groupe ou groupe de données à rechercher. Cet Assistant vous permet de sélectionner dans la liste complète des types d’informations sensibles dans la gestion de la confidentialité. Chaque type d’informations possède ses propres propriétés. Utilisez le bouton d’informations à côté de l’un d’eux pour obtenir des détails et des remarques sur les paramètres recommandés. Si vous créez plusieurs groupes, l’Assistant vous permet d’appliquer des opérateurs booléens pour les relier et définir leur ordre d’opération.

Si vous utilisez des groupes de classification pré-définies, vous ne pouvez pas également sélectionner des types individuels ou créer vos propres groupes. Pour une plus grande flexibilité, choisissez des types d’informations sensibles individuels. Pour utiliser les normes les plus courantes, choisissez parmi les groupes de classification.

#### <a name="test-your-policy"></a>Tester votre stratégie

Si vous souhaitez évaluer une nouvelle stratégie avant de l’activer entièrement, définissez votre stratégie en mode test. Le mode test vous permet de rechercher les correspondances des 30 derniers jours, d’évaluer le comportement de la stratégie et de passer en revue les types d’alertes générés. Nous vous recommandons d’exécutez des stratégies de test pendant au moins cinq jours pour obtenir des résultats représentatifs. Au cours de la phase de test, vous avez la possibilité de modifier et d’ajuster les paramètres de la stratégie. Une fois que vous avez obtenu des informations sur l’exécution du test, vous pouvez activer la stratégie. Pendant l’exécution d’une stratégie en mode test, aucun message de notification de l’utilisateur n’est remis.

#### <a name="set-user-email-notifications"></a>Définir les notifications par courrier électronique de l’utilisateur

Avec les notifications par courrier électronique, les utilisateurs reçoivent des notifications directes sur les correspondances de stratégie et les tâches importantes à effectuer. Les destinataires recevront des résumés de courrier qui résument les données à examiner et les actions possibles, telles que la possibilité de rendre les documents privés, de les conserver dans un fichier, de signaler les correspondances faux positifs et d’ajouter des notes pour référence ultérieure. Ces e-mails incluent également des liens pour les destinataires de formation sur la façon de gérer ces cas. La fourniture de ces liens est requise lors de la configuration initiale des notifications et doit pointer vers votre propre documentation interne sur les processus et les meilleures pratiques.

Les notifications peuvent être activées pour des stratégies individuelles lors de la création d’une stratégie personnalisée ou lors de la modification d’une stratégie. Utilisez la section Résultats pour définir ce qui se produit lorsqu’une correspondance de stratégie est détectée, y compris l’option permettant d’activer ces notifications et définir la fréquence de livraison de ces résumés.

La fonctionnalité de notification par courrier électronique est contrôlée au niveau global au sein Paramètres. Elle est activée par défaut. La mise hors service de ce paramètre arrête tous les e-mails même si des notifications spécifiques ont été configurées au niveau d’une stratégie individuelle. Pour plus d’informations, voir [Gérer les paramètres de gestion de la confidentialité.](privacy-management-settings.md)

## <a name="view-policy-details"></a>Afficher les détails de la stratégie

Une fois votre stratégie créée, sélectionnez-la sur la page **principale Stratégies** pour voir sa vue d’ensemble complète. La page de détails de stratégie fournit des informations sur vos données, vous permet d’afficher du contenu sur des correspondances de stratégie spécifiques et vous donne des conseils sur les étapes suivantes. Si votre stratégie s’exécute en mode test, cette page est également l’endroit où vous pouvez activer votre stratégie lorsque le test est terminé.

Une fois que votre stratégie est active, vous pouvez continuer à consulter sa page de détails de stratégie pour voir les informations en cours sur les domaines problématiques, la gravité et les tendances des alertes, ainsi que les mesures correctives prises.

## <a name="resolve-policy-alerts-and-issues"></a>Résoudre les alertes et les problèmes de stratégie

Une fois vos stratégies activées, la gestion de la confidentialité vous informera des découvertes importantes en vous avertissant des correspondances de stratégie, en aclassant leur gravité et en vous permettant d’agir en créant et en résolvant les problèmes.

La page Vue d’ensemble de la gestion de la confidentialité fournit une vue d’ensemble de ces résultats avec des mises à jour dynamiques sur les principaux domaines de préoccupation, tels que les stratégies ayant le plus de correspondances et vos alertes de stratégie actuellement actives. Vous pouvez également accéder aux détails de vos alertes et problèmes via la page principale stratégies.

### <a name="alerts"></a>Alertes

Pour évaluer vos alertes actives et spécifier les problèmes qui nécessitent un suivi, accédez à votre page **Alertes.** Il fournit une liste filtrable des alertes générées par vos stratégies, que vous pouvez examiner individuellement pour déterminer les circonstances dans lesquelles elles ont été déclenchées.

La sélection d’une alerte ouvre un volet deover avec des détails supplémentaires, tels que le type de stratégie, le nombre d’éléments correspondants et la gravité selon les paramètres de votre stratégie. Sous **l’onglet** Contenu, vous pouvez passer en revue les fichiers impliqués dans cette alerte. Ces informations peuvent fournir des informations supplémentaires sur l’événement spécifique qui a déclenché l’alerte, l’endroit où se trouvent les fichiers et les types de données personnelles impliqués. Les déclencheurs des alertes sont déterminés par les conditions spécifiques de chaque stratégie. Par exemple, une alerte peut être déclenchée sur une stratégie de transfert de données si la gestion de la confidentialité détecte un transfert entre les départements ou régions spécifiés de la stratégie.

Après avoir évalué une alerte dans la  liste, vous pouvez utiliser l’action Créer un problème pour vous aider à poursuivre l’examen et l’action. Vous serez invité à nommer le problème et à ajouter les commentaires pertinents pour le contexte. Vous pouvez également ignorer les alertes ici si elles ne nécessitent pas de suivi.

### <a name="issues"></a>Problèmes

Comme décrit dans la section Alertes, des problèmes sont créés lors de l’évaluation des alertes concernant les correspondances de stratégie. Pour suivre et résoudre les problèmes indiqués, visitez la page Problèmes. À partir de là, vous pouvez examiner les problèmes individuels, examiner les conditions d’analyse, examiner les données et prendre les mesures nécessaires pour fermer le cas.

Cette page fournit la liste de tous les problèmes d’ouverture. Les problèmes sont répertoriés par nom et triés par gravité pour vous aider à hiérarchiser les cas, y compris les catégories élevée, moyenne et faible, ainsi que les catégories non classées. Sélectionnez un problème dans la liste pour examiner son contenu et prendre des mesures pour le résoudre. Vous pouvez évaluer la gravité des problèmes non signés au cours de l’examen.

#### <a name="issue-overview"></a>Vue d’ensemble du problème

Les pages de détails des problèmes vous aident à résoudre les risques de confidentialité identifiés et à gérer correctement les fichiers indiqués. Sous **l’onglet** Vue d’ensemble, vous pouvez voir l’étape en cours à prendre, indiquant l’état du problème et les actions recommandées suivantes. Vous pouvez également passer en revue les informations essentielles sur le contenu impliqué, la stratégie associée, les détails sur l’alerte et la chronologie.

Les onglets suivants fournissent des détails supplémentaires sur les alertes et le contenu associés, ainsi que les notes d’autres membres de votre équipe qui travaillent sur le problème. Vous pouvez gérer la liste des collaborateurs actifs via **l’onglet Collaborateurs.**

#### <a name="share-the-issue"></a>Partager le problème

L’ajout de personnes en tant que collaborateurs vous permet de partager le problème avec d’autres membres de votre entreprise via un canal Microsoft Teams sécurisé, un courrier électronique de l’entreprise ou en partageant un lien directement vers la page du problème dans la gestion de la confidentialité. Ces options sont disponibles sous le **bouton** Partager. Lors du partage via Teams, vous serez invité à sélectionner les équipes disponibles dans votre organisation, à sélectionner le canal spécifique et à laisser un message sur le problème, qui sera partagé avec le canal spécifié.

#### <a name="review-content-and-remediate"></a>Examiner le contenu et corriger

Pour examiner le contenu associé à  un problème, choisissez l’action Examiner le contenu si vous y êtes invité ou ouvrez l’onglet Contenu. Sélectionnez n’importe quel fichier de la liste pour l’afficher dans son intégralité. Vous pouvez voir ici des détails sur le fichier, les activités sur l’enregistrement et son historique de correction, si des étapes précédentes ont été prises pour gérer ce fichier.

Utilisez le **bouton Corriger** pour prendre vos propres décisions de gestion des données pour ce contenu. La sélection du bouton vous permet de choisir parmi une ou plusieurs actions de correction. Les options suivantes sont disponibles : 

**Toutes les stratégies**

- **Avertir**: informer le propriétaire du contenu du problème détecté.
- **Appliquer une étiquette de rétention**: ajoutez une étiquette sur la rétention des données pour cet élément. 
- **Appliquer une étiquette de niveau de** sensibilité : ajoutez une étiquette sur la sensibilité des données de cet élément.
- **Marquer comme n’étant pas une correspondance**: identifiez un résultat de recherche comme faux positif pour supprimer l’élément de contenu de la considération.

**Réduction des données**

- **Recyclage/suppression :** utilisez cette option pour une suppression souple des données. Le contenu est déplacé dans le dossier des éléments supprimés ou dans la bac de recyclage (Exchange, SharePoint, OneDrive) ou supprimé avec une option de récupération (Teams messages). La suppression peut être annulée dans un laps de temps donné, en fonction des paramètres du service.

**Surexposation de données et transfert de données**

- **Unshare**: arrêter le partage d’un lien vers cet élément de contenu.

Chaque option vous invite à laisser des commentaires et toute autre information de prise en charge nécessaire pour le propriétaire du contenu avant de confirmer votre choix.

Une fois que toutes les mesures correctives ont été prises et que le problème est prêt à se fermer, utilisez le bouton Résoudre et ajoutez vos commentaires finaux avant de l’envoyer.

## <a name="delete-a-policy"></a>Suppression d’une stratégie

Si vous avez besoin de supprimer une stratégie de gestion de la confidentialité existante, recherchez-la dans la liste de la page Stratégies, sélectionnez le menu d’action (ellipses verticales), puis choisissez l’action supprimer la stratégie. Vous serez invité à confirmer votre choix avant la suppression finale et la suppression définitive de la stratégie. La suppression d’une stratégie n’affectera pas les fichiers précédemment évalués par la stratégie, et les problèmes et alertes générés par la stratégie resteront.
