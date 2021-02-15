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
ms.openlocfilehash: c946ec3c0772cf95ab696266475b50959d682ef2
ms.sourcegitcommit: 849b365bd3eaa9f3c3a9ef9f5973ef81af9156fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49688664"
---
# <a name="ad-fs-migration-steps-for-the-migration-from-microsoft-cloud-deutschland"></a>Étapes de migration AD FS pour la migration à partir de Microsoft Cloud Deutschland

Pour migrer votre batterie de serveurs AD FS (Active Directory Federation Services) à partir de Microsoft Cloud Deutschland :

1. Back up your AD FS settings including FF trust info with [these steps](#backup). Nommez l’Deutschland_Only microsoft **cloud** de sauvegarde pour indiquer qu’elle ne possède que les informations client Microsoft Cloud Deutschland.
2. Testez la restauration à l’aide de la sauvegarde microsoft cloud Deutschland_Only, la batterie AD FS doit continuer à fonctionner en tant que Microsoft Cloud Deutschland uniquement.
3. Créez une nouvelle confiance de partie de confiance à partir **d’AD FS > services Office 365**.
4. Dans **les trusts de partie de confiance** dans la console de gestion AD FS, sélectionnez Ajouter une confiance de partie de **confiance.**
5. Sélectionnez **Suivant** sur la page **d’accueil** de l’Assistant Ajouter une confiance de partie de confiance.
6. Dans la page **Sélectionner une source de données,** sélectionnez Importer des données sur la partie de confiance publiée en ligne ou sur un réseau **local.** La **valeur d’adresse de métadonnées de fédération (nom d’hôte** ou URL) est définie sur `https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml` . Cliquez sur **Suivant**.
7. Dans la page **Sélectionner une source de données,** tapez le nom complet. Microsoft recommande de **Microsoft Office 365 Identity Platform WorldWide**. Cliquez sur **Suivant**.
8. Cliquez **sur Suivant** dans les pages Configurer l’authentification **multifacteur maintenant ?**, Sélectionnez Règles d’autorisation d’émission et Prêt à ajouter  **une** approbation.
9. Cliquez **sur Fermer** sur la page Terminer. 

En fermant l’Assistant, l’confiance de partie de confiance pour les services Office 365 eSTS est établie. Toutefois, aucune règle de transformation d’émission n’est établie.

Vous pouvez utiliser [l’aide AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) pour générer les règles de transformation d’émission correctes. Les règles de revendication générées créées avec l’aide d’AD FS peuvent être ajoutées manuellement via la console de gestion AD FS ou avec PowerShell. L’aide des AD FS génère les scripts PowerShell nécessaires à exécuter.  

1. Exécutez **l’aide** Générer des revendications sur AD FS  et copiez le script de transformation de revendications PowerShell à l’aide de l’option Copier dans le coin supérieur droit du script.
2. Collez le PowerShell généré dans les données suivantes :

  ```powershell
  $RuleSet = New-AdfsClaimRuleSet -ClaimRule "<AD FS Help generated PSH>"
  Set-AdfsRelyingPartyTrust -TargetName “Microsoft Office 365 Identity Platform WorldWide” -IssuanceTransformRules $RuleSet.ClaimRulesString;
  ```
3.  Exécutez le script terminé.
4.  Vérifiez que deux confiances de partie de confiance sont présentes ; un pour le monde entier et un pour BF.
5.  Sauvegardez vos confiances à [l’aide de ces étapes.](#backup) Enregistrez-le sous le nom **FFAndWorldwide**.
6.  Terminez votre migration back-end et vérifiez que les AD FS fonctionnent toujours pendant le processus de migration.

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
