---
title: Planifier la protection contre la perte de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Vue d’ensemble du processus de planification de la protection contre la perte de données
ms.openlocfilehash: 68e2b3145521433dd8e0f602b8edb571c45ed9df
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953446"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Planifier la protection contre la perte de données (DLP)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Chaque organisation planifie et implémente la protection contre la perte de données (DLP) différemment, car les besoins, les objectifs, les ressources et la situation de chaque organisation lui sont propres. Toutefois, certains éléments sont communs à toutes les implémentations DLP réussies. Cet article présente les meilleures pratiques utilisées par les organisations dans leur planification DLP.

## <a name="multiple-starting-points"></a>Plusieurs points de départ

De nombreuses organisations choisissent d’implémenter DLP pour se conformer à diverses réglementations gouvernementales ou industrielles. Par exemple, le Règlement général sur la protection des données (RGPD) de l’Union européenne, le Health Insurance Portability and Accountability Act (HIPAA) ou le California Consumer Privacy Act (CCPA). Ils implémentent également la protection contre la perte de données pour protéger leur propriété intellectuelle. Mais le lieu de départ et la destination ultime dans le parcours DLP varient. 

Les organisations peuvent commencer leur parcours DLP :

- à partir d’un focus de plateforme, par exemple pour protéger les informations dans Teams messages de conversation et de canal ou sur des appareils Windows 10
- savoir quelles informations sensibles ils veulent hiérarchiser la protection, comme les dossiers de soins de santé, et aller directement à la définition de stratégies pour les protéger
- sans savoir ce qu’est leurs informations sensibles, où elles sont, et qui fait quoi avec elle afin qu’ils commencent par la découverte et la catégorisation et prennent une approche plus méthodique
- sans savoir quelles sont leurs informations sensibles, ni où elles se trouvent, ni qui fait quoi avec, mais ils passeront directement à la définition de stratégies et utiliseront ces résultats comme point de départ, puis affineront leurs politiques à partir de là
- sachant qu’ils doivent implémenter l’intégralité de la pile de Information Protection Microsoft Purview et qu’ils ont donc l’intention d’adopter une approche méthodique à long terme

Ce ne sont que quelques exemples de la façon dont les clients peuvent aborder DLP et peu importe d’où vous commencez, DLP est suffisamment flexible pour prendre en charge différents types de parcours de protection des informations du début à une stratégie de protection contre la perte de données entièrement réalisée. 

## <a name="overview-of-planning-process"></a>Vue d’ensemble du processus de planification

The [Learn about Microsoft Purview Data Loss Prevention](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) introduit les trois aspects différents du processus de [planification DLP](dlp-learn-about-dlp.md#plan-for-dlp). Nous allons examiner plus en détail ici les éléments communs à tous les plans DLP.

### <a name="identify-stakeholders"></a>Identifier les parties prenantes

Une fois implémentées, les stratégies DLP peuvent être appliquées sur de grandes parties de votre organisation. L’informatique ne peut pas développer elle-même un vaste plan sans conséquences négatives. Vous devez identifier les parties prenantes qui peuvent :

- décrire les réglementations, les lois et les normes sectorielles soumises à votre organisation;
- catégories d’éléments sensibles à protéger
- processus métier dans lesquels ils sont utilisés
- comportement à risque qui doit être limité
- hiérarchiser les données qui doivent d’abord être protégées en fonction de la sensibilité des éléments et du risque
- décrire le processus de révision et de correction des événements de correspondance de stratégie DLP 
 
En général, ces besoins ont tendance à être de 85 % de protection réglementaire et de conformité, et de 15 % de protection de la propriété intellectuelle. Voici quelques suggestions sur les rôles à inclure dans votre processus de planification :

- Agents de réglementation et de conformité
- Chef de la direction des risques
- Agents juridiques
- Agents de sécurité et de conformité
- Propriétaires d’entreprise pour les éléments de données
- Utilisateurs professionnels
- Professionnels de l’informatique

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Décrire les catégories d’informations sensibles à protéger

Les parties prenantes décrivent ensuite les catégories d’informations sensibles à protéger et le processus métier dans lequel elles sont utilisées. Par exemple, DLP définit les catégories suivantes :

- Financier 
- Informations médicales et médicales
- Confidentialité
- Personnalisé

Les parties prenantes peuvent identifier les informations sensibles comme « Nous sommes un processeur de données, nous devons donc implémenter des protections de la confidentialité sur les informations de la personne concernée et les informations financières ».

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Définir des objectifs et une stratégie

Une fois que vous avez identifié vos parties prenantes et que vous savez quelles informations sensibles doivent être protégées et où elles sont utilisées, les parties prenantes peuvent définir leurs objectifs de protection et le service informatique peut développer un plan d’implémentation. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Définir le plan d’implémentation

Votre plan d’implémentation doit inclure :

- Mappage de l’état de départ et de l’état de fin souhaité et des étapes à suivre pour passer de l’un à l’autre
- comment traiter la découverte d’éléments sensibles
- la planification de la stratégie et l’ordre dans lequel elles seront implémentées
- comment vous allez répondre aux conditions préalables
- planification de la façon dont les stratégies seront d’abord testées avant de passer à l’application
- comment vous allez entraîner vos utilisateurs finaux
- comment vous allez tester et paramétrer vos stratégies
- comment passer en revue et mettre à jour votre stratégie de protection contre la perte de données en fonction de l’évolution des besoins en matière de réglementation, juridiques, de normes sectorielles ou de protection de la propriété intellectuelle et d’entreprise

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Mapper le chemin du début à l’état final souhaité

Il est essentiel de documenter la façon dont votre organisation va passer de son état de départ à l’état final souhaité pour communiquer avec vos parties prenantes et définir l’étendue du projet. Voici un ensemble d’étapes couramment utilisées pour déployer DLP. Vous aurez besoin de plus de détails, mais vous pouvez l’utiliser pour cadrer votre chemin d’adoption DLP.

![graphique montrant l’ordre commun pour le déploiement de DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Découverte d’éléments sensibles

Il existe plusieurs façons de découvrir les éléments sensibles individuels et leur emplacement. Vous avez peut-être déjà déployé des étiquettes de confidentialité ou vous avez peut-être décidé de déployer une stratégie DLP étendue à tous les emplacements qui détectent et auditent uniquement les éléments. Pour en savoir plus, consultez [Connaître vos données](information-protection.md#know-your-data).

#### <a name="policy-planning"></a>Planification de la stratégie

Lorsque vous commencez votre adoption de DLP, vous pouvez utiliser ces questions pour concentrer vos efforts de conception et d’implémentation de stratégie.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Quelles lois, réglementations et normes sectorielles votre organisation doit-elle respecter ?

Étant donné que de nombreuses organisations viennent à DLP avec l’objectif de conformité réglementaire, répondre à cette question est un point de départ naturel pour la planification de votre implémentation DLP. Toutefois, en tant qu’implémenteur informatique, vous n’êtes probablement pas en mesure d’y répondre. Il doit être répondu par votre équipe juridique et les dirigeants d’entreprise. 
 
**Exemple** Votre organisation est soumise au Royaume-Uni. règlements financiers.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Quels éléments sensibles votre organisation doit-il protéger contre les fuites ?

Une fois que votre organisation sait où elle se situe en termes de besoins de conformité réglementaire, vous aurez une idée des éléments sensibles à protéger contre les fuites et de la façon dont vous souhaitez hiérarchiser l’implémentation de stratégie pour les protéger. Cela vous aidera à choisir les modèles de stratégie DLP les plus appropriés. Microsoft Purview est fourni avec des modèles DLP préconfigurés pour la finance, la santé et la santé, la confidentialité, et vous pouvez créer vos propres modèles à l’aide du modèle personnalisé. Lorsque vous concevez et créez vos stratégies DLP réelles, connaître la réponse à cette question vous aidera également à choisir le [type d’informations sensibles](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types) approprié.

**Exemple** Pour commencer rapidement, vous choisissez le `U.K. Financial Data` modèle de stratégie, qui inclut les types d’informations sensibles, `EU Debit Card Number`et `SWIFT Code` les `Credit Card Number`types d’informations sensibles. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Où sont les éléments sensibles et dans quels processus métier sont-ils impliqués ?

Les éléments qui contiennent des informations sensibles de votre organisation sont utilisés chaque jour dans le cadre de vos activités. Vous devez savoir où des instances de ces informations sensibles peuvent se produire et dans quels processus métier elles sont utilisées. Cela vous aidera à choisir les emplacements appropriés pour appliquer vos stratégies DLP. Les stratégies DLP sont appliquées aux emplacements :

- La messagerie électronique Exchange
- Sites SharePoint
- Les comptes OneDrive
- conversation et messages de canal Teams
- appareils Windows 10
- Microsoft Defender for Cloud Apps
- Référentiels locaux

**Exemple** Les auditeurs internes de votre organisation effectuent le suivi d’un ensemble de numéros de carte de crédit. Ils conservent une feuille de calcul d’eux dans un site SharePoint sécurisé. Plusieurs des employés font des copies et les enregistrent sur leur site OneDrive Entreprise travail, qui est synchronisé avec leur appareil Windows 10. L’un d’eux colle une liste de 14 d’entre eux dans un e-mail et tente de l’envoyer aux auditeurs externes pour examen. Vous souhaitez appliquer la stratégie au site de SharePoint sécurisé, à tous les auditeurs internes OneDrive Entreprise comptes, à leurs appareils Windows 10 et à Exchange courrier électronique.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Quelle est la tolérance de vos organisations pour les fuites ?

Différents groupes de votre organisation peuvent avoir des vues différentes sur le niveau acceptable de fuite d’éléments sensibles et sur ce qui n’est pas le cas. Atteindre la perfection de zéro fuite peut venir à un coût trop élevé pour l’entreprise.

**Exemple** Le groupe de sécurité de votre organisation, ainsi que l’équipe juridique, estiment tous deux qu’il ne devrait y avoir aucun partage de numéros de carte de crédit avec quiconque en dehors de l’organisation et insiste sur aucune fuite. Toutefois, dans le cadre de l’examen régulier de l’activité des numéros de carte de crédit, les vérificateurs internes doivent partager certains numéros de carte de crédit avec des vérificateurs tiers. Si votre stratégie DLP interdit tout partage de numéros de carte de crédit en dehors de l’organisation, il y aura une interruption significative du processus métier et des coûts supplémentaires pour atténuer cette interruption afin que les auditeurs internes terminent leur suivi. Ce coût supplémentaire est inacceptable pour la direction. Pour résoudre ce problème, il doit y avoir une conversation interne pour décider d’un niveau acceptable de fuite. Une fois que la stratégie a été décidée, elle peut fournir des exceptions pour que certaines personnes puissent partager les informations, ou elle peut être appliquée en mode audit uniquement.

#### <a name="planning-for-prerequisites"></a>Planification des prérequis

Avant de pouvoir surveiller certains emplacements DLP, des conditions préalables doivent être remplies. Consultez les sections **Avant de commencer** :

- [Prise en main du scanneur local de protection contre la perte de données (préversion)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md#before-you-begin)
- [Démarrage avec l’extension de conformité Microsoft](dlp-chrome-get-started.md#before-you-begin)
- [Utiliser des stratégies de protection contre la perte de données pour les applications cloud non Microsoft (préversion)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Déploiement de stratégie

Lorsque vous créez vos stratégies DLP, vous devez envisager de les déployer progressivement pour évaluer leur impact et tester leur efficacité avant de les appliquer pleinement. Par exemple, vous ne souhaitez pas qu’une nouvelle stratégie DLP bloque involontairement l’accès à des milliers de documents ou arrête un processus métier existant.
  
Si vous créez des stratégies DLP susceptibles d’avoir un impact important, nous vous recommandons de suivre l’ordre suivant :
  
1. **Démarrez en mode test sans conseils de stratégie**, puis utilisez les rapports DLP et les rapports d’incident pour évaluer l’impact. Vous pouvez utiliser les rapports DLP pour connaître le nombre, l’emplacement, le type et la gravité des correspondances de stratégie. En fonction des résultats, vous pouvez affiner les stratégies en fonction des besoins. En mode test, les stratégies DLP n’auront aucun impact sur la productivité des personnes qui travaillent dans votre organisation. Utilisez également cette étape pour tester votre flux de travail pour la révision des événements DLP et la correction des problèmes.
    
2. **Passez en mode Test avec des notifications et des Astuces** de stratégie afin que vous puissiez commencer à informer les utilisateurs sur vos stratégies de conformité et à les préparer pour les stratégies qui vont être appliquées. Il est utile d’avoir un lien vers une page de stratégie d’organisation qui fournit plus de détails sur la stratégie dans l’info-bulle de stratégie. À ce stade, vous pouvez également demander aux utilisateurs de signaler des faux positifs afin de pouvoir affiner davantage les stratégies. Passez à cette étape une fois que vous êtes sûr que les résultats de l’application de stratégie correspondent à ce qu’ils avaient à l’esprit par les parties prenantes. 
    
3. **Démarrez l’application complète des stratégies** afin que les actions dans les règles soient appliquées et le contenu protégé. Continuez de surveiller les rapports DLP et tous les rapports ou notifications d’incident pour vous assurer que les résultats correspondent à ce que vous aviez prévu. 

    ![Options d’utilisation du mode test et d’activation de la stratégie.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Vous pouvez désactiver une stratégie DLP à tout moment, ce qui a une incidence sur toutes les règles de la stratégie. Toutefois, chaque règle peut également être désactivée individuellement en basculant son état dans l’éditeur de règles.

    ![Options permettant de désactiver une règle dans une stratégie.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Vous pouvez également modifier la priorité de plusieurs règles dans une stratégie. Pour ce faire, ouvrez une stratégie pour modification. Dans une ligne de règle, sélectionnez les points de suspension (**...**), puis choisissez une option, comme, par exemple, **Descendre** ou **Mettre à la fin**.

    ![Définissez la priorité des règles.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Formation des utilisateurs finaux

Quand une stratégie DLP est déclenchée, vous pouvez configurer vos stratégies pour [envoyer des notifications par e-mail et afficher des conseils de stratégie pour les stratégies DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) aux administrateurs et aux utilisateurs finaux. Bien que vos stratégies soient toujours en mode test et avant qu’elles ne soient définies pour appliquer une action de blocage, les conseils de stratégie sont des moyens utiles de sensibiliser les utilisateurs aux comportements à risque sur les éléments sensibles et d’entraîner les utilisateurs à éviter ces comportements à l’avenir.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Passer en revue les exigences DLP et mettre à jour la stratégie

Les réglementations, les lois et les normes sectorielles auxquelles votre organisation est soumise changeront au fil du temps et vos objectifs commerciaux en matière de protection contre la perte de données seront également atteints. Veillez à inclure des révisions régulières de tous ces domaines afin que votre organisation reste en conformité et que votre implémentation DLP continue à répondre aux besoins de votre entreprise.

## <a name="approaches-to-deployment"></a>Approches du déploiement

|Description des besoins de l’entreprise client  | Approche  |
|---------|---------|
|**Contoso Bank** est dans un secteur hautement réglementé et a de nombreux types d’éléments sensibles différents dans de nombreux emplacements différents. </br> - sait quels types d’informations sensibles sont prioritaires. </br> - doit réduire les perturbations de l’activité au fur et à mesure que les stratégies sont déployées. </br> - dispose de ressources informatiques et peut embaucher des experts pour aider à planifier, concevoir le déploiement </br> - a un contrat de support principal avec Microsoft| - Prenez le temps de comprendre les règlements auxquels ils doivent se conformer et comment ils vont se conformer. </br> -Prenez le temps de comprendre la meilleure valeur conjointe de la pile de Information Protection Microsoft Purview </br> - Développer un schéma d’étiquetage de confidentialité pour les éléments hiérarchisés et appliquer </br> - Impliquer les propriétaires de processus métier </br>- Concevoir/coder des stratégies, déployer en mode test, former des utilisateurs </br>- répéter|
|**TailSpin Toys** ne sait pas ce qu’il a ou où il se trouve, et n’a que peu ou pas de profondeur de ressource. Ils utilisent beaucoup Teams, OneDrive Entreprise et Exchange.     |- Commencez par des stratégies simples sur les emplacements hiérarchisés. </br>- Surveiller ce qui est identifié </br>- Appliquer des étiquettes de confidentialité en conséquence </br>- Affiner les stratégies, former les utilisateurs       |
|**Fabrikam** est une petite start-up qui veut protéger sa propriété intellectuelle et doit se déplacer rapidement. Ils sont prêts à consacrer des ressources, mais ne peuvent pas se permettre d’embaucher des experts extérieurs. </br>- Les éléments sensibles sont tous dans Microsoft 365 OneDrive Entreprise/SharePoint </br>- L’adoption de OneDrive Entreprise et de SharePoint est lente, les employés/l’informatique fantôme utilisent DropBox et Google Drive pour partager/stocker des éléments </br>- Les employés apprécient la vitesse de travail par rapport à la discipline de protection des données </br>- Le client a fait des folies et acheté tous les 18 employés de nouveaux appareils Windows 10     |- Tirez parti de la stratégie DLP par défaut dans Teams </br>- Utiliser restreint par paramètre par défaut pour les éléments SharePoint </br>- Déployer des stratégies qui empêchent le partage externe </br>- Déployer des stratégies sur des emplacements hiérarchisés </br>- Déployer des stratégies sur des appareils Windows 10 </br>- Bloquer les chargements vers le stockage cloud non OneDrive Entreprise      |

<!--

## Planning for workloads

### Exchange

### SharePoint

### OneDrive for Business

### Teams

### Windows 10 Devices

### Microsoft Cloud App Security (MCAS)

### On-premises Scanner
-->

## <a name="see-also"></a>Voir aussi
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
