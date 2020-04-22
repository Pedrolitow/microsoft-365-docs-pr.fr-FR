---
title: Sécurité Microsoft 365 pour les décideurs d’entreprise (BDM)
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.service: o365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: les scénarios de menace et d’attaque les plus courants rencontrés par les organisations pour leurs environnements Microsoft 365 et les actions recommandées pour atténuer ces risques.
ms.openlocfilehash: ed147bd2ac01e2f7a0581ac18542467e40d84ddb
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43638523"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Sécurité Microsoft 365 pour les décideurs d’entreprise (BDM)

Cet article décrit quelques-uns des scénarios de menace et d’attaque les plus courants rencontrés par les organisations pour leurs environnements Microsoft 365, et les actions recommandées pour atténuer ces risques. Bien que Microsoft 365 propose un large éventail de fonctionnalités de sécurité préconfigurées, il nécessite également que vous soyez le client responsable de la sécurisation de vos propres identités, données et périphériques utilisés pour accéder aux services Cloud. Ces conseils ont été développés par Kozeta Beam (Microsoft Cloud Security Architect) et Thiagaraj Sundararajan (consultant senior Microsoft).

Cet article est organisé par ordre de priorité du travail, en commençant par la protection de ces comptes utilisés pour administrer les services et les ressources les plus critiques, comme votre client, votre courrier électronique et SharePoint. Il fournit un moyen méthodique de s’approcher de la sécurité et fonctionne avec le feuille de calcul suivante afin que vous puissiez suivre votre progression avec les parties prenantes et les équipes dans votre organisation : [Microsoft 365 Security for BDM Spreadsheet](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx). 

[![Image miniature de la feuille de calcul recommandations de sécurité Microsoft 365 BDM](../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx)

Microsoft vous fournit l’outil de score sécurisé au sein de votre client pour analyser automatiquement votre position de sécurité en fonction de vos activités régulières, attribuer un score et fournir des recommandations en matière d’amélioration de la sécurité. Avant de prendre les mesures recommandées dans cet article, Notez votre score actuel et vos recommandations. Les actions recommandées dans cet article augmentent votre score. L’objectif est de ne pas atteindre le score maximal, mais de prendre conscience des possibilités de protection de votre environnement d’une manière qui n’influe pas sur la productivité de vos utilisateurs. Consultez la rubrique [Microsoft Secure score](mtp/microsoft-secure-score.md).

Une autre chose avant de commencer. . . Veillez à [activer le journal d’audit](../compliance/search-the-audit-log-in-security-and-compliance.md). Vous aurez besoin de ces données ultérieurement, dans le cas où vous devriez examiner un incident ou une violation. 

## <a name="protect-privileged-accounts"></a>Protéger les comptes privilégiés

Dans un premier temps, nous vous recommandons de veiller à ce que les comptes critiques de l’environnement bénéficient d’une couche supplémentaire de protection car ces comptes disposent d’un accès et des autorisations nécessaires pour gérer et modifier les services critiques et les ressources susceptibles d’avoir un impact négatif sur l’ensemble de l’organisation, si elles sont compromises. La protection des comptes privilégiés est l’une des méthodes les plus efficaces pour se protéger contre un agresseur qui cherche à élever les autorisations d’un compte compromis à un administrateur. 

|Recommandation  |E3 |E5  |
|---------|---------|---------|
|Appliquer l’authentification multifacteur (MFA) pour tous les comptes d’administration.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)| 
|Implement Azure Active Directory (Azure AD) Privileged Identity Management (PIM) pour appliquer un accès privilégié juste-à-temps aux ressources Azure AD et Azure. Vous pouvez également découvrir qui a accès et vérifier l’accès privilégié.|         | ![coche verte](../media/green-check-mark.png)|
|Implémenter la gestion des accès privilégiés pour gérer le contrôle d’accès granulaire sur les tâches d’administration privilégiées dans Office 365. |         | ![coche verte](../media/green-check-mark.png)|
|Configurez et utilisez des stations de travail accès privilégié pour administrer les services. N’utilisez pas les mêmes stations de travail pour naviguer sur Internet et en vérifiant le courrier électronique qui n’est pas lié à votre compte d’administrateur.|  ![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png) | 

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection des comptes privilégiés](../media/m365-security-bdm-illustrations-privileged-accounts.png)

Recommandations supplémentaires :
- Assurez-vous que les comptes qui sont synchronisés à partir de l’organisation locale ne sont pas affectés aux rôles d’administrateur pour les services Cloud. Cela permet d’empêcher un agresseur de tirer parti des comptes locaux pour bénéficier d’un accès administratif aux services Cloud. 
- Vérifiez que les comptes de service ne sont pas affectés de rôles d’administrateur. Ces comptes ne sont souvent pas surveillés et sont définis avec des mots de passe qui n’expirent pas. Commencez par vous assurer que les comptes AADConnect et ADFS ne sont pas des administrateurs globaux par défaut.
- Supprimer des licences de comptes d’administrateur. À moins qu’il existe un cas d’utilisation spécifique pour attribuer des licences à des comptes d’administrateur spécifiques, supprimez les licences de ces comptes. 

## <a name="reduce-the-surface-of-attack"></a>Réduire la surface d’attaque

La zone de sélection suivante réduit la surface d’attaque. Cela peut être réalisé avec un effort et un impact minimes pour vos utilisateurs et services. En réduisant la surface d’attaque, les agresseurs ont moins de moyens de lancer une attaque contre votre organisation.

Voici quelques exemples :
- Désactivez les protocoles POP3, IMAP et SMTP. La plupart des organisations modernes n’utilisent plus ces anciens protocoles. Vous pouvez les désactiver en toute sécurité et autoriser les exceptions uniquement si nécessaire. 
- Réduire et conserver le nombre d’administrateurs globaux dans le client au minimum absolu requis. Cela réduit directement la surface d’exposition pour toutes les applications Cloud. 
- Retirer les serveurs et les applications qui ne sont plus utilisés dans votre environnement. 
- Implémentez un processus de désactivation et de suppression des comptes qui ne sont plus utilisés. 

## <a name="protect-against-known-threats"></a>Se protéger contre les menaces connues

Les menaces connues incluent les programmes malveillants, les comptes compromis et le hameçonnage. Certaines protections contre ces menaces peuvent être mises en œuvre rapidement sans impact direct sur vos utilisateurs, tandis que d’autres nécessitent une planification et une formation utilisateur supplémentaires. 

|Recommandation  |E3  |E5  |
|---------|---------|---------|
|**Configurer l’authentification multifacteur et utiliser des stratégies d’accès conditionnel recommandées, y compris des stratégies de risque de connexion**. Microsoft recommande de tester un ensemble de stratégies qui fonctionnent ensemble pour protéger toutes les applications Cloud, y compris les services Office 365 et Microsoft 365. Voir [configurations d’identité et d’accès aux appareils](../enterprise/microsoft-365-policies-configurations.md). | |![coche verte](../media/green-check-mark.png)|
|**Exigez l’authentification multifacteur pour tous les utilisateurs**. Si vous ne disposez pas de la licence requise pour implémenter les stratégies d’accès conditionnel recommandées, au minimum, nécessite l’authentification multifacteur pour tous les utilisateurs.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Augmentez le niveau de protection contre les programmes malveillants dans les messages**. Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Protégez votre courrier électronique contre les attaques par hameçonnage ciblées**. Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage ATP, partie de la protection avancée contre les menaces d’Office 365, peut vous aider à protéger votre organisation contre les attaques par hameçonnage malveillantes et les attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin d’effectuer cette opération.| |![coche verte](../media/green-check-mark.png)|
|**Protégez-vous contre les attaques par ransomware dans les messages électroniques**. Les ransomware prennent l’accès à vos données en chiffrant les fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite de extort l’argent des victimes en demandant « ransomware », généralement sous la forme de cryptocurrencies comme Bitcoin, dans Exchange pour le retour de l’accès à vos données. Vous pouvez vous protéger contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichiers couramment utilisées pour les ransomware ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Bloquez les connexions à partir des pays avec lesquels vous ne faites pas affaire**. Créez une stratégie d’accès conditionnel Azure AD pour bloquer les connexions en provenance de ces pays, créant ainsi un pare-feu géo pour votre client.| |![coche verte](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre les menaces connues](../media/m365-security-bdm-illustrations-known-threats.png)

## <a name="protect-against-unknown-threats"></a>Se protéger contre les menaces inconnues

Après avoir ajouté des protections supplémentaires à vos comptes privilégiés et protégé contre les attaques connues, attirez votre attention sur la protection contre les menaces inconnues. Les adversaires les plus déterminés et les plus avancés utilisent des méthodes innovantes et inconnues pour attaquer les organisations. Avec la grande télémétrie de Microsoft des données collectées sur les milliards d’appareils, d’applications et de services, nous pouvons effectuer une protection avancée contre les menaces sur Windows, Office 365 et Azure pour éviter les attaques de jour zéro, utiliser des environnements de boîtier de sable et vérifier la validité avant d’autoriser l’accès à votre contenu. 


|Recommandation  |E3  |E5  |
|---------|---------|---------|
|**Configurez Office 365 Advanced Threat Protection (ATP)**:<br>* Pièces jointes fiables ATP<br>* Liens fiables ATP<br>* ATP pour SharePoint, OneDrive et Microsoft teams<br>* Protection contre le hameçonnage de la protection avancée contre les menaces|         |![coche verte](../media/green-check-mark.png) |
|**Configurez les fonctionnalités de protection avancée contre les menaces Microsoft Defender**:<br>* Antivirus Windows Defender <br>* Protection contre les attaques <br> * Réduction de la surface d’attaque <br> * Isolement matériel <br>* Accès contrôlé aux dossiers     |         |![coche verte](../media/green-check-mark.png) |
|**Utilisez Microsoft Cloud App Security** pour découvrir les applications SaaS et commencer à utiliser l’analyse de comportement et la détection des anomalies. |         |![coche verte](../media/green-check-mark.png) |

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre les menaces inconnues](../media/m365-security-bdm-illustrations-unknown-threats.png)

Recommandations supplémentaires :
- Sécuriser les communications de canaux partenaires comme les courriers électroniques à l’aide de TLS.
- Ouvrez la Fédération teams uniquement aux partenaires avec lesquels vous communiquez.
- Ne pas autoriser les domaines d’expéditeurs autorisés, les expéditeurs individuels ou les adresses IP source, car cela permet aux utilisateurs de contourner les vérifications de courrier indésirable et de programmes malveillants (une pratique courante avec les clients est la liste d’autorisation des domaines acceptés ou un certain nombre d’autres domaines où des problèmes de flux de messagerie peuvent avoir été signalés N’ajoutez pas de domaines dans la liste de filtrage des connexions et du courrier indésirable, car cela peut ignorer toutes les vérifications de courrier indésirable. 
- Activer les notifications de courrier indésirable sortant : autorise les notifications de courrier indésirable sortant à une liste de distribution en interne à l’équipe de support technique ou d’administrateur informatique à signaler si des utilisateurs internes envoient des courriers indésirables en externe. Cela peut indiquer que le compte a été compromis.
- Désactiver PowerShell à distance pour tous les utilisateurs : l’utilisation de PowerShell à distance est principalement utilisée par les administrateurs pour accéder aux services à des fins d’administration ou d’accès à l’API par programme. Nous vous recommandons de désactiver cette option pour les utilisateurs non-administrateurs afin d’éviter la reconnaissance, sauf s’ils ont besoin d’accéder à l’entreprise. 
- Bloquez l’accès au portail de gestion Microsoft Azure pour tous les non-administrateurs. Pour ce faire, vous pouvez créer une règle d’accès conditionnel afin de bloquer tous les utilisateurs, à l’exception des administrateurs. 


## <a name="assume-breach"></a>Supposer une violation

Bien que Microsoft prenne toutes les mesures possibles afin de prévenir les menaces et les attaques, nous vous recommandons de toujours fonctionner dans le cadre de l’esprit de violation. Même si un utilisateur malveillant a réussi à gérer l’environnement, nous devons vous assurer qu’il ne parvient pas à exfiltrer les données ou les informations d’identité à partir de l’environnement. Pour cette raison, nous vous recommandons d’activer la protection contre les fuites de données sensibles, telles que les numéros de sécurité sociale, les numéros de carte de crédit, des informations personnelles supplémentaires et d’autres informations confidentielles au niveau organisationnel. 

L’mentalité « présupposez une faille » nécessite l’implémentation d’une stratégie réseau sans approbation, ce qui signifie que les utilisateurs ne sont pas entièrement approuvés, car ils sont internes au réseau. Au lieu de cela, dans le cadre de l’autorisation de ce que les utilisateurs peuvent faire, les ensembles de conditions sont spécifiés et, lorsque ces conditions sont remplies, certains contrôles sont appliqués. Les conditions peuvent inclure l’état d’intégrité de l’appareil, l’accès à l’application, les opérations effectuées et le risque de l’utilisateur. Par exemple, une action d’authentification d’appareil doit toujours déclencher l’authentification MFA afin de s’assurer qu’aucun périphérique rouge n’est ajouté à votre environnement. 

Une stratégie de réseau de confiance zéro exige également que vous sachiez où vos informations sont stockées et appliquer les contrôles appropriés à des fins de classification, de protection et de rétention. Pour protéger efficacement les ressources les plus critiques et sensibles dont vous avez besoin pour identifier d’abord où elles se trouvent et effectuer des inventaires, ce qui peut être difficile. Ensuite, collaborez avec votre organisation pour définir une stratégie de gouvernance. La définition d’un schéma de classification pour une organisation et la configuration de stratégies, d’étiquettes et de conditions nécessitent une planification et une préparation soignées. Il est important de comprendre qu’il ne s’agit pas d’un processus informatique. Veillez à collaborer avec votre équipe juridique et de conformité pour développer un schéma de classification et d’étiquetage approprié pour les données de votre organisation.

Les fonctionnalités de protection des informations de Microsoft 365 peuvent vous aider à découvrir les informations dont vous disposez, où elles sont stockées, et quelles informations nécessitent une protection supplémentaire. La protection des informations est un processus continu, et les fonctionnalités de Microsoft 365 vous permettent de savoir comment les utilisateurs utilisent et distribuent des informations sensibles, où vos informations sont actuellement stockées et où elles circulent. Vous pouvez également consulter la manière dont les utilisateurs traitent les informations qui sont réglementées pour vérifier que les étiquettes et les protections appropriées sont appliquées.


|Recommandation |E3|E5 |
|---------|---------|---------|
|**Examinez et optimisez votre accès conditionnel et les stratégies associées afin de s’aligner sur vos objectifs pour un réseau de confiance zéro**. La protection contre les menaces connues inclut l’implémentation d’un ensemble de [stratégies recommandées](../enterprise/microsoft-365-policies-configurations.md). Examinez votre implémentation de ces stratégies pour vous assurer que vous protégez vos applications et vos données contre les pirates qui ont obtenu l’accès à votre réseau. Notez que la stratégie de protection des applications Intune recommandée pour Windows 10 active la protection des informations Windows (WIP). Les travaux en cours protègent contre les fuites accidentelles des données de votre organisation via des applications et des services, tels que le courrier électronique, les réseaux sociaux et le cloud public. |         |![coche verte](../media/green-check-mark.png)|
|**Désactivez le transfert de courrier électronique externe**. Les pirates qui accèdent à la boîte aux lettres d’un utilisateur peuvent voler votre courrier en définissant la boîte aux lettres pour transférer automatiquement le courrier électronique. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez éviter cela en configurant une règle de flux de messagerie.|![coche verte](../media/green-check-mark.png) |![coche verte](../media/green-check-mark.png)|
|**Désactiver le partage de calendrier externe anonyme**. Par défaut, le partage de calendrier anonyme externe est autorisé. [Désactiver le partage de calendrier](https://docs.microsoft.com/exchange/sharing/sharing-policies/modify-a-sharing-policy) pour réduire les fuites potentielles d’informations sensibles.|![coche verte](../media/green-check-mark.png) |![coche verte](../media/green-check-mark.png)|
|**Configurez les stratégies de protection contre la perte de données pour les données sensibles**. Créez une stratégie de protection contre la perte de &amp; données dans le centre de sécurité conformité pour découvrir et protéger les données sensibles, telles que les numéros de carte de crédit, les numéros de sécurité sociale et les numéros de compte bancaire. Microsoft 365 inclut de nombreux types d’informations sensibles prédéfinis que vous pouvez utiliser dans les stratégies de protection contre la perte de données. Vous pouvez également créer vos propres types d’informations sensibles pour les données sensibles qui sont personnalisées pour votre environnement. |![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Implémenter la classification des données et les stratégies de protection des informations**. Implémentez des étiquettes de confidentialité et utilisez-les pour classer et appliquer une protection aux données sensibles. Vous pouvez également utiliser ces étiquettes dans les stratégies de protection contre la perte de données. Si vous utilisez des étiquettes Azure information protection, nous vous recommandons de ne pas créer de nouvelles étiquettes dans d’autres centres d’administration.|         |![coche verte](../media/green-check-mark.png)|
|**Protégez les données des applications et services tiers à l’aide de la sécurité des applications Cloud**. Configurez les stratégies de sécurité des applications Cloud pour protéger les informations sensibles dans les applications Cloud tierces, telles que Salesforce, Box ou Dropbox. Vous pouvez utiliser des types d’informations sensibles et les étiquettes de sensibilité que vous avez créées dans les stratégies de sécurité des applications Cloud et les appliquer dans vos applications SaaS. <br><br>La sécurité des applications Cloud Microsoft vous permet d’appliquer une large gamme de processus automatisés. Les stratégies peuvent être configurées pour fournir des analyses en continu de conformité, des tâches eDiscovery juridiques, la protection contre le contenu sensible partagé publiquement, et bien plus encore. La sécurité des applications Cloud peut surveiller tout type de fichier basé sur plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). |         |![coche verte](../media/green-check-mark.png)|
|**Utilisez [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) pour identifier si les utilisateurs stockent des informations sensibles sur leurs appareils Windows**. |         |![coche verte](../media/green-check-mark.png)|
|**Utilisez le [scanneur AIP](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner) pour identifier et classer les informations sur les différents serveurs et partages de fichiers**. Utilisez l’outil de création de rapports AIP pour afficher les résultats et prendre les mesures appropriées.|         |![coche verte](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre la violation](../media/m365-security-bdm-illustrations-assume-breach.png)

## <a name="continuous-monitoring-and-auditing"></a>Surveillance continue et audit

En dernier lieu, mais pas la surveillance et l’audit les moins continus de l’environnement Microsoft 365, ainsi que les fenêtres et les appareils sont essentiels pour garantir la détection et la correction rapides des intrusions. Des outils tels que le score de sécurité, le centre de sécurité et l’analyse avancée de Microsoft Graph fournissent des informations précieuses à votre client et lient des quantités d’aide à la décision et des données de sécurité inégalées pour assurer une protection et une détection inégalées.


|Recommandation |E3 |E5 |
|---------|---------|---------|
|Vérifiez que le **Journal d’audit** est activé.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Vérifier le score de sécurisation hebdomadaire** : le score sécurisé est un emplacement central pour accéder à l’état de sécurité de votre entreprise et prendre des mesures en fonction des recommandations de score sécurisé. Il est recommandé d’effectuer cette vérification chaque semaine.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|Utiliser les outils **Office 365 ATP** :<br>* Fonctionnalités d’enquête et de réponse aux menaces<br> * Analyse et réponse automatisées |         |![coche verte](../media/green-check-mark.png)|
|Utiliser **Microsoft Defender ATP**:<br> *    [Détection et réponse du point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br> * Le score de sécurisation de l’enquête et de la correction automatisés <br>*    [Chasse avancée](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Cloud App Security** pour détecter un comportement inhabituel dans les applications Cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non fiables, analyser l’utilisation à haut risque et résoudre automatiquement les risques pour votre organisation.|         |![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Azure Sentinel** ou votre outil Siem actuel pour surveiller les menaces au sein de votre environnement. |         |![coche verte](../media/green-check-mark.png)|
|**Déployer [Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) ** pour surveiller et protéger contre les menaces ciblant votre environnement Active Directory local.   |         |![coche verte](../media/green-check-mark.png) |
|Utilisez le **Centre de sécurité Azure** pour surveiller les menaces entre les charges de travail hybrides et de Cloud. Azure Security Center inclut un niveau de fonctionnalité gratuit et un niveau standard de fonctionnalités qui sont payants en fonction des heures ou des heures de ressource.|         |         |

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la surveillance continue et l’audit](../media/m365-security-bdm-illustrations-monitoring-auditing.png)

Principales actions de surveillance recommandées :
- **Consulter le score** de sécurité Microsoft toutes les semaines : le score sécurisé est un emplacement central pour accéder à l’état de sécurité de votre client et prendre des mesures en fonction des recommandations principales. Il est recommandé d’effectuer cette vérification chaque semaine. Le score de sécurité inclut des recommandations provenant d’Azure AD, Intune, de la sécurité des applications Cloud et de Microsoft Defender Advanced Threat Protection, ainsi que Office 365. 
- **Examiner les connexions risquées** toutes les semaines : utilisez le centre d’administration Azure AD pour examiner les connexions à risque hebdomadaires. Le groupe de règles d’identité et d’accès aux appareils recommandé inclut une stratégie pour appliquer la modification du mot de passe sur les connexions à risque.  
- **Passez en revue toutes les semaines les utilisateurs de logiciels malveillants et d’hameçons** , utilisez Office Advanced Threat Protection Threat Explorer pour examiner les principaux utilisateurs ciblés par les logiciels malveillants et les hameçons, et pour déterminer la cause principale de l’impact de ces utilisateurs.
