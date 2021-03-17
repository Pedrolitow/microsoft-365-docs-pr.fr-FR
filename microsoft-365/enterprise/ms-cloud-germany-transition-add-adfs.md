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
ms.openlocfilehash: 852fc8f93158d7b6080f1add5a05e7367539f889
ms.sourcegitcommit: 8f1721de52dbe3a12c11a0fa5ed0ef5972ca8196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2021
ms.locfileid: "50838412"
---
# <a name="ad-fs-migration-steps-for-the-migration-from-microsoft-cloud-deutschland"></a>Étapes de migration AD FS pour la migration à partir de Microsoft Cloud Deutschland

Cette modification de configuration doit être appliquée à tout moment avant le démarrage de la phase 2.
Une fois la phase 2 terminée, la modification de configuration fonctionne et vous pouvez vous connectez via des points de terminaison globaux Office 365 tels que `https://portal.office.com` . Si vous implémentez la modification de configuration avant la phase 2, les points de terminaison globaux Office 365 ne fonctionneront pas encore, mais la nouvelle confiance de partie de confiance fait toujours partie de votre configuration AD FS (Active Directory Federation Services). 

Les clients qui utilisent l’authentification fédérée avec les services AD FS (Active Directory Federation Services) ne doivent pas apporter de modifications aux AUTHENTIFICATION d’émetteur utilisées pour toutes les authentifications avec les services de domaine Active Directory (AD DS) locaux lors de la migration. La modification des URL d’émetteur entraîne des échecs d’authentification pour les utilisateurs du domaine. Les URIs d’émetteur peuvent être modifiés directement dans  AD  FS ou lorsqu’un domaine est converti de géré en fédéré et vice-versa. Nous vous recommandons de ne pas ajouter, supprimer ou convertir un domaine fédéré dans le client Azure AD qui a été migré. Les URL de l’émetteur peuvent être modifiées une fois la migration terminée.

Pour préparer votre batterie de serveurs AD FS pour la migration à partir de Microsoft Cloud Deutschland, effectuez les étapes suivantes :

1. En suivant ces étapes, vous pouvez également back up your AD FS settings, including the existing Microsoft Cloud Deutschland Relying Party [trust.](#backup) Nommez la **sauvegarde MicrosoftCloudDeueulandOnly** pour indiquer qu’elle ne possède que les informations du client Microsoft Cloud Deutschland.

   > [!NOTE]
   > La sauvegarde contient non seulement l’confiance de partie de confiance Office 365 existante pour Microsoft Cloud Deutschland, mais également toutes les autres confiances de partie de confiance présentes sur la batterie AD FS respective.

2. Testez la restauration à l’aide de la sauvegarde MicrosoftCloudDeueulandOnly, la batterie AD FS doit continuer à fonctionner en tant que Microsoft Cloud Deutschland uniquement.

Une fois que vous avez terminé et testé la sauvegarde AD FS, effectuez les étapes suivantes pour ajouter une nouvelle confiance de partie de confiance à votre configuration ADFS :

1. Ouvrez la console de gestion AD FS.

2. Dans le volet gauche de la console de gestion ADFS, accédez au menu Des **confiances de** partie de confiance.

3. Dans le volet droit, sélectionnez **Ajouter une confiance de partie de confiance...**

4. Sélectionnez **Démarrer** sur la page **d’accueil** de l’Assistant Ajouter une confiance de partie de confiance.

5. Dans la page **Sélectionner une source de données,** sélectionnez Importer des données sur la partie de confiance publiée en ligne ou sur un réseau **local.** La **valeur d’adresse de métadonnées de** fédération (nom d’hôte ou URL) doit être définie sur `https://nexus.microsoftonline-p.com/federationmetadata/2007-06/federationmetadata.xml` . Cliquez sur **Suivant**.

6. Dans la page **Spécifier le** nom complet, tapez le nom complet tel que **Microsoft Office 365 Identity Platform WorldWide**. Cliquez sur **Suivant**.

7. Si vous utilisez ADFS dans Windows Server 2012, dans la page de l’Assistant Configurer l’authentification **multifacteur maintenant ?**, sélectionnez le choix approprié en fonction de vos exigences d’authentification. Si vous respectez la valeur par défaut, sélectionnez Je ne souhaite pas configurer de **paramètres d’authentification multifacteur** pour cette relation d’confiance pour le moment. Vous pouvez modifier ce paramètre ultérieurement si vous le souhaitez.

8. For AD FS 2012: On the **Choose Issuance Authorization Rules**, keep Allow all users to access this **relying party** selected and click **Next**.

8. Pour AD FS 2016 et AD FS 2019 : dans la **page** Choisir la stratégie de contrôle d’accès, sélectionnez la stratégie de contrôle d’accès appropriée, puis cliquez sur **Suivant**. Si aucune n’est choisie, l’confiance de la partie de confiance **ne fonctionne pas.**

9. Cliquez **sur Suivant** dans la page Prêt à ajouter **une** confiance pour terminer l’Assistant.

10. Cliquez **sur Fermer** sur la page Terminer. 

En fermant l’Assistant, l’confiance de partie de confiance avec le service global Office 365 est établie. Toutefois, aucune règle de transformation d’émission n’est encore configurée.

Vous pouvez utiliser [l’aide AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) pour générer les règles de transformation d’émission correctes. Les règles de revendication générées créées avec l’aide d’AD FS peuvent être ajoutées manuellement via la console de gestion AD FS ou avec PowerShell. L’aide des AD FS génère les scripts PowerShell nécessaires à l’exécution.  

> [!NOTE]
> [L’aide des AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) génère les règles de transformation d’émission standard qui sont générées avec le produit. Toutefois, si des règles de transformation d’émission personnalisées sont en place dans l’trust de partie de confiance Microsoft Cloud Deutschland (par exemple, les UR d’émetteur personnalisés, les ID non standard immuables ou toute autre personnalisation), les règles générées par AD FS doivent être modifiées de manière à ce qu’elles correspondent à la logique personnalisée actuellement en place pour l’confiance de partie de confiance Microsoft Cloud Deutschland. Si ces personnalisations ne sont pas intégrées aux règles générées via l’aide [d’AD FS,](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator)l’authentification à **Microsoft Office 365 Identity Platform WorldWide** ne fonctionne probablement pas pour vos identités fédérées. 

1. Exécutez **l’aide Générer** des revendications [sur AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) et copiez le script PowerShell à l’aide de l’option  Copier dans le coin supérieur droit du script.

2. Suivez les étapes décrites dans l’aide [AD FS](https://adfshelp.microsoft.com/AadTrustClaims/ClaimsGenerator) sur la façon d’exécuter le script PowerShell dans votre batterie de serveurs AD FS pour générer l’confiance de partie de confiance globale.

3. Vérifiez que deux règles PartyTtrust de confiance sont présentes ; un pour Microsoft Cloud Deutschland et un pour le service global Office 365. La commande suivante peut être mise à profit pour la vérification. Elle doit renvoyer deux lignes, ainsi que les noms et identificateurs respectifs.

   ```powershell
   Get-AdfsRelyingPartyTrust | Where-Object {$_.Identifier -like 'urn:federation:MicrosoftOnline*'} | Select-Object Name, Identifier
   ```

4. Sauvegardez votre configuration de migration complète, y compris les deux confiances de partie de confiance, en suivant [ces étapes.](#backup) Enregistrez-le sous le **nom MicrosoftCloudDeueueulandAndWorldwide**.

5. Pendant la migration de votre client, vérifiez régulièrement que l’authentification AD FS fonctionne avec Microsoft Cloud Deutschland et le cloud global Microsoft dans les différentes étapes de migration prises en charge.


## <a name="ad-fs-disaster-recovery-wid-database"></a>Récupération d’urgence AD FS (base de données WID)

Pour restaurer la batterie de serveurs AD FS en cas d’urgence, l’outil de restauration rapide [AD FS](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/ad-fs-rapid-restore-tool) doit être utilisé. Par conséquent, l’outil doit être téléchargé et avant le début de la migration, une sauvegarde doit être créée et stockée en toute sécurité. Dans cet exemple, les commandes suivantes ont été exécutés pour la back up d’une batterie de serveurs s’exécutant sur une base de données WID :

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
