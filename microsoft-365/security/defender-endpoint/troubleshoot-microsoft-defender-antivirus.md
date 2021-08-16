---
title: ID d’événement et codes d’erreur de l’Antivirus Microsoft Defender
description: Rechercher les causes et les solutions pour les erreurs et les ID Antivirus Microsoft Defender événements
keywords: événement, code d’erreur, siem, journalisation, résolution des problèmes, wef, forwarding d’événement Windows
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/11/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 2c6532ca3d610d2cc0650ee8fee986b296cd54af90d62fdb71926938302635b1
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53867839"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Consulter les journaux d'événements et les codes d'erreur pour résoudre les problèmes liés à l'antivirus Microsoft Defender.

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Si vous rencontrez un problème avec Antivirus Microsoft Defender, vous pouvez rechercher dans les tableaux de cette rubrique un problème correspondant et une solution potentielle.

La liste des tableaux :

- [Antivirus Microsoft Defender’événement (s’appliquent](#windows-defender-av-ids) aux deux Windows 10 et Windows Server 2016)
- [Antivirus Microsoft Defender d’erreur client](#error-codes)
- [Codes d Antivirus Microsoft Defender client interne (utilisés par Microsoft pendant le développement et les tests)](#internal-error-codes)

> [!TIP]
> Vous pouvez également consulter le site web de démonstration microsoft Defender pour point de terminaison [sur demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) pour vérifier que les fonctionnalités suivantes fonctionnent :
> 
> - Protection fournie par le cloud
> - Apprentissage rapide (y compris Bloquer à la première vue)
> - Blocage d’applications potentiellement indésirables

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>Antivirus Microsoft Defender’événement

Antivirus Microsoft Defender des ID d’événement dans le journal Windows événements.

Vous pouvez afficher directement le journal des événements, ou si vous avez un outil tiers de gestion des événements et des informations de sécurité (SIEM), vous pouvez également utiliser des ID d’événement client Antivirus Microsoft Defender pour passer en revue des événements et des [erreurs](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) spécifiques à partir de vos points de terminaison.

Le tableau de cette section répertorie les principaux ID d’Antivirus Microsoft Defender et, dans la mesure du possible, fournit des solutions suggérées pour corriger ou résoudre l’erreur. 

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Pour afficher un événement Antivirus Microsoft Defender

1.  Ouvrez **l’Observateur d’événements.**
2.  Dans l’arborescence de la console, développez **Journaux des applications** et des services, puis **Microsoft,** **puis Windows**, **puis Windows Defender**.
3.  Double-cliquez sur **Opérationnel**.
4.  Dans le volet d’informations, affichez la liste des événements individuels pour trouver votre événement.
5.  Cliquez sur l’événement pour voir des détails spécifiques  sur un événement dans le volet inférieur, sous les **onglets** Général et Détails.

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
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Analyser les ressources : &lt; Ressources (telles que les fichiers/répertoires/BHO) qui ont été analysées. &gt; </dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; Utilisateur &gt; </dt>
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
<b>Analyse anti-programme malveillant terminée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt; Domain &gt; \& lt; Durée &gt; </dt>
<dt>de l’analyse utilisateur &lt; : durée d’une analyse. &gt; </dt>
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
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt; Domain &gt; &amp; lt; Durée &gt; </dt>
<dt>de l’analyse utilisateur &lt; : durée d’une analyse. &gt; </dt>
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
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt; Domaine &gt; \& lt; Utilisateur&gt;</dt>
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
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt; Domaine &gt; \& lt; Utilisateur&gt;</dt>
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
<b>Échec de l’analyse du logiciel anti-programme malveillant. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
<dl>
<dt>ID d’analyse : &lt; Numéro d’ID de &gt; l’analyse pertinente.</dt> 
<dt> Type d’analyse &lt; : type &gt; d’analyse, par exemple :<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
</ul>
</dt>
<dt>Paramètres d’analyse &lt; : paramètres d’analyse, &gt; par exemple :<ul>
<li>Analyse complète</li>
<li>Analyse rapide</li>
<li>Analyse du client</li>
</ul>
</dt>
<dt>Utilisateur : &lt; Domain &gt; \& lt; Code &gt; </dt>
<dt>d’erreur utilisateur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le client antivirus a rencontré une erreur et l’analyse en cours s’est arrêtée. L’analyse peut échouer en raison d’un problème côté client. Cet enregistrement d’événement inclut l’ID d’analyse, le type d’analyse (Antivirus Microsoft Defender, antispyware, anti-programme malveillant), les paramètres d’analyse, l’utilisateur qui a démarré l’analyse, le code d’erreur et une description de l’erreur.
Pour résoudre les problèmes de cet événement :
<ol>
<li>Exécutez à nouveau l’analyse.</li>
<li>Si elle échoue de la même manière, allez sur le <b></b> site de support <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a>, entrez le numéro d’erreur dans la zone de recherche pour rechercher le code d’erreur.</li>
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
<b>Le moteur du logiciel anti-programme malveillant a détecté des programmes malveillants ou d’autres logiciels potentiellement indésirables. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
État du contrôle </dt> 
<dt>d’accès au client : &lt; utilisateur &gt; </dt>
<dt>d’état &lt; : domaine &gt; \& lt; User &gt; </dt>
<dt>Process Name: &lt; Process &gt; in the PID</dt>
<dt>Signature Version: &lt; Definition version &gt; </dt>Engine
<dt>Version: Antimalware Engine &lt; version &gt; </dt>
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
Antivirus Microsoft Defender a pris des mesures pour protéger cet ordinateur contre les programmes malveillants ou d’autres logiciels potentiellement indésirables. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Utilisateur : &lt; Domain &gt; \& lt; Nom &gt; </dt>
<dt>d’utilisateur &lt; : &gt; </dt>ID du
<dt>nom de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : Gravité , par exemple 
<dt> &lt; &gt; :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt> Action : &lt; &gt; Action, par exemple :<ul>
<li>Nettoyer : la ressource a été nettoyée</li>
<li>Quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiée</li>
<li>Aucune action : aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État : &lt; Version &gt; de</dt>
<dt>la signature d’état &lt; : version de &gt; </dt>définition du moteur : Antimalware Engine
<dt> &lt; version &gt; </dt>
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
Antivirus Microsoft Defender a rencontré une erreur lors de l’action sur des programmes malveillants ou d’autres logiciels potentiellement indésirables. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Utilisateur : &lt; Domain &gt; \& lt; Nom &gt; </dt>
<dt>d’utilisateur &lt; : &gt; </dt>ID du
<dt>nom de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : Gravité , par exemple 
<dt> &lt; &gt; :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Action &gt; du chemin</dt> 
<dt> d’accès &lt; au fichier &gt; : Action, par exemple :<ul>
<li>Nettoyer : la ressource a été nettoyée</li>
<li>Quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiée</li>
<li>Aucune action : aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>Code d’erreur : &lt; Code de résultat du &gt; code d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt> 
<dt>Description de &lt; l’erreur : description &gt; de l’erreur.</dt> 
<dt>État : &lt; Version &gt; de</dt>
<dt>la signature d’état &lt; : version de &gt; </dt>définition du moteur : Antimalware Engine
<dt> &lt; version &gt; </dt>
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
<b>La plateforme anti-programme malveillant a restauré un élément de la quarantaine. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a restauré un élément de la quarantaine. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; File &gt; path</dt>
<dt>User: &lt; Domain &gt; \& lt; Version &gt; de</dt>
<dt>la signature utilisateur : version de &lt; définition &gt; </dt>du moteur : Antimalware Engine
<dt> &lt; version &gt; </dt>
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
<b>La plateforme anti-programme malveillant n’a pas pu restaurer un élément de la quarantaine. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de restauration d’un élément de la quarantaine. Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; File &gt; path</dt>
<dt>User: &lt; Domain &gt; \& lt; Code &gt; </dt>
<dt>d’erreur utilisateur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt> 
<dt>Description de &lt; l’erreur : description &gt; de l’erreur.</dt> 
<dt>Version de la signature : &lt; Version &gt; du moteur</dt>
<dt>de définition : Antimalware Engine &lt; version &gt; </dt>
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
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; File &gt; path</dt>
<dt>User: &lt; Domain &gt; \& lt; Version &gt; de</dt>
<dt>la signature utilisateur : version de &lt; définition &gt; </dt>du moteur : Antimalware Engine
<dt> &lt; version &gt; </dt>
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
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de suppression d’un élément de la quarantaine.
Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; File &gt; path</dt>
<dt>User: &lt; Domain &gt; \& lt; Code &gt; </dt>
<dt>d’erreur utilisateur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt> 
<dt>Description de &lt; l’erreur : description &gt; de l’erreur.</dt> 
<dt>Version de la signature : &lt; Version &gt; du moteur</dt>
<dt>de définition : Antimalware Engine &lt; version &gt; </dt>
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
<b>L’historique de suppression de la plateforme anti-programme malveillant des programmes malveillants et d’autres logiciels potentiellement indésirables.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a supprimé l’historique des programmes malveillants et autres logiciels potentiellement indésirables.
<dl>
<dt>Heure : heure à quel moment l’événement s’est produit, par exemple lorsque l’historique est purgé. Ce paramètre n’est pas utilisé dans les événements de menace afin qu’il n’y a aucune confusion quant à la durée de correction ou d’infection. Pour ceux-ci, nous les appelons spécifiquement Heure de l’action ou Heure de détection.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; Utilisateur &gt; </dt>
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
La plateforme anti-programme malveillant n’a pas pu supprimer l’historique des programmes malveillants et autres logiciels potentiellement indésirables.
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de suppression de l’historique des programmes malveillants et d’autres logiciels potentiellement indésirables.
<dl>
<dt>Heure : heure à quel moment l’événement s’est produit, par exemple lorsque l’historique est purgé. Ce paramètre n’est pas utilisé dans les événements de menace afin qu’il n’y a aucune confusion quant à la durée de correction ou d’infection. Pour ceux-ci, nous les appelons spécifiquement Heure de l’action ou Heure de la détection.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; Code &gt; </dt>
<dt>d’erreur utilisateur &lt; : code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard. </dt> 
<dt>Description de &lt; l’erreur : description &gt; de l’erreur.</dt>
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
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
État du contrôle </dt> 
<dt>d’accès au client : &lt; utilisateur &gt; </dt>
<dt>d’état &lt; : domaine &gt; \& lt; Nom &gt; </dt>
<dt>du processus utilisateur : processus dans &lt; l’ID &gt; </dt>de signature PID : gravité de correspondance
<dt>d’éumération.</dt> 
<dt>Version de la signature : &lt; Version &gt; de la définition</dt>du moteur
<dt>: Antimalware Engine la &lt; version &gt; </dt>
<dt>Fidelity Label :</dt>Nom de fichier cible : nom de fichier du
<dt> &lt; &gt; fichier.</dt>
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
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
Utilisateur UAC </dt> 
<dt>: domaine &lt; &gt; \& lt; User &gt; </dt>
<dt>Process Name: &lt; Process &gt; in the PID</dt>
<dt>Signature Version: &lt; Definition version &gt; </dt>Engine
<dt>Version: Antimalware Engine &lt; version &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est requise. Antivirus Microsoft Defender pouvez suspendre et prendre des mesures de routine sur cette menace. Si vous souhaitez supprimer la menace manuellement, dans l’interface Antivirus Microsoft Defender, cliquez <b>sur Nettoyer l’ordinateur.</b>
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
Antivirus Microsoft Defender a pris des mesures pour protéger cet ordinateur contre les programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
Utilisateur UAC </dt> 
<dt>: domaine &lt; &gt; \& lt; Nom &gt; </dt>
<dt>du processus utilisateur : processus dans &lt; l’action &gt; PID</dt>: 
<dt> &lt; &gt; Action, par exemple :<ul>
<li>Nettoyer : la ressource a été nettoyée</li>
<li>Quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiée</li>
<li>Aucune action : aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description des &gt; actions supplémentaires Code</dt>
<dt>d’erreur : &lt; code de résultat de code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> 
<dt>Version de la signature : &lt; &gt;</dt>Version du moteur de définition :
<dt> &lt; Antimalware Engine version &gt; </dt> REMARQUE : chaque fois que Antivirus Microsoft Defender, Microsoft Security Essentials, outil de suppression de logiciels malveillants ou System Center Endpoint Protection détecte un programme malveillant, il restaure les paramètres et services système suivants qui ont pu être modifiés :<ul>
<li>Paramètre par défaut d’Internet Explorer Microsoft Edge paramètre</li>
<li>Paramètres de contrôle d’accès utilisateur</li>
<li>Paramètres Chrome</li>
<li>Données de contrôle de démarrage</li>
<li>Paramètres de Registre Regedit et du Gestionnaire des tâches</li>
<li>Windows Mise à jour, service de transfert intelligent en arrière-plan et service d’appel de procédure distante</li>
<li>Windows Fichiers du système d’exploitation</li></ul>
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
Windows Vista (Service Pack 1 ou Service Pack 2), Windows 7 et ultérieures
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
Aucune action n’est nécessaire. Antivirus Microsoft Defender une menace est supprimée ou mise en quarantaine. 
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
Antivirus Microsoft Defender a rencontré une erreur non critique lors de l’action sur des programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
Utilisateur UAC </dt> 
<dt>: domaine &lt; &gt; \& lt; Nom &gt; </dt>
<dt>du processus utilisateur : processus dans &lt; l’action &gt; PID</dt>: 
<dt> &lt; &gt; Action, par exemple :<ul>
<li>Nettoyer : la ressource a été nettoyée</li>
<li>Quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiée</li>
<li>Aucune action : aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description des &gt; actions supplémentaires Code</dt>
<dt>d’erreur : &lt; code de résultat de code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> 
<dt>Version de la signature : &lt; Version &gt; du moteur</dt>
<dt>de définition : Antimalware Engine &lt; version &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Antivirus Microsoft Defender n’a pas réussi à effectuer une tâche liée à la correction des programmes malveillants. Il ne s’agit pas d’une défaillance critique.
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
<b>La plateforme anti-programme malveillant a rencontré une erreur critique lors de la tentative d’action sur des programmes malveillants ou d’autres logiciels potentiellement indésirables. Le message d’événement est plus détaillé.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur critique lors de l’action sur des programmes malveillants ou d’autres logiciels potentiellement indésirables.<br/>Pour plus d'informations, consultez les articles suivants :
<dl>
<dt>Nom : &lt; ID &gt; du nom</dt>
<dt>de la menace : Gravité de &lt; l’ID &gt; </dt>de menace : 
<dt> &lt; &gt; Gravité, par exemple :<ul>
<li>Faible</li>
<li>Modéré</li>
<li>Élevé</li>
<li>Grave</li>
</ul>
</dt>
<dt>Catégorie : &lt; Description de &gt; catégorie, par exemple, tout type de menace ou de programme malveillant.</dt> 
<dt>Chemin d’accès : &lt; Origine &gt; de la détection</dt> 
<dt> du chemin d’accès &lt; au fichier : origine de la &gt; détection, par exemple :
<ul>
<li>Inconnu</li>
<li>Ordinateur local</li>
<li>Partage réseau</li>
<li>Internet</li>
<li>Trafic entrant</li>
<li>Trafic sortant</li>
</ul>
</dt>
<dt>Type de détection &lt; : type de &gt; détection, par exemple :<ul>
<li>Heuristics</li>
<li>Generic</li>
<li>Concret</li>
<li>Signature dynamique</li>
</ul>
</dt>
<dt>Source de détection : &lt; source de détection par exemple &gt; :<ul>
<li>Utilisateur : initié par l’utilisateur</li>
<li>Système : initié par le système</li>
<li>En temps réel : composant en temps réel initié</li>
<li>IOAV : téléchargements d’IE et Outlook pièces jointes Express lancées</li>
<li>NIS : système d’inspection du réseau</li>
<li>IEPROTECT : IE - IExtensionValidation ; cela protège contre les contrôles de page web malveillants</li>
<li>Logiciel anti-programme malveillant à lancement précoce (ELAM). Cela inclut les programmes malveillants détectés par la séquence de démarrage</li>
<li>Attestation à distance</li>
</ul>Interface d’analyse anti-programme malveillant (AMSI). Principalement utilisé pour protéger les scripts (PS, VBS), bien qu’il puisse également être appelé par des tiers.
Utilisateur UAC </dt> 
<dt>: domaine &lt; &gt; \& lt; Nom &gt; </dt>
<dt>du processus utilisateur : processus dans &lt; l’action &gt; PID</dt>: 
<dt> &lt; &gt; Action, par exemple :<ul>
<li>Nettoyer : la ressource a été nettoyée</li>
<li>Quarantaine : la ressource a été mise en quarantaine</li>
<li>Supprimer : la ressource a été supprimée</li>
<li>Autoriser : la ressource a été autorisée à s’exécuter/exister</li>
<li>Défini par l’utilisateur : action définie par l’utilisateur qui est normalement une de cette liste d’actions que l’utilisateur a spécifiée</li>
<li>Aucune action : aucune action</li>
<li>Bloc : l’exécution de la ressource a été bloquée</li>
</ul>
</dt>
<dt>État de l’action : &lt; Description des &gt; actions supplémentaires Code</dt>
<dt>d’erreur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> 
<dt>Version de la signature : &lt; Version &gt; du moteur</dt>
<dt>de définition : Antimalware Engine &lt; version &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le Antivirus Microsoft Defender client a rencontré cette erreur en raison de problèmes critiques. Le point de terminaison peut ne pas être protégé. Examinez la description de l’erreur, puis suivez les étapes <b>d’action utilisateur appropriées</b> ci-dessous.
<table>
<tr>
<th>Action</th>
<th>Action de l’utilisateur</th>
</tr>
<tr>
<td>
<b>Supprimer</b>
</td>
<td>
Mettez à jour les définitions, puis vérifiez que la suppression a réussi.
</td>
</tr>
<tr>
<td>
<b>Clean</b>
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
Mettez à jour les définitions et vérifiez que l’utilisateur est autorisé à accéder aux ressources nécessaires.
</td>
</tr>
<tr>
<td>
<b>Autoriser</b>
</td>
<td>
Vérifiez que l’utilisateur est autorisé à accéder aux ressources nécessaires.
</td>
</tr>
</table>

Si cet événement persiste :<ol>
<li>Exécutez à nouveau l’analyse.</li>
<li>Si elle échoue de la même manière, allez sur le <b></b> site de support <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a>, entrez le numéro d’erreur dans la zone de recherche pour rechercher le code d’erreur.</li>
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
<b>Antivirus Microsoft Defender a déduit les h biens pour une ressource de menace.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender client est opérationnel dans un état sain.
<dl>
<dt>Version actuelle de la plateforme : &lt; Chemin d’accès actuel de la &gt; ressource</dt>de la version de la plateforme contre les menaces
<dt> &lt; : &gt; </dt>
<dt>hèses de chemin d’accès : &lt; hchéths &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Remarque : Cet événement sera enregistré uniquement si la stratégie suivante est définie : <b>ThreatFileHashLogging non signé.</b></div>
<div> </div>
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
<b>Si votre plateforme anti-programme malveillant signale l’état à une plateforme de surveillance, cet événement indique que la plateforme anti-programme malveillant est en cours d’exécution et dans un état sain. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender client est opérationnel dans un état sain.
<dl>
<dt>Version de la plateforme : &lt; Version actuelle &gt; de la signature</dt>de la version de la plateforme
<dt>: &lt; &gt; version</dt>de définition
<dt>du moteur : Antimalware Engine &lt; version &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le Antivirus Microsoft Defender client est dans un état sain. Cet événement est signalé toutes les heures.
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
<b>Endpoint Protection d’état du client (heure UTC)</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Rapport d’état du client antivirus.
<dl>
<dt>Version de la plateforme : &lt; &gt;</dt>Version actuelle du moteur de la plateforme : version
<dt> &lt; Antimalware Engine &gt; version</dt>du moteur d’inspection en temps réel du réseau : version antivirus du moteur d’inspection du réseau : version de signature
<dt> &lt; &gt; antivirus</dt>version
<dt> &lt; Antispyware &gt; signature version</dt>: version de signature Network
<dt> &lt; &gt; Realtime</dt>Inspection version : État RTP de la signature d’inspection
<dt> &lt; &gt; </dt>en temps réel du réseau : état de protection en temps réel
<dt> &lt; &gt; (Activer</dt>État de l’OAd ou désactivé : état IOAV sur l’état d’accès (activé ou désactivé) : état BM des
<dt> &lt; téléchargements d’Internet Internet (IE) &gt; </dt>et de l’état Outlook des pièces jointes express (activé ou désactivé) d’IOAV : état de surveillance du comportement (activé ou
<dt> &lt; &gt; désactivé)</dt>âge de signature antivirus : âge de signature antivirus
<dt> &lt; &gt; </dt>
<dt> &lt; &gt; (en jours) </dt>Âge de signature antispyware : âge de signature 
<dt> &lt; antispyware &gt; (en jours)</dt>Âge de la dernière analyse rapide : Dernière analyse rapide
<dt> &lt; &gt; (en jours)</dt>Âge de la dernière analyse complète : dernière heure de création de la signature antivirus
<dt> &lt; &gt; (en jours)</dt>:
<dt>? &lt; Heure de &gt; création de signature</dt>antivirus Heure de création de
<dt>signature Antispyware : ? &lt; Heure de création de &gt; signature antispyware Heure</dt>de la dernière
<dt>analyse rapide : ? &lt; Heure de début &gt; de la dernière analyse rapide</dt>Heure de fin de
<dt>l’analyse rapide : ? &lt; &gt;</dt>Heure de fin de la dernière analyse rapide Dernière source d’analyse rapide : Dernière source d’analyse rapide (0 = l’analyse&#39;pas été exécuté, 1 = initié par l’utilisateur, 2 = initié par le
<dt> &lt; &gt; système)</dt>Heure de début de la dernière analyse complète :
<dt>? &lt; Heure de début &gt; de la dernière analyse complète</dt>Heure de fin de
<dt>l’analyse complète : ? &lt; &gt;</dt>Dernière heure de fin de l’analyse complète Dernière source d’analyse complète : Dernière source d’analyse complète (0 = l’analyse&#39;pas été exécuté, 1 = initié par l’utilisateur, 2 = initié par le
<dt> &lt; &gt; système)</dt>État du produit : pour le dépannage interne 
<dt>
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
<b>Les définitions du logiciel anti-programme malveillant ont été correctement mises à jour. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La version de signature antivirus a été mise à jour.
<dl>
<dt>Version actuelle de la signature : &lt; Version actuelle &gt; de la signature</dt>Version précédente de la signature : type de
<dt>signature &lt; &gt; version précédente</dt>: type de 
<dt> &lt; &gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Type de mise à jour : &lt; Type de &gt; mise à jour , complet ou delta.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; User &gt; </dt>
<dt>Current Engine Version: &lt; Current engine version &gt; </dt>Previous Engine
<dt>Version: Previous engine &lt; version &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le Antivirus Microsoft Defender client est dans un état sain. Cet événement est signalé lorsque les signatures sont correctement mises à jour.
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
<b>Échec de la mise à jour des informations de sécurité. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de mise à jour des signatures.
<dl>
<dt>Nouvelle version de l’intelligence de la sécurité : &lt; Nouveau numéro &gt; de version</dt>
<dt>Version précédente de l’intelligence de la sécurité : &lt; Version &gt; précédente</dt>Mise à jour Source : Source de mise à 
<dt> &lt; &gt; jour, par exemple :
<ul>
<li>Dossier de mise à jour des informations de sécurité</li>
<li>Serveur de mise à jour de l’intelligence de sécurité interne</li>
<li>Microsoft Update Server</li>
<li>Partage de fichiers</li>
<li>Centre de protection Microsoft contre les programmes malveillants (MMPC)</li>
</ul>
</dt>
<dt>Étape de mise à jour &lt; : étape de mise à &gt; jour, par exemple :
<ul>
<li>Rechercher</li>
<li>Télécharger</li>
<li>Installer</li>
</ul>
</dt>Chemin d’accès source : nom de partage de fichiers pour la convention d’attribution de noms universelle (UNC), nom de serveur 
<dt>pour Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt> 
<dt> Type de signature &lt; : type de &gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Type de mise à jour : &lt; Type de &gt; mise à jour , complet ou delta.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; User &gt; </dt>
<dt>Current Engine Version: &lt; Current engine version &gt; </dt>Previous Engine
<dt>Version: Previous engine &lt; &gt; version</dt>Error
<dt>Code: Error code Result code associated &lt; with threat &gt; status. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Cette erreur se produit en cas de problème de mise à jour des définitions.
Pour résoudre les problèmes de cet événement :
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Mettez à jour les définitions</a> et forcez un rescan directement sur le point de terminaison.</li>
<li>Examinez les entrées dans le fichier %Windir%\WindowsUpdate.log pour plus d’informations sur cette erreur.</li>
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
<b>Le moteur du logiciel anti-programme malveillant a été mis à jour avec succès. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender version du moteur a été mise à jour.
<dl>
<dt>Version actuelle du moteur : &lt; Version actuelle &gt; du moteur</dt>Version précédente du moteur : Type de moteur
<dt> &lt; version &gt; </dt>précédente : type de moteur , moteur anti-programme malveillant ou moteur système d’inspection
<dt>du &lt; &gt; réseau.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; Utilisateur &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Aucune action n’est nécessaire. Le Antivirus Microsoft Defender client est dans un état sain. Cet événement est signalé lorsque le moteur du logiciel anti-programme malveillant est correctement mis à jour.
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
<b>Échec de la mise à jour du moteur du logiciel anti-programme malveillant. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de mise à jour du moteur.
<dl>
<dt>Nouvelle version du moteur :</dt>version précédente du moteur : type de moteur
<dt> &lt; version &gt; </dt>précédente : type de moteur , moteur anti-programme malveillant ou moteur système d’inspection
<dt>du &lt; &gt; réseau.</dt> 
<dt>Utilisateur : &lt; Domain &gt; \& lt; Code &gt; </dt>
<dt>d’erreur utilisateur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
La mise à Antivirus Microsoft Defender client a échoué. Cet événement se produit lorsque le client ne parvient pas à se mettre à jour lui-même. Cet événement est généralement dû à une interruption de la connectivité réseau pendant une mise à jour.
Pour résoudre les problèmes de cet événement :
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Mettez à jour les définitions</a> et forcez un rescan directement sur le point de terminaison.</li>
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
<b>Un problème est à l’écran lors du chargement des définitions de logiciel anti-programme malveillant. Le moteur du logiciel anti-programme malveillant tentera de charger le dernier ensemble connu de définitions.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de chargement des signatures et tente de revenir à un ensemble connu de signatures.
<dl>
<dt>Signatures tentées : Code</dt>
<dt>d’erreur : &lt; code de résultat du code &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> 
<dt>Version de la signature : &lt; Version &gt; du moteur de définition</dt>: version du moteur
<dt> &lt; anti-programme malveillant &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le Antivirus Microsoft Defender a tenté de télécharger et d’installer le fichier de définitions le plus récent et a échoué. Cette erreur peut se produire lorsque le client rencontre une erreur lors de la tentative de chargement des définitions, ou si le fichier est endommagé. Antivirus Microsoft Defender tenteront de revenir à un ensemble de définitions connu.
Pour résoudre les problèmes de cet événement :
<ol>
<li>Redémarrez l’ordinateur et réessayez.</li>
<li>Téléchargez les dernières définitions à partir <a href="https://aka.ms/wdsi">du site Renseignement de sécurité Microsoft.</a>
Remarque : la taille du fichier de définitions téléchargé à partir du site peut dépasser 60 Mo et ne doit pas être utilisée comme solution à long terme pour la mise à jour des définitions.
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
<b>Le moteur du logiciel anti-programme malveillant n’a pas réussi à se charger car la plateforme anti-programme malveillant est hors de la date. La plateforme anti-programme malveillant charge le dernier moteur anti-programme malveillant connu et tente de la mettre à jour.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender n’a pas pu charger le moteur du logiciel anti-programme malveillant, car la version actuelle de la plateforme n’est pas prise en charge. Antivirus Microsoft Defender revenir au dernier moteur connu et une tentative de mise à jour de plateforme sera tentée.
<dl>
<dt>Version actuelle de la plateforme : &lt; version actuelle de la plateforme&gt;</dt>
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
<dt>Version actuelle de la plateforme : &lt; Code d’erreur de la version actuelle &gt; </dt>de la plateforme : code de résultat du code
<dt> &lt; &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
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
<b>La plateforme sera bientôt à jour. Téléchargez la dernière plateforme pour maintenir une protection à jour.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender nécessitera bientôt une version plus récente de la plateforme pour prendre en charge les futures versions du moteur anti-programme malveillant. Téléchargez la dernière plateforme Antivirus Microsoft Defender pour maintenir le meilleur niveau de protection disponible.
<dl>
<dt>Version actuelle de la plateforme : &lt; version actuelle de la plateforme&gt;</dt>
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
<b>Le moteur du logiciel anti-programme malveillant a utilisé le service signature dynamique pour obtenir des définitions supplémentaires. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender service <i>signature dynamique pour récupérer</i> des signatures supplémentaires afin de protéger votre ordinateur.
<dl>
<dt>Version actuelle de la signature : &lt; Type de &gt; signature de la version</dt>actuelle de la signature : type de 
<dt> &lt; &gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Type de &gt; signature</dt>dynamique de la version actuelle du moteur 
<dt> : type de signature &lt; &gt; dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Sans limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin d’accès de persistance : &lt; Version &gt; </dt>de signature dynamique du chemin d’accès : timestamp de compilation de signature dynamique de numéro de
<dt> &lt; version &gt; </dt>: Type limite de persistance d’timestamp
<dt> &lt; &gt; </dt>: type de limite 
<dt> de &lt; &gt; persistance, par exemple :
<ul>
<li>Version VDM</li>
<li>Timestamp</li>
<li>Sans limite</li>
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
<b>Le service signature dynamique a supprimé les définitions dynamiques hors date. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender service <i>signature dynamique pour</i> ignorer les signatures obsolètes.
<dl>
<dt>Version actuelle de la signature : &lt; Type de &gt; signature de la version</dt>actuelle de la signature : type de 
<dt> &lt; &gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Type de &gt; signature</dt>dynamique de la version actuelle du moteur 
<dt> : type de signature &lt; &gt; dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Sans limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin d’accès de persistance : &lt; Version &gt; </dt>de signature dynamique du chemin d’accès : timestamp de compilation de signature dynamique de numéro de
<dt> &lt; version &gt; </dt>: Motif de suppression de l’timestamp
<dt> &lt; &gt; </dt>: Type de limite de persistance : type de limite de
<dt></dt> 
<dt> &lt; &gt; persistance, par exemple :
<ul>
<li>Version VDM</li>
<li>Timestamp</li>
<li>Sans limite</li>
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
Aucune action n’est nécessaire. Le Antivirus Microsoft Defender client est dans un état sain. Cet événement est signalé lorsque le service Signature dynamique supprime correctement les définitions dynamiques hors date.
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
<b>Le moteur du logiciel anti-programme malveillant a rencontré une erreur lors de la tentative d’utilisation du service signature dynamique. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative d’utilisation du <i>service signature dynamique.</i>
<dl>
<dt>Version actuelle de la signature : &lt; Type de &gt; signature de la version</dt>actuelle de la signature : type de 
<dt> &lt; &gt; signature, par exemple : <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Logiciel anti-programme malveillant</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Version actuelle du moteur : &lt; Code d’erreur de la version &gt; </dt>actuelle du moteur : code de résultat du code
<dt> &lt; &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> 
<dt> Type de signature dynamique : &lt; type de signature &gt; dynamique, par exemple :
<ul>
<li>Version</li>
<li>Timestamp</li>
<li>Sans limite</li>
<li>Durée</li>
</ul>
</dt>
<dt>Chemin d’accès de persistance : &lt; Version &gt; </dt>de signature dynamique du chemin d’accès : timestamp de compilation de signature dynamique de numéro de
<dt> &lt; version &gt; </dt>: Type limite de persistance d’timestamp
<dt> &lt; &gt; </dt>: type de limite 
<dt> de &lt; &gt; persistance, par exemple :
<ul>
<li>Version VDM</li>
<li>Timestamp</li>
<li>Sans limite</li>
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
<b>Le service signature dynamique a supprimé toutes les définitions dynamiques. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender toutes les signatures <i>du service signature</i> dynamique.
<dl>
<dt>Version actuelle de la signature : &lt; version actuelle de la signature&gt;</dt>
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
<b>Le moteur du logiciel anti-programme malveillant a téléchargé un fichier propre. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender téléchargé un fichier propre.
<dl>
<dt>Nom du fichier : &lt; Nom de &gt; fichier du fichier.</dt> 
<dt>Version actuelle de la signature : &lt; Version actuelle &gt; de la signature</dt>
<dt>Version actuelle du moteur : version actuelle du &lt; moteur &gt; </dt>
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
<b>Le moteur du logiciel anti-programme malveillant n’a pas réussi à télécharger un fichier propre. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de téléchargement d’un fichier propre.
<dl>
<dt>Nom du fichier : &lt; Nom de &gt; fichier du fichier.</dt> 
<dt>Version actuelle de la signature : &lt; Version actuelle &gt; du moteur de la signature</dt>: code d’erreur de la
<dt> &lt; version &gt; </dt>actuelle du moteur : code de résultat du code d’erreur
<dt>associé à &lt; &gt; l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Vérifiez vos paramètres de connectivité Internet.
Le client Antivirus Microsoft Defender rencontré une erreur lors de l’utilisation du service signature dynamique pour télécharger les dernières définitions d’une menace spécifique. Cette erreur est probablement due à un problème de connectivité réseau. 
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
<b>Le moteur du logiciel anti-programme malveillant a été téléchargé et est configuré pour s’exécuter hors connexion lors du redémarrage suivant du système.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender un antivirus hors connexion téléchargé et configuré pour s’exécuter au prochain redémarrage.
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
<b>Le moteur du logiciel anti-programme malveillant n’a pas pu télécharger et configurer une analyse hors connexion.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a rencontré une erreur lors de la tentative de téléchargement et de configuration de l’antivirus hors connexion.
<dl>
<dt>Code d’erreur : &lt; Code de résultat du &gt; code d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
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
<b>La prise en charge du logiciel anti-programme malveillant pour cette version du système d’exploitation va bientôt se terminer. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La prise en charge de votre système d’exploitation expirera prochainement. L’Antivirus Microsoft Defender sur un système d’exploitation hors prise en charge n’est pas une solution adéquate pour se protéger contre les menaces.
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
<b>La prise en charge du logiciel anti-programme malveillant pour ce système d’exploitation est terminée. Vous devez mettre à niveau le système d’exploitation pour une prise en charge continue. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
La prise en charge de votre système d’exploitation a expiré. L’Antivirus Microsoft Defender sur un système d’exploitation hors prise en charge n’est pas une solution adéquate pour se protéger contre les menaces.
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
<b>Le moteur du logiciel anti-programme malveillant ne prend plus en charge ce système d’exploitation et ne protège plus votre système contre les programmes malveillants. </b>
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
Antivirus Microsoft Defender Real-Time protection des données a rencontré une erreur et a échoué.
<dl>
<dt>Fonctionnalité : &lt; &gt; fonctionnalité, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements Internet Explorer et pièces jointes Microsoft Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Code d’erreur : &lt; Code de résultat du &gt; code d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt> Raison : la raison Antivirus Microsoft Defender protection en temps réel 
<dt>a redémarré une fonctionnalité.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Vous devez redémarrer le système, puis exécuter une analyse complète, car il est possible&#39;le système n’a pas été protégé pendant un certain temps.
La Antivirus Microsoft Defender client&#39;fonctionnalité de protection en temps réel a rencontré une erreur, car l’un des services n’a pas réussi à démarrer. S’il est suivi d’un ID d’événement 3007, l’échec était temporaire et le client anti-programme malveillant a récupéré après l’échec. 
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
<b>La protection en temps réel a récupéré après une défaillance. Nous vous recommandons d’exécution d’une analyse système complète lorsque vous voyez cette erreur. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender La protection en temps réel a redémarré une fonctionnalité. Il est recommandé d’exécuter une analyse système complète pour détecter les éléments qui ont pu être manqués pendant que cet agent était en panne.
<dl>
<dt>Fonctionnalité : &lt; &gt; fonctionnalité, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements d’IE et Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Raison : la raison Antivirus Microsoft Defender protection en temps réel a redémarré une fonctionnalité.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
La fonctionnalité de protection en temps réel a redémarré. Si cet événement se produit à nouveau, contactez <a href="https://go.microsoft.com/fwlink/?LinkId=215491">le support technique Microsoft.</a> 
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
Antivirus Microsoft Defender’analyse de la protection en temps réel pour les programmes malveillants et d’autres logiciels potentiellement indésirables a été activé.
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
Antivirus Microsoft Defender’analyse de la protection en temps réel pour les programmes malveillants et d’autres logiciels potentiellement indésirables a été désactivé. 
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
<dt>Fonctionnalité : &lt; &gt; fonctionnalité, par exemple :
<ul>
<li>Sur Access</li>
<li>Téléchargements d’IE et Outlook Express</li>
<li>Surveillance du comportement</li>
<li>Système d’inspection du réseau</li>
</ul>
</dt>
<dt>Configuration : </dt>
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
<b>La configuration de la plateforme anti-programme malveillant a été modifiée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender configuration a changé. S’il s’agit d’un événement inattendu, vous devez passer en revue les paramètres, car cela peut être le résultat d’un programme malveillant.
<dl>
<dt>Ancienne valeur : &lt; Old value number &gt; Old antivirus configuration value.</dt> 
<dt>Nouvelle valeur : &lt; Nouvelle valeur nombre &gt; Nouvelle valeur de configuration antivirus.</dt>
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
<b>Le moteur du logiciel anti-programme malveillant a rencontré une erreur et a échoué.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender moteur a été interrompu en raison d’une erreur inattendue.
<dl>
<dt>Type d’échec : &lt; Type &gt; d’échec, par exemple : Code d’exception</dt>d’incident ou de hang : ressource de
<dt> &lt; code &gt; </dt>
<dt>d’erreur : &lt; ressource &gt; </dt>
</dl>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Pour résoudre les problèmes de cet événement :<ol>
<li>Essayez de redémarrer le service.<ul>
<li>Pour les logiciels anti-programme malveillant, les antivirus et les logiciels espions, à une invite de commandes avec élévation de niveaux, tapez <b>net stop msmpsvc,</b>puis tapez <b>net start msmpsvc</b> pour redémarrer le moteur de logiciel anti-programme malveillant.</li>
<li>Pour le système <i>d’inspection</i>du réseau, à une invite de commandes avec élévation de niveaux, tapez <b>net start nissrv,</b>puis tapez <b>net start nissrv</b> pour redémarrer le moteur du système d’inspection du réseau à l’aide du fichier NiSSRV.exe. <i></i>
</li>
</ul>
</li>
<li>Si elle échoue de la même manière, recherchez le code d’erreur en <b></b> accédant au Site de support <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a> et en entrant le numéro d’erreur dans la zone de recherche, puis contactez le support <a href="https://go.microsoft.com/fwlink/?LinkId=215491">technique Microsoft.</a></li>
</ol>
</td>
</tr>
<tr>
<td>
Action de l’utilisateur :
</td>
<td >
Le moteur Antivirus Microsoft Defender client est arrêté en raison d’une erreur inattendue.
Pour résoudre les problèmes de cet événement :
<ol>
<li>Exécutez à nouveau l’analyse.</li>
<li>Si elle échoue de la même manière, allez sur le <b></b> site de support <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft</a>, entrez le numéro d’erreur dans la zone de recherche pour rechercher le code d’erreur.</li>
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
<b>L’analyse des programmes malveillants et autres logiciels potentiellement indésirables est activée. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender recherche de programmes malveillants et d’autres logiciels potentiellement indésirables a été activée.
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
<b>L’analyse des programmes malveillants et autres logiciels potentiellement indésirables est désactivée.</b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender recherche de programmes malveillants et d’autres logiciels potentiellement indésirables est désactivée.
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
Antivirus Microsoft Defender recherche de virus a été activée. 
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
Antivirus Microsoft Defender recherche de virus est désactivée. 
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
<b>La plateforme anti-programme malveillant va bientôt expirer. </b>
</td>
</tr>
<tr>
<td>
Description :
</td>
<td >
Antivirus Microsoft Defender a entré une période de grâce et va bientôt expirer. Après l’expiration, ce programme désactive la protection contre les virus, les logiciels espions et d’autres logiciels potentiellement indésirables.
<dl>
<dt>Raison de l’expiration</dt> : la raison Antivirus Microsoft Defender arrive à expiration. 
<dt>Date d’expiration : date Antivirus Microsoft Defender date d’expiration.</dt>
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
Antivirus Microsoft Defender période de grâce a expiré. La protection contre les virus, les logiciels espions et les autres logiciels potentiellement indésirables est désactivée.
<dl>
<dt>Raison de l’expiration :</dt>
<dt>Date d’expiration : </dt>Code 
<dt>d’erreur : code de résultat du code &lt; &gt; d’erreur associé à l’état de la menace. Valeurs HRESULT standard.</dt> 
<dt>Description de l’erreur : &lt; Description de &gt; l’erreur.</dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Antivirus Microsoft Defender codes d’erreur du client si Antivirus Microsoft Defender des problèmes, il vous donne généralement un code d’erreur pour vous aider à résoudre le problème. Le plus souvent, une erreur signifie qu’il y a eu un problème d’installation d’une mise à jour.
Cette section fournit les informations suivantes sur les erreurs Antivirus Microsoft Defender client.
-   Le code -   d’erreur La raison possible de l’erreur -   Conseils sur ce qu’il faut faire maintenant

Utilisez les informations de ces tableaux pour résoudre les problèmes Antivirus Microsoft Defender codes d’erreur.


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
Cette erreur indique que vous n’avez peut-être plus de mémoire. 
</td>
</tr>
<tr>
<td>Résolution</td>
<td>
<ol>
<li>Vérifiez la mémoire disponible sur votre appareil.</li>
<li>Fermez les applications inutilisées en cours d’exécution pour libérer de la mémoire sur votre appareil.</li>
<li>Redémarrez l’appareil et ré-exécutez l’analyse. 
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
<li>Mettez à jour les définitions. Les deux :<ol>
<li>Cliquez sur <b>le bouton Mettre à jour les définitions</b> sous <b>l’onglet</b> Mettre à jour Antivirus Microsoft Defender. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Ou,
</li>
<li>Téléchargez les dernières définitions à partir <a href="https://aka.ms/wdsi">du site Renseignement de sécurité Microsoft.</a>
Remarque : la taille du fichier de définitions téléchargé à partir du site peut dépasser 60 Mo et ne doit pas être utilisée comme solution à long terme pour la mise à jour des définitions.
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
Cette erreur indique qu’il peut y avoir une erreur de configuration du moteur ; Généralement, cela est lié aux données d’entrée qui ne permettent pas au moteur de fonctionner correctement. 
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x805080211
</th>
</tr><tr><td>Message</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une Antivirus Microsoft Defender mise en quarantaine d’une menace a échoué. 
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
Cette erreur indique que la menace n’est peut-être plus présente sur le média ou que des programmes malveillants peuvent vous empêcher d’analyser votre appareil. 
</tr><tr><td>Résolution
</td>
<td>
Exécutez le <a href="https://www.microsoft.com/security/scanner/default.aspx">Scanner de sécurité Microsoft</a> puis mettez à jour votre logiciel de sécurité et essayez à nouveau. 
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508024 </th></tr>
<tr>
<td>Message</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une analyse complète du système peut être nécessaire. 
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
Suivez les étapes de correction manuelle décrites dans le Programme d’aide à la protection microsoft contre les programmes <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">malveillants.</a> Vous pouvez trouver un lien spécifique aux menaces dans l’historique des événements.<br/></td>
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
Antivirus Microsoft Defender’est pas en mesure de corriger les menaces détectées à l’intérieur de l’archive. Envisagez de supprimer manuellement les ressources détectées. 
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
Vérifiez les menaces détectées et résolvez-les selon les besoins. 
</td>
</tr>
<tr>
<th colspan="2">Code d’erreur : 0x80508029
</th>
</tr><tr><td>Message</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Raison possible</td>
<td>
Cette erreur indique qu’une nouvelle recherche de la menace est requise. 
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
Exécutez le Antivirus Microsoft Defender. Vous pouvez en savoir plus sur la façon de le faire dans <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">l’article Antivirus Microsoft Defender hors connexion.</a>
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
Vous ne pouvez utiliser les Antivirus Microsoft Defender que dans Windows 10. Pour Windows 8, Windows 7 et Windows Vista, vous pouvez utiliser <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">System Center Endpoint Protection</a>.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Les codes d’erreur suivants sont utilisés lors des tests internes de Antivirus Microsoft Defender.

Si vous voyez ces erreurs, vous pouvez essayer de mettre à jour les [définitions](manage-updates-baselines-microsoft-defender-antivirus.md) et forcer une nouvellecane directement sur le point de terminaison.


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
Vérifiez votre connexion Internet, puis exécutez à nouveau l’analyse.
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
Il s’agit d’une erreur interne. Elle peut être déclenchée lorsque la suppression des programmes malveillants ne réussit pas. 
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
Il s’agit d’une erreur interne. Il se peut qu’il se soit déclenché lorsqu’une analyse échoue. 
</td>
</tr>
</table>

## <a name="related-topics"></a>Sujets connexes

- [Rapport sur la protection Antivirus Microsoft Defender de données](report-monitor-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)