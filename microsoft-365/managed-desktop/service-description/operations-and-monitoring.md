---
title: Surveillance et opérations du bureau géré Microsoft
description: ''
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.topic: article
ms.openlocfilehash: 8355b1609746abee12e4ca02942a567fec940623
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846215"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Surveillance et opérations du bureau géré Microsoft

<!-- Operations and monitoring: -->


## <a name="change-management"></a>Gestion des modifications

Dans une offre de service, l’équilibre des responsabilités pour des opérations telles que la maintenance du matériel et les mises à jour relatives à la sécurité se déplace vers le fournisseur de services (Microsoft) plutôt que vers le client (vous). Toutefois, vous devez toujours vous assurer que les logiciels tiers et personnalisés continuent de fonctionner comme prévu lors de l’exécution des mises à jour.

Pour les produits sur site, votre organisation assume toutes les responsabilités en matière de gestion des modifications.

### <a name="balance-of-responsibility"></a>Équilibre des responsabilités

Responsibility | Service bureau géré Microsoft | Logiciel client Microsoft 365 | Serveurs et clients locaux | logiciels tiers et personnalisés
----- | ----- | ----- | ----- | -----
Fournir de nouvelles fonctionnalités | Microsoft | Microsoft | Les deux | Client
Tester de nouvelles fonctionnalités pour l’assurance qualité |  Microsoft | Microsoft | Les deux | Client
Communiquer sur les nouvelles fonctionnalités | Les deux | Les deux | Les deux | Client
Intégrer le logiciel personnalisé | Les deux | Les deux | Client | Client
Appliquer les mises à jour relatives à la sécurité | Microsoft | Microsoft | Client | Client
Gérer les logiciels système | Microsoft | Microsoft | Client | Client
Package pour le déploiement | Microsoft | Microsoft | Client | Client


### <a name="change-process-overview"></a>Vue d’ensemble du processus de modification

Voici un résumé de la façon dont le processus de modification est partagé entre Microsoft et les clients. 



<table>
<tr><th></th><th><p>Rôle de Microsoft :</p></th><th><p>Rôle du client :</p></th></tr>
<tr><td>Avant une modification</td><td><ul><li>Définir les attentes pour les modifications apportées au service.</li><li>Informer les clients 5 jours à l’avance pour les modifications qui requièrent l’intervention de l’administrateur.</li><li>Pour les modifications d’urgence, appliquez une atténuation avant de prévenir.</li></ul></td><td><ul><li>Comprendre les attentes pour les modifications et les communications.</li><li>Lisez régulièrement le centre de messages de bureau géré Microsoft.</li><li>Passer en revue et mettre à jour les processus de gestion des modifications internes.</li><li>Comprenez et vérifiez la conformité avec Microsoft Managed Desktop Requirements. </li><li>Accuser réception et approbation, le cas échéant.</li></ul></td></tr><tr><td>Pendant une modification</td><td><ul><li>Publier et déployer des mises à jour mensuelles de sécurité et non relatives à la sécurité pour les clients Windows 10 et Office 365.</li><li>Surveillez les signaux de données et les files d’attente de prise en charge.</li></ul></td><td><ul><li>Vérifiez le centre de messages du bureau géré Microsoft et examinez les informations supplémentaires.</li><li>   Effectuer les actions requises, le cas échéant, et tester les applications.</li><li>Si un scénario de réparation est pris en charge, créez une demande de support.</li></ul></td></tr><tr><td>Après une modification</td><td><ul><li>Recueillez les commentaires des clients afin d’améliorer le déploiement des futures modifications.</li><li>Surveillez les signaux de données et les files d’attente de prise en charge.</li></ul></td><td><ul><li>Collaborez avec les personnes de votre organisation pour adopter le changement.</li><li>   Passez en revue les processus de gestion des modifications et des adoptions pour gagner en efficacité.</li><li>Fournissez des commentaires généraux et des commentaires spécifiques dans l’outil de commentaires administrateur.</li><li>Former les utilisateurs à fournir des commentaires propres à l’application à l’aide du concentrateur de commentaires Windows et du bouton sourire dans les applications Office.</li></ul></td></tr>
<table> 






### <a name="change-types"></a>Types de modifications

Il existe plusieurs types de modifications apportées au service régulièrement. Le canal de communication pour ces modifications et les actions que les clients sont responsables de varient.

Toutes les modifications n’ont pas le même impact sur vos utilisateurs et ne nécessitent pas toutes une action. Certains sont planifiés et d’autres non planifiés par leur nature (les mises à jour non relatives à la sécurité et les mises à jour de sécurité ne sont généralement pas planifiées). Selon le type de modification, le canal de communication peut varier. Le tableau suivant répertorie les types de modifications que vous pouvez vous attendre pour le service bureau géré Microsoft.

|   | Les fonctionnalités |   Mises à jour non relatives à la sécurité |  Sécurité
--- | --- | --- | ---
**Type de modification** | -Mises à jour de fonctionnalités<br>-Nouvelles fonctionnalités ou applications<br>-Fonctionnalités déconseillées | Correctifs client pour des problèmes | Correctifs de sécurité
**Préavis** | 5 jours remarquent les modifications qui nécessitent une action |    Non, ces éléments sont inclus dans la publication mensuelle   | Non, ces éléments sont inclus dans la publication mensuelle 
**Canal de communication** | -Centre de messages<br>-Alerte par courrier électronique | -Centre de messages<br>-Alerte par courrier électronique | -Centre de messages<br>-Alerte par courrier électronique
**Nécessite une action d’administrateur global** | Parfois |  Rarement |    Rarement 
**Type d’action** | Modifier les paramètres | Communiquer les modifications aux utilisateurs | Modifier les paramètres d’administration     
**Nécessite un test** | Vérifier les applications métiers, y compris les services d’accès à distance |  Parfois : tests du correctif par rapport aux processus ou aux personnalisations |   Rarement 
**Exemples de modifications** | -Mises à jour de fonctionnalité : portail d’administration informatique simplifie l’envoi et la révision du ticket de support<br>-Nouvelles fonctionnalités ou applications : Semi-Annual publication d’une mise à jour de la fonctionnalité Windows 10 | Correctifs basés sur les bogues signalés par le client |  


## <a name="standard-operating-procedures"></a>Procédures d’exploitation standard

Le service Microsoft Managed Desktop est implémenté et géré par Microsoft dans votre instance de Cloud Microsoft où vous pouvez effectuer d’autres activités administratives. Microsoft est seul responsable de la configuration, de la configuration et du fonctionnement propres au bureau géré par Microsoft. 

Pour les produits sur site, votre organisation assume toutes les responsabilités liées à la gestion de la configuration, ainsi qu’aux activités de configuration et d’exploitation.

Catégories |    Microsoft va | Le client va
--- | --- | ---
Réseau (proxy, inspection de paquets, VPN)  | Conseillez et planifiez avec les clients pour limiter les risques pour les utilisateurs de l’entreprise. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.
Comptes de service |-Implémenter, stocker en toute sécurité et gérer les informations d’identification.<br> -Communiquer un accès non autorisé ou utiliser ces informations d’identification à votre équipe des opérations de sécurité. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.<br>-N’attribuez pas de stratégie, d’authentification multifacteur, d’accès conditionnel ou de déploiement d’application aux comptes de service de bureau géré Microsoft.<br>-Ne pas réinitialiser le mot de passe ou utiliser les informations d’identification.<br>-Ouvrez une demande de support gravité C pour Microsoft Managed Desktop Operations si l’activité suspecte est observée dans les journaux d’audit Intune ou Azure, associés à ces comptes de service.
Groupes d’appareils | : Implémentez et gérez l’appartenance des appareils dans les groupes de bureau gérés Microsoft.<br>-Utilisez les groupes de bureau gérés Microsoft pour gérer l’attribution et la publication de la configuration et des mises à jour sur les appareils. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.<br>-Ne modifiez pas l’appartenance à un groupe de bureau géré Microsoft.<br>-Utilisez uniquement les groupes pour attribuer des certificats d’entreprise pour des services tels que le VPN, Windows Hello entreprise ou le chiffrement de messagerie, ou pour la configuration de profil Wi-Fi d’entreprise.<br>-Où la co-gestion existe, excluez explicitement tous les groupes de bureau gérés par Microsoft lors du déploiement du client gestionnaire de configuration.
Stratégies |  -Implémenter et gérer les stratégies de bureau géré Microsoft qui régissent l’état de configuration des appareils au sein du service.<br>-Déployez les mises à jour, les stratégies ou les fenêtres, de manière incrémentielle, à l’aide de groupes d’appareils.<br> -Exclure explicitement le ciblage des groupes de bureau gérés non-Microsoft. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.<br>-Ne modifiez pas ou n’affectez pas de stratégies de bureau géré Microsoft aux appareils ou aux utilisateurs qui ne sont pas gérés par le service bureau géré Microsoft.
Microsoft Defender pour point de terminaison | Surveillez et examinez les appareils dans l’étendue du service bureau géré Microsoft. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé
Microsoft Store pour Entreprises |  Configurez et gérez le profil Windows AutoPilot pour le service de bureau géré Microsoft. | -Créez une demande de support demandant des informations pour une modification de configuration planifiée, y compris des détails de configuration, une étendue, une chronologie et d’autres informations pertinentes à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.<br>-Ne modifiez pas la configuration du profil Windows AutoPilot du bureau géré Microsoft ou ajoutez/supprimez des appareils attribués.
Certificats | | -Créez une demande de prise en charge de 60 jours avant l’expiration d’un certificat, en demandant des informations pour une modification de configuration planifiée, y compris des détails de la configuration, une étendue, une chronologie et d’autres détails pertinents à consulter pour Microsoft.<br>-Appliquer une modification une fois que Microsoft Managed Desktop Operations a été évalué et conseillé.<br>-Mettez à jour tous les certificats requis pour configurer des profils de certificats, des profils VPN et des profils de Wi-Fi.




## <a name="device-wipe-with-factory-reset"></a>Réinitialisation du périphérique avec la réinitialisation d’usine

L’équipe Microsoft Managed Desktop Operations peut effectuer une réinitialisation en usine des appareils qui sont déployés dans le service lorsque cela est nécessaire. Cela est utile si vous devez attribuer un appareil à un autre employé ou si un employé quitte votre entreprise. 

Voici quelques conditions requises :

- Votre administrateur général doit soumettre une demande de service.
- Incluez le nom de l’ordinateur de l’appareil dans la demande.
- Le compte d’utilisateur doit être dans Azure AD avant la réinitialisation de l’appareil.

L’équipe des opérations de bureau géré effectuera les opérations suivantes :

- Rechercher le nom de l’appareil dans Intune
- Envoyer la commande de réinitialisation usine au périphérique

>[!NOTE]
>Ne supprimez pas le compte d’utilisateur d’Azure AD avant la réinitialisation de l’appareil. Si l’utilisateur n’est pas dans Azure AD, Intune ne peut pas envoyer la commande de réinitialisation usine au périphérique. 

L’appareil démarrera dans l’expérience insuffisante et tous les paramètres et applications préinstallés seront de nouveau appliqués. L’utilisateur de l’appareil doit de nouveau fournir les informations de configuration initiales. 

Une fois que l’appareil a été réinitialisé, vous pouvez lui attribuer une autre personne au sein de votre organisation. Aucune des données de l’utilisateur ou de l’entreprise précédente ne se trouvera sur l’appareil. L’utilisateur suivant passera le même processus par la personne précédente avec un nouveau périphérique de bureau géré Microsoft.

BitLocker est un composant clé de la sécurité des données dans ce processus. Avec le chiffrement BitLocker sur des appareils de bureau gérés Microsoft, les données sur le lecteur restent sécurisées même après la réinitialisation de l’appareil. Les données qui se trouvaient sur le lecteur ne seront pas disponibles pour le prochain utilisateur de l’appareil. Pour plus d’informations, consultez la rubrique [vue d’ensemble de BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).

Pour plus d’informations, consultez [la rubrique Factory Reset a Device](https://docs.microsoft.com/intune/remote-actions/devices-wipe#factory-reset-a-device). 