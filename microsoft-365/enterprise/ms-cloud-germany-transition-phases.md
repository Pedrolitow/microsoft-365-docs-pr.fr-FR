---
title: Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (général)
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/15/2020
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
ms.openlocfilehash: f0c81813522be1f9d759980df98995f1adb261c5
ms.sourcegitcommit: 7ecd10b302b3b3dfa4ba3be3a6986dd3c189fbff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "49921621"
---
# <a name="migration-phases-actions-and-impacts-for-the-migration-from-microsoft-cloud-deutschland-general"></a>Actions et impacts des phases de migration pour la migration à partir de Microsoft Cloud Deutschland (général)

Les migrations de clients de Microsoft Cloud Deutschland vers la région Allemagne des services Office 365 de Microsoft sont exécutées sous la forme d’un ensemble de phases et leurs actions configurées pour chaque charge de travail. Cette figure montre les neuf phases de migration vers les nouveaux centres de données allemands.

![Les neuf phases de migration vers les nouveaux centres de données allemands](../media/ms-cloud-germany-migration-opt-in/migration-organization.png)

Les phases et leurs actions garantissent que les données et expériences critiques sont migrées vers les services Office 365. Une fois que votre client est ajouté à la file d’attente de migration, chaque charge de travail est exécutée en tant qu’ensemble d’étapes exécutées sur le service backend. Certaines charges de travail peuvent nécessiter des actions de l’administrateur (ou de l’utilisateur) ou la migration peut affecter l’utilisation des phases exécutées et abordées dans Comment la [migration est-elle organisée ?](ms-cloud-germany-transition.md#how-is-the-migration-organized)

Les sections suivantes contiennent des actions et des effets pour les charges de travail au fil des différentes phases de la migration. Examinez les tableaux et déterminez les actions ou effets applicables à votre organisation. Assurez-vous que vous êtes prêt à exécuter les étapes des phases respectives selon les besoins. L’échec des étapes nécessaires peut entraîner une panne du service et retarder l’achèvement de la migration vers les services Office 365.

## <a name="exchange-online"></a>Exchange Online

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Une nouvelle région d’Allemagne est ajoutée à la configuration de l’organisation existante et les boîtes aux lettres sont déplacées vers les services Office 365. | La configuration d’Exchange Online ajoute la nouvelle région allemande locale à l’organisation en transition. Cette région de services Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer les boîtes aux lettres vers la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (services d’Allemagne ou d’Office 365) sont dans la même organisation et peuvent utiliser l’un ou l’autre point de terminaison d’URL. | Exchange Online | - Transition des utilisateurs et des services depuis les URL d’Allemagne vers les URL de services Office 365 ( `https://outlook.office365.com` ). <br><br> - Les utilisateurs continueront d’accéder au service via les URL héritées d’Allemagne pendant la migration. Aucune action immédiate n’est nécessaire. <br><br> - Les utilisateurs doivent commencer à utiliser le portail office.com pour les fonctionnalités Office Online (Calendrier, Courrier, Personnes). La navigation vers les services qui ne sont pas encore migrés vers les services Office 365 ne fonctionne pas tant que la migration n’est pas terminée. <br><br> - Outlook Web App ne fournira pas l’expérience de dossier public pendant la migration. |
|||||

Considérations supplémentaires :

- `myaccount.msft.com` fonctionne uniquement après le passage d’Office 365. Les liens produisent des messages d’erreur « Un problème s’est produit » jusqu’à ce moment-là.

- Les utilisateurs d’Outlook Web App qui accèdent à une boîte aux lettres partagée dans l’autre environnement (par exemple, un utilisateur de l’environnement allemand accède à une boîte aux lettres partagée dans l’environnement global) seront invités à s’authentifier une deuxième fois. L’utilisateur doit d’abord s’authentifier et accéder à sa boîte aux lettres dans, puis ouvrir la boîte aux lettres `outlook.office.de` partagée qui se trouve dans `outlook.office365.com` . Ils devront s’authentifier une deuxième fois lors de l’accès aux ressources partagées hébergées dans l’autre service.

- Pour les clients Microsoft Cloud Deutschland existants ou ceux en transition, lorsqu’une boîte aux lettres partagée est ajoutée à Outlook à l’aide de File **> Info > Add Account**, l’affichage des autorisations de calendrier peut échouer (le client Outlook tente d’utiliser l’API `https://outlook.office.de/api/v2.0/Me/Calendars` Rest).) Les clients qui souhaitent ajouter un compte pour afficher les autorisations de calendrier peuvent ajouter la clé de Registre comme décrit dans les modifications de l’expérience utilisateur pour le partage d’un calendrier dans [Outlook](https://support.microsoft.com/office/user-experience-changes-for-sharing-a-calendar-in-outlook-5978620a-fe6c-422a-93b2-8f80e488fdec) afin de garantir la réussite de cette action. Cette clé de Registre peut être déployée à l’échelle de l’organisation à l’aide de la stratégie de groupe.

- Pendant la phase de migration, l’utilisation des cmdlets PowerShell **New-migrationEndpoint,** **Set-MigrationEndpoint** et **Test-MigrationsServerAvailability** peut entraîner des erreurs (erreur sur le proxy). Cela se produit lorsque la boîte aux lettres d’arbitrage a migré vers le monde entier, mais pas la boîte aux lettres d’administration, et inversement. Pour résoudre ce problème, lors de la création de la session PowerShell du client, utilisez la boîte aux lettres d’arbitrage comme conseil de routage dans **connectionUri**. Par exemple : `New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid?email=Migration.8f3e7716-2011-43e4-96b1-aba62d229136@TENANT.onmicrosoft.de" -Credential $UserCredential -Authentication Basic -AllowRedirection`

- Si vous utilisez Exchange Online hybride :

    - Vous devez réexécuter l’Assistant Configuration hybride (HCW) pour mettre à jour la configuration sur site par rapport à Microsoft Cloud Deutschland avant la transition, puis réexécuter le HCW lors du nettoyage sur les services Office 365. Des mises à jour DNS supplémentaires peuvent être nécessaires si vous utilisez des domaines personnalisés.

Pour en savoir plus sur les différences entre les organisations lors de la migration et après la migration des ressources Exchange Online, examinez les informations relatives à l’expérience client pendant la migration vers les [services Office 365](ms-cloud-germany-transition-experience.md)dans les nouvelles régions de centres de données allemandes.

## <a name="exchange-online-protection"></a>Exchange Online Protection

Les fonctionnalités d’Exchange Online Protection (EOP) principales sont copiées dans une nouvelle région d’Allemagne. 

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration du routage Exchange Online et historique des détails des messages. | Exchange Online permet le routage d’hôtes externes vers Office 365. Les enregistrements MX externes sont acheminés vers le service EOP. La configuration du client et les détails historiques sont migrés. | Clients Exchange Online | - Les entrées DNS gérées par Microsoft sont mises à jour depuis Office 365 Germany EOP vers les services Office 365. <br><br> - Les clients doivent attendre 30 jours après la double écriture EOP pour la migration EOP. Dans le cas contraire, il peut y avoir une perte de données. |
|||||

## <a name="sharepoint-online"></a>SharePoint Online

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| SharePoint et OneDrive sont en transition. | SharePoint et OneDrive sont migrés de Microsoft Cloud Deutschland vers les services Office 365 au cours de cette phase. Les URL Microsoft Cloud Deutschland existantes sont conservées (par exemple, `contoso.sharepoint.de` ). Les jetons émis par les services Microsoft Cloud Deutschland ou Office 365 sont valides pendant la transition. | Clients SharePoint | - Le contenu sera en lecture seule pendant deux brèves périodes pendant la migration. Pendant ce temps, attendez-vous à une bannière « Vous ne pouvez pas modifier le contenu » dans SharePoint. <br><br> - L’index de recherche ne sera pas conservé et peut prendre jusqu’à 10 jours pour être reconstruit. <br><br> - Le contenu SharePoint/OneDrive sera en lecture seule pendant deux brèves périodes pendant la migration. Les utilisateurs voient une bannière « Vous ne pouvez pas modifier le contenu » brièvement pendant cette période. <br><br> - L’index de recherche peut être indisponible pendant la reconstruction de l’index. Pendant cette période, les requêtes de recherche peuvent ne pas renvoyer de résultats complets. <br><br> - Les sites existants sont conservés. |
|||||

Considérations supplémentaires :

- Une fois la migration de SharePoint Online vers la région allemande terminée, les index de données sont recréés. Les fonctionnalités qui dépendent des index de recherche peuvent être affectées lorsque la réindexation est terminée.

- Si votre organisation utilise toujours des flux de travail SharePoint 2010, ils ne fonctionneront plus après le 31 décembre 2021. Les flux de travail SharePoint 2013 restent pris en charge, bien qu’ils restent désactivés par défaut pour les nouveaux locataires à compter du 1er novembre 2020. Une fois la migration vers le service SharePoint Online terminée, nous vous recommandons de passer à Power Automate ou à d’autres solutions pris en charge.

- À la fin de la migration de OneDrive vers la région allemande, les index de données sont reconstruits. Les fonctionnalités qui dépendent d’index de recherche peuvent être affectées lors de la réindexation en cours.

- Les clients Microsoft Cloud Deutschland dont l’instance SharePoint Online n’a pas encore migré doivent rester sur le module SharePoint Online PowerShell/Microsoft.SharePointOnline.CSOM version 16.0.20616.12000 ou une version inférieure. Dans le cas contraire, les connexions à SharePoint Online via PowerShell ou le modèle objet côté client échoueront.

- Les clients Microsoft Cloud Deutschland dont l’instance SharePoint Online est migre doivent mettre à jour le module SharePoint Online PowerShell/Microsoft.SharePointOnline.CSOM vers la version 16.0.20717.12000 ou supérieure. Dans le cas contraire, les connexions à SharePoint Online via PowerShell ou le modèle objet côté client échoueront.


## <a name="skype-for-business-online"></a>Skype Entreprise Online

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration de Skype Entreprise vers Teams. | Les clients Skype Entreprise existants sont migrés vers les services Office 365 en Europe, puis migrés vers Microsoft Teams dans la région Allemagne des services Office 365. | Clients Skype Entreprise | - Les utilisateurs ne pourront pas se connecter à Skype Entreprise à la date de migration. Dix jours avant la migration, nous publierons un billet dans le Centre d’administration pour vous faire savoir quand la migration aura lieu, et à nouveau lorsque nous commencerons la migration. <br><br> - La configuration de la stratégie est migrée. <br><br> - Les utilisateurs seront migrés vers Teams et n’auront plus Skype Entreprise après la migration. <br><br> - Le client de bureau Teams doit être installé pour les utilisateurs. L’installation aura lieu au cours des 10 jours via une stratégie sur l’infrastructure Skype Entreprise, mais en cas d’échec, les utilisateurs devront toujours télécharger le client ou se connecter à un navigateur pris en charge. <br><br> - Les contacts et les réunions seront migrés vers Teams. <br><br> - Les utilisateurs ne pourront pas se connecter à Skype Entreprise entre les transitions de service de temps vers les services Office 365, et pas tant que les entrées DNS client ne seront pas terminées. <br><br> - Les contacts et les réunions existantes continueront de fonctionner en tant que réunions Skype Entreprise. |
|||||

## <a name="office-services"></a>Office Services

Le dernier service utilisé dans Office est un passage du service Germany aux services Office 365, et non une migration. Seuls les liens de LRU du côté des services Office 365 seront visibles après la migration à partir du Office.com web. Les liens de MRU du service Germany ne sont pas visibles en tant que liens MRU dans les services Office 365. Dans Office 365, les liens de liste de contrôle d’accès sont accessibles uniquement une fois la migration du client terminée.

## <a name="subscription"></a>Abonnement

| Étapes | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Nous ne pouvons pas migrer des clients sans le consentement. | Microsoft obtient le droit de migrer de deux manières, ce qui permet à Microsoft d’orchestrer la transition des données et des services vers l’instance des services Office 365. <br> L’administrateur choisit la migration pilotée par Microsoft. <br> Les clients renouvellent tous les abonnements dans leur client Microsoft Cloud Deutschland après le 1er mai 2020. Nous informerons ces clients du droit de migration chaque mois, attendrons 30 jours pour donner aux clients la possibilité d’annuler, puis d’y opter directement, suivis dans ICM. | Tous les clients Office | - Le client est marqué comme étant accepté pour la migration et le Centre d’administration affiche la confirmation. <br><br> - L’accusé de réception est publié sur le client du centre de messages Cloud Germany. La configuration du service continue à partir des points de terminaison Microsoft Cloud Deutschland. <br><br> - Surveillez le Centre de messages pour les mises à jour sur l’état de la phase de migration. |
| Les abonnements sont transférés et les licences sont réassignées. | Une fois le client transféré vers les services Office 365, les abonnements aux services Office 365 correspondants sont achetés pour les abonnements Microsoft Cloud Deutschland transférés. Les utilisateurs ayant des licences Microsoft Cloud Deutschland se voit attribuer des licences de services Office 365. Les abonnements Microsoft Cloud Deutschland hérités sont supprimés du client de services Office 365 à la fin de l’exécution. | Tous les clients Office | - Les modifications apportées aux abonnements existants seront bloquées (par exemple, aucun nouvel achat d’abonnement ou changement de nombre de sièges) au cours de cette phase. <br><br> - Les modifications d’attribution de licence seront bloquées. <br><br> - L’abonnement Microsoft Cloud Deutschland sera migré vers l’abonnement aux services Office 365 correspondant. L’offre de services Office 365 de cet abonnement est définie par Microsoft (également appelée _mappage des offres)._ <br><br> - Le nombre de fonctionnalités (plans de service) proposées par les services Office 365 peut être supérieur à celui de l’offre Microsoft Cloud Deutschland d’origine. Les licences utilisateur dans les services Office 365 seront affectées de manière équivalente à des fonctionnalités Microsoft Cloud Deutschland similaires (plans de service). Les licences utilisateur de tous les utilisateurs sont automatiquement attribuées aux nouvelles fonctionnalités. L’administrateur doit prendre une action explicite pour désactiver ces licences, si nécessaire. <br><br> - Lorsque la migration des abonnements est terminée, les services Office 365 et les abonnements Germany sont visibles dans le portail d’administration Office 365, avec l’état des abonnements En Allemagne comme supprimé. <br><br> - Les utilisateurs seront réassignés avec des licences liées aux nouveaux abonnements aux services Office 365. Tous les processus clients qui ont des dépendances sur les abonnements ou les GUID de référence (SKU) en Allemagne sont rompus et doivent être révisés avec l’offre de services Office 365. <br><br> - Les nouveaux abonnements dans les services Office 365 seront achetés avec la nouvelle période (mensuelle/trimestrielle/année), et le client recevra un remboursement au pro total pour le solde inutilisé de l’abonnement Microsoft Cloud Deutschland. <br><br> - Les clients Microsoft Cloud Deutschland partenaires ne seront pas migrés. Les clients CSP seront migrés vers les services Office 365 sous le nouveau client de services Office 365 du même partenaire. Après la migration du client, le partenaire peut gérer ce client uniquement à partir du client des services Office 365. <br><br> - Des fonctionnalités supplémentaires sont disponibles (par exemple, Microsoft Planner et Microsoft Flow), sauf si elles sont désactivées par l’administrateur client. Pour plus d’informations sur la désactivation des plans de service affectés aux licences des utilisateurs, voir Désactiver l’accès aux [services Microsoft 365](disable-access-to-services-while-assigning-user-licenses.md)tout en attribuant des licences utilisateur.  |
|||||

## <a name="next-step"></a>Étape suivante

[Effectuer des travaux préalables supplémentaires](ms-cloud-germany-transition-add-pre-work.md)

## <a name="more-information"></a>Informations supplémentaires

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
