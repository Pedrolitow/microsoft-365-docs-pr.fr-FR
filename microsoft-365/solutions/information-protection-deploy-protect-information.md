---
title: Protéger les informations soumises au règlement de confidentialité des données
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
ms.custom: ''
description: Déployer les fonctionnalités de sécurité et de conformité de Microsoft 365 et protéger vos informations personnelles.
ms.openlocfilehash: 87057d7c823fc9808169efd254300f2b2f5e0487
ms.sourcegitcommit: c76c025fe75cd9c06eccbf9c7fc887b09da36659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "46903894"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Protéger les informations soumises au règlement de confidentialité des données

Un certain nombre de contrôles de protection des informations peuvent être employés dans votre abonnement afin de répondre aux exigences et aux réglementations en matière de confidentialité des données. Il s’agit notamment du règlement général sur la protection des données (RGPD), de la loi HIPAA-Hi (Health Care Privacy Act), de California Consumer Protection Act (CCPA) et du Brésil Data Protection Act (LGPD).

Ces contrôles se situent dans les zones de solution suivantes :

- Étiquettes de confidentialité
- Protection contre la perte de données (DLP)
- Chiffrement des messages Office (OME)
- Contrôles d’accès aux équipes et aux sites

![Services clés pour protéger les informations personnelles soumises au Règlement sur la confidentialité des données](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

>[!Note]
>Cette solution décrit les fonctionnalités de sécurité et de conformité permettant de protéger les informations soumises à la réglementation en matière de confidentialité des données. Pour obtenir la liste complète des fonctionnalités de sécurité dans Microsoft 365, voir [microsoft 365 Security documentation](https://docs.microsoft.com/microsoft-365/security/). Pour obtenir la liste complète des fonctionnalités de conformité dans Microsoft 365, consultez la [documentation de conformité de microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/).
>

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Réglementations en matière de confidentialité des données ayant un impact sur les contrôles de protection des informations

Voici un exemple de liste de réglementations sur la confidentialité des données pouvant être liées aux contrôles de protection des informations :

- RGPD article 5 (1) (f)
- Article RGPD (32) (1) (a)
- Article 46 de la LGPD
- HIPAA-Hi (45 CFR 164.312 (e) (1))
- HIPAA-HI (45 C.F.R. 164.312 (e) (2) (II))

Pour plus d’informations sur chacune des versions ci-dessus, consultez l' [article évaluation des risques de confidentialité des données et identification des éléments sensibles](information-protection-deploy-assess.md) .

Réglementation en matière de confidentialité des données pour la protection des informations :

- Protection contre la perte ou l’accès non autorisé, utilisation et/ou transmission.
- Application basée sur les risques de mécanismes de protection.
- Utilisation du chiffrement, le cas échéant.

Votre organisation peut également souhaiter protéger le contenu Microsoft 365 à d’autres fins, telles que d’autres besoins en matière de conformité ou pour des raisons professionnelles. Établir votre schéma de protection des informations pour la confidentialité des données doit être réalisé dans le cadre de la planification, de l’implémentation et de la gestion de la protection globale de l’information.

Pour vous aider à commencer à utiliser un modèle de protection des informations dans Microsoft 365, la section suivante inclut une courte liste des capacités associées et des actions d’amélioration pour Microsoft 365. La liste inclut des fonctionnalités et des actions d’amélioration applicables à la réglementation en matière de confidentialité des données. Toutefois, la liste n’inclut pas de technologies plus anciennes s’il existe une nouvelle fonctionnalité qui remplace en grande partie l’ancienne. Par exemple, la gestion des droits relatifs à l’information (IRM) pour SharePoint et OneDrive n’est pas incluse dans la liste, mais les étiquettes de confidentialité sont incluses.

## <a name="managing-information-protection-in-microsoft-365"></a>Gestion de la protection des informations dans Microsoft 365

Les [solutions Microsoft information protection](../compliance/protect-information.md) incluent un certain nombre de fonctionnalités intégrées dans Microsoft 365, Microsoft Azure et Microsoft Windows. Dans Microsoft 365, les solutions de protection des informations sont les suivantes :

- [Chiffrement de service avec clé client](../compliance/customer-key-overview.md)
- [Types d’informations sensibles](../compliance/what-the-sensitive-information-types-look-for.md) (décrits dans l' [article évaluation des risques de confidentialité des données et de l’identification des éléments sensibles](information-protection-deploy-assess.md))
- [Étiquettes de confidentialité](../compliance/sensitivity-labels.md) 
  - Service/niveau du conteneur
  - Côté client/niveau de contenu
  - Automatisation des données au repos dans SharePoint et OneDrive
- Protection contre la perte de données (DLP)
- [Microsoft 365 protection contre la perte de données (préversion)](https://docs.microsoft.com/microsoft-365/compliance/endpoint-dlp-learn-about?view=o365-worldwide)
- [Office 365 chiffrement des messages nouvelles fonctionnalités (OME)](../compliance/ome.md) et OMe [Advanced message Encryption](../compliance/ome-advanced-message-encryption.md)

De plus, la protection au niveau du site et de la bibliothèque est un mécanisme important à inclure dans n’importe quel modèle de protection.

Pour plus d’informations sur les autres fonctionnalités de protection des informations en dehors de Microsoft 365, voir :

- [Sécurité des applications Cloud Microsoft (MCAS)](https://docs.microsoft.com/cloud-app-security/)
- [Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection)
- [Gestionnaire de points de terminaison Microsoft](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Protection des informations Windows](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Les étiquettes de sensibilité de Microsoft information protection Framework vous permettent de classer et de protéger les données de votre organisation sans entraver la productivité des utilisateurs et la possibilité de collaborer.

![Étiquettes de confidentialité dans Microsoft 365](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Conditions préalables pour les étiquettes de sensibilité

Effectuez ces activités avant d’implémenter les fonctionnalités de sensibilité basées sur l’étiquette ci-dessous :

1. Comprendre les points suivants :
   - **Besoins de l’entreprise.** Établissez les raisons commerciales pour l’application d’étiquettes de sensibilité dans votre entreprise. Par exemple, vos exigences en matière de confidentialité des données pour la protection des informations.
   - **Fonctionnalités d’étiquette de confidentialité.** L’étiquetage de la sensibilité peut être complexe, donc veillez à lire la [documentation des étiquettes de confidentialité](../compliance/sensitivity-labels.md) avant de commencer.
   - **Principaux points à retenir** Les étiquettes de sensibilité sont gérées dans le centre d’administration de la conformité Microsoft, mais les options de ciblage et d’application varient de manière significative.
      - Il existe des étiquettes de sensibilité pour les sites, les groupes et les équipes au niveau du conteneur (les paramètres ne s’appliquent pas au contenu à l’intérieur du conteneur). Celles-ci sont publiées pour les utilisateurs et les groupes qui les appliquent lorsqu’un site, un groupe ou une équipe est mis en service.
      - Il y a des étiquettes de sensibilité pour le contenu actif. Celles-ci sont également publiées pour les utilisateurs ou les groupes, qui les appliquent manuellement ou qui sont appliquées automatiquement dans les cas suivants :
        - Le fichier est ouvert/modifié/enregistré sur le Bureau de l’utilisateur ou sur un site SharePoint.
        - Un message électronique est rédigé et envoyé.
      - Il existe des étiquettes de sensibilité pour l’application automatique aux fichiers dans SharePoint et OneDrive en plus des courriers électroniques en transit via Exchange. Celles-ci sont destinées à tous les sites ou à des fichiers spécifiques et s’appliquent automatiquement aux fichiers au repos dans ces environnements.

2. Rationalisation des étiquettes de sensibilité actuelle avec des méthodes passées ou alternatives

   - Azure Information Protection

      Le schéma d’étiquetage de la sensibilité actuelle peut devoir être concilié avec toute implémentation d’étiquette [Azure information protection](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) existante.
   - OME

      Si vous envisagez d’utiliser une étiquette de sensibilité moderne pour la protection de la messagerie et des méthodes de chiffrement de courrier électronique existantes comme OME, elles peuvent coexister, mais vous devez comprendre les scénarios dans lesquels l’une ou l’autre doit être appliquée. Reportez-vous à la rubrique [Office 365 message Encryption New Capabilities (OME)](#office-365-message-encryption-ome-new-capabilities), qui inclut un tableau comparant la protection moderne de type étiquette-protection et protection basée sur ome.

3. Planifiez l’intégration dans un schéma de protection des informations plus large. En plus de la coexistence avec OME, les étiquettes de sensibilité actuelle peuvent être utilisées avec des fonctionnalités telles que la protection contre la perte de données (DLP) Microsoft 365 et la sécurité des applications Cloud Microsoft. Consultez les étiquettes de confidentialité [et la sécurité des applications Cloud Microsoft](../compliance/sensitivity-labels.md#sensitivity-labels-and-microsoft-cloud-app-security) pour atteindre vos objectifs en matière de protection des informations relatives à la confidentialité des données.

4. Développez une étiquette de sensibilité et un modèle de contrôle. Voir [classification des données et classification des étiquettes de confidentialité](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Directives générales

1. **Définition de schéma.** Avant d’utiliser les fonctionnalités techniques pour appliquer des étiquettes et la protection, travaillez au sein de votre organisation pour définir un schéma de classification. Vous disposez peut-être déjà d’un schéma de classification, ce qui facilite l’ajout de données personnelles. 
2. **Prise en main.** Commencez par déterminer le nombre et les noms des étiquettes à implémenter. Effectuez cette activité sans vous soucier de la technologie à utiliser et de la façon dont les étiquettes seront appliquées. Appliquez ce schéma universellement au sein de votre organisation, y compris les données qui résident sur site et dans d’autres services Cloud.
3. **Recommandations supplémentaires** Lors de la conception et de la mise en œuvre de stratégies, d’étiquettes et de conditions, prenez en compte les recommandations suivantes :

   - **Utiliser le schéma de classification existant (le cas échéant).** De nombreuses organisations utilisent déjà la classification des données sous certaines forme. Évaluez soigneusement le schéma d’étiquette existant et, si possible, utilisez-le comme c’est le cas. L’utilisation d’étiquettes familières reconnaissables à vos utilisateurs finaux entraînera l’adoption.
   - **Démarrez petit.** Il n’existe quasiment aucune limite au nombre d’étiquettes que vous pouvez créer. Toutefois, un grand nombre d’étiquettes et de sous-étiquettes peuvent ralentir l’adoption.
   - **Utilisez des scénarios et des cas d’utilisation.** Identifiez les cas d’utilisation courants au sein de votre organisation et utilisez des scénarios dérivés des réglementations sur la confidentialité des données auxquelles vous êtes soumis. Vérifiez que la configuration d’étiquette et de classification prévisionnelle fonctionne en pratique.
   - **Question chaque demande pour une nouvelle étiquette.** Chaque scénario ou cas d’utilisation nécessite-t-il une nouvelle étiquette ou pouvez-vous utiliser ce que vous possédez déjà ? Le nombre d’étiquettes à un minimum augmente l’adoption.
   - **Utiliser des sous-étiquettes pour les services clés.** Certains services ont des besoins spécifiques qui nécessitent des étiquettes spécifiques. Définissez ces étiquettes en tant que sous-étiquettes sur une étiquette existante et envisagez d’utiliser des stratégies délimitées qui sont affectées à des groupes d’utilisateurs au lieu d’globalement.
   - **Prendre en compte les stratégies étendues.** Les stratégies destinées aux sous-ensembles d’utilisateurs empêchent la surcharge d’étiquette. Une stratégie étendue permet d’affecter des étiquettes ou des sous-étiquettes propres aux rôles ou aux services uniquement aux employés qui travaillent pour ce service spécifique. 
   - **Utiliser des noms d’étiquettes explicites.** Essayez de ne pas utiliser le jargon, les normes ou les acronymes comme noms d’étiquette. Essayez d’utiliser des noms qui résonnent avec l’utilisateur final pour améliorer l’adoption. Au lieu d’utiliser des étiquettes comme PII, PCI, HIPAA, IFA, MBI et IEA, considérez les noms comme les personnes non professionnelles, publiques, générales, confidentielles et hautement confidentiels.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Créer et déployer des étiquettes de confidentialité pour les sites, les groupes et les équipes

Lorsque vous créez des [étiquettes de confidentialité](../compliance/sensitivity-labels-teams-groups-sites.md) dans le centre de conformité Microsoft 365, vous pouvez les appliquer à ces conteneurs :

- Sites Microsoft teams
- Groupes Microsoft 365 (anciennement groupes Office 365)
- Sites SharePoint

Utilisez les paramètres d’étiquette suivants pour renforcer la protection du contenu de ces conteneurs :

- Confidentialité (publique ou privée) de sites teams connectés à un groupe Microsoft 365
- Accès des utilisateurs externes
- Accès à partir d’appareils enregistrés

Pour la confidentialité des données, pour empêcher le partage externe des conteneurs qui seront utilisés pour le stockage de contenu avec des données personnelles sensibles, marquez les fichiers contenant les données comme privés et exigez des appareils gérés.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Créer et déployer des étiquettes de confidentialité pour le contenu

Les étiquettes de sensibilité appliquées aux fichiers vous permettent de chiffrer leur contenu, de filigraner le contenu et de définir d’autres contrôles pour le contenu des applications Office, y compris Outlook et Office sur le Web.

Lorsque vous êtes prêt à commencer à protéger les données de votre organisation avec des étiquettes de sensibilité :

1. **Créez les étiquettes.** Créez et nommez vos étiquettes de confidentialité conformément à la taxonomie de classification de votre organisation pour différents niveaux de confidentialité de contenu. Pour plus d’informations sur le développement d’une taxonomie de classification, voir le livre blanc sur la [classification des données et la taxonomie](https://aka.ms/dataclassificationwhitepaper)de l’étiquette de sensibilité.
2. **Définissez l’incidence possible de chaque étiquette.** Configurez les paramètres de protection que vous voulez associer à chaque étiquette. Par exemple, vous souhaiterez peut-être que le contenu de la sensibilité inférieure (par exemple, l’étiquette « général ») soit appliqué à un en-tête ou un pied de page, tandis que le contenu à haute sensibilité (par exemple, une étiquette « confidentiel ») doit avoir un filigrane et que le chiffrement est activé.
3. **Publiez les étiquettes.** Après avoir configuré vos étiquettes de confidentialité, publiez-les à l’aide d’une stratégie d’étiquette. Déterminez les utilisateurs et les groupes devant utiliser les étiquettes ainsi que les paramètres de stratégie à utiliser. Une seule étiquette est réutilisable. Vous la définissez une fois et vous pouvez l’inclure dans plusieurs stratégies d’étiquette affectées à différents utilisateurs.

Une fois que vous avez publié les étiquettes de confidentialité dans le centre de conformité Microsoft 365, elles apparaissent dans les [applications Office](../compliance/sensitivity-labels-office-apps.md) pour permettre aux utilisateurs de classer et de protéger le contenu lors de sa création ou de sa modification.

![Flux de déploiement des étiquettes de confidentialité dans Microsoft 365](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Pour la confidentialité des données, vous appliquez manuellement une étiquette de sensibilité avec le chiffrement et d’autres règles pour le courrier électronique ou le contenu contenant des informations personnelles sensibles.

>[!Note]
>Les étiquettes de sensibilité dont le chiffrement est activé pour le courrier électronique ont des fonctionnalités qui se chevauchent avec OME. Consultez la rubrique relative [à la comparaison des scénarios de messagerie avec OME et des étiquettes de sensibilité](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Étiquetage automatique côté client lorsque les utilisateurs modifient des documents ou rédigent des courriers électroniques

Lorsque vous créez une étiquette de critère de diffusion, vous pouvez [attribuer automatiquement cette étiquette](../compliance/apply-sensitivity-label-automatically.md) au contenu, y compris aux messages électroniques lorsqu’il répond aux conditions que vous spécifiez.

La possibilité d’appliquer automatiquement des étiquettes à du contenu est importante pour les raisons suivantes :

- Vous n’avez pas besoin de former vos utilisateurs pour leur apprendre quand ils doivent utiliser chacune de vos classifications.
- Vous n’avez pas à dépendre des utilisateurs pour classer correctement tout le contenu.
- Vos utilisateurs n’ont plus besoin de connaître vos stratégies. À la place, ils peuvent porter leur attention sur leur travail.

L’étiquetage automatique prend en charge la recommandation d’une étiquette pour les utilisateurs, ainsi que l’application automatique d’une étiquette. Dans les deux cas, l’utilisateur décide d’accepter ou de refuser l’étiquette afin de garantir l’étiquetage correct du contenu.

Cet étiquetage côté client présente un délai minimal pour les documents, car l’étiquette peut être appliquée avant même que le document ne soit enregistré. Cependant, toutes les applications clientes ne prennent pas en charge l’étiquetage automatique. Cette fonctionnalité est prise en charge par le client d’étiquetage unifié Azure information protection et [certaines versions des applications Office](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Pour obtenir des instructions de configuration, consultez [la rubrique How to configure auto-Labeling for Office Apps](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Pour la confidentialité des données, vous appliquez automatiquement des étiquettes de confidentialité pour le contenu contenant des informations personnelles sensibles.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Étiquetage automatique du côté service lorsque le contenu est déjà enregistré

Cette méthode est appelée classification automatique avec des étiquettes de confidentialité. Vous pouvez également entendre l’étiquetage automatique des données au repos (pour les documents dans SharePoint et OneDrive) et les données en transit (pour les courriers électroniques envoyés ou reçus par Exchange). Pour Exchange, il n’inclut pas les courriers électroniques dans les boîtes aux lettres au repos.
 
Étant donné que cette étiquette est appliquée par le service lui-même plutôt que par l’application utilisateur, vous n’avez pas à vous soucier des applications dont disposent les utilisateurs et de la version. Par conséquent, cette fonctionnalité est immédiatement disponible dans toute l’organisation et est appropriée pour l’étiquetage à grande échelle. Les stratégies d’étiquetage automatique ne prennent pas en charge l’étiquetage recommandé, car l’utilisateur n’interagit pas avec le processus d’étiquetage. En effet, l’administrateur exécute les stratégies en mode simulation pour s’assurer que le contenu est correctement étiqueté avant d’appliquer réellement l’étiquette.

Pour obtenir des instructions de configuration, reportez-vous [à la rubrique How to configure auto-Labeling Policies for SharePoint, OneDrive et Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Pour la confidentialité des données dans les sites de préoccupation, les étiquettes de sensibilité de diffusion pour le chiffrement automatique du contenu contenant des informations personnelles sensibles.

## <a name="data-loss-prevention"></a>Protection contre la perte de données 

Vous pouvez utiliser la [protection contre la perte de données (DLP)](../compliance/data-loss-prevention-policies.md) dans Microsoft 365 pour détecter, avertir et bloquer le partage risqué, accidentel ou inapproprié, comme le partage de données contenant des informations personnelles, à la fois en interne et en externe.

DLP vous permet d’effectuer les opérations suivantes :

- Identifier et surveiller les activités de partage à risque.
- Sensibilisez les utilisateurs à des conseils de contexte pour prendre les bonnes décisions.
- Appliquer des stratégies d’utilisation des données sur le contenu sans entraver la productivité.
- Intégrez la classification et l’étiquetage pour détecter et protéger les données lorsqu’elles sont partagées.

### <a name="supported-workloads-for-dlp"></a>Charges de travail prises en charge pour DLP

Avec une stratégie DLP dans le centre de conformité Microsoft 365, vous pouvez identifier, surveiller et protéger automatiquement les éléments sensibles dans de nombreux emplacements de Microsoft 365, comme Exchange Online, SharePoint, OneDrive et Microsoft Teams.

Par exemple, vous pouvez identifier tout document contenant un numéro de carte de crédit stocké dans un site OneDrive, ou vous pouvez surveiller uniquement les sites OneDrive de personnes spécifiques.

Vous pouvez également surveiller et protéger des éléments sensibles dans les versions installées localement d’Excel, de PowerPoint et de Word, qui incluent la possibilité d’identifier des éléments sensibles et d’appliquer des stratégies DLP. DLP assure une surveillance continue lorsque des personnes partagent du contenu à partir de ces applications Office.

![Charges de travail prises en charge pour DLP](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Cette figure illustre un exemple de protection DLP contre les données personnelles.

![Exemple de protection des données personnelles à l’aide de DLP](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP est utilisé pour identifier un document ou un e-mail contenant un enregistrement d’intégrité, bloque automatiquement l’accès à ce document ou bloque l’envoi du courrier électronique. DLP informe ensuite le destinataire à l’aide d’un Conseil de stratégie et envoie une alerte à l’utilisateur final et à l’administrateur.

### <a name="planning-for-dlp"></a>Planification de DLP

Planifiez vos stratégies DLP pour : 

- Besoins de votre entreprise.

- Évaluation basée sur les risques de l’organisation, telle que décrite dans l' [article évaluation des risques de confidentialité des données et de l’identification des éléments sensibles](information-protection-deploy-assess.md).

- Autres mécanismes de protection et de gouvernance des informations en place ou à des fins de planification de la confidentialité des données.

- Les types d’informations sensibles que vous avez identifiés pour les données personnelles en fonction de votre travail d’évaluation, comme décrit dans l' [article évaluation des risques de confidentialité des données et de l’identification des éléments sensibles](information-protection-deploy-assess.md). Les conditions de stratégie DLP peuvent être basées sur des types d’informations sensibles et des étiquettes de rétention.

- Les étiquettes de rétention dont vous avez besoin pour spécifier les conditions DLP. Pour plus d’informations, reportez-vous à la rubrique gestion des [informations relatives au Règlement sur la confidentialité des données dans votre organisation](information-protection-deploy-govern.md) .

- Gestion des stratégies DLP en cours, qui nécessite qu’une personne de l’organisation fonctionne et règle les stratégies pour les modifications des types d’informations sensibles, des étiquettes de rétention, des réglementations et des stratégies de conformité.

Bien que les étiquettes de confidentialité ne puissent pas être utilisées dans les conditions de stratégie DLP, certains scénarios de protection pour empêcher l’accès peuvent être réalisables avec des étiquettes de sensibilité qui peuvent être appliquées automatiquement en fonction des types d’informations sensibles. Si une étiquette de sensibilité robuste est mise en place, déterminez si DLP doit être utilisé pour améliorer la protection car :

  - DLP peut empêcher le partage de fichiers. Les étiquettes de sensibilité peuvent simplement empêcher l’accès.

  - DLP a un niveau de contrôle plus granulaire en termes de règles, conditions et actions.

  - Les stratégies DLP peuvent être appliquées à la conversation de teams et aux messages de canal. Les étiquettes de sensibilité ne peuvent être appliquées qu’aux documents et aux messages électroniques.


### <a name="dlp-policies"></a>Stratégies de protection contre la perte de données

Les stratégies DLP sont configurées dans le centre d’administration de la conformité Microsoft et spécifient le niveau de protection, le type d’informations sensibles que la stratégie recherche, ainsi que les charges de travail cibles. Leurs composants de base consistent à identifier la protection et les types de données.

![Configuration de la stratégie DLP dans Microsoft 365](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Voici un exemple de stratégie DLP pour la sensibilisation de RGPD.

![Exemple de stratégie DLP pour la sensibilisation de RGPD](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

Pour plus d’informations sur la création et l’application de stratégies DLP, consultez [cet article](../compliance/create-test-tune-dlp-policy.md) .

### <a name="protection-levels-for-data-privacy"></a>Niveaux de protection pour la confidentialité des données

Le tableau suivant répertorie trois configurations qui améliorent la protection à l’aide de DLP.

![Niveaux de protection de la confidentialité des données avec DLP](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

La première configuration, sensibilisation, peut être utilisée comme point de départ et niveau de protection minimal pour répondre aux besoins de conformité des réglementations en matière de confidentialité des données.

>[!Note]
>À mesure que les niveaux de protection augmentent, la possibilité pour les utilisateurs de partager et d’accéder aux informations diminue dans certains cas et peut avoir un impact sur leur productivité ou leur capacité à effectuer des tâches quotidiennes.
>

Pour aider vos employés à continuer à être productifs dans un environnement plus sécurisé lors de l’augmentation des niveaux de protection, prenez le temps de former et de former les nouvelles stratégies et procédures de sécurité.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Exemple d’utilisation d’étiquettes de sensibilité avec DLP

Les étiquettes de sensibilité peuvent fonctionner avec DLP pour garantir la confidentialité des données dans un environnement hautement réglementé. Voici les étapes clés du déploiement intégré :

1. Les exigences réglementaires et professionnelles en matière de confidentialité des données sont documentées.
2. Les sources de données cibles, les types et la propriété sont caractérisés par rapport aux préoccupations de confidentialité des données.
3. Une stratégie globale visant à répondre aux exigences et à protéger et à régir les zones sensibles de confidentialité des données est établie.
4. Un plan d’action échelonné pour la gestion de la stratégie de contrôle de la confidentialité des données est mis en place.

Une fois que ces éléments sont déterminés, vous pouvez utiliser les types d’informations sensibles, votre taxonomie et les stratégies DLP ensemble. Cette illustration montre un exemple.

![Exemple d’étiquettes de sensibilité fonctionnant avec DLP](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Afficher une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Voici quelques scénarios de protection des données qui utilisent les étiquettes DLP et Sensitivity, comme illustré dans la figure.

| Scénario | Processus |
|:-------|:-----|
| A | <ol><li>Les étiquettes de sensibilité pour le contenu sont publiées par un administrateur sur les utilisateurs et les groupes pour une application manuelle ou automatique au contenu et à la messagerie électronique. </li><li>L’utilisateur A applique les étiquettes manuellement ou automatiquement lors de l’interaction avec le contenu, avec le chiffrement ou d’autres paramètres appliqués. </li><li>L’utilisateur A envoie un message ou un fichier protégé à l’utilisateur B, un utilisateur invité. </li></ol> |
| B | Stratégie DLP publiée par un administrateur pour l’utilisateur A empêche l’utilisateur A d’envoyer le courrier électronique et/ou le fichier à l’utilisateur B. |
| C |  Étiquette de confidentialité avec le paramètre « le propriétaire ne peut pas inviter des invités » est publié à l’utilisateur A, qui met en service une équipe de teams ou un site SharePoint. Un autre utilisateur du site essaie de partager un fichier avec l’utilisateur B, mais DLP le bloque. |
| D | Étiquette de sensibilité pour l’application automatique au contenu de site est publiée sur un ou plusieurs sites, fournissant une autre couche de protection, aboutissant ainsi à un site protégé. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Nouvelles fonctionnalités de chiffrement de messages Office 365 (OME)

Les utilisateurs utilisent souvent le courrier électronique pour échanger des éléments sensibles, tels que des informations médicales sur les patients ou des informations sur les clients et les employés. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu du message.

Avec [OME](../compliance/ome.md), vous pouvez envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. OME fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. OME permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu du message.

Pour garantir la confidentialité des données, vous utilisez OME pour protéger les messages internes contenant des éléments sensibles. Le chiffrement de messages Office 365 est un service en ligne qui repose sur Microsoft Azure Rights Management (Azure RMS) qui fait partie d’Azure information protection. Cela inclut les stratégies de chiffrement, d’identité et d’autorisation pour sécuriser votre courrier électronique. Vous pouvez chiffrer les messages à l’aide des modèles de gestion des droits, de l’option ne pas transférer et de l’option de chiffrement uniquement.

Vous pouvez également définir des règles de flux de messagerie pour appliquer cette protection. Par exemple, vous pouvez créer une règle qui nécessite le chiffrement de tous les messages adressés à un destinataire spécifique, ou qui contient des mots clés spécifiques dans la ligne d’objet, et spécifier que les destinataires ne peuvent pas copier ou imprimer le contenu du message.

De plus, le [chiffrement de messages avancé](../compliance/ome-advanced-message-encryption.md) OME vous permet de respecter des obligations de conformité nécessitant des contrôles plus souples pour les destinataires externes et leur accès à des messages chiffrés. Avec le chiffrement de messages avancé OME dans Microsoft 365, vous pouvez contrôler les e-mails sensibles partagés hors de l’organisation à l’aide de stratégies automatiques qui détectent les types d’informations sensibles. 

Pour la confidentialité des données, si vous avez besoin de partager des courriers électroniques avec une partie externe, vous pouvez spécifier une date d’expiration et révoquer les messages. Vous pouvez uniquement révoquer et définir une date d’expiration pour les messages envoyés à des destinataires externes.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Comparaison des scénarios de messagerie sécurisée et des OME et des étiquettes de confidentialité

Les OME et les étiquettes de sensibilité appliquées au courrier électronique avec chiffrement ont un chevauchement, c’est pourquoi il est important de comprendre quels scénarios peuvent s’appliquer, comme illustré dans ce tableau.

| Scénario | Étiquettes de sensibilité | OME |
|:-------|:-----|:-------|
| Partenaires internes + <br> Communiquer et collaborer en toute sécurité entre les utilisateurs internes et les partenaires approuvés | Recommended – étiquettes avec une protection et une classification entièrement personnalisées | Oui – chiffrer uniquement ou ne pas transférer la protection sans classification |
| Parties externes <br> Communiquer et collaborer en toute sécurité avec des utilisateurs externes/consommateurs | Oui – prédéfinir les destinataires dans l’étiquette | Recommandation : protection juste-à-temps basée sur les destinataires |
| Interne + partenaires, avec expiration/révocation <br> Contrôler l’accès au courrier et au contenu avec les utilisateurs internes et les partenaires approuvés avec l’expiration et la révocation | Recommandation : protection entièrement personnalisée avec une durée d’accès, l’utilisateur peut suivre et révoquer manuellement des fichiers | Non – pas de révocation ou d’expiration pour les messages internes |
| Parties externes avec expiration/révocation <br> Contrôler l’accès des messages et du contenu avec des utilisateurs externes/consommateurs avec l’expiration et la révocation | Oui – l’utilisateur peut effectuer un suivi manuel des fichiers | Recommende (E5) : l’administrateur peut révoquer le courrier de la sécurité & le centre de conformité |
| Etiquetage automatique <br> L’organisation souhaite protéger automatiquement les messages/pièces jointes avec du contenu sensible spécifique et/ou des destinataires spécifiques. | Recommendation (E5)-étiquetage automatique dans les clients Exchange et Outlook, augmentation des règles de flux de messagerie et de la stratégie DLP | Oui-règles de flux de messagerie et stratégie DLP avec chiffrer uniquement ou ne pas transférer la protection |
||||

Il existe également des différences dans les expériences d’utilisateur final et d’administration entre ces deux méthodes.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams avec protection des données hautement sensibles

Pour les organisations qui envisagent de stocker des données personnelles soumises à des réglementations en matière de confidentialité des données dans Teams, consultez [la rubrique Configure a Team with Security isolation](secure-teams-security-isolation.md), qui fournit des instructions détaillées et des étapes de configuration pour les éléments suivants :

- Accès aux identités et appareils
- Création d’une équipe privée
- Verrouillage des autorisations de site d’équipe sous-jacent
- Étiquette de confidentialité basée sur un groupe avec chiffrement
