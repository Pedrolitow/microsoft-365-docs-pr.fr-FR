---
title: Opérations et surveillance du Bureau géré Microsoft
description: Qui fait quoi pour différents processus de modification
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
ms.openlocfilehash: 3e56066f0b4e63fc9b73bbecf5aaa3180ffd2e4f
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920419"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Opérations et surveillance du Bureau géré Microsoft

<!-- Operations and monitoring: -->


## <a name="change-management"></a>Gestion des modifications

Dans une offre de service, l’équilibre des responsabilités pour des opérations telles que la maintenance du matériel et les mises à jour relatives à la sécurité se déplace vers le fournisseur de services (Microsoft) plutôt que vers le client (vous). Toutefois, vous devez toujours vous assurer que les logiciels non Microsoft et personnalisés continuent de fonctionner comme prévu lorsque des mises à jour sont déployées.

Pour les produits locaux, votre organisation assume toute la responsabilité de la gestion des changements.

### <a name="balance-of-responsibility"></a>Équilibre des responsabilités

Responsibility | Service Bureau géré Microsoft | Logiciel client Microsoft 365 | Serveurs et clients locaux | logiciels non Microsoft et personnalisés
----- | ----- | ----- | ----- | -----
Fournir de nouvelles fonctionnalités | Microsoft | Microsoft | Les deux | Client
Tester de nouvelles fonctionnalités pour l’assurance qualité |  Microsoft | Microsoft | Les deux | Client
Communiquer sur les nouvelles fonctionnalités | Les deux | Les deux | Les deux | Client
Intégrer le logiciel personnalisé | Les deux | Les deux | Client | Client
Appliquer les mises à jour relatives à la sécurité | Microsoft | Microsoft | Client | Client
Gérer les logiciels système | Microsoft | Microsoft | Client | Client
Package pour le déploiement | Microsoft | Microsoft | Client | Client


### <a name="change-process-overview"></a>Vue d’ensemble du processus de modification

Voici un résumé de la façon dont le processus de modification est partagé entre Microsoft et les clients : 



<table>
<tr><th></th><th><p>Rôle de Microsoft :</p></th><th><p>Rôle du client :</p></th></tr>
<tr><td>Avant une modification</td><td><ul><li>Définir les attentes pour les modifications apportées au service.</li><li>Informez les clients 5 jours à l’avance des modifications qui nécessitent une action de l’administrateur.</li><li>Pour les modifications d’urgence, appliquez une atténuation avant d’avertir.</li></ul></td><td><ul><li>Comprendre les attentes pour les modifications et les communications.</li><li>Lisez régulièrement le Centre de messages du Bureau géré Microsoft.</li><li>Passer en revue et mettre à jour les processus de gestion des modifications internes.</li><li>Comprendre et vérifier la conformité avec les exigences de Bureau géré Microsoft. </li><li>Reconnaissez et approuvez, le cas échéant.</li></ul></td></tr><tr><td>Pendant une modification</td><td><ul><li>Publiez et déployez des mises à jour mensuelles de sécurité et non de sécurité pour les clients Windows 10 et Office 365.</li><li>Surveiller les signaux de données et les files d’attente de prise en charge pour l’impact.</li></ul></td><td><ul><li>Consultez le Centre de messages du Bureau géré Microsoft et consultez toutes les informations supplémentaires.</li><li>   Prenez les mesures requises, le cas échéant, et testez les applications.</li><li>Si un scénario de rupture/correction est connu, créez une demande de support.</li></ul></td></tr><tr><td>Après une modification</td><td><ul><li>Recueillir les commentaires des clients pour améliorer le déploiement des modifications futures.</li><li>Surveiller les signaux de données et les files d’attente de prise en charge pour l’impact.</li></ul></td><td><ul><li>Travaillez en équipe avec les membres de votre organisation pour adopter la modification.</li><li>   Examinez les processus de gestion des changements et de l’adoption pour obtenir plus d’efficacité.</li><li>Fournissez des commentaires généraux et des commentaires spécifiques dans l’outil de commentaires de l’administrateur.</li><li>Formez les utilisateurs à fournir des commentaires spécifiques à l’application à l’aide du Hub de commentaires Windows et du bouton Souris dans les applications Office.</li></ul></td></tr>
<table> 






### <a name="change-types"></a>Types de modification

Plusieurs types de modifications sont apportés régulièrement au service. Le canal de communication de ces modifications et les actions dont vous êtes responsable varient.

Toutes les modifications n’ont pas le même impact sur vos utilisateurs et ne nécessitent pas toutes une action. Certaines sont planifiées et d’autres non planifiées par nature (les mises à jour non de sécurité et les mises à jour de sécurité ne sont généralement pas planifiées). Selon le type de modification, le canal de communication peut varier. Le tableau suivant répertorie les types de modifications que vous pouvez attendre pour le service Bureau géré Microsoft.

|   | Les fonctionnalités |   Mises à jour non relatives à la sécurité |  Sécurité
--- | --- | --- | ---
**Type de modification** | - Mises à jour des fonctionnalités<br>- Nouvelles fonctionnalités ou applications<br>- Fonctionnalités dépréciées | Correctifs client pour des problèmes | Mises à jour de sécurité
**Préavis** | Préavis de cinq jours pour les modifications qui nécessitent une action | Non, ces modifications sont incluses dans la version mensuelle    | Non, les modifications sont incluses dans la version mensuelle 
**Canal de communication** | - Centre de messages<br>- Alerte par courrier électronique | - Centre de messages<br>- Alerte par courrier électronique | - Centre de messages<br>- Alerte par courrier électronique
**Nécessite une action de l’administrateur global** | Parfois |  Rarement |    Rarement 
**Type d’action** | Modifier les paramètres | Communiquer les modifications aux utilisateurs | Modifier les paramètres d’administration     
**Nécessite des tests** | Vérifier les applications métiers, y compris les services d’accès à distance |  Parfois : tests du correctif par rapport aux processus ou aux personnalisations |   Rarement 
**Exemples de modification** | - Mises à jour des fonctionnalités : portail d’administration informatique simplifie l’envoi et la révision des tickets de support<br>- Nouvelles fonctionnalités ou applications : Semi-Annual d’une mise à jour des fonctionnalités Windows 10 | Correctifs basés sur les bogues signalés par le client |  


## <a name="standard-operating-procedures"></a>Procédures d’exploitation standard

Le service Bureau géré Microsoft est implémenté et géré par Microsoft dans votre instance de cloud Microsoft où vous pouvez effectuer d’autres activités administratives. Microsoft est l’unique responsable de l’installation, de la configuration et du fonctionnement propres au Bureau géré Microsoft. 

Pour les produits locaux, votre organisation assume toutes les responsabilités de gestion de l’installation, ainsi que de la configuration et des activités opérationnelles.

Categories |    Microsoft | Le client
--- | --- | ---
Réseau (proxy, inspection des paquets, VPN)  | Conseillez les clients et planifiez-les pour minimiser les risques pour les utilisateurs professionnels. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.
Comptes de service |- Implémenter, stocker et gérer les informations d’identification en toute sécurité.<br> - Communiquez l’accès non autorisé ou l’utilisation de ces informations d’identification à votre équipe des opérations de sécurité. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.<br>- Ne pas affecter de stratégie, d’authentification multifacteur, d’accès conditionnel ou de déploiement d’application aux comptes de service Bureau géré Microsoft.<br>- Ne pas réinitialiser le mot de passe ou utiliser les informations d’identification.<br>- Ouvrez une demande de support Sev C aux opérations de bureau géré Microsoft si une activité suspecte est observée dans les journaux d’audit Intune ou Azure, liés à ces comptes de service.
Groupes d’appareils | - Implémenter et gérer l’appartenance des appareils au sein de groupes Bureau géré Microsoft.<br>- Utilisez les groupes Bureau géré Microsoft pour gérer l’affectation et la publication de la configuration et des mises à jour des appareils. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.<br>- Ne modifiez pas l’appartenance d’un groupe Bureau géré Microsoft.<br>- Utilisez uniquement les groupes pour attribuer des certificats d’entreprise pour des services tels que VPN, Windows Hello Entreprise ou le chiffrement de courrier ou la configuration de profil Wi-Fi entreprise.<br>- Lorsque la cogestion existe, excluez explicitement tous les groupes Bureau géré Microsoft lors du déploiement du client Configuration Manager.
Stratégies |  - Implémenter et gérer les stratégies bureau géré Microsoft qui régissent l’état de configuration des appareils au sein du service.<br>- Déployer des mises à jour, vers une stratégie ou Windows, de manière incrémentielle à l’aide de groupes d’appareils.<br> - Exclure explicitement le ciblage de groupes bureau gérés non-Microsoft. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.<br>- Ne modifiez pas ou n’affectez pas de stratégies bureau géré Microsoft aux appareils ou aux utilisateurs qui ne sont pas gérés par le service Bureau géré Microsoft.
Microsoft Defender pour point de terminaison | Surveiller et examiner les appareils dans l’étendue du service Bureau géré Microsoft. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquer une modification uniquement une fois que les opérations du Bureau géré Microsoft ont été évaluées et conseillées
Microsoft Store pour Entreprises |  Configurez et gérez le profil Windows Autopilot pour le service Bureau géré Microsoft. | - Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.<br>- Ne modifiez pas la configuration du profil Microsoft Managed Desktop Windows Autopilot ou ajoutez/supprimez des appareils affectés.
Certificats | | - Créez une demande de support 60 jours avant l’expiration d’un certificat, en demandant des informations sur une modification de configuration planifiée, y compris les détails de configuration, l’étendue, la chronologie et d’autres détails pertinents que Microsoft peut examiner.<br>- Appliquez une modification uniquement une fois que les opérations du bureau géré Microsoft ont été évaluées et conseillées.<br>- Mettez à jour tous les certificats requis pour configurer les profils de certificat, les profils VPN et Wi-Fi profils.




## <a name="device-wipe-with-factory-reset"></a>Réinitialisation d’appareil avec réinitialisation aux usine

L’équipe Microsoft Managed Desktop Operations peut effectuer une réinitialisation d’usine des appareils inscrits au service si nécessaire. La réinitialisation est utile si vous devez donner un appareil à un autre employé ou si un employé quitte votre entreprise. 

Il existe quelques conditions requises :

- Votre administrateur général doit envoyer une demande de service.
- Incluez le nom de l’ordinateur de l’appareil dans la demande.
- Le compte d’utilisateur doit se trouver dans Azure AD avant de réinitialiser l’appareil.

L’équipe Des opérations de bureau gérés va :

- Rechercher le nom de l’appareil dans Intune
- Envoyer la commande de réinitialisation d’usine à l’appareil

>[!NOTE]
>Ne supprimez pas le compte d’utilisateur d’Azure AD avant la réinitialisation de l’appareil. Si l’utilisateur n’est pas dans Azure AD, Intune ne peut pas envoyer la commande de réinitialisation d’usine à l’appareil. 

L’appareil démarre dans l’expérience « out of box experience », et toutes les applications et paramètres préinstallés sont à nouveau appliqués. L’utilisateur de l’appareil doit fournir à nouveau les informations d’installation initiales. 

Lorsque l’appareil a été réinitialisé, vous pouvez le donner à une autre personne de votre organisation. Aucune des données de l’utilisateur précédent ou des données d’entreprise ne sera sur l’appareil. L’utilisateur suivant va passer par le même processus que la personne précédente avec un nouvel appareil bureau géré Microsoft.

BitLocker est un composant clé de la sécurité des données dans ce processus. Avec le chiffrement BitLocker sur les appareils de bureau géré Microsoft, les données sur le lecteur restent sécurisées même après la réinitialisation d’usine de l’appareil. Les données qui se trouvaient sur le lecteur ne seront pas disponibles pour le prochain utilisateur de l’appareil. Pour plus d’informations, voir [vue d’ensemble de BitLocker.](/windows/security/information-protection/bitlocker/bitlocker-overview)

Pour plus d’informations, voir [Réinitialiser un appareil aux états d’usine.](/intune/remote-actions/devices-wipe#factory-reset-a-device)