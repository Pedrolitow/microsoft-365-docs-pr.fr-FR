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
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Vue d’ensemble du processus de planification de la protection contre la perte de données
ms.openlocfilehash: 130675ad15a872ed14041289fb24aeec471014ff
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183535"
---
# <a name="plan-for-data-loss-prevention-dlp"></a>Planifier la protection contre la perte de données (DLP)

Chaque organisation planifie et implémente la protection contre la perte de données (DLP) différemment, car les besoins, les objectifs, les ressources et la situation de chaque organisation sont propres à elles. Toutefois, il existe des éléments communs à toutes les implémentations DLP réussies. Cet article présente les meilleures pratiques utilisées par les organisations dans leur planification DLP.

## <a name="multiple-starting-points"></a>Plusieurs points de départ

De nombreuses organisations choisissent d’implémenter la DLP pour se conformer à diverses réglementations gouvernementales ou industrielles. Par exemple, le Règlement général sur la protection des données (R GDPR) de l’Union européenne, la loi HIPAA (Health Insurance Portability and Accountability Act) ou le CCPA (California Consumer Privacy Act). Ils implémentent également la protection contre la perte de données pour protéger leur propriété intellectuelle. Toutefois, le point de départ et la destination finale dans le parcours DLP varient. 

Les organisations peuvent commencer leur parcours DLP :

- à partir d’un focus de plateforme, comme la volonté de protéger les informations dans Teams messages de conversation et de canal ou sur Windows 10 appareils
- connaître les informations sensibles qu’ils souhaitent hiérarchiser pour la protection, telles que les dossiers de soins de santé, et passer directement à la définition de stratégies pour les protéger ;
- sans savoir quelles sont leurs informations sensibles, où elles se trouvent et qui fait quoi avec elles afin qu’elles commencent par la découverte et la catégorisation et qu’elles prennent une approche plus méthodique
- sans savoir quelles sont leurs informations sensibles, où elles se trouvent ou qui fait quoi avec, mais elles passeront directement à la définition des stratégies et utiliseront ces résultats comme point de départ, puis affinera leurs stratégies à partir de là.
- sachant qu’ils doivent implémenter la pile Microsoft 365 protection des informations complète et ont donc l’intention d’appliquer une approche plus méthodique à long terme

Voici quelques exemples de la façon dont les clients peuvent aborder la DLP et peu importe où vous commencez, Microsoft 365 DLP est suffisamment flexible pour prendre en charge différents types de parcours de protection des informations du début à une stratégie de protection contre la perte de données entièrement mise en œuvre. 

## <a name="overview-of-planning-process"></a>Vue d’ensemble du processus de planification

La [procédure En savoir plus sur la](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) protection contre la perte de données présente les trois différents aspects du processus de planification [DLP.](dlp-learn-about-dlp.md#plan-for-dlp) Nous allons passer en détail ici sur les éléments communs à tous les plans DLP.

### <a name="identify-stakeholders"></a>Identifier les parties prenantes

Lorsqu’elles sont implémentées, les stratégies DLP peuvent être appliquées à de grandes parties de votre organisation. Le secteur de l’entreprise ne peut pas développer seul un plan étendu sans conséquences négatives. Vous devez identifier les parties prenantes qui peuvent :

- décrire les réglementations, lois et normes industrielles soumises à votre organisation
- catégories d’éléments sensibles à protéger ;
- les processus d’entreprise dans
- comportement à risque qui doit être limité ;
- hiérarchiser les données qui doivent être protégées en premier en fonction de la sensibilité des éléments et des risques impliqués
- décrire le processus de révision et de correction des événements de correspondance de stratégie DLP 
 
En général, ces besoins sont généralement de 85 % de protection réglementaire et de conformité et de protection de la propriété intellectuelle à 15 %. Voici quelques suggestions sur les rôles à inclure dans votre processus de planification :

- Responsables de la réglementation et de la conformité
- Responsable des risques
- Responsables juridiques
- Responsables de la sécurité et de la conformité
- Propriétaires d’entreprise pour les éléments de données
- Utilisateurs professionnels
- IT

### <a name="describe-the-categories-of-sensitive-information-to-protect"></a>Décrire les catégories d’informations sensibles à protéger

Les parties prenantes décrivent ensuite les catégories d’informations sensibles à protéger et le processus d’entreprise dans qui elles sont utilisées. Par exemple, Microsoft 365 DLP définit les catégories suivantes :

- Financier 
- Informations médicales et médicales
- Confidentialité
- Personnalisé

Les parties prenantes peuvent identifier les informations sensibles comme « Nous sommes un processeur de données, donc nous devons implémenter des protections de confidentialité sur les informations de la personne concernée et les informations financières ».

 
  <!-- The business process is important as it informs the ‘data at rest’, ‘data in transit’, ‘data in use’ aspect of DLP planning and who should be sharing the items and who should not.-->

### <a name="set-goals-and-strategy"></a>Définir des objectifs et une stratégie

Une fois que vous avez identifié vos parties prenantes et que vous savez quelles informations sensibles doivent être protégées et où elles sont utilisées, les parties prenantes peuvent définir leurs objectifs de protection et le service it peut développer un plan d’implémentation. 


 <!--
### Discovery
 for the locations (DLP workloads) of these types of items.  (mapping DLP locations and data at rest, data in transit, data in use)

### IT can start coding test policies
start small and always in test mode. Note that DLP policies can feed into insider risk.

### Business process owners help with tuning
 false positive/false negative results and fitting DLP into their business processes.

-->

### <a name="set-implementation-plan"></a>Définir le plan d’implémentation

Votre plan d’implémentation doit inclure les suivants :

- Mappage de l’état de départ et de l’état final souhaité, ainsi que les étapes à suivre pour passer de l’un à l’autre
- comment vous allez résoudre la découverte d’éléments sensibles
- planification de stratégie et ordre d’implémenter
- comment traiter les conditions préalables
- planification de la façon dont les stratégies seront d’abord testées avant de passer à l’application
- comment vous allez former vos utilisateurs finaux
- comment tester et régler vos stratégies
- la manière dont vous allez examiner et mettre à jour votre stratégie de protection contre la perte de données en fonction de l’évolution des besoins de l’entreprise en matière de protection réglementaire, juridique, standard ou de propriété intellectuelle ;

#### <a name="map-out-path-from-start-to-desired-end-state"></a>Ma cartographier le chemin d’accès du début à l’état final souhaité

Il est essentiel de documenter la façon dont votre organisation va passer de son état de départ à l’état final souhaité pour communiquer avec vos parties prenantes et définir l’étendue du projet. Voici un ensemble d’étapes couramment utilisées pour déployer la DLP. Vous souhaiterez plus de détails que cela, mais vous pouvez l’utiliser pour cadrer votre chemin d’adoption DLP.

![graphique montrant l’ordre commun pour le déploiement de DLP.](../media/dlp-deployment-planning.png)

#### <a name="sensitive-item-discovery"></a>Découverte d’éléments sensibles

Il existe plusieurs façons de découvrir les éléments sensibles individuels et leur emplacement. Vous avez peut-être déjà déployé des étiquettes de confidentialité ou vous avez peut-être décidé de déployer une stratégie DLP étendue à tous les emplacements qui découvre et audite uniquement les éléments. Pour en savoir plus, [consultez Connaître vos données.](information-protection.md#know-your-data)

#### <a name="policy-planning"></a>Planification des stratégies

Lorsque vous commencez à adopter la DLP, vous pouvez utiliser ces questions pour vous concentrer sur la conception et l’implémentation de votre stratégie.

##### <a name="what-laws-regulations-and-industry-standards-must-your-organization-comply-with"></a>Quelles lois, réglementations et normes industrielles votre organisation doit-elle respecter ?

Étant donné que de nombreuses organisations viennent à la DLP dans le but de se conformer aux réglementations, la réponse à cette question est un point de départ naturel pour la planification de votre implémentation DLP. Mais, en tant qu’implémenteur de l’it, vous n’êtes probablement pas positionné pour y répondre. Votre équipe juridique et les cadres commerciaux doivent y répondre. 
 
**Exemple** Votre organisation est soumise au Royaume-Uni. réglementations financières.


##### <a name="what-sensitive-items-does-your-organization-have-that-must-be-protected-from-leakage"></a>Quels éléments sensibles votre organisation doit-il protéger contre les fuites ?

Une fois que votre organisation sait où elle se trouve en termes de exigences de conformité réglementaire, vous avez une idée des éléments sensibles qui doivent être protégés contre les fuites et de la façon dont vous souhaitez hiérarchiser l’implémentation de la stratégie pour les protéger. Cela vous aidera à choisir les modèles de stratégie DLP les plus appropriés. Microsoft 365 est livré avec des modèles DLP pré-configurés pour les données financières, médicales et médicales, la confidentialité, et vous pouvez créer vos propres modèles à l’aide du modèle personnalisé. Lorsque vous concevez et créez vos stratégies DLP réelles, le fait de connaître la réponse à cette question vous aidera également à choisir le [type d’informations sensibles qui vous est le plus utile.](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)

**Exemple** Pour commencer rapidement, vous choisissez le modèle de stratégie, qui inclut les types d’informations sensibles `U.K. Financial Data` `Credit Card Number` et les types `EU Debit Card Number` `SWIFT Code` d’informations sensibles. 

##### <a name="where-are-the-sensitive-items-and-what-business-processes-are-they-involved-in"></a>Où sont les éléments sensibles et dans quels processus d’entreprise sont-ils impliqués ?

Les éléments qui contiennent des informations sensibles de votre organisation sont utilisés tous les jours dans le cadre de leurs activités. Vous devez savoir où se produisent des instances de ces informations sensibles et dans quels processus d’entreprise elles sont utilisées. Cela vous aidera à choisir les emplacements où appliquer vos stratégies DLP. Microsoft 365 Les stratégies DLP sont appliquées aux emplacements :

- La messagerie électronique Exchange
- Sites SharePoint
- Les comptes OneDrive
- conversation et messages de canal Teams
- Windows 10 Appareils
- Microsoft Cloud App Security
- Référentiels locaux

**Exemple** Les auditeurs internes de votre organisation font le suivi d’un ensemble de numéros de carte de crédit. Ils conservent une feuille de calcul de ces derniers dans un site SharePoint sécurisé. Plusieurs employés font des copies et les enregistrent sur leur site OneDrive Entreprise travail, qui est synchronisé avec Windows 10 appareil. L’un d’eux place une liste de 14 d’entre eux dans un e-mail et tente de l’envoyer aux auditeurs externes pour révision. Vous souhaitez appliquer la stratégie au site SharePoint sécurisé, à tous les auditeurs internes OneDrive Entreprise comptes, à leurs appareils Windows 10 et à Exchange messagerie électronique.

##### <a name="what-is-your-organizations-tolerance-for-leakage"></a>Quelle est la tolérance de votre organisation pour les fuites ?

Différents groupes de votre organisation peuvent avoir différents affichages sur un niveau acceptable de fuite d’éléments sensibles et sur ce qui n’est pas le cas. L’obtention d’une fuite sans fuite peut avoir un coût trop élevé pour l’entreprise.

**Exemple** Le groupe de sécurité de votre organisation, ainsi que l’équipe juridique, estiment qu’il ne doit pas y avoir de partage de numéros de carte de crédit avec des personnes extérieures à l’organisation et qu’ils ne doivent pas être en fuite. Toutefois, dans le cadre d’un examen régulier de l’activité des numéros de carte de crédit, les auditeurs internes doivent partager certains numéros de carte de crédit avec des auditeurs tiers. Si votre stratégie DLP interdit tout partage de numéros de carte de crédit en dehors de l’organisation, il y aura une perturbation importante du processus d’entreprise et un coût supplémentaire pour atténuer la perturbation afin que les auditeurs internes terminent leur suivi. Ce coût supplémentaire est inacceptable pour la direction. Pour résoudre ce problème, une conversation interne doit être nécessaire pour déterminer un niveau acceptable de fuite. Une fois cette stratégie décidée, elle peut fournir des exceptions pour que certaines personnes partagent les informations ou elle peut être appliquée en mode audit uniquement.

#### <a name="planning-for-prerequisites"></a>Planification des conditions préalables

Avant de pouvoir surveiller certains emplacements DLP, il existe des conditions préalables qui doivent être remplies. Consultez les sections **Avant de commencer** :

- [Prise en main du scanneur local de protection contre la perte de données (préversion)](dlp-on-premises-scanner-get-started.md#before-you-begin)
- [Prise en main la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md#before-you-begin)
- [Mise en place de l’extension de conformité Microsoft (prévisualisation)](dlp-chrome-get-started.md#before-you-begin)
- [Utiliser des stratégies de protection contre la perte de données pour les applications cloud non-Microsoft (aperçu)](dlp-use-policies-non-microsoft-cloud-apps.md#before-you-begin)

#### <a name="policy-deployment"></a>Déploiement de stratégie

Lorsque vous créez vos stratégies DLP, vous devez envisager de les déployer progressivement pour évaluer leur impact et tester leur efficacité avant de les appliquer pleinement. Par exemple, vous ne souhaitez pas qu’une nouvelle stratégie DLP bloque involontairement l’accès à des milliers de documents ou qu’elle casse un processus d’entreprise existant.
  
Si vous créez des stratégies DLP susceptibles d’avoir un impact important, nous vous recommandons de suivre l’ordre suivant :
  
1. **Démarrez en mode test sans conseils de stratégie**, puis utilisez les rapports DLP et les rapports d’incident pour évaluer l’impact. Vous pouvez utiliser les rapports DLP pour connaître le nombre, l’emplacement, le type et la gravité des correspondances de stratégie. En fonction des résultats, vous pouvez affiner les stratégies selon vos besoins. En mode test, les stratégies DLP n’auront aucun impact sur la productivité des personnes qui travaillent dans votre organisation. Utilisez également cette étape pour tester votre flux de travail pour la révision des événements DLP et la correction des problèmes.
    
2. **Passer en mode Test** avec les notifications et les Astuces de stratégie pour commencer à enseigner aux utilisateurs vos stratégies de conformité et les préparer aux stratégies qui vont être appliquées. Il est utile d’avoir un lien vers une page de stratégie d’organisation qui fournit plus de détails sur la stratégie dans le conseil de stratégie. À ce stade, vous pouvez également demander aux utilisateurs de signaler les faux positifs afin de pouvoir affiner les stratégies. Passer à cette étape une fois que vous êtes sûr que les résultats de l’application de stratégie correspondent à ce que les parties prenantes avaient à l’esprit. 
    
3. **Démarrez l’application complète des stratégies** afin que les actions dans les règles soient appliquées et le contenu protégé. Continuez de surveiller les rapports DLP et tous les rapports ou notifications d’incident pour vous assurer que les résultats correspondent à ce que vous aviez prévu. 

    ![Options d’utilisation du mode test et d’option de stratégie.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    Vous pouvez désactiver une stratégie DLP à tout moment, ce qui a une incidence sur toutes les règles de la stratégie. Toutefois, chaque règle peut également être désactivée individuellement en basculant son état dans l’éditeur de règles.

    ![Options de la stratégie de la stratégie.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    Vous pouvez également modifier la priorité de plusieurs règles dans une stratégie. Pour ce faire, ouvrez une stratégie pour modification. Dans une ligne de règle, sélectionnez les points de suspension (**...**), puis choisissez une option, comme, par exemple, **Descendre** ou **Mettre à la fin**.

    ![Définissez la priorité de la règle.](../media/dlp-set-rule-priority.png)

#### <a name="end-user-training"></a>Formation des utilisateurs finals

Lorsqu’une stratégie DLP est déclenchée, vous pouvez configurer vos stratégies pour envoyer des notifications par courrier électronique et afficher des conseils de stratégie pour les stratégies [DLP](use-notifications-and-policy-tips.md#send-email-notifications-and-show-policy-tips-for-dlp-policies) aux administrateurs et aux utilisateurs finaux. Bien que vos stratégies soient toujours en mode test et avant qu’elles ne soient définies pour appliquer une action de blocage, les conseils de stratégie sont utiles pour sensibiliser les utilisateurs aux comportements à risque sur les éléments sensibles et former les utilisateurs à éviter ces comportements à l’avenir.  

#### <a name="review-dlp-requirements-and-update-strategy"></a>Examiner les exigences DLP et la stratégie de mise à jour

Les réglementations, les lois et les normes industrielles soumises à votre organisation changeront au fil du temps et vos objectifs d’entreprise pour la protection contre lalp (DLP) changeront au fil du temps. N’oubliez pas d’inclure des examens réguliers de tous ces domaines afin que votre organisation reste en conformité et que votre implémentation DLP continue de répondre aux besoins de votre entreprise.

## <a name="approaches-to-deployment"></a>Approches du déploiement

|Description des besoins commerciaux des clients  | approche  |
|---------|---------|
|**Contoso Bank** se trouve dans un secteur hautement réglementé et dispose de nombreux types différents d’éléments sensibles dans de nombreux emplacements différents. </br> - sait quels types d’informations sensibles sont prioritaires. </br> - doit minimiser les perturbations de l’activité lors du programme de déployé des stratégies. </br> - dispose de ressources informatiques et peut faire appel à des experts pour vous aider à planifier et à concevoir le déploiement </br> - a un contrat de support premier avec Microsoft| - Prenez le temps de comprendre les réglementations qu’ils doivent respecter et la façon dont ils vont se conformer. </br> -Prenez le temps de comprendre la meilleure valeur ensemble de la pile Microsoft 365 protection des informations personnelles </br> - Développer un modèle d’étiquetage de niveau de sensibilité pour les éléments hiérarchisés et appliquer </br> - Impliquer les propriétaires de processus d’entreprise </br>- Stratégies de conception/code, déployer en mode test, former les utilisateurs </br>- répéter|
|**TailSpin Toys** ne sait pas ce qu’ils ont ou où il se trouve, et ont peu ou pas de profondeur de ressources. Ils utilisent Teams, OneDrive Entreprise et Exchange de manière étendue.     |- Commencez par des stratégies simples sur les emplacements hiérarchisés. </br>- Surveiller ce qui est identifié </br>- Appliquer les étiquettes de niveau de sensibilité en conséquence </br>- Affiner les stratégies, former les utilisateurs       |
|**Fabrikam est** un petit démarrage et souhaite protéger sa propriété intellectuelle et doit se déplacer rapidement. Ils sont prêts à dédier des ressources, mais ne peuvent pas se permettre d’engager des experts externes. </br>- Les éléments sensibles sont tous dans Microsoft 365 OneDrive Entreprise/SharePoint </br>- L’adoption de OneDrive Entreprise et SharePoint est lente, les employés/shadow IT utilisent DropBox et Google Drive pour partager/stocker des éléments </br>- Vitesse de travail des employés par rapport à la protection des données </br>- Le client s’est lancé et a acheté les 18 nouveaux appareils Windows 10 employés     |- Tirez parti de la stratégie DLP par défaut dans Teams </br>- Utiliser restreint par défaut pour les éléments de SharePoint </br>- Déployer des stratégies qui empêchent le partage externe </br>- Déployer des stratégies vers des emplacements hiérarchisés </br>- Déployer des stratégies sur Windows 10 périphériques </br>- Bloquer les téléchargements vers le stockage cloud OneDrive Entreprise non-stockage      |

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
