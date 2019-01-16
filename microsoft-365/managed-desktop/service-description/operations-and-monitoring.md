---
title: Opérations de l’ordinateur de bureau Microsoft et de surveillance
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 12/18/2018
ms.openlocfilehash: 66945d44df150b5be9af9a9dfe52daa4d7468298
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867013"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Opérations de l’ordinateur de bureau Microsoft et de surveillance

<!-- Operations and monitoring: -->


## <a name="change-management"></a>Gestion du changement

Dans un service qui offre, l’équilibre de responsabilité pour les éléments tels que la maintenance du matériel et la sécurité des mises à jour décale vers le fournisseur de services (Microsoft) au lieu du client (vous). Toutefois, vous devez vous assurer que tiers et logiciels personnalisés continuent à fonctionner comme prévu lorsque des mises à jour sont déployées.

Pour les produits local, votre organisation suppose que toutes les responsabilités pour la gestion des modifications.

### <a name="balance-of-responsibility"></a>Équilibrer de responsabilité

Responsibility | Service de l’ordinateur de bureau Microsoft | Logiciel client Microsoft 365 | Serveurs et clients locaux | 3e partie et logiciels personnalisés
----- | ----- | ----- | ----- | -----
Fournir de nouvelles fonctionnalités | Microsoft | Microsoft | Les deux | Client
Tester de nouvelles fonctionnalités pour l’assurance qualité |  Microsoft | Microsoft | Les deux | Client
Communiquer sur les nouvelles fonctionnalités | Les deux | Les deux | Les deux | Client
Intégrer le logiciel personnalisé | Les deux | Les deux | Client | Client
Appliquer les mises à jour relatives à la sécurité | Microsoft | Microsoft | Client | Client
Gérer les logiciels système | Microsoft | Microsoft | Client | Client
Nom du package de déploiement | Microsoft | Microsoft | Client | Client


### <a name="change-process-overview"></a>Vue d’ensemble du processus de modification

Voici un résumé de la façon dont le processus de modification est partagé entre Microsoft et les clients. 



<table>
<tr><th></th><th><p>Rôle de Microsoft :</p></th><th><p>Rôle du client :</p></th></tr>
<tr><td>Avant une modification</td><td><ul><li>Définir les attentes pour les modifications apportées au service.</li><li>Informer les clients 5 jours à l’avance pour les modifications qui nécessitent une action de l’administrateur.</li><li>Pour les modifications d’urgence, appliquer une atténuation avant la notification.</li></ul></td><td><ul><li>Comprendre les attentes pour les modifications et les communications.</li><li>Lecture Microsoft gérées bureau centre de messages régulièrement.</li><li>Passer en revue et mettre à jour les processus de gestion des modifications internes.</li><li>Comprendre et contrôler le respect des exigences de bureau Microsoft. </li><li>Confirmer et d’approuver, lorsque cela est nécessaire.</li></ul></td></tr><tr><td>Pendant une modification</td><td><ul><li>Version et déployer des mises à jour de sécurité et non mensuelles pour les clients Windows 10 et Office 365.</li><li>Surveiller des signaux de données et prendre en charge des files d’attente d’impact.</li></ul></td><td><ul><li>Vérifiez le Message Desktop Microsoft Managed Center et passez en revue les informations supplémentaires.</li><li>   Aucune action requise, le cas échéant et tester des applications.</li><li>Si un scénario de réparation est rencontré, créez une demande de Support.</li></ul></td></tr><tr><td>Après une modification</td><td><ul><li>Recueillir les commentaires client afin d’améliorer le déploiement de modifications ultérieures.</li><li>Surveiller des signaux de données et prendre en charge des files d’attente d’impact.</li></ul></td><td><ul><li>Travailler avec des personnes de votre organisation d’adopter la modification.</li><li>   Passez en revue les processus de gestion de modification et d’adoption des opportunités gagner en efficacité.</li><li>Fournir des commentaires généraux et des commentaires dans l’outil de commentaires d’administration spécifiques.</li><li>Former les utilisateurs à fournir des commentaires spécifiques à l’application à l’aide du concentrateur de commentaires Windows et le bouton sourire dans les applications Office.</li></ul></td></tr>
<table> 






### <a name="change-types"></a>Types de modification

Il existe plusieurs types de modifications apportées au service régulièrement. Le canal de communication pour ces modifications et les actions que les clients sont chargés de varie.

Toutes les modifications ont le même impact sur les utilisateurs ou nécessitent une action. Certains sont certains planifiées et par leur nature (mises à jour de sécurité et les mises à jour de sécurité ne sont pas planifiées généralement). Selon le type de modification, le canal de communication peut-être varier. Le tableau suivant répertorie les types de modifications à prévoir pour le service de bureau Microsoft.

|   | Fonctionnalité |   Mises à jour non relatives à la sécurité |  Sécurité
--- | --- | --- | ---
**Type de modification** | -Mises à jour de la fonctionnalité<br>-Les nouvelles fonctionnalités ou des applications<br>-Déconseillées | Correctifs client pour des problèmes | Correctifs de sécurité
**Avance** | Avis de 5 jours pour que les modifications qui nécessitent une action |    Non, ils sont inclus dans la version de tous les mois   | Non, ils sont inclus dans la version de tous les mois 
**Canal de communication** | -Centre de messages<br>-Message d’alerte | -Centre de messages<br>-Message d’alerte | -Centre de messages<br>-Message d’alerte<br>-Bulletin de sécurité ou CVE 
**Nécessite l’action de l’administrateur client** | Parfois |  Rarement |    Rarement 
**Type d’action** | Modifier les paramètres | Communiquer les modifications aux utilisateurs | Modifier les paramètres d’administration     
**Requiert des tests** | Vérifier les applications d’entreprise, notamment les services d’accès à distance |  Parfois : tests du correctif par rapport aux processus ou aux personnalisations |   Rarement 
**Exemples de modification** | -Fonctionnalités mises à jour : portail d’administration informatique simplifié envoi ticket de prise en charge et de révision<br>-Les nouvelles fonctionnalités ou applications : semestrielle version d’une mise à jour de la fonctionnalité Windows 10 | Correctifs basés sur les bogues signalés par le client |  


## <a name="standard-operating-procedures"></a>Procédures d’exploitation standard

Le service de bureau Microsoft est implémenté et géré par Microsoft de votre instance de cloud Microsoft où vous pouvez effectuer d’autres opérations d’administration. Microsoft chargée uniquement pour le programme d’installation, la configuration et opération Microsoft Managed Desktop spécifique. 

Pour les produits local, votre organisation prend tous les la responsabilité pour la gestion du programme d’installation et les activités opérationnelles.

Categories |    Microsoft ne | Client
--- | --- | ---
Réseau (proxy, l’inspection des paquets, VPN)  | Conseiller et plan avec les clients afin de réduire le risque pour les utilisateurs professionnels. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.
Comptes de service |-Mettre en œuvre, en toute sécurité stocker et gérer les informations d’identification.<br> -Communiquer les accès non autorisés ou l’utilisation de ces informations d’identification à votre équipe des opérations de sécurité. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.<br>-Pas affecter stratégie, l’authentification multifacteur, accès conditionnel ou le déploiement d’applications pour les comptes de Service Microsoft gérés du bureau.<br>-Pas réinitialiser le mot de passe ou utiliser les informations d’identification.<br>-Ouvrir une demande de support Sev C aux opérations de bureau géré Microsoft si suspect est respectée dans les journaux d’audit Intune ou Azure, liés à ces comptes de service.
Groupes de périphériques | -Mettre en œuvre et gérer l’appartenance des périphériques dans les groupes de l’ordinateur de bureau Microsoft.<br>-Utilisez les groupes de l’ordinateur de bureau Microsoft pour gérer l’attribution et la version de configuration et de mises à jour sur les périphériques. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.<br>-Pas modifier l’appartenance d’un groupe de bureau Microsoft.<br>-Uniquement utiliser les groupes pour assigner des certificats d’entreprise pour les services, telles que VPN, Hello Windows pour le chiffrement de courrier électronique ou de l’entreprise, ou configuration d’un profil d’entreprise Wi-Fi.<br>-Où se trouve la gestion, explicitement exclure tous les groupes de l’ordinateur de bureau Microsoft lorsque vous déployez le client Gestionnaire de Configuration.
Policies |  -Mettre en œuvre et gérer les stratégies de bureau Microsoft qui régissent l’état de la configuration des périphériques au sein du service.<br>-Déployer les mises à jour, à la stratégie ou Windows, de manière incrémentielle à l’aide de groupes de périphériques.<br> -Exclure explicitement ciblage des groupes non - Microsoft de bureau. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.<br>-Pas modifier ou affecter des stratégies de bureau Microsoft périphériques ou des utilisateurs non gérés par le service de bureau Microsoft.
Windows Defender Advanced Threat Protection | Surveiller et examiner les périphériques dans l’étendue du service Microsoft de bureau. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et conseillé
Microsoft Store pour Entreprises |  Configurer et mettre à jour le profil de pilote Windows pour le service de bureau Microsoft. | -Permet de créer une demande de support demandant des informations d’une modification de configuration planifiée, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.<br>-Pas modifier la configuration du profil Microsoft gérées bureau Windows pilote ou Ajout/Suppression de périphériques affectés.
Certificats | | -Créer une demande de prise en charge 60 jours avant un certificat arrive à expiration, qui demande des informations pour un changement de configuration prévues, y compris les détails de configuration, étendue, chronologie et les autres détails pertinents pour Microsoft passer en revue.<br>-Ne s’appliquent qu’une modification une fois que Microsoft gérées bureau Operations a évalué et technicien.<br>-Mettre à jour tous les certificats sont requis pour configurer les profils de certificat, les profils VPN et profils Wi-Fi.




## <a name="device-wipe-with-factory-reset"></a>Effacement de périphérique avec réinitialisation

Équipe d’exploitation de bureau géré peut faire un répartiteur de réinitialiser sur les appareils Microsoft de bureau géré qui doivent être reconfiguration. Ceci est utile si vous devez donner un périphérique à un autre employé, ou si un employé quitte votre société. 

Il existe quelques conditions préalables :

- Administrateur du client doit soumettre une demande de service
- Nous avons besoin du nom de l’ordinateur de l’appareil
- Compte d’utilisateur doit être dans Azure Active Directory avant de faire la réinitialisation

Équipe chargée des opérations bureau géré sera :

- Rechercher le nom du périphérique dans Intune
- Envoyer que la commande de réinitialisation à l’appareil

>[!NOTE]
>Ne supprimez pas le compte d’utilisateur AD Azure avant la réinitialisation. Si l’utilisateur n’est pas dans Azure AD, Intune ne peuvent pas envoyer de que la commande de réinitialisation à l’appareil. 

Le dispositif démarre en mode OOBE et tous les paramètres et les applications préinstallées seront appliquées à nouveau. L’utilisateur du périphérique doit fournir un ensemble initial des informations à nouveau. 

Lorsque le périphérique a été réinitialisé, vous pouvez lui donner à une autre personne dans votre organisation. Aucun des données ou les données d’entreprise de l’utilisateur précédent sera sur l’appareil. L’utilisateur suivant passe en revue le même processus que la personne précédente avec un nouveau périphérique de bureau Microsoft.

BitLocker est un composant essentiel de la sécurité des données dans ce processus. Avec le chiffrement BitLocker sur les périphériques de bureau Microsoft, les données sur le lecteur restent sécurisées même après que réinitialisation a été appliquée à l’appareil. Toutes les données qui était sur le lecteur ne sera pas disponibles à l’utilisateur suivant du périphérique. Pour plus d’informations, voir [vue d’ensemble de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).

Pour plus d’informations, voir [réinitialisation un périphérique](https://docs.microsoft.com/intune/devices-wipe#factory-reset-a-device). 
