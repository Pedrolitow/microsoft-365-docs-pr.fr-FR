---
title: 'Microsoft 365 Entreprise ressources de gestion des ressources : architecture de cybersécurité'
description: Découvrez comment surmonter les défis liés à la sécurité dans l’architecture Enterprise Microsoft à partir de Kozeta Contrôle, architecte de cybersécurité chez Microsoft.
ms.author: bcarter
author: brendacarter
manager: bcarter
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- M365solutions
ms.custom: seo-marvel-jun2020
f1.keywords: NOCSH
ms.openlocfilehash: 3ce1715baaf9b23fe53d900d67fc378d8fa624bb
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58568203"
---
# <a name="security-hurdles-you-can-sail-overone-architects-viewpoint"></a>Les obstacles à la sécurité que vous pouvez surmonter : l’opinion d’un architecte

Dans cet article, [Kozeta Contrôle,](https://www.linkedin.com/in/kozeta-garrett-53013a6/)architecte en cybersécurité chez Microsoft, décrit les principaux défis en matière de sécurité qu’elle rencontre au niveau des organisations d’entreprise et recommande des approches pour s’en sortir.

## <a name="about-the-author"></a>À propos de l’auteur

![Photo Kozeta Stock.](../media/solutions-architecture-center/kozeta-garrett-security.jpg)

En tant qu’architecte de sécurité cloud, j’ai travaillé avec plusieurs organisations pour fournir des conseils stratégiques et techniques sur la conception et l’implémentation de l’architecture de sécurité pour les clients qui migrent vers Microsoft 365 et Azure, qui développent des solutions de sécurité d’entreprise et contribuent à transformer l’architecture et la culture de sécurité pour la résilience de l’entreprise. Mon expérience inclut la détection et la réponse aux incidents, l’analyse des programmes malveillants, les tests de pénétration et la recommandation d’améliorations en matière de sécurité et de défense informatiques. Je suis très passionné par les transformations de pointe qui entraînent la sécurité en tant qu’enableur pour l’entreprise, y compris les efforts de modernisation.

Il a été très satisfaisant de voir comment les organisations qui ont adopté un état d’esprit de modernisation de la sécurité au cours des deux dernières années sont dans une excellente position qui leur permet de continuer à fonctionner à distance de manière sécurisée, malgré la situation récente du COVID-19. Malheureusement, ces circonstances ont également servi d’appel de veille pour certains clients, qui n’étaient pas prêts pour ce besoin immédiat. De nombreuses organisations réalisent qu’elles doivent se moderniser rapidement, retirer leur dette de sécurité informatique cumulée et améliorer leur posture de sécurité du jour au lendemain afin de pouvoir fonctionner dans des circonstances extrêmement inhabituelles.

La bonne nouvelle est que Microsoft a organisé des ressources importantes pour aider les organisations à augmenter rapidement leur posture de sécurité. En plus de ces ressources, j’aime partager les principaux défis que j’ai rencontrés quotidiennement avec les clients dans le but d’être confronté à ces obstacles.

Je vis actuellement dans le Nord du Nord, près de la ville de Washington, la capitale de notre pays. J’aime presque toutes les formes d’activités extérieures et d’exercices, comme la course à pied, la course à pied, la course à pied et la loisirs. Pour faire face à ces problèmes, j’aime autant la cuisine, la cuisine que les voyages.

## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Travailler en partenariat avec l’équipe de sécurité dès le début de l’adoption du cloud

Pour commencer, je ne peux pas mettre suffisamment l’accent sur l’importance que les équipes de votre organisation se coordonnent depuis le début. Les équipes de sécurité doivent être adoptées en tant que partenaires essentiels lors des premières étapes de conception et d’adoption du cloud. Cela implique l’intégration des équipes de sécurité en tant que champion de l’adoption du cloud, non seulement pour les fonctionnalités ajoutées à l’entreprise (telles qu’une excellente expérience utilisateur à partir d’appareils mobiles sécurisés, d’applications de fonctionnalités complètes ou pour créer de la valeur sur les données d’entreprise au-delà des applications de messagerie et de productivité limitées), mais aussi pour tirer parti des fonctionnalités de stockage, d’IA et d’analyse informatique qui permettent de résoudre les défis de sécurité nouveaux et anciens. Les équipes de sécurité doivent être incluses dans la gestion de tous les aspects de cette transition, y compris les personnes (culture), les processus (formation) et la technologie pour réussir. Cela implique également d’investir dans la modernisation et l’amélioration continue du Centre des opérations de sécurité (SOC). Travaillez ensemble pour aligner votre stratégie de sécurité avec votre stratégie d’entreprise et les tendances de votre environnement afin de vous assurer que la transformation numérique est effectuée en toute sécurité. Lorsque cela est bien fait, les organisations développent la possibilité de s’adapter plus rapidement aux modifications, y compris aux modifications apportées à l’entreprise, aux services informatiques et à la sécurité.

L’endroit où je vois les clients s’en aller le plus souvent, c’est lorsqu’il n’y a pas de partenariat réel entre les opérations et les équipes SOC. Bien que l’équipe des opérations soit sous pression et chargée d’adopter le cloud à l’aide d’échéances très élevées, les équipes de sécurité ne sont pas toujours incluses au début du processus pour réviser et planifier une stratégie de sécurité complète. Cela implique l’intégration de différents composants et composants cloud sur site. Ce manque de partenariat se complique davantage pour les différentes équipes qui semblent travailler en silos pour implémenter des contrôles pour leurs composants spécifiques, ce qui complique davantage l’implémentation, la résolution des problèmes et l’intégration.

Les clients qui s’emploient à ces difficultés ont de bons partenariats entre les équipes d’exploitation et de gouvernance et de gestion de la sécurité et des risques pour remanier la stratégie de sécurité et les conditions requises pour la protection des charges de travail cloud hybrides. Ils se concentrent sur les objectifs et résultats de sécurité ultimes : la protection des données et la disponibilité des systèmes et des services conformément aux exigences de gouvernance, de risque et de conformité en matière de cybersécurité. Ces organisations développent des partenariats précoces entre leur équipe d’exploitation et de gouvernance et SOC, ce qui est essentiel à l’approche de conception de la sécurité et qui optimisera la valeur de leurs investissements.

## <a name="build-a-modern-identity-based-security-perimeter"></a>Créer un périmètre de sécurité moderne (basé sur l’identité)

Ensuite, adoptez une approche d’architecture de confiance zéro. Cela commence par la création d’un périmètre de sécurité moderne basé sur l’identité. Concevez l’architecture de sécurité dans laquelle chaque tentative d’accès, qu’elle soit locale ou cloud, est traitée comme non vérifiée jusqu’à ce qu’elle soit vérifiée : « ne jamais faire confiance, toujours vérifier ». Cette approche de conception augmente non seulement la sécurité et la productivité, mais elle permet également aux utilisateurs de travailler n’importe où avec n’importe quel type d’appareil. Les contrôles cloud sophistiqués inclus Microsoft 365 vous aident à protéger les identités des utilisateurs tout en contrôlant l’accès aux ressources précieuses en fonction du niveau de risque des utilisateurs.

Pour une configuration recommandée, voir [Configurations d’identité et d’accès aux appareils.](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="transition-security-controls-to-the-cloud"></a>Transition des contrôles de sécurité vers le cloud

De nombreuses équipes de sécurité utilisent toujours les meilleures pratiques de sécurité traditionnelles conçues pour un monde local, notamment la gestion d’une « sécurité de périmètre réseau » et la tentative de « forcer » les outils et contrôles de sécurité sur site aux solutions cloud. Ces contrôles n’ont pas été conçus pour le cloud, sont inefficaces et empêchent l’adoption des fonctionnalités cloud modernes. Les processus et les outils qui fonctionnent pour une approche de sécurité de périmètre de réseau se sont révélés inefficaces, s’avèrent efficaces pour les fonctionnalités cloud et ne permettent pas de tirer parti des fonctionnalités de sécurité modernes et automatisées.

Vous pouvez faire face à cette difficulté en déplaçant les stratégies de défense vers la protection gérée par le cloud, l’examen et la correction automatisés, le test automatisé du stylet, Defender pour Office 365 et l’analyse des incidents. Les clients qui utilisent des solutions de gestion d’appareils modernes ont implémenté une gestion automatisée, une correction normalisée, un antivirus, une application de stratégie et une protection des applications sur tous les appareils (qu’il s’agit d’un smartphone, d’un ordinateur personnel, d’un ordinateur portable ou d’une tablette). Cela élimine la nécessité d’un VPN, de Microsoft System Center Configuration Manager (SCCM) et de stratégies de groupe Active Directory. Cela, combiné aux stratégies d’accès conditionnel, offre un contrôle et une visibilité puissants, ainsi qu’un accès simplifié aux ressources, quel que soit l’endroit d’où leurs utilisateurs opèrent.

## <a name="strive-for-best-together-security-tools"></a>Recherchez des outils de sécurité « meilleurs ensemble »

Une autre difficulté pour les clients est la prise d’une approche « de premier choix » pour les outils de sécurité. La superposition continue de solutions de point de qualité pour répondre aux besoins de sécurité émergentes entraîne une panne de la sécurité de l’entreprise. Même avec les meilleures intentions, les outils de la plupart des environnements ne sont pas intégrés, car ils deviennent trop coûteux et complexes. Cela, à son tour, crée des lacunes dans la visibilité, car il existe plus d’alertes à trier que l’équipe ne peut gérer. La formation de l’équipe SecOps sur les nouveaux outils devient également un défi constant.

L’approche « simple est préférable » fonctionne également pour la sécurité. Au lieu d’utiliser les outils « les plus puissants » , préférez cette difficulté en adoptant une stratégie de « meilleure collaboration » avec des outils qui fonctionnent ensemble par défaut. Les fonctionnalités de sécurité Microsoft protègent l’ensemble de votre organisation avec une protection intégrée contre les menaces qui englobe les applications, les utilisateurs et les nuages. L’intégration permet à une organisation d’être plus résiliente et de réduire les risques en contenant les attaquants à l’entrée et en remédiant rapidement aux attaques.

## <a name="balance-security-with-functionality"></a>Trouver un équilibre entre sécurité et fonctionnalité

À mesure que je suis issu d’une longue expérience et d’une longue expérience en matière de cybersécurité, j’ai tendance à préférer commencer par la configuration la plus sécurisée et permettre aux organisations d’relâcher les configurations de sécurité en fonction de leurs besoins opérationnels et de sécurité. Toutefois, cela peut se faire au prix d’une perte de fonctionnalités et d’une expérience utilisateur médiocre. Comme de nombreuses organisations l’ont appris, si la sécurité est trop difficile pour les utilisateurs, elles trouveront un moyen de vous contourner, y compris l’utilisation de services cloud nonmanagés. Aussi difficile que cela soit à accepter, je réalise que l’équilibre entre fonctionnalités et sécurité doit être atteint.

Les organisations qui réalisent que les utilisateurs feront tout ce qu’il faut pour réaliser leurs tâches, elles reconnaissent que le « shadow IT en question » ne vaut pas la peine d’être en conflit. Ils reconnaissent que les employés de l’équipe de l’équipe de sécurité sont les plus importants en matière de shadow it et d’utilisation d’applications SaaS non approuvées pour leur travail. Ils ont déplacé leur stratégie pour encourager son utilisation (plutôt que la suppression) et se concentrer sur la réduction de l’exposition aux risques qu’elle pourrait créer. Les équipes de sécurité de l’organisation n’ont pas à dire que tout est bloqué, journalisé et envoyé par le biais d’un proxy inverse ou d’un VPN. Au lieu de cela, ces équipes de sécurité doublent leurs efforts pour protéger les données précieuses et sensibles contre l’exposition aux mauvaises parties ou applications malveillantes. Ils s’emploient à protéger l’intégrité des données. Ils utilisent pleinement des fonctionnalités de protection des informations cloud plus avancées, notamment le chiffrement, l’authentification multifacteur sécurisée, les risques et la conformité automatisés et les fonctionnalités de Sécurité des applications cloud Broker (CASB), tout en permettant et en encourageant même le partage protégé sur plusieurs plateformes. Ils transforment les technologies de l’ombre en créativité, productivité et collaboration, ce qui permet à leur entreprise de rester sur le marché.

## <a name="adopt-a-methodical-approach"></a>Adopter une approche méthodique

La plupart des défis auxquels j’ai été confronté lors de l’implémentation de la sécurité cloud au niveau de différentes organisations, quel que soit le secteur, ont été très similaires. Tout d’abord, bien qu’il existe une documentation complète sur des fonctionnalités et fonctionnalités spécifiques, il existe une certaine confusion au niveau de l’organisation quant à ce qui s’applique à ces fonctionnalités, à l’endroit où les fonctionnalités de sécurité se chevauchent et à la façon dont les fonctionnalités doivent être intégrées. Il existe également un niveau d’incertitude quant aux fonctionnalités de sécurité pré-configurées et qui nécessitent une configuration par l’organisation. En outre, les équipes SOC n’ont malheureusement pas eu l’exposition complète, la formation ou l’allocation budgétaire nécessaire pour se préparer à l’adoption rapide du cloud et à la transformation numérique que leurs organisations subissent déjà.

Pour vous aider à effacer ces obstacles, Microsoft a organisé plusieurs ressources conçues pour vous aider à prendre une approche méthodique de votre stratégie de sécurité et de votre implémentation.

|Ressource   |Plus d’informations  |
|---------|---------|
|[Principales tâches pour les équipes de sécurité qui prennent en charge le travail à domicile](../security/top-security-tasks-for-remote-work.md)      | Si vous vous retrouvez soudainement à prendre en charge un personnel qui travaille principalement à domicile, cet article vous aide à augmenter rapidement la sécurité. Il inclut les principales tâches recommandées en fonction de votre plan de gestion des licences.    |
|[Microsoft 365 Sécurité pour les décideurs d’entreprise](../security/Microsoft-365-security-for-bdm.md)    | Lorsque vous avez le temps de planifier un plan plus complet, cet article inclut des recommandations qui couvrent Microsoft 365, hiérarchisées par surface d’attaque. Il est même livré avec une feuille de calcul que vous pouvez utiliser pour trier les licences et le domaine (par exemple, identité, protection contre les menaces et surveillance).  |
|[Recommandations en matière d’architecture de sécurité Microsoft](/security/compass/compass)    | Si vous êtes architecte de sécurité, assurez-vous de voir les recommandations de sécurité organisées par domaine, y compris les opérations d’identité, de mise en réseau et de sécurité.   |
|[Recommandations en matière d’opérations de sécurité Microsoft](/security/compass/security-operations-videos-and-decks)|Découvrez les recommandations de Microsoft pour la configuration et l’exécution d’un centre des opérations de sécurité (SOC) |
|[Formation à l’atelier du directeur général de la sécurité des informations (CISO)](/security/ciso-workshop/ciso-workshop)   | Si vous débutez avec la sécurité cloud, ne manquez pas cette série de vidéos.        |
|[docs.security.com/security](/security/)    | Conseils techniques de Microsoft pour la stratégie et l’architecture de sécurité.        |
| | |

Toutes ces ressources sont conçues pour être utilisées comme point de départ et adaptées aux besoins de votre organisation.