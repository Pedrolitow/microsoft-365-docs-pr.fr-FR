---
title: Récupérer après une attaque par rançongiciel
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.article: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Les administrateurs de Microsoft 365 peuvent découvrir comment effectuer une récupération suite à une attaque par ransomware.
ms.openlocfilehash: ad3f044e338abeb56046538bdda8df7b8510be0e
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615899"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Récupération d’une attaque par ransomware dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Même si vous avez toutes les précautions à prendre pour protéger votre organisation, vous pouvez toujours devenir victime d’une attaque par [ransomware](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware) . Les ransomware sont de grandes entreprises et les attaques sont très sophistiquées.

Les étapes décrites dans cet article vous permettront de récupérer les données et d’arrêter la propagation interne de l’infection. Avant de commencer, prenez en compte les éléments suivants :

- Il n’existe aucune garantie que le fait de payer le ransomware renverra l’accès à vos fichiers. En fait, le paiement du ransomware peut vous faire une cible pour plus de ransomware.

  Si vous avez déjà payé, mais que vous avez récupéré sans utiliser la solution de l’agresseur, contactez votre banque pour savoir si elle peut bloquer la transaction.

  Nous vous recommandons également de signaler les attaques par ransomware à l’application de la Loi, les sites Web de notification de fraude et Microsoft, comme décrit plus loin dans cet article.

- Il est important pour vous de répondre rapidement à l’attaque et ses conséquences. Plus vous patientez, moins vous pouvez récupérer les données affectées.

## <a name="step-1-verify-your-backups"></a>Étape 1 : vérifier vos sauvegardes

Si vous avez des sauvegardes hors connexion, vous pouvez probablement restaurer les données chiffrées **après avoir** supprimé la charge du ransomware (programme malveillant) de votre environnement.

Si vous n’avez pas de sauvegardes, ou si vos sauvegardes ont également été affectées par le ransomware, vous pouvez ignorer cette étape.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>Étape 2 : désactivation de la synchronisation Exchange ActiveSync et OneDrive

Le point important ici est d’arrêter la propagation du chiffrement des données par les ransomware.

Si vous suspectez un courrier électronique en tant que cible du chiffrement de ransomware, désactivez temporairement l’accès des utilisateurs aux boîtes aux lettres. Exchange ActiveSync synchronise les données entre les appareils et les boîtes aux lettres Exchange Online.

Pour désactiver Exchange ActiveSync pour une boîte aux lettres, consultez [la rubrique How to Disable Exchange ActiveSync for users in Exchange Online](https://support.microsoft.com/help/2795303).

Pour désactiver d’autres types d’accès à une boîte aux lettres, voir :

- [Activer ou désactiver MAPI pour une boîte aux lettres](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).

- [Activer ou désactiver l’accès POP3 ou IMAP4 pour un utilisateur](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

La suspension de la synchronisation de OneDrive permettra de protéger vos données de Cloud contre la mise à jour des appareils potentiellement infectés. Pour plus d’informations, consultez [la rubrique How to pause and Resume Sync in OneDrive](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>Étape 3 : supprimer le programme malveillant des appareils affectés

Exécutez une analyse antivirus complète et active sur tous les ordinateurs et appareils suspects pour détecter et supprimer la charge utile associée aux ransomware.

N’oubliez pas d’analyser les périphériques qui synchronisent des données ou les cibles des lecteurs réseau mappés.

Vous pouvez utiliser [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) ou (pour les clients plus anciens) [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

L' [outil de suppression des logiciels malveillants (MSRT)](https://www.microsoft.com/download/details.aspx?id=9905)peut également être utilisé pour supprimer des ransomware ou des programmes malveillants.

Si ces options ne fonctionnent pas, vous pouvez essayer [Windows Defender Offline](https://support.microsoft.com/help/17466) ou [résoudre les problèmes liés à la détection et à la suppression de programmes malveillants](https://support.microsoft.com/help/4466982).

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>Étape 4 : récupérer des fichiers sur un ordinateur ou un périphérique nettoyé

Une fois que vous avez terminé l’étape précédente pour supprimer la charge du ransomware de votre environnement (ce qui empêchera les ransomware de chiffrer ou supprimer vos fichiers), vous pouvez utiliser [l’historique des fichiers](https://support.microsoft.com/help/17128) dans Windows 10 et Windows 8,1 ou la protection du système dans Windows 7 pour tenter de récupérer vos fichiers et dossiers locaux.

**Remarques** :

- Certains ransomware seront également en mesure de chiffrer ou de supprimer les versions de sauvegarde, de sorte que vous ne pouvez pas utiliser l’historique des fichiers ou la protection du système pour restaurer des fichiers. Dans ce cas, vous devez utiliser des sauvegardes sur des lecteurs externes ou des périphériques qui n’ont pas été affectés par le ransomware ou le OneDrive, comme décrit dans la section suivante.

- Si un dossier est synchronisé avec OneDrive et que vous n’utilisez pas la dernière version de Windows, certaines limites peuvent se présenter à l’aide de l’historique des fichiers.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>Étape 5 : récupération de vos fichiers dans OneDrive entreprise

La restauration des fichiers dans OneDrive entreprise vous permet de restaurer l’intégralité de votre OneDrive à un point antérieur dans le temps au cours des 30 derniers jours. Pour plus d’informations, consultez [la rubrique restaurer votre espace OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>Étape 6 : récupérer les messages électroniques supprimés

Dans le cas rare où le ransomware a supprimé tous vos courriers électroniques, vous pouvez probablement récupérer les éléments supprimés. Pour plus d’informations, voir :

- [Récupérer des messages supprimés dans la boîte aux lettres d’un utilisateur](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Récupérer des éléments supprimés dans Outlook pour Windows](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>Étape 7 : réactivation de la synchronisation Exchange ActiveSync et OneDrive

Une fois que vous avez nettoyé vos ordinateurs et vos appareils et récupéré vos données, vous pouvez réactiver Exchange ActiveSync et la synchronisation OneDrive précédemment désactivée à l' [étape 2](#step-2-disable-exchange-activesync-and-onedrive-sync).

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>Étape 8 (facultatif) : bloquer la synchronisation de OneDrive pour des extensions de fichier spécifiques

Une fois que vous avez effectué la récupération, vous pouvez empêcher les clients OneDrive entreprise de synchroniser les types de fichiers qui ont été affectés par ces ransomware. Pour plus d’informations, consultez la rubrique [Set-SPOTenantSyncClientRestriction](https://docs.microsoft.com/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>Signaler l’attaque

### <a name="contact-law-enforcement"></a>Application de la Loi sur les contacts

Vous devez contacter vos organismes d’application de la loi fédérale ou locale. Par exemple, si vous êtes aux États-Unis, vous pouvez contacter le service de [terrain local FBI](https://www.fbi.gov/contact-us/field), le [IC3](http://www.ic3.gov/complaint/default.aspx) ou le [service secret](http://www.secretservice.gov/).

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>Envoyer un rapport sur le site Web de notification d’escroquerie de votre pays

Les sites Web de signalement de fraude fournissent des informations sur la façon d’empêcher et d’éviter les arnaques. Ils fournissent également des mécanismes de signalement si vous avez été victime d’une escroquerie.

- Australie : [SCAMwatch](http://www.scamwatch.gov.au/)

- Canada : [Centre anti-fraude canadien](http://www.antifraudcentre-centreantifraude.ca/)

- France : [Agence nationale de la sécurité des systèmes d’information](http://www.ssi.gouv.fr/)

- Allemagne : [Bundesamt für Sicherheit dans der Informationstechnik](https://www.bsi.bund.de/DE/Home/home_node.html)

- Irlande : [un Garda Síochána](http://www.garda.ie/)

- Nouvelle-Zélande : [arnaques](http://www.consumeraffairs.govt.nz/scams) pour les consommateurs

- Royaume-Uni : [fraude d’action](http://www.actionfraud.police.uk/)

- États-Unis : [on Guard Online](http://www.onguardonline.gov/)

Si votre pays n’est pas indiqué, demandez à vos organismes d’application de la loi locale ou fédérale.

### <a name="submit-email-messages-to-microsoft"></a>Envoyer des messages électroniques à Microsoft

Vous pouvez signaler les messages de hameçonnage contenant des ransomware à l’aide de l’une des méthodes suivantes. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="see-also"></a>Voir aussi

- [Rançongiciels](https://docs.microsoft.com/windows/security/threat-protection/intelligence/ransomware-malware)

- [Réponse contre les ransomware : souhaitez-vous payer ou ne pas payer ?](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)

- [Norsk Hydro répond aux attaques par ransomware avec transparence](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)

- [Détection de ransomware et RECUPERATION de vos fichiers dans OneDrive](https://support.microsoft.com/office/0d90ec50-6bfd-40f4-acc7-b8c12c73637f)

- [Rapport sur les renseignements de sécurité Microsoft](https://www.microsoft.com/securityinsights/)

- [Activer ou désactiver les macros dans les fichiers Office](https://support.microsoft.com/office/12b036fd-d140-4e74-b45e-16fed1a7e5c6)

- [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](recommended-settings-for-eop-and-office365-atp.md)

- [Une mise à niveau fiable : la sécurité de la génération suivante sur Windows 10 s’avère résiliente contre les foyers de ransomware dans 2017](https://www.microsoft.com/security/blog/2018/01/10/a-worthy-upgrade-next-gen-security-on-windows-10-proves-resilient-against-ransomware-outbreaks-in-2017/)

- [Aucune Mas, Samas : qu’est-ce que le modus operandi de ce ransomware ?](https://www.microsoft.com/security/blog/2016/03/17/no-mas-samas-whats-in-this-ransomwares-modus-operandi/)

- [Protection contre les programmes malveillants, la chance de l’éviter](https://www.microsoft.com/security/blog/2016/02/24/locky-malware-lucky-to-avoid-it/)

- [MSRT juillet 2016 : cerber ransomware](https://www.microsoft.com/security/blog/2016/07/12/msrt-july-2016-cerber-ransomware/)

- [Les trois têtes du Cerberus cerber ransomware](https://www.microsoft.com/security/blog/2016/03/09/the-three-heads-of-the-cerberus-like-cerber-ransomware/)

- [Troldesh ransomware influencé par (le) Code da Vinci](https://www.microsoft.com/security/blog/2016/07/13/troldesh-ransomware-influenced-by-the-da-vinci-code/)
