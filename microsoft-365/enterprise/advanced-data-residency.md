---
title: Résidence avancée des données dans Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.reviewer: dmwmsft
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Découvrez les options avancées de résidence des données dans Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3f770faaf96de604fa9d190f538006f67242b227
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805373"
---
# <a name="advanced-data-residency-in-microsoft-365"></a>Data Residency avancée dans Microsoft 365

## <a name="overview-of-advanced-data-residency"></a>Vue d’ensemble des Data Residency avancées

Le module complémentaire Microsoft 365 Advanced Data Residency (« ADR ») offre aux clients éligibles une couverture étendue des charges de travail Microsoft 365 et des données client, la résidence des données validées pour les régions du centre de données du pays local et les services de migration de locataire prioritaires.  Avec advanced Data Residency, les clients d’entreprise peuvent mieux répondre à leurs exigences en matière de conformité de résidence des données et d’emplacement du locataire.

Les charges de travail suivantes sont incluses dans ADR. Pour plus d’informations, consultez l’article suivant :

- [Exchange Online](m365-dr-workload-exo.md)
- [SharePoint Online et OneDrive Entreprise](m365-dr-workload-spo.md)
- [Microsoft Teams](m365-dr-workload-teams.md)
- [Microsoft Defender pour Office P1 et Exchange Online Protection](m365-dr-workload-mdo-p1.md)
- [Office pour le web](m365-dr-workload-office-for-web.md)
- [Connexions Microsoft Viva](m365-dr-workload-viva-connections.md)
- [Sujets Viva](m365-dr-workload-viva-topics.md)
- [Microsoft Purview](m365-dr-workload-purview.md)
  - [Audit (Standard)](m365-dr-workload-purview.md#purview-audit-standard)
  - [Audit (Premium)](m365-dr-workload-purview.md#purview-audit-premium)
  - [Conservation des données](m365-dr-workload-purview.md#data-lifecycle-management---data-retention)
  - [Gestion des enregistrements Microsoft Purview](m365-dr-workload-purview.md#data-lifecycle-management---records-management)
  - [Étiquettes de confidentialité](m365-dr-workload-purview.md#information-protection---sensitivity-labels)
  - [Protection contre la perte de données](m365-dr-workload-purview.md#information-protection---data-loss-prevention-dlp)
  - [Chiffrement des messages Office](m365-dr-workload-purview.md#information-protection---office-message-encryption)
  - [Obstacles aux informations](m365-dr-workload-purview.md#insider-risk-management---information-barriers)

## <a name="licensing-and-purchase"></a>Licences et achat

### <a name="licensing-requirements"></a>Conditions requises pour les licences

- Microsoft 365 F1, F3, E3 ou E5
- Office 365 F3, E1, E3 ou E5
- Exchange Online (plan 1) ou plan 2
- OneDrive entreprise (plan 1 ou plan 2)
- SharePoint Online Plan 1 ou Plan 2

### <a name="eligibility"></a>Éligibilité

Le module complémentaire Advanced Data Residency (« ADR ») est destiné aux clients d’entreprise de Microsoft 365 qui ont des exigences complètes en matière de résidence des données.  Pour pouvoir acheter une ADR, les clients doivent remplir deux conditions préalables :

- Les abonnements dans le _locataire_ sont achetés via microsoft Accord Entreprise (« EA ») ou le canal Web Direct.
- La _zone géographique par défaut_ du _locataire_ doit être l’un des pays inclus dans la _zone géographique de la région locale_
  
La disponibilité géographique et des canaux sera mise à jour en fonction des disponibilités.

Les clients doivent couvrir 100 % des utilisateurs payants ci-dessus avec une licence de module complémentaire ADR pour que le locataire reçoive la résidence des données pour les charges de travail ADR.

### <a name="mixedhybrid-tenants"></a>Locataires mixtes/hybrides :

Un client est défini comme « mixte » ou « hybride » s’il a plusieurs types de licences, y compris les licences commerciales/publiques (par exemple, E3, E5) **et** éducation (par exemple, A1, A3, etc.) dans son abonnement.

Les clients mixtes/hybrides ont le droit d’acheter le module complémentaire ADR complet pour la partie payante des références SKU Microsoft 365 et ne sont pas obligés de couvrir les types d’abonnements gratuits. Toutefois, ils doivent couvrir les sièges d’éducation payants avec ADR (Microsoft 365 A3/A5, Office 365 A3/A5).

## <a name="data-migration-management"></a>Gestion de la migration des données

Si toutes les données client d’un client couvertes par la fonctionnalité advanced Data Residency ne sont pas déjà stockées au repos dans leur _zone géographique de région locale_ éligible, une migration des données vers la _zone géographique de la région locale_ est requise.  Si toutes les données client d’un client couvertes par la fonctionnalité advanced Data Residency sont déjà stockées au repos dans leur _zone géographique de région locale_ éligible, aucune migration de données vers la _zone géographique de la région locale_ n’est nécessaire.

### <a name="starting-data-migration"></a>Démarrage de la migration de données

Une fois qu’un client a reçu ses licences Advanced Data Residency, le client doit indiquer qu’il est prêt à commencer la migration de ses données, si nécessaire. Pour signaler que votre locataire est prêt pour la migration de ses données, l’administrateur du client visitera la section Emplacement des données de la console Administration Microsoft 365 dans la zone Paramètres -> Paramètres de l’organisation -> Profil de l’organisation. À partir de là, l’administrateur client peut voir l’emplacement actuel de ses données au repos et la _région géographique vers_ laquelle les données client seront migrées. Remarque : La migration des données ne commence pas tant que l’administrateur du client n’a pas exécuté cette tâche. En outre, l’attente de migration abordée ailleurs dans cette documentation ne commencera pas à être suivie tant que cette tâche n’aura pas été exécutée par l’administrateur du client.

Une fois le signal client reçu, il reçoit sa date d’adhésion et la date cible d’achèvement.

En plus d’une notification publiée dans le Centre de messages à l’achèvement, la section Emplacement des données dans la console Administration Microsoft 365 est également mise à jour à mesure que chaque charge de travail nécessitant une migration de données est terminée.

### <a name="migration-expectations"></a>Attentes en matière de migration

Microsoft fera des efforts raisonnables pour tenter d’effectuer une migration de client Data Residency avancée dans les douze (12) mois à compter du moment où l’administrateur du client a signalé qu’il est prêt pour la migration. Toutefois, Microsoft peut ne pas être en mesure d’effectuer la migration dans ce délai pour tous les clients. Par exemple, des clients plus volumineux ou plus complexes ou des situations en dehors du contrôle de Microsoft peuvent nécessiter du temps supplémentaire pour terminer la migration. Les clients du module complémentaire advanced Data Residency reçoivent également des services de migration prioritaires pour leurs locataires par rapport à l’option de migration du programme de déplacement héritée. Ces attentes de migration s’appliquent également à tous les clients ADR EDU. Les clients qui utilisent le programme de déplacement hérité pour une migration de données qui ne disposent pas de la fonctionnalité Advanced Data Residency suivront à la place [les attentes de migration du programme de déplacement hérité](m365-dr-legacy-move-program.md#migration-expectations).

Les déplacements de données sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Nous respectons le [Contrat de niveau de service (SLA) Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité, de sorte que les clients n’ont rien à préparer ou à surveiller pendant le déplacement. La notification de toute maintenance de service est effectuée si nécessaire.

Pendant le processus de migration, Microsoft copie temporairement vos données de carnet d’adresses dans des ressources globales Microsoft où elles sont chiffrées et utilisées uniquement pour prendre en charge les opérations de continuité d’activité et de récupération d’urgence (BCDR). Une fois que Microsoft a terminé le déplacement des données de boîte aux lettres, Microsoft supprime ces données temporaires des ressources globales. Microsoft continue d’investir régulièrement dans des ressources mondiales et régionales. Au cours de l’année civile 2023, Microsoft prévoit d’utiliser des ressources régionales à des fins BCDR pendant le processus de migration.

### <a name="during-and-after-your-migration"></a>Pendant et après votre migration

Les déplacements de données sont une opération back-end avec un impact minimal, voire aucun, sur les utilisateurs finaux. Aucune action n’est nécessaire pendant que Microsoft déplace chaque service et les données client associées pour votre locataire vers la zone géographique applicable.

> [!NOTE]
> Le déplacement se produit à différents moments pour chaque service. Par conséquent, vous verrez que les fonctionnalités réduites de chaque service sont décrites ci-dessous à des moments différents.

Regardez le Centre de messages Microsoft 365 pour obtenir la confirmation de la fin des déplacements pour chaque service de charge de travail.

### <a name="impact-on-end-users-and-workloads"></a>Impact sur les utilisateurs finaux et les charges de travail

Les déplacements de données sont une opération de service principal avec un impact minimal sur les utilisateurs finaux. Les fonctionnalités qui peuvent être affectées sont répertoriées dans la page Pendant et après le déplacement de vos données. Nous respectons le [Contrat de niveau de service (SLA) Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkId=523897) pour la disponibilité, de sorte que les clients n’ont rien à préparer ou à surveiller pendant le déplacement. La notification de toute maintenance de service est effectuée si nécessaire.

### <a name="features-impacted"></a>Fonctionnalités impactées

En raison de la nature complexe des centaines de services (standard et personnalisables) disponibles dans les nombreuses charges de travail auxquelles les clients s’inscrivent et utilisent dans le cadre d’une licence E3 ou E5 classique, la migration des données client d’un centre de données vers un autre peut entraîner une interruption mineure et/ou une indisponibilité temporaire de certains services que les clients utilisent. Pour plus d’informations, consultez les sections de migration de chaque charge de travail dans la [section Fonctionnalités de Data Residency](m365-dr-workload-exo.md) de charge de travail.

### <a name="status-notification"></a>Notification d’état

Pour les clients nécessitant une migration de données, ils peuvent surveiller le Centre de messages pour les mises à jour à fournir à mesure que chaque charge de travail termine sa migration de données. La section Emplacement des données dans la console Administration Microsoft 365 peut également être référencée pour voir si une charge de travail a terminé sa migration.
En raison de la nature du fonctionnement des migrations, aucun état précis n’est fourni pour indiquer à quel point une migration peut être proche de l’achèvement.

### <a name="faq"></a>Questions fréquentes (FAQ)

#### <a name="how-do-enterprise-customers-purchase-the-microsoft-365-advanced-data-residency-add-on"></a>Comment les clients d’entreprise achètent-ils le module complémentaire Microsoft 365 Advanced Data Residency ?
<details><summary>Cliquez pour développer</summary>

Les clients d’entreprise éligibles doivent contacter leur équipe de compte Microsoft ou Accord Entreprise partenaire de gestion des licences pour faciliter l’achat du module complémentaire Advanced Data Residency. Les clients Web Direct doivent acheter via leur compte en ligne.
</details>

#### <a name="what-does-the-launch-of-adr-mean-for-the-move-program"></a>Que signifie le lancement de l’ADR pour le programme Move ?
<details><summary>Cliquez pour développer</summary>

Les efforts du programme Advanced Data Residency et Move existent simultanément pendant une durée limitée et ont des engagements clients différents. Le programme de déplacement est limité à Exchange Online, SharePoint Online, OneDrive Entreprise et Microsoft Teams. Adr inclut ces charges de travail et d’autres.  Le programme Move a pris fin avec le lancement du centre de données local du Qatar et ne sera pas disponible pour les centres de données locaux futurs.  Les clients Data Residency avancés reçoivent des services de migration prioritaires par rapport aux clients du programme de déplacement. Pour plus d’informations, consultez la section Attentes de migration.
</details>

#### <a name="how-can-i-move-my-data-to-my-country-with-advanced-data-residency-what-does-the-process-look-like"></a>Comment puis-je déplacer mes données vers mon pays avec Advanced Data Residency ? À quoi ressemble le processus ?
<details><summary>Cliquez pour développer</summary>

La première étape consiste à acheter la référence SKU ADR. Reportez-vous à [Éligibilité adr](advanced-data-residency.md#eligibility).  Une fois que vous avez acheté adr, vous recevez une notification via le Centre de messages (dans le centre d’administration client) décrivant la confirmation d’achat.  Une fois que vous avez confirmé que vous êtes prêt à commencer les migrations, l’attente de 12 mois pour migrer toutes les données de votre client au repos, en ce qui concerne les charges de travail répertoriées ci-dessus, commence. À partir de là, toutes les charges de travail qui migrent les données client fournissent des notifications à l’administrateur client via le Centre de messages (deux messages chacun ; un au début et à la fin du processus de migration).
</details>

## <a name="related-articles"></a>Articles connexes

[Programme de déplacement hérité](m365-dr-legacy-move-program.md)
  
[Nouvelles régions de centres de données pour Microsoft Dynamics CRM Online](/power-platform/admin/new-datacenter-regions?branch=main)
  
[Services Azure par région](https://azure.microsoft.com/regions/)

[Expérience Teams dans une location multigéographique Microsoft 365](/microsoftteams/teams-experience-o365odb-spo-multi-geo?branch=main)
