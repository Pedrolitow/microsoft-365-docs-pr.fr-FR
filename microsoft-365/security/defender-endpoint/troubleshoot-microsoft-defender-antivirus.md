---
title: Antivirus Microsoft Defender ID d’événement et codes d’erreur
description: Rechercher les causes et les solutions des erreurs et des ID d’événement Antivirus Microsoft Defender
keywords: événement, code d’erreur, siem, journalisation, résolution des problèmes, wef, transfert d’événements Windows
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/27/2022
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 9008fe0d6a4c46d544e4d806c3a15b24c53f2f10
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637979"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Consulter les journaux d'événements et les codes d'erreur pour résoudre les problèmes liés à l'antivirus Microsoft Defender.

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Si vous rencontrez un problème avec Antivirus Microsoft Defender, vous pouvez rechercher dans les tableaux de cette rubrique un problème correspondant et une solution potentielle.

La liste des tables :

- [Antivirus Microsoft Defender ID d’événement](#windows-defender-av-ids) (ceux-ci s’appliquent aux Windows 10, Windows 11 et Windows Server 2016)
- [codes d’erreur du client Antivirus Microsoft Defender](#error-codes)
- [Codes d’erreur internes Antivirus Microsoft Defender client (utilisés par Microsoft lors du développement et du test)](#internal-error-codes)

> [!TIP]
> Vous pouvez également visiter le site web de démonstration Microsoft Defender pour point de terminaison à [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités suivantes fonctionnent :
>
> - Protection fournie par le cloud
> - Apprentissage rapide (y compris bloquer à la première consultation)
> - Blocage d’applications potentiellement indésirables

> [!NOTE]
> Le site de démonstration Defender pour point de terminaison sur demo.wd.microsoft.com est déconseillé et sera supprimé à l’avenir.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>ID d’événement Antivirus Microsoft Defender

Antivirus Microsoft Defender enregistre les ID d’événement dans le journal des événements Windows.

Vous pouvez afficher directement le journal des événements, ou si vous disposez d’un outil siem (Security Information and Event Management) tiers, vous pouvez également utiliser [Antivirus Microsoft Defender ID d’événement client](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) pour passer en revue des événements et des erreurs spécifiques de vos points de terminaison.

Le tableau de cette section répertorie les principaux ID d’événement Antivirus Microsoft Defender et, si possible, fournit des solutions suggérées pour corriger ou résoudre l’erreur.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Pour afficher un événement Antivirus Microsoft Defender

1. Ouvrez **observateur d'événements**.
2. Dans l’arborescence de la console, développez **les journaux des applications et des services**, puis **Microsoft**, **puis Windows**, puis **Windows Defender**.
3. Double-cliquez sur **Operational**.
4. Dans le volet d’informations, affichez la liste des événements individuels pour rechercher votre événement.
5. Cliquez sur l’événement pour afficher des détails spécifiques sur un événement dans le volet inférieur, sous les **onglets** **Général** et Détails.

<table>
<tr>
<th colspan="2" >ID d’événement : 1000</th>
</tr>
<tr>
<td>
Nom symbolique :
</td>
<td>
<b>MALWAREPROTECTION_SCAN_STARTED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant a démarré. </b>
</td>
</tr>
<tr>
<td >
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Analyser les ressources : &lt; Ressources (telles que les fichiers/répertoires/BHO) qui ont été analysées.&gt;</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; Utilisateur&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1001</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SCAN_COMPLETED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant s’est terminée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur: &lt; Domainlt&gt;\&; Heure UserScan&gt;</dt> 
<dt>: &lt;durée d’une analyse.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1002</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SCAN_CANCELLED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant a été arrêtée avant sa fin. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur: &lt; Domainlt&gt;&amp;; Heure UserScan&gt;</dt> 
<dt>: &lt;durée d’une analyse.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1003</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SCAN_PAUSED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant a été suspendue. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt;Domainlt&gt;\& ; Utilisateur&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1004</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SCAN_RESUMED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant a été reprise. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt;Domainlt&gt;\& ; Utilisateur&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1005</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SCAN_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Une analyse anti-programme malveillant a échoué. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de l’analyse appropriée.&gt;</dt>
<dt> Type d’analyse : &lt;type d’analyse&gt;, par exemple :<ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Paramètres d’analyse : &lt;Analyser les paramètres&gt;, par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur: &lt; Domainlt&gt;\&; Code UserError&gt;</dt> 
<dt>: &lt;code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le client antivirus a rencontré une erreur et l’analyse actuelle s’est arrêtée. L’analyse peut échouer en raison d’un problème côté client. Cet enregistrement d’événement inclut l’ID d’analyse, le type d’analyse (Antivirus Microsoft Defender, antispyware, anti-programme malveillant), les paramètres d’analyse, l’utilisateur qui a démarré l’analyse, le code d’erreur et une description de l’erreur.
Pour résoudre les problèmes liés à cet événement :
<ol>
<li>Réexélez l’analyse.</li>
<li>Si elle échoue de la même façon, accédez au <a href="https://go.microsoft.com/fwlink/?LinkId=215163">site Support Microsoft</a>, entrez le numéro d’erreur dans la zone <b>de recherche</b> pour rechercher le code d’erreur.</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1006</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_DETECTED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a détecté des programmes malveillants ou d’autres logiciels potentiellement indésirables. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACStatus</dt> 
<dt>: &lt;StatusUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 1007</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a effectué une action pour protéger votre système contre les programmes malveillants ou d’autres logiciels potentiellement indésirables. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a pris des mesures pour protéger cette machine contre les programmes malveillants ou d’autres logiciels potentiellement indésirables. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Utilisateur: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt>
<dt> Action : &lt;Action&gt;, par exemple :<ul>
<li>Nettoyage : la ressource a été nettoyée</li>
<li>Mise en quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiées</li>
<li>Aucune action : Aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>Statut: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 1008</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a tenté d’effectuer une action pour protéger votre système contre les programmes malveillants ou d’autres logiciels potentiellement indésirables, mais l’action a échoué.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de l’action contre des programmes malveillants ou d’autres logiciels potentiellement indésirables. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Utilisateur: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; File pathAction&gt;</dt>
<dt> : &lt;action&gt;, par exemple :<ul>
<li>Nettoyage : la ressource a été nettoyée</li>
<li>Mise en quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiées</li>
<li>Aucune action : Aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>Code d’erreur : &lt; Code d’erreur&gt; : Code de résultat associé à l’état de la menace. Valeurs HRESULT standard. </dt>
<dt>Description de l’erreur : &lt;description&gt; de l’erreur. </dt> 
<dt>Statut: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 1009</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a restauré un élément à partir de la mise en quarantaine. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a restauré un élément à partir de la mise en quarantaine. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; File pathUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 1010</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant n’a pas pu restaurer un élément à partir de la mise en quarantaine. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de restauration d’un élément à partir de la mise en quarantaine. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; File pathUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; Code UserError&gt;</dt> 
<dt>: &lt;code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt>
<dt>Description de l’erreur : &lt;description&gt; de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>définitionEngine : &lt;version&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1011</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a supprimé un élément de la quarantaine. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a supprimé un élément de la quarantaine.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; File pathUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 1012</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant n’a pas pu supprimer un élément de la quarantaine.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de suppression d’un élément en quarantaine.
Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; File pathUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; Code UserError&gt;</dt> 
<dt>: &lt;code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt>
<dt>Description de l’erreur : &lt;description&gt; de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>définitionEngine : &lt;version&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1013</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a supprimé l’historique des programmes malveillants et d’autres logiciels potentiellement indésirables.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a supprimé l’historique des programmes malveillants et d’autres logiciels potentiellement indésirables.
<dl>
<dt>Heure : heure à laquelle l’événement s’est produit, par exemple lorsque l’historique est purgé. Ce paramètre n’est pas utilisé dans les événements de menace afin qu’il n’y ait aucune confusion quant à savoir s’il s’agit de temps de correction ou de temps d’infection. Pour ceux-ci, nous les appelons spécifiquement temps d’action ou heure de détection.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; Utilisateur&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1014</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
La plateforme anti-programme malveillant n’a pas pu supprimer l’historique des programmes malveillants et d’autres logiciels potentiellement indésirables.
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de suppression de l’historique des programmes malveillants et d’autres logiciels potentiellement indésirables.
<dl>
<dt>Heure : heure à laquelle l’événement s’est produit, par exemple lorsque l’historique est purgé. Ce paramètre n’est pas utilisé dans les événements de menace afin qu’il n’y ait aucune confusion quant à savoir s’il s’agit de temps de correction ou de temps d’infection. Pour ceux-ci, nous les appelons spécifiquement temps d’action ou heure de détection.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; Code UserError&gt;</dt> 
<dt>: &lt;code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt>
<dt>Description de l’erreur : &lt;description&gt; de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1015</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_BEHAVIOR_DETECTED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a détecté un comportement suspect.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a détecté un comportement suspect.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACStatus</dt> 
<dt>: &lt;StatusUser&gt;</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>ID: Enumeration matching severity.</dt> 
<dt>Version de signature : &lt; Version versionEngine&gt; de la définition</dt> 
<dt>: &lt;Antimalware Engine versionFidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;File name&gt; name of the file.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1116</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_DETECTED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a détecté des programmes malveillants ou d’autres logiciels potentiellement indésirables. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a détecté des programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACUser</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est requise. Antivirus Microsoft Defender pouvez suspendre et prendre des mesures de routine sur cette menace. Si vous souhaitez supprimer la menace manuellement, dans l’interface Antivirus Microsoft Defender, cliquez sur <b>Ordinateur propre</b>.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1117</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a effectué une action pour protéger votre système contre les programmes malveillants ou d’autres logiciels potentiellement indésirables. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a pris des mesures pour protéger cette machine contre les programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACUser</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, par exemple :<ul>
<li>Nettoyage : la ressource a été nettoyée</li>
<li>Mise en quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiées</li>
<li>Aucune action : Aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description d’autres actionsError&gt;</dt> 
<dt>Code : &lt;Code d’erreur&gt; : code de résultat associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>definitionEngine : &lt;Antimalware Engine version&gt;</dt> REMARQUE : Chaque fois que Antivirus Microsoft Defender, Microsoft Security Essentials, outil de suppression de logiciels malveillants ou System Center Endpoint Protection détecte un programme malveillant, il restaure les paramètres système et les services suivants que le programme malveillant a peut-être modifiés :<ul>
<li>Paramètre Internet Explorer ou Microsoft Edge par défaut</li>
<li>Paramètres de Access Control utilisateur</li>
<li>Paramètres Chrome</li>
<li>Données de contrôle de démarrage</li>
<li>Paramètres de Registre Regedit et Task Manager</li>
<li>Windows Update, service de transfert intelligent en arrière-plan et service d’appel de procédure distante</li>
<li>fichiers du système d’exploitation Windows</li></ul>
Le contexte ci-dessus s’applique aux versions client et serveur suivantes :
<table>
<tr>
<th>Système d’exploitation</th>
<th>Version du système d'exploitation</th>
</tr>
<tr>
<td>
Système d’exploitation client
</td>
<td>
Windows Vista (Service Pack 1 ou Service Pack 2), Windows 7 et versions ultérieures
</td>
</tr>
<tr>
<td>
Système d’exploitation du serveur
</td>
<td>
Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 et Windows Server 2016
</td>
</tr>
</table>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Antivirus Microsoft Defender supprimé ou mis en quarantaine une menace.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1118</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a tenté d’effectuer une action pour protéger votre système contre les programmes malveillants ou d’autres logiciels potentiellement indésirables, mais l’action a échoué. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur non critique lors de l’action contre des programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACUser</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, par exemple :<ul>
<li>Nettoyage : la ressource a été nettoyée</li>
<li>Mise en quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiées</li>
<li>Aucune action : Aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description d’autres actionsError&gt;</dt> 
<dt>Code : &lt;Code d’erreur&gt; : code de résultat associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>définitionEngine : &lt;version&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Antivirus Microsoft Defender n’a pas pu effectuer une tâche liée à la correction des programmes malveillants. Il ne s’agit pas d’un échec critique.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1119</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_CRITICALLY_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a rencontré une erreur critique lors de la tentative d’action sur les programmes malveillants ou d’autres logiciels potentiellement indésirables. Il y a plus de détails dans le message d’événement.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur critique lors de l’action contre des programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie: &lt; Description de la catégorie&gt;, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin: &lt; Origine pathDetection&gt;</dt>
<dt> du fichier : &lt;origine&gt; de détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection : &lt;type de&gt; détection, par exemple :<ul>
<li>Heuristique</li>
<li>Generic</li>
<li>Béton</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt;Source&gt; de détection, par exemple :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel lancé</li>
<li>IOAV : Téléchargements et Outlook pièces jointes Express initiés par Internet Explorer</li>
<li>NIS : système d’inspection réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Lancement anticipé du logiciel anti-programme malveillant (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PowerShell, VBS), mais il peut également être appelé par des tiers.
UACUser</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, par exemple :<ul>
<li>Nettoyage : la ressource a été nettoyée</li>
<li>Mise en quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiées</li>
<li>Aucune action : Aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description d’autres actionsError&gt;</dt> 
<dt>Code : &lt;Code d’erreur&gt; : code de résultat associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>définitionEngine : &lt;version&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le client Antivirus Microsoft Defender a rencontré cette erreur en raison de problèmes critiques. Le point de terminaison peut ne pas être protégé. Passez en revue la description de l’erreur, puis suivez les étapes <b>d’action utilisateur</b> appropriées ci-dessous.
<table>
<tr>
<th>Action</th>
<th>Action de l’utilisateur</th>
</tr>
<tr>
<td>
<b>Retirer</b>
</td>
<td>
Mettez à jour les définitions, puis vérifiez que la suppression a réussi.
</td>
</tr>
<tr>
<td>
<b>Propre</b>
</td>
<td>
Mettez à jour les définitions, puis vérifiez que la correction a réussi.
</td>
</tr>
<tr>
<td>
<b>Quarantaine</b>
</td>
<td>
Mettez à jour les définitions et vérifiez que l’utilisateur a l’autorisation d’accéder aux ressources nécessaires.
</td>
</tr>
<tr>
<td>
<b>Permettre</b>
</td>
<td>
Vérifiez que l’utilisateur est autorisé à accéder aux ressources nécessaires.
</td>
</tr>
</table>

Si cet événement persiste :<ol>
<li>Réexélez l’analyse.</li>
<li>Si elle échoue de la même façon, accédez au <a href="https://go.microsoft.com/fwlink/?LinkId=215163">site Support Microsoft</a>, entrez le numéro d’erreur dans la zone <b>de recherche</b> pour rechercher le code d’erreur.</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1120</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_THREAT_HASH</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Antivirus Microsoft Defender a déduit les hachages d’une ressource de menace.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender client est opérationnel dans un état sain.
<dl>
<dt>Version actuelle de la plateforme : &lt; Current platform versionThreat&gt;</dt> 
<dt>Resource Path: &lt;PathHashes&gt;</dt>
<dt>: &lt;Hashes&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Remarque : cet événement est journalisé uniquement si la stratégie suivante est définie : <b>ThreatFileHashLogging non signé</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1127</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_FOLDER_GUARD_SECTOR_BLOCK</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>L’accès contrôlé aux dossiers (CFA) a empêché un processus non approuvé d’apporter des modifications à la mémoire. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
L’accès contrôlé aux dossiers a empêché un processus non approuvé de modifier potentiellement des secteurs de disque.
<br/> Pour plus d’informations sur l’enregistrement d’événement, consultez les rubriques suivantes :
<dl>
<dt>Eventid: &lt; EventID&gt;, par exemple : 1127Version</dt> 
<dt>: &lt;Version&gt;, par exemple :</dt> 
<dt>0Level : &lt;Level&gt;, par exemple : win:</dt>
<dt>WarningTimeCreated: &lt;SystemTime&gt;, heure à laquelle l’événement a été</dt> 
<dt>crééEventRecordID : &lt;EventRecordID&gt;, numéro d’index de l’événement dans l’événement</dt> 
<dt>logExecution ProcessID: &lt;Execution ProcessID&gt;, processus qui a généré</dt> 
<dt>eventChannel : &lt;Canal&gt; d’événements, par exemple : Microsoft- Windows-Windows Defender/</dt>
<dt>OperationalComputer: &lt;Computer nameSecurity&gt;</dt> 
<dt>UserID: &lt;Security UserIDProduct&gt;</dt> 
<dt>Name: &lt;Product Name&gt;, par exemple: Antivirus Microsoft Defender</dt> 
<dt>Product Version: &lt;Product VersionDetection&gt;</dt> 
<dt>Time: &lt;Heure&gt; de détection, heure à laquelle CFA a bloqué un processUser non approuvé</dt> 
<dt>: &lt;Domainlt&gt;\& ; UserPath&gt;</dt> 
<dt>: &lt;Nom&gt; de l’appareil, nom de l’appareil ou du disque auquel un processus non approuvé a accédé pour</dt> 
<dt>modificationProcess Name: &lt;Process path, nom du chemin&gt; de processus que CFA a bloqué pour accéder à l’appareil ou au disque pour</dt> 
<dt>modificationSecurity Intelligence Version: &lt;Security Intelligence versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware Engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
L’utilisateur peut ajouter le processus bloqué à la liste <i>des processus autorisés</i> pour CFA, à l’aide de PowerShell ou de Sécurité Windows Center.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 1150</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTHY</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Si votre plateforme de logiciels anti-programme malveillant signale l’état à une plateforme de surveillance, cet événement indique que la plateforme anti-programme malveillant est en cours d’exécution et dans un état sain. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender client est opérationnel dans un état sain.
<dl>
<dt>Version de la plateforme : &lt; Version actuelle de la plateforme VersionSignature&gt;</dt> 
<dt>: &lt;Version de définitionEngine&gt;</dt> 
<dt>: &lt;version&gt; Antimalware Engine</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le client Antivirus Microsoft Defender est dans un état sain. Cet événement est signalé toutes les heures.
</td>
</tr>

<tr>
<th colspan="2">ID d’événement : 1151</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTH_REPORT</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Endpoint Protection rapport d’intégrité du client (heure UTC)</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Rapport d’intégrité du client antivirus.
<dl>
<dt>Version de la plateforme : &lt; Version actuelle de&gt; la</dt> 
<dt>plateformeEngine : &lt;Antimalware Engine version du moteur d’inspection en temps réel version de version&gt;</dt> du 
<dt>moteur d’inspection en temps réel du réseau versionAntivirus&gt; : version de signature antivirus versionAntispyware signature version : Version de signature Antispyware versionNetwork Realtime Inspection version : &lt;</dt>
<dt>&lt;&gt;</dt>
<dt>&lt;&gt;</dt>
<dt>&lt; État versionRTP&gt; de la signature d’inspection en temps réel :</dt> 
<dt>&lt;état&gt; de protection en temps réel (activé ou désactivé)</dt> 
<dt>État OA : &lt;État d’accès&gt; (activé ou désactivé)</dt> 
<dt>État IOAV : &lt;Téléchargements internet et Outlook état&gt; Des pièces jointes rapides (activé ou désactivé)</dt>
<dt>BM état : &lt;État&gt; de surveillance du comportement (activé ou désactivé)</dt> 
<dt>Âge de signature antivirus : &lt;âge&gt; de la signature antivirus  (en jours)</dt> 
<dt>Âge de signature Antispyware : &lt; Âge de signature&gt; Antispyware (en jours)</dt>
<dt>Dernier âge de l’analyse rapide : &lt;Dernier âge&gt; de l’analyse rapide (en jours)</dt>
<dt>Dernier âge complet de l’analyse : &lt;Dernière période&gt; d’analyse complète (en jours)</dt>
<dt>Heure de création de la signature antivirus : ?&lt; Heure de création de la signature antivirus TimeAntispyware&gt;</dt> 
<dt>: ?&lt; Heure&gt; de début de l’analyse rapide de la signature Antispyware</dt> 
<dt>: ?&lt; Heure de début&gt; de la dernière analyse</dt> 
<dt>rapideL’heure de fin de l’analyse rapide : ?&lt; Dernière heure&gt; de fin de l’analyse rapideLa</dt> 
<dt>source de l’analyse rapide : &lt;Dernière source&gt; d’analyse rapide (0 = l’analyse n’a pas été exécutée, 1 = initiée par l’utilisateur, 2 = initiée par le système)</dt>
<dt>Dernière heure de début de l’analyse complète : ?&lt; Heure de début&gt; de la dernière analyse</dt> 
<dt>complèteLa fin de l’analyse complète : ?&lt; Dernière analyse complète heure&gt;</dt> 
<dt>de finLa source d’analyse complète : &lt;Dernière source&gt; d’analyse complète (0 = l’analyse n’a pas été exécutée, 1 = initiée par l’utilisateur, 2 = initiée par le système)</dt>
<dt>État du produit : Pour la résolution des problèmes internes
</dl>
</td>
</tr>

<tr>
<th colspan="2">ID d’événement : 2000</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Les définitions de logiciel anti-programme malveillant ont été correctement mises à jour. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La version de signature antivirus a été mise à jour.
<dl>
<dt>Version de signature actuelle : &lt; Version de&gt; signature actuelle</dt> 
<dt>VersionPrevious Signature : &lt;Type de signature versionSignature&gt;</dt>
<dt> précédent : &lt;type de&gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Type de mise à jour : &lt; Type de&gt; mise à jour, Complet ou Delta.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le client Antivirus Microsoft Defender est dans un état sain. Cet événement est signalé lorsque les signatures sont correctement mises à jour.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2001</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Échec de la mise à jour du renseignement de sécurité. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de mise à jour des signatures.
<dl>
<dt>Nouvelle version du renseignement de sécurité : &lt; Nouvelle version numberPrevious&gt;</dt> 
<dt>security intelligence version: &lt;Previous versionUpdate&gt;</dt>
<dt> Source: &lt;Update source&gt;, par exemple :
<ul>
<li>Dossier de mise à jour du renseignement de sécurité</li>
<li>Serveur de mise à jour du renseignement de sécurité interne</li>
<li>Microsoft Update Server</li>
<li>Partage de fichiers</li>
<li>Centre de protection Microsoft contre les programmes malveillants (MMPC)</li>
</ul>
</dt>
<dt>Phase de mise à jour : &lt;phase&gt; de mise à jour, par exemple :
<ul>
<li>Rechercher</li>
<li>Télécharger</li>
<li>Installer</li>
</ul>
</dt>
<dt>Chemin d’accès source : nom du partage de fichiers pour la convention d’affectation de noms universelle (UNC), nom du serveur pour Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt>
<dt> Type de signature : &lt;type de&gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Type de mise à jour : &lt; Type de&gt; mise à jour, Complet ou Delta.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine versionError&gt;</dt> 
<dt>Code: &lt;Error code&gt; Result code associated with threat status. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Cette erreur se produit en cas de problème de mise à jour des définitions.
Pour résoudre les problèmes liés à cet événement :
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Mettez à jour les définitions</a> et forcez une nouvelle analyse directement sur le point de terminaison.</li>
<li>Pour plus d’informations sur cette erreur, consultez les entrées du fichier %Windir%\WindowsUpdate.log.</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2002</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a été mis à jour avec succès. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender version du moteur a été mise à jour.
<dl>
<dt>Version actuelle du moteur : &lt; Version actuelle du moteur&gt;</dt> 
<dt>VersionPrevious Engine Version: &lt;Previous engine versionEngine&gt;</dt> 
<dt>Type: &lt;Engine type&gt;, either antimalware engine or Network Inspection System engine.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; Utilisateur&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le client Antivirus Microsoft Defender est dans un état sain. Cet événement est signalé lorsque le moteur de logiciel anti-programme malveillant est correctement mis à jour.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2003</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Échec de la mise à jour du moteur anti-programme malveillant. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de mise à jour du moteur.
<dl>
<dt>New Engine Version:</dt>
<dt>Previous Engine Version: &lt;Previous engine versionEngine&gt;</dt> 
<dt>Type: &lt;Engine type&gt;, either antimalware engine or Network Inspection System engine.</dt> 
<dt>Utilisateur: &lt; Domainlt&gt;\&; Code UserError&gt;</dt> 
<dt>: &lt;code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Échec de la mise à jour du client Antivirus Microsoft Defender. Cet événement se produit lorsque le client ne parvient pas à se mettre à jour lui-même. Cet événement est généralement dû à une interruption de la connectivité réseau pendant une mise à jour.
Pour résoudre les problèmes liés à cet événement :
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Mettez à jour les définitions</a> et forcez une nouvelle analyse directement sur le point de terminaison.</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2004</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_REVERSION</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Un problème s’est produite lors du chargement des définitions de logiciel anti-programme malveillant. Le moteur de logiciel anti-programme malveillant tente de charger le dernier bon ensemble connu de définitions.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de chargement des signatures et tente de revenir à un ensemble connu de signatures.
<dl>
<dt>Signatures Attempted:</dt>
<dt>Error Code: &lt;Error code&gt; Result code associated with threat status. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt> 
<dt>Version de signature : &lt; Version de&gt;</dt> 
<dt>définitionEngine : &lt;version&gt; du moteur Antimalware</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le client Antivirus Microsoft Defender a tenté de télécharger et d’installer le fichier de définitions le plus récent et a échoué. Cette erreur peut se produire lorsque le client rencontre une erreur lors de la tentative de chargement des définitions, ou si le fichier est endommagé. Antivirus Microsoft Defender tente de revenir à un ensemble connu de définitions correctes.
Pour résoudre les problèmes liés à cet événement :
<ol>
<li>Redémarrez l’ordinateur et réessayez.</li>
<li>Téléchargez les dernières définitions à partir du <a href="https://aka.ms/wdsi">site Renseignement de sécurité Microsoft</a>.
Remarque : la taille du fichier de définitions téléchargé à partir du site peut dépasser 60 Mo et ne doit pas être utilisée comme solution à long terme pour mettre à jour les définitions.
</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2005</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_PLATFORMOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant n’a pas pu se charger, car la plateforme anti-programme malveillant est obsolète. La plateforme anti-programme malveillant charge le dernier moteur de logiciel anti-programme malveillant connu et tente de le mettre à jour.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender n’a pas pu charger le moteur de logiciel anti-programme malveillant, car la version actuelle de la plateforme n’est pas prise en charge. Antivirus Microsoft Defender revenez au dernier moteur connu et une mise à jour de plateforme est tentée.
<dl>
<dt>Version actuelle de la plateforme : &lt;version actuelle de la plateforme&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2006</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Échec de la mise à jour de la plateforme. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de mise à jour de la plateforme.
<dl>
<dt>Version actuelle de la plateforme : &lt; Code versionError&gt; de la plateforme actuelle</dt> 
<dt>: &lt;Code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2007</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_ALMOSTOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme sera bientôt obsolète. Téléchargez la dernière plateforme pour maintenir une protection à jour.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender aurez bientôt besoin d’une version de plateforme plus récente pour prendre en charge les versions futures du moteur de logiciel anti-programme malveillant. Téléchargez la dernière plateforme Antivirus Microsoft Defender pour maintenir le meilleur niveau de protection disponible.
<dl>
<dt>Version actuelle de la plateforme : &lt;version actuelle de la plateforme&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2010</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a utilisé le service de signature dynamique pour obtenir des définitions supplémentaires. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender utilisé <i>Dynamic Signature Service</i> pour récupérer des signatures supplémentaires afin de protéger votre machine.
<dl>
<dt>Version de signature actuelle : &lt; Type de signature actuelle versionSignature&gt;</dt>
<dt> : &lt;type de&gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Type de signature biodynamique du moteur&gt;</dt>
<dt> actuel : &lt;type de&gt; signature dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Aucune limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin de persistance : &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, par exemple :
<ul>
<li>Version de VDM</li>
<li>Timestamp</li>
<li>Aucune limite</li>
</ul>
</dt>
<dt>Limite de persistance : limite de persistance de la signature fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 2011</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le service de signature dynamique a supprimé les définitions dynamiques obsolètes. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender utilisé <i>Dynamic Signature Service</i> pour ignorer les signatures obsolètes.
<dl>
<dt>Version de signature actuelle : &lt; Type de signature actuelle versionSignature&gt;</dt>
<dt> : &lt;type de&gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Type de signature biodynamique du moteur&gt;</dt>
<dt> actuel : &lt;type de&gt; signature dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Aucune limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin de persistance : &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistence limit type&gt;, par exemple :
<ul>
<li>Version de VDM</li>
<li>Timestamp</li>
<li>Aucune limite</li>
</ul>
</dt>
<dt>Limite de persistance : limite de persistance de la signature fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le client Antivirus Microsoft Defender est dans un état sain. Cet événement est signalé lorsque le service de signature dynamique supprime avec succès des définitions dynamiques obsolètes.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2012</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a rencontré une erreur lors de la tentative d’utilisation du service de signature dynamique. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative d’utilisation du <i>service de signature dynamique</i>.
<dl>
<dt>Version de signature actuelle : &lt; Type de signature actuelle versionSignature&gt;</dt>
<dt> : &lt;type de&gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Logiciel anti-espion</li>
<li>Antimalware</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Code versionerror&gt; du moteur actuel</dt> 
<dt>: &lt;Code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
<dt> Type de signature dynamique : &lt;type de&gt; signature dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Aucune limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin de persistance : &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;Version numberDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistence limit type&gt;, par exemple :
<ul>
<li>Version de VDM</li>
<li>Timestamp</li>
<li>Aucune limite</li>
</ul>
</dt>
<dt>Limite de persistance : limite de persistance de la signature fastpath.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Vérifiez vos paramètres de connectivité Internet.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2013</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED_ALL </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le service de signature dynamique a supprimé toutes les définitions dynamiques. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender ignoré toutes les signatures <i>de service de signature dynamique</i>.
<dl>
<dt>Version de signature actuelle : &lt;version de signature actuelle&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2020</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOADED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a téléchargé un fichier propre. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender téléchargé un fichier propre.
<dl>
<dt>Fichier: &lt; Nom&gt; du fichier.</dt> 
<dt>Version de signature actuelle : &lt; Version actuelle du moteurCurrent version&gt; de la signature</dt> 
<dt>: &lt;version&gt; actuelle du moteur</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2021</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOAD_FAILED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant n’a pas pu télécharger un fichier propre. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de téléchargement d’un fichier propre.
<dl>
<dt>Fichier: &lt; Nom&gt; du fichier.</dt> 
<dt>Version de signature actuelle : &lt; Version actuelle du moteur de versionCurrent&gt;</dt> 
<dt>: &lt;Code de version&gt; du moteur actuel</dt> 
<dt>: &lt;Code de résultat du code&gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Vérifiez vos paramètres de connectivité Internet.
Le client Antivirus Microsoft Defender a rencontré une erreur lors de l’utilisation du service de signature dynamique pour télécharger les dernières définitions vers une menace spécifique. Cette erreur est probablement due à un problème de connectivité réseau.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2030</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALLED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a été téléchargé et est configuré pour s’exécuter hors connexion au prochain redémarrage du système.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender téléchargé et configuré l’antivirus hors connexion pour qu’il s’exécute au prochain redémarrage.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2031</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALL_FAILED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant n’a pas pu télécharger et configurer une analyse hors connexion.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de téléchargement et de configuration de l’antivirus hors connexion.
<dl>
<dt>Code d’erreur : &lt; Code d’erreur&gt; : Code de résultat associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2040</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_OS_EXPIRING </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La prise en charge des logiciels anti-programme malveillant pour cette version du système d’exploitation prendra bientôt fin. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La prise en charge de votre système d’exploitation expirera sous peu. L’exécution Antivirus Microsoft Defender sur un système d’exploitation hors support n’est pas une solution adéquate pour se protéger contre les menaces.
</td>
</tr>
<tr>
<th colspan="2">ID d'événement : 2041</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_OS_EOL </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La prise en charge des logiciels anti-programme malveillant pour ce système d’exploitation est terminée. Vous devez mettre à niveau le système d’exploitation pour une prise en charge continue. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La prise en charge de votre système d’exploitation a expiré. L’exécution Antivirus Microsoft Defender sur un système d’exploitation hors support n’est pas une solution adéquate pour se protéger contre les menaces.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 2042</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_PROTECTION_EOL </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant ne prend plus en charge ce système d’exploitation et ne protège plus votre système contre les programmes malveillants. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La prise en charge de votre système d’exploitation a expiré. Antivirus Microsoft Defender n’est plus pris en charge sur votre système d’exploitation, a cessé de fonctionner et ne protège pas contre les menaces de programmes malveillants.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 3002</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_FAILURE </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La protection en temps réel a rencontré une erreur et a échoué.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender Real-Time fonctionnalité protection a rencontré une erreur et a échoué.
<dl>
<dt>Fonctionnalité : &lt;Fonctionnalité&gt;, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements d’Internet Explorer et pièces jointes Microsoft Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Code d’erreur : &lt; Code d’erreur&gt; : Code de résultat associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt> 
<dt>Motif : raison pour laquelle Antivirus Microsoft Defender protection en temps réel a redémarré une fonctionnalité.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Vous devez redémarrer le système, puis exécuter une analyse complète, car il est possible que le système n’ait pas été protégé pendant un certain temps.
La fonctionnalité de protection en temps réel du client Antivirus Microsoft Defender a rencontré une erreur, car l’un des services n’a pas pu démarrer.
S’il est suivi d’un ID d’événement 3007, l’échec était temporaire et le client anti-programme malveillant récupéré après l’échec.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 3007</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_RECOVERED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Protection en temps réel récupérée après un échec. Nous vous recommandons d’exécuter une analyse système complète lorsque vous voyez cette erreur. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender protection en temps réel a redémarré une fonctionnalité. Il est recommandé d’exécuter une analyse système complète pour détecter tous les éléments qui ont pu être manqués pendant que cet agent était en panne.
<dl>
<dt>Fonctionnalité : &lt;Fonctionnalité&gt;, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements d’Internet Explorer et pièces jointes Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Motif : raison pour laquelle Antivirus Microsoft Defender protection en temps réel a redémarré une fonctionnalité.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
La fonctionnalité de protection en temps réel a redémarré. Si cet événement se produit à nouveau, contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">support technique Microsoft</a>.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5000</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_RTP_ENABLED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La protection en temps réel est activée. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender analyse en temps réel de la protection contre les programmes malveillants et d’autres logiciels potentiellement indésirables a été activée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5001</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_RTP_DISABLED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La protection en temps réel est désactivée. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender analyse en temps réel de la protection contre les programmes malveillants et d’autres logiciels potentiellement indésirables a été désactivée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5004</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_CONFIGURED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La configuration de la protection en temps réel a changé. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender configuration des fonctionnalités de protection en temps réel a changé.
<dl>
<dt>Fonctionnalité : &lt;Fonctionnalité&gt;, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements d’Internet Explorer et pièces jointes Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection réseau</li>
</ul>
</dt>
<dt>Configuration: </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5007</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_CONFIG_CHANGED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La configuration de la plateforme anti-programme malveillant a changé.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender configuration a changé. S’il s’agit d’un événement inattendu, vous devez examiner les paramètres, car il peut s’agir du résultat d’un programme malveillant.
<dl>
<dt>Ancienne valeur : &lt; Ancien numéro de&gt; valeur Ancienne valeur de configuration antivirus.</dt> 
<dt>Nouvelle valeur : &lt; Nouveau numéro de&gt; valeur Nouvelle valeur de configuration antivirus.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5008</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_FAILURE</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>Le moteur de logiciel anti-programme malveillant a rencontré une erreur et a échoué.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender moteur a été arrêté en raison d’une erreur inattendue.
<dl>
<dt>Type d’échec : &lt; Type d’échec&gt;, par exemple : Code crash ou</dt> 
<dt>HangException : &lt;CodeResource&gt; d’erreur</dt> 
<dt>: &lt;ressource&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Pour résoudre les problèmes liés à cet événement :<ol>
<li>Essayez de redémarrer le service.<ul>
<li>Pour les logiciels malveillants, antivirus et logiciels espions, à une invite de commandes avec élévation de privilèges, <b>tapez net stop msmpsvc</b>, puis <b>tapez net start msmpsvc</b> pour redémarrer le moteur de logiciel anti-programme malveillant.</li>
<li>Pour le <i>système d’inspection réseau</i>, à une invite de commandes avec élévation de privilèges, <b>tapez net start nissrv</b>, puis <b>tapez net start nissrv</b> pour redémarrer le moteur <i>du système d’inspection réseau</i> à l’aide du fichier NiSSRV.exe.
</li>
</ul>
</li>
<li>Si elle échoue de la même façon, recherchez le code d’erreur en accédant au <a href="https://go.microsoft.com/fwlink/?LinkId=215163">site Support Microsoft</a> et en entrant le numéro d’erreur dans la zone <b>de recherche</b>, puis contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">support technique Microsoft</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le moteur client Antivirus Microsoft Defender s’est arrêté en raison d’une erreur inattendue.
Pour résoudre les problèmes liés à cet événement :
<ol>
<li>Réexélez l’analyse.</li>
<li>Si elle échoue de la même façon, accédez au <a href="https://go.microsoft.com/fwlink/?LinkId=215163">site Support Microsoft</a>, entrez le numéro d’erreur dans la zone <b>de recherche</b> pour rechercher le code d’erreur.</li>
<li>Contactez le <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Support technique Microsoft</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5009</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_ENABLED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>L’analyse des programmes malveillants et d’autres logiciels potentiellement indésirables est activée. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender’analyse des programmes malveillants et d’autres logiciels potentiellement indésirables a été activée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5010</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_DISABLED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>L’analyse des programmes malveillants et d’autres logiciels potentiellement indésirables est désactivée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender’analyse des programmes malveillants et d’autres logiciels potentiellement indésirables est désactivée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5011</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_ENABLED</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>L’analyse des virus est activée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender’analyse des virus a été activée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5012</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_DISABLED </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>L’analyse des virus est désactivée. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender’analyse des virus est désactivée.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5013</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>
</b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La protection contre les falsifications a bloqué une modification de Antivirus Microsoft Defender.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Si la protection contre les falsifications est activée, toute tentative de modification des paramètres de Defender si elle est bloquée et si l’ID d’événement 5013 est généré indique quel changement de paramètre a été bloqué.
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5100</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_EXPIRATION_WARNING_STATE </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant expirera bientôt. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender est entré dans une période de grâce et expirera bientôt. Après expiration, ce programme désactive la protection contre les virus, les logiciels espions et d’autres logiciels potentiellement indésirables.
<dl>
<dt>Raison de l’expiration : raison pour laquelle Antivirus Microsoft Defender expirera.</dt> 
<dt>Date d’expiration : date d’expiration Antivirus Microsoft Defender.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">ID d’événement : 5101</th>
</tr>
<tr><td>
Nom symbolique :
</td>
<td >
<b>MALWAREPROTECTION_DISABLED_EXPIRED_STATE </b>
</td>
</tr>
<tr>
<td>
Message :
</td>
<td >
<b>La plateforme anti-programme malveillant a expiré. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender période de grâce a expiré. La protection contre les virus, les logiciels espions et d’autres logiciels potentiellement indésirables est désactivée.
<dl>
<dt>Expiration Reason:</dt>
<dt>Expiration Date: </dt>
<dt>Error Code: &lt;Error code&gt; Result code associated with threat status. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description&gt; de l’erreur Description de l’erreur. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Antivirus Microsoft Defender codes d’erreur du client Si Antivirus Microsoft Defender rencontre des problèmes, il vous fournira généralement un code d’erreur pour vous aider à résoudre le problème. Le plus souvent, une erreur signifie qu’il y a eu un problème lors de l’installation d’une mise à jour.
Cette section fournit les informations suivantes sur les erreurs de Antivirus Microsoft Defender client.
- Le code - d’erreur La raison possible de l’erreur - Conseils sur ce qu’il faut faire maintenant

Utilisez les informations contenues dans ces tables pour résoudre Antivirus Microsoft Defender codes d’erreur.


<table>
<tr>
<th colspan="2">Code d’erreur : 0x80508007</th>
</tr>
<tr>
<td>Message</td>
<td>
<b>ERR_MP_NO_MEMORY </b>
</td>
</tr>
<tr>
<td>
Raison possible
</td>
<td>
Cette erreur indique que vous avez peut-être manquer de mémoire.
</td>
</tr>
<tr>
<td>Résolution</td>
<td>
<ol>
<li>Vérifiez la mémoire disponible sur votre appareil.</li>
<li>Fermez toutes les applications inutilisées qui s’exécutent pour libérer de la mémoire sur votre appareil.</li>
<li>Redémarrez l’appareil et réexélez l’analyse.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x8050800C</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_BAD_INPUT_DATA</b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’il peut y avoir un problème avec votre produit de sécurité.
</td>
</tr><tr><td>Résolution</td><td>
<ol>
<li>Mettez à jour les définitions. Soit:<ol>
<li>Obtenez vos mises à jour de renseignement de sécurité dans l’application Sécurité Windows. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Ou,
</li>
<li>Téléchargez les dernières définitions à partir du <a href="https://aka.ms/wdsi">site Renseignement de sécurité Microsoft</a>.
Remarque : la taille du fichier de définitions téléchargé à partir du site peut dépasser 60 Mo et ne doit pas être utilisée comme solution à long terme pour mettre à jour les définitions.
</li>
</ol>
</li>
<li>Exécutez une analyse complète.
</li>
<li>Redémarrez l’appareil et réessayez.</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508020</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_BAD_CONFIGURATION </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’il peut y avoir une erreur de configuration du moteur ; cela est généralement lié aux données d’entrée qui ne permettent pas au moteur de fonctionner correctement.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x805080211
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que Antivirus Microsoft Defender n’a pas pu mettre en quarantaine une menace.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508022
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’un redémarrage est nécessaire pour terminer la suppression des menaces.
</td>
</tr>
<tr>
<th colspan="2">
0x80508023
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_THREAT_NOT_FOUND </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que la menace peut ne plus être présente sur le média, ou que des programmes malveillants peuvent vous empêcher d’analyser votre appareil.
</tr><tr><td>Résolution
</td>
<td>
Exécutez le <a href="https://www.microsoft.com/security/scanner/default.aspx">Scanner de sécurité Microsoft</a> puis mettez à jour votre logiciel de sécurité et réessayez.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508024 </th></tr>
<tr>
<td>Message</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une analyse système complète peut être nécessaire.
</td></tr>
<tr>
<td>Résolution</td><td>
Exécutez une analyse système complète.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508025
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_MANUAL_STEPS_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que des étapes manuelles sont nécessaires pour terminer la suppression des menaces.
</td></tr><tr><td>Résolution</td><td>
Suivez les étapes de correction manuelle décrites dans Microsoft <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">Malware Protection Encyclopedia</a>. Vous trouverez un lien spécifique aux menaces dans l’historique des événements.<br/></td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508026
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que la suppression à l’intérieur du type de conteneur peut ne pas être prise en charge.
</td></tr><tr><td>Résolution</td><td>
Antivirus Microsoft Defender n’est pas en mesure de corriger les menaces détectées dans l’archive. Envisagez de supprimer manuellement les ressources détectées.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508027
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que la suppression des menaces faibles et moyennes peut être désactivée.
</td></tr><tr><td>Résolution</td><td>
Vérifiez les menaces détectées et résolvez-les en fonction des besoins.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508029
</th>
</tr><tr><td>Message</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une nouvelle analyse de la menace est requise.
</td></tr><tr><td>Résolution</td><td>
Exécutez une analyse système complète.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508030
</th>
</tr><tr><td>Message</td>
<td><b>ERROR_MP_CALLISTO_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une analyse hors connexion est requise.
</td></tr><tr><td>Résolution</td><td>
Exécutez Antivirus Microsoft Defender hors connexion. Vous pouvez en savoir plus sur la procédure à suivre dans <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">l’article Antivirus Microsoft Defender hors connexion</a>.
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508031
</th>
</tr><tr><td>Message</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique que Antivirus Microsoft Defender ne prend pas en charge la version actuelle de la plateforme et nécessite une nouvelle version de la plateforme.
</td></tr><tr><td>Résolution</td><td>
Vous ne pouvez utiliser Antivirus Microsoft Defender que dans Windows 10 et Windows 11. Pour Windows 8, Windows 7 et Windows Vista, vous pouvez utiliser <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">System Center Endpoint Protection</a>.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Les codes d’erreur suivants sont utilisés lors des tests internes de Antivirus Microsoft Defender.

Si vous voyez ces erreurs, vous pouvez essayer de [mettre à jour les définitions](manage-updates-baselines-microsoft-defender-antivirus.md) et forcer une nouvelle analyse directement sur le point de terminaison.


<table>
<tr>
<th colspan="3">Codes d’erreur internes</th>
</tr>
<tr>
<th><b>Code d’erreur</b></th>
<th>Message affiché</th>
<th>Raison possible de l’erreur et de la résolution</th>
</tr>
<tr>
<td>
0x80501004
</td>
<td>
<b>ERROR_MP_NO_INTERNET_CONN </b>
</td>
<td>
Vérifiez votre connexion Internet, puis réexécriez l’analyse.
</td>
</tr>
<tr>
<td>
0x80501000
</td>
<td>
<b>ERROR_MP_UI_CONSOLIDATION_BAS</b> E
</td>
<td rowspan="34">
Il s’agit d’une erreur interne. La cause n’est pas clairement définie.
</td>
<td rowspan="36">

</td>
</tr>
<tr>
<td>
0x80501001
</td>
<td>
<b>ERROR_MP_ACTIONS_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80501002
</td>
<td>
<b>ERROR_MP_NOENGINE</b>
</td>
</tr>
<tr>
<td>
0x80501003
</td>
<td>
<b>ERROR_MP_ACTIVE_THREATS</b>
</td>
</tr>
<tr>
<td>
0x805011011
</td>
<td>
<b>MP_ERROR_CODE_LUA_CANCELLED </b>
</td>
</tr>
<tr>
<td>
0x80501101
</td>
<td>
<b>ERROR_LUA_CANCELLATION </b>
</td>
</tr>
<tr>
<td>
0x80501102
</td>
<td>
<b>MP_ERROR_CODE_ALREADY_SHUTDOWN</b>
</td>
</tr>
<tr>
<td>
0x80501103
</td>
<td>
<b>MP_ERROR_CODE_RDEVICE_S_ASYNC_CALL_PENDING </b>
</td>
</tr>
<tr>
<td>
0x80501104
</td>
<td>
<b>MP_ERROR_CODE_CANCELLED</b>
</td>
</tr>
<tr>
<td>
0x80501105
</td>
<td>
<b>MP_ERROR_CODE_NO_TARGETOS</b>
</td>
</tr>
<tr>
<td>
0x80501106
</td>
<td>
<b>MP_ERROR_CODE_BAD_REGEXP</b>
</td>
</tr>
<tr>
<td>
0x80501107
</td>
<td>
<b>MP_ERROR_TEST_INDUCED_ERROR</b>
</td>
</tr>
<tr>
<td>
0x80501108
</td>
<td>
<b>MP_ERROR_SIG_BACKUP_DISABLED</b>
</td>
</tr>
<tr>
<td>
0x80508001
</td>
<td>
<b>ERR_MP_BAD_INIT_MODULES</b>
</td>
</tr>
<tr>
<td>
0x80508002
</td>
<td>
<b>ERR_MP_BAD_DATABASE</b>
</td>
</tr>
<tr>
<td>
0x80508004
</td>
<td>
<b>ERR_MP_BAD_UFS </b>
</td>
</tr>
<tr>
<td>
0x8050800C
</td>
<td>
<b>ERR_MP_BAD_INPUT_DATA</b>
</td>
</tr>
<tr>
<td>
0x8050800D
</td>
<td>
<b>ERR_MP_BAD_GLOBAL_STORAGE</b>
</td>
</tr>
<tr>
<td>
0x8050800E
</td>
<td>
<b>ERR_MP_OBSOLETE</b>
</td>
</tr>
<tr>
<td>
0x8050800F
</td>
<td>
<b>ERR_MP_NOT_SUPPORTED</b>
</td>
</tr>
<tr>
<td>
0x8050800F 0x80508010
</td>
<td>
<b>ERR_MP_NO_MORE_ITEMS </b>
</td>
</tr>
<tr>
<td>
0x80508011
</td>
<td>
<b>ERR_MP_DUPLICATE_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508012
</td>
<td>
<b>ERR_MP_BAD_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508013
</td>
<td>
<b>ERR_MP_BAD_USERDB_VERSION</b>
</td>
</tr>
<tr>
<td>
0x80508014
</td>
<td>
<b>ERR_MP_RESTORE_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80508016
</td>
<td>
<b>ERR_MP_BAD_ACTION</b>
</td>
</tr>
<tr>
<td>
0x80508019
</td>
<td>
<b>ERR_MP_NOT_FOUND</b>
</td>
</tr>
<tr>
<td>
0x80509001
</td>
<td>
<b>ERR_RELO_BAD_EHANDLE</b>
</td>
</tr>
<tr>
<td>
0x80509003
</td>
<td>
<b>ERR_RELO_KERNEL_NOT_LOADED</b>
</td>
</tr>
<tr>
<td>
0x8050A001
</td>
<td>
<b>ERR_MP_BADDB_OPEN</b>
</td>
</tr>
<tr>
<td>
0x8050A002
</td>
<td>
<b>ERR_MP_BADDB_HEADER</b>
</td>
</tr>
<tr>
<td>
0x8050A003
</td>
<td>
<b>ERR_MP_BADDB_OLDENGINE</b>
</td>
</tr>
<tr>
<td>
0x8050A004
</td>
<td>
<b>ERR_MP_BADDB_CONTENT </b>
</td>
</tr>
<tr>
<td>
0x8050A005
</td>
<td>
<b>ERR_MP_BADDB_NOTSIGNED</b>
</td>
</tr>
<tr>
<td>
0x8050801
</td>
<td>
<b>ERR_MP_REMOVE_FAILED</b>
</td>
<td>
Il s’agit d’une erreur interne. Il peut être déclenché lorsque la suppression des programmes malveillants échoue.
</td>
</tr>
<tr>
<td>
0x80508018
</td>
<td>
<b>ERR_MP_SCAN_ABORTED </b>
</td>
<td>
Il s’agit d’une erreur interne. Elle peut s’être déclenchée lorsqu’une analyse n’est pas terminée.
</td>
</tr>
</table>

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)


## <a name="related-topics"></a>Voir aussi

- [Rapport sur la protection Antivirus Microsoft Defender](report-monitor-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
