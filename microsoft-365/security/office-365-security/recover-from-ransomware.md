---
title: Récupérer après une attaque par rançongiciel
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365 administrateurs peuvent apprendre à récupérer d’une attaque par ransomware.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: da9b53aec47231446571a2ae5852bed842311079
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60552679"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Récupérer d’une attaque par ransomware dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Même si vous prenez toutes les précautions nécessaires pour protéger votre organisation, vous pouvez toujours être la victime d’une attaque par [ransomware.](/windows/security/threat-protection/intelligence/ransomware-malware) Les ransomware sont une grande entreprise et, dans le paysage actuel des menaces, Microsoft 365 est une cible croissante [pour les attaques sophistiquées.](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Cloudy-With-A-Chance-Of-APT-Novel-Microsoft-365-Attacks-In-The-Wild.pdf)

Les étapes de cet article vous offrent la meilleure opportunité de récupérer des données et d’arrêter la propagation interne de l’infection. Avant de commencer, prenez en compte les éléments suivants :

- Il n’existe aucune garantie que le paiement de la rançon retourne l’accès à vos fichiers. En fait, le paiement de la rançon peut faire de vous une cible pour d’autres ransomware.

  Si vous avez déjà payé, mais que vous avez récupéré sans utiliser la solution de l’attaquant, contactez votre banque pour voir si elle peut bloquer la transaction.

  Nous vous recommandons également de signaler l’attaque par ransomware aux forces de l’ordre, aux sites web de signalement des fraudes et à Microsoft, comme décrit plus loin dans cet article.

- Il est important que vous répondiez rapidement à l’attaque et à ses conséquences. Plus vous patientez longtemps, moins il est probable que vous récupériez les données affectées.

## <a name="step-1-verify-your-backups"></a>Étape 1 : Vérifier vos sauvegardes

Si vous avez des sauvegardes hors connexion,  vous pouvez probablement restaurer les données chiffrées après  avoir supprimé la charge utile de ransomware (programmes malveillants) de votre environnement et après avoir vérifié qu’il n’existe aucun accès non autorisé dans vos environnements Microsoft 365.

Si vous n’avez pas de sauvegardes ou si vos sauvegardes ont également été affectées par le ransomware, vous pouvez ignorer cette étape.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>Étape 2 : Désactiver les Exchange ActiveSync et Synchronisation OneDrive

Le point clé ici est d’arrêter la propagation du chiffrement des données par le ransomware.

Si vous pensez que le courrier électronique est une cible du chiffrement de ransomware, désactivez temporairement l’accès des utilisateurs aux boîtes aux lettres. Exchange ActiveSync synchronise les données entre les appareils et Exchange Online boîtes aux lettres.

Pour désactiver la Exchange ActiveSync d’une boîte aux lettres, voir Comment désactiver la Exchange ActiveSync pour les utilisateurs [dans Exchange Online](https://support.microsoft.com/help/2795303).

Pour désactiver d’autres types d’accès à une boîte aux lettres, voir :

- [Activez ou désactivez MAPI pour une boîte aux lettres.](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi)

- [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

L’interruption Synchronisation OneDrive permet de protéger vos données cloud contre la mise à jour par des appareils potentiellement infectés. Pour plus d’informations, [voir Comment suspendre](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e)et reprendre la synchronisation dans OneDrive .

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>Étape 3 : Supprimer les programmes malveillants des appareils concernés

Exécutez une analyse antivirus complète et actuelle sur tous les ordinateurs et appareils suspectés de détecter et de supprimer la charge utile associée au ransomware.

N’oubliez pas d’analyser les appareils qui synchronisent des données ou les cibles des lecteurs réseau mappés.

Vous pouvez utiliser [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) ou (pour les clients [plus anciens) Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

Une alternative qui vous aidera également à supprimer des ransomware ou des programmes malveillants est l’outil de suppression de logiciels malveillants [(MSRT).](https://www.microsoft.com/download/details.aspx?id=9905)

Si ces options ne fonctionnent pas, vous pouvez essayer Windows Defender [hors](https://support.microsoft.com/help/17466) connexion ou résoudre les problèmes de détection et de suppression de programmes [malveillants.](https://support.microsoft.com/help/4466982)

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>Étape 4 : Récupérer des fichiers sur un ordinateur ou un appareil nettoyé

Une fois que vous avez terminé l’étape précédente pour supprimer la charge utile de ransomware de [](https://support.microsoft.com/help/17128) votre environnement (ce qui empêchera le ransomware de chiffrer ou de supprimer vos fichiers), vous pouvez utiliser l’historique des fichiers dans Windows 11, Windows 10, Windows 8.1 et à l’aide de la Protection système dans Windows 7 pour essayer de récupérer vos fichiers et dossiers locaux.

**Remarques** :

- Certains ransomware chiffrent ou suppriment également les versions de sauvegarde, vous ne pouvez donc pas utiliser l’historique des fichiers ou la Protection système pour restaurer des fichiers. Si cela se produit, vous devez utiliser des sauvegardes sur des lecteurs externes ou des appareils qui n’ont pas été affectés par le ransomware ou OneDrive comme décrit dans la section suivante.

- Si un dossier est synchronisé avec OneDrive et que vous n’utilisez pas la dernière version de Windows, l’utilisation de l’historique des fichiers peut être limitée.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>Étape 5 : Récupérer vos fichiers dans votre OneDrive Entreprise

La restauration de fichiers OneDrive Entreprise vous permet de restaurer l’intégralité de votre OneDrive à un point antérieur dans le temps au cours des 30 derniers jours. Pour plus dʼinformations, voir [Restaurer votre espace OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>Étape 6 : Récupérer les messages supprimés

Dans les rares cas où le ransomware a supprimé tous vos messages électroniques, vous pouvez probablement récupérer les éléments supprimés. Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Récupérer des messages supprimés dans la boîte aux lettres d’un utilisateur](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Récupérer des éléments supprimés dans Outlook pour Windows](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>Étape 7 : Ré-activer Exchange ActiveSync et Synchronisation OneDrive

Après avoir nettoyé vos ordinateurs et appareils et récupéré vos données, vous pouvez réactiver Exchange ActiveSync et Synchronisation OneDrive que vous avez précédemment désactivés à l’étape [2.](#step-2-disable-exchange-activesync-and-onedrive-sync)

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>Étape 8 (facultative) : bloquer les Synchronisation OneDrive pour des extensions de fichier spécifiques

Une fois que vous avez récupéré, vous pouvez empêcher les clients OneDrive Entreprise de synchroniser les types de fichiers qui ont été affectés par ce ransomware. Pour plus d’informations, [voir Set-SPOTenantSyncClientRestriction](/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>Signaler l’attaque

### <a name="contact-law-enforcement"></a>Contacter l’application de la loi

Vous devez contacter vos autorités judiciaires locales ou fédérales. Par exemple, si vous êtes aux États-Unis, vous pouvez contacter le [bureau local DE LASV](https://www.fbi.gov/contact-us/field), [IC3](http://www.ic3.gov/complaint/default.aspx) ou [le service secret](http://www.secretservice.gov/).

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>Envoyer un rapport sur le site web de signalement des fraudes de votre pays

Les sites web de signalement des fraudes fournissent des informations sur la prévention et la prévention des fraudes. Ils fournissent également des mécanismes permettant de signaler si vous avez été victime d’une fraude.

- Australie : [SCAMwatch](http://www.scamwatch.gov.au/)

- Canada : [Centre anti-fraude canadien](http://www.antifraudcentre-centreantifraude.ca/)

- France : [Agence nationale de la sécurité des systèmes d’information](http://www.ssi.gouv.fr/)

- Allemagne : [ContrôleAmt für Sicherheit in der Informationstechnik](https://www.bsi.bund.de/DE/Home/home_node.html)

- Irlande : [An Síochána](http://www.garda.ie/)

- Nouvelle-Zélande : [fraudes de consommateur](http://www.consumeraffairs.govt.nz/scams)

- [Suisse National Zenheit für Cybersicherheit NCSC](https://www.ncsc.admin.ch/ncsc/de/home.html)

- Royaume-Uni : fraude [d’action](http://www.actionfraud.police.uk/)

- États-Unis : [Sur Guard Online](http://www.onguardonline.gov/)

Si votre pays n’est pas répertorié, demandez à vos autorités judiciaires locales ou fédérales.

### <a name="submit-email-messages-to-microsoft"></a>Envoyer des messages électroniques à Microsoft

Vous pouvez signaler des messages de hameçonnage qui contiennent un ransomware à l’aide de l’une des méthodes. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="additional-ransomware-resources"></a>Ressources supplémentaires sur les rançongiciels

Informations clés de Microsoft :

- [Menace croissante des rançongiciels](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), billet de blog Microsoft On the Issues du 20 juillet 2021
- [Rançongiciel géré par l’humain](/security/compass/human-operated-ransomware)
- [Se protéger rapidement contre les rançongiciels et les attaques](/security/compass/protect-against-ransomware)
- [Rapport de défense numérique Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (voir les pages 10 à 19)
- [Ransomware : rapport d’analyse des menaces](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) en cours et de menaces sur le portail Microsoft 365 Defender client


Microsoft 365 :

- [Déployer la protection contre les rançongiciels pour votre client Microsoft 365](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Optimisez la résilience aux ransomwares avec Azure et Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Protection contre les rançongiciels et programmes malveillants](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Protéger votre PC Windows contre les ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Gérer les rançongiciels dans SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Rapports d’analyse des menaces pour les ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) dans le portail Microsoft 365 Defender web

Microsoft 365 Defender :

- [Rechercher un rançongiciel avec la recherche avancée](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure :

- [Défenses Azure pour les attaques par rançongiciel](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Optimisez la résilience aux ransomwares avec Azure et Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Plan de sauvegarde et de restauration pour se protéger contre les rançongiciels](/security/compass/backup-plan-to-protect-against-ransomware)
- [Protéger contre les ransomware avec Microsoft Azure sauvegarde](https://www.youtube.com/watch?v=VhLOr2_1MCg) (vidéo de 26 minutes)
- [Récupération d’une compromission d’identité systémique](/azure/security/fundamentals/recover-from-identity-compromise)
- [Détection avancée d’attaques à plusieurs niveaux dans Azure Sentinel](/azure/sentinel/fusion#ransomware)
- [Détection de fusion pour rançongiciel dans Azure Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Cloud App Security :

-  [Créer des stratégies de détection des anomalies dans Cloud App Security](/cloud-app-security/anomaly-detection-policy)

Billets de blog de l’équipe de sécurité Microsoft :

- [3 étapes pour empêcher et récupérer à partir d’un rançongiciel (septembre 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [Devenir résilient en comprenant les risques de cybersécurité : partie 4 : navigation avec les menaces actuelles (mai 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Consultez la section **Rançongiciel**.

- [Attaques par rançongiciels contrôlés par l’homme : un sinistre pouvant être évité (mars 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Inclut des analyses de chaîne d’attaques des attaques réelles.

- [Réponse au rançongiciel : payer ou ne pas payer ? (Décembre 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro répond aux attaques par rançongiciel avec transparence (décembre 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
