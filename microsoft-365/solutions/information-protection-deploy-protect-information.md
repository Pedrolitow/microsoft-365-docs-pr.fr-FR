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
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Déployez les fonctionnalités de sécurité et de conformité de Microsoft 365 et protégez vos informations personnelles.
ms.openlocfilehash: 3bd59720680802928ad259354f74d2b4829766ef
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986199"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises à la réglementation sur la confidentialité des données

Un certain nombre de contrôles de protection des informations peuvent être utilisés dans votre abonnement pour vous aider à répondre aux besoins et aux réglementations de conformité à la confidentialité des données. Il s’agit notamment du Règlement général sur la protection des données (RGPD), de HIPAA-HITECH (loi États-Unis sur la confidentialité des soins de santé), de la Loi de Californie sur la protection des consommateurs (CCPA) et de la Loi brésilienne sur la protection des données (LGPD).

Ces contrôles se trouvent dans les domaines de solution suivants :

- Étiquettes de confidentialité
- Protection contre la perte de données Microsoft Purview (DLP)
- Chiffrement des messages Microsoft Purview
- Contrôles d’accès Teams et sites

![Services clés pour protéger les informations personnelles soumises à la réglementation sur la confidentialité des données.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Cette solution décrit les fonctionnalités de sécurité et de conformité pour protéger les informations soumises aux réglementations en matière de confidentialité des données. Pour obtenir la liste complète des fonctionnalités de sécurité dans Microsoft 365, consultez la [documentation sur la sécurité de Microsoft 365](../security/index.yml). Pour obtenir la liste complète des fonctionnalités de conformité dans Microsoft 365, consultez [la documentation de Microsoft Purview](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Réglementations sur la confidentialité des données qui ont un impact sur les contrôles de protection des informations

Voici un exemple de liste de réglementations relatives à la confidentialité des données qui peuvent être liées aux contrôles de protection des informations :

- RGPD Article 5(1)(f))
- Article RGPD (32)(1)(a)
- LGPD Article 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Consultez [l’article Évaluer les risques de confidentialité des données et identifier les éléments sensibles](information-protection-deploy-assess.md) pour plus d’informations sur chacun des éléments ci-dessus.

Les réglementations sur la confidentialité des données pour la protection des informations recommandent :

- Protection contre la perte ou l’accès non autorisé, l’utilisation et/ou la transmission.
- Application basée sur les risques des mécanismes de protection.
- Utilisation du chiffrement le cas échéant.

Votre organisation peut également vouloir protéger le contenu Microsoft 365 à d’autres fins, telles que d’autres besoins de conformité ou pour des raisons professionnelles. L’établissement de votre schéma de protection des informations pour la confidentialité des données doit être effectué dans le cadre de la planification, de l’implémentation et de la gestion globales de la protection des informations.

Pour vous aider à prendre en main un schéma de protection des informations dans Microsoft 365, la section suivante inclut une courte liste des fonctionnalités associées et des actions d’amélioration pour Microsoft 365. La liste inclut des fonctionnalités et des actions d’amélioration qui s’appliquent aux réglementations sur la confidentialité des données. Toutefois, la liste n’inclut pas les technologies plus anciennes s’il existe une fonctionnalité plus récente qui remplace en grande partie l’ancienne. Par exemple, la gestion des droits relatifs à l’information (IRM) pour SharePoint et OneDrive n’est pas incluse dans la liste, mais les étiquettes de confidentialité sont incluses.

## <a name="managing-information-protection-in-microsoft-365"></a>Gestion de la protection des informations dans Microsoft 365

Les [solutions de protection des informations](../compliance/information-protection.md) Microsoft incluent un certain nombre de fonctionnalités intégrées dans Microsoft 365, Microsoft Azure et Microsoft Windows. Dans Microsoft 365, les solutions de protection des informations sont les suivantes :

- [Types d’informations sensibles](../compliance/sensitive-information-type-entity-definitions.md) (décrits dans [l’article Évaluer les risques de confidentialité des données et identifier les éléments sensibles)](information-protection-deploy-assess.md)
- [Étiquettes de confidentialité](../compliance/sensitivity-labels.md)
  - Niveau de service/conteneur
  - Côté client/au niveau du contenu
  - Automatisé pour les données au repos dans SharePoint et OneDrive
- Protection contre la perte de données (DLP)
- [Point de terminaison protection contre la perte de données](../compliance/endpoint-dlp-learn-about.md)
- [Office 365 nouvelles fonctionnalités de chiffrement des messages (OME)](../compliance/ome.md) et OME [Advanced Message Encryption](../compliance/ome-advanced-message-encryption.md)

En outre, la protection au niveau du site et de la bibliothèque est un mécanisme important à inclure dans tout schéma de protection.

Pour plus d’informations sur d’autres fonctionnalités de protection des informations en dehors de Microsoft 365, consultez :

- [Microsoft Defender for Cloud Apps](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Protection des informations Windows](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Les étiquettes de confidentialité de Protection des données Microsoft Purview vous permettent de classifier et de protéger les données de votre organisation sans entraver la productivité des utilisateurs et leur capacité à collaborer.

> [!div class="mx-imgBorder"]
> ![Étiquettes de confidentialité dans Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Prérequis pour les étiquettes de confidentialité

Effectuez ces activités avant d’implémenter l’une des fonctionnalités basées sur les étiquettes de sensibilité mises en évidence ci-dessous :

1. Comprenez les éléments suivants :
   - **Besoins de l'entreprise** Établissez les raisons métier de l’application d’étiquettes de confidentialité dans votre entreprise. Par exemple, vos exigences de confidentialité des données pour la protection des informations.
   - **Fonctionnalités d’étiquette de confidentialité.** L’étiquetage de sensibilité peut devenir complexe. Veillez donc à lire la [documentation sur les étiquettes de confidentialité](../compliance/sensitivity-labels.md) avant de commencer.
   - **Éléments clés à retenir** Les étiquettes de confidentialité sont gérées dans le portail de conformité Microsoft Purview, mais les options de ciblage et d’application varient considérablement.
      - Il existe des étiquettes de confidentialité pour les sites, les groupes et Teams au niveau du conteneur (les paramètres ne s’appliquent pas au contenu à l’intérieur du conteneur). Elles sont publiées aux utilisateurs et aux groupes qui les appliquent lorsqu’un site, un groupe ou une équipe est approvisionné.
      - Il existe des étiquettes de confidentialité pour le contenu actif. Ils sont également publiés sur des utilisateurs ou des groupes, qui les appliquent manuellement ou qui sont appliqués automatiquement quand :
        - Le fichier est ouvert/modifié/enregistré, sur le bureau de l’utilisateur ou sur un site SharePoint.
        - Un e-mail est rédigé et envoyé.
      - Il existe des étiquettes de confidentialité pour l’application automatique aux fichiers au repos dans SharePoint et OneDrive, en plus des e-mails en transit via Exchange. Ils sont destinés à tous les sites ou à des sites spécifiques et s’appliquent automatiquement aux fichiers au repos dans ces environnements.

2. Rationaliser l’étiquetage de sensibilité actuel avec des méthodes passées ou alternatives

   - Azure Information Protection

      Le schéma d’étiquetage de sensibilité actuel doit peut-être être rapproché de toute implémentation d’étiquetage [Azure Information Protection](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) existante.
   - Ome

      Si vous envisagez d’utiliser l’étiquetage de confidentialité moderne pour la protection des e-mails et que des méthodes de chiffrement de messagerie existantes comme OME sont en place, elles peuvent coexister, mais vous devez comprendre les scénarios dans lesquels l’une ou l’autre des méthodes doit être appliquée. Consultez [Office 365 nouvelles fonctionnalités de chiffrement des messages (OME),](#office-365-message-encryption-ome-new-capabilities) qui inclut un tableau comparant la protection moderne des types d’étiquettes de confidentialité à la protection basée sur OME.

3. Planifier l’intégration à un schéma de protection de l’information plus large. En plus de la coexistence avec OME, les étiquettes de confidentialité peuvent être utilisées parallèlement à des fonctionnalités telles que Protection contre la perte de données Microsoft Purview (DLP) et Microsoft Defender for Cloud Apps. Consultez [Protéger vos données avec Microsoft Purview](../compliance/information-protection.md) pour atteindre vos objectifs de protection des informations liées à la confidentialité des données.

4. Développez une classification d’étiquette de confidentialité et un schéma de contrôle. Consultez [classification des données et taxonomie des étiquettes de confidentialité](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Directives générales

1. **Définition de schéma.** Avant d’utiliser des fonctionnalités techniques pour appliquer des étiquettes et une protection, travaillez au sein de votre organisation pour définir un schéma de classification. Vous disposez peut-être déjà d’un schéma de classification, ce qui facilite l’ajout de données personnelles.
2. **Commencer.** Commencez par décider du nombre et des noms d’étiquettes à implémenter. Effectuez cette activité sans vous soucier de la technologie à utiliser et de la façon dont les étiquettes seront appliquées. Appliquez ce schéma de manière universelle dans toute votre organisation, y compris les données qui résident localement et dans d’autres services cloud.
3. **Recommandations supplémentaires** Lorsque vous concevez et implémentez des stratégies, des étiquettes et des conditions, tenez compte des recommandations suivantes :

   - **Utilisez le schéma de classification existant (le cas échéant).** De nombreuses organisations utilisent déjà la classification des données sous une certaine forme. Évaluez soigneusement le schéma d’étiquette existant et, si possible, utilisez-le tel qu’il est. L’utilisation d’étiquettes familières qui sont reconnaissables à vos utilisateurs finaux favorisera l’adoption.
   - **Commencez petit.** Il n’existe pratiquement aucune limite au nombre d’étiquettes que vous pouvez créer. Toutefois, un grand nombre d’étiquettes et de sous-étiquettes peut ralentir l’adoption.
   - **Utiliser des scénarios et des cas d’usage.** Identifiez les cas d’usage courants au sein de votre organisation et les scénarios d’utilisation dérivés des réglementations de confidentialité des données auxquelles vous êtes soumis. Vérifiez si l’étiquette et la configuration de classification envisagées fonctionneront dans la pratique.
   - **Interrogez chaque demande d’une nouvelle étiquette.** Chaque scénario ou cas d’usage a-t-il vraiment besoin d’une nouvelle étiquette ou pouvez-vous utiliser ce que vous avez déjà ? Le fait de conserver au minimum le nombre d’étiquettes améliore l’adoption.
   - **Utilisez des sous-étiquettes pour les services clés.** Certains ministères auront des besoins spécifiques qui nécessitent des étiquettes spécifiques. Définissez ces étiquettes en tant que sous-étiquettes pour une étiquette existante et envisagez d’utiliser des stratégies délimitées qui sont affectées à des groupes d’utilisateurs plutôt qu’globalement.
   - **Envisagez des stratégies délimitées.** Les stratégies ciblant des sous-ensembles d’utilisateurs empêchent la surcharge d’étiquette. Une stratégie délimitée permet d’attribuer des étiquettes ou des sous-étiquettes spécifiques au rôle ou au service uniquement aux employés qui travaillent pour ce service spécifique.
   - **Utilisez des noms d’étiquette explicites.** Essayez de ne pas utiliser de jargon, de normes ou d’acronymes comme noms d’étiquette. Essayez d’utiliser des noms qui font écho à l’utilisateur final pour améliorer l’adoption. Au lieu d’utiliser des étiquettes telles que PII, PCI, HIPAA, LBI, MBI et HBI, considérez des noms tels que Non-Entreprise, Public, Général, Confidentiel et Hautement Confidentiel.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Créer et déployer des étiquettes de confidentialité pour les sites, les groupes et les équipes

Lorsque vous créez [des étiquettes de confidentialité](../compliance/sensitivity-labels-teams-groups-sites.md) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, vous pouvez désormais les appliquer aux conteneurs suivants :

- Sites Microsoft Teams
- Groupes Microsoft 365 (anciennement groupes Office 365)
- sites SharePoint

Utilisez les paramètres d’étiquette suivants pour renforcer la protection du contenu de ces conteneurs :

- Confidentialité (publique ou privée) des sites Teams connectés au groupe Microsoft 365
- Accès des utilisateurs externes
- Accès à partir d’appareils enregistrés

Pour la confidentialité des données, afin d’empêcher le partage externe pour les conteneurs qui seront utilisés pour stocker du contenu avec des données personnelles sensibles, marquez les fichiers contenant les données comme privés et nécessitez des appareils gérés.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Créer et déployer des étiquettes de confidentialité pour le contenu

Les étiquettes de confidentialité appliquées aux fichiers vous permettent de chiffrer leur contenu, de filigraner le contenu et de définir d’autres contrôles pour le contenu des applications Office, notamment Outlook et Office sur le Web.

Lorsque vous êtes prêt à commencer à protéger les données de votre organisation avec des étiquettes de confidentialité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Pour plus d’informations sur l’élaboration d’une taxonomie de classification, consultez le [livre blanc sur la taxonomie des étiquettes de classification des données et de sensibilité](https://aka.ms/dataclassificationwhitepaper).
2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous souhaiterez peut-être que le contenu de sensibilité inférieure (par exemple, une étiquette « Général ») ne soit appliqué qu’à un en-tête ou à un pied de page, tandis que le contenu de sensibilité plus élevé (par exemple, une étiquette « Confidentiel ») doit avoir un filigrane et que le chiffrement soit activé.
3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une seule étiquette est réutilisable. Vous le définissez une seule fois, puis vous pouvez l’inclure dans plusieurs stratégies d’étiquette affectées à différents utilisateurs.

Une fois que vous publiez des étiquettes de confidentialité à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, elles commencent à apparaître dans les [applications Office](../compliance/sensitivity-labels-office-apps.md) pour que les utilisateurs classent et protègent le contenu lors de sa création ou de sa modification.

![Flux de déploiement d’étiquettes de confidentialité dans Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Pour la confidentialité des données, vous appliquez manuellement une étiquette de confidentialité avec chiffrement et d’autres règles à l’e-mail ou au contenu contenant des informations personnelles sensibles.

> [!NOTE]
> Les étiquettes de confidentialité avec le chiffrement activé appliqué à la messagerie ont certaines fonctionnalités qui se chevauchent avec OME. Consultez [la comparaison des scénarios de messagerie sécurisée avec OME et les étiquettes de confidentialité](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Étiquetage automatique côté client lorsque les utilisateurs modifient des documents ou composent des e-mails

Lorsque vous créez une étiquette de confidentialité, vous pouvez [automatiquement affecter cette étiquette](../compliance/apply-sensitivity-label-automatically.md) au contenu, y compris à l’e-mail, lorsqu’elle correspond aux conditions que vous spécifiez.

La possibilité d’appliquer automatiquement des étiquettes à du contenu est importante pour les raisons suivantes :

- Vous n’avez pas besoin de former vos utilisateurs pour leur apprendre quand ils doivent utiliser chacune de vos classifications.
- Vous n’avez pas à dépendre des utilisateurs pour classer correctement tout le contenu.
- Vos utilisateurs n’ont plus besoin de connaître vos stratégies. À la place, ils peuvent porter leur attention sur leur travail.

L’étiquetage automatique prend en charge la recommandation d’une étiquette aux utilisateurs, ainsi que l’application automatique d’une étiquette. Dans les deux cas, l’utilisateur décide d’accepter ou de refuser l’étiquette afin de garantir l’étiquetage correct du contenu.

Cet étiquetage côté client présente un délai minimal pour les documents, car l’étiquette peut être appliquée avant même que le document ne soit enregistré. Cependant, toutes les applications clientes ne prennent pas en charge l’étiquetage automatique. Cette fonctionnalité est prise en charge par le client d’étiquetage unifié Azure Information Protection et [certaines versions des applications Office](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Pour obtenir des instructions de configuration, consultez [Comment configurer l’étiquetage automatique pour les applications Office](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Pour la confidentialité des données, vous appliquez automatiquement des étiquettes de confidentialité pour le contenu contenant des informations personnelles sensibles.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Étiquetage automatique côté service lorsque le contenu est déjà enregistré

Cette méthode est appelée classification automatique avec des étiquettes de confidentialité. Vous pouvez également l’entendre sous le nom d’étiquetage automatique pour les données au repos (pour les documents dans SharePoint et OneDrive) et les données en transit (pour les e-mails envoyés ou reçus par Exchange). Pour Exchange, il n’inclut pas les e-mails dans les boîtes aux lettres au repos.

Étant donné que cette étiquetage est appliqué par le service lui-même plutôt que par l’application utilisateur, vous n’avez pas besoin de vous soucier des applications dont disposent les utilisateurs et de leur version. Par conséquent, cette fonctionnalité est immédiatement disponible dans toute l’organisation et est appropriée pour l’étiquetage à grande échelle. Les stratégies d’étiquetage automatique ne prennent pas en charge l’étiquetage recommandé, car l’utilisateur n’interagit pas avec le processus d’étiquetage. En effet, l’administrateur exécute les stratégies en mode simulation pour s’assurer que le contenu est correctement étiqueté avant d’appliquer réellement l’étiquette.

Pour obtenir des instructions de configuration, consultez [Comment configurer des stratégies d’étiquetage automatique pour SharePoint, OneDrive et Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Pour la confidentialité des données dans les sites concernés, envoyez (push) des étiquettes de confidentialité pour le chiffrement automatique du contenu contenant des informations personnelles sensibles.

## <a name="data-loss-prevention"></a>Protection contre la perte de données

Vous pouvez utiliser [la protection contre la perte de données (DLP)](../compliance/dlp-learn-about-dlp.md) dans Microsoft Purview pour détecter, avertir et bloquer le partage risqué, accidentel ou inapproprié, tel que le partage de données contenant des informations personnelles, en interne et en externe.

DLP vous permet d’effectuer les opérations suivantes :

- Identifier et surveiller les activités de partage à risque.
- Formez les utilisateurs avec des conseils contextuels pour prendre les bonnes décisions.
- Appliquer des stratégies d’utilisation des données sur le contenu sans entraver la productivité.
- S’intégrer à la classification et à l’étiquetage pour détecter et protéger les données lorsqu’elles sont partagées.

### <a name="supported-workloads-for-dlp"></a>Charges de travail prises en charge pour DLP

Avec une stratégie DLP dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a>, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans de nombreux emplacements dans Microsoft 365, tels que Exchange Online, SharePoint, OneDrive et Microsoft Teams.

Par exemple, vous pouvez identifier n’importe quel document contenant un numéro de carte de crédit stocké dans n’importe quel site OneDrive, ou vous pouvez surveiller uniquement les sites OneDrive de personnes spécifiques.

Vous pouvez également surveiller et protéger les éléments sensibles dans les versions installées localement d’Excel, PowerPoint et Word, qui incluent la possibilité d’identifier les éléments sensibles et d’appliquer des stratégies DLP. DLP assure une surveillance continue lorsque les utilisateurs partagent du contenu à partir de ces applications Office.

> [!div class="mx-imgBorder"]
> ![Charges de travail prises en charge pour DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Cette figure montre un exemple de protection DLP des données personnelles.

> [!div class="mx-imgBorder"]
> ![Exemple de protection des données personnelles à l’aide de DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP est utilisé pour identifier un document ou un e-mail contenant un enregistrement d’intégrité, puis bloque automatiquement l’accès à ce document ou empêche l’envoi de l’e-mail. DLP avertit ensuite le destinataire avec un conseil de stratégie et envoie une alerte à l’utilisateur final et à l’administrateur.

### <a name="planning-for-dlp"></a>Planification de la protection contre la perte de données

Consultez [la page Planifier la protection contre la perte de données (DLP)](../compliance/dlp-overview-plan-for-dlp.md) pour obtenir des conseils complets sur la planification de votre implémentation DLP.

<!-- Plan your DLP policies for:

- Your business requirements.

- A risk-based assessment of the organization as described in the [assess data privacy risks and identify sensitive items article](information-protection-deploy-assess.md).

- Other information protection and governance mechanisms in place or in planning for data privacy.

- The sensitive information types that you’ve identified for personal data based on your assessment work as described in the [assess data privacy risks and identify sensitive items article](information-protection-deploy-assess.md). DLP policy conditions can be based on both sensitive information types and retention labels.

- The retention labels you'll need to specify DLP conditions. See the [govern information subject to data privacy regulation in your organization](information-protection-deploy-govern.md) article for more information.

- Ongoing DLP policy management, which requires someone in the organization to operate and tune policies for changes in sensitive information types, retention labels, regulations, and compliance policies.

Although sensitivity labels can’t be used in DLP policy conditions, certain protection scenarios to prevent access may be achievable with just sensitivity labels that can be auto-applied based on sensitive information types. If robust sensitivity labeling is in place, consider whether DLP should be used to augment protection because:

  - DLP can prevent sharing of files. Sensitivity labels can just prevent access.

  - DLP has more granular levels of control in terms of rules, conditions, and actions.

  - DLP policies can be applied to Teams chat and channel messages. Sensitivity labels can only be applied to documents and email. -->


### <a name="dlp-policies"></a>Stratégies de protection contre la perte de données

Les stratégies DLP sont configurées dans le portail de conformité Microsoft Purview et spécifient le niveau de protection, les informations recherchées par la stratégie et les charges de travail cibles. Chaque stratégie DLP vous oblige à :

1. Choisissez ce que vous souhaitez surveiller.
1. Choisissez l’emplacement à surveiller.
1. Choisissez les conditions qui doivent être mises en correspondance pour qu’une stratégie soit appliquée à un élément.
1. Choisissez l’action à effectuer lorsque les conditions de stratégie sont remplies.

Pour en savoir plus sur les stratégies DLP et la façon de les concevoir, consultez :

- [En savoir plus sur la prévention des pertes de données](../compliance/dlp-learn-about-dlp.md)
- [Concevoir une stratégie de protection contre la perte de données](../compliance/dlp-policy-design.md)
- [Informations de référence sur la stratégie de protection contre la perte de données](../compliance/dlp-policy-reference.md)


<!--

> [!div class="mx-imgBorder"]
> ![DLP policy configuration in Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Here is an example DLP policy for awareness of GDPR.

![Example DLP policy for awareness of GDPR.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

See [this article](../compliance/create-test-tune-dlp-policy.md) for more information about creating and applying DLP policies.-->

### <a name="protection-levels-for-data-privacy"></a>Niveaux de protection de la confidentialité des données

Le tableau suivant répertorie trois configurations d’augmentation de la protection à l’aide de DLP.

![Niveaux de protection de la confidentialité des données avec DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

La première configuration, La sensibilisation, peut être utilisée comme point de départ et comme niveau minimal de protection pour répondre aux besoins de conformité des réglementations sur la confidentialité des données.

> [!NOTE]
> À mesure que les niveaux de protection augmentent, la capacité des utilisateurs à partager et à accéder aux informations diminue dans certains cas et peut avoir un impact sur leur productivité ou leur capacité à effectuer des tâches quotidiennes.

Pour aider vos employés à continuer à être productifs dans un environnement plus sécurisé lors de l’augmentation des niveaux de protection, prenez le temps de les former et de les former aux nouvelles stratégies et procédures de sécurité.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Exemple d’utilisation d’étiquettes de confidentialité avec DLP

Les étiquettes de confidentialité peuvent fonctionner avec DLP pour fournir la confidentialité des données dans un environnement hautement réglementé. Voici les étapes clés du déploiement intégré :

1. Les exigences réglementaires et autres en matière de confidentialité des données sont documentées.
2. Les sources de données cibles, les types et la propriété sont caractérisés par rapport aux préoccupations de confidentialité des données.
3. Une stratégie globale pour répondre aux exigences et protéger et régir les points d’accès à la confidentialité des données est établie.
4. Un plan d’action par phases pour répondre à la stratégie de contrôle de la confidentialité des données est mis en place.

Une fois ces éléments déterminés, vous pouvez utiliser ensemble des types d’informations sensibles, votre taxonomie d’étiquetage de confidentialité et des stratégies DLP. Cette figure montre un exemple.

> [!div class="mx-imgBorder"]
> ![Exemple d’étiquettes de confidentialité fonctionnant avec DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Voici quelques scénarios de protection des données qui utilisent ensemble des étiquettes DLP et de confidentialité, comme illustré dans la figure.

| Scénario | Processus |
|:-------|:-----|
| A | <ol><li>Les étiquettes de confidentialité pour le contenu sont publiées par un administrateur pour les utilisateurs et les groupes pour une application manuelle ou automatique au contenu et à l’e-mail. </li><li>L’utilisateur A applique les étiquettes manuellement ou automatiquement lors de l’interaction avec le contenu, avec le chiffrement ou d’autres paramètres appliqués. </li><li>L’utilisateur A envoie un e-mail ou un fichier protégé à l’utilisateur B, un utilisateur invité. </li></ol> |
| B | La stratégie DLP publiée par un administrateur sur l’utilisateur A empêche l’utilisateur A d’envoyer l’e-mail et/ou le fichier à l’utilisateur B. |
| C |  L’étiquette de confidentialité avec le paramètre « Le propriétaire ne peut pas inviter d’invités » est publiée sur l’utilisateur A, qui provisionne une équipe Teams ou un site SharePoint. Un autre utilisateur du site tente de partager un fichier avec l’utilisateur B, mais DLP le bloque. |
| D | L’étiquette de confidentialité pour le contenu de l’application automatique sur le site est publiée sur un ou plusieurs sites, ce qui fournit une autre couche de protection, ce qui entraîne un site protégé. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Office 365 nouvelles fonctionnalités de chiffrement des messages (OME)

Personnes souvent utiliser la messagerie électronique pour échanger des éléments sensibles, tels que des informations sur la santé des patients ou des informations sur les clients et les employés. Le chiffrement de messages vous permet de vous assurer que seuls les destinataires prévus peuvent afficher le contenu des courriers.

Avec [OME](../compliance/ome.md), vous pouvez envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. OME fonctionne avec Outlook.com, Yahoo!, Gmail et d’autres services de messagerie. OME permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

Pour la confidentialité des données, vous utilisez OME pour protéger les messages internes contenant des éléments sensibles. Office 365 Message Encryption est un service en ligne basé sur Microsoft Azure Rights Management (Azure RMS) qui fait partie d’Azure Information Protection. Cela inclut les stratégies de chiffrement, d’identité et d’autorisation pour sécuriser votre courrier électronique. Vous pouvez chiffrer les messages à l’aide de modèles de gestion des droits, de l’option Ne pas transférer et de l’option chiffrer uniquement.

Vous pouvez également définir des règles de flux de messagerie pour appliquer cette protection. Par exemple, vous pouvez créer une règle qui nécessite le chiffrement de tous les messages adressés à un destinataire spécifique, ou qui contient des mots clés spécifiques dans la ligne d’objet, et spécifier que les destinataires ne peuvent pas copier ou imprimer le contenu du message.

En outre, OME [Advanced Message Encryption](../compliance/ome-advanced-message-encryption.md) vous permet de respecter les obligations de conformité qui nécessitent des contrôles plus flexibles sur les destinataires externes et leur accès aux e-mails chiffrés. Avec OME Advanced Message Encryption dans Microsoft 365, vous pouvez contrôler les e-mails sensibles partagés en dehors de l’organisation avec des stratégies automatiques qui détectent les types d’informations sensibles.

Pour la confidentialité des données, si vous devez partager des e-mails avec une partie externe, vous pouvez spécifier une date d’expiration et révoquer des messages. Vous pouvez uniquement révoquer et définir une date d’expiration pour les messages envoyés aux destinataires externes.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Comparaison des scénarios de messagerie sécurisée avec OME et les étiquettes de confidentialité

L’OME et les étiquettes de confidentialité appliquées aux e-mails avec chiffrement ont un certain chevauchement. Il est donc important de comprendre les scénarios auxquels l’un ou l’autre des scénarios peut s’appliquer, comme indiqué dans ce tableau.

| Scénario | Étiquettes de confidentialité | Ome |
|:-------|:-----|:-------|
| Interne + partenaires <br> Communiquer et collaborer en toute sécurité entre les utilisateurs internes et les partenaires approuvés | Recommander : étiquettes avec une classification et une protection entièrement personnalisées | Oui : chiffrer uniquement ou ne pas transférer la protection sans classification |
| Parties externes <br> Communiquer et collaborer en toute sécurité avec les utilisateurs externes/consommateurs | Oui : destinataires prédéfinir dans l’étiquette | Recommander une protection juste-à-temps en fonction des destinataires |
| Interne + partenaires, avec expiration/révocation <br> Contrôler l’accès à la messagerie et au contenu avec des utilisateurs internes et des partenaires approuvés avec expiration et révocation | Recommandation : protection entièrement personnalisée avec durée d’accès, l’utilisateur peut suivre et révoquer manuellement des fichiers | Non : pas de révocation ou d’expiration pour le courrier interne |
| Parties externes avec expiration/révocation <br> Contrôler l’accès à la messagerie et au contenu avec les utilisateurs externes/consommateurs avec expiration et révocation | Oui : l’utilisateur peut suivre manuellement les fichiers | Recommandation (E5) : l’administrateur peut révoquer le courrier du Centre de sécurité & conformité |
| Etiquetage automatique <br> L’organisation souhaite protéger automatiquement les courriers/pièces jointes avec du contenu sensible spécifique et/ou des destinataires spécifiques | Recommandation (E5) - Étiquetage automatique dans les clients Exchange et Outlook, augmente les règles de flux de messagerie et la stratégie DLP | Oui : règles de flux de messagerie et stratégie DLP avec chiffrer uniquement ou ne pas transférer la protection |
||||

Il y aura également des différences entre les expériences de l’utilisateur final et de l’administrateur entre ces deux méthodes.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Équipes avec protection pour les données hautement sensibles

Pour les organisations qui envisagent de stocker des données personnelles soumises aux réglementations de confidentialité des données dans Teams, consultez [Configurer une équipe avec isolation de sécurité](secure-teams-security-isolation.md), qui fournit des instructions détaillées et des étapes de configuration pour :

- Accès aux identités et appareils
- Création d’une équipe privée
- Verrouillage des autorisations de site d’équipe sous-jacentes
- Étiquette de confidentialité basée sur un groupe avec chiffrement
