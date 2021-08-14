---
title: Récupérer après une attaque par rançongiciel
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Microsoft 365 administrateurs peuvent apprendre à récupérer d’une attaque par ransomware.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b7511039c1d33722790e993e8cd9c8c89e1e620b2585255359cb14f59ddb1ece
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56850705"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Récupérer d’une attaque par ransomware dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Même si vous prenez toutes les précautions nécessaires pour protéger votre organisation, vous pouvez toujours être la victime d’une attaque par [ransomware.](/windows/security/threat-protection/intelligence/ransomware-malware) Les ransomware sont une grande entreprise et les attaques sont très sophistiquées.

Les étapes de cet article vous offrent la meilleure opportunité de récupérer des données et d’arrêter la propagation interne de l’infection. Avant de commencer, prenez en compte les éléments suivants :

- Il n’existe aucune garantie que le paiement de la rançon retourne l’accès à vos fichiers. En fait, le paiement de la rançon peut faire de vous une cible pour d’autres ransomware.

  Si vous avez déjà payé, mais que vous avez récupéré sans utiliser la solution de l’attaquant, contactez votre banque pour voir si elle peut bloquer la transaction.

  Nous vous recommandons également de signaler l’attaque par ransomware aux forces de l’ordre, aux sites web de signalement des fraudes et à Microsoft, comme décrit plus loin dans cet article.

- Il est important que vous répondiez rapidement à l’attaque et à ses conséquences. Plus vous patientez longtemps, moins il est probable que vous récupériez les données affectées.

## <a name="step-1-verify-your-backups"></a>Étape 1 : Vérifier vos sauvegardes

Si vous avez des sauvegardes hors connexion,  vous pouvez probablement restaurer les données chiffrées après avoir supprimé la charge utile de ransomware (programmes malveillants) de votre environnement.

Si vous n’avez pas de sauvegardes ou si vos sauvegardes ont également été affectées par le ransomware, vous pouvez ignorer cette étape.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>Étape 2 : Désactiver les Exchange ActiveSync et Synchronisation OneDrive

Le point clé ici est d’arrêter la propagation du chiffrement des données par le ransomware.

Si vous pensez que le courrier électronique est une cible du chiffrement de ransomware, désactivez temporairement l’accès des utilisateurs aux boîtes aux lettres. Exchange ActiveSync synchronise les données entre les appareils et Exchange Online boîtes aux lettres.

Pour désactiver la Exchange ActiveSync d’une boîte aux lettres, voir Comment désactiver la Exchange ActiveSync pour les utilisateurs [dans Exchange Online](https://support.microsoft.com/help/2795303).

Pour désactiver d’autres types d’accès à une boîte aux lettres, voir :

- [Activez ou désactivez MAPI pour une boîte aux lettres.](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi)

- [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

L’interruption Synchronisation OneDrive permet de protéger vos données cloud contre la mise à jour par des appareils potentiellement infectés. Pour plus d’informations, [voir Comment suspendre et reprendre la synchronisation dans OneDrive](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>Étape 3 : Supprimer les programmes malveillants des appareils concernés

Exécutez une analyse antivirus complète et actuelle sur tous les ordinateurs et appareils suspectés de détecter et de supprimer la charge utile associée au ransomware.

N’oubliez pas d’analyser les appareils qui synchronisent des données ou les cibles des lecteurs réseau mappés.

Vous pouvez utiliser [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) ou (pour les clients [plus anciens) Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

Une alternative qui vous aidera également à supprimer des ransomware ou des programmes malveillants est l’outil de suppression de logiciels malveillants [(MSRT).](https://www.microsoft.com/download/details.aspx?id=9905)

Si ces options ne fonctionnent pas, vous pouvez essayer Windows Defender [hors](https://support.microsoft.com/help/17466) connexion ou résoudre les problèmes liés à la détection et à la suppression [de programmes malveillants.](https://support.microsoft.com/help/4466982)

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>Étape 4 : Récupérer des fichiers sur un ordinateur ou un appareil nettoyé

Une fois que vous avez terminé l’étape précédente pour supprimer la charge utile du ransomware de [](https://support.microsoft.com/help/17128) votre environnement (ce qui empêchera le ransomware de chiffrer ou de supprimer vos fichiers), vous pouvez utiliser l’historique des fichiers dans Windows 10 et Windows 8.1 ou protection système dans Windows 7 pour tenter de récupérer vos fichiers et dossiers locaux.

**Remarques** :

- Certains ransomware chiffrent ou suppriment également les versions de sauvegarde, vous ne pouvez donc pas utiliser l’historique des fichiers ou la Protection système pour restaurer des fichiers. Si cela se produit, vous devez utiliser des sauvegardes sur des lecteurs externes ou des appareils qui n’ont pas été affectés par le ransomware ou OneDrive comme décrit dans la section suivante.

- Si un dossier est synchronisé avec OneDrive et que vous n’utilisez pas la dernière version de Windows, l’utilisation de l’historique des fichiers peut être limitée.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>Étape 5 : Récupérer vos fichiers dans votre OneDrive Entreprise

La restauration de fichiers OneDrive Entreprise vous permet de restaurer l’intégralité de votre OneDrive à un point antérieur dans le temps au cours des 30 derniers jours. Pour plus dʼinformations, voir [Restaurer votre espace OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>Étape 6 : Récupérer les messages supprimés

Dans les rares cas où le ransomware a supprimé tous vos messages électroniques, vous pouvez probablement récupérer les éléments supprimés. Si vous souhaitez en savoir plus, veuillez consulter les rubrique suivantes :

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

## <a name="additional-ransomware-resources"></a>Ressources supplémentaires sur les ransomware

Informations clés sur le secteur :

- [Vue d’ensemble des ransomware gérés par l’humain](/security/compass/human-operated-ransomware)

- [Se protéger rapidement contre les ransomware et les attaques](/security/compass/protect-against-ransomware)

- [Le dernier rapport Renseignement de sécurité Microsoft de données](https://www.microsoft.com/securityinsights/) (voir les pages 22 à 24)

- **Ransomware : rapport sur les menaces** courantes et les menaces dans le nœud **d’analyse** des menaces du portail Microsoft 365 Defender (consultez ces exigences en matière de [licences)](/microsoft-365/security/defender/prerequisites#licensing-requirements)

Microsoft 365 protection :

- [Protection contre les ransomware et programmes malveillants](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Détection de ransomware et récupération de vos fichiers dans OneDrive](https://support.microsoft.com/office/0d90ec50-6bfd-40f4-acc7-b8c12c73637f)
- [Activer ou désactiver des macros dans Office fichiers](https://support.microsoft.com/office/12b036fd-d140-4e74-b45e-16fed1a7e5c6)
- [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365.md)

Billets de blog de l’équipe de sécurité Microsoft :

- [Devenir résilient en comprenant les risques de cybersécurité : partie 4 : navigation avec les menaces actuelles (mai 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Consultez la section **Ransomware.**

- [Attaques par ransomware gérées par l’homme : un sinistre qui peut être évité (mars 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)
- [Réponse de ransomware : payer ou ne pas payer ? (Décembre 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [NorskQue répond aux attaques par ransomware avec transparence (décembre 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
- [Une mise à niveau fiable : la sécurité de nouvelle génération sur Windows 10 s’avère résiliente contre les attaques de ransomware en 2017 (janvier 2018)](https://www.microsoft.com/security/blog/2018/01/10/a-worthy-upgrade-next-gen-security-on-windows-10-proves-resilient-against-ransomware-outbreaks-in-2017/)

