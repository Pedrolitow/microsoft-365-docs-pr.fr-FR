---
title: Obstacles de sécurité que vous pouvez parcourir — point de vue d’un architecte
description: Description.
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
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: cdb6b557bf2f46a2338d929547167cf89a048695
ms.sourcegitcommit: 0f71042edc7c3a7f10a7b92e1943abf51532cbf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "46522276"
---
# <a name="security-hurdles-you-can-sail-over--one-architects-viewpoint"></a>Obstacles de sécurité que vous pouvez parcourir — point de vue d’un architecte

Dans cet article, [Kozeta Garrett](https://www.linkedin.com/in/kozeta-garrett-53013a6/), Cybersecurity Architect chez Microsoft, décrit les principaux défis de sécurité qu’elle rencontre dans les organisations d’entreprise et recommande des approches pour parcourir ces obstacles. 

## <a name="about-the-author"></a>À propos de l’auteur

![Photo Garrett Kozeta](../media/solutions-architecture-center/kozeta-garrett-security.jpg) 

Dans mon rôle en tant qu’architecte de la sécurité dans le Cloud, j’ai travaillé avec plusieurs organisations pour fournir des conseils stratégiques et techniques sur la conception et l’implémentation de l’architecture de sécurité pour les clients qui migrent vers Microsoft 365 et Azure, développant des solutions de sécurité d’entreprise, et qui contribuent à transformer l’architecture de sécurité et la culture pour la résilience d’entreprise. Mon expérience inclut la détection d’incidents, l’analyse des programmes malveillants, le test de pénétration et la recommandation d’améliorations en matière de sécurité informatique et de défense. Je suis très passionné par les transformations de pointe qui se traduisent par une clé de sécurité pour l’entreprise, y compris les efforts de modernisation.

Il a été le plus satisfait pour voir comment les organisations qui ont adopté une mentalité de la modernisation de la sécurité au cours des deux dernières années sont en bonne position, ce qui leur permet de continuer à fonctionner à distance de manière sécurisée, malgré la dernière COVID-19. Malheureusement, ces circonstances ont également servi d’appel de réactivation pour certains clients qui n’étaient pas prêts pour ce besoin immédiat. De nombreuses organisations se rendent compte qu’elles doivent moderniser rapidement, retirer leur dette de sécurité informatique accumulée et améliorer leur sécurité la nuit pour qu’elles puissent fonctionner dans ces circonstances extrêmement inhabituelles.

La bonne nouvelle est que Microsoft a rassemblé des ressources intéressantes pour aider les organisations à renforcer rapidement leur position de sécurité. En plus de ces ressources, j’aimerais partager les principaux défis que j’ai rencontrés quotidiennement par les clients dans l’espoir que vous puissiez parcourir ces obstacles.

Je suis actuellement en Virginie du Nord, près du capital de notre pays, Washington DC. J’adore chaque forme d’activités et d’exercices extérieurs, comme l’exécution, le biroi, le randonnée et la natation. Pour contrer ces éléments, je profite de la cuisine, des épiceries et des voyages. 


## <a name="partner-with-the-security-team-from-the-start-of-cloud-adoption"></a>Partenariat avec l’équipe de sécurité depuis le début de l’adoption du Cloud

Pour commencer, je ne peux pas insister sur l’importance de la coordination des équipes de votre organisation à partir du début. Les équipes de sécurité doivent être adoptées en tant que partenaires critiques dans les premières étapes de l’adoption et de la conception dans le Cloud. Cela signifie que les équipes de sécurité doivent être à l’origine de l’adoption de Cloud, non seulement pour les fonctionnalités ajoutées à l’entreprise (telles que l’expérience utilisateur des appareils mobiles sécurisés, les applications de fonctionnalités complètes ou la création de valeur sur les données d’entreprise au-delà des applications de messagerie et de productivité limitées), mais aussi pour tirer parti des fonctionnalités de stockage, de protection des Les équipes de sécurité doivent être incluses dans la gestion de tous les aspects de cette équipe, y compris les personnes (culture), les processus (formation) et la technologie pour réussir. Cela signifie également que vous investissez dans la modernisation et l’amélioration continue du centre d’opérations sécurité (SOC). Collaborez pour aligner votre stratégie de sécurité avec vos besoins en matière de stratégie et d’environnement afin de garantir la réalisation de la transformation numérique de manière sécurisée. Une fois cette opération terminée, les organisations développent la capacité d’adaptation plus rapide aux modifications, y compris les modifications apportées à l’entreprise, à l’informatique et à la sécurité. 

Où je vois les clients qui traversent les obstacles le plus souvent lorsqu’il n’y a aucun partenariat réel entre les opérations et les équipes SOC. Tandis que l’équipe des opérations est soumise à une pression et qu’elle est soumise à des délais serrés pour adopter le Cloud, les équipes de sécurité ne sont pas toujours incluses dès le début du processus pour réviser et planifier une stratégie de sécurité complète. Cela implique l’intégration de différents composants de Cloud ainsi que des composants sur-local. Ce manque de partenariat est encore plus important pour les différentes équipes qui semblent fonctionner dans des silos pour mettre en œuvre des contrôles pour leurs composants spécifiques, ce qui entraîne une complexité accrue de la mise en œuvre, de la résolution des problèmes et de l’intégration.

Les clients qui battent ces obstacles ont de bonnes partenariats entre les opérations et la gouvernance, ainsi que les équipes de gestion de la sécurité et des risques pour réutiliser la stratégie et les exigences de sécurité pour la protection des charges de travail de Cloud hybride. Ils se concentrent sur les objectifs et les résultats de sécurité de pointe, à savoir la protection des données et la disponibilité des systèmes et services conformément aux exigences de gouvernance, de risque et de conformité d’Cybersecurity. Ces organisations développent des partenariats précoces entre leurs opérations et l’équipe de gouvernance et la société sociale qui est essentielle à l’approche de conception de la sécurité et optimise la valeur de leurs investissements. 

## <a name="build-a-modern-identity-based-security-perimeter"></a>Créer un périmètre de sécurité moderne (basé sur une identité)

Ensuite, adoptez une approche de l’architecture sans approbation. Cela commence par la création d’un périmètre de sécurité moderne basé sur l’identité. Concevez l’architecture de sécurité où chaque tentative d’accès, qu’elle soit local ou Cloud, est considérée comme non approuvée jusqu’à ce qu’elle soit vérifiée, « ne jamais approuver, toujours vérifier ». Cette approche de conception non seulement augmente la sécurité et la productivité, mais elle permet également aux utilisateurs de travailler n’importe où avec n’importe quel type d’appareil. Les contrôles de Cloud élaborés fournis avec Microsoft 365 vous aident à protéger les identités des utilisateurs tout en contrôlant l’accès aux ressources utiles en fonction du niveau de risque de l’utilisateur.

Pour obtenir une configuration recommandée, consultez la rubrique [configuration de l’accès aux identités et aux appareils](../enterprise/microsoft-365-policies-configurations.md). 

## <a name="transition-security-controls-to-the-cloud"></a>Basculer les contrôles de sécurité vers le Cloud

De nombreuses équipes de sécurité utilisent toujours les meilleures pratiques de sécurité traditionnelles créées pour tout le monde local, y compris la maintenance d’une « sécurité de périmètre réseau » et la tentative de « forcer » les outils et les contrôles de sécurité sur local vers des solutions Cloud. Ces contrôles n’ont pas été conçus pour le Cloud, sont inefficaces et entravent l’adoption de fonctionnalités de Cloud modernes. Les processus et les outils qui fonctionnent pour une approche de sécurité du périmètre réseau ont prouvé qu’ils ne sont pas efficaces, ce qui permet de tirer parti des fonctionnalités de sécurité modernes et automatisées.

Vous pouvez parler de cette difficulté en décalant les stratégies de défense vers la protection gérée sur le Cloud, l’analyse et la correction automatisées, le test de stylet automatisé, la protection avancée contre les menaces et l’analyse des incidents. Les clients qui utilisent des solutions de gestion des appareils modernes ont mis en œuvre une gestion automatisée, une mise à jour standardisée, un antivirus, une application de stratégie et une protection des applications sur tous les périphériques (smartphone, ordinateur personnel, ordinateur portable ou tablette). Cela élimine la nécessité de recourir à un VPN, à Microsoft System Center Configuration Manager (SCCM) et aux stratégies de groupe Active Directory. Ceci, combiné à des stratégies d’accès conditionnel, offre un contrôle et une visibilité puissants, ainsi qu’un accès simplifié aux ressources, quel que soit l’emplacement d’utilisation de leurs utilisateurs.

## <a name="strive-for-best-together-security-tools"></a>S’efforcer des outils de sécurité « de meilleure qualité »

Un autre obstacle à ce que je vois les clients Stumble sur l’une des meilleures approches des outils de sécurité. En continuant à superposer les solutions de point de « meilleures performances » pour répondre aux besoins émergents en matière de sécurité, la sécurité de l’entreprise est dégradation. Même avec les meilleures intentions, les outils dans la plupart des environnements ne sont pas intégrés, car il devient trop onéreux et complexe. Cela crée, à son tour, des intervalles de visibilité dans la mesure où il y a plus d’alertes à trier que l’équipe ne peut gérer. La nouvelle formation l’équipe SECOPS sur de nouveaux outils devient également un défi constant.

L’approche « simple est meilleure » fonctionne également pour la sécurité. Au lieu de passer des outils « meilleurs résultats », naviguez sur ce seuil en adoptant une stratégie « de meilleure qualité » avec des outils qui fonctionnent ensemble par défaut. Les fonctionnalités de sécurité de Microsoft protègent toute votre organisation avec une protection intégrée contre les menaces qui s’étend sur les applications, les utilisateurs et les nuages. L’intégration permet à une organisation d’être plus résiliente et de réduire les risques en contenant des attaquants à l’entrée et en corrigeant rapidement les attaques.

## <a name="balance-security-with-functionality"></a>Équilibrer la sécurité avec les fonctionnalités

Comme je provient d’un arrière-plan et d’une expérience Cybersecurity long, je préfère commencer par la configuration la plus sécurisée et permettre aux organisations de assouplir les configurations de sécurité en fonction de leurs besoins opérationnels et de sécurité. Toutefois, cela peut prendre un prix Hefty de perte de fonctionnalité et d’expérience utilisateur médiocre. Comme de nombreuses organisations ont appris, si la sécurité est trop difficile pour les utilisateurs, elles trouveront un moyen de vous contourner, notamment à l’aide de services Cloud non gérés. Comme je suis difficile d’accepter, j’ai conscience que la fonctionnalité délicate-bilan de sécurité doit être atteint.

Les organisations qui réalisent des utilisateurs effectueront toutes les opérations nécessaires pour faire en sorte que le « cliché instantané de la bataille » ne mérite pas de combattre. Elles reconnaissent que les employés informatiques sont les plus grands contrevenants lorsqu’il s’agit de les occulter et de l’utilisation d’applications SaaS non approuvées pour leur travail. Elles ont déplacé leur stratégie afin d’encourager son utilisation (au lieu de supprimer) et de se concentrer sur la limitation de l’exposition aux risques qu’elle pourrait créer. Les équipes de sécurité de cette organisation n’insistent pas sur le fait que tout est bloqué, journalisé et envoyé par le biais d’un proxy inverse ou d’un VPN. Au lieu de cela, ces équipes de sécurité doublent leurs efforts pour protéger les données importantes et sensibles d’être exposées aux mauvaises parties ou aux applications malveillantes. Ils travaillent à protéger l’intégrité des données. Ils utilisent toutes les fonctionnalités de protection des informations de Cloud plus avancées, notamment le chiffrement, l’authentification multifacteur sécurisée, la conformité et la conformité automatisées, ainsi que les fonctionnalités CASB (Cloud App Security Broker) tout en permettant et même d’encourager le partage protégé sur plusieurs plateformes. Elles permettent de les occulter de la créativité, de la productivité et de la collaboration, ce qui leur permet de rester au fait du côté compétitif.


## <a name="adopt-a-methodical-approach"></a>Adopter une approche méthodique 

La plupart des défis que j’ai rencontrés lors de l’implémentation de la sécurité dans le Cloud dans différentes organisations, indépendamment de l’industrie, ont été très similaires. Tout d’abord, tandis qu’il existe beaucoup de documentation intéressante sur les fonctionnalités et les fonctionnalités spécifiques, le niveau de la structure de l’organisation est de confusion, et les fonctionnalités de sécurité se chevauchent, ainsi que la façon dont les fonctionnalités doivent être intégrées. Il existe également un certain degré d’incertitude quant aux fonctionnalités de sécurité préconfigurées et qui nécessitent une configuration par l’organisation. En outre, les équipes SOC n’ont malheureusement pas bénéficié de la totalité de l’exposition, de la formation ou de l’allocation budgétaire nécessaires pour préparer l’adoption rapide de Cloud et la transformation numérique de leurs organisations.

Pour vous aider à résoudre ces obstacles, Microsoft a créé plusieurs ressources conçues pour vous aider à adopter une approche méthodique de votre stratégie de sécurité et de votre implémentation. 


|Resource   |Plus d’informations  |
|---------|---------|
|[Principales tâches pour les équipes de sécurité qui prennent en charge le travail à domicile](../security/top-security-tasks-for-remote-work.md)      | Si vous vous retrouvez soudainement à la mise en place d’un personnel de travail à la maison, cet article vous permet d’effectuer un renforcement de la sécurité rapidement. Elle inclut les principales tâches recommandées en fonction de votre plan de gestion des licences.    |
|[Sécurité Microsoft 365 pour les décideurs d’entreprise](../security/Microsoft-365-security-for-bdm.md)    | Lorsque vous avez le temps d’utiliser un plan plus complet, cet article inclut des recommandations qui s’étendent sur Microsoft 365, classées par surface d’attaque. Il s’agit même d’une feuille de calcul que vous pouvez utiliser pour trier les licences et les domaines (par exemple, l’identité, la protection contre les menaces et la surveillance).  |
|[Recommandations sur l’architecture de sécurité Microsoft](https://docs.microsoft.com/security/compass/compass)    | Si vous êtes un architecte de sécurité, veillez à consulter les recommandations de sécurité organisées par discipline, notamment l’identité, la mise en réseau et les opérations de sécurité.   |
|[Recommandations concernant les opérations de sécurité Microsoft](https://docs.microsoft.com/security/compass/security-operations-videos-and-decks)|Découvrez les recommandations de Microsoft concernant la configuration et l’exécution d’un centre d’opérations sécurité (SOC) |
|[Formation pour les ateliers de directeur CISO (Information Security officier)](https://docs.microsoft.com/security/ciso-workshop/ciso-workshop)   | Si vous débutez en matière de sécurité dans le Cloud, ne manquez pas cette série de vidéos.        |
|[docs.security.com/security](https://docs.microsoft.com/security/)    | Guide technique de Microsoft sur l’architecture et la stratégie de sécurité.        |
| | |

Toutes ces ressources sont conçues pour être utilisées comme point de départ et adaptées aux besoins de votre organisation. 

