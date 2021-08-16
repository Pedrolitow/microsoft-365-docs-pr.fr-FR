---
title: Feuille de route pour la fin de la prise en charge d'Exchange 2010
ms.author: dstrome
author: dstrome
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 a atteint la fin de la prise en charge. Utilisez cette feuille de route de planification pour préparer la mise à niveau vers Exchange Online ou une version plus récente de Exchange Server en local.
ms.openlocfilehash: dc7a9355be8232daefb158ca143fac377949480e714de77a644b5f8b1bdc3c6a
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53904950"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge d'Exchange 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2010 a atteint sa fin de prise en charge le **13 octobre 2020.** Si vous n’avez pas encore commencé la migration de Exchange 2010 vers Microsoft 365, Office 365 ou Exchange 2016, il est temps de commencer la planification.

## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

La plupart des produits Microsoft ont un cycle de vie de support au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Étant donné Exchange 2010 a atteint sa fin de support le 13 octobre 2020, Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.
- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.
- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.
- Mises à jour de fuseau horaire.

Votre installation de Exchange 2010 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées ci-dessus, nous vous recommandons vivement de migrer de Exchange 2010 dès que possible.

Pour plus d’informations sur l’approche de la fin de la prise en charge, voir Ressources pour vous aider à mettre à niveau des serveurs et [des clients Office 2010.](upgrade-from-office-2010-servers-and-products.md)

## <a name="what-are-my-options"></a>Quelles sont mes options ?

C’est le moment idéal pour explorer vos options et préparer un plan de migration. Vous pouvez :

- Migrez entièrement vers Microsoft 365. Migrer des boîtes aux lettres à l’aide d’une migration hybride à cutover, hybride minimale ou complète. Supprimez ensuite les serveurs Exchange locaux et Active Directory.
- Migrez Exchange serveurs 2010 vers Exchange 2016 sur vos serveurs locaux.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de conserver DirSync ou Azure AD Connecter en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Microsoft Exchange local. Si vous supprimez tous les serveurs Exchange, vous ne pourrez pas apporter de modifications aux destinataires Exchange dans Exchange Online car la source d’autorité reste dans votre annuaire Active Directory local. Des modifications doivent y être apportées. Dans ce scénario, vous avez les options suivantes :
>
>- *Recommandé :* Si vous avez migré vos boîtes aux lettres vers Microsoft 365 et mis à niveau vos serveurs d’ici le 13 octobre 2020, utilisez Exchange 2010 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres. Ensuite, migrez Exchange 2010 vers Exchange 2016 et désaffectez les serveurs Exchange 2010 restants.
>- Si vous n’avez pas terminé la migration de boîtes aux lettres et la mise à niveau du serveur local d’ici le 13 octobre 2020, vous devez d’abord mettre à niveau vos serveurs Exchange 2010 locaux vers Exchange 2016. Utilisez ensuite Exchange 2016 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres.

> [!NOTE]
> Cela est un peu plus compliqué, mais vous pouvez également migrer des boîtes aux lettres vers Microsoft 365 lors de la migration de vos serveurs Exchange 2010 locaux vers Exchange 2016.

Voici les trois chemins que vous pouvez prendre pour éviter la fin de la prise en charge Exchange Server 2010.

![Exchange Server de mise à niveau vers 2010](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Les sections suivantes explorent chaque option plus en détail.

## <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration de votre courrier vers Microsoft 365 est l’option la plus simple et la plus simple pour vous aider à retirer votre déploiement Exchange 2010. Avec une migration vers Microsoft 365, vous pouvez effectuer un saut unique entre l’ancienne technologie et les fonctionnalités actuelles, notamment :

- Fonctionnalités de conformité telles que les stratégies de rétention, In-Place conservation pour litige, eDiscovery sur place, etc.
- Microsoft Teams.
- Power BI.
- Boîte de réception Focused.
- MyAnalytics.

Microsoft 365 également de nouvelles fonctionnalités et expériences, afin que votre organisation puisse commencer à les utiliser immédiatement. En outre, vous n’avez pas à vous soucier des :

- Achat et maintenance du matériel.
- Payer à la température et à la température de vos serveurs.
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire.
- Maintenance du stockage et des logiciels pour prendre en charge les exigences de conformité.
- Mise à niveau vers une nouvelle version de Exchange. Vous êtes toujours sur la dernière version de Exchange dans Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment migrer vers Microsoft 365 ?

Selon votre organisation, plusieurs options s’offrent à vous pour Microsoft 365. Tout d’abord, vous devez prendre en compte quelques éléments, tels que :

- Nombre de sièges ou de boîtes aux lettres à déplacer.
- Durée de la migration.
- Si vous avez besoin d’une intégration transparente entre votre installation locale et Microsoft 365 lors de la migration.

Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser.

<br>

****

|Option de migration|Taille de l’organisation|Durée|
|---|---|---|
|Migration à basculement|Moins de 150 sièges|Une semaine ou moins|
|Migration hybride minimale|Moins de 150 sièges|Quelques semaines ou moins|
|Migration complète hybride|Plus de 150 sièges|Quelques semaines ou plus|
|

Les sections suivantes donnent une vue d’ensemble de ces méthodes. Pour plus d’informations, [voir Décider d’un chemin de migration.](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27)

### <a name="cutover-migration"></a>Migration à basculement

Dans une migration à cutover, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, etc., vers Office 365 à une date et une heure définies. Lorsque vous avez terminé, vous fermez vos serveurs Exchange locaux et commencez à utiliser Microsoft 365 exclusivement.

La migration à cutover est très efficace pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent Microsoft 365 rapidement et qui ne veulent pas gérer la complexité des autres méthodes. Toutefois, il doit être terminé dans une semaine ou moins. En plus, les utilisateurs doivent reconfigurer leurs profils Outlook utilisateurs. La migration à cutover peut migrer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons de l’utiliser pour un maximum de 150 boîtes aux lettres. Si vous essayez de migrer davantage, vous risquez de ne plus pouvoir transférer toutes les boîtes aux lettres avant l’échéance, et votre personnel de support technique risque d’être submergé par les demandes d’aide aux utilisateurs pour reconfigurer les Outlook.

Voici les éléments à prendre en compte concernant la migration àover :

- Microsoft 365 vous connecter à vos serveurs Exchange 2010 à l’aide de Outlook Anywhere sur le port TCP 443.
- Toutes les boîtes aux lettres sur site sont déplacées vers Microsoft 365.
- Vous aurez besoin d’un compte d’administrateur local qui dispose d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
- Les Exchange 2010 acceptés que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
- Entre le début de la migration et la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et en local. Cela vous permet d’effectuer la migration sans vous soucier du fait que le courrier électronique soit laissé dans vos boîtes aux lettres sur site.
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour Microsoft 365 compte. Ils devront les modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs doivent configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-Outlook que vous téléchargerez peut varier. Pour plus d’informations, [voir Travail hors connexion dans Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Pour en savoir plus sur la migration à cutover, voir :

- [Ce que vous devez savoir sur une migration de messagerie à cutover](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Effectuer une migration à cutover du courrier électronique vers Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimale

Dans une migration hybride ou express minimale, vous déplacez quelques centaines de boîtes aux lettres vers Microsoft 365 en quelques semaines. Cette méthode ne prend pas en charge les fonctionnalités avancées de migration hybride telles que les informations de calendrier de libre/occupé partagées.

La migration hybride minimale est très efficace pour les organisations qui ont besoin de plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365, mais qui prévoient de terminer la migration dans un délai de quelques semaines. Vous bénéficiez de certains avantages de la *migration hybride* complète plus avancée sans grande complexité. Vous pouvez contrôler le nombre et les boîtes aux lettres à migrer à un moment donné. Microsoft 365 boîtes aux lettres seront créées avec les noms d’utilisateur et les mots de passe des comptes locaux. Et, contrairement aux migrations à bas Outlook, vos utilisateurs n’ont pas à recréer leur profil.

Voici les éléments à prendre en considération concernant la migration hybride minimale :

- Vous devrez synchroniser l’annuaire à une seule fois entre vos serveurs Active Directory locaux et les serveurs Microsoft 365.
- Les utilisateurs pourront se Microsoft 365 à leur boîte aux lettres avec les mêmes nom d’utilisateur et mot de passe qu’avant leur boîte aux lettres.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’auront pas besoin de configurer un nouveau profil Outlook la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leur courrier électronique.

Pour plus d’informations, voir [Utiliser l’hybride](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate)minimal pour migrer rapidement Exchange boîtes aux lettres vers Office 365 .

### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, vous avez plusieurs centaines, jusqu’à des dizaines de milliers, de boîtes aux lettres et vous déplacez une partie ou la totalité vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides rendent possible :

- Affichez les informations de calendrier des utilisateurs locaux pour les utilisateurs dans Microsoft 365, et vice versa.
- Consultez une liste d’adresses globale unifiée qui contient des destinataires à la fois en local et Microsoft 365.
- Afficher les propriétés Outlook destinataire complètes pour tous les utilisateurs, qu’ils soient locaux ou Microsoft 365.
- Sécuriser la communication par courrier électronique entre les serveurs Exchange locaux et les Office 365 à l’aide de TLS et de certificats.
- Traitez les messages envoyés entre des serveurs Exchange locaux et Microsoft 365 comme internes, ce qui leur permet de :
  - Être correctement évaluées et traitées par les agents de transport et de conformité ciblant les messages internes.
  - Contourner les filtres anti-courrier indésirable.

Les migrations hybrides complètes sont les meilleures pour les organisations qui s’attendent à rester dans une configuration hybride pendant plusieurs mois ou plus. Vous obtenez les fonctionnalités répertoriées plus tôt dans cette section, ainsi que la synchronisation d’annuaires, de meilleures fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide de déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation sur site.

Éléments à prendre en compte concernant la migration hybride complète :

- Elles ne sont pas adaptées à toutes les organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas d’avantages qui justifient l’effort et le coût impliqués. Dans de tels cas, nous vous recommandons plutôt d’envisager une migration hybride à cutover ou une migration hybride minimale.
- Vous devez configurer la synchronisation d’annuaires à l’aide de Azure Active Directory (Azure AD) Connecter entre vos serveurs Active Directory locaux et Microsoft 365.
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite azure ad Connecter avec synchronisation de mot de passe et/ou services de fédération Active Directory).
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leur courrier électronique.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de conserver DirSync ou Azure AD Connecter en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Exchange local. Si tous Exchange serveurs sont supprimés, vous ne pourrez pas modifier les destinataires Exchange dans Exchange Online. Cela est dû au fait que la source d’autorité reste dans votre annuaire Active Directory local et que des modifications doivent être apportées à cet annuaire.

Si une migration hybride complète vous semble appropriées, consultez les ressources utiles suivantes :

- [Exchange Assistant de déploiement](/exchange/exchange-deployment-assistant)
- [Déploiements hybrides Exchange Server](/exchange/exchange-hybrid)
- [Assistant de configuration hybride](/exchange/hybrid-configuration-wizard)
- [FAQ de l’assistant Configuration hybride](/exchange/hybrid-configuration-wizard-faqs)
- [Configuration requise pour un déploiement hybride](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Mise à niveau vers une version plus récente Exchange Server sur site

Nous pensons vivement que vous obtenez la meilleure valeur et la meilleure expérience utilisateur en migrer entièrement vers Microsoft 365. Toutefois, nous comprenons que certaines organisations doivent conserver Exchange serveurs locaux. Cela peut être dû à des exigences réglementaires, pour garantir que les données ne sont pas stockées dans un centre de données étranger, parce que vous avez des paramètres ou des exigences uniques qui ne peuvent pas être satisfaits dans le cloud, ou parce que vous avez besoin de Exchange pour gérer les boîtes aux lettres cloud, car vous utilisez toujours Active Directory en local. Dans tous les cas, si vous conservez Exchange en local, vous devez vous assurer que votre environnement Exchange 2010 est mis à niveau vers au moins Exchange 2013 ou Exchange 2016.

Pour une expérience améliorée, nous vous recommandons de mettre à niveau votre environnement local restant vers Exchange 2016. Vous n’avez pas besoin d’installer Exchange Server 2013 si vous souhaitez passer directement de Exchange Server 2010 à Exchange Server 2016.

Exchange 2016 inclut toutes les fonctionnalités des versions précédentes de Exchange. Il correspond le mieux à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités soient disponibles uniquement dans Microsoft 365. Découvrez quelques-uns des éléments manquants :

<br>

****

|Exchange version|Fonctionnalités|
|---|---|
|**Exchange 2013**|L’architecture simplifiée réduit le nombre de rôles serveur à trois (boîte aux lettres, accès au client, transport Edge)|
||Stratégies de protection contre la perte de données (DLP) qui empêchent la fuite d’informations sensibles|
||Amélioration de Outlook Web App|
|**Exchange 2016**|*Fonctionnalités de Exchange 2013 et ...*|
||Autres rôles serveur simplifiés pour les boîtes aux lettres et le transport Edge|
||Amélioration de la DLP avec l’intégration avec SharePoint|
||Résilience de base de données améliorée|
||Collaboration sur des documents en ligne|
|

<br>

****

|Considération|Informations supplémentaires|
|---|---|
|Dates de fin du support|Comme Exchange 2010, chaque version de Exchange a sa propre date de fin de prise en charge : <p> Exchange 2013 - Avril 2023 <p> Exchange 2016 - Octobre 2025 <p> Plus la date de fin de support est antérieure, plus vite vous devrez effectuer une autre migration. Avril 2023 est beaucoup plus proche que vous ne le pensez !|
|Migration vers Exchange 2013 ou 2016|Le chemin de migration de Exchange 2010 vers une version plus récente est le même, que vous choisissiez Exchange 2013 ou Exchange 2016 : <p> Installez Exchange 2013 ou 2016 dans votre organisation Exchange 2010 existante. <p> Déplacez les services et autres infrastructures vers Exchange 2013 ou 2016. <p> Déplacez les boîtes aux lettres et les dossiers publics vers Exchange 2013 ou 2016 Désaffecter les serveurs restants Exchange 2010.|
|Coexistence de version|Lors de la migration vers Exchange 2013 ou Exchange 2016, vous pouvez installer chaque version dans une organisation Exchange 2010 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2013 ou 2016 Exchange 2016 et d’y faire votre migration.|
|Matériel serveur|La configuration matérielle requise pour le serveur Exchange 2010. Assurez-vous que votre matériel est compatible. En savoir plus sur la configuration matérielle requise pour chaque version ici : <p> [Configuration requise pour Exchange 2016](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <p> [Configuration requise pour Exchange 2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <p> Avec les améliorations significatives des performances de Exchange et l’augmentation de la puissance informatique et de la capacité de stockage sur les serveurs plus nouveaux, vous aurez probablement besoin de moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.|
|Version du système d'exploitation|Les versions minimales de système d’exploitation pris en charge pour chaque version sont les : <p> Exchange 2016 - Windows Server 2012 <p> Exchange 2013 - Windows Server 2008 R2 SP1 <p> Pour plus d’informations sur la prise en charge du système [d’exploitation, voir Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Niveau fonctionnel de la forêt Active Directory|Les niveaux fonctionnels minimaux de forêt Active Directory pris en charge pour chaque version sont : <p> Exchange 2016 - Windows Server 2008 R2 SP1 <p> Exchange 2013 - Windows Server 2003 <p> Pour plus d’informations sur la prise en charge du niveau fonctionnel de la [forêt, voir Exchange Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix).|
|Office versions clientes|Les versions minimales Office client pour chaque version sont les Office les plus récentes : <p> Exchange 2016 - Office 2010 (avec les dernières mises à jour) <p> Exchange 2013 - Office 2007 SP3 <p> Pour plus d’informations sur Office prise en charge du client, [voir Exchange Matrice de prise en charge.](/exchange/plan-and-deploy/supportability-matrix)|
|

Utilisez les ressources suivantes pour faciliter votre migration :

- [Exchange Assistant de déploiement](/exchange/exchange-deployment-assistant)
- Modifications apportées au schéma Active Directory pour Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)
- System requirements for Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- Conditions préalables Exchange [2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client Office 2010 et les serveurs et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![End of support for Office 2010 clients and servers and Windows 7 poster](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche d’une page illustre les différents chemins d’accès que vous pouvez prendre pour répondre aux produits client et serveur Office 2010 et Windows 7 jusqu’à la fin de la prise en charge, avec les chemins d’accès préférés et la prise en charge des options dans Microsoft 365 Entreprise mis en évidence.

Vous pouvez également [télécharger cette](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="what-if-i-need-help"></a>Que se passe-t-il si j’ai besoin d’aide ?

Si vous migrez vers Microsoft 365, vous pouvez utiliser notre service Microsoft FastTrack. FastTrack fournit les meilleures pratiques, outils et ressources pour rendre votre migration vers Microsoft 365 aussi transparente que possible. Mieux encore, vous aurez un ingénieur du support technique pour vous aider à passer de la planification et de la conception à la migration de votre dernière boîte aux lettres. Pour plus d’informations sur FastTrack, voir [Microsoft FastTrack.](https://fasttrack.microsoft.com/)

Si vous avez des problèmes lors de votre migration vers Microsoft 365 et que vous n’utilisez pas FastTrack ou que vous migrez vers une version plus récente de Exchange Server, voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>Articles connexes

[Ressources facilitant la mise à jour de vos clients et serveurs Office 2010](upgrade-from-office-2010-servers-and-products.md)
