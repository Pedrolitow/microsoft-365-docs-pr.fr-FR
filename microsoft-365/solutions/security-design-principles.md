---
title: planification des ressources Microsoft 365 Entreprise - Architecture de la cybersécurité
description: Découvrez comment surmonter les défis de sécurité dans l’architecture Microsoft Enterprise à partir de KozetaRet, architecte en cybersécurité chez Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: aefce57eb633f028768ee5a4a2ae8591e6dc9c13
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67983121"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>Obstacles à la sécurité que vous pouvez franchir : point de vue d’un architecte

Dans cet article, [KozetaRet](https://www.linkedin.com/in/kozeta-garrett-53013a6/), architecte en cybersécurité chez Microsoft, décrit les principaux défis de sécurité qu’elle rencontre au sein d’organisations d’entreprise et recommande des approches pour surmonter ces obstacles.

## <a name="about-the-author"></a>À propos de l’auteur

![Photo de KozetaRet.](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

En tant qu’architecte de sécurité cloud, j’ai travaillé avec plusieurs organisations pour fournir des conseils stratégiques et techniques axés sur la conception et l’implémentation de l’architecture de sécurité pour les clients qui migrent vers Microsoft 365 et Azure, le développement de solutions de sécurité d’entreprise et la transformation de l’architecture et de la culture de sécurité pour la résilience de l’entreprise. Mon expérience comprend la détection et la réponse aux incidents, l’analyse des programmes malveillants, les tests d’intrusion et la recommandation d’améliorations de la sécurité informatique et de la posture de défense. Je suis passionné par les transformations de pointe qui se traduisent par la sécurité comme un outil pour l’entreprise, y compris les efforts de modernisation.

Il a été très satisfaisant de voir comment les organisations qui ont adopté un état d’esprit de modernisation de la sécurité au cours des deux dernières années sont dans une excellente position qui leur permet de continuer à fonctionner à distance de manière sécurisée, malgré la situation récente du COVID-19. Malheureusement, ces circonstances ont également servi de rappel pour certains clients, qui n’étaient pas prêts à répondre à ce besoin immédiat. De nombreuses organisations se rendent compte qu’elles doivent se moderniser rapidement, mettre hors service leur dette de sécurité informatique accumulée et améliorer leur posture de sécurité du jour au lendemain afin de pouvoir fonctionner dans ces circonstances extrêmement inhabituelles.

La bonne nouvelle est que Microsoft a organisé des ressources exceptionnelles pour aider les organisations à augmenter rapidement leur posture de sécurité. En plus de ces ressources, je voudrais partager les principaux défis que j’ai rencontrés avec les clients quotidiennement dans l’espoir que vous pouvez naviguer sur ces obstacles.

Je vis actuellement en Virginie du Nord, près de la capitale de notre pays, Washington DC. J’aime à peu près toutes les formes d’activités de plein air et d’exercice, comme la course, le vélo, la randonnée et la natation. Pour contrer ces j’aime tout autant la cuisine, les aliments gastronomiques, et les voyages.

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Collaborer avec l’équipe Sécurité dès le début de l’adoption du cloud

Pour commencer, je ne peux pas souligner à quel point il est important que les équipes de votre organisation se coordonnent dès le départ. Les équipes de sécurité doivent être adoptées en tant que partenaires critiques dans les premières étapes de l’adoption et de la conception du cloud. Cela signifie que les équipes de sécurité sont intégrées pour favoriser l’adoption du cloud, non seulement pour les fonctionnalités ajoutées à l’entreprise (telles qu’une expérience utilisateur optimale à partir d’appareils mobiles sécurisés, d’applications complètes ou de création de valeur sur les données d’entreprise au-delà des applications de messagerie et de productivité limitées), mais aussi pour tirer parti des fonctionnalités de stockage, d’IA et d’analytique informatique qui aident à résoudre les nouveaux et anciens défis de sécurité. Les équipes de sécurité doivent être incluses dans la gestion de tous les aspects de ce changement, y compris les personnes (culture), les processus (formation) et la technologie pour réussir. Cela implique également d’investir dans la modernisation et l’amélioration continue du Centre des opérations de sécurité (SOC). Collaborez pour aligner votre stratégie de sécurité avec les tendances de votre stratégie d’entreprise et de l’environnement afin de garantir que la transformation numérique est effectuée en toute sécurité. Lorsque cela est bien fait, les organisations développent la possibilité de s’adapter plus rapidement aux changements, y compris les modifications apportées à l’entreprise, à l’informatique et à la sécurité.

Là où je vois les clients se déplacer sur les obstacles le plus, c’est quand il n’y a pas de véritable partenariat entre les opérations et les équipes SOC. Alors que l’équipe des opérations est contrainte et mandatée avec des délais serrés pour adopter le cloud, les équipes de sécurité ne sont pas toujours incluses au début du processus pour réviser et planifier une stratégie de sécurité complète. Cela implique l’intégration locale de différents composants et composants cloud. Ce manque de partenariat se complique davantage pour les différentes équipes qui semblent travailler en silos pour implémenter des contrôles pour leurs composants spécifiques, ce qui entraîne une complexité supplémentaire de l’implémentation, de la résolution des problèmes et de l’intégration.

Les clients qui naviguent sur ces obstacles ont de bons partenariats entre les équipes d’exploitation et de gouvernance et les équipes de gestion de la sécurité et des risques pour réorganiser la stratégie de sécurité et les exigences de protection des charges de travail cloud hybrides. Ils se concentrent au laser sur les objectifs de sécurité et les résultats ultimes : la protection des données et la disponibilité des systèmes et des services conformément aux exigences de gouvernance, de risque et de conformité en matière de cybersécurité. Ces organisations développent des partenariats précoces entre leur équipe des opérations et de la gouvernance et SOC, qui est essentielle à l’approche de conception de la sécurité et maximisera la valeur de leurs investissements.

## <a name="build-a-modern-identity-based-security-perimeter"></a>Créer un périmètre de sécurité moderne (basé sur l’identité)

Ensuite, adoptez une approche d’architecture Confiance nulle. Cela commence par la création d’un périmètre de sécurité moderne basé sur l’identité. Concevez l’architecture de sécurité dans laquelle chaque tentative d’accès, locale ou cloud, est traitée comme non approuvée jusqu’à ce qu’elle soit vérifiée : « ne jamais faire confiance, toujours vérifier ». Cette approche de conception augmente non seulement la sécurité et la productivité, mais permet également aux utilisateurs de travailler n’importe où avec n’importe quel type d’appareil. Les contrôles cloud sophistiqués inclus avec Microsoft 365 vous aident à protéger les identités des utilisateurs tout en contrôlant l’accès aux ressources précieuses en fonction du niveau de risque utilisateur.

Pour obtenir une configuration recommandée, consultez [Les configurations d’identité et d’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="transition-security-controls-to-the-cloud"></a>Transition des contrôles de sécurité vers le cloud

De nombreuses équipes de sécurité utilisent toujours les meilleures pratiques de sécurité traditionnelles conçues pour un monde local, notamment le maintien d’une « sécurité de périmètre réseau » et la tentative de « forcer » les outils et contrôles de sécurité locaux aux solutions cloud. Ces contrôles n’ont pas été conçus pour le cloud, sont inefficaces et entravent l’adoption des fonctionnalités cloud modernes. Les processus et les outils qui fonctionnent pour une approche de sécurité de périmètre réseau se sont avérés inefficaces, ne permettent pas de tirer parti des fonctionnalités de sécurité modernes et automatisées.

Vous pouvez surmonter cet obstacle en transférant les stratégies de défense vers la protection gérée par le cloud, l’investigation et la correction automatisées, les tests de stylet automatisés, les Defender pour Office 365 et l’analyse des incidents. Les clients qui utilisent des solutions modernes de gestion des appareils ont implémenté la gestion automatisée, la mise à jour corrective standardisée, l’antivirus, l’application de stratégies et la protection des applications sur tous les appareils (qu’il s’agisse d’un smartphone, d’un ordinateur personnel, d’un ordinateur portable ou d’une tablette). Cela élimine la nécessité d’un VPN, de Microsoft System Center Configuration Manager (SCCM) et de stratégies de groupe Active Directory. Ceci, combiné à des stratégies d’accès conditionnel, offre un contrôle et une visibilité puissants, ainsi qu’un accès simplifié aux ressources, quel que soit l’endroit d’où opèrent leurs utilisateurs.

## <a name="strive-for-best-together-security-tools"></a>S’efforcer d’obtenir des outils de sécurité « meilleurs ensemble »

Un autre obstacle que je vois les clients trébucher est d’adopter une approche « meilleure de race » pour les outils de sécurité. La superposition continue de solutions de point « best of breed » pour répondre aux besoins de sécurité émergents entraîne l’arrêt de la sécurité de l’entreprise. Même avec les meilleures intentions, les outils de la plupart des environnements ne sont pas intégrés, car ils deviennent trop coûteux et complexes. Cela crée à son tour des lacunes de visibilité, car il y a plus d’alertes à trier que l’équipe ne peut gérer. Le réentraînement de l’équipe SecOps sur de nouveaux outils devient également un défi constant.

L’approche « simple est mieux » fonctionne également pour la sécurité. Au lieu d’aller après les outils « best of breed », naviguez au-dessus de cet obstacle en adoptant une stratégie « best together » avec des outils qui fonctionnent ensemble par défaut. Les fonctionnalités de sécurité Microsoft protègent l’ensemble de votre organisation avec une protection intégrée contre les menaces qui couvre les applications, les utilisateurs et les clouds. L’intégration permet à une organisation d’être plus résiliente et de réduire les risques en contenant les attaquants à l’entrée et en corrigeant rapidement les attaques.

## <a name="balance-security-with-functionality"></a>Équilibrer la sécurité avec les fonctionnalités

Comme je viens d’un arrière-plan et d’une longue expérience en cybersécurité, j’ai tendance à préférer commencer par la configuration la plus sécurisée et permettant aux organisations d’assouplir les configurations de sécurité en fonction de leurs besoins opérationnels et de sécurité. Toutefois, cela peut se faire à un prix élevé de fonctionnalités perdues et d’une mauvaise expérience utilisateur. Comme de nombreuses organisations l’ont appris, si la sécurité est trop difficile pour les utilisateurs, elles trouveront un moyen de vous contourner, notamment en utilisant des services cloud non managés. Aussi difficile que cela soit pour moi d’accepter, je me suis rendu compte que l’équilibre délicat entre fonctionnalité et sécurité doit être atteint.

Les organisations qui réalisent que les utilisateurs feront tout ce qu’il faut pour accomplir leur travail reconnaissent que la « bataille de l’informatique fantôme » ne vaut pas la peine de se battre. Ils reconnaissent que les employés informatiques sont les plus grands délinquants en ce qui concerne l’informatique fantôme et l’utilisation d’applications SaaS non approuvées pour leur travail. Ils ont changé leur stratégie pour encourager son utilisation (au lieu de supprimer) et se concentrer sur l’atténuation des risques qu’elle pourrait créer. Les équipes de sécurité de ces organisations n’insistent pas pour que tout soit bloqué, journalisé et envoyé via un proxy inverse ou un VPN. Au lieu de cela, ces équipes de sécurité doublent leurs efforts pour protéger les données précieuses et sensibles contre l’exposition à des parties ou des applications malveillantes incorrectes. Ils fonctionnent pour protéger l’intégrité des données. Ils utilisent pleinement des fonctionnalités de protection des informations cloud plus avancées, notamment le chiffrement, l’authentification multifacteur sécurisée, les risques et la conformité automatisés, ainsi que les fonctionnalités de service de sécurité d’accès cloud (CASB), tout en autorisant et même encourageant le partage protégé entre plusieurs plateformes. Ils transforment l’informatique fantôme en créativité, productivité et collaboration inspirantes, ce qui permet à leur entreprise de rester à l’avant-garde de la concurrence.

## <a name="adopt-a-methodical-approach"></a>Adopter une approche méthodique

La plupart des défis que j’ai rencontrés lors de l’implémentation de la sécurité cloud auprès de différentes organisations, quel que soit l’industrie, ont été très similaires. Tout d’abord, bien qu’il existe une grande documentation sur des fonctionnalités et fonctionnalités spécifiques, il existe un niveau de confusion au niveau de l’organisation quant à ce qui s’applique à ces fonctionnalités, où les fonctionnalités de sécurité se chevauchent et comment les fonctionnalités doivent être intégrées. Il existe également un niveau d’incertitude quant aux fonctionnalités de sécurité qui sont préconfigurées et qui nécessitent une configuration par l’organisation. En outre, les équipes soc n’ont malheureusement pas eu l’exposition complète, la formation ou l’allocation budgétaire nécessaire pour préparer l’adoption rapide du cloud et la transformation numérique de leurs organisations sont déjà en cours.

Pour vous aider à surmonter ces obstacles, Microsoft a organisé plusieurs ressources conçues pour vous aider à adopter une approche méthodique de votre stratégie de sécurité et de votre implémentation.

|Ressource   |Plus d’informations  |
|---------|---------|
|[Principales tâches pour les équipes de sécurité qui prennent en charge le télétravail](../security/top-security-tasks-for-remote-work.md)      | Si vous vous retrouvez soudainement à soutenir une main-d’œuvre essentiellement professionnelle à la maison, cet article vous aide à augmenter rapidement la sécurité. Il inclut les principales tâches recommandées en fonction de votre plan de licences.    |
|[Plan de déploiement zéro trust Microsoft 365](../security/microsoft-365-zero-trust.md)    | Cet article fournit un plan de déploiement pour créer Confiance nulle sécurité avec Microsoft 365. Il inclut une affiche téléchargeable que vous pouvez utiliser pour suivre votre progression. |
|[Centre d’aide sur la confiance zéro](/security/zero-trust/)  | Découvrez le modèle de sécurité Confiance nulle, ses principes et comment implémenter une architecture Confiance nulle à l’aide des plans de déploiement. |
|[docs.security.com/security](/security/)    | Conseils techniques de Microsoft pour la stratégie et l’architecture de sécurité.        |
| | |

Toutes ces ressources sont conçues pour être utilisées comme point de départ et adaptées aux besoins de votre organisation.
