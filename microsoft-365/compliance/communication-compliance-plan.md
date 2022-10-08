---
title: Planifier la conformité des communications
description: En savoir plus sur la planification de l’utilisation de la conformité des communications dans votre organisation.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: f491cbc346bf79824be782403b4ae3a7d54431a6
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68504015"
---
# <a name="plan-for-communication-compliance"></a>Planifier la conformité des communications

>[!IMPORTANT]
>Conformité des communications Microsoft Purview fournit les outils nécessaires pour aider les organisations à détecter les violations de conformité réglementaire (par exemple sec ou FINRA), telles que les informations sensibles ou confidentielles, le harcèlement ou la menace de langue, et le partage de contenu pour adultes. Créés avec la confidentialité par conception, les noms d’utilisateur sont pseudonymés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont choisis par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Avant de commencer à vous familiariser avec [la conformité des communications](/microsoft-365/compliance/communication-compliance) au sein de votre organisation, vos équipes de gestion des technologies de l’information et de la conformité doivent examiner les activités et considérations de planification importantes. Une bonne compréhension et une planification approfondies du déploiement dans les domaines suivants vous aideront à garantir que votre implémentation et votre utilisation des fonctionnalités de conformité des communications se déroulent correctement et sont alignées sur les meilleures pratiques pour la solution.

Pour plus d’informations et pour obtenir une vue d’ensemble du processus de planification visant à résoudre les problèmes de conformité et les activités à risque au sein de votre organisation, consultez [Démarrage d’un programme de gestion des risques internes](https://download.microsoft.com/download/b/2/0/b208282a-2482-4986-ba07-15a9b9286df0/pwc-starting-an-insider-risk-management-program-with-pwc-and-microsoft.pdf).

Vous pouvez également consulter la [vidéo Microsoft Mechanics](https://www.youtube.com/watch?v=Ynkfu8OF0wQ) sur la façon dont la gestion des risques internes et la conformité des communications fonctionnent ensemble pour réduire les risques liés aux données des utilisateurs de votre organisation.

> [!IMPORTANT]
> La conformité des communications est actuellement disponible dans les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances du service Azure. Pour vérifier que la conformité des communications est prise en charge pour votre organisation, consultez [la disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="transitioning-from-supervision-in-office-365"></a>Transition de la supervision dans Office 365

Pour les organisations qui utilisent des stratégies de supervision dans Office 365, vous devez immédiatement planifier la transition vers des stratégies de conformité des communications dans Microsoft Purview et comprendre les points importants suivants :

- La solution de supervision dans Office 365 a été entièrement remplacée par la solution de conformité des communications dans Microsoft Purview. Nous vous recommandons de créer des stratégies de conformité des communications qui ont les mêmes paramètres que les stratégies de supervision existantes pour utiliser les nouvelles améliorations apportées à l’examen et à la correction.
- Les messages enregistrés dans la supervision dans Office 365 correspondances de stratégie ne peuvent pas être déplacés ou partagés dans la conformité des communications.
- Pour les organisations avec les deux solutions utilisées côte à côte pendant le processus de transition, les stratégies utilisées dans chaque solution doivent avoir des noms de stratégie uniques. Les groupes et les dictionnaires de mots clés personnalisés peuvent être partagés entre les solutions pendant une période de transition.

Pour plus d’informations sur la mise hors service pour la supervision dans Office 365, consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour plus d’informations.

## <a name="work-with-stakeholders-in-your-organization"></a>Collaborer avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées de votre organisation pour collaborer pour prendre des mesures sur les alertes de conformité des communications. Certaines parties prenantes recommandées à envisager, notamment dans la planification initiale et le flux de travail de [conformité des communications](/microsoft-365/compliance/communication-compliance#workflow) de bout en bout, sont des personnes des domaines suivants de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planifier le flux de travail d’investigation et de correction

### <a name="permissions"></a>Autorisations

Sélectionnez des parties prenantes dédiées pour examiner et examiner les alertes et les cas à une cadence régulière dans le [portail de conformité Microsoft Purview](https://compliance.microsoft.com/). Veillez à comprendre comment vous allez affecter des utilisateurs et des parties prenantes à différents groupes de rôles de conformité des communications dans votre organisation.

> [!IMPORTANT]
> Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Six groupes de rôles sont utilisés pour configurer les autorisations initiales pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des communications** disponible en tant qu’option de menu dans portail de conformité Microsoft Purview et pour poursuivre ces étapes de configuration, vous devez être affecté à l’un des rôles ou groupes de rôles suivants :

- Rôle [*Administrateur général*](/azure/active-directory/roles/permissions-reference#global-administrator) Azure Active Directory
- Rôle [*Administrateur de conformité*](/azure/active-directory/roles/permissions-reference#compliance-administrator) Azure Active Directory
- portail de conformité Microsoft Purview groupe [*de rôles Gestion de l’organisation*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- groupe de [*rôles administrateur de conformité*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portail de conformité Microsoft Purview
- *Groupe de rôles Conformité des communications*
- *Groupe de rôles Administration conformité des communications*

Les membres des rôles suivants disposent des mêmes autorisations de solution incluses dans le groupe de rôles *Administration conformité* des communications :

- *Administrateur général* Azure Active Directory
- *Administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* portail de conformité Microsoft Purview
- *Administrateur de conformité* portail de conformité Microsoft Purview

> [!IMPORTANT]
> Assurez-vous d’avoir toujours au moins un utilisateur dans les groupes de *rôles Conformité* des communications ou Conformité des communications *Administration* (selon l’option que vous choisissez) afin que votre configuration de conformité des communications n’accède pas à un scénario « zéro administrateur » si des utilisateurs spécifiques quittent votre organisation.

Selon la façon dont vous souhaitez gérer les stratégies et les alertes de conformité des communications, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de conformité des communications. Vous avez la possibilité d’affecter des utilisateurs ayant des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles *Conformité des communications* . Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles de solution lors de la configuration et de la gestion de la conformité des communications :

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration est le moyen le plus simple de prendre rapidement en main la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications et, plus tard, pour séparer les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des attributions de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies à l’endroit où ils sont affectés en tant que réviseurs, afficher les métadonnées de message (et non le contenu du message), effectuer une escalade vers des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas eDiscovery (Premium), envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

### <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la conformité des communications, vous devez déterminer qui a besoin de ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou groupes de personnes à superviser. Voici quelques exemples de ces groupes : Groupes Microsoft 365, les listes de distribution Exchange, les communautés Yammer et les canaux Microsoft Teams. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de l’analyse d’un groupe d’exclusion spécifique ou d’une liste de groupes. Pour plus d’informations sur les types de groupes pris en charge dans les stratégies de conformité des communications, consultez [Prise en main de la conformité des communications](/microsoft-365/compliance/communication-compliance-configure#step-3-optional-set-up-groups-for-communication-compliance).

> [!IMPORTANT]
> Les utilisateurs couverts par les stratégies de conformité des communications doivent disposer d’une licence Microsoft 365 E5 Conformité, d’une licence Office 365 Entreprise E3 avec le module complémentaire Conformité avancée ou être inclus dans un abonnement Office 365 Entreprise E5. Si vous n’avez pas de plan Entreprise E5 existant et que vous souhaitez essayer la conformité des communications, vous pouvez vous [inscrire à une version d’évaluation de Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de conformité des communications, vous devez déterminer qui examine les messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou les groupes de personnes qui doivent réviser les communications contrôlées. Tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online, être affectés aux groupes de *rôles Analyste de conformité des communications* ou *Enquêteur de conformité des communications* et être affectés dans la stratégie à examiner. Lorsque les réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les avertit de l’attribution à la stratégie et fournit des liens vers des informations sur le processus de révision.

### <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs supervisés et les réviseurs

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de passer en revue leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé. Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie détecte tous les e-mails de chaque utilisateur du groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie détecte tous les e-mails envoyés à ce groupe, et non les e-mails individuels reçus par chaque membre du groupe.

L’ajout de groupes et de listes de distribution aux stratégies de conformité des communications fait partie des conditions générales et des règles définies. Par conséquent, le nombre maximal de groupes et de listes de distribution pris en charge par une stratégie varie en fonction du nombre de conditions également ajoutées à la stratégie. Chaque stratégie doit prendre en charge environ 20 groupes ou listes de distribution, en fonction du nombre de conditions supplémentaires présentes dans la stratégie.

Utilisez le graphique suivant pour vous aider à configurer des groupes dans votre organisation pour les stratégies de conformité des communications :

| **Membre de stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs exclus | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie <br> Groupes Microsoft 365 avec appartenance dynamique |
| Relecteurs | Aucun | Groupes de distribution <br> Groupes de distribution dynamique <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie |

### <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs qui ont des correspondances de stratégie est importante et peut contribuer à promouvoir l’objectivité dans les examens d’analyse et d’investigation des données pour les alertes de conformité des communications. Ce paramètre s’applique uniquement aux noms d’utilisateurs affichés dans la solution de conformité des communications. Cela n’affecte pas la façon dont les noms sont affichés dans d’autres solutions de conformité ou dans le Centre d’administration.

Pour les utilisateurs ayant une correspondance de conformité des communications, vous pouvez choisir l’un des paramètres suivants dans les **paramètres de conformité des communications** :

- **Afficher les versions anonymes des noms d’utilisateur** : les noms d’utilisateur sont anonymes pour empêcher les utilisateurs du groupe de *rôles Analyste de conformité des communications* de voir qui est associé aux alertes de stratégie. Les utilisateurs du groupe de *rôles Enquêteur de conformité des communications* voient toujours les noms d’utilisateur, et non les versions anonymes. Par exemple, un utilisateur « Grace Taylor » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans tous les domaines de l’expérience de conformité des communications. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans les détails de l’alerte de conformité des communications ne sont pas disponibles lorsque cette option est choisie. Toutefois, les noms d’utilisateur sont affichés lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateurs s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelles ou passées.
- **Ne pas afficher les versions anonymes des noms d’utilisateur** : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelles et passées pour les alertes de conformité des communications. Les informations de profil utilisateur (nom, titre, alias et organisation ou service) s’affichent pour l’utilisateur pour toutes les alertes de conformité des communications.

## <a name="plan-for-policies"></a>Planifier des stratégies

La création de stratégies de conformité des communications est rapide et facile avec les [modèles prédéfinis](/microsoft-365/compliance/communication-compliance-policies#policy-templates) pour le contenu inapproprié, les informations sensibles et la conformité réglementaire. Les stratégies de conformité des communications personnalisées permettent de détecter et d’examiner les problèmes spécifiques à votre organisation et aux exigences.

Lorsque vous planifiez des stratégies de conformité des communications, tenez compte des domaines suivants :

- Envisagez d’ajouter tous les utilisateurs de votre organisation comme inclus dans l’étendue de vos stratégies de conformité des communications. L’identification d’utilisateurs spécifiques comme inclus dans l’étendue des stratégies individuelles est utile dans certaines circonstances, mais la plupart des organisations doivent inclure tous les utilisateurs dans des stratégies de conformité des communications optimisées pour la détection du harcèlement ou de la discrimination.
- Configurez le pourcentage de communications à examiner à 100 % pour vous assurer que les stratégies interceptent tous les problèmes de préoccupation dans les communications de votre organisation.
- Vous pouvez analyser les communications de [sources tierces](/microsoft-365/compliance/communication-compliance-channels#third-party-sources) à la recherche de données importées dans des boîtes aux lettres de votre organisation Microsoft 365. Pour inclure la révision des communications dans ces plateformes, vous devez configurer un connecteur à ces services avant que les messages répondant aux conditions de stratégie soient détectés par la stratégie de communication.
- Les stratégies peuvent prises en charge la détection de langues autres que l’anglais dans les stratégies de conformité des communications personnalisées. Créez un [dictionnaire de mots clés personnalisé](/microsoft-365/compliance/communication-compliance-policies#custom-keyword-dictionaries) de mots offensants dans la langue de votre choix ou créez votre propre modèle Machine Learning à l’aide de [classifieurs pouvant être formés](/microsoft-365/compliance/classifier-get-started-with) dans Microsoft 365.
- Toutes les organisations ont des normes de communication et des besoins de stratégie différents. Détecter des mots clés spécifiques à l’aide de [conditions](/microsoft-365/compliance/communication-compliance-policies#conditional-settings) de stratégie de conformité des communications ou détecter des types d’informations spécifiques avec des [types d’informations sensibles personnalisés](/microsoft-365/compliance/create-a-custom-sensitive-information-type).

## <a name="creating-a-communication-compliance-policy-walkthrough"></a>Procédure pas à pas pour créer une stratégie de conformité des communications

Vous souhaitez voir une procédure détaillée de configuration d’une nouvelle stratégie de conformité des communications et de correction d’une alerte ? Regardez la vidéo suivante de 15 minutes pour voir une démonstration de la façon dont les stratégies de conformité des communications peuvent vous aider à détecter les messages inappropriés, à examiner les violations potentielles et à corriger les problèmes de conformité.
<br>
<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RWNchy]
<br>

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité des communications pour votre organisation Microsoft 365, consultez [Configurer la conformité des communications](/microsoft-365/compliance/communication-compliance-configure) ou consultez l’étude de [cas pour Contoso](/microsoft-365/compliance/communication-compliance-case-study) et la façon dont elle a rapidement configuré une stratégie de conformité des communications pour détecter le contenu inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer.
