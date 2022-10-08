---
title: Préparer le déploiement de Microsoft Defender pour point de terminaison
description: Préparer l’approbation des parties prenantes, les délais, les considérations relatives à l’environnement et l’ordre d’adoption pour le déploiement de Microsoft Defender pour point de terminaison
keywords: déployer, préparer, parties prenantes, chronologie, environnement, point de terminaison, serveur, gestion, adoption
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-endpointprotect
- m365solution-scenario
- highpri
- tier1
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: df603a3c7739502a1225b8986c4b3282e45d78ca
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233989"
---
# <a name="prepare-microsoft-defender-for-endpoint-deployment"></a>Préparer le déploiement de Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Le déploiement de Defender pour point de terminaison est un processus en trois phases :

|![phase de déploiement : préparez-vous.](images/phase-diagrams/prepare.png)<br>Phase 1 : préparation|[![phase de déploiement - configuration](images/phase-diagrams/setup.png)](production-deployment.md)<br>[Phase 2 : configuration](production-deployment.md)|[![phase de déploiement - intégration](images/phase-diagrams/onboard.png)](onboarding.md)<br>[Phase 3 : intégration](onboarding.md)|
|---|---|---|
|*Vous êtes là !*|||

Vous êtes actuellement en phase de préparation.

La préparation est essentielle pour tout déploiement réussi. Dans cet article, vous serez guidé sur les points à prendre en compte lors de la préparation du déploiement de Defender pour point de terminaison.

## <a name="stakeholders-and-approval"></a>Parties prenantes et approbation

La section suivante permet d’identifier toutes les parties prenantes impliquées dans le projet et qui doivent approuver, examiner ou rester informés.

Ajoutez des parties prenantes au tableau ci-dessous selon les besoins de votre organisation.

- SO = Approuver le projet
- R = Examiner ce projet et fournir une entrée
- I = Informé de ce projet

<br>

****

|Nom|Rôle|Action|
|---|---|---|
|Entrer le nom et l’e-mail|**Chef de la sécurité de l’information (CISO)** *Représentant exécutif qui sert de sponsor au sein de l’organisation pour le déploiement de nouvelles technologies.*|SO|
|Entrer le nom et l’e-mail|**Chef du Centre d’opérations de cyberdéfense (CDOC)** *Représentant de l’équipe CDOC chargée de définir la façon dont cette modification est alignée sur les processus de l’équipe des opérations de sécurité des clients.*|SO|
|Entrer le nom et l’e-mail|**Architecte de sécurité** *Un représentant de l’équipe sécurité responsable de la définition de la façon dont cette modification est alignée sur l’architecture de sécurité principale de l’organisation.*|R|
|Entrer le nom et l’e-mail|**Architecte du lieu** *de travail Un représentant de l’équipe informatique responsable de la définition de la façon dont ce changement est aligné sur l’architecture de travail principale de l’organisation.*|R|
|Entrer le nom et l’e-mail|**Analyste de sécurité** *Un représentant de l’équipe CDOC qui peut fournir des informations sur les fonctionnalités de détection, l’expérience utilisateur et l’utilité globale de ce changement du point de vue des opérations de sécurité.*|I|
||||

## <a name="environment"></a>Environnement

Cette section permet de s’assurer que votre environnement est bien compris par les parties prenantes, ce qui vous aidera à identifier les dépendances potentielles et/ou les modifications requises dans les technologies ou les processus.

<br>

****

|Quoi|Description|
|---|---|
|Nombre de points de terminaison|Nombre total de points de terminaison par système d’exploitation.|
|Nombre de serveurs|Nombre total de serveurs par version du système d’exploitation.|
|Moteur de gestion|Nom et version du moteur de gestion (par exemple, System Center Configuration Manager Current Branch 1803).|
|Distribution CDOC|Structure CDOC de haut niveau (par exemple, niveau 1 externalisé à Contoso, niveau 2 et niveau 3 en interne distribué à travers l’Europe et l’Asie).|
|Informations et événements de sécurité (SIEM)|Technologie SIEM utilisée.|
|||

## <a name="role-based-access-control"></a>Contrôle d'accès basé sur les rôles

Microsoft recommande d’utiliser le concept de privilèges minimum. Defender pour point de terminaison tire parti des rôles intégrés dans Azure Active Directory. Microsoft recommande de [passer en revue les différents rôles disponibles](/azure/active-directory/roles/permissions-reference) et de choisir le bon rôle pour répondre à vos besoins pour chaque personnage de cette application. Certains rôles peuvent devoir être appliqués temporairement et supprimés une fois le déploiement terminé.

<br>

****

|Personas|Rôles|Rôle Azure AD (si nécessaire)|Affecter à|
|---|---|---|---|
|Administrateur de sécurité||||
|Analyste de sécurité||||
|Administrateur de point de terminaison||||
|Administrateur d’infrastructure||||
|Propriétaire/partie prenante de l’entreprise||||
|

Microsoft recommande d’utiliser [Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure) pour gérer vos rôles afin de fournir un audit, un contrôle et une révision d’accès supplémentaires pour les utilisateurs disposant d’autorisations d’annuaire.

Defender pour point de terminaison prend en charge deux façons de gérer les autorisations :

- **Gestion des autorisations de base** : définissez les autorisations sur un accès complet ou en lecture seule. Les utilisateurs disposant de rôles Administrateur général ou Administrateur de sécurité dans Azure Active Directory ont un accès complet. Le rôle lecteur Sécurité dispose d’un accès en lecture seule et n’accorde pas l’accès pour afficher l’inventaire des machines/appareils.

- **Contrôle d’accès en fonction du rôle (RBAC)** : définissez des autorisations granulaires en définissant des rôles, en attribuant des groupes d’utilisateurs Azure AD aux rôles et en accordant aux groupes d’utilisateurs l’accès aux groupes d’appareils. Pour plus d’informations. consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

Microsoft recommande d’utiliser RBAC pour s’assurer que seuls les utilisateurs disposant d’une justification métier peuvent accéder à Defender pour point de terminaison.

Vous trouverez des détails sur les instructions d’autorisation ici : [créez des rôles et attribuez le rôle à un groupe Azure Active Directory](/microsoft-365/security/defender-endpoint/user-roles#create-roles-and-assign-the-role-to-an-azure-active-directory-group).

L’exemple de tableau suivant sert à identifier la structure du Centre des opérations de cyberdéfense dans votre environnement qui vous aidera à déterminer la structure RBAC requise pour votre environnement.

<br>

****

|Niveau|Description|Autorisation requise|
|---|---|---|
|Niveau 1|**Équipe des opérations de sécurité locale/équipe informatique** <p> Cette équipe trie et examine généralement les alertes contenues dans sa géolocalisation et passe au niveau 2 dans les cas où une correction active est nécessaire.||
|Niveau 2|**Équipe des opérations de sécurité régionales** <p> Cette équipe peut voir tous les appareils de leur région et effectuer des actions de correction.|Afficher les données|
|Niveau 3|**Équipe des opérations de sécurité globale** <p> Cette équipe se compose d’experts en sécurité et est autorisée à voir et à effectuer toutes les actions à partir du portail.|Afficher les données <p> Alertes investigation Active remediation actions <p> Alertes investigation Active remediation actions <p> Gérer les paramètres système du portail <p> Gérer les paramètres de sécurité|
||||

## <a name="adoption-order"></a>Ordre d’adoption

Dans de nombreux cas, les organisations disposent de produits de sécurité de point de terminaison existants. Le strict minimum de chaque organisation aurait dû être une solution antivirus. Mais dans certains cas, une organisation peut également avoir déjà implanté une solution EDR.

Historiquement, le remplacement de n’importe quelle solution de sécurité était fastidieux et difficile à atteindre en raison des raccordements étroits dans la couche application et les dépendances de l’infrastructure. Toutefois, étant donné que Defender pour point de terminaison est intégré au système d’exploitation, il est désormais facile de remplacer des solutions tierces.

Choisissez le composant de Defender pour point de terminaison à utiliser et supprimez celles qui ne s’appliquent pas. Le tableau ci-dessous indique la commande recommandée par Microsoft pour la façon dont la suite de sécurité de point de terminaison doit être activée.

<br>

****

|Composant|Description|Classement des ordres d’adoption|
|---|---|---|
|Endpoint Detection & Response (EDR)|Les fonctionnalités de détection et de réponse des points de terminaison Defender pour point de terminaison fournissent des détections d’attaque avancées qui sont quasiment en temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces. <p> [En savoir plus.](/windows/security/threat-protection/windows-defender-atp/overview-endpoint-detection-response)|1|
|Gestion des vulnérabilités Microsoft Defender (MDVM)|Defender Vulnerability Management est un composant de Microsoft Defender pour point de terminaison et fournit aux administrateurs de sécurité et aux équipes des opérations de sécurité une valeur unique, notamment : <ul><li>Informations sur la détection et la réponse au point de terminaison en temps réel (EDR) corrélées avec les vulnérabilités de point de terminaison</li><li>Contexte de vulnérabilité d’appareil inestimable pendant les enquêtes sur les incidents</li><li>Processus de correction intégrés via Microsoft Intune et Microsoft System Center Configuration Manager</li></ul> <p> [En savoir plus](https://techcommunity.microsoft.com/t5/Windows-Defender-ATP/Introducing-a-risk-based-approach-to-threat-and-vulnerability/ba-p/377845).|2|
|Protection de nouvelle génération (NGP)|Microsoft Defender Antivirus est une solution anti-programme malveillant intégrée qui fournit une protection de nouvelle génération pour les ordinateurs de bureau, les ordinateurs portables et les serveurs. L’antivirus Microsoft Defender inclut les éléments suivants : <ul><li>Protection fournie par le cloud pour une détection et un blocage quasi instantanés des menaces nouvelles et émergentes. Tout comme l’apprentissage automatique et le système Intelligent Security Graph, la protection fournie par le cloud fait partie des technologies nouvelle génération intégrées à l’antivirus Microsoft Defender.</li><li>Analyse always on à l’aide de la surveillance avancée du comportement des fichiers et des processus et d’autres heuristiques (également appelées « protection en temps réel »).</li><li>Mises à jour de protection dédiées basées sur le Machine Learning, l’analyse du Big Data humaine et automatisée, ainsi que la recherche approfondie sur la résistance aux menaces.</li></ul> <p> [En savoir plus](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10).|3|
|Réduction de la surface d’attaque (ASR)|Les fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison aident à protéger les appareils et les applications de l’organisation contre les menaces nouvelles et émergentes. <br> [En savoir plus.](/windows/security/threat-protection/windows-defender-atp/overview-attack-surface-reduction)|4|
|Correction d'& d’investigation automatique (AIR)|Microsoft Defender pour point de terminaison utilise des investigations automatisées pour réduire considérablement le volume d’alertes qui doivent être examinées individuellement. La fonctionnalité d’investigation automatisée utilise différents algorithmes d’inspection et processus utilisés par les analystes (tels que les playbooks) pour examiner les alertes et prendre des mesures de correction immédiates pour résoudre les violations. Cela réduit considérablement les volumes d’alertes, ce qui permet aux experts en matière de sécurité de se concentrer sur des menaces plus sophistiquées et d’autres initiatives de grande valeur. <p> [En savoir plus.](/windows/security/threat-protection/windows-defender-atp/automated-investigations-windows-defender-advanced-threat-protection)|Non applicable|
|Spécialistes des menaces Microsoft (MTE)|Spécialistes des menaces Microsoft est un service de chasse managé qui fournit aux centres d’opérations de sécurité (SOC) une surveillance et une analyse de niveau expert pour les aider à s’assurer que les menaces critiques dans leurs environnements uniques ne sont pas manquées. <p> [En savoir plus.](/windows/security/threat-protection/windows-defender-atp/microsoft-threat-experts)|Non applicable|

## <a name="next-step"></a>Étape suivante

![Phase 2 : Installation.](images/setup.png) <br> [Phase 2 : configuration](production-deployment.md)

Configurez Microsoft Defender pour point de terminaison déploiement.
