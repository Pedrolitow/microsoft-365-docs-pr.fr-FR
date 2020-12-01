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
description: Exchange 2010 a atteint la fin de la prise en charge. Utilisez cette feuille de route de planification pour préparer la mise à niveau vers Exchange Online ou une version plus récente d’Exchange Server en local.
ms.openlocfilehash: 23384d93c4e65fb25a66ca6f2f0bcbe46b34ee18
ms.sourcegitcommit: d3ca8021f7da00a474ac14aac5f1358204a848f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "49519690"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge d'Exchange 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2010 a atteint sa fin de prise en charge le **13 octobre 2020**. Si vous n’avez pas encore commencé la migration d’Exchange 2010 vers Microsoft 365, Office 365 ou Exchange 2016, il est temps de commencer la planification.

## <a name="what-does-end-of-support-mean"></a>Qu’est-ce que la *fin de la prise en charge* ?

La plupart des produits Microsoft ont un cycle de vie de la prise en charge au cours duquel ils obtiennent de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans après la publication initiale du produit. La fin de ce cycle de vie est appelée fin de la prise en charge du produit. Étant donné qu’Exchange 2010 a atteint sa fin de prise en charge le 13 octobre 2020, Microsoft ne fournit plus :

- Support technique pour les problèmes susceptibles de se produire.
- Correctifs de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et l’utilisation du serveur.
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
- Mises à jour de fuseau horaire.

Votre installation d’Exchange 2010 continuera de s’exécuter après cette date. Toutefois, en raison des modifications indiquées ci-dessus, nous vous recommandons vivement de procéder à une migration à partir d’Exchange 2010 dès que possible.

Pour plus d’informations sur la fin de la prise en charge, reportez-vous [à ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Quelles sont les options ?

Il est très utile d’explorer vos options et de préparer un plan de migration. Vous pouvez :

- Migrer entièrement vers Microsoft 365. Migration de boîtes aux lettres à l’aide du basculement, d’un environnement hybride minimal ou d’une migration hybride complète. Ensuite, supprimez les serveurs Exchange locaux et Active Directory.
- Migrez vos serveurs Exchange 2010 vers Exchange 2016 sur vos serveurs locaux.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365, mais que vous prévoyez de maintenir DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Microsoft Exchange local. Si vous supprimez tous les serveurs Exchange, vous ne pourrez pas modifier les destinataires Exchange dans Exchange Online car la source d’autorité reste dans votre environnement Active Directory local. Les modifications doivent être apportées à cet emplacement. Dans ce scénario, vous disposez des options suivantes :
>
>- *Recommandé :* Si vous avez migré vos boîtes aux lettres vers Microsoft 365 et mis à niveau vos serveurs le 13 octobre 2020, utilisez Exchange 2010 pour vous connecter à Microsoft 365 et migrer les boîtes aux lettres. Ensuite, migrez Exchange 2010 vers Exchange 2016 et désactivez tous les autres serveurs Exchange 2010.
>- Si vous n’avez pas terminé la migration de la boîte aux lettres et la mise à niveau du serveur local du 13 octobre 2020, mettez d’abord à niveau vos serveurs Exchange 2010 sur site vers Exchange 2016. Ensuite, utilisez Exchange 2016 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres.

> [!NOTE]
> Il est peu plus compliqué, mais vous pouvez également migrer des boîtes aux lettres vers Microsoft 365 lors de la migration de vos serveurs Exchange 2010 locaux vers Exchange 2016.

Voici les trois chemins que vous pouvez suivre pour éviter la fin de la prise en charge d’Exchange Server 2010.

![Chemins de mise à niveau vers Exchange Server 2010](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Les sections suivantes explorent chaque option plus en détail.

## <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration de votre courrier électronique vers Microsoft 365 est l’option la plus simple et la plus simple pour vous aider à supprimer votre déploiement Exchange 2010. Avec une migration vers Microsoft 365, vous pouvez passer un seul tronçon de l’ancienne technologie aux fonctionnalités actuelles, notamment :

- Les fonctionnalités de conformité telles que les stratégies de rétention, les In-Place et la mise en attente pour litige, la découverte électronique inaltérable et bien plus encore.
- Microsoft Teams.
- Power BI.
- Boîte de réception prioritaire.
- MyAnalytics.

Microsoft 365 fournit également de nouvelles fonctionnalités et de nouvelles expériences, de sorte que votre organisation puisse commencer à les utiliser immédiatement. En outre, vous n’avez pas à vous soucier des éléments suivants :

- L’achat et la maintenance du matériel ;
- Le paiement de la chaleur et le refroidissement de vos serveurs.
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire.
- Maintenance du stockage et des logiciels pour prendre en charge les exigences de conformité.
- Mise à niveau vers une nouvelle version d’Exchange. Vous êtes toujours sur la dernière version d’Exchange dans Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment dois-je migrer vers Microsoft 365 ?

En fonction de votre organisation, vous disposez de plusieurs options pour accéder à Microsoft 365. Tout d’abord, vous devez prendre en compte quelques éléments, tels que :
- Nombre de places ou de boîtes aux lettres à déplacer.
- La durée de la migration.
- Si vous avez besoin d’une intégration transparente entre votre installation locale et Microsoft 365 lors de la migration.
 
Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser.

|Option de migration|Taille de l’Organisation|Durée|
|---|---|---|
|Migration à basculement|Moins de 150 sièges|Une semaine ou moins|
|Migration hybride minimale|Moins de 150 sièges|Quelques semaines ou moins|
|Migration complète hybride|Plus de 150 sièges|Quelques semaines ou plus|

Les sections suivantes vous donnent une vue d’ensemble de ces méthodes. Pour plus d’informations, reportez-vous [à la rubrique choisir un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migration à basculement

Lors d’une migration à basculement, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, etc. vers Office 365 à une date et une heure définies. Une fois que vous avez fini, arrêtez vos serveurs Exchange locaux et commencez à utiliser exclusivement Microsoft 365.

La migration à basculement est idéale pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent accéder à Microsoft 365 rapidement et ne veulent pas gérer la complexité des autres méthodes. Toutefois, elle doit être achevée dans une semaine ou moins. De plus, les utilisateurs doivent reconfigurer leurs profils Outlook. La migration à basculement peut migrer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons de l’utiliser pour un maximum de 150. Si vous essayez d’effectuer une migration plus longue, vous pouvez exécuter le transfert de toutes les boîtes aux lettres avant la date d’échéance et votre personnel du support informatique peut être submergé de demandes pour aider les utilisateurs à reconfigurer Outlook.

Voici quelques éléments à prendre en compte lors de la migration à basculement :

- Microsoft 365 doit se connecter à vos serveurs Exchange 2010 à l’aide d’Outlook Anywhere via le port TCP 443.
- Toutes les boîtes aux lettres locales seront déplacées vers Microsoft 365.
- Vous avez besoin d’un compte d’administrateur local qui dispose d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
- Les domaines Exchange 2010 acceptés que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
- Entre le démarrage de la migration et le début de la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et locales. Cela vous permet d’effectuer la migration sans vous inquiéter de laisser le courrier électronique en arrière-plan dans vos boîtes aux lettres locales.
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Microsoft 365. Ils devront les modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois.
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez.
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier. La quantité de courriers électroniques qu’Outlook télécharge peut varier. Pour plus d’informations, consultez la rubrique [travailler hors connexion dans Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Pour en savoir plus sur la migration à basculement, voir :

- [Ce que vous devez savoir sur une migration de courrier à basculement](https://docs.microsoft.com/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Effectuer une migration à basculement de la messagerie vers Office 365](https://docs.microsoft.com/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimale

Dans une migration minimale hybride ou rapide, vous déplacez quelques centaines de boîtes aux lettres vers Microsoft 365 en quelques semaines. Cette méthode ne prend pas en charge les fonctionnalités de migration hybride avancées comme les informations de calendrier de disponibilité partagées.

Une migration hybride minimale est idéale pour les organisations qui ont besoin de plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365, tout en préservant la migration en quelques semaines. Vous bénéficiez de quelques-uns des avantages de la *migration hybride complète* plus avancée sans plus de complexité. Vous pouvez contrôler le nombre et les boîtes aux lettres à migrer à un moment donné. Les boîtes aux lettres Microsoft 365 seront créées avec les noms d’utilisateur et mots de passe des comptes locaux. Contrairement aux migrations à basculement, vos utilisateurs n’ont pas besoin de recréer leurs profils Outlook.

Voici quelques éléments à prendre en compte concernant la migration hybride minimale :

- Vous devez effectuer une synchronisation d’annuaires unique entre vos serveurs Active Directory locaux et Microsoft 365.
- Les utilisateurs peuvent se connecter à leur boîte aux lettres Microsoft 365 avec les mêmes nom d’utilisateur et mot de passe qu’avant leur boîte aux lettres.
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez.
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, bien que certains anciens téléphones Android aient besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de télécharger de leur courrier électronique.

Pour plus d’informations, consultez la rubrique [use minimal Hybrid hybride pour migrer rapidement des boîtes aux lettres Exchange vers Office 365](https://docs.microsoft.com/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, vous avez plusieurs centaines, jusqu’à dizaines de milliers, de boîtes aux lettres, et vous déplacez une partie ou la totalité vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides permettent d’effectuer les opérations suivantes :

- Afficher les informations de disponibilité des utilisateurs sur site pour les utilisateurs dans Microsoft 365, et inversement.
- Consultez une liste d’adresses globale unifiée qui contient des destinataires à la fois sur site et Microsoft 365.
- Affichez toutes les propriétés de destinataire Outlook pour tous les utilisateurs, qu’ils soient locaux ou dans Microsoft 365.
- Sécurisation des communications de messagerie entre les serveurs Exchange locaux et Office 365 à l’aide du protocole TLS et des certificats.
- Traiter les messages envoyés entre les serveurs Exchange locaux et Microsoft 365 comme internes, ce qui leur permet de :
  - Être correctement évalué et traité par les agents de transport et de conformité ciblant les messages internes.
  - Contourner les filtres anti-courrier indésirable.

Les migrations hybrides complètes sont idéales pour les organisations qui s’attendent à rester dans une configuration hybride pendant de nombreux mois ou plus. Vous obtenez les fonctionnalités répertoriées plus haut dans cette section, ainsi que la synchronisation d’annuaires, les fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide des déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation locale.

Éléments à prendre en compte concernant la migration totale hybride :

- Ils ne sont pas adaptés à toutes les organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas les avantages qui justifient les efforts et les coûts impliqués. Dans ce cas, nous vous recommandons de prendre en compte le basculement ou la migration hybride minimale.
- Vous devez configurer la synchronisation d’annuaires à l’aide d’Azure Active Directory (Azure AD) se connecter entre vos serveurs Active Directory locaux et Microsoft 365.
- Les utilisateurs peuvent se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite Azure AD Connect avec synchronisation de mot de passe et/ou Active Directory Federation Services).
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres d’utilisateur que vous migrez.
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, bien que certains anciens téléphones Android aient besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de télécharger de leur courrier électronique.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365, mais que vous prévoyez de maintenir DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateurs à partir d’Active Directory local, vous devez conserver au moins un serveur Exchange local. Si tous les serveurs Exchange sont supprimés, vous ne pourrez pas modifier les destinataires Exchange dans Exchange Online. En effet, la source d’autorité reste dans votre annuaire Active Directory local et des modifications doivent y être apportées.

Si une migration hybride complète vous paraît directement, consultez les ressources utiles suivantes :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- [Déploiements hybrides Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid)
- [Assistant de configuration hybride](https://docs.microsoft.com/exchange/hybrid-configuration-wizard)
- [FAQ de l’assistant Configuration hybride](https://docs.microsoft.com/exchange/hybrid-configuration-wizard-faqs)
- [Configuration requise pour un déploiement hybride](https://docs.microsoft.com/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Effectuer une mise à niveau vers une version plus récente d’Exchange Server en local

Nous pensons fortement que vous bénéficiez de la meilleure valeur et de l’expérience utilisateur en effectuant une migration complète vers Microsoft 365. Toutefois, nous comprenons que certaines organisations doivent conserver certains serveurs Exchange en local. Cela peut être dû à des exigences réglementaires, afin de garantir que les données ne sont pas stockées dans un centre de données étranger, car vous avez des paramètres ou des exigences uniques qui ne peuvent pas être satisfaits dans le Cloud, ou parce que vous avez besoin d’Exchange pour gérer les boîtes aux lettres de Cloud car vous utilisez toujours Active Directory en local. Dans tous les cas, si vous conservez Exchange local, vous devez vous assurer que votre environnement Exchange 2010 est mis à niveau vers au moins Exchange 2013 ou Exchange 2016.

Pour une expérience optimale, nous vous recommandons de mettre à niveau votre environnement local restant vers Exchange 2016. Vous n’avez pas besoin d’installer Exchange Server 2013 si vous voulez effectuer directement à partir d’Exchange Server 2010 vers Exchange Server 2016.

Exchange 2016 inclut toutes les fonctionnalités des versions précédentes d’Exchange. Il correspond le mieux à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités ne soient disponibles que dans Microsoft 365. Voici quelques-unes des choses que vous avez manquantes :

|Version d’Exchange|Fonctionnalités|
|---|---|
|**Exchange 2013**|Une architecture simplifiée réduit le nombre de rôles serveur à trois (boîte aux lettres, accès au client, transport Edge).|
||Stratégies de protection contre la perte de données (DLP) pour éviter la fuite d’informations sensibles|
||Amélioration de l’expérience Outlook Web App|
|**Exchange 2016**|*Fonctionnalités d’Exchange 2013 et...*|
||Autres rôles serveur simplifiés pour le transport de boîtes aux lettres et de transport Edge uniquement|
||Amélioration de DLP et intégration avec SharePoint|
||Résilience de base de données améliorée|
||Collaboration sur des documents en ligne|

|Considération|Informations supplémentaires|
|---|---|
|Fin des dates de prise en charge|À l’instar d’Exchange 2010, chaque version d’Exchange a sa propre date de fin de prise en charge :<br/><br/>Exchange 2013-2023 avril<br/>Exchange 2016-octobre 2025<br/><br/>Avant la date de fin de prise en charge, plus tôt vous devrez effectuer une autre migration. Le 2023 avril est beaucoup plus proche que vous ne le pensez !|
|Chemin de migration vers Exchange 2013 ou 2016|Le chemin de migration d’Exchange 2010 vers une version plus récente est le même que vous choisissiez Exchange 2013 ou Exchange 2016 :<br/><br/>Installez Exchange 2013 ou 2016 dans votre organisation existante d’Exchange 2010.<br/>Déplacez des services et d’autres infrastructures vers Exchange 2013 ou 2016.<br/>Déplacez les boîtes aux lettres et les dossiers publics vers Exchange 2013 ou 2016 désactivez les autres serveurs Exchange 2010.|
|Coexistence de la version|Lors de la migration vers Exchange 2013 ou Exchange 2016, vous pouvez installer l’une ou l’autre de ces versions dans une organisation Exchange 2010 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2013 ou Exchange 2016 et de procéder à la migration.|
|Matériel serveur|La configuration matérielle requise pour le serveur a changé par rapport à Exchange 2010. Assurez-vous que votre matériel est compatible. Pour en savoir plus sur la configuration matérielle requise pour chaque version, procédez comme suit :<br/><br/>[Configuration requise pour Exchange 2016](https://docs.microsoft.com/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016)<br/>[Configuration requise pour Exchange 2013](https://docs.microsoft.com/Exchange/exchange-2013-system-requirements-exchange-2013-help)<br/><br/>Avec les améliorations significatives des performances d’Exchange et l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus récents, vous aurez probablement besoin de serveurs moins nombreux pour prendre en charge le même nombre de boîtes aux lettres.|
|Version du système d'exploitation|Les versions minimales de système d’exploitation prises en charge pour chaque version sont les suivantes :<br/><br/>Exchange 2016-Windows Server 2012<br/>Exchange 2013-Windows Server 2008 R2 SP1<br/><br/>Vous trouverez plus d’informations sur la prise en charge du système d’exploitation dans la [matrice de prise en charge d’Exchange](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix).|
|Niveau fonctionnel de la forêt Active Directory|Les niveaux fonctionnels de forêt Active Directory minimum pris en charge pour chaque version sont les suivants :<br/><br/>Exchange 2016-Windows Server 2008 R2 SP1<br/>Exchange 2013-Windows Server 2003<br/><br/>Pour plus d’informations sur la prise en charge du niveau fonctionnel de la forêt, consultez la rubrique [Exchange Supporting Matrix](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix).|
|Versions du client Office|Les versions de client Office minimales prises en charge pour chaque version sont les suivantes :<br/><br/>Exchange 2016-Office 2010 (avec les dernières mises à jour)<br/>Exchange 2013-Office 2007 SP3<br/><br/>Pour plus d’informations sur la prise en charge des clients Office, consultez la rubrique [Exchange Supporting Matrix](https://docs.microsoft.com/exchange/plan-and-deploy/supportability-matrix).||| 


Utilisez les ressources suivantes pour vous aider dans votre migration :

- [Assistant de déploiement Exchange](https://aka.ms/exdeploy)
- Modifications apportées au schéma Active Directory pour Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016), [2013](https://docs.microsoft.com/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)
- Configuration système requise pour Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/system-requirements?view=exchserver-2016), [2013](https://docs.microsoft.com/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- Conditions préalables pour Exchange [2016](https://docs.microsoft.com/exchange/plan-and-deploy/prerequisites?view=exchserver-2016), [2013](https://docs.microsoft.com/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Résumé des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin de la prise en charge des clients et serveurs Office 2010 et de l’affiche Windows 7](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche sur une page illustre les différents chemins que vous pouvez suivre pour répondre aux produits client et serveur Office 2010 et Windows 7 arrive à la fin de la prise en charge, avec les chemins d’accès et les options de prise en charge par défaut dans Microsoft 365 entreprise en surbrillance.

Vous pouvez également [Télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format Letter, Legal ou tabloïd (11 x 17).

## <a name="what-if-i-need-help"></a>Qu’en est-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Microsoft 365, vous pouvez être autorisé à utiliser notre service FastTrack Microsoft. FastTrack fournit des meilleures pratiques, des outils et des ressources pour faciliter la migration vers Microsoft 365. De plus, vous disposerez d’un ingénieur du support technique, de la planification et de la migration de votre dernière boîte aux lettres. Pour plus d’informations sur FastTrack, consultez la rubrique [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes lors de la migration vers Microsoft 365 et que vous n’utilisez pas FastTrack, ou si vous effectuez une migration vers une version plus récente d’Exchange Server, voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>Articles connexes

[Ressources facilitant la mise à jour de vos clients et serveurs Office 2010](upgrade-from-office-2010-servers-and-products.md)
