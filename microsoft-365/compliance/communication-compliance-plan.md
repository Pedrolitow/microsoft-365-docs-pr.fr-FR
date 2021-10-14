---
title: Planifier la conformité des communications
description: Découvrez la planification de l’utilisation de la conformité des communications dans votre organisation.
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
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 8f6ca7e0b1996a7213eae0612f8b801b28514f50
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60335453"
---
# <a name="plan-for-communication-compliance"></a>Planifier la conformité des communications

Avant de commencer à mettre en place la conformité des [communications](communication-compliance.md) dans votre organisation, il existe d’importantes activités de planification et des considérations qui doivent être examinées par vos équipes de gestion des technologies de l’information et de la conformité. Une compréhension approfondie et la planification du déploiement dans les domaines suivants vous aideront à vous assurer que votre implémentation et l’utilisation des fonctionnalités de conformité des communications se déroulent sans problème et sont conformes aux meilleures pratiques pour la solution.

## <a name="transitioning-from-supervision-in-office-365"></a>Transition à partir de la surveillance dans Office 365

Pour les organisations qui utilisent des stratégies de surveillance dans Office 365, vous devez immédiatement planifier la transition vers les stratégies de conformité des communications dans Microsoft 365 et devez comprendre les points importants ci-après :

- La solution de surveillance dans Office 365 a été entièrement remplacée par la solution de conformité des communications dans Microsoft 365. Nous vous recommandons de créer de nouvelles stratégies de conformité des communications qui ont les mêmes paramètres que les stratégies de surveillance existantes pour utiliser les nouvelles améliorations d’examen et de correction.
- Les messages enregistrés sous surveillance dans Office 365 correspondances de stratégie ne peuvent pas être déplacés ou partagés dans la conformité des communications Microsoft 365.
- Pour les organisations avec les deux solutions utilisées côte à côte pendant le processus de transition, les stratégies utilisées dans chaque solution doivent avoir des noms de stratégie uniques. Les groupes et les dictionnaires de mots clés personnalisés peuvent être partagés entre les solutions pendant une période de transition.

Pour plus d’informations sur la surveillance dans Office 365, consultez la [feuille de route Microsoft 365 pour](https://www.microsoft.com/microsoft-365/roadmap) plus d’informations.

## <a name="work-with-stakeholders-in-your-organization"></a>Travailler avec les parties prenantes de votre organisation

Identifiez les parties prenantes appropriées de votre organisation à collaborer pour prendre des mesures sur les alertes de conformité des communications. Certaines parties prenantes recommandées à envisager, y compris dans la planification initiale et le flux de travail de conformité des [communications](communication-compliance.md#workflow) de bout en bout, sont les personnes des zones suivantes de votre organisation :

- Technologie de l’information
- Conformité
- Confidentialité
- Sécurité
- Ressources humaines
- Informations juridiques

## <a name="plan-for-the-investigation-and-remediation-workflow"></a>Planifier le flux de travail d’examen et de correction

### <a name="permissions"></a>Autorisations

Sélectionnez des parties prenantes dédiées pour surveiller et examiner les alertes et les cas à une cadence régulière dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com/). Assurez-vous de bien comprendre comment vous allez affecter des utilisateurs et des parties prenantes à différents groupes de rôles de conformité des communications au sein de votre organisation.

Il existe cinq groupes de rôles utilisés pour configurer les autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des** communications disponible en tant qu’option de menu dans  Centre de conformité Microsoft 365  et pour poursuivre ces étapes de configuration, vous devez être affecté aux groupes de rôles Conformité des communications ou Administrateur de la conformité des communications. Pour accéder aux fonctionnalités de conformité des communications et les gérer après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de conformité des communications.

> [!IMPORTANT]
> Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont requis pour que les fonctionnalités de conformité des communications soient accessibles.

Selon la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques. Vous pouvez choisir d’affecter des utilisateurs ayant différentes responsabilités de conformité à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés au groupe de rôles *Conformité* des communications. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles lors de la configuration de la conformité des communications :

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de se lancer rapidement dans la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis séparez les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupe de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées des messages (et non le contenu du message), passer à des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas Advanced eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

### <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la conformité des communications, vous devez déterminer qui a besoin de ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou groupes de personnes à superviser. Voici quelques exemples de ces groupes : Microsoft 365 groupes de distribution, Exchange listes de distribution basées sur des Yammer et des canaux Microsoft Teams réseau. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de l’analyse d’un groupe d’exclusion spécifique ou d’une liste de groupes. Pour plus d’informations sur les types de groupes pris en charge dans les stratégies de conformité des communications, voir [Prise en charge de la conformité des communications.](communication-compliance-configure.md#step-3-optional-set-up-groups-for-communication-compliance)

> [!IMPORTANT]
> Les utilisateurs couverts par les stratégies de conformité des communications doivent avoir une licence Microsoft 365 E5 Conformité, une licence Office 365 Entreprise E3 avec le module de conformité avancée ou être inclus dans un abonnement Office 365 Entreprise E5. Si vous n’avez pas de plan E5 Enterprise existant et que vous souhaitez essayer la conformité des communications, vous pouvez vous inscrire à une version d’essai Office 365 Entreprise [E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de conformité des communications, vous devez déterminer qui examine les messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou les groupes de personnes qui doivent réviser les communications contrôlées. Tous les réviseurs doivent avoir des boîtes aux lettres  hébergées sur Exchange Online et doivent être affectés aux rôles Analyse de conformité des communications ou Examen de la conformité *des* communications. Le rôle Gestion des cas de conformité  des communications doit également être attribué aux réviseurs (analystes ou enquêteurs). Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.

### <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs et les relecteurs supervisés

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de réviser leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé.

Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie surveille tous les messages électroniques de chaque utilisateur du groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie surveille tous les messages électroniques envoyés à ce groupe, et non les messages électroniques reçus par chaque membre du groupe.

L’ajout de groupes et de listes de distribution aux stratégies de conformité des communications fait partie des conditions globales et des règles définies. Par ailleurs, le nombre maximal de groupes et de listes de distribution pris en charge par une stratégie varie en fonction du nombre de conditions également ajoutées à la stratégie. Chaque stratégie doit prendre en charge environ 20 groupes ou listes de distribution, selon le nombre de conditions supplémentaires présentes dans la stratégie.

### <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs qui ont des correspondances de stratégie est importante et peut contribuer à promouvoir la fiabilité dans les examens d’analyse et d’examen des données pour les alertes de conformité des communications. Ce paramètre s’applique uniquement aux noms d’utilisateurs affichant la solution de conformité des communications. Cela n’affecte pas la façon dont les noms sont affichés dans d’autres solutions de conformité ou dans le Centre d’administration.

Pour les utilisateurs avec une correspondance de conformité des communications, vous pouvez choisir l’un des paramètres suivants dans les **paramètres** de conformité des communications :

- **Afficher les versions anonymisées** des noms d’utilisateur  : les noms d’utilisateur sont rendus anonymes pour empêcher les utilisateurs du groupe de rôles Analyste de conformité des communications de voir qui est associé aux alertes de stratégie. Les utilisateurs du groupe de rôles *Enquêteur de* conformité des communications voient toujours les noms d’utilisateur, et non les versions rendues anonymes. Par exemple, un utilisateur « Grace Grace » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans tous les domaines de l’expérience de conformité des communications. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans les détails de l’alerte de conformité des communications ne seront pas disponibles lorsque cette option sera choisie. Toutefois, les noms d’utilisateurs s’affichent lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelles ou passées.
- **N’affichez pas les versions rendues anonymes** des noms d’utilisateur : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelles et passées pour les alertes de conformité des communications. Les informations de profil utilisateur (nom, titre, alias et organisation ou service) s’affichent pour l’utilisateur pour toutes les alertes de conformité des communications.

## <a name="plan-for-policies"></a>Planifier les stratégies

La création de stratégies de conformité des communications est rapide et facile avec les [modèles prédéfinie](communication-compliance-policies.md#policy-templates) pour le langage choquant, les informations sensibles et la conformité réglementaire. Les stratégies de conformité des communications personnalisées permettent de détecter et d’enquêter les problèmes spécifiques à votre organisation et aux exigences.

Lorsque vous planifiez des stratégies de conformité des communications, prenez en compte les points suivants :

- Envisagez d’ajouter tous les utilisateurs de votre organisation dans le cadre de vos stratégies de conformité des communications. L’identification d’utilisateurs spécifiques comme étant dans l’étendue des stratégies individuelles est utile dans certains cas, mais la plupart des organisations doivent inclure tous les utilisateurs dans les stratégies de conformité des communications optimisées pour la détection du harcèlement ou de la discrimination.
- Configurez le pourcentage de communications à examiner à 100 % pour vous assurer que les stratégies capturent tous les problèmes problématiques dans les communications de votre organisation.
- Vous pouvez analyser les communications provenant de [sources](communication-compliance-channels.md#third-party-sources) tierces pour les données importées dans les boîtes aux lettres de Microsoft 365 organisation. Pour inclure la révision des communications dans ces plateformes, vous devez configurer un connecteur vers ces services avant que les messages qui rencontrent des conditions de stratégie soient surveillés par la stratégie de communication.
- Les stratégies peuvent prendre en charge les langues de surveillance autres que l’anglais dans les stratégies de conformité des communications personnalisées. Créez [un dictionnaire de](communication-compliance-policies.md#custom-keyword-dictionaries) mots clés personnalisé de mots choquants dans le langage de votre choix ou créez votre propre modèle d’apprentissage automatique à l’aide de classifieurs entraidables dans Microsoft 365. [](classifier-get-started-with.md)
- Toutes les organisations ont des normes de communication et des besoins en matière de stratégie différents. Surveillez les mots clés spécifiques à l’aide des conditions de stratégie de conformité des [communications](communication-compliance-policies.md#conditional-settings) ou surveillez les types spécifiques d’informations avec des types d’informations [sensibles personnalisés.](create-a-custom-sensitive-information-type.md)

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité des communications pour votre organisation Microsoft 365, voir Configurer la conformité des communications pour [Microsoft 365](communication-compliance-configure.md) ou consultez l’étude de cas pour [Contoso](communication-compliance-case-study.md) et la façon dont il a configuré rapidement une stratégie de conformité des communications pour surveiller les langages choquants dans les communications Microsoft Teams, Exchange Online et Yammer.
