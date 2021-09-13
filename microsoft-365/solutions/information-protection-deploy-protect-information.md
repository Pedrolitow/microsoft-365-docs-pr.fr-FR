---
title: Protéger les informations soumises à la réglementation sur la confidentialité des données
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Déployez Microsoft 365 fonctionnalités de sécurité et de conformité et protégez vos informations personnelles.
ms.openlocfilehash: 084faec3b9c2d7bc9c7da17ee69f7821dd79a754
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59164588"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises à la réglementation sur la confidentialité des données

Un certain nombre de contrôles de protection des informations peuvent être utilisés dans votre abonnement pour vous aider à répondre aux exigences et réglementations en matière de conformité des données. Il s’agit notamment du Règlement général sur la protection des données (RGPD), hipAA-HITECH (loi américaine sur la confidentialité des soins de santé), du CCPA (California Consumer Protection Act) et du LGPD (Brazil Data Protection Act).

Ces contrôles sont dans les zones de solution suivantes :

- Étiquettes de confidentialité
- Protection contre la perte de données (DLP)
- Chiffrement des messages Office (OME)
- contrôles Teams’accès aux sites et aux sites

![Services clés pour protéger les informations personnelles soumises à la réglementation sur la confidentialité des données.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Cette solution décrit les fonctionnalités de sécurité et de conformité pour protéger les informations soumises aux réglementations en matière de confidentialité des données. Pour obtenir la liste complète des fonctionnalités de sécurité dans Microsoft 365, voir [Microsoft 365 documentation de sécurité.](../security/index.yml) Pour obtenir la liste complète des fonctionnalités de conformité dans Microsoft 365, voir [Microsoft 365 documentation de conformité.](../compliance/index.yml)

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Réglementations en matière de confidentialité des données qui ont une incidence sur les contrôles de protection des informations

Voici une liste d’exemples de réglementations de confidentialité des données qui peuvent être liées aux contrôles de protection des informations :

- R GDPR Article 5(1)(f))
- Article R GDPR (32)(1)(a)
- LGPD Article 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Consultez l’article évaluer les risques de confidentialité des données et [identifier les éléments sensibles](information-protection-deploy-assess.md) pour plus d’informations sur chacun des éléments ci-dessus.

Les réglementations en matière de confidentialité des données pour la protection des informations sont recommandées :

- Protection contre la perte ou l’accès non autorisé, l’utilisation et/ou la transmission.
- Application basée sur les risques des mécanismes de protection.
- Utilisation du chiffrement, le cas échéant.

Votre organisation peut également vouloir protéger le contenu Microsoft 365 à d’autres fins, telles que d’autres besoins de conformité ou pour des raisons professionnelles. L’établissement de votre schéma de protection des informations pour la confidentialité des données doit être effectué dans le cadre de la planification, de l’implémentation et de la gestion globales de la protection des informations.

Pour vous aider à démarrer avec un schéma de protection des informations dans Microsoft 365, la section suivante inclut une courte liste des fonctionnalités associées et des actions d’amélioration pour Microsoft 365. La liste inclut des fonctionnalités et des actions d’amélioration applicables aux réglementations en matière de confidentialité des données. Toutefois, la liste n’inclut pas les technologies plus anciennes s’il existe une fonctionnalité plus nouvelle qui a largement la place de l’ancienne. Par exemple, la Gestion des droits de l’information (IRM) pour SharePoint et OneDrive n’est pas incluse dans la liste, mais les étiquettes de niveau de sensibilité sont incluses.

## <a name="managing-information-protection-in-microsoft-365"></a>Gestion de la protection des informations dans Microsoft 365

Les [solutions de protection des informations](../compliance/information-protection.md) Microsoft incluent un certain nombre de fonctionnalités intégrées dans Microsoft 365, Microsoft Azure et Microsoft Windows. Dans Microsoft 365, les solutions de protection des informations sont les suivantes :

- [Types d’informations sensibles](../compliance/sensitive-information-type-entity-definitions.md) (décrits dans l’article Évaluer les risques de confidentialité des données [et identifier les éléments sensibles)](information-protection-deploy-assess.md)
- [Étiquettes de confidentialité](../compliance/sensitivity-labels.md)
  - Niveau service/conteneur
  - Côté client/niveau de contenu
  - Automatisé pour les données au repos dans SharePoint et OneDrive
- Protection contre la perte de données (DLP)
- [Microsoft 365 Protection contre la perte de données de point de terminaison](../compliance/endpoint-dlp-learn-about.md)
- [chiffrement de messages Office 365 nouvelles fonctionnalités (OME)](../compliance/ome.md) et chiffrement [de messages](../compliance/ome-advanced-message-encryption.md) avancés OME

En outre, la protection au niveau du site et de la bibliothèque est un mécanisme important à inclure dans n’importe quel schéma de protection.

Pour plus d’informations sur les autres fonctionnalités de protection des informations en dehors Microsoft 365, voir :

- [Microsoft Cloud Application Security (MCAS)](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Protection des informations Windows](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Les étiquettes de niveau de Protection des données Microsoft vous permet de classifier et de protéger les données de votre organisation sans entraver la productivité des utilisateurs et leur capacité à collaborer.

> [!div class="mx-imgBorder"]
> ![Étiquettes de niveau de Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Conditions préalables pour les étiquettes de niveau de sensibilité

Effectuer ces activités avant d’implémenter l’une des fonctionnalités basées sur les étiquettes de sensibilité mises en évidence ci-dessous :

1. Comprenez les choses suivantes :
   - **Besoins de l'entreprise** Établissez les raisons professionnelles de l’application d’étiquettes de niveau de sensibilité dans votre entreprise. Par exemple, vos exigences de confidentialité des données pour la protection des informations.
   - **Fonctionnalités des étiquettes de sensibilité.** L’étiquetage de la sensibilité peut devenir complexe. Veillez donc à lire la [documentation](../compliance/sensitivity-labels.md) sur les étiquettes de sensibilité avant de commencer.
   - **Éléments clés à retenir** Les étiquettes de sensibilité sont gérées dans le Centre d’administration de conformité Microsoft, mais les options de ciblage et d’application varient considérablement.
      - Il existe des étiquettes de niveau de sensibilité pour les sites, les groupes et les Teams au niveau du conteneur (les paramètres ne s’appliquent pas au contenu à l’intérieur du conteneur). Ceux-ci sont publiés pour les utilisateurs et les groupes qui les appliquent lorsqu’un site, un groupe ou une équipe est en service.
      - Il existe des étiquettes de niveau de sensibilité pour le contenu actif. Ils sont également publiés pour des utilisateurs ou des groupes, qui les appliquent manuellement ou sont automatiquement appliqués dans les cas ci-après :
        - Le fichier est ouvert/modifié/enregistré, soit sur le bureau de l’utilisateur, soit sur SharePoint site.
        - Un e-mail est rédigé et envoyé.
      - Il existe des étiquettes de niveau de sensibilité pour l’application automatique aux fichiers au repos dans SharePoint et OneDrive en plus des e-mails en transit via Exchange. Elles sont ciblées sur tous les sites ou sur des sites spécifiques et s’appliquent automatiquement aux fichiers au repos dans ces environnements.

2. Rationaliser l’étiquetage de sensibilité actuel avec des méthodes passées ou alternatives

   - Azure Information Protection

      Le schéma d’étiquetage de sensibilité actuel peut avoir besoin d’être rapproché de toute implémentation d’étiquetage [Azure Information Protection](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) existante.
   - OME

      Si vous envisagez d’utiliser l’étiquetage de niveau de sensibilité moderne pour la protection du courrier électronique et que des méthodes de chiffrement de courrier électronique existantes telles que OME sont en place, elles peuvent co-exister, mais vous devez comprendre les scénarios dans lesquels l’une ou l’autre doit être appliquée. Voir chiffrement de messages Office 365 nouvelles fonctionnalités [(OME),](#office-365-message-encryption-ome-new-capabilities)qui inclut un tableau comparant la protection moderne du type d’étiquette de sensibilité à la protection basée sur OME.

3. Planifier l’intégration dans un schéma de protection des informations plus large. En plus de la coexistence avec OME, les étiquettes de sensibilité peuvent être utilisées avec des fonctionnalités parallèles telles que la protection contre la perte de données Microsoft 365 (DLP) et Microsoft Cloud App Security. Consultez [Protection des données Microsoft la Microsoft 365](../compliance/information-protection.md) pour atteindre vos objectifs de protection des informations liées à la confidentialité des données.

4. Développer une classification et un modèle de contrôle des étiquettes de sensibilité. Voir [Classification des données et taxonomie des étiquettes de sensibilité.](https://aka.ms/dataclassificationwhitepaper)

### <a name="general-guidance"></a>Directives générales

1. **Définition de schéma.** Avant d’utiliser des fonctionnalités techniques pour appliquer des étiquettes et une protection, travaillez au sein de votre organisation pour définir un schéma de classification. Vous avez peut-être déjà un schéma de classification, ce qui facilite l’ajout de données personnelles.
2. **Mise en place.** Commencez par choisir le nombre et les noms des étiquettes à implémenter. Faites cette activité sans vous soucier de la technologie à utiliser et de la façon dont les étiquettes seront appliquées. Appliquez ce schéma universellement dans toute votre organisation, y compris les données qui résident sur site et dans d’autres services cloud.
3. **Recommandations supplémentaires** Lorsque vous concevez et implémentez des stratégies, des étiquettes et des conditions, envisagez de suivre ces recommandations :

   - **Utilisez le schéma de classification existant (le cas caser).** De nombreuses organisations utilisent déjà la classification des données sous une forme ou une autre. Évaluez soigneusement le schéma d’étiquette existant et, si possible, utilisez-le tel qu’il est. L’utilisation d’étiquettes familières qui sont reconnaissables pour vos utilisateurs finaux permet d’stimuler l’adoption.
   - **Commencez petit.** Il n’existe pratiquement aucune limite au nombre d’étiquettes que vous pouvez créer. Toutefois, un grand nombre d’étiquettes et de sous-étiquettes peut ralentir l’adoption.
   - **Utilisez des scénarios et des cas d’utilisation.** Identifiez les cas d’utilisation courants au sein de votre organisation et utilisez des scénarios dérivés des réglementations en matière de confidentialité des données à laquelle vous êtes soumis. Vérifiez si la configuration d’étiquette et de classification envisagée fonctionne dans la pratique.
   - **Interrogez chaque demande pour une nouvelle étiquette.** Chaque scénario ou cas d’utilisation a-t-il vraiment besoin d’une nouvelle étiquette ou pouvez-vous utiliser ce que vous avez déjà ? Le fait de conserver un nombre minimal d’étiquettes améliore l’adoption.
   - **Utilisez des sous-étiquettes pour les services clés.** Certains services auront des besoins spécifiques qui nécessitent des étiquettes spécifiques. Définissez ces étiquettes en tant que sous-étiquettes d’une étiquette existante et envisagez d’utiliser des stratégies limitées qui sont affectées à des groupes d’utilisateurs plutôt que globalement.
   - **Envisagez des stratégies limitées.** Les stratégies ciblées sur les sous-ensembles d’utilisateurs empêcheront la surcharge des étiquettes. Une stratégie étendue permet d’attribuer des étiquettes ou des sous-étiquettes spécifiques à un rôle ou à un service uniquement aux employés qui travaillent pour ce service spécifique.
   - **Utilisez des noms d’étiquette significatifs.** Essayez de ne pas utiliser de jargon, de normes ou d’acronymes comme noms d’étiquettes. Essayez d’utiliser des noms qui trouvent une écho auprès de l’utilisateur final pour améliorer l’adoption. Au lieu d’utiliser des étiquettes telles que PII, PCI, HIPAA, LBI, MBI et HBI, prenons des noms comme Non-Business, Public, General, Confidential et Highly Confidential.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Créer et déployer des étiquettes de niveau de sensibilité pour des sites, des groupes et des équipes

Lorsque vous créez [des étiquettes](../compliance/sensitivity-labels-teams-groups-sites.md) de niveau de Centre de conformité Microsoft 365, vous pouvez désormais les appliquer à ces conteneurs :

- Microsoft Teams sites
- Microsoft 365 groupes de sécurité (anciennement Office 365 groupes)
- Sites SharePoint

Utilisez les paramètres d’étiquette suivants pour renforcer la protection du contenu de ces conteneurs :

- Confidentialité (publique ou privée) des sites Microsoft 365 connectés à un groupe Teams sites
- Accès des utilisateurs externes
- Accès à partir d’appareils enregistrés

Pour la confidentialité des données, pour empêcher le partage externe pour les conteneurs qui seront utilisés pour stocker du contenu avec des données personnelles sensibles, marquez les fichiers contenant les données comme privés et exigez des appareils gérés.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Créer et déployer des étiquettes de niveau de sensibilité pour le contenu

Les étiquettes de niveau de sensibilité appliquées aux fichiers vous permettent de chiffrer leur contenu, de filigraner le contenu et de définir d’autres contrôles pour le contenu des applications Office, notamment Outlook et Office sur le Web.

Lorsque vous êtes prêt à commencer à protéger les données de votre organisation avec des étiquettes de sensibilité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Pour plus d’informations sur le développement d’une taxonomie de classification, voir le livre blanc sur la classification des données et la taxonomie des [étiquettes de sensibilité.](https://aka.ms/dataclassificationwhitepaper)
2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous souhaitez peut-être qu’un simple en-tête ou pied de page soit appliqué au contenu de niveau de confidentialité inférieur (par exemple, une étiquette « Général », par exemple), tandis que le contenu de niveau de confidentialité plus élevé (tel qu’une étiquette « Confidentiel » ) doit avoir un filigrane et activer le chiffrement.
3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une seule étiquette est réutilisable. Vous la définissez une seule fois, puis vous pouvez l’inclure dans plusieurs stratégies d’étiquette attribuées à différents utilisateurs.

Une fois que vous avez publié des étiquettes de niveau de sensibilité à partir du Centre de conformité Microsoft 365, elles commencent à apparaître dans les applications [Office](../compliance/sensitivity-labels-office-apps.md) pour que les utilisateurs classifient et protègent le contenu tel qu’il est créé ou modifié.

![Flux de déploiement des étiquettes de niveau de Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Pour la confidentialité des données, vous appliquez manuellement une étiquette de confidentialité avec chiffrement et d’autres règles au courrier électronique ou au contenu contenant des informations personnelles sensibles.

> [!NOTE]
> Les étiquettes de niveau de sensibilité avec chiffrement activé pour la messagerie électronique ont des fonctionnalités qui se chevauchent avec OME. Voir comparaison des scénarios de messagerie sécurisée avec [OME et les étiquettes de sensibilité.](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels)

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Étiquetage automatique côté client lorsque les utilisateurs modifient des documents ou rédigent des messages électroniques

Lorsque vous créez une étiquette [](../compliance/apply-sensitivity-label-automatically.md) de sensibilité, vous pouvez affecter automatiquement cette étiquette au contenu, y compris aux e-mails, lorsqu’elle correspond aux conditions que vous spécifiez.

La possibilité d’appliquer automatiquement des étiquettes à du contenu est importante pour les raisons suivantes :

- Vous n’avez pas besoin de former vos utilisateurs pour leur apprendre quand ils doivent utiliser chacune de vos classifications.
- Vous n’avez pas à dépendre des utilisateurs pour classer correctement tout le contenu.
- Vos utilisateurs n’ont plus besoin de connaître vos stratégies. À la place, ils peuvent porter leur attention sur leur travail.

L’étiquetage automatique prend en charge la recommandation d’une étiquette aux utilisateurs, ainsi que l’application automatique d’une étiquette. Dans les deux cas, l’utilisateur décide d’accepter ou de refuser l’étiquette afin de garantir l’étiquetage correct du contenu.

Cet étiquetage côté client présente un délai minimal pour les documents, car l’étiquette peut être appliquée avant même que le document ne soit enregistré. Cependant, toutes les applications clientes ne prennent pas en charge l’étiquetage automatique. Cette fonctionnalité est prise en charge par le client d’étiquetage unifié Azure Information Protection et certaines [versions de Office applications.](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)

Pour obtenir des instructions de configuration, voir Comment configurer l’étiquetage automatique [pour Office applications.](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)

Pour la confidentialité des données, vous appliquez automatiquement des étiquettes de confidentialité pour le contenu contenant des informations personnelles sensibles.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Étiquetage automatique côté service lorsque le contenu est déjà enregistré

Cette méthode est appelée classification automatique avec des étiquettes de confidentialité. Vous pouvez également l’entendre sous le nom d’étiquetage automatique pour les données au repos (pour les documents en SharePoint et OneDrive) et les données en transit (pour les messages électroniques envoyés ou reçus par Exchange). Par Exchange, il n’inclut pas les e-mails dans les boîtes aux lettres au repos.

Étant donné que cette étiquetage est appliqué par le service lui-même plutôt que par l’application utilisateur, vous n’avez pas besoin de vous soucier des applications dont les utilisateurs ont et de quelle version. Par conséquent, cette fonctionnalité est immédiatement disponible dans toute l’organisation et est appropriée pour l’étiquetage à grande échelle. Les stratégies d’étiquetage automatique ne prennent pas en charge l’étiquetage recommandé, car l’utilisateur n’interagit pas avec le processus d’étiquetage. En effet, l’administrateur exécute les stratégies en mode simulation pour s’assurer que le contenu est correctement étiqueté avant d’appliquer réellement l’étiquette.

Pour obtenir des instructions de configuration, voir Comment configurer des stratégies d’étiquetage automatique pour [SharePoint, OneDrive et Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Pour la confidentialité des données dans les sites de préoccupation, appuyez sur les étiquettes de confidentialité pour le chiffrement automatique du contenu contenant des informations personnelles sensibles.

## <a name="data-loss-prevention"></a>Protection contre la perte de données

Vous pouvez utiliser la protection contre la perte de données [(DLP)](../compliance/dlp-learn-about-dlp.md) dans Microsoft 365 pour détecter, avertir et bloquer le partage à risque, par inadvertance ou inapproprié, tel que le partage de données contenant des informations personnelles, à la fois en interne et en externe.

DLP vous permet de :

- Identifier et surveiller les activités de partage à risque.
- Former les utilisateurs à l’aide d’instructions en contexte pour prendre les bonnes décisions.
- Appliquer des stratégies d’utilisation des données sur le contenu sans entraver la productivité.
- Intégrer la classification et l’étiquetage pour détecter et protéger les données lorsqu’elles sont partagées.

### <a name="supported-workloads-for-dlp"></a>Charges de travail prise en charge pour la DLP

Avec une stratégie DLP dans le Centre de conformité Microsoft 365, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans de nombreux emplacements dans Microsoft 365, tels que Exchange Online, SharePoint, OneDrive et Microsoft Teams.

Par exemple, vous pouvez identifier n’importe quel document contenant un numéro de carte de crédit stocké sur n’importe quel site OneDrive ou surveiller uniquement les sites OneDrive de personnes spécifiques.

Vous pouvez également surveiller et protéger les éléments sensibles dans les versions installées localement de Excel, PowerPoint et Word, qui incluent la possibilité d’identifier les éléments sensibles et d’appliquer des stratégies DLP. La DLP assure une surveillance continue lorsque des personnes partagent du contenu à partir de Office applications.

> [!div class="mx-imgBorder"]
> ![Charges de travail prise en charge pour la DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Cette figure illustre un exemple de protection contre la protection contre la protection des données personnelles.

> [!div class="mx-imgBorder"]
> ![Exemple de protection des données personnelles à l’aide de DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

La DLP est utilisée pour identifier un document ou un e-mail contenant un enregistrement d’état d’santé, puis bloque automatiquement l’accès à ce document ou empêche l’envoi du courrier électronique. DLP avertit ensuite le destinataire avec un conseil de stratégie et envoie une alerte à l’utilisateur final et à l’administrateur.

### <a name="planning-for-dlp"></a>Planification de la DLP

Planifiez vos stratégies DLP pour :

- Besoins de votre entreprise.

- Une évaluation basée sur les risques de l’organisation, comme décrit dans l’article sur l’évaluation des risques de confidentialité des données et [l’identification des éléments sensibles.](information-protection-deploy-assess.md)

- Autres mécanismes de protection et de gouvernance des informations en place ou dans la planification de la confidentialité des données.

- Les types d’informations sensibles que vous avez identifiés pour les données personnelles en fonction de votre travail d’évaluation, comme décrit dans l’article d’évaluation des risques de confidentialité des données et d’identification des [éléments sensibles.](information-protection-deploy-assess.md) Les conditions de stratégie DLP peuvent être basées sur des types d’informations sensibles et des étiquettes de rétention.

- Étiquettes de rétention dont vous aurez besoin pour spécifier les conditions DLP. Pour plus [d’informations,](information-protection-deploy-govern.md) voir les informations de gouvernance soumises à la réglementation sur la confidentialité des données dans votre organisation.

- Gestion continue des stratégies DLP, qui exige que quelqu’un de l’organisation fonctionne et régler les stratégies pour les modifications apportées aux types d’informations sensibles, aux étiquettes de rétention, aux réglementations et aux stratégies de conformité.

Bien que les étiquettes de confidentialité ne peuvent pas être utilisées dans les conditions de stratégie DLP, certains scénarios de protection pour empêcher l’accès peuvent être réalisables uniquement avec des étiquettes de confidentialité qui peuvent être appliquées automatiquement en fonction des types d’informations sensibles. Si un étiquetage de niveau de sensibilité robuste est en place, envisagez d’utiliser la protection contre la protection des données pour les raisons qui s’offrent à vous :

  - DLP peut empêcher le partage de fichiers. Les étiquettes de sensibilité peuvent simplement empêcher l’accès.

  - DLP dispose de niveaux de contrôle plus granulaires en termes de règles, de conditions et d’actions.

  - Les stratégies DLP peuvent être appliquées Teams messages de conversation et de canal. Les étiquettes de niveau de sensibilité peuvent uniquement être appliquées aux documents et aux e-mails.


### <a name="dlp-policies"></a>Stratégies de protection contre la perte de données

Les stratégies DLP sont configurées dans le Centre d’administration de conformité Microsoft et spécifient le niveau de protection, le type d’informations sensibles que la stratégie recherche et les charges de travail cibles. Leurs composants de base consistent à identifier la protection et les types de données.

> [!div class="mx-imgBorder"]
> ![Configuration de stratégie DLP dans Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Voici un exemple de stratégie DLP pour la sensibilisation au R GDPR.

![Exemple de stratégie DLP pour la sensibilisation au R GDPR.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

Consultez [cet article pour](../compliance/create-test-tune-dlp-policy.md) plus d’informations sur la création et l’application de stratégies DLP.

### <a name="protection-levels-for-data-privacy"></a>Niveaux de protection de la confidentialité des données

Le tableau suivant répertorie trois configurations d’augmentation de la protection à l’aide de la protection contre la dlp.

![Niveaux de protection de la confidentialité des données avec DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

La première configuration, Sensibilisation, peut être utilisée comme point de départ et niveau de protection minimal pour répondre aux besoins de conformité des réglementations en matière de confidentialité des données.

> [!NOTE]
> À mesure que les niveaux de protection augmentent, la capacité des utilisateurs à partager et à accéder aux informations diminue dans certains cas et peut avoir un impact sur leur productivité ou leur capacité à effectuer des tâches quotidiennes.

Pour aider vos employés à continuer à être productifs dans un environnement plus sécurisé lors de l’augmentation des niveaux de protection, prenez le temps de les former et de les former aux nouvelles stratégies et procédures de sécurité.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Exemple d’utilisation d’étiquettes de sensibilité avec DLP

Les étiquettes de confidentialité peuvent fonctionner avec DLP pour assurer la confidentialité des données dans un environnement hautement réglementé. Voici les principales étapes du déploiement intégré :

1. Les exigences réglementaires et autres exigences commerciales en matière de confidentialité des données sont documentées.
2. Les sources de données cibles, les types et la propriété sont caractérisés par des problèmes de confidentialité des données.
3. Une stratégie globale visant à répondre aux exigences et à protéger et à régir les points d’accès à la confidentialité des données est établie.
4. Un plan d’action par phases pour répondre à la stratégie de contrôle de la confidentialité des données est mis en place.

Une fois ces éléments déterminés, vous pouvez utiliser les types d’informations sensibles, votre taxonomie d’étiquetage de confidentialité et les stratégies DLP ensemble. Cette figure montre un exemple.

> [!div class="mx-imgBorder"]
> ![Exemple d’étiquettes de niveau de sensibilité qui fonctionnent avec DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Voici quelques scénarios de protection des données qui utilisent ensemble des étiquettes de sensibilité et DLP, comme illustré dans la figure.

| Scénario | Processus |
|:-------|:-----|
| A | <ol><li>Les étiquettes de niveau de sensibilité pour le contenu sont publiées par un administrateur pour les utilisateurs et les groupes pour une application manuelle ou automatique au contenu et à la messagerie électronique. </li><li>L’utilisateur A applique les étiquettes manuellement ou automatiquement lors de l’interaction avec le contenu, avec le chiffrement ou d’autres paramètres appliqués. </li><li>L’utilisateur A envoie un e-mail ou un fichier protégé à l’utilisateur B, un utilisateur invité. </li></ol> |
| B | La stratégie DLP publiée par un administrateur à l’utilisateur A empêche l’utilisateur A d’envoyer le courrier électronique et/ou le fichier à l’utilisateur B. |
| C |  L’étiquette de niveau de sensibilité avec le paramètre « propriétaire ne peut pas inviter d’invités » est publiée dans l’utilisateur A, qui Teams une équipe ou SharePoint site. Un autre utilisateur du site tente de manière sélective de partager un fichier avec l’utilisateur B, mais la DLP le bloque. |
| D | L’étiquette de niveau de sensibilité de l’application automatique au contenu du site est publiée sur un ou plusieurs sites, fournissant ainsi une autre couche de protection, ce qui entraîne la mise en place d’un site protégé. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>chiffrement de messages Office 365 nouvelles fonctionnalités (OME)

Les personnes utilisent souvent le courrier électronique pour échanger des éléments sensibles, tels que des informations sur la santé des patients ou des informations sur les clients et les employés. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

Avec [OME,](../compliance/ome.md)vous pouvez envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. OME fonctionne avec Outlook.com, Yahoo!, Gmail et d’autres services de messagerie. OME permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

Pour la confidentialité des données, vous utilisez OME pour protéger les messages internes contenant des éléments sensibles. chiffrement de messages Office 365 est un service en ligne qui repose sur Microsoft Azure Rights Management (Azure RMS) qui fait partie d’Azure Information Protection. Cela inclut les stratégies de chiffrement, d’identité et d’autorisation pour sécuriser votre courrier électronique. Vous pouvez chiffrer des messages à l’aide de modèles de gestion des droits, de l’option Ne pas forwarder et de l’option Chiffrer uniquement.

Vous pouvez également définir des règles de flux de messagerie pour appliquer cette protection. Par exemple, vous pouvez créer une règle qui requiert le chiffrement de tous les messages adressés à un destinataire spécifique, ou qui contient des mots clés spécifiques dans la ligne d’objet, et spécifier que les destinataires ne peuvent pas copier ou imprimer le contenu du message.

En outre, le chiffrement de messages avancé [OME](../compliance/ome-advanced-message-encryption.md) vous aide à respecter les obligations de conformité qui nécessitent des contrôles plus flexibles sur les destinataires externes et leur accès aux e-mails chiffrés. Avec le chiffrement de messages avancé OME dans Microsoft 365, vous pouvez contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui détectent les types d’informations sensibles.

Pour la confidentialité des données, si vous devez partager des messages électroniques avec une partie externe, vous pouvez spécifier une date d’expiration et révoquer des messages. Vous pouvez uniquement révoquer et définir une date d’expiration pour les messages envoyés à des destinataires externes.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Comparaison des scénarios de messagerie sécurisée avec OME et les étiquettes de sensibilité

Les étiquettes OME et de niveau de sensibilité appliquées aux e-mails avec chiffrement se chevauchent, il est donc important de comprendre les scénarios qui peuvent s’appliquer à l’un ou l’autre, comme indiqué dans ce tableau.

| Scénario | Étiquettes de niveau de sensibilité | OME |
|:-------|:-----|:-------|
| Interne + partenaires <br> Communiquer et collaborer en toute sécurité entre les utilisateurs internes et les partenaires de confiance | Recommandation : étiquettes avec une classification et une protection entièrement personnalisées | Oui : chiffrer uniquement ou ne pas forwarder la protection sans classification |
| Parties externes <br> Communiquer et collaborer en toute sécurité avec tous les utilisateurs externes/consommateurs | Oui : destinataires prédefine dans l’étiquette | Recommandation : protection juste-à-temps basée sur les destinataires |
| Internes + partenaires, avec expiration/révocation <br> Contrôler l’accès au courrier et au contenu avec des utilisateurs internes et des partenaires de confiance avec expiration et révocation | Recommandation : protection entièrement personnalisée avec durée d’accès, l’utilisateur peut suivre et révoquer manuellement les fichiers | Non – pas de révocation ou d’expiration pour le courrier interne |
| Parties externes avec expiration/révocation <br> Contrôler l’accès au courrier et au contenu avec des utilisateurs externes/consommateurs avec expiration et révocation | Oui : l’utilisateur peut suivre manuellement les fichiers | Recommandation (E5) : l’administrateur peut révoquer le courrier du Centre de sécurité & conformité |
| Etiquetage automatique <br> L’organisation souhaite protéger automatiquement les messages/pièces jointes avec du contenu sensible spécifique et/ou des destinataires spécifiques | Recommandé (E5) : l’étiquetage automatique dans Exchange clients Outlook, augmente les règles de flux de messagerie et la stratégie DLP | Oui : règles de flux de messagerie et stratégie DLP avec la protection Chiffrer uniquement ou Ne pas forwardr |
||||

Il existe également des différences entre ces deux méthodes dans les expériences utilisateur final et administrateur.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams protection des données hautement sensibles

Pour les organisations qui prévoient de stocker des données personnelles soumises aux réglementations en matière de confidentialité des données dans Teams, voir [Configurer](secure-teams-security-isolation.md)une équipe avec l’isolation de la sécurité, qui fournit des instructions détaillées et des étapes de configuration pour :

- Accès aux identités et appareils
- Création d’une équipe privée
- Verrouillage des autorisations de site d’équipe sous-jacentes
- Une étiquette de niveau de sensibilité basée sur un groupe avec chiffrement