---
title: Microsoft 365 Sécurité pour les décideurs d’entreprise (BDM)
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: les scénarios de menace et d’attaque les plus courants auxquels sont confrontés les organisations pour leurs environnements de Microsoft 365 et les actions recommandées pour atténuer ces risques.
ms.openlocfilehash: dabd4e094962c15ade360db317fa197698733e2da4cedc752d602337df090a37
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53839987"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 Sécurité pour les décideurs d’entreprise (BDM)

Cet article décrit certains des scénarios de menace et d’attaque les plus courants auxquels sont confrontés les organisations pour leurs environnements Microsoft 365, ainsi que les actions recommandées pour atténuer ces risques. Bien que Microsoft 365 soit livré avec un large éventail de fonctionnalités de sécurité pré-configurées, vous devez également, en tant que client, prendre la responsabilité de sécuriser vos propres identités, données et appareils utilisés pour accéder aux services cloud. Ces conseils ont été développés par Kozeta Ray (architecte de sécurité Microsoft Cloud) et Thiagaraj Sundararajan (consultant senior Microsoft).

Cet article est organisé par priorité de travail, en commençant par la protection des comptes utilisés pour administrer les services et biens les plus critiques, tels que votre client, votre messagerie et vos SharePoint. Il fournit un moyen méthodique d’aborder la sécurité et fonctionne avec la feuille de calcul suivante afin que vous pouvez suivre votre progression avec les parties prenantes et les équipes au sein de votre organisation : sécurité Microsoft 365 pour la feuille de calcul [BDM](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx). 

[![Image miniature Microsoft 365 de recommandations de sécurité BDM](../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx)

Microsoft vous fournit l’outil Score de sécurité au sein de votre client pour analyser automatiquement votre posture de sécurité en fonction de vos activités régulières, attribuer un score et fournir des recommandations d’amélioration de la sécurité. Avant d’agir sur les actions recommandées dans cet article, prenez note de votre score actuel et de vos recommandations. Les actions recommandées dans cet article augmenteront votre score. L’objectif n’est pas d’atteindre le score maximum, mais de prendre en compte les opportunités de protection de votre environnement d’une manière qui n’affecte pas la productivité de vos utilisateurs. Voir [Microsoft Secure Score](defender/microsoft-secure-score.md).

![Suivez ces étapes pour atténuer les risques pour votre entreprise.](../media/security/security-for-bdms-overview.png)

Une chose de plus avant de commencer . . . n’oubliez [pas d’activer le journal d’audit.](../compliance/search-the-audit-log-in-security-and-compliance.md) Vous aurez besoin de ces données ultérieurement, au cas où vous devrez examiner un incident ou une violation. 

## <a name="protect-privileged-accounts"></a>Protéger les comptes privilégiés

Dans un premier temps, nous vous recommandons de vous assurer que les comptes critiques de l’environnement disposent d’une couche de protection supplémentaire, car ces comptes disposent d’accès et d’autorisations pour gérer et modifier les services et ressources critiques, ce qui peut avoir un impact négatif sur l’ensemble de l’organisation, en cas de compromission. La protection des comptes privilégiés est l’un des moyens les plus efficaces de se protéger contre une personne malveillante qui cherche à élever les autorisations d’un compte compromis à un compte administratif. 

|Recommandation  |E3 |E5  |
|---------|---------|---------|
|Appliquer l’authentification multifacteur (MFA) pour tous les comptes d’administration.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)| 
|Implémentez Azure Active Directory (Azure AD) Privileged Identity Management (PIM) pour appliquer un accès privilégié juste-à-temps aux ressources Azure AD et Azure. Vous pouvez également découvrir qui a accès et passer en revue l’accès privilégié.|         | ![coche verte](../media/green-check-mark.png)|
|Implémenter la gestion des accès privilégiés pour gérer le contrôle d’accès granulaire sur les tâches d’administration privilégiées Office 365. |         | ![coche verte](../media/green-check-mark.png)|
|Configurez et utilisez les stations de travail à accès privilégié (PAW) pour administrer les services. N’utilisez pas les mêmes stations de travail pour naviguer sur Internet et vérifier les messages électroniques qui ne sont pas liés à votre compte d’administration.|  ![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png) | 

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection des comptes privilégiés](../media/m365-security-bdm-illustrations-privileged-accounts.png)

Recommandations supplémentaires :
- Assurez-vous que les comptes synchronisés à partir de l’local ne se voit pas attribuer de rôles d’administrateur pour les services cloud. Cela permet d’empêcher un attaquant d’appliquer des comptes locaux pour obtenir un accès administratif aux services cloud. 
- Assurez-vous que les rôles d’administrateur ne sont pas attribués aux comptes de service. Ces comptes ne sont souvent pas surveillés et ne sont pas définies avec des mots de passe qui n’expirent pas. Commencez par vous assurer que les comptes de services AADConnect et ADFS ne sont pas des administrateurs globaux par défaut.
- Supprimez les licences des comptes d’administrateur. À moins qu’il n’existe un cas d’utilisation spécifique pour attribuer des licences à des comptes d’administrateur spécifiques, supprimez les licences de ces comptes. 

## <a name="reduce-the-surface-of-attack"></a>Réduire la surface d’attaque

La zone de mise au point suivante consiste à réduire la surface d’attaque. Cela peut être réalisé avec un minimum d’efforts et d’impact sur vos utilisateurs et services. En réduisant la surface d’attaque, les attaquants ont moins de moyens de lancer une attaque contre votre organisation.

Voici quelques exemples :
- Désactivez les protocoles POP3, IMAP et SMTP. La plupart des organisations modernes n’utilisent plus ces anciens protocoles. Vous pouvez les désactiver en toute sécurité et autoriser les exceptions uniquement si nécessaire. 
- Réduisez et conservez le nombre minimal d’administrateurs globaux dans le client. Cela réduit directement la surface d’attaque pour toutes les applications cloud. 
- Retirez les serveurs et les applications qui ne sont plus utilisés dans votre environnement. 
- Implémenter un processus de désactivation et de suppression des comptes qui ne sont plus utilisés. 

## <a name="protect-against-known-threats"></a>Se protéger contre les menaces connues

Les menaces connues incluent les programmes malveillants, les comptes compromis et le hameçonnage. Certaines protections contre ces menaces peuvent être implémentées rapidement sans impact direct sur vos utilisateurs, tandis que d’autres nécessitent plus de planification et de formation des utilisateurs. 

|Recommandation  |E3  |E5  |
|---------|---------|---------|
|**Configurer l’authentification multifacteur et utiliser les stratégies d’accès conditionnel recommandées,** y compris les stratégies de risque de la signature. Microsoft recommande et a testé un ensemble de stratégies qui fonctionnent ensemble pour protéger toutes les applications cloud, y compris les services Office 365 et Microsoft 365 cloud. Voir [configurations d’identité et d’accès aux appareils.](./office-365-security/microsoft-365-policies-configurations.md) | |![coche verte](../media/green-check-mark.png)|
|**Exiger une authentification multifacteur pour tous les utilisateurs.** Si vous n’avez pas la licence requise pour implémenter les stratégies d’accès conditionnel recommandées, exigez au minimum une authentification multifacteur pour tous les utilisateurs.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Augmentez le niveau de protection contre les programmes malveillants dans la messagerie.** Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Protégez votre messagerie contre les attaques par hameçonnage ciblées.** Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer une protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Defender for Office 365, peut vous aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.| |![coche verte](../media/green-check-mark.png)|
|**Protégez-vous contre les attaques par ransomware dans les e-mails.** Un ransomware vous permet d’accéder à vos données en chiffrant des fichiers ou en verrouiller les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent à des personnes victime en demandant « rançon », généralement sous forme de cryptomonnaie telle que Cryptograph, en échange du renvoi de l’accès à vos données. Vous pouvez vous défendre contre les ransomware en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichier couramment utilisées pour les ransomware, ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par courrier électronique.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|Bloquez les connexions en provenance des pays avec qui vous **n’avez pas d’activité.** Créez une stratégie d’accès conditionnel Azure AD pour bloquer les connexions provenant de ces pays, créant ainsi efficacement un pare-feu géographique autour de votre client.| |![coche verte](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre les menaces connues](../media/m365-security-bdm-illustrations-known-threats.png)

## <a name="protect-against-unknown-threats"></a>Se protéger contre les menaces inconnues

Après avoir ajouté des protections supplémentaires à vos comptes privilégiés et protégé contre les attaques connues, faites attention à la protection contre les menaces inconnues. Les adversaires plus déterminés et avancés utilisent des méthodes innovantes et nouvelles et inconnues pour attaquer les organisations. Avec l’importante télémétrie de données de Microsoft recueillie sur des milliards d’appareils, d’applications et de services, nous sommes en mesure d’effectuer Defender pour Office 365 sur Windows, Office 365 et Azure pour empêcher les attaques de Zero-Day, l’utilisation d’environnements de bac à sable et la vérification de la validité avant d’autoriser l’accès à votre contenu. 


|Recommandation  |E3  |E5  |
|---------|---------|---------|
|**Configurez Microsoft Defender pour Office 365**:<br>* Coffre pièces jointes<br>* Coffre liens<br>* Microsoft Defender for Endpoint for SharePoint, OneDrive, and Microsoft Teams<br>* Anti-hameçonnage dans Defender pour la protection Office 365 protection|         |![coche verte](../media/green-check-mark.png) |
|**Configurez Microsoft Defender pour les fonctionnalités de point de terminaison**:<br>* Antivirus Windows Defender <br>* Exploit Protection <br> * Réduction de la surface d’attaque <br> * Isolation matérielle <br>* Accès contrôlé aux dossiers     |         |![coche verte](../media/green-check-mark.png) |
|**Utilisez Microsoft Cloud App Security** pour découvrir les applications SaaS et commencer à utiliser l’analyse du comportement et la détection des anomalies. |         |![coche verte](../media/green-check-mark.png) |

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre les menaces inconnues](../media/m365-security-bdm-illustrations-unknown-threats.png)

Recommandations supplémentaires :
- Sécuriser les communications de canal partenaire telles que les e-mails à l’aide de TLS.
- Ouvrez Teams fédération uniquement aux partenaires avec qui vous communiquez.
- N’ajoutez pas de domaines d’expéditeurs, d’expéditeurs individuels ou d’adresses IPS sources à votre liste d’adresses fiables, car cela permet de contourner les contrôles de courrier indésirable et de programmes malveillants . Une pratique courante chez les clients consiste à ajouter leurs propres domaines acceptés ou un certain nombre d’autres domaines où des problèmes de flux de messagerie peuvent avoir été signalés à la liste d’expéditeurs. N’ajoutez pas de domaines dans la liste Filtrage du courrier indésirable et des connexions, car cela contourne potentiellement toutes les vérifications de courrier indésirable. 
- Activer les notifications de courrier indésirable sortant : activez les notifications de courrier indésirable sortant vers une liste de distribution en interne à l’équipe du service d’aide ou d’administration informatique pour signaler si l’un des utilisateurs internes envoie des courriers indésirables en externe. Il peut s’agit d’un indicateur de compromissions du compte.
- Désactivez Remote PowerShell pour tous les utilisateurs — Remote PowerShell est principalement utilisé par les administrateurs pour accéder aux services à des fins administratives ou à des fins d’accès à l’API par programme. Nous vous recommandons de désactiver cette option pour les utilisateurs non administrateurs afin d’éviter la reconnaissance, sauf s’ils ont besoin d’y accéder. 
- Bloquer l’accès Microsoft Azure portail de gestion à tous les non-administrateurs. Pour ce faire, vous pouvez créer une règle d’accès conditionnel pour bloquer tous les utilisateurs, à l’exception des administrateurs. 


## <a name="assume-breach"></a>Supposer une violation

Bien que Microsoft prenne toutes les mesures possibles pour empêcher les menaces et les attaques, nous vous recommandons de toujours travailler dans la logique « Supposer une violation ». Même si un attaquant a réussi à s’identiser dans l’environnement, nous devons nous assurer qu’il ne peut pas exfiltrer les données ou les informations d’identité de l’environnement. Pour cette raison, nous vous recommandons d’activer la protection contre les fuites de données sensibles telles que les numéros de sécurité sociale, les numéros de cartes de crédit, les informations personnelles supplémentaires et d’autres informations confidentielles au niveau de l’organisation. 

La logique « Supposer une violation » nécessite l’implémentation d’une stratégie de réseau de confiance zéro, ce qui signifie que les utilisateurs ne sont pas entièrement fiables simplement parce qu’ils sont internes au réseau. Au lieu de cela, dans le cadre de l’autorisation de ce que les utilisateurs peuvent faire, des ensembles de conditions sont spécifiés et lorsque ces conditions sont remplies, certains contrôles sont appliqués. Les conditions peuvent inclure l’état d’état de l’appareil, l’accès à l’application, les opérations effectuées et les risques pour l’utilisateur. Par exemple, une action d’inscription d’appareil doit toujours déclencher l’authentification MFA pour s’assurer qu’aucun périphérique rouge n’est ajouté à votre environnement. 

Une stratégie de réseau de confiance zéro exige également que vous connaissiez l’endroit où vos informations sont stockées et que vous appliquiez les contrôles appropriés pour la classification, la protection et la rétention. Pour protéger efficacement vos biens les plus critiques et sensibles, vous devez d’abord identifier où ils se trouvent et faire l’inventaire, ce qui peut être difficile. Ensuite, travaillez avec votre organisation pour définir une stratégie de gouvernance. La définition d’un schéma de classification pour une organisation et la configuration de stratégies, d’étiquettes et de conditions nécessitent une planification et une préparation minutieuses. Il est important de savoir qu’il ne s’agit pas d’un processus piloté par l’it. N’oubliez pas de travailler avec votre équipe juridique et de conformité pour développer une classification et un schéma d’étiquetage appropriés pour les données de votre organisation.

Microsoft 365 fonctionnalités de protection des informations peuvent vous aider à découvrir les informations dont vous avez besoin, l’endroit où elles sont stockées et les informations qui nécessitent une protection supplémentaire. La protection des informations est un processus continu et les fonctionnalités de Microsoft 365 vous offrent une visibilité sur la façon dont les utilisateurs utilisent et distribuent des informations sensibles, l’endroit où vos informations sont actuellement stockées et où elles circulent. Vous pouvez également voir comment les utilisateurs gèrent les informations réglementées pour s’assurer que les étiquettes et protections appropriées sont appliquées.


|Recommandation |E3|E5 |
|---------|---------|---------|
|**Examinez et optimisez votre accès conditionnel et les stratégies associées** pour vous aligner sur vos objectifs pour un réseau de confiance zéro . La protection contre les menaces connues inclut l’implémentation d’un ensemble de [stratégies recommandées.](./office-365-security/microsoft-365-policies-configurations.md) Examinez votre implémentation de ces stratégies pour vous assurer que vous protégez vos applications et vos données contre les pirates informatiques qui ont accédé à votre réseau. La stratégie de protection des applications Intune recommandée pour Windows 10 active Windows Protection des informations personnelles (WIP). Wip protège contre les fuites accidentelles de données de votre organisation par le biais d’applications et de services, tels que le courrier électronique, les réseaux sociaux et le cloud public. |         |![coche verte](../media/green-check-mark.png)|
|**Désactiver le forwarding de courrier externe.** Les pirates informatiques qui accèdent à la boîte aux lettres d’un utilisateur peuvent dérober votre courrier en l’insérez pour qu’elle les envoie automatiquement. Cela peut se produire même sans la sensibilisation de l’utilisateur. Vous pouvez empêcher cela en configurant une règle de flux de messagerie.|![coche verte](../media/green-check-mark.png) |![coche verte](../media/green-check-mark.png)|
|**Désactiver le partage de calendrier externe anonyme.** Par défaut, le partage de calendrier anonyme externe est autorisé. [Désactivez le partage de calendrier](/exchange/sharing/sharing-policies/modify-a-sharing-policy) pour réduire les fuites potentielles d’informations sensibles.|![coche verte](../media/green-check-mark.png) |![coche verte](../media/green-check-mark.png)|
|**Configurer des stratégies de protection contre la perte de données pour les données sensibles.** Créez une stratégie de protection contre la perte de données dans le Centre de conformité de sécurité pour découvrir et protéger les données sensibles telles que les numéros de carte de crédit, les numéros de sécurité sociale et les numéros &amp; de compte bancaire. Microsoft 365 comprend de nombreux types d’informations sensibles prédéfinés que vous pouvez utiliser dans les stratégies de protection contre la perte de données. Vous pouvez également créer vos propres types d’informations sensibles pour les données sensibles personnalisées dans votre environnement. |![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Implémenter des stratégies de classification des données et de protection des informations.** Implémentez des étiquettes de sensibilité et utilisez-les pour classifier et appliquer la protection aux données sensibles. Vous pouvez également utiliser ces étiquettes dans les stratégies de protection contre la perte de données. Si vous utilisez des étiquettes Azure Information Protection, nous vous recommandons d’éviter de créer de nouvelles étiquettes dans d’autres centres d’administration.|         |![coche verte](../media/green-check-mark.png)|
|Protéger les données dans les applications et services tiers à **l’aide de Sécurité des applications cloud**. Configurez Sécurité des applications cloud stratégies de protection des informations sensibles sur des applications cloud tierces, telles que Salesforce, Box ou Dropbox. Vous pouvez utiliser les types d’informations sensibles et les étiquettes de confidentialité que vous avez créées dans Sécurité des applications cloud et les appliquer à vos applications SaaS. <br><br>Microsoft Cloud App Security vous permettent d’appliquer un large éventail de processus automatisés. Les stratégies peuvent être définies de manière à fournir des analyses de conformité continues, des tâches eDiscovery juridiques, la protection contre la courrier électronique (DLP) pour le contenu sensible partagé publiquement, et bien plus encore. Sécurité des applications cloud pouvez surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier). |         |![coche verte](../media/green-check-mark.png)|
|**Utilisez [Microsoft Defender pour le point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) pour** identifier si les utilisateurs stockent des informations sensibles sur Windows appareils. |         |![coche verte](../media/green-check-mark.png)|
|**Utilisez le [scanneur AIP pour](/azure/information-protection/deploy-aip-scanner) identifier et classer les informations sur les serveurs et les partages de fichiers.** Utilisez l’outil de rapports AIP pour afficher les résultats et prendre les mesures appropriées.|         |![coche verte](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la protection contre les violations](../media/m365-security-bdm-illustrations-assume-breach.png)

## <a name="continuous-monitoring-and-auditing"></a>Surveillance et audit continus

Enfin, la surveillance et l’audit continus de l’environnement Microsoft 365 avec les Windows et les périphériques sont essentiels pour vous assurer que vous êtes en mesure de détecter et de corriger rapidement les intrusions. Les outils tels que le Score de sécurité, le Centre de sécurité et l’analyse avancée de Microsoft Intelligent Graph fournissent des informations précieuses sur votre client et lier d’importantes quantités de données de sécurité et d’intelligence contre les menaces pour vous offrir une protection et une détection des menaces inédites.


|Recommandation |E3 |E5 |
|---------|---------|---------|
|Assurez-vous **que le journal d’audit** est allumé.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|**Examinez le score de sécurisation** toutes les semaines — Le score de sécurité est un emplacement central pour accéder au statut de sécurité de votre entreprise et prendre des mesures en fonction des recommandations de niveau de sécurité. Il est recommandé d’effectuer cette vérification toutes les semaines.|![coche verte](../media/green-check-mark.png)|![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender pour les outils Office 365** de gestion :<br>* Fonctionnalités d’examen et de réponse aux menaces<br> * Examen et réponse automatisés |         |![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender pour le point de terminaison**:<br> *    [Détection et réponse des points de terminaison](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br> * Examen automatisé et score de sécurisation de correction <br>*    [Recherche avancée](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Cloud App Security** pour détecter des comportements inhabituels dans les applications cloud afin d’identifier les ransomware, les utilisateurs compromis ou les applications non autorisées, d’analyser l’utilisation à risque élevé et de corriger automatiquement les risques pour votre organisation.|         |![coche verte](../media/green-check-mark.png)|
|Utilisez **Microsoft Azure Sentinel** ou votre outil SIEM actuel pour surveiller les menaces au sein de votre environnement. |         |![coche verte](../media/green-check-mark.png)|
|**Déployez [Microsoft Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp)** pour surveiller et protéger contre les menaces ciblant votre environnement Active Directory local.   |         |![coche verte](../media/green-check-mark.png) |
|Utilisez **Azure Defender** _ pour surveiller les menaces sur les charges de travail hybrides et cloud. Azure Defender_ inclut un niveau gratuit de fonctionnalités et un niveau standard de fonctionnalités qui sont payés en fonction des heures de ressources ou des transactions.|         |         |

Le diagramme suivant illustre ces fonctionnalités.
![Fonctionnalités recommandées pour la surveillance et l’audit continus](../media/m365-security-bdm-illustrations-monitoring-auditing.png)

Principales actions de surveillance recommandées :
- **Examinez le Score de sécurité Microsoft** toutes les semaines — Le niveau de sécurité est un emplacement central pour accéder à l’état de sécurité de votre client et prendre des mesures en fonction des recommandations les plus importantes. Il est recommandé d’effectuer cette vérification toutes les semaines. Le score de sécurité inclut des recommandations d’Azure AD, d’Intune, de Sécurité des applications cloud et de Microsoft Defender pour le point de terminaison, ainsi que Office 365. 
- **Passer en revue les connexions risquées** toutes les semaines : utilisez le Centre d’administration Azure AD pour passer en revue les connexions risquées toutes les semaines. L’ensemble de règles d’accès aux identités et appareils recommandé inclut une stratégie pour appliquer la modification du mot de passe aux connecteurs à risque.  
-  Passer en revue les principaux programmes malveillants et utilisateurs de hameçonnage chaque semaine : utilisez Microsoft Defender pour l’Explorateur de menaces Office 365 pour passer en revue les principaux utilisateurs ciblés avec des programmes malveillants et le hameçonnage et pour connaître la cause première de l’impact de ces utilisateurs.