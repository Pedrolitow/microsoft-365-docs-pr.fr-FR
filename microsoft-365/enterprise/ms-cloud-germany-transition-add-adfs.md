---
title: Étapes de migration d’AD FS pour la migration à partir de Microsoft Cloud Deutschland
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
description: 'Résumé : étapes de migration des services ADFS (Active Directory Federation Services) pour la migration à partir de Microsoft Cloud Deutschland.'
ms.openlocfilehash: 175734851c2838eb2e224a9afb57a600d4ed9523
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49554797"
---
# <a name="ad-fs-migration-steps-for-the-migration-from-microsoft-cloud-deutschland"></a>Étapes de migration d’AD FS pour la migration à partir de Microsoft Cloud Deutschland

Pour migrer votre batterie de serveurs AD FS (Active Directory Federation Services) à partir de Microsoft Cloud Deutschland :

1. Sauvegardez vos paramètres AD FS, y compris les informations de confiance de FF, en [procédant comme suit](#backup). Nommez la sauvegarde **Cloud microsoft Deutschland_Only** pour indiquer qu’elle contient uniquement les informations du client Microsoft Cloud Deutschland.
2. Test de la restauration à l’aide de Microsoft Cloud Deutschland_Only Backup, la batterie AD FS doit continuer à fonctionner en tant que Microsoft Cloud Deutschland uniquement.
3. Créer une approbation de partie de confiance à partir des **services AD FS > Office 365**.
4. Dans **approbations de partie de confiance** dans la console de gestion AD FS, sélectionnez **Ajouter une approbation de partie de confiance**.
5. Sélectionnez **suivant** dans la page d' **Accueil** de l’Assistant Ajout d’approbation de partie de confiance.
6. Dans la page **Sélectionner la source de données** , sélectionnez **Importer les données relatives à la partie de confiance publiée en ligne ou sur un réseau local**. La valeur de l' **adresse de métadonnées de Fédération (nom d’hôte ou URL)** est définie sur `https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml` . Cliquez sur **Suivant**.
7. Dans la page **Sélectionner la source de données** , tapez le nom complet. Microsoft recommande la **plateforme d’identité Microsoft Office 365 dans le monde**. Cliquez sur **Suivant**.
8. Cliquez sur **suivant** dans la page **configurer l’authentification multifacteur maintenant ?**, **Choisissez règles d’autorisation d’émission** et **prêt à ajouter** des pages d’approbation.
9. Cliquez sur **Fermer** sur la page **Terminer** .

En fermant l’Assistant, l’approbation de la partie de confiance pour le service Office 365 services eSTS est établie. Toutefois, aucune règle de transformation d’émission n’est établie.

Vous pouvez utiliser l' [aide d’AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) pour générer les règles de transformation d’émission correctes. Les règles de revendication générées créées avec l’aide d’AD FS peuvent être ajoutées manuellement via la console de gestion AD FS ou avec PowerShell. L’aide d’AD FS génère les scripts PowerShell nécessaires à exécuter.  

1. Exécutez **générer des revendications** sur l’aide d’AD FS et copiez le script de transformation de revendications PowerShell à l’aide de l’option de **copie** située dans le coin supérieur droit du script.
2. Collez le PowerShell généré dans ce qui suit :

  ```powershell
  $RuleSet = New-AdfsClaimRuleSet -ClaimRule "<AD FS Help generated PSH>"
  Set-AdfsRelyingPartyTrust -TargetName “Microsoft Office 365 Identity Platform WorldWide” -IssuanceTransformRules $RuleSet.ClaimRulesString;
  ```
3.  Exécutez le script terminé.
4.  Vérifier que deux approbations de partie de confiance sont présentes ; un pour le monde entier et un pour BF.
5.  Sauvegardez vos approbations à l’aide de [ces étapes](#backup). Enregistrez-le sous le nom **FFAndWorldwide**.
6.  Terminez votre migration principale et vérifiez qu’AD FS fonctionne toujours pendant le processus de migration.

## <a name="ad-fs-disaster-recovery-wid-database"></a>Récupération d’urgence AD FS (base de données WID)

La restauration de la batterie AD FS dans un incident de [restauration rapide AD FS](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/ad-fs-rapid-restore-tool) doit être exploitée. Par conséquent, l’outil doit être téléchargé et avant le début de la migration, une sauvegarde doit être créée et stockée en toute sécurité. Dans cet exemple (environnements TAT), les commandes suivantes ont été exécutées pour sauvegarder la batterie de serveurs :

<h2 id="backup"></h2>

### <a name="back-up-an-ad-fs-farm"></a>Sauvegarder une batterie AD FS

1. Installez l’outil de restauration rapide AD FS sur le serveur AD FS principal.
2. Importez le module dans une session PowerShell à l’aide de cette commande.

  ```powershell
  Import-Module "C:\Program Files (x86)\ADFS Rapid Recreation Tool\ADFSRapidRecreationTool.dll"
  ```
3. Exécutez la commande Backup :

  ```powershell
  Backup-ADFS -StorageType "FileSystem" -storagePath "<Storage path of backup>" -EncryptionPassword "<password>" -BackupComment "Restore Doku" -BackupDKM
  ```

4. Stockez la sauvegarde en toute sécurité sur une destination souhaitée. 

### <a name="restore-an-ad-fs-farm"></a>Restaurer une batterie de serveurs AD FS

Si votre batterie de serveurs a échoué complètement et qu’il n’existe aucun moyen de revenir à l’ancienne batterie de serveurs, procédez comme suit. 

1. Déplacez la sauvegarde précédemment générée et stockée sur le nouveau serveur AD FS principal.
2. Exécutez la `Restore-ADFS` commande PowerShell suivante. Si nécessaire, importez le certificat SSL AD FS à l’avance.

  ```powershell
  Restore-ADFS -StorageType "FileSystem" -StoragePath "<Path to Backup>" -DecryptionPassword "<password>" -GroupServiceAccountIdentifier "<gMSA>" -DBConnectionString "WID" -RestoreDKM
  ```

3. Pointez vos nouveaux enregistrements DNS ou équilibreur de charge vers les nouveaux serveurs AD FS.

## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts sur les phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
