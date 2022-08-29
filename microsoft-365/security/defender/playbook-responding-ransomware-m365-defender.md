---
title: Réponse aux attaques par rançongiciels
description: Cet article fournit un playbook généralisé pour répondre aux attaques par ransomware.
search.appverid: MET150
author: nic-name
ms.author: noriordan
manager: dolmont
audience: ITPro
ms.topic: article
ms.date: 05/30/2022
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.technology: m365d
f1.keywords: NOCSH
ms.openlocfilehash: aaf672f8ec913b8d0e206f9d630452bac36185ee
ms.sourcegitcommit: ab32c6e19af08837aaa84a058653c3a209d366ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2022
ms.locfileid: "67445091"
---
# <a name="responding-to-ransomware-attacks"></a>Réponse aux attaques par rançongiciels

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Lorsque vous pensez que vous êtes ou êtes actuellement sous une attaque par ransomware, établissez immédiatement des communications sécurisées avec votre équipe de réponse aux incidents. Ils peuvent effectuer les phases de réponse suivantes pour interrompre l’attaque et atténuer les dommages :

* Investigation et confinement
* Éradication et récupération

Cet article fournit un playbook généralisé pour répondre aux attaques par ransomware. Envisagez d’adapter les étapes et tâches décrites dans cet article à votre propre playbook d’opérations de sécurité.
REMARQUE : Pour plus d’informations sur la prévention des attaques par ransomware, consultez [Protection rapide contre les ransomware et l’extorsion](/security/compass/protect-against-ransomware).

## <a name="containment"></a>Confinement

L’endiguement et l’investigation doivent se produire aussi simultanément que possible; toutefois, vous devez vous concentrer sur la réalisation rapide de l’endiguement, de sorte que vous avez plus de temps pour examiner. Ces étapes vous aident à déterminer l’étendue de l’attaque et à l’isoler uniquement pour les entités affectées, telles que les comptes d’utilisateur et les appareils.

### <a name="step-1-assess-the-scope-of-the-incident"></a>Étape 1 : Évaluer l’étendue de l’incident

Exécutez cette liste de questions et de tâches pour découvrir l’étendue de l’attaque. Microsoft 365 Defender pouvez fournir une vue consolidée de toutes les ressources affectées ou à risque pour faciliter l’évaluation de votre réponse aux incidents. Consultez [la réponse aux incidents avec Microsoft 365 Defender](incidents-overview.md). Vous pouvez utiliser les alertes et la liste des preuves dans l’incident pour déterminer :

* Quels comptes d’utilisateur peuvent être compromis ?
  * Quels comptes ont été utilisés pour remettre la charge utile ?
* Quels appareils [intégrés](../defender-endpoint/investigate-machines.md) et [découverts](../defender-endpoint/device-discovery.md) sont affectés et comment ?
  * Appareils d’origine
  * Appareils affectés
  * Appareils suspects
* Identifiez toute communication réseau associée à l’incident.
* Quelles applications sont affectées ?
* Quelles charges utiles ont été réparties ?
* Comment l’attaquant communique-t-il avec les appareils compromis ? (La protection réseau doit être [activée)](../defender-endpoint/enable-network-protection.md) :
  * Accédez à la [page indicateurs](../defender-endpoint/indicator-ip-domain.md#create-indicators-for-ips-and-urlsdomains) pour ajouter un bloc pour l’ADRESSE IP et l’URL (si vous disposez de ces informations).
* Quel était le support de remise de charge utile ?

### <a name="step-2-preserve-existing-systems"></a>Étape 2 : Préserver les systèmes existants

Exécutez cette liste de tâches et de questions pour protéger les systèmes existants contre les attaques :

* Si vous disposez de sauvegardes en ligne, envisagez de déconnecter le système de sauvegarde du réseau jusqu’à ce que vous soyez certain que l’attaque est contenue. Consultez le [plan de sauvegarde et de restauration pour vous protéger contre les ransomware | Microsoft Docs](/security/compass/backup-plan-to-protect-against-ransomware).
* Si vous rencontrez ou attendez un déploiement de ransomware imminent et actif :
  * [Suspendez les comptes privilégiés et locaux](/investigate-users.md) que vous soupçonnez de faire partie de l’attaque. Vous pouvez le faire à partir de l’onglet **Utilisateurs** dans les propriétés de l’incident dans le portail Microsoft 365 Defender.
  * Arrêtez toutes les [sessions d’ouverture de session distantes](/defender-for-identity/playbook-domain-dominance).
  * Réinitialisez les mots de passe de compte d’utilisateur compromis et demandez aux utilisateurs des comptes d’utilisateur compromis de se reconnecter.
  * Procédez de la même manière pour les comptes d’utilisateur susceptibles d’être compromis.
  * Si des comptes locaux partagés sont compromis, votre administrateur informatique vous aide à appliquer une modification de mot de passe sur tous les appareils exposés. Exemple de requête Kusto :

```kusto
DeviceLogonEvents | where DeviceName  contains (AccountDomain) | take 10 
```

* Pour les appareils qui ne sont pas encore isolés et ne font pas partie de l’infrastructure critique :
  * Isolez les appareils compromis du réseau, mais ne les arrêtez pas.
  * Si vous identifiez les appareils d’origine ou de diffusion, isolez-les en premier.
* Conservez les systèmes compromis à des fins d’analyse.

### <a name="step-3-prevent-the-spread"></a>Étape 3 : Empêcher la propagation

Utilisez cette liste pour empêcher l’attaque de se propager à des entités supplémentaires.

* Si des comptes locaux partagés sont utilisés dans l’attaque, envisagez de [bloquer l’utilisation à distance des comptes locaux](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/blocking-remote-use-of-local-accounts/ba-p/701042).
  * Requête Kusto pour tous les journaux d’activité réseau qui sont des administrateurs locaux :

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* Requête Kusto pour les logons non-RDP (plus réaliste pour la plupart des réseaux) :

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName and LogonType != 'RemoteInteractive'
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* Mettez en quarantaine et ajoutez des indicateurs pour les fichiers infectés.
* Assurez-vous que votre solution antivirus est configurable dans son état de protection optimal. Pour l’Antivirus Microsoft Defender, cela inclut :
  * [La protection en temps réel](../defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus.md) est activée.
  * [La protection contre les falsifications](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md) est activée. Dans le portail Microsoft 365 Defender, sélectionnez **Paramètres > points de terminaison > fonctionnalités avancées > protection contre les falsifications**.
  * [Les règles de réduction de la surface d’attaque (ASR)](../defender-endpoint/enable-attack-surface-reduction.md) sont activées.
  * [La protection cloud](../defender-endpoint/enable-attack-surface-reduction.md) est activée.
* Désactivez Exchange ActiveSync et Synchronisation OneDrive.
  * Pour désactiver Exchange ActiveSync pour une boîte aux lettres, consultez [Comment désactiver Exchange ActiveSync pour les utilisateurs dans Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-exchange-activesync).
  * Pour désactiver d’autres types d’accès à une boîte aux lettres, consultez :
    * [Activez ou désactivez MAPI pour une boîte aux lettres](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).
    * [Activez ou désactivez l’accès POP3 ou IMAP4 pour un utilisateur](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access).
  * La suspension de Synchronisation OneDrive vous aidera à protéger vos données cloud contre la mise à jour par des appareils potentiellement infectés. Pour plus d’informations, consultez [Comment suspendre et reprendre la synchronisation dans OneDrive](https://support.microsoft.com/office/how-to-pause-and-resume-sync-in-onedrive-2152bfa4-a2a5-4d3a-ace8-92912fb4421e).
* Appliquez les correctifs appropriés et les modifications de configuration sur les systèmes affectés.
* Bloquez les communications par ransomware à l’aide de contrôles internes et externes.
* Vider le contenu mis en cache

## <a name="investigation"></a>Enquête

Utilisez cette section pour examiner l’attaque et planifier votre réponse.

### <a name="assess-your-current-situation"></a>Évaluer votre situation actuelle

* Qu’est-ce qui vous a initialement fait prendre conscience de l’attaque par ransomware?
  * Si le personnel informatique a identifié la menace initiale , comme la détection des sauvegardes en cours de suppression, les alertes antivirus, la détection de point de terminaison et les alertes de réponse (EDR) ou les modifications suspectes du système, il est souvent possible de prendre des mesures décisives rapides pour contrer l’attaque, généralement par les actions de confinement décrites dans cet article.
* Quelle date et quelle heure avez-vous appris l’incident pour la première fois ?
  * Quelles mises à jour système et de sécurité n’ont pas été installées sur les appareils à cette date ? Il est important de comprendre quelles vulnérabilités ont pu être exploitées pour pouvoir être traitées sur d’autres appareils.
  * Quels comptes d’utilisateur ont été utilisés à cette date ?
  * Quels comptes d’utilisateur ont été créés depuis cette date ?
  * Quels programmes ont été ajoutés pour démarrer automatiquement au moment où l’incident s’est produit ?
* Existe-t-il des indications indiquant que l’attaquant accède actuellement aux systèmes ?
  * Existe-t-il des systèmes compromis suspectés qui connaissent une activité inhabituelle ?
  * Y a-t-il des comptes compromis présumés qui semblent être utilisés activement par l’adversaire ?
  * Existe-t-il des preuves de serveurs de commande et de contrôle actifs (C2) dans EDR, pare-feu, VPN, proxy web et autres journaux ?

### <a name="identify-the-ransomware-process"></a>Identifier le processus de ransomware

* À l’aide de la [chasse avancée](/microsoft-365/security/defender/advanced-hunting-overview.md), recherchez le processus identifié dans les événements de création de processus sur d’autres appareils.

### <a name="look-for-exposed-credentials-in-the-infected-devices"></a>Rechercher les informations d’identification exposées dans les appareils infectés

* Pour les comptes d’utilisateur dont les informations d’identification ont été potentiellement compromises, réinitialisez les mots de passe du compte et demandez aux utilisateurs de se reconnecter.
* Les E/S suivantes peuvent indiquer un mouvement latéral :

<details>
  <summary>Cliquez pour développer</summary>

* SuspiciousExploratoryCommands
* MLFileBasedAlert
* IfeoDebuggerPersistence
* SuspiciousRemoteFileDropAndExecution
* ExploratoryWindowsCommands
* IoaStickyKeys
* Amplificateur Mimikatz Defender
* Outil d’analyse réseau utilisé par PARINACOTA
* DefenderServerAlertMSSQLServer
* SuspiciousLowReputationFileDrop
* SuspiciousServiceExecution
* AdminUserAddition
* MimikatzArtifactsDetector
* Scuba-WdigestEnabledToAccessCredentials
* DefenderMalware
* MLSuspCmdBehavior
* MLSuspiciousRemoteInvocation
* SuspiciousRemoteComponentInvocation
* SuspiciousWmiProcessCreation
* MLCmdBasedWithRemoting
* Processus Accesses Lsass
* Exécution suspecte du processus Rundll32
* BitsAdmin
* DefenderCobaltStrikeDetection
* DefenderHacktool
* IoaSuspPSCommandline
* Metasploit
* MLSuspToolBehavior
* RegistryQueryForPasswords
* SuspiciousWdavExclusion
* ASEPRegKey
* CobaltStrikeExecutionDetection
* DefenderBackdoor
* DefenderBehaviorSuspiciousActivity
* DefenderMalwareExecuted
* DefenderServerAlertDomainController
* DupTokenPrivilegeEscalationDetector
* FakeWindowsBinary
* IoaMaliciousCmdlets
* LivingOffTheLandBinary
* MicrosoftSignedBinaryAbuse
* MicrosoftSignedBinaryScriptletAbuse
* MLFileBasedWithRemoting
* MLSuspSvchostBehavior
* ReadSensitiveMemory
* RemoteCodeInjection-IREnabled
* Scuba-EchoSeenOverPipeOnLocalhost
* Scuba-SuspiciousWebScriptFileDrop
* Inscription suspecte de DLL par odbcconf
* Activité DPAPI suspecte
* Exécution suspecte du processus Exchange
* Lancement suspect d’une tâche planifiée
* SuspiciousLdapQueryDetector
* SuspiciousScheduledTaskRegistration
* Une application non approuvée ouvre une connexion RDP

</details>

### <a name="identify-the-line-of-business-lob-apps-that-are-unavailable-due-to-the-incident"></a>Identifier les applications métier qui ne sont pas disponibles en raison de l’incident

* L’application nécessite-t-elle une identité ?
  * Comment l’authentification est-elle effectuée ?
  * Comment les informations d’identification telles que les certificats ou les secrets sont-elles stockées et gérées ?
* Les sauvegardes évaluées de l’application, sa configuration et ses données sont-elles disponibles ?
* Déterminez votre processus de récupération de compromission.

## <a name="eradication-and-recovery"></a>Éradication et récupération

Suivez ces étapes pour éliminer la menace et récupérer les ressources endommagées.

### <a name="step-1-verify-your-backups"></a>Étape 1 : Vérifier vos sauvegardes

Si vous disposez de sauvegardes hors connexion, vous pouvez probablement restaurer les données qui ont été chiffrées après avoir supprimé la charge utile de ransomware (programme malveillant) de votre environnement et après avoir vérifié qu’il n’y a pas d’accès non autorisé dans votre locataire Microsoft 365.

### <a name="step-2-add-indicators"></a>Étape 2 : Ajouter des indicateurs

Ajoutez tous les canaux de communication d’attaquant connus en tant qu’indicateurs, bloqués dans les pare-feu, dans vos serveurs proxy et sur les points de terminaison.

### <a name="step-3-reset-compromised-users"></a>Étape 3 : Réinitialiser les utilisateurs compromis

Réinitialisez les mots de passe de tous les comptes d’utilisateurs compromis connus et nécessitez une nouvelle connexion.

* Envisagez de réinitialiser les mots de passe pour tout compte privilégié disposant d’une large autorité administrative, comme les membres du groupe Administrateurs de domaine.
* Si un compte d’utilisateur a peut-être été créé par un attaquant, désactivez-le. Ne supprimez pas le compte, sauf s’il n’est pas prévu d’effectuer des investigations de sécurité pour l’incident.

### <a name="step-4-isolate-attacker-control-points"></a>Étape 4 : Isoler les points de contrôle des attaquants

Isolez les points de contrôle d’attaquant connus à l’intérieur de l’entreprise d’Internet.

### <a name="step-5-remove-malware"></a>Étape 5 : Supprimer les programmes malveillants

Supprimez les programmes malveillants des appareils affectés.

* Exécutez une analyse antivirus complète et actuelle sur tous les ordinateurs et appareils suspectés pour détecter et supprimer la charge utile associée au ransomware.
* N’oubliez pas d’analyser les appareils qui synchronisent les données ou les cibles des lecteurs réseau mappés.

### <a name="step-6-recover-files-on-a-cleaned-device"></a>Étape 6 : Récupérer des fichiers sur un appareil nettoyé

Récupérer des fichiers sur un appareil nettoyé.

* Vous pouvez utiliser [l’historique](https://support.microsoft.com/help/17128) des fichiers dans Windows 11, Windows 10, Windows 8.1 et la protection système dans Windows 7 pour tenter de récupérer vos fichiers et dossiers locaux.

### <a name="step-7-recover-files-in-onedrive-for-business"></a>Étape 7 : Récupérer des fichiers dans OneDrive Entreprise

Récupérer des fichiers dans OneDrive Entreprise.

* La restauration de fichiers dans OneDrive Entreprise vous permet de restaurer un OneDrive entier à un point antérieur dans le temps au cours des 30 derniers jours. Pour plus dʼinformations, voir [Restaurer votre espace OneDrive](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).

### <a name="step-8-recover-deleted-email"></a>Étape 8 : Récupérer les e-mails supprimés

Récupérer les e-mails supprimés.

* Dans les rares cas où le ransomware a supprimé tous les e-mails d’une boîte aux lettres, vous pouvez récupérer les éléments supprimés. Consultez [Récupérer les messages supprimés dans la boîte aux lettres d’un utilisateur dans Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages).

### <a name="step-9-re-enable-exchange-activesync-and-onedrive-sync"></a>Étape 9 : Réactiver Exchange ActiveSync et Synchronisation OneDrive

* Une fois que vous avez nettoyé vos ordinateurs et appareils et récupéré les données, vous pouvez réactiver Exchange ActiveSync et Synchronisation OneDrive que vous avez précédemment désactivés à l’étape 3 de l’endiguement.
