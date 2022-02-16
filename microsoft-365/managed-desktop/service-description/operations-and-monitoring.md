---
title: Microsoft Manged Desktop et surveillance
description: Qui fait quoi pour différents processus de modification
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6b1771660cb25ccd9d23c97d1e3fcf6edd27feaa
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2022
ms.locfileid: "62825217"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Microsoft Manged Desktop et surveillance

<!-- Operations and monitoring: -->

## <a name="change-management"></a>Gestion des modifications

Dans l’offre de services, l’équilibre des responsabilités en matière de maintenance du matériel et de mises à jour de sécurité est déplacé vers le fournisseur de services (Microsoft) au lieu du client (vous). Toutefois, vous devez toujours vous assurer que les logiciels non Microsoft et personnalisés continuent de fonctionner comme prévu lorsque des mises à jour sont déployées.

Pour les produits locaux, votre organisation assume toute la responsabilité de la gestion des changements.

### <a name="balance-of-responsibility"></a>Équilibre des responsabilités

| Responsabilité | Microsoft Manged Desktop service | Microsoft 365 logiciel client | Serveurs et clients locaux | Logiciels non Microsoft et personnalisés
| ----- | ----- | ----- | ----- | ----- |
| Fournir de nouvelles fonctionnalités | Microsoft | Microsoft | Les deux | Client
| Tester de nouvelles fonctionnalités pour l’assurance qualité |  Microsoft | Microsoft | Les deux | Client
| Communiquer sur les nouvelles fonctionnalités | Les deux | Les deux | Les deux | Client
| Intégrer le logiciel personnalisé | Les deux | Les deux | Client | Client
| Appliquer les mises à jour relatives à la sécurité | Microsoft | Microsoft | Client | Client
| Gérer les logiciels système | Microsoft | Microsoft | Client | Client
| Package pour le déploiement | Microsoft | Microsoft | Client | Client

### <a name="change-process-overview"></a>Vue d’ensemble du processus de modification

Voici un résumé de la façon dont le processus de modification est partagé entre Microsoft et les clients :

| Scénario | Rôle de Microsoft | Rôle du client |
| ----- | ----- | ----- |
| Avant une modification | <ul><li>Définir les attentes pour les modifications apportées au service.</li><li>Informez les clients 5 jours à l’avance des modifications qui nécessitent une action de l’administrateur.</li><li>Pour les modifications d’urgence, appliquez une atténuation avant d’avertir.</li></ul> | <ul><li>Comprendre les attentes pour les modifications et les communications.</li><li>Lisez Microsoft Manged Desktop centre de messages régulièrement.</li><li>Passer en revue et mettre à jour les processus de gestion des modifications internes.</li><li>Comprendre et vérifier la conformité avec Microsoft Manged Desktop requises. </li><li>Reconnaissez et approuvez, le cas échéant.</li></ul>
| Pendant une modification | <ul><li>Publiez et déployez des mises à jour mensuelles de sécurité et non de sécurité pour Windows 10 et Office 365 clients.</li><li>Surveiller les signaux de données et les files d’attente de prise en charge pour l’impact.</li></ul> | <ul><li>Consultez le centre Microsoft Manged Desktop messages et consultez toutes les informations supplémentaires.</li><li>Prenez les mesures requises, le cas échéant, et testez les applications.</li><li>Si un scénario de rupture/correction est connu, créez une demande de support.</li></ul> |
| Après une modification | <ul><li>Recueillir les commentaires des clients pour améliorer le déploiement des modifications futures.</li><li>Surveiller les signaux de données et les files d’attente de prise en charge pour l’impact.</li></ul> | <ul><li>Travaillez en équipe avec les membres de votre organisation pour adopter la modification.</li><li>Examinez les processus de gestion des changements et de l’adoption pour obtenir plus d’efficacité.</li><li>Fournissez des commentaires généraux et des commentaires spécifiques dans l’outil de commentaires de l’administrateur.</li><li>Formez les utilisateurs à fournir des commentaires spécifiques à l’application à l’Hub de commentaires Windows et au bouton Souris dans Office applications.</li></ul> |

### <a name="change-types"></a>Types de modification

Plusieurs types de modifications sont apportés régulièrement au service. Le canal de communication de ces modifications et les actions dont vous êtes responsable varient.

Toutes les modifications n’ont pas le même effet sur vos utilisateurs ou ne nécessitent pas d’action. Certaines sont planifiées et d’autres non planifiées. Par exemple, les mises à jour non de sécurité et les mises à jour de sécurité ne sont généralement pas planifiées.

Selon le type de modification, le canal de communication peut varier. Le tableau suivant répertorie les types de modifications que vous pouvez attendre pour Microsoft Manged Desktop service.

|  | Les fonctionnalités | Mises à jour non liées à la sécurité | Sécurité |
| ----- | ----- | ----- | ----- |
| **Type de modification** | <ul><li>Mises à jour de fonctionnalité</li><li>Nouvelles fonctionnalités ou applications</li><li>Fonctionnalités déconseillées</li></ul> | Correctifs client pour des problèmes | Mises à jour de sécurité |
**Préavis** | Préavis de cinq jours pour les modifications qui nécessitent une action | Aucune modification de ce type n’est incluse dans la version mensuelle | Aucune modification n’est incluse dans la version mensuelle |
**Canal de communication** | <ul><li>Centre de messages</li><li>Alerte par courrier électronique</li></ul> | <ul><li>Centre de messages</li><li>Alerte par courrier électronique</li></ul> | <ul><li>Centre de messages</li><li>Alerte par courrier électronique</li></ul> |
**Nécessite une action de l’administrateur global** | Parfois | Rarement | Rarement |
**Type d’action** | Modifier les paramètres | Communiquer les modifications aux utilisateurs | Modifier les paramètres d’administration |
**Nécessite des tests** | Vérifier les applications métiers, y compris les services d’accès à distance | Parfois ; test du correctif par rapport aux processus ou aux personnalisations ; | Rarement |
**Exemples de modification** | <ul><li>Mises à jour des fonctionnalités : portail d’administration informatique simplifie l’envoi et la révision des tickets de support</li><li>Nouvelles fonctionnalités ou applications : Semi-Annual publication d’une mise à jour Windows 10 fonctionnalités</li></ul> | Correctifs basés sur les bogues signalés par le client |

## <a name="standard-operating-procedures"></a>Procédures d’exploitation standard

Le service Microsoft Manged Desktop est implémenté et géré par Microsoft dans votre instance de cloud Microsoft où vous pouvez effectuer d’autres activités administratives. Microsoft est le seul responsable de l Microsoft Manged Desktop, de la configuration et du fonctionnement spécifiques.

Pour les produits locaux, votre organisation assume toutes les responsabilités de gestion de l’installation, ainsi que de la configuration et des activités opérationnelles.

| Catégories | Microsoft | Le client |
| ----- | ----- | ----- |
| Réseau (proxy, inspection des paquets, VPN) | Conseillez les clients et planifiez-les pour minimiser les risques pour les utilisateurs professionnels. | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Incluez les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li></ul> |
Comptes de service | <ul><li>Implémenter, stocker et gérer les informations d’identification en toute sécurité.</li><li>Communiquez l’accès non autorisé ou l’utilisation de ces informations d’identification à votre équipe des opérations de sécurité.</li></ul> | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li><li>N’affectez pas de stratégie, d’authentification multifacteur, d’accès conditionnel ou de déploiement d’application aux comptes Microsoft Manged Desktop service.</li><li>Ne réinitialisez pas le mot de passe ou n’utilisez pas les informations d’identification.</li><li>Ouvrez une demande de support Sev C à Microsoft Manged Desktop Operations si une activité suspecte est observée dans les journaux d’audit Intune ou Azure, liés à ces comptes de service.</li></ul>
| Groupes d’appareils | <li> Implémenter et affecter l’appartenance des appareils au sein Microsoft Manged Desktop groupes.</li><li>Utilisez les groupes Microsoft Manged Desktop pour gérer l’affectation et la publication de la configuration et des mises à jour sur les appareils.</li></ul> | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li><li>Affectez uniquement des appareils à Microsoft Manged Desktop groupe de déploiement en suivant les étapes décrites dans Affecter des appareils [à un groupe de déploiement](../working-with-managed-desktop/assign-deployment-group.md).</li><li>Utilisez uniquement les groupes pour attribuer des certificats d’entreprise pour des services tels que VPN, Windows Hello Entreprise ou le chiffrement de courrier ou la configuration de profil Wifi d’entreprise.</li><li>Lorsque la cogestion existe, excluez explicitement tous les groupes Microsoft Manged Desktop lors du déploiement du client Configuration Manager.</li></ul>
| Stratégies | <ul><li>Implémenter et gérer les stratégies Microsoft Manged Desktop qui régissent l’état de configuration des appareils au sein du service.</li><li> Déployer des mises à jour, à des Windows, à l’aide de groupes d’appareils de manière incrémentielle.</li><li>Exclure explicitement les groupes non Microsoft Manged Desktop cible.</li></ul> | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li><li>Ne modifiez ni n’affectez Microsoft Manged Desktop stratégies de gestion aux appareils ou aux utilisateurs qui ne sont pas gérés par Microsoft Manged Desktop service.
Microsoft 365 Defender point de terminaison.</li></ul> | Surveillez et examinez les appareils dans l’étendue Microsoft Manged Desktop service. | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li></ul>
| Microsoft Store pour Entreprises | Configurez et maintenez le Windows Autopilot pour le service Microsoft Manged Desktop service. | <ul><li>Créez une demande de support demandant des informations pour une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li><li>Ne modifiez pas la configuration du profil Autopilot Microsoft Manged Desktop Windows ou ajoutez/supprimez des appareils affectés.</li></ul>
| Certificats | | <ul><li>Créez une demande de support 60 jours avant l’expiration d’un certificat, en demandant des informations sur une modification de configuration planifiée. Inclure les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.</li><li>Appliquez une modification uniquement une fois Microsoft Manged Desktop Opérations a évalué et conseillé.</li><li>Mettez à jour tous les certificats requis pour configurer les profils de certificat, les profils VPN et Wi-Fi profils.</li></ul>|

## <a name="device-wipe-with-factory-reset"></a>Réinitialisation d’appareil avec réinitialisation aux usine

L Microsoft Manged Desktop des opérations d’usine peut effectuer une réinitialisation d’usine des appareils inscrits au service si nécessaire. La réinitialisation est utile si vous devez donner un appareil à un autre employé ou si un employé quitte votre entreprise.

Il existe quelques conditions requises :

- Votre administrateur général doit envoyer une demande de support.
- Incluez le nom de l’ordinateur de l’appareil dans la demande.
- Le compte d’utilisateur doit être Azure AD avant de réinitialiser l’appareil.

L’équipe Des opérations bureau gérées :

- Recherchez le nom de l’appareil dans Intune.
- Envoyez la commande de réinitialisation d’usine à l’appareil.

> [!NOTE]
> Ne supprimez pas le compte d’utilisateur Azure AD avant la réinitialisation de l’appareil. Si l’utilisateur n’est pas Azure AD, Intune ne peut pas envoyer la commande de réinitialisation d’usine à l’appareil.

L’appareil démarre dans l’expérience « out of box experience », et toutes les applications et paramètres préinstallés sont à nouveau appliqués. L’utilisateur de l’appareil doit fournir à nouveau les informations d’installation initiales.

Lorsque l’appareil a été réinitialisé, vous pouvez le donner à une autre personne de votre organisation. Aucune des données de l’utilisateur précédent ou des données d’entreprise ne sera sur l’appareil. L’utilisateur suivant va passer par le même processus que la personne précédente l’a fait avec un nouvel Microsoft Manged Desktop appareil.

BitLocker est un composant clé de la sécurité des données dans ce processus. Avec le chiffrement BitLocker sur Microsoft Manged Desktop, les données du lecteur restent sécurisées même après la réinitialisation d’usine de l’appareil. Les données qui se trouvaient sur le lecteur ne seront pas disponibles pour le prochain utilisateur de l’appareil. Pour plus d’informations, voir [vue d’ensemble de BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview).

Pour plus d’informations, voir [Réinitialiser un appareil aux états d’usine](/intune/remote-actions/devices-wipe#factory-reset-a-device).
