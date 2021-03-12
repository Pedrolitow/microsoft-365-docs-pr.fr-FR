---
title: Étapes de migration AD FS pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: 'Résumé : Étapes de migration des services AD FS (Active Directory Federation Services) pour la migration à partir de Microsoft Cloud Deutschland.'
ms.openlocfilehash: 030515227f3abdae82736807a01d1691d2d45552
ms.sourcegitcommit: 3d48e198e706f22ac903b346cadda06b2368dd1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2021
ms.locfileid: "50727466"
---
# <a name="ad-fs-migration-steps-for-the-migration-from-microsoft-cloud-deutschland"></a>Étapes de migration AD FS pour la migration à partir de Microsoft Cloud Deutschland

Cette modification de configuration peut être appliquée à tout moment avant le démarrage de la phase 4.
Une fois la phase 2 terminée, la modification de configuration fonctionne et vous pouvez vous connectez aux points de terminaison globaux Office 365 tels que `https://portal.office.com` . Si vous implémentez la modification de configuration avant la phase 2, les points de terminaison globaux Office 365 ne fonctionneront pas encore, mais la nouvelle confiance de partie de confiance fait toujours partie de votre configuration AD FS (Active Directory Federation Services). 

Pour migrer votre batterie de serveurs AD FS à partir de Microsoft Cloud Deutschland :

1. Back up your AD FS settings including FF trust info with [these steps](#backup). Nommez l’Deutschland_Only Microsoft **Cloud** de sauvegarde pour indiquer qu’elle ne possède que les informations client Microsoft Cloud Deutschland.
2. Testez la restauration à l’aide de la sauvegarde microsoft cloud Deutschland_Only, la batterie AD FS doit continuer à fonctionner en tant que Microsoft Cloud Deutschland uniquement.

Une fois que vous avez terminé et testé la sauvegarde AD FS, effectuez les étapes suivantes pour ajouter une nouvelle confiance de partie de confiance à votre configuration ADFS :

1. Ouvrir la console de gestion AD FS
2. Dans le volet gauche de la console de gestion **ADFS, développez ADFS,** puis **Relations** d’confiance, puis **Trusting Party Trusts**
3. Dans le volet droit, sélectionnez **Ajouter une confiance de partie de confiance...**
4. Sélectionnez **Suivant** sur la page **d’accueil** de l’Assistant Ajouter une confiance de partie de confiance.
5. Dans la page **Sélectionner une source de données,** sélectionnez Importer des données sur la partie de confiance publiée en ligne ou sur un réseau **local.** La **valeur d’adresse de métadonnées de** fédération (nom d’hôte ou URL) doit être définie sur `https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml` . Ensuite, cliquez sur **Suivant**.
6. Dans la page **Sélectionner une source de** données, tapez le nom complet tel que Microsoft Office **365 Identity Platform WorldWide**. Ensuite, cliquez sur **Suivant**.
7. Dans la page de l’Assistant **Configurer l’authentification multifacteur maintenant ?**, sélectionnez le choix approprié en fonction de vos exigences d’authentification. Si vous respectez la valeur par défaut, sélectionnez je ne souhaite pas configurer de **paramètres d’authentification multifacteur** pour cette relation d’confiance pour le moment. Vous pouvez modifier ce paramètre ultérieurement si vous le souhaitez.
8. Dans la **sélection des règles d’autorisation d’émission,** conservez autoriser tous les utilisateurs à accéder à cette **partie de** confiance sélectionnée en **cliquant** sur Suivant
9. Cliquez **sur Suivant** dans la page Prêt à ajouter **une** confiance pour terminer l’Assistant.
10. Cliquez **sur Fermer** sur la page Terminer. 

En fermant l’Assistant, l’confiance de partie de confiance avec les services globaux Office 365 est établie. Toutefois, aucune règle de transformation d’émission n’est encore configurée.

Vous pouvez utiliser [l’aide AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) pour générer les règles de transformation d’émission correctes. Les règles de revendication générées créées avec l’aide d’AD FS peuvent être ajoutées manuellement via la console de gestion AD FS ou avec PowerShell. L’aide des AD FS génère les scripts PowerShell nécessaires à l’exécution.  

<!--
    Question from ckinder
    is step #3 true?
    how to verify step 5? Need more information!
-->
1. Exécutez **l’aide** Générer des revendications sur AD FS  et copiez le script de transformation de revendications PowerShell à l’aide de l’option Copier dans le coin supérieur droit du script.
2. Ouvrez votre éditeur de texte préféré et collez le script PowerShell dans une nouvelle fenêtre de texte.
3. Ajoutez les lignes PowerShell suivantes à la fin du script passé à l’étape 2
    ```powershell
    $authzRules = "=>issue(Type = `"http://schemas.microsoft.com/authorization/claims/permit`", Value = `"true`"); "
    $RuleSet = New-AdfsClaimRuleSet -ClaimRule "<AD FS Help generated PSH>"
    Set-AdfsRelyingPartyTrust -TargetName “Microsoft Office 365 Identity Platform WorldWide” -IssuanceTransformRules $RuleSet.ClaimRulesString -IssuanceAuthorizationRules $authzRules
    ```
4. Exécutez le script PowerShell en toute sécurité.
5. Vérifiez que deux confiances de partie de confiance sont présentes ; un pour Microsoft Cloud Deutschland et un pour le service global Office 365.
6. Sauvegardez vos confiances à [l’aide de ces étapes.](#backup) Enregistrez-le sous le nom **FFAndWorldwide**.
7. Terminez votre migration back-end et vérifiez que les AD FS fonctionnent toujours pendant le processus de migration.

## <a name="ad-fs-disaster-recovery-wid-database"></a>Récupération d’urgence AD FS (base de données WID)

Pour restaurer la batterie de serveurs AD FS en cas d’urgence, l’outil de restauration rapide [AD FS](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/ad-fs-rapid-restore-tool) doit être utilisé. Par conséquent, l’outil doit être téléchargé et avant le début de la migration, une sauvegarde doit être créée et stockée en toute sécurité. Dans cet exemple (environnements TAT), les commandes suivantes ont été exécutés pour la back up de la batterie de serveurs :

<h2 id="backup"></h2>

### <a name="back-up-an-ad-fs-farm"></a>Back up an AD FS Farm

1. Installez l’outil de restauration rapide AD FS sur le serveur AD FS principal.
2. Importez le module dans une session PowerShell avec cette commande.
    ```powershell
    Import-Module "C:\Program Files (x86)\ADFS Rapid Recreation Tool\ADFSRapidRecreationTool.dll"
    ```
3. Exécutez la commande de sauvegarde :
    ```powershell
    Backup-ADFS -StorageType "FileSystem" -storagePath "<Storage path of backup>" -EncryptionPassword "<password>" -BackupComment "Restore Doku" -BackupDKM
    ```
4. Stockez la sauvegarde en toute sécurité sur la destination souhaitée.

### <a name="restore-an-ad-fs-farm"></a>Restaurer une batterie de serveurs AD FS

Si votre batterie de serveurs a complètement échoué et qu’il n’existe aucun moyen de revenir à l’ancienne batterie de serveurs, faites ce qui suit. 

1. Déplacez la sauvegarde précédemment générée et stockée vers le nouveau serveur AD FS principal.
2. Exécutez la commande `Restore-ADFS` PowerShell suivante. Si nécessaire, importez au préalable le certificat SSL AD FS.

    ```powershell
    Restore-ADFS -StorageType "FileSystem" -StoragePath "<Path to Backup>" -DecryptionPassword "<password>" -GroupServiceAccountIdentifier "<gMSA>" -DBConnectionString "WID" -RestoreDKM
    ```

3. Pointez vos nouveaux enregistrements DNS ou équilibreur de charge vers les nouveaux serveurs AD FS.

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client pendant la migration](ms-cloud-germany-transition-experience.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
