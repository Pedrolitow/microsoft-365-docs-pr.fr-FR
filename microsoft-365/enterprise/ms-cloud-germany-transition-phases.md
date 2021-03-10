---
title: Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (général)
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 03/05/2021
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
description: 'Résumé : Comprendre les actions et les impacts des phases de migration du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: 045e29cba293dd74d3a77beae80d78380eaa4147
ms.sourcegitcommit: 9adb89206daa075af34a73bcb7e8fb86d7c2919a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/10/2021
ms.locfileid: "50604007"
---
# <a name="migration-phases-actions-and-impacts-for-the-migration-from-microsoft-cloud-deutschland-general"></a>Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (général)

Les migrations de clients de Microsoft Cloud Deutschland (MCD) vers la région « Allemagne » des services globaux Office 365 de Microsoft sont exécutées en tant qu’ensemble de phases et leurs actions configurées pour chaque charge de travail. Cette figure montre les neuf phases de migration vers les nouveaux centres de données allemands.

![Les neuf phases de migration vers les nouveaux centres de données allemands](../media/ms-cloud-germany-migration-opt-in/migration-organization.png)

Le processus de migration s’achèvera sur plusieurs semaines en fonction de la taille et de la complexité globales de l’organisation. Pendant la migration, les utilisateurs et les administrateurs peuvent continuer à utiliser les services avec des modifications notables détaillées dans cette documentation. Le graphique et le tableau définissent les phases et les étapes de la migration.

|Étape|Duration|Partie responsable|Description|
|:--------|:--------|:--------|:--------|
|Opt-In|Heures|Client|Choisissez votre organisation pour la migration.|
|Pré-travail|Jours|Client|Effectuer le travail nécessaire pour préparer les utilisateurs, les stations de travail et le réseau pour la migration.|
|Azure Active Directory (Azure AD)|1 à 2 jours|Microsoft|Migrez l’organisation Azure AD vers le monde entier.|
|Azure|Semaines|Client|Créez des abonnements Azure dans le monde entier et transition des services Azure.|
|Transition de licence & abonnement|1 à 2 jours|Microsoft|Acheter des abonnements dans le monde entier, annuler des abonnements Microsoft Cloud Deutschland et passer des licences utilisateur.|
|SharePoint et OneDrive|15+ jours|Microsoft|Migrer du contenu SharePoint et OneDrive Entreprise, en sharepoint.de URL.|
|Exchange Online|15+ jours|Microsoft|Migrez le contenu Exchange Online et migrez vers des URL dans le monde entier.|
|Sécurité et conformité|1 à 2 jours|Microsoft|Transition de la sécurité & stratégies de conformité et du contenu.|
|Skype Entreprise|1 à 2 jours|Microsoft|Transition de Skype Entreprise vers Microsoft Teams.|
|Power BI & Dynamics 365|15+ jours|Microsoft|Migrez le contenu Power BI et Dynamics 365.|
|Finaliser Azure AD|1 à 2 jours|Microsoft|Effectuer un cutover client dans le monde entier.|
|Clean-Up|1 à 2 jours|Client|Nettoyez les connexions héritées à Microsoft Cloud Deutschland, telles que l’confiance de partie de confiance AD FS (Active Directory Federation Services), Azure AD Connect et les redémarrages du client Office.|

Les phases et leurs actions garantissent que les données et expériences critiques sont migrées vers les services globaux Office 365. Une fois que votre client est ajouté à la file d’attente de migration, chaque charge de travail est exécutée en tant qu’ensemble d’étapes exécutées sur le service backend. Certaines charges de travail peuvent nécessiter des actions de l’administrateur (ou de l’utilisateur) ou la migration peut affecter l’utilisation des phases exécutées et abordées dans Comment la migration est-elle [organisée ?](ms-cloud-germany-transition.md#how-is-the-migration-organized)

Les sections suivantes contiennent des actions et des effets pour les charges de travail au fil de différentes phases de la migration. Examinez les tableaux et déterminez les actions ou effets applicables à votre organisation. Assurez-vous que vous êtes prêt à exécuter les étapes des phases respectives, le cas échéant. L’échec des étapes nécessaires peut entraîner une panne du service et retarder l’achèvement de la migration vers les services Office 365.

## <a name="opt-in"></a>Opt-In

**S’applique** à : Tous les clients avec un client Office 365 hébergé dans Microsoft Cloud Deutschland (MCD)
| Étapes | Description | Impact |
|:-------|:-----|:-------|
| Nous ne pouvons pas migrer des locataires Office 365 hébergés dans le MCD sans le consentement. | Microsoft obtient le droit de migrer de deux manières, ce qui permet à Microsoft d’orchestrer la transition des données et des services vers l’instance des services globaux Office 365. <ol><li>L’administrateur client Office 365 choisit la migration pilotée par Microsoft. </li><li> Les clients renouvellent tous les abonnements dans leur client McD Office 365 après le 1er mai 2020. Nous informerons ces clients du droit de migration chaque mois, attendrons 30 jours pour donner aux clients la possibilité d’annuler, puis nous les choisirons directement.</li></ol> | <ul><li>Le client est marqué comme étant accepté pour la migration et le Centre d’administration affiche la confirmation. </li><li>L’accusé de réception est publié dans le centre de messages du client Office 365. La configuration du service se poursuit à partir des points de terminaison Microsoft Cloud Deutschland. </li><li>Le client administatror doit surveiller le Centre de messages Office 365 pour les mises à jour sur l’état de la phase d’igration. </li></ul>|

## <a name="subscription-phase-3"></a>Abonnement (phase 3)

**S’applique** à : Tous les clients avec un client Office 365 hébergé dans Microsoft Cloud Deutschland (MCD)

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Les abonnements sont transférés et les licences sont réassignées. | Les abonnements aux services globaux Office 365 correspondants sont achetés dans l’instance globale d’Office 365 pour les abonnements Microsoft Cloud Deutschland transférés. Les utilisateurs ayant des licences Microsoft Cloud Deutschland se voit attribuer des licences dans l’instance globale d’Office 365. Les abonnements Microsoft Cloud Deutschland hérités sont supprimés du client de services Office 365 à la fin.| <ul><li>Les modifications apportées aux abonnements existants seront bloquées (par exemple, aucun nouvel achat d’abonnement ou changement de nombre de sièges) au cours de cette phase.</li><li>Les modifications d’attribution de licence seront bloquées.</li><li>L’abonnement Microsoft Cloud Deutschland sera migré vers l’abonnement aux services globaux Office 365 correspondant. L’offre de services globale Office 365 de cet abonnement est définie par Microsoft (également appelée _mappage des offres)._</li><li>Le nombre de fonctionnalités (plans de service) proposées par les services Office 365 peut être supérieur à celui de l’offre Microsoft Cloud Deutschland d’origine. Les licences utilisateur dans les services Office 365 seront affectées de manière équivalente à des fonctionnalités Microsoft Cloud Deutschland similaires (plans de service). Les licences utilisateur de tous les utilisateurs seront automatiquement attribuées aux nouvelles fonctionnalités. L’administrateur doit prendre une action explicite pour désactiver ces licences, si nécessaire. </li><li>Lorsque la migration des abonnements est terminée, les services Office 365 et les abonnements Microsoft Cloud Deutschland sont visibles dans le portail d’administration Office 365, avec l’état des abonnements Microsoft Cloud Deutschland comme étant supprimés. </li><li>Les utilisateurs seront réassignés avec des licences liées aux nouveaux abonnements aux services Office 365. Tous les processus clients qui ont des dépendances sur les abonnements MCD ou les GUID SKU sont rompus et doivent être révisés avec l’offre de services Office 365. </li><li>Les nouveaux abonnements dans les services Office 365 seront achetés avec la nouvelle période (mensuelle/trimestrielle/année), et le client recevra un remboursement au pro total pour le solde inutilisé de l’abonnement Microsoft Cloud Deutschland. </li><li>Les clients Microsoft Cloud Deutschland partenaires ne seront pas migrés. Les clients CSP seront migrés vers les services Office 365 sous le nouveau client de services Office 365 du même partenaire. Après la migration des clients, le partenaire peut gérer ce client uniquement à partir du client des services Office 365. </li><li>Des fonctionnalités supplémentaires sont disponibles (par exemple, Microsoft Planner et Microsoft Flow), sauf si elles sont désactivées par l’administrateur client. Pour plus d’informations sur la désactivation des plans de service affectés aux licences des utilisateurs, voir Désactiver l’accès aux [services Microsoft 365](disable-access-to-services-while-assigning-user-licenses.md)tout en attribuant des licences utilisateur.</li></ul> |
||||

## <a name="sharepoint-online-phase-4"></a>SharePoint Online (phase 4)

**S’applique à**: Tous les clients utilisant SharePoint Online

| Étapes | Description | Impact |
|:-------|:-----|:-------|
| SharePoint et OneDrive sont transitionn s | SharePoint Online et OneDrive Entreprise sont migrés de Microsoft Cloud Deutschland vers les services globaux Office 365 au cours de cette phase.<br><ul><li>Les URL Microsoft Cloud Deutschland existantes sont conservées (par exemple, `contoso.sharepoint.de` ).</li><li>Les sites existants sont conservés.</li><li>Les jetons d’authentification côté client qui ont été émis par le service d’émission de jeton de sécurité (STS) dans l’instance des services globaux Microsoft Cloud Deutschland ou Office 365 sont valides pendant la transition.</li></ul>|<ul><li>Le contenu sera en lecture seule pendant deux brèves périodes pendant la migration. Pendant ce temps, attendez-vous à une bannière « Vous ne pouvez pas modifier le contenu » dans SharePoint.</li><li>L’index de recherche ne sera pas conservé et peut prendre jusqu’à 10 jours pour être reconstruit.</li><li>Le contenu SharePoint Online et OneDrive Entreprise sera en lecture seule pendant deux brèves périodes pendant la migration. Les utilisateurs voient une bannière « Vous ne pouvez pas modifier le contenu » brièvement pendant cette période.</li><li>À la fin de la migration SharePoint Online, les résultats de recherche pour le contenu SharePoint Online et OneDrive Entreprise peuvent être indisponibles pendant la reconstruction de l’index. Pendant cette période, les requêtes de recherche peuvent ne pas renvoyer de résultats complets. Les fonctionnalités qui dépendent d’index de recherche, telles que SharePoint Online News, peuvent être affectées lorsque la réindexation est terminée.</li></ul>|
||||

Considérations supplémentaires :

- Si votre organisation utilise toujours des flux de travail SharePoint 2010, ils ne fonctionneront plus après le 31 décembre 2021. Les flux de travail SharePoint 2013 restent pris en charge, bien qu’ils restent désactivés par défaut pour les nouveaux locataires à compter du 1er novembre 2020. Une fois la migration vers le service SharePoint Online terminée, nous vous recommandons de passer à Power Automate ou à d’autres solutions pris en charge.

- Les clients Microsoft Cloud Deutschland dont l’instance SharePoint Online n’est pas encore migre doivent rester sur le module SharePoint Online PowerShell/Microsoft.SharePointOnline.CSOM version 16.0.20616.12000 ou une version inférieure. Dans le cas contraire, les connexions à SharePoint Online via PowerShell ou le modèle objet côté client échoueront.

- Les clients Microsoft Cloud Deutschland dont l’instance SharePoint Online est migre doivent mettre à jour le module SharePoint Online PowerShell/Microsoft.SharePointOnline.CSOM vers la version 16.0.20717.12000 ou supérieure. Dans le cas contraire, les connexions à SharePoint Online via PowerShell ou le modèle objet côté client échoueront.

## <a name="exchange-online-phase-5"></a>Exchange Online (phase 5)

**S’applique à :** Tous les clients utilisant Exchange Online

Si vous utilisez Exchange Online hybride : les administrateurs hybrides Exchange Online doivent exécuter l’Assistant Configuration hybride  **(HCW)** plusieurs fois dans le cadre de cette transition. Consultez les [étapes de migration avancée de prétravail pour Exchange](ms-cloud-germany-transition-add-experience.md#Exchange-Online-before-phase-5)

Comme décrit dans [](ms-cloud-germany-transition-add-pre-work.md#exchange-online)le prétravail de migration, avant le début de la **phase de migration 5,** les clients hybrides Exchange Online doivent exécuter la dernière version de l’Assistant Configuration hybride Exchange (HCW) en mode « Office 365 Germany » pour préparer la configuration sur site pour la migration vers les services globaux Office 365.

À la fin de la **phase de migration 5** (lorsque l’avis du Centre de messages est publié), vous devez exécuter à nouveau le HCW à l’aide des paramètres d’Office 365 dans le monde entier pour faire pointer vos systèmes locaux vers les services globaux Office 365. Des mises à jour DNS supplémentaires peuvent être nécessaires si vous utilisez des domaines personnalisés.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Les boîtes aux lettres Exchange Online sont déplacées de Microsoft Cloud Deutschland vers les services globaux Office 365.| La configuration d’Exchange Online ajoute la nouvelle région allemande locale à l’organisation en transition. La région des services globaux Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer les boîtes aux lettres vers la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (MCD ou services globaux) sont dans la même organisation et peuvent utiliser l’un ou l’autre point de terminaison d’URL. |<ul><li>Transition d’utilisateurs et de services à partir de vos URL MCD héritées (outlook.office.de) vers les nouvelles URL de services Office 365 ( `https://outlook.office365.com` ).</li><li>Les utilisateurs peuvent continuer à accéder au service via les URL MCD héritées pendant la migration, mais ils doivent arrêter d’utiliser les URL héritées à la fin de la migration.</li><li>Les utilisateurs doivent passer à l’utilisation du portail Office mondial pour les fonctionnalités Office Online (Calendrier, Courrier, Personnes). La navigation vers les services qui ne sont pas encore migrés vers les services Office 365 ne fonctionne pas tant qu’ils ne sont pas migrés. </li><li>Outlook Web App ne fournit pas l’expérience de dossier public pendant la migration. </li></ul>|
| Mettre à jour les paramètres DNS personnalisés pour la découverte automatique| Les paramètres DNS gérés par le client pour la découverte automatique qui pointent actuellement vers Microsoft Cloud Deutschland doivent être mis à jour pour faire référence au point de terminaison global Office 365 à la fin de la phase Exchange Online (phase 5). <br> Les entrées DNS existantes avec CNAME pointant vers autodiscover-outlook.office.de doivent être mises à jour pour pointer vers autodiscover.outlook.com. |  Les demandes de disponibilité et les appels de découverte de service via le point de découverte automatique pointent directement vers les services Office 365. Les clients qui n’effectuent pas ces mises à jour DNS peuvent être face à des problèmes de service de découverte automatique lors de la finalisation de la migration. |
||||

Considérations supplémentaires :
<!--
    The statement below is not clear. What does myaccount.microsoft.com mean?
-->

- `myaccount.microsoft.com` fonctionne uniquement après le passage à la phase 9 du client. Les liens produisent des messages d’erreur « Un problème s’est produit » jusqu’à ce moment-là.

- Les utilisateurs d’Outlook Web App qui accèdent à une boîte aux lettres partagée dans l’autre environnement (par exemple, un utilisateur de l’environnement MCD accède à une boîte aux lettres partagée dans l’environnement global) seront invités à s’authentifier une deuxième fois. L’utilisateur doit d’abord s’authentifier et accéder à sa boîte aux lettres dans, puis ouvrir la boîte aux lettres `outlook.office.de` partagée qui se trouve dans `outlook.office365.com` . Ils devront s’authentifier une deuxième fois lors de l’accès aux ressources partagées hébergées dans l’autre service.

- Pour les clients Microsoft Cloud Deutschland existants ou ceux en transition, lorsqu’une boîte aux lettres partagée est ajoutée à Outlook à l’aide de **l'>** Informations > Ajouter un compte, l’affichage des autorisations de calendrier peut échouer (le client Outlook tente d’utiliser l’API `https://outlook.office.de/api/v2.0/Me/Calendars` Rest).) Les clients qui souhaitent ajouter un compte pour afficher les autorisations de calendrier peuvent ajouter la clé de Registre comme décrit dans les modifications de l’expérience utilisateur pour le partage d’un calendrier dans [Outlook](https://support.microsoft.com/office/user-experience-changes-for-sharing-a-calendar-in-outlook-5978620a-fe6c-422a-93b2-8f80e488fdec) afin de garantir la réussite de cette action. Cette clé de Registre peut être déployée à l’échelle de l’organisation à l’aide de la stratégie de groupe.

- Pendant la phase de migration, l’utilisation des cmdlets **PowerShell New-migrationEndpoint,** **Set-MigrationEndpoint** et **Test-MigrationsServerAvailability** peut entraîner des erreurs (erreur sur le proxy). Cela se produit lorsque la boîte aux lettres d’arbitrage a migré vers le monde entier, mais pas la boîte aux lettres d’administration, et inversement. Pour résoudre ce problème, lors de la création de la session PowerShell du client, utilisez la boîte aux lettres d’arbitrage comme conseil de routage dans **connectionUri**. Par exemple :

```powershell
New-PSSession 
    -ConfigurationName Microsoft.Exchange 
    -ConnectionUri "https://outlook.office365.com/powershell-liveid?email=Migration.8f3e7716-2011-43e4-96b1-aba62d229136@TENANT.onmicrosoft.de"
    -Credential $UserCredential
    -Authentication Basic
    -AllowRedirection
```

Pour en savoir plus sur les différences entre les organisations lors de la migration et après la migration des ressources Exchange Online, examinez les informations relatives à l’expérience client pendant la migration vers les [services Office 365](ms-cloud-germany-transition-experience.md)dans les nouvelles régions de centres de données allemandes.

## <a name="exchange-online-protection--security-and-compliance-phase-6"></a>Exchange Online Protection/ Security and Compliance (Phase 6)

**S’applique à :** Tous les clients utilisant Exchange Online<br>

Les fonctionnalités d’Exchange Online Protection (EOP) principales sont copiées dans la nouvelle région « Allemagne ».

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Migration du routage Exchange Online et historique des détails des messages. | Exchange Online permet le routage des hôtes externes vers Office 365. Les enregistrements MX externes sont acheminés vers le service EOP. La configuration du client et les détails historiques sont migrés. |<ul><li>Les entrées DNS gérées par Microsoft sont mises à jour depuis Office 365 Germany EOP vers les services Office 365.</li><li>Les clients doivent attendre 30 jours après la double écriture EOP pour la migration EOP. Dans le cas contraire, il peut y avoir une perte de données.</li></ul>|
||||

## <a name="skype-for-business-online-phase-7"></a>Skype Entreprise Online (phase 7)

**S’applique à :** Tous les clients utilisant SharePoint Online

<!--
    Question from ckinder
    the PowerShell command seems to be incomplete
-->
| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Migration de Skype Entreprise vers Teams. | Les clients Skype Entreprise existants sont migrés vers les services globaux Office 365 en Europe, puis migrés vers Microsoft Teams dans la région « Allemagne » des services Office 365. |<ul><li>Les utilisateurs ne pourront pas se connecter à Skype Entreprise à la date de migration. Dix jours avant la migration, nous publierons dans le Centre d’administration pour vous faire savoir quand la migration aura lieu, et à nouveau lorsque nous commencerons la migration.</li><li> La configuration de la stratégie est miggrée. </li><li>Les utilisateurs seront migrés vers Teams et n’auront plus Skype Entreprise après la migration. </li><li>Le client de bureau Teams doit être installé sur les utilisateurs. L’installation aura lieu au cours des 10 jours via une stratégie sur l’infrastructure Skype Entreprise, mais en cas d’échec, les utilisateurs devront toujours télécharger le client ou se connecter à un navigateur pris en charge. </li><li>Les contacts et les réunions seront migrés vers Teams.</li><li>Les utilisateurs ne pourront pas se connecter à Skype Entreprise entre les transitions de service de temps vers les services Office 365, et pas tant que les entrées DNS client ne seront pas terminées. </li><li>Les contacts et les réunions existantes continueront de fonctionner en tant que réunions Skype Entreprise. </li><li>PowerShell vous permet d’administrer les paramètres et les stratégies de votre client et de vos utilisateurs. Lorsque vous vous connectez à une session PowerShell, ajoutez les valeurs suivantes : <br><br> `-OverridePowershellUri "https://admin4E.online.lync.com/OcsPowershellOAuth"`</li></ul>|
||||

## <a name="dynamics-365-phase-8"></a>Dynamics 365 (phase 8)

**S’applique à :** Tous les clients utilisant Microsoft Dynamics 365

Les clients avec Dynamics 365 ont besoin d’un engagement supplémentaire pour migrer les organisations Dynamics de l’organisation indépendamment.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Ressources Microsoft Dynamics | Les clients avec Microsoft Dynamics seront engagés par Microsoft Engineering ou Microsoft FastTrack pour la transition de Microsoft Dynamics 365 vers l’instance des services globaux Office 365.* |<ul><li>Après la migration, l’administrateur valide l’organisation. <</li><li>L’administrateur modifie les flux de travail, si nécessaire. </li><li>L’administrateur désessonne le mode AdminOnly selon le cas.</li><li>L’administrateur modifie le type d’organisation à partir _du bac_ à sable , selon le cas</li><li>Informer les utilisateurs finaux de la nouvelle URL pour accéder à l’instance (org).</li><li>Mettez à jour les connexions entrantes vers la nouvelle URL de point de terminaison. </li><li>Le service Dynamics n’est pas disponible pour les utilisateurs pendant la transition. </li><li>Les utilisateurs doivent valider l’état et les fonctionnalités de l’organisation après la migration de chaque organisation.</li></ul>|
|||||

\* (i) Les clients avec Microsoft Dynamics 365 doivent prendre des mesures dans ce scénario de migration, comme défini par le processus de migration fourni. (ii) Si le client ne parvient pas à prendre des mesures, Microsoft ne pourra pas terminer la migration. (iii) Lorsque Microsoft ne parvient pas à terminer la migration en raison de l’inaction du client, l’abonnement du client expirera le 29 octobre 2021.

## <a name="power-bi-phase-8-of-9"></a>Power BI (phase 8 sur 9)

**S’applique à :** Tous les clients utilisant Microsoft Power BI (PBI)

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Migration des ressources Power BI | Les clients avec Microsoft Power BI (PBI) seront engagés par Microsoft Engineering ou Microsoft FastTrack après avoir déclenché manuellement un outil de migration PBI existant pour migrer Power BI vers l’instance des services globaux Office 365.\*\* |<ul><li>Les éléments Power BI suivants _ne_ seront pas transitionn et devront être re-créés : <</li><li>Jeux de données en temps réel (par exemple, jeux de données de diffusion en continu ou push). </li><li>Configuration et source de données de la passerelle de données power BI sur site. </li><li>Les rapports créés en plus des jeux de données en temps réel ne seront pas disponibles après la migration et doivent être recréés. </li><li>Les services Power BI ne seront pas disponibles pour les utilisateurs pendant la transition. L’indisponibilité du service ne doit pas être plus de 24 heures.</li><li>Les utilisateurs doivent reconfigurer les sources de données et leurs passerelles de données locales avec le service Power BI après la migration.  Tant qu’ils ne le feront pas, les utilisateurs ne pourront pas utiliser ces sources de données pour effectuer une actualisation programmée et/ou des requêtes directes sur ces sources de données. </li><li>Les capacités et les espaces de travail premium ne peuvent pas être migrés. Les clients doivent supprimer toutes les capacités avant la migration et les re-créer après la migration. Déplacez les espaces de travail vers les capacités comme vous le souhaitez.</li></ul>  |
||||

\*\* (i) Les clients avec Microsoft Power BI doivent prendre des mesures dans ce scénario de migration, comme défini par le processus de migration fourni. (ii) Si le client ne parvient pas à prendre des mesures, Microsoft ne pourra pas terminer la migration. (iii) Lorsque Microsoft ne parvient pas à terminer la migration en raison de l’inaction du client, l’abonnement du client expirera le 29 octobre 2021.

## <a name="office-apps"></a>Applications Office

**S’applique à :** Tous les clients utilisant des applications de bureau Office (Word, Excel, PowerPoint, Outlook, ...)

Les clients Office 365 qui migrent vers la région « Allemagne » exigent que tous les utilisateurs se ferment, se connectent à Office 365 et se connectent à toutes les applications de bureau Office (Word, Excel, PowerPoint, Outlook, etc.) et au client OneDrive Entreprise une fois que la migration du client a atteint la phase 9. La dédauthentification permet aux services Office d’obtenir de nouveaux jetons d’authentification à partir du service Azure AD global.

| Étapes | Description | Impact |
|:-------|:-------|:-------|
| Clients, Office Online pendant le cutover client Office, Azure AD finalise l’étendue du client pour pointer vers les services Office 365. | Cette modification de configuration permet aux clients Office de mettre à jour et de pointer vers les points de terminaison des services Office 365. | <ul><li>Avertissez les utilisateurs de fermer toutes les applications _Office,_ puis connectez-vous (ou forcez les clients à redémarrer et les utilisateurs à se connecter) pour permettre aux clients Office de récupérer la modification. </li><li>Informez les utilisateurs  et le personnel du service d’aide que les utilisateurs peuvent voir une bannière Office qui les invite à réactiver les applications Office dans les 72 heures qui s’ernt après le passage à la ligne. </li><li>Toutes les applications Office sur des ordinateurs personnels doivent être fermées, et les utilisateurs doivent se fermer, puis se connectent à nouveau. Dans la barre d’activation jaune, connectez-vous pour vous réactiver aux services Office 365.</li><li>Les ordinateurs partagés nécessitent des actions similaires à des ordinateurs personnels et ne nécessitent pas de procédure spéciale. </li><li>Sur les appareils mobiles, les utilisateurs doivent se fermer des applications, les fermer, puis se connecter à nouveau. </li></ul>|
||||

## <a name="office-services"></a>Office Services

Le dernier service utilisé dans Office est un passage du MCD aux services globaux Office 365, et non une migration. Seuls les liens de LRU du côté des services globaux Office 365 seront visibles après la migration à partir du portail Office.com client. Les liens de MRU provenant du MCD ne sont pas visibles en tant que liens MRU dans les services globaux Office 365. Dans les services globaux Office 365, les liaisons de gestion des données sont accessibles uniquement une fois que la migration du client a atteint la phase 9.

## <a name="next-step"></a>Étape suivante

[Effectuer des travaux préalables supplémentaires](ms-cloud-germany-transition-add-pre-work.md)

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client pendant la migration](ms-cloud-germany-transition-experience.md)

Transition :

- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
