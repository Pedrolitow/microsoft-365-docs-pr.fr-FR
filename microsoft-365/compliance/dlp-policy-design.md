---
title: Concevoir une stratégie de protection contre la perte de données
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
description: Découvrez comment concevoir une stratégie de protection contre la perte de données (DLP)
ms.openlocfilehash: 14e9fbb5efd20ddcf3d0a47da41a0cce89c88cee
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526317"
---
# <a name="design-a-data-loss-prevention-policy"></a>Concevoir une stratégie de protection contre la perte de données

Prendre le temps de concevoir une stratégie avant de l’implémenter vous permet d’obtenir les résultats souhaités plus rapidement et avec moins de problèmes inattendus, que de la créer, puis de la régler par essai et erreur uniquement. La documentation de vos conceptions de stratégies vous aidera également dans les communications, les révisions de stratégies, la résolution des problèmes et l’optimisation.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

Si vous débutez avec Microsoft 365 DLP, il est utile de lire ces articles avant de commencer à concevoir une stratégie :

- [En savoir plus sur la protection contre la](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) perte de données : cet article vous présente les stratégies de protection contre la perte de données et l’implémentation de La protection contre la perte de données par Microsoft
- [Planifiez la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) : vous allez passer en revue cet article :
    - [Identifier les parties prenantes](dlp-overview-plan-for-dlp.md#identify-stakeholders)
    - [Décrire les catégories d’informations sensibles à protéger](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
    - [Définir des objectifs et une stratégie](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [Référence de stratégie de](dlp-policy-reference.md#data-loss-prevention-policy-reference) protection contre la perte de données : cet article présente tous les composants d’une stratégie DLP et la façon dont chacun d’eux influence le comportement d’une stratégie

## <a name="policy-design-overview"></a>Vue d’ensemble de la conception de stratégie

[La conception d’une](#policy-design-process) stratégie consiste principalement à définir clairement les besoins de votre entreprise, à les [documenter](#define-intent-for-the-policy) dans une déclaration d’intention de stratégie, puis à ma mappage de ces besoins à la [configuration de la stratégie](#map-business-needs-to-policy-configuration). Vous utiliserez les décisions que vous avez prises lors de la phase de planification pour informer certaines de vos décisions de conception de stratégie. 

### <a name="define-intent-for-the-policy"></a>Définir l’intention de la stratégie 

Vous devez être en mesure de résumer l’objectif de l’entreprise pour chaque stratégie dont vous avez une seule déclaration. Le développement de cette déclaration pilote les conversations dans votre organisation et, lorsqu’elle est complète, elle lie directement la stratégie à un objectif commercial et fournit une feuille de route pour la conception de la stratégie. Les étapes de [l’article Planifier](dlp-overview-plan-for-dlp.md#overview-of-planning-process) la protection contre la perte de données (DLP) vous aideront à prendre en compte votre déclaration d’intention de stratégie.  

À partir de la vue [d’ensemble de la configuration](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) des stratégies DLP, n’oubliez pas que toutes les stratégies DLP nécessitent que vous :

- Choisir ce que vous souhaitez surveiller
- Choisir l’endroit où vous souhaitez surveiller
- Choisir les conditions qui doivent correspondre pour qu’une stratégie soit appliquée à un élément
- Choisir l’action à prendre lorsque les conditions de stratégie sont remplies 

Par exemple, voici un premier brouillon fictif d’une déclaration d’intention qui fournit des réponses aux quatre questions : 

*« Nous sommes une organisation basée aux États-Unis et nous devons détecter les documents Office qui contiennent des informations sensibles sur les soins de santé couverts par la loi HIPPA qui sont stockées dans OneDrive/SharePoint et se protéger contre le partage de ces informations dans les messages de conversation et de canal Teams et empêcher tout le monde de les partager avec des tiers non autorisés ».* 

Lorsque vous développerez une conception de stratégie, vous modifierez et étendrez probablement l’instruction.

### <a name="map-business-needs-to-policy-configuration"></a>Ma cartographie des besoins de l’entreprise à la configuration de la stratégie

Nous allons décomposer l’exemple d’instruction provisoire et la ma mappage sur des points de configuration de stratégie DLP.

|Statement  |Réponse à la question de configuration et mappage de configuration  |
|---------|---------|
| « Nous sommes une organisation américaine et nous devons détecter les documents Office qui contiennent des informations sensibles sur les soins de santé couverts par hippa...  |- **Ce qu’il** faut surveiller : Office documents, utilisez le modèle [HIPAA (Health Insurance Act)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) des États-Unis </br>- **Conditions** d’une correspondance : (préconfigurée mais modifiable) : l’élément contient le numéro de la SSN et de la Drug Enforcement Agency (DEA) des États-Unis, la classification internationale des maladie (ICD-9-CM), la classification internationale des maladie (ICD-10-CM), le contenu est partagé avec des personnes extérieures à mon organisation.  </br> - dirige les conversations pour clarifier le seuil de déclenchement pour la détection, comme les niveaux de [confiance](sensitive-information-type-learn-about.md#more-on-confidence-levels) et le nombre [d’instances](dlp-policy-reference.md#content-contains) (appelé tolérance de fuite).|
|... qui sont stockés dans OneDrive/SharePoint et se protègent contre le partage de ces informations Teams messages de conversation et de canal... |- **Emplacement à surveiller** : [](dlp-policy-reference.md#locations) portée de l’emplacement en incluant ou en excluant les sites OneDrive et SharePoint et Teams comptes de conversation/canal ou les groupes de distribution. |
|... et empêcher tout le monde de partager ces éléments avec des tiers non autorisés. »  | - **Actions à prendre :** [ajouter restreindre](dlp-policy-reference.md#actions) *l’accès ou chiffrer le contenu à Microsoft 365 emplacements* </br> - dirige la conversation sur les actions à prendre lorsqu’une stratégie est déclenchée, y compris les actions de protection telles que les restrictions de partage, les actions de sensibilisation telles que les notifications et les alertes, ainsi que les actions de l’utilisateur qui autorisent les remplacements d’une action bloquante par l’utilisateur |

Cet exemple ne couvre pas tous les points de configuration d’une stratégie DLP, mais doit être développé. Toutefois, vous devriez penser dans la bonne direction lorsque vous développez vos propres déclarations d’intention de stratégie DLP.

> [!IMPORTANT]
> N’oubliez pas que les emplacements que vous choisissez ont un impact sur l’utilisation des types d’informations sensibles, des étiquettes de sensibilité et des étiquettes de rétention, ainsi que des actions disponibles. Consultez la référence [de stratégie de protection contre la perte de données](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>Processus de conception de stratégie

1. Pour effectuer les étapes suivantes :
    1. [Planifiez la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) : vous allez passer en revue cet article :
        1. [Identifier vos parties prenantes](dlp-overview-plan-for-dlp.md#identify-stakeholders)
        1. [Décrire les catégories d’informations sensibles à protéger](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
        1. [Définir des objectifs et une stratégie](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
        1. [Définir votre plan de déploiement de stratégie](dlp-overview-plan-for-dlp.md#policy-deployment)

1. Familiarisez-vous avec la référence de stratégie de protection contre la perte de données afin de comprendre tous les composants d’une stratégie DLP et la façon dont chacun d’eux influence le comportement d’une stratégie.[](dlp-policy-reference.md#data-loss-prevention-policy-reference)

1. Familiarisez-vous [avec les modèles de stratégie DLP](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

1. Développez votre déclaration d’intention de stratégie avec vos principales parties prenantes. Reportez-vous à l’exemple plus tôt dans cet article.

1. Déterminez comment cette stratégie s’inscrit dans votre stratégie de stratégie DLP globale.

> [!IMPORTANT]
> Les stratégies ne peuvent pas être renommées une fois qu’elles sont créées. Si vous devez renommer une stratégie, vous devez en créer une nouvelle avec le nom souhaité et retirer l’ancienne. Décidez donc de la structure d’attribution de noms que toutes vos stratégies utiliseront maintenant. 

6. Mapz les éléments de votre déclaration d’intention de stratégie sur les options de configuration.

7. Déterminez le modèle de stratégie à partir duquel vous allez commencer, prédéféré ou personnalisé.

8. Allez dans le modèle et assemblez toutes les informations requises avant de créer la stratégie. Il est probable que vous trouverez certains points de configuration qui ne sont pas couverts dans votre déclaration d’intention de stratégie. C'est d'accord. Revenir à vos parties prenantes pour advenir aux exigences relatives aux points de configuration manquants. 

9. Documentez la configuration de tous les paramètres de stratégie et examinez-les avec vos parties prenantes. Vous pouvez ré-utiliser le mappage de votre déclaration d’intention de stratégie aux points de configuration, ce qui est désormais complètement fait.

10. [Créez un brouillon](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) de stratégie et reportez-vous à votre plan [de déploiement de stratégie](dlp-overview-plan-for-dlp.md#policy-deployment) .

<!--## Policy design examples

|Customer business needs description  | approach  |
|---------|---------|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft| - Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.     |- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users       |
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices     |- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage      |


1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally



–   For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**


  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
–   (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

<!--


> [!TIP] The more locations you include ensures broader application of the policy and more consistent coverage. If you include locations that are mostly used for internal collaboration, the responsiveness of collaboration may be impacted.


- whether the protective actions you need are supported throught the associated location or if you need to compromise to extend coverage
    - also usefule for identifying the most restrictive actions available 
    - (we shouldn't mention here that the "content contains" condition is the primary staple for a DLP policy and should be utilized as a starting point for policy creation. The other workload-specific conditions can be ustilized as an extended or granular control of company's DLP policy. Useful for when "too much" data is being restricted and known sensitive data typically falls under certain conditions.)
    - (We can mention here that their quantitative goal such as "protect X% of data across all locations while maintaining x productivity" can be monitored throught alerts or reports. If protection is too high of working against their established goals, they can come back to policy and tweak their conditions/actions)
- Finally, you should have a union of what, hwo and when to be covered which will easily map to generating a live policy via Microsoft DLP. 
- 
5. At this stage you should asses how you should start this policy. ***LINK OUT TO DEPLOYING A POLICY COVERED IN THE PLANNING TOPIC TOO***
    - Test: your company is very large, conservative or the actions established are pretty restrictive
    - Test w/ notifications: same as above, but you get to test out investigation cadence or volume
    - Live: immediately start this policy in your environment. Useful for when data protection is needed immediately, such as a reactive policy creation, or if you're confident in your planning, or if the risk is low (liek audit actions, etc.)
    - keep it off:
-->

<!--## Policy Design Examples

Here are some examples of more detailed policy intent statement to configuration mappings.

*We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information and prevent it from egressing outside of our company’s borders. We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices. We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item. We have a Microsoft 365 E5 subscription and want to protect all locations and first party apps that are available to us because we can’t afford to have any data leaks. If an event occurs or is prevented, we want to alert our compliance admin and educate our end-users where necessary.*

|Statement  |Configuration question answered and configuration mapping  |
|---------|---------|
| We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
| ...and prevent it from egressing outside of our company’s borders... |- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...| - **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
| ...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....| - **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages... |- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups. |
|...and restrict everyone from sharing those items with unauthorized third parties."  | - **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action |

-->


## <a name="see-also"></a>Voir aussi

- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Planifier la protection contre la perte de données (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Référence de stratégie de protection contre la perte de données](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [Référence des conseils de stratégie de prévention contre la perte de données](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)