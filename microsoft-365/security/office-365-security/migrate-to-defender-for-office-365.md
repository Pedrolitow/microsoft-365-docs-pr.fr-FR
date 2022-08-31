---
title: Migrer d’un service de protection tiers vers Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365solution-mdo-migration
- highpri
ms.custom: ''
description: Découvrez le bon moyen de migrer à partir de services de protection tiers ou d’appareils tels que Google Postini, le pare-feu de courrier indésirable et de virus Barracuda ou Cisco IronPort pour Microsoft Defender pour Office 365 protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d833f264fc222a5199f3a2406f85cbe8108aadbd
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479860"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Migrer d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

Si vous disposez déjà d’un service ou d’un appareil de protection tiers existant devant Microsoft 365, vous pouvez utiliser ce guide pour migrer votre protection vers Microsoft Defender pour Office 365 afin d’obtenir les avantages d’une expérience de gestion consolidée, d’un coût potentiellement réduit (à l’aide de produits que vous payez déjà) et d’un produit mature avec une protection de sécurité intégrée. Pour plus d’informations, consultez [Microsoft Defender pour Office 365](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Regardez cette courte vidéo pour en savoir plus sur la migration vers Defender pour Office 365.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfH]

Ce guide fournit des étapes spécifiques et actionnables pour votre migration et suppose les faits suivants :

- Vous disposez déjà de boîtes aux lettres Microsoft 365, mais vous utilisez actuellement un service ou un appareil tiers pour la protection par e-mail. Les messages provenant d’Internet transitent par le service de protection avant leur remise dans votre organisation Microsoft 365, et la protection Microsoft 365 est aussi faible que possible (elle n’est jamais complètement désactivée ; par exemple, la protection contre les programmes malveillants est toujours appliquée).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="Le courrier circule à partir d’Internet via le service ou l’appareil de protection tiers avant la remise à Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- Vous dépassez la phase d’investigation et de considération pour la protection par Defender pour Office 365. Si vous devez évaluer Defender pour Office 365 pour décider s’il est approprié pour votre organisation, nous vous recommandons de prendre en compte les options décrites dans [Try Microsoft Defender pour Office 365](try-microsoft-defender-for-office-365.md).

- Vous avez déjà acheté Defender pour Office 365 licences.

- Vous devez mettre hors service votre service de protection tiers existant, ce qui signifie que vous devrez finalement pointer les enregistrements MX de vos domaines de messagerie vers Microsoft 365. Lorsque vous avez terminé, le courrier provenant d’Internet transite directement vers Microsoft 365 et est protégé exclusivement par Exchange Online Protection (EOP) et Defender pour Office 365.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="Le courrier passe d’Internet à Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

L’élimination de votre service de protection existant en faveur de Defender pour Office 365 est une étape importante que vous ne devez pas prendre à la légère, et vous ne devez pas vous précipiter pour apporter le changement. Les conseils de ce guide de migration vous aideront à faire passer votre protection de manière ordonnée, avec une interruption minimale pour vos utilisateurs.

Les étapes de migration de très haut niveau sont illustrées dans le diagramme suivant. Les étapes réelles sont répertoriées dans la section intitulée [Processus de migration](#the-migration-process) plus loin dans cet article.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="Processus de migration d’une solution ou d’un appareil de protection tiers vers Defender pour Office 365" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>Pourquoi utiliser les étapes décrites dans ce guide ?

Dans le secteur informatique, les surprises sont généralement mauvaises. Le simple fait de retourner vos enregistrements MX pour pointer vers Microsoft 365 sans tests préalables et réfléchis entraîne de nombreuses surprises. Par exemple :

- Vous ou vos prédécesseurs avez probablement consacré beaucoup de temps et d’efforts à personnaliser votre service de protection existant pour une distribution optimale du courrier (en d’autres termes, en bloquant ce qui doit être bloqué et en autorisant ce qui doit être autorisé). Il est presque garanti que toutes les personnalisations de votre service de protection actuel ne sont pas nécessaires dans Defender pour Office 365. Il est également très possible que Defender pour Office 365 introduise de nouveaux problèmes (autorisations ou blocs) qui n’ont pas eu lieu ou n’ont pas été requis dans votre service de protection actuel.
- Votre support technique et le personnel de sécurité doivent savoir quoi faire dans Defender pour Office 365. Par exemple, si un utilisateur se plaint d’un message manquant, votre support technique sait-il où ou comment le rechercher ? Ils sont probablement familiarisés avec les outils de votre service de protection existant, mais qu’en est-il des outils dans Defender pour Office 365 ?

En revanche, si vous suivez les étapes décrites dans ce guide de migration, vous obtiendrez les avantages tangibles suivants pour votre migration :

- Interruption minimale pour les utilisateurs.
- Données objectives de Defender pour Office 365 que vous pouvez utiliser lorsque vous signalez la progression et la réussite de la migration vers la gestion.
- Participation précoce et instruction pour le support technique et le personnel de sécurité.

Plus vous vous familiariserez avec la façon dont Defender pour Office 365 affectera votre organisation, plus la transition sera efficace pour les utilisateurs, le personnel du support technique, le personnel de sécurité et la gestion.

Ce guide de migration vous offre un plan pour « activer progressivement la numérotation » afin de pouvoir surveiller et tester la façon dont Defender pour Office 365 affecte vos utilisateurs et leurs e-mails afin de pouvoir réagir rapidement aux problèmes que vous rencontrez.

## <a name="the-migration-process"></a>Processus de migration

Le processus de migration d’un service de protection tiers vers Defender pour Office 365 peut être divisé en trois phases, comme décrit dans le tableau suivant :

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="Processus de migration vers Defender pour Office 365" lightbox="../../media/phase-diagrams/migration-phases.png":::

|Phase|Description|
|---|---|
|[Préparer votre migration](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Inventaire des paramètres de votre service de protection existant](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Vérifier votre configuration de protection existante dans Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Vérifier la configuration de votre routage de messagerie](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[Déplacer des fonctionnalités qui modifient des messages dans Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[Définir le courrier indésirable et les expériences utilisateur en bloc](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Identifier et désigner des comptes prioritaires](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Configurer Defender pour Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Créer des groupes de distribution pour les utilisateurs pilotes](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Configurer la soumission d’utilisateurs pour la création de rapports de messages utilisateur](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[Gérer ou créer la règle de flux de messagerie SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Configurer le filtrage amélioré pour les connecteurs](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Créer des stratégies de protection pilote](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Intégrer à Defender pour Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Commencer à intégrer Security Teams](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(Facultatif) Exempter les utilisateurs pilotes du filtrage par votre service de protection existant](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Paramétrer l’intelligence de l’usurpation d’identité](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Paramétrer la protection de l’emprunt d’identité et l’intelligence de boîte aux lettres](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Utiliser les données des soumissions d’utilisateurs pour mesurer et ajuster](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(Facultatif) Ajouter d’autres utilisateurs à votre pilote et itérer](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[Étendre la protection Microsoft 365 à tous les utilisateurs et désactiver la règle de flux de messagerie SCL=-1](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[Changer vos enregistrements MX](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Étape suivante

- Passez à la [phase 1 : Préparer](migrate-to-defender-for-office-365-prepare.md).
