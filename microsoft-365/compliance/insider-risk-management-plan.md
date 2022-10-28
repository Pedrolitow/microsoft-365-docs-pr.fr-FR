---
title: Planifier la gestion des risques Insider
description: Découvrez comment planifier l’utilisation de stratégies de gestion des risques internes dans votre organisation.
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
ms.openlocfilehash: 6c49afa544e72110ff6646fc68f6ea3da498547d
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68767648"
---
# <a name="plan-for-insider-risk-management"></a>Planifier la gestion des risques Insider

> [!IMPORTANT]
> Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Avant de commencer à utiliser [la gestion des risques internes](insider-risk-management.md) dans votre organisation, il existe des activités de planification et des considérations importantes qui doivent être examinées par vos équipes de gestion des technologies de l’information et de la conformité. Une compréhension et une planification approfondies du déploiement dans les domaines suivants vous aideront à garantir que votre implémentation et votre utilisation des fonctionnalités de gestion des risques internes se déroule sans problème et s’aligne sur les meilleures pratiques. 

Pour plus d’informations et une vue d’ensemble du processus de planification pour traiter les activités à risque dans votre organisation, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Regardez la vidéo ci-dessous pour découvrir comment le workflow de gestion des risques internes peut aider votre organisation à prévenir, détecter et contenir les risques tout en hiérarchisant les valeurs, la culture et l’expérience utilisateur de votre organisation :


>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OUXB]

Regardez la [vidéo Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) sur la façon dont la gestion des risques internes et la conformité des communications fonctionnent ensemble pour réduire les risques liés aux données des utilisateurs de votre organisation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="work-with-stakeholders-in-your-organization"></a>Collaborer avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées dans votre organisation pour collaborer pour prendre des mesures sur les alertes et les cas de gestion des risques internes. Certaines parties prenantes recommandées à envisager d’inclure dans la planification initiale et le [workflow de gestion des risques internes](insider-risk-management.md#workflow) de bout en bout sont des personnes des domaines suivants de votre organisation :

- Technologies de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="determine-any-regional-compliance-requirements"></a>Déterminer les exigences de conformité régionales

Différentes zones géographiques et organisationnelles peuvent avoir des exigences de conformité et de confidentialité différentes des autres zones de votre organisation. Collaborez avec les parties prenantes dans ces domaines pour vous assurer qu’elles comprennent les contrôles de conformité et de confidentialité dans la gestion des risques internes et comment ils doivent être utilisés dans différents domaines de votre organisation. Dans certains scénarios, les exigences de conformité et de confidentialité peuvent nécessiter des stratégies qui désignent ou restreignent certaines parties prenantes des enquêtes et des cas en fonction du cas d’un utilisateur ou des exigences réglementaires ou stratégiques pour le domaine.

Si vous avez des exigences pour que des parties prenantes spécifiques soient impliquées dans des enquêtes de cas impliquant des utilisateurs dans certaines régions, rôles ou divisions, vous pouvez implémenter des [stratégies de gestion des risques internes](insider-risk-management-policies.md) distinctes (même si identiques) ciblant les différentes régions et populations. Cette configuration permet aux bonnes parties prenantes de trier et de gérer plus facilement les cas pertinents pour leurs rôles et régions. Vous pouvez envisager de créer des processus et des stratégies pour les régions où les enquêteurs et les réviseurs parlent la même langue que les utilisateurs, ce qui peut simplifier le processus d’escalade des alertes et des cas de gestion des risques internes.

## <a name="plan-for-the-review-and-investigation-workflow"></a>Planifier le flux de travail de révision et d’examen

Selon la façon dont vous souhaitez gérer les stratégies et les alertes de gestion des risques internes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de gestion des risques internes. Vous avez la possibilité d’affecter des utilisateurs avec des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines des fonctionnalités de gestion des risques internes. Vous pouvez également décider d’attribuer tous les comptes d’utilisateur des administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles Gestion des risques internes. Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Choisissez parmi les options de groupe de rôles et les actions de solution suivantes lors de l’utilisation de la gestion des risques internes :

|**Actions**|**Gestion des risques internes**|**Administration de gestion des risques internes**|**Analystes de la gestion des risques internes.**|**Enquêteurs sur la gestion des risques internes.**|**Auditeurs de gestion des risques internes**|**Approbateurs de gestion des risques internes**|
|---|---|---|---|---|---|---|
|Configurer des stratégies et des paramètres|Oui|Oui|Non|Non|Non|Non|
|Accéder aux insights d’analyse|Oui|Oui|Oui|Non|Non|Non|
|Accéder aux alertes et les examiner|Oui|Non|Oui|Oui|Non|Non|
|Accéder aux cas et les examiner|Oui|Non|Oui|Oui|Non|Non|
|Accéder à l’Explorateur de contenu et l’afficher|Oui|Non|Non|Oui|Non|Non|
|Configurer des modèles de notification|Oui|Non|Oui|Oui|Non|Non|
|Afficher et exporter les journaux d’audit|Oui|Non|Non|Non|Oui|Non|
|Accéder aux captures de preuves d’investigation et les afficher|Oui|Non|Non|Oui|Non|Non|
|Créer une demande de capture de preuves forensiques|Oui|Oui|Non|Non|Non|Non|
|Approuver les demandes de capture de preuves forensiques|Oui|Non|Non|Non|Non|Oui|
|Afficher le rapport d’intégrité de l’appareil|Oui|Oui|Non|Non|Non|Non|

> [!IMPORTANT]
> Assurez-vous que vous avez toujours au moins un utilisateur dans les groupes de rôles *Gestion des risques internes* ou *Gestion des risques internes Administration* (en fonction de l’option que vous choisissez) afin que votre configuration de gestion des risques internes n’accède pas à un scénario « administrateur zéro » si des utilisateurs spécifiques quittent votre organisation.

Les membres des rôles suivants peuvent affecter des utilisateurs à des groupes de rôles de gestion des risques internes et disposer des mêmes autorisations de solution que celles incluses dans le groupe *de rôles Gestion des risques internes Administration* :

- *Administrateur général* Azure Active Directory
- *Administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* portail de conformité Microsoft Purview
- *Administrateur de conformité* portail de conformité Microsoft Purview

## <a name="understand-requirements-and-dependencies"></a>Comprendre les exigences et les dépendances

Selon la façon dont vous prévoyez d’implémenter des stratégies de gestion des risques internes, vous devez disposer des abonnements de licence Microsoft 365 appropriés et comprendre et planifier certaines conditions préalables à la solution.

**Licences:** La gestion des risques internes est disponible dans le cadre d’un large choix d’abonnements de licence Microsoft 365. Pour plus d’informations, consultez l’article [Prise en main de la gestion des risques internes](insider-risk-management-configure.md#subscriptions-and-licensing) .

> [!IMPORTANT]
> La gestion des risques internes est actuellement disponible dans les locataires hébergés dans des régions et des pays géographiques pris en charge par les dépendances de service Azure. Pour vérifier que la gestion des risques internes est prise en charge pour votre organisation, consultez [Disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas d’offre Microsoft 365 Entreprise E5 existante et que vous souhaitez essayer la gestion des risques internes, vous pouvez [ajouter Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire à un essai](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 Entreprise E5.

**Exigences du modèle de stratégie :** Selon le modèle de stratégie que vous choisissez, vous devez être sûr de comprendre les exigences suivantes et de planifier en conséquence avant de configurer la gestion des risques internes dans votre organisation :

- Lorsque vous utilisez le modèle **Vol de données par des utilisateurs sortants** , vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement les informations de date de démission et d’arrêt pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur Microsoft 365 HR.
- Lorsque vous utilisez le modèle **Fuites de données**, vous devez configurer au moins une stratégie Protection contre la perte de données Microsoft Purview (DLP) pour définir des informations sensibles dans votre organisation et recevoir des alertes de risque interne pour les alertes de stratégie DLP de gravité élevée. Consultez l’article [Créer, tester et régler une stratégie DLP](create-test-tune-dlp-policy.md) pour obtenir des instructions détaillées sur la configuration des stratégies DLP.
- Lorsque vous utilisez le modèle **de violation de stratégie de sécurité**, vous devez activer Microsoft Defender pour point de terminaison pour l’intégration de la gestion des risques internes dans Defender Security Center pour importer les alertes de violation de sécurité. Pour obtenir des instructions pas à pas pour activer l’intégration de Defender pour point de terminaison à la gestion des risques internes, consultez [Configurer des fonctionnalités avancées dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/advanced-features).
- Lorsque vous utilisez le modèle **d’utilisateur à risque** , vous devez configurer un connecteur Microsoft 365 HR pour importer régulièrement les informations d’état de performances ou de rétrogradation pour les utilisateurs de votre organisation. Consultez l’article [Importer des données avec le connecteur RH](import-hr-data.md) pour obtenir des instructions détaillées sur la configuration du connecteur Microsoft 365 HR.

## <a name="test-with-a-small-group-of-users-in-a-production-environment"></a>Tester avec un petit groupe d’utilisateurs dans un environnement de production

Avant d’activer cette solution à grande échelle dans votre environnement de production, vous devez envisager de tester les stratégies avec un petit ensemble d’utilisateurs de production tout en effectuant les révisions de conformité, de confidentialité et juridiques nécessaires dans votre organisation. L’évaluation de la gestion des risques internes dans un environnement de test nécessite que vous génériez des actions utilisateur simulées et d’autres signaux pour créer des alertes pour le triage et des cas à traiter. Cette approche n’étant peut-être pas pratique pour de nombreuses organisations, nous vous recommandons de tester la gestion des risques internes avec un petit groupe d’utilisateurs dans un environnement de production.

Conservez la fonctionnalité d’anonymisation dans les paramètres de stratégie activée pour rendre anonymes les noms d’affichage des utilisateurs dans la console de gestion des risques internes pendant ce test afin de maintenir la confidentialité au sein de l’outil. Ce paramètre permet de protéger la confidentialité des utilisateurs qui ont des correspondances de stratégie et peut contribuer à promouvoir l’objectivité dans les examens d’analyse et d’investigation des données pour les alertes de risque interne.

Si vous ne voyez aucune alerte immédiatement après la configuration d’une stratégie de gestion des risques internes, cela peut signifier que le seuil de risque minimal n’a pas encore été atteint. Consultez la page **Utilisateurs** pour vérifier que la stratégie est déclenchée et fonctionne comme prévu et pour voir si les utilisateurs sont dans l’étendue de la stratégie.

## <a name="resources-for-stakeholders"></a>Ressources pour les parties prenantes

Partagez la documentation de gestion des risques internes avec les parties prenantes de votre organisation qui sont incluses dans votre workflow de gestion et de correction :

- [Créer et gérer les stratégies de risques internes](insider-risk-management-policies.md)
- [Identifier les activités de risques internes](insider-risk-management-activities.md)
- [Agir sur les cas de risques internes](insider-risk-management-cases.md)
- [Examiner les données de cas avec l’Explorateur de contenu à risque interne](insider-risk-management-content-explorer.md)
- [Créer des modèles d’avertissement sur les risques internes](insider-risk-management-notices.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Vous êtes prêt à configurer la gestion des risques internes pour votre organisation ? Nous vous recommandons de consulter les articles suivants :

- [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md) pour configurer les paramètres de stratégie globaux.
- [Prise en main de la gestion des risques internes](insider-risk-management-configure.md) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
- [Prise en main des preuves forensiques de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) pour obtenir des instructions pas à pas pour configurer la capture de preuves forensiques dans votre organisation.
