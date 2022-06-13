---
title: Microsoft 365 security for Business Decision Makers (BDM)
description: Les scénarios de menaces et d’attaques les plus courants auxquels sont actuellement confrontées les organisations pour leurs environnements Microsoft 365 et les actions recommandées pour atténuer ces risques.
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.openlocfilehash: 056244562191389ee0991ef1040348ef5e6f82f7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015393"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 security for Business Decision Makers (BDM)

Cet article décrit certains des scénarios les plus courants de menaces et d’attaques auxquels sont actuellement confrontées les organisations pour leurs environnements Microsoft 365, ainsi que les actions recommandées pour atténuer ces risques. Bien que Microsoft 365 soit fourni avec un large éventail de fonctionnalités de sécurité préconfigurées, vous devez également, en tant que client, prendre la responsabilité de sécuriser vos propres identités, données et appareils utilisés pour accéder aux services cloud. Ces conseils ont été développés par Kozeta Beam (Microsoft Cloud Security Architect) et Thiagaraj Sundararajan (Microsoft Senior Consultant).

Cet article est organisé par priorité de travail, en commençant par la protection des comptes utilisés pour administrer les services et ressources les plus critiques, tels que votre locataire, votre courrier électronique et SharePoint. Il fournit un moyen méthodique d’aborder la sécurité et fonctionne avec la feuille de calcul suivante afin que vous puissiez suivre vos progrès auprès des parties prenantes et des équipes au sein de votre organisation : [Microsoft 365 sécurité pour la feuille de calcul bdMs](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Exemple de feuille de calcul de recommandation de sécurité BDM Microsoft 365" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Microsoft vous fournit l’outil Degré de sécurisation au sein de votre locataire pour analyser automatiquement votre posture de sécurité en fonction de vos activités régulières, attribuer un score et fournir des recommandations d’amélioration de la sécurité. Avant d’effectuer les actions recommandées dans cet article, prenez note de votre score actuel et de vos recommandations. Les actions recommandées dans cet article augmenteront votre score. L’objectif n’est pas d’atteindre le score maximal, mais d’être conscient des opportunités de protéger votre environnement d’une manière qui n’affecte pas négativement la productivité de vos utilisateurs. Voir [Microsoft Secure Score](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Étapes permettant d’atténuer les risques pour votre entreprise" lightbox="../media/security/security-for-bdms-overview.png":::

Encore une chose avant de commencer . . . veillez à [activer le journal d’audit](../compliance/search-the-audit-log-in-security-and-compliance.md). Vous aurez besoin de ces données ultérieurement, si vous avez besoin d’enquêter sur un incident ou une violation.

## <a name="protect-privileged-accounts"></a>Protéger les comptes privilégiés

Dans un premier temps, nous vous recommandons de veiller à ce que les comptes critiques dans l’environnement bénéficient d’une couche de protection supplémentaire, car ces comptes disposent d’un accès et d’autorisations pour gérer et modifier les services et ressources critiques, ce qui peut avoir un impact négatif sur l’ensemble de l’organisation, s’il est compromis. La protection des comptes privilégiés est l’un des moyens les plus efficaces de se protéger contre un attaquant qui cherche à élever les autorisations d’un compte compromis à un compte administratif.

|Recommandation|E3|E5|
|---|---|---|
|Appliquer l’authentification multifacteur (MFA) pour tous les comptes d’administration.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|Implémentez Azure Active Directory (Azure AD) Privileged Identity Management (PIM) pour appliquer un accès privilégié juste-à-temps aux ressources Azure AD et Azure. Vous pouvez également découvrir qui a accès et passer en revue l’accès privilégié.||![coche verte.](../media/green-check-mark.png)|
|Implémentez la gestion des accès privilégiés pour gérer le contrôle d’accès granulaire sur les tâches d’administration privilégiées dans Office 365.||![coche verte.](../media/green-check-mark.png)|
|Configurez et utilisez des stations de travail à accès privilégié (PAW) pour administrer les services. N’utilisez pas les mêmes stations de travail pour naviguer sur Internet et vérifier les e-mails qui ne sont pas liés à votre compte d’administration.|!![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png):::|

Le diagramme suivant illustre ces fonctionnalités.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="Fonctionnalités recommandées pour la protection des comptes privilégiés" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Recommandations supplémentaires :

- Vérifiez que les comptes qui sont synchronisés à partir d’un site local ne reçoivent pas de rôles d’administrateur pour les services cloud. Cela permet d’empêcher un attaquant d’appliquer des comptes locaux pour obtenir un accès administratif aux services cloud.
- Vérifiez que les comptes de service ne reçoivent pas de rôles d’administrateur. Ces comptes ne sont souvent pas surveillés et définis avec des mots de passe qui n’expirent pas. Commencez par vous assurer que les comptes de services AADConnect et ADFS ne sont pas des administrateurs généraux par défaut.
- Supprimez les licences des comptes d’administrateur. À moins qu’il n’existe un cas d’usage spécifique pour attribuer des licences à des comptes d’administrateur spécifiques, supprimez les licences de ces comptes.

## <a name="reduce-the-surface-of-attack"></a>Réduire la surface d’attaque

La zone de focus suivante consiste à réduire la surface d’attaque. Cela peut être effectué avec un minimum d’efforts et d’impact sur vos utilisateurs et services. En réduisant la surface d’attaque, les attaquants ont moins de moyens de lancer une attaque contre votre organisation.

Voici quelques exemples :

- Désactivez les protocoles POP3, IMAP et SMTP. La plupart des organisations modernes n’utilisent plus ces protocoles plus anciens. Vous pouvez les désactiver en toute sécurité et autoriser les exceptions uniquement en fonction des besoins.
- Réduisez et conservez le nombre d’administrateurs généraux dans le locataire au minimum absolu requis. Cela réduit directement la surface d’attaque pour toutes les applications cloud.
- Mettez hors service les serveurs et applications qui ne sont plus utilisés dans votre environnement.
- Implémentez un processus de désactivation et de suppression de comptes qui ne sont plus utilisés.

## <a name="protect-against-known-threats"></a>Se protéger contre les menaces connues

Les menaces connues incluent les programmes malveillants, les comptes compromis et le hameçonnage. Certaines protections contre ces menaces peuvent être implémentées rapidement sans impact direct sur vos utilisateurs, tandis que d’autres nécessitent davantage de planification et de formation des utilisateurs.

|Recommandation|E3|E5|
|---|---|---|
|**Configurez l’authentification multifacteur et utilisez les stratégies d’accès conditionnel recommandées, notamment les stratégies de risque de connexion**. Microsoft recommande et a testé un ensemble de stratégies qui fonctionnent ensemble pour protéger toutes les applications cloud, y compris les services Office 365 et Microsoft 365. Consultez [les configurations d’identité et d’accès aux appareils](./office-365-security/microsoft-365-policies-configurations.md).||![coche verte.](../media/green-check-mark.png)|
|**Exiger une authentification multifacteur pour tous les utilisateurs**. Si vous n’avez pas les licences requises pour implémenter les stratégies d’accès conditionnel recommandées, au minimum, nécessitez une authentification multifacteur pour tous les utilisateurs.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Augmentez le niveau de protection contre les programmes malveillants dans le courrier**. Votre environnement Office 365 ou Microsoft 365 inclut une protection contre les programmes malveillants, mais vous pouvez augmenter cette protection en bloquant les pièces jointes avec des types de fichiers couramment utilisés pour les programmes malveillants.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Protégez votre courrier contre les attaques ciblées par hameçonnage**. Si vous avez configuré un ou plusieurs domaines personnalisés pour votre environnement Office 365 ou Microsoft 365, vous pouvez configurer la protection anti-hameçonnage ciblée. La protection anti-hameçonnage, qui fait partie de Defender pour Office 365, peut aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillantes et d’autres attaques par hameçonnage. Si vous n’avez pas configuré de domaine personnalisé, vous n’avez pas besoin de le faire.||![coche verte.](../media/green-check-mark.png)|
|**Protégez-vous contre les attaques par ransomware dans les e-mails**. Le ransomware supprime l’accès à vos données en chiffrant des fichiers ou en verrouillant les écrans d’ordinateur. Il tente ensuite d’extorquer de l’argent aux victimes en demandant une « rançon », généralement sous forme de crypto-monnaies comme Le Bitcoin, en échange du retour de l’accès à vos données. Vous pouvez vous défendre contre les ransomwares en créant une ou plusieurs règles de flux de messagerie pour bloquer les extensions de fichier couramment utilisées pour les ransomware ou pour avertir les utilisateurs qui reçoivent ces pièces jointes par e-mail.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Bloquez les connexions à partir de pays avec lesquels vous ne faites pas d’affaires**. Créez une stratégie d’accès conditionnel Azure AD pour bloquer toutes les connexions en provenance de ces pays, créant ainsi un pare-feu géographique autour de votre locataire.||![coche verte.](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="Fonctionnalités recommandées pour la protection contre les menaces connues" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::

## <a name="protect-against-unknown-threats"></a>Se protéger contre les menaces inconnues

Après avoir ajouté des protections supplémentaires à vos comptes privilégiés et protégé contre les attaques connues, faites attention à la protection contre les menaces inconnues. Les adversaires les plus déterminés et les plus avancés utilisent des méthodes innovantes et nouvelles et inconnues pour attaquer les organisations. Grâce à la vaste télémétrie des données collectées par Microsoft sur des milliards d’appareils, d’applications et de services, nous sommes en mesure d’effectuer des Defender pour Office 365 sur Windows, Office 365 et Azure afin d’éviter les attaques Zero-Day, l’utilisation d’environnements bac à sable et la vérification de la validité avant d’autoriser l’accès à votre contenu.

|Recommandation|E3|E5|
|---|---|---|
|**Configurer Microsoft Defender pour Office 365** :<ul><li>Pièces jointes fiables</li><li>Liens fiables</li><li>Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams</li><li>Protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage</li></ul>||![coche verte.](../media/green-check-mark.png)|
|**Configurer Microsoft Defender pour point de terminaison fonctionnalités** :<ul><li>Antivirus Windows Defender</li><li>Exploit Protection</li><li>Réduction de la surface d'attaque</li><li>L'isolation matérielle </li><li>Accès contrôlé aux dossiers</li></ul>||![coche verte.](../media/green-check-mark.png)|
|**Utilisez Microsoft Defender for Cloud Apps** pour découvrir les applications SaaS et commencer à utiliser l’analytique du comportement et la détection des anomalies.||![coche verte.](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Exemple des fonctionnalités offertes par les outils de protection contre les menaces inconnues" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::

Recommandations supplémentaires :

- Sécurisez les communications de canal partenaire telles que les e-mails à l’aide de TLS.
- Ouvrez Teams Fédération uniquement aux partenaires avec lesquels vous communiquez.
- N’ajoutez pas de domaines d’expéditeur, d’expéditeurs individuels ou d’adresses IP sources à votre liste verte, car cela permet de contourner les vérifications du courrier indésirable et des programmes malveillants . Une pratique courante avec les clients consiste à ajouter leurs propres domaines acceptés ou de nombreux autres domaines où des problèmes de flux de courrier électronique peuvent avoir été signalés à la liste verte. N’ajoutez pas de domaines dans la liste de filtrage du courrier indésirable et des connexions, car cela contourne potentiellement toutes les vérifications de courrier indésirable.
- Activer les notifications de courrier indésirable sortant : activez les notifications de courrier indésirable sortant vers une liste de distribution en interne au support technique ou à l’équipe d’administration informatique pour signaler si l’un des utilisateurs internes envoie des e-mails de courrier indésirable en externe. Il peut s’agir d’un indicateur indiquant que le compte a été compromis.
- Désactivez PowerShell à distance pour tous les utilisateurs . PowerShell distant est principalement utilisé par les administrateurs pour accéder aux services à des fins d’administration ou d’accès à l’API par programmation. Nous vous recommandons de désactiver cette option pour les utilisateurs non administrateurs afin d’éviter la reconnaissance, sauf s’ils ont une exigence métier pour y accéder.
- Bloquer l’accès au portail de gestion Microsoft Azure à tous les non-administrateurs. Pour ce faire, vous pouvez créer une règle d’accès conditionnel pour bloquer tous les utilisateurs, à l’exception des administrateurs.

## <a name="assume-breach"></a>Supposer une violation

Bien que Microsoft prenne toutes les mesures possibles pour prévenir les menaces et les attaques, nous vous recommandons de toujours travailler dans l’état d’esprit « Assume Breach ». Même si un attaquant a réussi à s’infiltrer dans l’environnement, nous devons nous assurer qu’il ne peut pas exfiltrer des données ou des informations d’identité de l’environnement. Pour cette raison, nous vous recommandons d’activer la protection contre les fuites de données sensibles telles que les numéros de sécurité sociale, les numéros de cartes de crédit, d’autres informations personnelles et d’autres informations confidentielles au niveau de l’organisation.

|Recommandation|E3|E5|
|---|---|---|
|**Passez en revue et optimisez votre accès conditionnel et vos stratégies associées pour vous aligner sur vos objectifs pour un réseau de confiance zéro**. La protection contre les menaces connues comprend l’implémentation d’un ensemble de [stratégies recommandées](./office-365-security/microsoft-365-policies-configurations.md). Passez en revue votre implémentation de ces stratégies pour vous assurer que vous protégez vos applications et vos données contre les pirates qui ont obtenu l’accès à votre réseau. La stratégie de protection des applications Intune recommandée pour Windows 10 active Windows Information Protection (WIP). WIP protège contre les fuites accidentelles de données de votre organisation par le biais d’applications et de services, tels que la messagerie électronique, les médias sociaux et le cloud public.||![coche verte.](../media/green-check-mark.png)|
|**Désactivez le transfert de courrier externe**. Les pirates qui accèdent à la boîte aux lettres d’un utilisateur peuvent voler votre courrier en définissant la boîte aux lettres pour transférer automatiquement le courrier électronique. Cela peut se produire même sans que l’utilisateur en soit conscient. Vous pouvez empêcher cela en configurant une règle de flux de messagerie.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Désactivez le partage de calendrier externe anonyme**. Par défaut, le partage de calendrier anonyme externe est autorisé. [Désactivez le partage de calendrier](/exchange/sharing/sharing-policies/modify-a-sharing-policy) pour réduire les fuites potentielles d’informations sensibles.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Configurez des stratégies de protection contre la perte de données pour les données sensibles**. Créez une stratégie de protection contre la perte de données Microsoft Purview pour découvrir et protéger des données sensibles telles que les numéros de carte de crédit, les numéros de sécurité sociale et les numéros de compte bancaire. Microsoft 365 inclut de nombreux types d’informations sensibles prédéfinis que vous pouvez utiliser dans les stratégies de protection contre la perte de données. Vous pouvez également créer vos propres types d’informations sensibles pour les données sensibles personnalisées à votre environnement.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Implémentez des stratégies de classification des données et de protection des informations**. Implémentez des étiquettes de confidentialité et utilisez-les pour classifier et appliquer la protection aux données sensibles. Vous pouvez également utiliser ces étiquettes dans les stratégies de protection contre la perte de données. Si vous utilisez des étiquettes Azure Information Protection, nous vous recommandons d’éviter de créer des étiquettes dans d’autres centres d’administration.||![coche verte.](../media/green-check-mark.png)|
|**Protégez les données dans des applications et des services tiers à l’aide de Defender pour le cloud Apps**. Configurez des stratégies Defender pour le cloud Apps pour protéger les informations sensibles sur des applications cloud tierces, telles que Salesforce, Box ou Dropbox. Vous pouvez utiliser les types d’informations sensibles et les étiquettes de confidentialité que vous avez créés dans les stratégies Defender pour le cloud Apps et les appliquer à vos applications SaaS. <p> Microsoft Defender for Cloud Apps vous permet d’appliquer un large éventail de processus automatisés. Les stratégies peuvent être définies pour fournir des analyses de conformité continues, des tâches eDiscovery légales, des DLP pour le contenu sensible partagé publiquement, etc. Defender pour le cloud Apps peut surveiller n’importe quel type de fichier en fonction de plus de 20 filtres de métadonnées (par exemple, niveau d’accès, type de fichier).||![coche verte.](../media/green-check-mark.png)|
|**Utilisez [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) pour déterminer si les utilisateurs stockent des informations sensibles sur leurs appareils Windows**.||![coche verte.](../media/green-check-mark.png)|
|**Utilisez [le scanneur AIP](/azure/information-protection/deploy-aip-scanner) pour identifier et classer les informations entre les serveurs et les partages de fichiers**. Utilisez l’outil de création de rapports AIP pour afficher les résultats et prendre les mesures appropriées.||![coche verte.](../media/green-check-mark.png)|

Le diagramme suivant illustre ces fonctionnalités.
:::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="Fonctionnalités recommandées pour la protection contre les menaces inconnues" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::

## <a name="continuous-monitoring-and-auditing"></a>Surveillance et audit continus

Enfin, la surveillance et l’audit continus de l’environnement Microsoft 365 ainsi que les Windows et les appareils sont essentiels pour vous assurer que vous êtes en mesure de détecter et de corriger rapidement les intrusions. Des outils tels que le degré de sécurisation, le portail Microsoft 365 Defender et l’analytique avancée de Microsoft Intelligent Graph fournissent des informations précieuses à votre locataire et lient des quantités massives de données de sécurité et de renseignement sur les menaces pour vous fournir une protection et une détection des menaces inégalées.

|Recommandation|E3|E5|
|---|---|---|
|Vérifiez que le **journal d’audit** est activé.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|**Passez en revue le degré de sécurisation hebdomadaire** : le degré de sécurisation est un emplacement central pour accéder à l’état sécurité de votre entreprise et prendre des mesures en fonction des recommandations de degré de sécurisation. Il est recommandé d’effectuer cette vérification toutes les semaines.|![coche verte.](../media/green-check-mark.png)|![coche verte.](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender pour Office 365** outils : <ul><li>Fonctionnalités d’investigation et de réponse aux menaces</li><li>Enquêtes et réponses automatisées</li></ul>||![coche verte.](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender pour point de terminaison** : <ul><li>[Détection et réponse du point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)</li><li>Degré de sécurisation de l’examen et de la correction automatisés</li><li>[Repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)</li></ul>||![coche verte.](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender for Cloud Apps** pour détecter les comportements inhabituels entre les applications cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non autorisées, analyser l’utilisation à haut risque et corriger automatiquement pour limiter le risque pour votre organisation.||:::image type="content" source="../media/green-check-mark.png" alt-text="Exemple de coche de couleur verte" lightbox="../media/green-check-mark.png":::|
|Utilisez **Microsoft Sentinel** ou votre outil SIEM actuel pour surveiller les menaces dans votre environnement.||![coche verte.](../media/green-check-mark.png)|
|**Déployez [Microsoft Defender pour Identity](/azure-advanced-threat-protection/what-is-atp)** pour surveiller et protéger contre les menaces ciblées sur votre environnement Active Directory local.||![coche verte.](../media/green-check-mark.png)|
|Utilisez **Microsoft Defender pour le cloud** pour surveiller les menaces sur les charges de travail hybrides et cloud. Microsoft Defender pour le cloud inclut un niveau gratuit de fonctionnalités et un niveau standard de fonctionnalités qui sont payées en fonction des heures de ressource ou des transactions.

Le diagramme suivant illustre ces fonctionnalités.

:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="Fonctionnalités recommandées pour la surveillance et l’audit continus" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::

Principales actions de supervision recommandées :

- **Passez en revue le degré de sécurisation Microsoft toutes les semaines** : le degré de sécurisation est un emplacement central pour accéder à l’état de sécurité de votre locataire et prendre des mesures en fonction des recommandations les plus recommandées. Il est recommandé d’effectuer cette vérification toutes les semaines. Le degré de sécurisation inclut des recommandations provenant d’Azure AD, de Intune, d’applications Defender pour le cloud et de Microsoft Defender pour point de terminaison, ainsi que de Office 365.
- **Passez en revue les connexions à risque toutes les semaines** . Utilisez le Centre d’administration Azure AD pour passer en revue les connexions à risque toutes les semaines. L’ensemble de règles d’identité et d’accès aux appareils recommandé inclut une stratégie pour appliquer la modification du mot de passe aux connexions à risque.
- **Passez en revue les principaux programmes malveillants et les utilisateurs hameçonné chaque semaine** : utilisez Microsoft Defender pour Office 365 Explorateur des menaces pour passer en revue les principaux utilisateurs ciblés par des programmes malveillants et des hameçonnages et pour déterminer la cause racine de ces utilisateurs.
