---
title: Actions et impacts sur les phases de migration
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
description: 'Résumé : Découvrez les actions et les impacts des phases de migration de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de connaissances allemande.'
ms.openlocfilehash: 9ffdb0bbe60bdb96d6e110ac08cba4030272c7e9
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49551656"
---
# <a name="migration-phases-actions-and-impacts"></a>Actions et impacts sur les phases de migration

Les migrations client de Microsoft Cloud Deutschland vers la région de l’Allemagne des services Office 365 de Microsoft sont exécutées comme un ensemble d’actions configurées pour chaque charge de travail. Ces actions permettent de s’assurer que les données et expériences critiques sont migrées vers les services Office 365. Une fois que votre client est ajouté à la file d’attente de migration, chaque charge de travail est effectuée comme un ensemble d’étapes exécutées sur le service principal. Certaines charges de travail peuvent nécessiter des actions de l’administrateur (ou utilisateur), ou la migration peut affecter l’utilisation pour les phases qui sont exécutées et décrites dans [Comment la migration est-elle organisée ?](ms-cloud-germany-transition.md#how-is-the-migration-organized)

Les sections suivantes contiennent les actions et les effets des charges de travail au fur et à mesure des différentes phases de la migration. Passez en revue les tableaux et déterminez les actions ou les effets qui s’appliquent à votre organisation. Assurez-vous que vous êtes prêt à exécuter les étapes dans les phases correspondantes, le cas échéant. L’échec de l’exécution des étapes nécessaires peut entraîner une panne de service et retarder la migration vers les services Office 365.

## <a name="exchange-online"></a>Exchange Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| La nouvelle région Germany est ajoutée à la configuration existante de l’organisation, et les boîtes aux lettres sont déplacées vers les services Office 365. | La configuration d’Exchange Online ajoute la nouvelle région locale allemande à l’organisation de transition. Cette région des services Office 365 est définie par défaut, ce qui permet au service d’équilibrage de charge interne de redistribuer des boîtes aux lettres à la région par défaut appropriée dans les services Office 365. Dans cette transition, les utilisateurs des deux côtés (Allemagne ou services Office 365) se trouvent dans la même organisation et peuvent utiliser le point de terminaison de l’URL. | Exchange Online | -Faire migrer les utilisateurs et les services des URL d’Allemagne vers les URL des services Office 365 ( `https://outlook.office365.com` ). <br><br> -Les utilisateurs continueront à accéder au service via les URL d’Allemagne héritées lors de la migration. Aucune action immédiate n’est nécessaire. <br><br> -Les utilisateurs doivent commencer à utiliser le portail office.com pour les fonctionnalités d’Office Online (calendrier, courrier, personnes). La navigation vers les services qui ne sont pas encore migrés vers les services Office 365 ne fonctionne pas tant qu’elles n’ont pas été migrées. <br><br> -Outlook Web App ne fournit pas d’expérience de dossier public pendant la migration. |
|||||

Pour en savoir plus sur les différences entre les organisations en cours de migration et une fois la migration des ressources Exchange Online, consultez les informations contenues dans l' [expérience client lors de la migration vers les services Office 365 dans les nouvelles régions de centre de données allemand](ms-cloud-germany-transition-experience.md).

## <a name="exchange-online-protection"></a>Exchange Online Protection

Les fonctionnalités Exchange Online Protection (EOP) principales sont copiées dans la nouvelle région Germany. 

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration du routage Exchange Online et du détail des messages historiques. | Exchange Online permet le routage à partir d’hôtes externes vers Office 365. Les enregistrements MX externes sont transférés vers le service EOP. Les détails de la configuration du client et de l’historique sont migrés. | Clients Exchange Online | -Les entrées DNS gérées par Microsoft sont mises à jour à partir d’Office 365 Germany EOP vers les services Office 365. <br><br> -Les clients doivent attendre 30 jours après la migration de EOP Dual Write pour EOP. Sinon, il peut y avoir une perte de données. |
|||||

## <a name="sharepoint-online"></a>SharePoint Online

<!--

| Step(s) | Description | Applies to | Impact |
|:-------|:-----|:-------|:-------|
| SharePoint and OneDrive are transitioned. | SharePoint and OneDrive are migrated from Microsoft Cloud Deutschland to Office 365 services in this phase. Existing Microsoft Cloud Deutschland URLs are preserved (for example, `contoso.sharepoint.de`). Tokens that were issued by Microsoft Cloud Deutschland or Office 365 services are valid during the transition. | SharePoint customers | - Content will be read-only for two brief periods (less than x minutes) during migration. During this time, expect a "you can't edit content" banner in SharePoint. <br><br> - The search index won't be preserved, and may take up to 10 days to be rebuilt. <br><br> - SharePoint/OneDrive content will be read-only for two brief periods (less than x minutes) during migration. Users will see a "you can't edit content" banner briefly during this time. <br><br> - The search index may be unavailable while the index is rebuilt. During this period, search queries might not return complete results. <br><br> - Existing sites are preserved. |
|||||

--> 

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| SharePoint et OneDrive sont en transition. | SharePoint et OneDrive sont migrés de Microsoft Cloud Deutschland vers les services Office 365 dans cette phase. Les URL de Microsoft Cloud Deutschland existantes sont préservées (par exemple, `contoso.sharepoint.de` ). Les jetons émis par les services Microsoft Cloud Deutschland ou Office 365 sont valides pendant la transition. | Clients SharePoint | -Le contenu sera en lecture seule pendant deux courtes périodes lors de la migration. Pendant ce temps, attendez une bannière « vous ne pouvez pas modifier le contenu » dans SharePoint. <br><br> -L’index de recherche ne sera pas conservé et la reconstruction peut prendre jusqu’à 10 jours. <br><br> -Le contenu SharePoint/OneDrive sera en lecture seule pendant deux courtes périodes lors de la migration. Les utilisateurs verront brièvement une bannière « vous ne pouvez pas modifier le contenu » pendant ce temps. <br><br> -L’index de recherche est peut-être indisponible pendant la reconstruction de l’index. Pendant cette période, il se peut que les requêtes de recherche ne renvoient pas les résultats complets. <br><br> -Les sites existants sont conservés. |
|||||


## <a name="skype-for-business-online"></a>Skype Entreprise Online

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Migration de Skype entreprise vers Teams. | Les clients Skype entreprise existants sont migrés vers les services Office 365 en Europe, puis transférés vers Microsoft teams dans la région d’Allemagne des services Office 365. | Clients Skype entreprise | -Les utilisateurs ne peuvent pas se connecter à Skype entreprise à la date de la migration. 10 jours avant la migration, nous allons informer les utilisateurs finaux via intrabande sur le client Skype entreprise qu’ils seront mis à niveau vers Teams. Nous publierons également dans le centre d’administration que ces modifications auront lieu après 10 jours. <br><br> -La configuration de la stratégie est migrée. <br><br> -Les utilisateurs sont migrés vers teams et ne disposent plus de Skype entreprise après la migration. <br><br> -Le client de bureau teams doit être installé sur les utilisateurs. L’installation aura lieu au cours des 10 jours suivant la stratégie sur l’infrastructure Skype entreprise, mais si cette opération échoue, les utilisateurs devront toujours télécharger le client ou se connecter avec un navigateur pris en charge. <br><br> -Les contacts et les réunions sont migrés vers Teams. <br><br> -Les utilisateurs ne peuvent pas se connecter à Skype entreprise entre les transitions de service de temps et les services Office 365, et non jusqu’à ce que les entrées DNS du client soient terminées. <br><br> -Les contacts et les réunions existantes continueront de fonctionner en tant que réunions Skype entreprise. |
|||||
        
## <a name="subscription"></a>Abonnement

| Étape (s) | Description | S’applique à | Impact |
|:-------|:-----|:-------|:-------|
| Nous ne pouvons pas migrer les clients sans consentement. | Microsoft gagne le droit de procéder à une migration de deux manières, ce qui permet à Microsoft d’orchestrer la transition des données et des services à l’instance Office 365 services. <br> L’administrateur opte pour la migration basée sur Microsoft. <br> Les clients renouvellent les abonnements dans leur client Deutschland Cloud Microsoft après le 1er mai 2020. Nous informerons ces clients de la migration par mois, patientent 30 jours pour permettre aux clients d’annuler, puis d’accepter directement les suivis dans ICM. | Tous les clients Office | -Le client est marqué comme étant accepté pour la migration, et le centre d’administration affiche la confirmation. <br><br> -L’accusé de réception est publié sur le client du centre de messages de Cloud Germany. La configuration du service se poursuit à partir des points de terminaison Deutschland Cloud de Microsoft. <br><br> -Surveillez le centre de messages pour les mises à jour de l’état des phases de migration. |
| Les abonnements sont transférés et les licences sont réaffectées. | Une fois le client transféré vers les services Office 365, les abonnements aux services Office 365 correspondants sont achetés pour les abonnements Microsoft Cloud Deutschland transférés. Les utilisateurs disposant de licences Microsoft Cloud Deutschland seront affectées aux licences des services Office 365. Les abonnements Microsoft Cloud Deutschland hérités sont supprimés du client des services Office 365 à la fin de l’opération. | Tous les clients Office | -Les modifications apportées aux abonnements existants sont bloquées (par exemple, aucune nouvelle inscription d’abonnement ou modification du nombre de sièges) pendant cette phase. <br><br> -Les modifications apportées aux attributions de licence sont bloquées. <br><br> -L’abonnement Microsoft Cloud Deutschland est migré vers l’abonnement aux services Office 365 correspondant. L’offre Office 365 services de cet abonnement est définie par Microsoft (également appelée _mappage des offres_). <br><br> -Le nombre de fonctionnalités (plans de service) offerts par les services Office 365 peut être plus important que dans l’offre Microsoft Cloud Deutschland d’origine. Les licences utilisateur dans les services Office 365 seront équivalentes aux fonctionnalités similaires de Microsoft Cloud Deutschland (plans de service). Les licences utilisateur de tous les utilisateurs seront automatiquement attribuées aux nouvelles fonctionnalités. Le cas échéant, l’administrateur doit prendre une mesure explicite pour désactiver ces licences. <br><br> -Lorsque la migration des abonnements est terminée, les abonnements Office 365 services et Germany seront visibles dans le portail d’administration d’Office 365, dont l’état des abonnements en Allemagne est _annulé._ <br><br> -Les utilisateurs se verront affecter des licences qui sont liées aux nouveaux abonnements aux services Office 365. Tous les processus client qui ont des dépendances sur les abonnements Germany ou les GUID SKU sont rompus et doivent être modifiés avec l’offre Office 365 services. <br><br> -Les nouveaux abonnements dans les services Office 365 seront achetés avec le nouveau terme (mensuel/trimestriel/annuel), et le client recevra un remboursement progressif pour le solde non utilisé de l’abonnement Microsoft Cloud Deutschland. <br><br> -Les locataires Microsoft Cloud Deutschland ne seront pas migrés. Les clients CSP seront migrés vers les services Office 365 sous le nouveau client des services Office 365 du même partenaire. Après la migration du client, le partenaire peut gérer ce client uniquement à partir du client des services Office 365. <br><br> -Une fonctionnalité supplémentaire est disponible (par exemple, le planificateur Microsoft et Microsoft Flow), sauf si elle est désactivée par l’administrateur client. Pour plus d’informations sur la désactivation des plans de service attribués aux licences des utilisateurs, consultez la rubrique [désactiver l’accès aux services Microsoft 365 lors de l’affectation de licences utilisateur](disable-access-to-services-while-assigning-user-licenses.md).  |
|||||

## <a name="next-step"></a>Étape suivante

[Effectuer des tâches supplémentaires préalables](ms-cloud-germany-transition-add-pre-work.md)

## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)