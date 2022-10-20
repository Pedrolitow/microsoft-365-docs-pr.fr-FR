---
title: Planifier la gestion des risques Insider
description: Découvrez comment planifier l’utilisation des stratégies de gestion des risques internes dans votre organisation.
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- tier1
- purview-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: e5243e403ffb110a2c7c1559869ae194c3e110a8
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621227"
---
# <a name="plan-for-insider-risk-management"></a>Planifier la gestion des risques Insider

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou involontaires, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Créés avec la confidentialité par conception, les utilisateurs sont pseudonymes par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Avant de commencer à gérer [les risques internes](insider-risk-management.md) au sein de votre organisation, vos équipes de gestion des technologies de l’information et de la conformité doivent examiner d’importantes activités et considérations de planification. Une compréhension et une planification approfondies du déploiement dans les domaines suivants vous aideront à vous assurer que votre implémentation et votre utilisation des fonctionnalités de gestion des risques internes se déroulent correctement et sont alignées sur les meilleures pratiques pour la solution. 

Pour plus d’informations et une vue d’ensemble du processus de planification pour traiter les activités à risque au sein de votre organisation, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Regardez la vidéo ci-dessous pour découvrir comment le flux de travail de gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir des risques tout en hiérarchisant les valeurs, la culture et l’expérience utilisateur de votre organisation :
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

Regardez la [vidéo Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) sur la façon dont la gestion des risques internes et la conformité des communications fonctionnent ensemble pour réduire les risques liés aux données des utilisateurs de votre organisation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="work-with-stakeholders-in-your-organization"></a>Collaborer avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées de votre organisation pour collaborer pour prendre des mesures sur les alertes et les cas de gestion des risques internes. Certaines parties prenantes recommandées à prendre en compte, notamment dans la planification initiale et le flux de travail de [gestion des risques internes](insider-risk-management.md#workflow) de bout en bout, sont des personnes issues des domaines suivants de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="determine-any-regional-compliance-requirements"></a>Déterminer les exigences régionales de conformité

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité différentes des autres domaines de votre organisation. Collaborez avec les parties prenantes dans ces domaines pour s’assurer qu’elles comprennent les contrôles de conformité et de confidentialité dans la gestion des risques internes et comment elles doivent être utilisées dans différents domaines de votre organisation. Dans certains scénarios, les exigences de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou limitent certaines parties prenantes des enquêtes et des cas en fonction du cas d’un utilisateur ou des exigences réglementaires ou de stratégie pour le domaine.

Si vous avez des exigences pour que des parties prenantes spécifiques soient impliquées dans des enquêtes de cas impliquant des utilisateurs dans certaines régions, rôles ou divisions, vous pouvez implémenter des [stratégies de gestion des risques internes distinctes](insider-risk-management-policies.md) (même si identiques) ciblant les différentes régions et populations. Cette configuration permettra aux parties prenantes appropriées de trier et de gérer plus facilement les cas pertinents pour leurs rôles et régions. En outre, vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les réviseurs parlent la même langue que les utilisateurs afin de simplifier le processus d’escalade pour les alertes et les cas de gestion des risques internes.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’examen

Selon la façon dont vous souhaitez gérer les stratégies et alertes de gestion des risques internes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez la possibilité d’affecter des utilisateurs ayant des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de gestion des risques internes. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles Insider Risk Management. Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Vous choisirez parmi ces options de groupe de rôles et actions de solution lorsque vous travaillez avec la gestion des risques internes :

|**Actions**|**Gestion des risques internes**|**Administration de gestion des risques internes**|**Analystes de la gestion des risques internes.**|**Enquêteurs sur la gestion des risques internes.**|**Auditeurs de gestion des risques internes**|**Approbateurs de gestion des risques internes**|
|---|---|---|---|---|---|---|
|Configurer des stratégies et des paramètres|Oui|Oui|Non|Non|Non|Non|
|Access Analytics Insights|Oui|Oui|Oui|Non|Non|Non|
|Accéder & examiner les alertes|Oui|Non|Oui|Oui|Non|Non|
|Accès & examiner les cas|Oui|Non|Oui|Oui|Non|Non|
|Accéder & afficher l’Explorateur de contenu|Oui|Non|Non|Oui|Non|Non|
|Configurer des modèles d’avis|Oui|Non|Oui|Oui|Non|Non|
|Afficher & exporter les journaux d’audit|Oui|Non|Non|Non|Oui|Non|
|Accès & afficher les captures de preuves légales|Oui|Non|Non|Oui|Non|Non|
|Créer une demande de capture de preuves légales|Oui|Oui|Non|Non|Non|Non|
|Approuver les demandes de capture de preuves légales|Oui|Non|Non|Non|Non|Oui|
|Afficher le rapport d’intégrité de l’appareil|Oui|Oui|Non|Non|Non|Non|

>[!IMPORTANT]
>Assurez-vous d’avoir toujours au moins un utilisateur dans les groupes de *rôles Insider Risk Management* ou *Insider Risk Management Administration* (selon l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’accède pas à un scénario « zéro administrateur » si des utilisateurs spécifiques quittent votre organisation.

Les membres des rôles suivants peuvent affecter des utilisateurs à des groupes de rôles de gestion des risques internes et disposer des mêmes autorisations de solution que le groupe de rôles *Insider Risk Management Administration* :

- *Administrateur général* Azure Active Directory
- *Administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* portail de conformité Microsoft Purview
- *Administrateur de conformité* portail de conformité Microsoft Purview

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

Selon la façon dont vous envisagez d’implémenter des stratégies de gestion des risques internes, vous devez disposer des abonnements de licences Microsoft 365 appropriés et comprendre et planifier certains prérequis de solution.

**Licences:** La gestion des risques internes est disponible dans le cadre d’une large sélection d’abonnements aux licences Microsoft 365. Pour plus d’informations, consultez l’article [de prise en main de la gestion des risques internes](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances du service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez [la disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas de plan Microsoft 365 Entreprise E5 et que vous souhaitez essayer la gestion des risques internes, vous pouvez [ajouter Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire à une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 Entreprise E5.

**Exigences du modèle de stratégie :** Selon le modèle de stratégie que vous choisissez, il existe des exigences que vous devez comprendre et planifier avant de configurer la gestion des risques internes dans votre organisation :

- Lorsque vous utilisez le **modèle De vol de données en quittant le modèle d’utilisateurs** , vous devez configurer un connecteur Rh Microsoft 365 pour importer régulièrement les informations de date de résiliation et de résiliation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.
- Lorsque vous utilisez des modèles de **fuite de données**, vous devez configurer au moins une stratégie de Protection contre la perte de données Microsoft Purview (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risque interne pour les alertes de stratégie DLP à gravité élevée. Pour obtenir des conseils détaillés sur la configuration de stratégies DLP pour votre organisation, consultez l’article [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md).
- Lorsque vous utilisez des modèles de violation de stratégie **de sécurité**, vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans le Centre de sécurité Defender pour importer des alertes de violation de la sécurité. Pour obtenir des instructions pas à pas pour activer l’intégration de Defender pour point de terminaison à la gestion des risques internes, consultez [Configurer les fonctionnalités avancées dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Lorsque vous utilisez des modèles **utilisateur mécontents** , vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement des informations d’état de performances ou de rétrogradation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des conseils détaillés pour configurer le connecteur Microsoft 365 RH au sein de votre organisation.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer la solution à grande échelle dans votre environnement de production, vous pouvez envisager de tester les stratégies auprès d’un petit ensemble d’utilisateurs de production tout en effectuant les vérifications de conformité, de confidentialité et juridiques nécessaires dans votre organisation. L’évaluation de la gestion des risques internes dans un environnement de test nécessite la génération d’actions utilisateur simulées et d’autres signaux pour créer des alertes pour le triage et les cas à traiter. Cette approche n’étant pas pratique pour la plupart des organisations, il est préférable de tester la gestion des risques internes avec un petit groupe d’utilisateurs dans un environnement de production.

Conservez la fonctionnalité d’anonymisation dans les paramètres de stratégie activés pour anonymiser les noms d’affichage des utilisateurs dans la console de gestion des risques internes pendant ce test afin de préserver la confidentialité au sein de l’outil. Ce paramètre permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et peut contribuer à promouvoir l’objectivité dans les examens d’analyse et d’investigation des données pour les alertes de risque interne.

Si vous ne voyez aucune alerte immédiatement après la configuration d’une stratégie de gestion des risques internes, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Un bon moyen de vérifier si la stratégie est déclenchée et fonctionne comme prévu consiste à voir si l’utilisateur est dans l’étendue de la stratégie sur la page **Utilisateurs** .

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation sur la gestion des risques internes avec les parties prenantes de votre organisation qui sont incluses dans votre flux de travail de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les activités de risques internes](insider-risk-management-activities.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu à risque interne](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Prêt à configurer la gestion des risques internes pour votre organisation ? Passez en revue les articles suivants :

- [Commencez à utiliser les paramètres de gestion des risques internes](insider-risk-management-settings.md) pour configurer les paramètres de stratégie globale.
- [Prise en main de la gestion des risques internes](insider-risk-management-configure.md) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
- [Commencez à utiliser les preuves légales de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) pour obtenir des instructions pas à pas pour configurer la capture de preuves légales dans votre organisation.
