---
title: Opérations de l’ordinateur de bureau Microsoft et de surveillance
description: ''
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: jdeckerms
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 00bdc95c191ce16be219cf0dc251f72eaf054e22
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867013"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Opérations de l’ordinateur de bureau Microsoft et de surveillance

<!-- Operations and monitoring: -->


## <a name="change-management"></a>Gestion du changement

Microsoft et les clients partagent gestion des modifications pour le service de bureau Microsoft. Responsabilités diffèrent pour un service en ligne par rapport à un client ou un serveur local. 

### <a name="change-process-overview"></a>Vue d’ensemble du processus de modification

Voici un résumé de la façon dont le processus de modification est partagé entre Microsoft et les clients. 



<table>
<tr><th></th><th><p>Microsoft est :</p></th><th><p>Les clients sont :</p></th></tr>
<tr><td>Avant une modification</td><td><ul><li>Informer les clients 5 jours à l’avance pour les modifications qui nécessitent une action de l’administrateur.</li><li>Pour les modifications d’urgence, appliquer une atténuation avant la notification.</li></ul></td><td><ul><li>Lisez et assimilez message électronique de notification.</li><li>Confirmer et d’approuver, lorsque cela est nécessaire.</li></ul></td></tr><tr><td>Pendant une modification</td><td><ul><li>Déployer des modifications pour 10 Windows et Office, version de sécurité et les mises à jour de sécurité, selon vos besoins.</li><li>Analyser la télémétrie et prendre en charge les remontées des problèmes inattendus.</li></ul></td><td><ul><li>Gérer les processus de gestion des modifications interne.</li><li>Créer une demande de prise en charge, si nécessaire.</li></ul></td></tr><tr><td>Après une modification</td><td><ul><li>Recueillir les commentaires client afin d’améliorer le déploiement de modifications ultérieures.</li><li>Analyser la télémétrie et prendre en charge les remontées des problèmes inattendus.</li></ul></td><td><ul><li>Lisez et assimilez message électronique de notification.</li><li>Fournir des commentaires généraux et des commentaires dans l’outil de commentaires d’administration spécifiques.</li><li>Former les utilisateurs à fournir des commentaires spécifiques à l’application à l’aide du concentrateur de commentaires Windows et le bouton sourire dans les applications Office.</li></ul></td></tr>
<table> 






### <a name="change-types"></a>Types de modification

Il existe plusieurs types de modifications apportées au service régulièrement. Le canal de communication pour ces modifications et les actions que les clients sont chargés de varie.

Les types de modifications suivants peuvent être attendus :

Type de modification | Notification | Action du client
--- | --- | ---
Mises à jour de la fonctionnalité et de nouveaux composants de service | Message électronique | -Communiquer les modifications aux utilisateurs<br><br> -Agir comme requis par Microsoft<br><br> -Vérification doit être effectuée dans 48 heures
Sécurité des mises à jour, les mises à jour tous les mois et les paramètres de base | Courrier électronique, des bulletins de sécurité ou entrée vulnérabilités courantes et risques (CVE) | -Mises à jour seront déployés à l’aide de notre [stratégie de gestion de mise à jour](updates.md)de sécurité tous les mois.<br><br> -Les paramètres pour réduire une menace seront déployés dans toute l’organisation pour protéger l’organisation. (CELA N’APPARAÎT PAS À UNE ACTION CLIENT)
Mises à jour de qualité, y compris les correctifs, mises à jour de service et stratégie de base du non à la sécurité | Message électronique | Signalera lorsque cela est nécessaire.
Mises à jour d’urgence : service, configuration ou logicielles requises de mises à jour pour atténuer les :<br><br> -Risques de sécurité critique<br><br> -Perte de données potentielle<br><br> -Accès aux données de télémétrie pour la gestion des périphériques de bureau Microsoft | Signalera lorsque cela est nécessaire.

## <a name="standard-operating-procedures"></a>Procédures d’exploitation standard

Ce service est implémenté et géré par Microsoft dans votre environnement où vous effectuer d’autres opérations d’administration. Microsoft chargée uniquement pour le programme d’installation, la configuration et opération Microsoft Managed Desktop spécifique. 

Pour les produits local, votre organisation prend toutes les responsabilités pour la gestion opérationnelle et les activités de configuration.

Categories |    Actions
--- | ---
Comptes de service |  Microsoft est :<br><br> -Mettre en œuvre, en toute sécurité stocker et gérer les informations d’identification<br><br> -Communiquer les accès non autorisés ou l’utilisation de ces informations d’identification à votre équipe des opérations de sécurité<br><br><br><br>Les clients sont :<br><br> -D’ouvrir une demande d’informations de prise en charge avec les opérations de bureau géré Microsoft lorsque vous planifiez une modification peut avoir un impact sur les comptes<br><br> -N’est pas attribuer la stratégie, l’authentification multifacteur, accès conditionnel ou le déploiement d’applications pour les comptes de Service Bureau géré Microsoft<br><br> -Pas réinitialiser le mot de passe ou utiliser les informations d’identification<br><br> -Ouvrir une demande de support Sev C aux opérations de bureau Microsoft si suspect est respectée dans les journaux d’audit Intune ou Azure, liés à ces comptes de service
Groupes de périphériques | Microsoft est :<br><br> -Mettre en œuvre et gérer l’appartenance des périphériques dans les groupes de l’ordinateur de bureau Microsoft<br><br> -Utilisez les groupes de l’ordinateur de bureau Microsoft pour gérer l’attribution et la version de configuration et de mises à jour de périphériques<br><br><br><br>Les clients sont :<br><br> -D’ouvrir une demande d’informations de prise en charge avec les opérations de bureau géré Microsoft lorsque vous planifiez une modification peut avoir un impact sur les groupes<br><br> -Pas modifier l’appartenance au groupe de n’importe quel ordinateur de bureau Microsoft<br><br> -Uniquement utiliser les groupes pour assigner des certificats d’entreprise pour les services, telles que VPN, Hello Windows pour le chiffrement de courrier électronique ou de l’entreprise, ou configuration d’un profil d’entreprise Wi-Fi<br><br> -Où se trouve la gestion, explicitement exclure tous les groupes de l’ordinateur de bureau Microsoft lorsque vous déployez le client Gestionnaire de Configuration
Policies |  Microsoft est :<br><br> -Mettre en œuvre et gérer les stratégies de bureau Microsoft qui régissent l’état de la configuration des périphériques au sein du service<br><br> -Déployer les mises à jour, à la stratégie ou Windows, de manière incrémentielle à l’aide de groupes de périphériques<br><br> -Exclure explicitement ciblage des groupes non - Microsoft de bureau<br><br><br><br>Client sera :<br><br> -Ouverture d’un ticket d’assistance d’information avec Microsoft gérées bureau Operations lors de la planification d’une modification peut avoir un impact sur l’état de la configuration de votre choix de périphériques<br><br> -Pas modifier ou affecter des stratégies de bureau Microsoft périphériques ou des utilisateurs non gérés par le service Microsoft de bureau
Windows Defender Advanced Threat Protection | Microsoft est :<br><br> -Surveiller et examiner les périphériques dans l’étendue du service Microsoft de bureau<br><br><br><br>Client sera :<br><br> -Ouverture d’un ticket d’assistance d’information avec Microsoft gérées bureau Operations lors de la planification d’une modification peut avoir un impact sur les fonctionnalités de surveillance ou investigation de Microsoft Managed Desktop Security Operations Center
Microsoft Store pour Entreprises |  Microsoft est :<br><br> -Configurer et mettre à jour le profil de pilote Windows pour le service Microsoft de bureau<br><br><br><br>Client sera :<br><br> -Ouverture d’un ticket d’assistance d’information avec opérations de bureau géré Microsoft lors de la planification d’une modification qu’ouvrir peut-être avoir un impact sur l’accès à la banque ou modifier le profil de pilote Microsoft gérées bureau Windows automatique<br><br> -Pas modifier la configuration du profil Microsoft gérées bureau Windows pilote ou Ajout/Suppression de périphériques affectés
Certificats |  Client sera :<br><br> -Ouvrir un ticket d’information de prise en charge avec Microsoft gérées bureau opérations 60 jours avant toute expiration du certificat<br><br> -Mettre à jour tous les certificats nécessaires à la configuration : profils, les profils VPN et profils Wi-Fi du certificat



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
