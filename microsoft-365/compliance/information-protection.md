---
title: Microsoft Information Protection dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: Implémentez Microsoft Information Protection (MIP) pour vous permettre de protéger les informations sensibles où qu’elles se trouvent.
ms.openlocfilehash: 5b9484826f0d3a297dae47c7d140d93297473023
ms.sourcegitcommit: 5a1cb7d95070eef47d401a4693cc137a90550a5e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52259272"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>Microsoft Information Protection dans Microsoft 365.

>*[Licences de sécurité et de conformité Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Implémentez Microsoft Information Protection (MIP) pour vous permettre de découvrir, classifier et protéger les informations sensibles où qu’elles se trouvent.

Les fonctionnalités MIP sont incluses dans la Conformité Microsoft 365 et vous donnent les outils nécessaires pour vous permettre de [connaître vos données](#know-your-data), [protéger vos données](#protect-your-data) et [éviter la perte de vos données](#prevent-data-loss).

![Image qui illustre la façon dont MIP vous permet de découvrir, de classifier et de protéger les données sensibles](../media/powered-by-intelligent-platform.png)

:::image type="content" source="../media/data-table1-4638524-new.png" alt-text="Connaître vos données":::

Si vous souhaitez en savoir plus sur la gestion de vos données, consultez l’article [Gouvernance des données Microsoft dans Microsoft 365](manage-Information-governance.md).

## <a name="know-your-data"></a>Connaître vos données

> [!NOTE]
> Si vous souhaitez en savoir plus sur la classification et l’étiquetage des données dans Azure Purview, actuellement en préversion, veuillez consulter la section [Étiqueter automatiquement votre contenu dans Azure Purview](/azure/purview/create-sensitivity-label).
> 
> Pour obtenir les annonces de publication concernant Azure Purview, consultez ces billets de blog : [Microsoft Information Protection et Microsoft Azure Purview : Better Together](https://techcommunity.microsoft.com/t5/microsoft-security-and/microsoft-information-protection-and-microsoft-azure-purview/ba-p/1957481) et [Azure Purview à Ignite 2021 du printemps](https://techcommunity.microsoft.com/t5/azure-purview/azure-purview-at-spring-ignite-2021/ba-p/2175919).

Pour comprendre votre paysage de données, puis identifier les données importantes dans votre environnement hybride, utilisez les fonctionnalités suivantes :

:::image type="content" source="../media/knowyourdata-new.png" alt-text="Connaître vos données"::: 


|**Fonctionnalité**|**Quels problèmes sont résolus ?**|**Prise en main**|**Licences**|
|--|--|--|--|
|[Types d’informations sensibles](sensitive-information-type-entity-definitions.md)| Identifie les données sensibles à l’aide d’expressions régulières intégrées ou personnalisées ou à l’aide d'une fonction, avec des preuves corroborantes comprenant des mots clés, des niveaux de confiance et la proximité. Utilisez les types d’informations sensibles pour identifier des types de données spécifiques dans votre organisation. Utilisez les types d’informations sensibles pré-disponibles pour rechercher des types de données standard, tels que les numéros de passeport. Créez un type d’informations personnalisé pour identifier les informations propres à votre environnement, telles que des numéros de pièces. | [Personnaliser un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md)| |
|[Classifieurs entraînables (préversion)](classifier-learn-about.md)| Classifie les données pour vous, en utilisant l’un des classifieurs intégrés ou entraîne un classifieur avec votre propre contenu | [Prise en main des classifieurs entraînables (préversion)](classifier-get-started-with.md)| |
|[Classification des données](data-classification-overview.md) | Identifie les éléments qui ont une étiquette de confidentialité, une étiquette de rétention ou qui ont été classés comme type d’informations sensibles dans votre organisation ainsi que les actions entreprises par vos utilisateurs concernant ces éléments  | [Prise en main de l’explorateur de contenu](data-classification-content-explorer.md)<br /><br /> [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)| |



## <a name="protect-your-data"></a>Protéger ses données

Pour appliquer des actions de protection flexibles qui incluent le chiffrement, les restrictions d’accès et les marquages visuelles, utilisez les fonctionnalités suivantes :


:::image type="content" source="../media/protectyourdata-4638524-new.png" alt-text="Protéger ses données":::

|**Fonctionnalité**|**Quels problèmes sont résolus ?**|**Prise en main**|**Licences**|
|--|--|--|--|
|[Étiquettes de confidentialité](sensitivity-labels.md)| Une solution unique pour les applications, les services et les appareils qui permet d’étiqueter et de protéger vos données lors de leur déplacement à l’intérieur et à l’extérieur de votre organisation <br /><br />Exemple de scénario : [appliquer et afficher les étiquettes de confidentialité dans Power BI et protéger les données lorsqu’elles sont exportées](/power-bi/admin/service-security-apply-data-sensitivity-labels)|[Prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md) |
|[Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security)| Découvre, étiquette, puis protège les informations sensibles résidant dans les magasins de données situés dans le cloud | [Découvrir, classifier, étiqueter et protéger les données réglementées et sensibles stockées dans le cloud](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner)| Découvre, étiquette et protège les informations sensibles résidant dans des magasins de données locaux. | [Configurer et installer le scanner d’étiquetage unifié Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Explorateur d’activités]()||||


## <a name="transition-from-aip-to-mip"></a>Transition d’AIP vers MIP
L’expérience classique d’administration et le client Azure Information Protection seront supprimés au début de l’année prochaine. Nous vous recommandons de migrer vers Microsoft Information Protection. Cela implique la migration de toutes vos étiquettes et stratégies existantes. 

:::image type="content" source="../media/transition-aip2mip-4638524-new.png" alt-text="Transition d’AIP vers MIP":::

## <a name="additional-capabilities"></a>Fonctionnalités supplémentaires
Microsoft 365 inclut ces fonctionnalités pour protéger les données :

|**Fonctionnalité**|**Quels problèmes sont résolus ?**|**Prise en main**|
|--|--|--|
| Chiffrement de messages Office 365(OME) | Chiffre les e-mails et les documents joints envoyés à tous les utilisateurs sur tous les appareils, pour que seuls les destinataires autorisés puissent lire les informations envoyées par e-mail. <br /><br /> Exemple de scénario : révoquer les e-mails chiffrés avec le Chiffrement avancé des messages | Configurer les nouvelles fonctionnalités de chiffrement de messages |
| Chiffrement à double clé | Dans tous les cas, vous seul pouvez déchiffrer le contenu protégé. Pour respecter les obligations réglementaires, vous devez conserver les clés de chiffrement dans la limite géographique définie | Déployer le chiffrement à double clé |  
| Chiffrement du service avec la clé client | Empêche l’affichage de données par des systèmes ou du personnel non autorisés, puis complète le chiffrement de disque BitLocker dans les centres de données Microsoft. | Configurer la clé client pour Office 365 |
| Gestion des droits relatifs à l’information SharePoint | Protège les listes et les bibliothèques SharePoint. Lorsqu’un utilisateur extrait un document, le fichier téléchargé est protégé pour que seules les personnes autorisées puissent l’afficher et l’utiliser conformément aux stratégies spécifiées | Configurer la Gestion des droits relatifs à l’information (Information Rights Management, IRM) dans le Centre d’administration SharePoint |
| Connecteur de gestion des droits | Offre uniquement une protection pour les déploiements locaux existants qui utilisent Exchange ou SharePoint Server et l’infrastructure de classification de fichiers (FCI) | Étapes de déploiement du connecteur RMS |



## <a name="prevent-data-loss"></a>Éviter les pertes de données

Pour éviter le partage excessif accidentel d’informations sensibles, utilisez les fonctionnalités suivantes :

:::image type="content" source="../media/dlp-4638524-new.png" alt-text="Éviter les pertes de données":::

|**Étape**|**Description**|**Plus d’informations**|
|--|--|--|
|[Concevoir des stratégies DLP](data-loss-prevention-policies.md)| Planifier le mode d’identification des informations (type d’informations sensibles, étiquette, autre) <br /><br /> Planifier où les stratégies seront ciblées (services, clients, applications tierces). <br /><br /> Planifier des conseils de stratégie, autres||
||||




|**Fonctionnalité**|**Quels problèmes sont résolus ?**|**Prise en main**|
|--|--|--|
|[En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)| Permet d’empêcher le partage involontaire d’éléments sensibles. | [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)|
|[Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)| Étend les fonctionnalités DLP aux éléments utilisés et partagés sur les ordinateurs Windows 10. | [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)|
|[En savoir plus sur l’extension de la conformité Microsoft (préversion).](dlp-chrome-learn-about.md) | Étend les fonctionnalités de protection contre la perte de données au navigateur Chrome | [Prise en main de l’extension de conformité Microsoft (préversion)](dlp-chrome-get-started.md)|
|[En savoir plus sur le scanneur local de protection contre la perte de données Microsoft 365 (préversion)](dlp-on-premises-scanner-learn.md)|Étend la surveillance de la protection contre la perte de données des activités sur fichier et des actions de protection pour les partages de fichiers locaux, pour les dossiers locaux et les bibliothèques de documents SharePoint.|[Prise en main du scanner local de protection contre la perte de données Microsoft 365 (préversion)](dlp-on-premises-scanner-get-started.md)|
|[Protéger les informations sensibles dans les messages de conversation et de canal de Microsoft Teams](dlp-microsoft-teams.md) | Étend certaines fonctionnalités de protection contre la perte de données aux messages de canal et aux conversations Teams. | [En savoir plus sur la stratégie de protection par défaut contre la perte de données dans Microsoft Teams (préversion)](dlp-teams-default-policy.md)| 


## <a name="additional-resources"></a>Ressources supplémentaires

De nombreuses organisations utilisent ces fonctionnalités de protection des informations pour se conformer aux réglementations relatives à la confidentialité des données. Pour vous aider, nous avons conçu un flux de travail qui vous guide dans un processus de bout en bout pour planifier et implémenter des fonctionnalités dans Microsoft 365, notamment l’accès sécurisé, la protection contre les menaces, la protection des informations et la gouvernance des données. Pour plus d’informations, consultez [Déployer la protection des informations pour la confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy). 

En outre, pour vous aider à planifier une stratégie intégrée pour l’implémentation des fonctionnalités de protection des informations, téléchargez l'ensemble des illustrations sur les *Fonctionnalités de conformité et de protection des informations Microsoft 365*.  N’hésitez pas à les adapter à votre usage personnel.

| Élément | Description |
|:-----|:------------|
|[![Poster du modèle : fonctionnalités de la conformité et de la protection des informations Microsoft 365](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> [Télécharger au format PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)  \| [Télécharger en tant que Visio](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx) <br/> Japonais : [Télécharger au format PDF](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.pdf)  \| [Télécharger en tant que Visio](https://download.microsoft.com/download/6/f/1/6f1a7d0e-dd8e-442e-b073-8e94327ae4f8/m365-compliance-illustrations.vsdx) <br/> Mise à jour : octobre 2020|Inclus : <ul><li>  Protection des informations et protection contre la perte de données Microsoft</li><li>Stratégies de rétention et étiquettes de rétention </li><li>Obstacles aux informations</li><li>Conformité des communications</li><li>Gestion des risques internes</li><li>Réception de données tierces</li>|

