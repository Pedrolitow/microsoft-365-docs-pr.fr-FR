---
title: Feuille de route pour la fin de la prise en charge d'Exchange 2010
ms.author: dstrome
author: dstrome
manager: scotv
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2010 a atteint la fin du support. Utilisez cette feuille de route de planification pour préparer la mise à niveau vers Exchange Online ou une version plus récente de Exchange Server localement.
ms.openlocfilehash: 02472f5d1ed1a4008e43bd89d227753465dcc409
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68171232"
---
# <a name="exchange-2010-end-of-support-roadmap"></a>Feuille de route pour la fin de la prise en charge d'Exchange 2010

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2010 a atteint sa fin de soutien le **13 octobre 2020**. Si vous n’avez pas encore commencé votre migration d’Exchange 2010 vers Microsoft 365, Office 365 ou Exchange 2016, il est temps de commencer à planifier.

## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

La plupart des produits Microsoft ont un cycle de vie de support pendant lequel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues, correctifs de sécurité, et ainsi de suite. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Étant donné qu’Exchange 2010 a atteint sa fin de support le 13 octobre 2020, Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.
- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
- Mises à jour de fuseau horaire.

Votre installation d’Exchange 2010 continuera d'être exécutée après cette date. Toutefois, en raison des modifications répertoriées ci-dessus, nous vous recommandons vivement de migrer à partir d’Exchange 2010 dès que possible.

Pour plus d’informations sur la fin du support, consultez [Ressources pour vous aider à effectuer une mise à niveau à partir de serveurs et clients Office 2010](upgrade-from-office-2010-servers-and-products.md).

## <a name="what-are-my-options"></a>Quelles sont mes options ?

C’est le moment idéal pour explorer vos options et préparer un plan de migration. Vous pouvez :

- Migrer entièrement vers Microsoft 365. Migrer des boîtes aux lettres à l’aide du basculement, d’une migration hybride minimale ou complète. Supprimez ensuite les serveurs Exchange locaux et Active Directory.
- Migrez vos serveurs Exchange 2010 vers Exchange 2016 sur vos serveurs locaux.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de conserver DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateur à partir de Active Directory local, vous devez conserver au moins un serveur Microsoft Exchange en local. Si vous supprimez tous les serveurs Exchange, vous ne pourrez pas apporter de modifications aux destinataires Exchange dans Exchange Online, car la source d’autorité reste dans votre Active Directory local. Des modifications doivent être apportées. Dans ce scénario, vous disposez des options suivantes :
>
> - *Recommandé:* Si vous avez migré vos boîtes aux lettres vers Microsoft 365 et mis à niveau vos serveurs avant le 13 octobre 2020, utilisez Exchange 2010 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres. Ensuite, migrez Exchange 2010 vers Exchange 2016 et désactivez les serveurs Exchange 2010 restants.
> - Si vous n’avez pas terminé la migration de boîte aux lettres et la mise à niveau du serveur local avant le 13 octobre 2020, mettez d’abord à niveau vos serveurs Exchange 2010 locaux vers Exchange 2016. Utilisez ensuite Exchange 2016 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres.

> [!NOTE]
> C’est un peu plus compliqué, mais vous pouvez également migrer des boîtes aux lettres vers Microsoft 365 lors de la migration de vos serveurs Exchange 2010 locaux vers Exchange 2016.

Voici les trois chemins que vous pouvez suivre pour éviter la fin du support pour Exchange Server 2010.

![Exchange Server chemins de mise à niveau 2010.](../media/exchange-2010-end-of-support/exchange-2010-end-of-support-options.png)

Les sections suivantes explorent chaque option plus en détail.

## <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration de votre courrier électronique vers Microsoft 365 est la meilleure et la plus simple option pour vous aider à mettre hors service votre déploiement Exchange 2010. Avec une migration vers Microsoft 365, vous pouvez effectuer un tronçon unique de l’ancienne technologie vers les fonctionnalités actuelles, notamment :

- Fonctionnalités de conformité telles que les stratégies de rétention, les In-Place et la conservation des litiges, la découverte électronique sur place, etc.
- Microsoft Teams.
- Power BI.
- Boîte de réception prioritaire.
- MyAnalytics.

Microsoft 365 obtient également de nouvelles fonctionnalités et expériences en premier, afin que votre organisation puisse commencer à les utiliser immédiatement. En outre, vous n’aurez pas à vous soucier de :

- Achat et maintenance du matériel.
- Payer pour chauffer et refroidir vos serveurs.
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire.
- Gestion du stockage et des logiciels pour prendre en charge les exigences de conformité.
- Mise à niveau vers une nouvelle version d’Exchange. Vous êtes toujours sur la dernière version d’Exchange dans Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment migrer vers Microsoft 365 ?

Selon votre organisation, vous avez quelques options pour accéder à Microsoft 365. Tout d’abord, vous devez prendre en compte quelques éléments, par exemple :

- Nombre de sièges ou de boîtes aux lettres que vous devez déplacer.
- Durée pendant laquelle vous souhaitez que la migration dure.
- Si vous avez besoin d’une intégration transparente entre votre installation locale et Microsoft 365 pendant la migration.

Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser.

|Option de migration|Taille de l’organisation|Durée|
|---|---|---|
|Migration à basculement|Moins de 150 sièges|Une semaine ou moins|
|Migration hybride minimale|Moins de 150 sièges|Quelques semaines ou moins|
|Migration complète hybride|Plus de 150 sièges|Quelques semaines ou plus|

Les sections suivantes vous donnent une vue d’ensemble de ces méthodes. Pour plus d’informations, consultez [Décider d’un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migration à basculement

Dans une migration de basculement, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, et ainsi de suite vers Office 365 à une date et une heure définies. Lorsque vous avez terminé, vous arrêtez vos serveurs Exchange locaux et commencez à utiliser Microsoft 365 exclusivement.

La migration de basculement est idéale pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent accéder rapidement à Microsoft 365 et qui ne veulent pas gérer la complexité des autres méthodes. Mais il devrait être terminé dans une semaine ou moins. Et cela oblige les utilisateurs à reconfigurer leurs profils Outlook. La migration de basculement peut migrer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons de l’utiliser pour un maximum de 150. Si vous essayez de migrer davantage, vous risquez de manquer de temps pour transférer toutes les boîtes aux lettres avant votre échéance, et votre personnel du support informatique risque d’être submergé par les demandes d’aide aux utilisateurs pour reconfigurer Outlook.

Voici quelques éléments à prendre en compte concernant la migration de basculement :

- Microsoft 365 devra se connecter à vos serveurs Exchange 2010 à l’aide d’Outlook Anywhere via le port TCP 443.
- Toutes les boîtes aux lettres locales seront déplacées vers Microsoft 365.
- Vous aurez besoin d’un compte d’administrateur local disposant d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
- Les domaines acceptés par Exchange 2010 que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
- Entre le moment où vous démarrez la migration et le début de la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et locales. Cela vous permet d’effectuer la migration sans vous soucier de la perte de courrier dans vos boîtes aux lettres locales.
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Microsoft 365. Ils devront les modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-mails téléchargés par Outlook peut varier. Pour plus d’informations, consultez [Travail hors connexion dans Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Pour en savoir plus sur la migration de basculement, consultez :

- [Ce que vous devez savoir sur une migration d’e-mail de basculement](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Effectuer une migration de basculement de l’e-mail vers Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimale

Dans une migration hybride ou rapide minimale, vous déplacez quelques centaines de boîtes aux lettres vers Microsoft 365 en quelques semaines. Cette méthode ne prend pas en charge les fonctionnalités avancées de migration hybride, telles que les informations de calendrier libre/occupé partagées.

La migration hybride minimale est idéale pour les organisations qui doivent prendre plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365, mais qui prévoient toujours d’effectuer la migration dans quelques semaines. Vous bénéficiez de certains des avantages de la *migration hybride complète* plus avancée sans trop de complexité. Vous pouvez contrôler le nombre et les boîtes aux lettres à migrer à un moment donné. Les boîtes aux lettres Microsoft 365 seront créées avec les noms d’utilisateur et les mots de passe des comptes locaux. Et, contrairement aux migrations de basculement, vos utilisateurs n’ont pas à recréer leurs profils Outlook.

Voici quelques éléments à prendre en compte concernant la migration hybride minimale :

- Vous devez effectuer une synchronisation d’annuaires unique entre vos serveurs Active Directory local et Microsoft 365.
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’avant leur boîte aux lettres.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’auront pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, bien que certains anciens téléphones Android aient peut-être besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leurs e-mails.

Pour plus d’informations, consultez [Utiliser un hybride minimal pour migrer rapidement les boîtes aux lettres Exchange vers Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, vous avez plusieurs centaines, jusqu’à des dizaines de milliers, de boîtes aux lettres, et vous déplacez une partie ou la totalité vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides permettent d’effectuer les opérations suivantes :

- Affichez aux utilisateurs locaux les informations de calendrier gratuit/occupé pour les utilisateurs dans Microsoft 365, et vice versa.
- Consultez une liste d’adresses globale unifiée qui contient des destinataires à la fois en local et dans Microsoft 365.
- Affichez les propriétés complètes du destinataire Outlook pour tous les utilisateurs, qu’ils soient locaux ou dans Microsoft 365.
- Sécuriser la communication par e-mail entre les serveurs Exchange locaux et les Office 365 à l’aide de TLS et de certificats.
- Traitez les messages envoyés entre des serveurs Exchange locaux et Microsoft 365 comme internes, ce qui leur permet de :
  - Être correctement évalué et traité par les agents de transport et de conformité ciblant les messages internes.
  - Contournez les filtres anti-courrier indésirable.

Les migrations hybrides complètes sont idéales pour les organisations qui s’attendent à rester dans une configuration hybride pendant plusieurs mois ou plus. Vous obtenez les fonctionnalités répertoriées plus haut dans cette section, ainsi que la synchronisation d’annuaires, de meilleures fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide de déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation locale.

Éléments à prendre en compte concernant la migration hybride complète :

- Elles ne sont pas adaptées à toutes les organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas d’avantages qui justifient l’effort et le coût impliqués. Dans ce cas, nous vous recommandons d’envisager plutôt le basculement ou la migration hybride minimale.
- Vous devez configurer la synchronisation d’annuaires à l’aide d’Azure Active Directory (Azure AD) Connect entre vos serveurs Active Directory local et Microsoft 365.
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite Azure AD Connect avec synchronisation de mot de passe et/ou Services ADFS).
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, bien que certains anciens téléphones Android aient peut-être besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leurs e-mails.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de conserver DirSync ou Azure AD Connect en place pour continuer à gérer les comptes d’utilisateur à partir de Active Directory local, vous devez conserver au moins un serveur Exchange en local. Si tous les serveurs Exchange sont supprimés, vous ne pourrez pas apporter de modifications aux destinataires Exchange dans Exchange Online. Cela est dû au fait que la source d’autorité reste dans votre Active Directory local et que des modifications doivent être apportées.

Si une migration hybride complète vous convient, consultez les ressources utiles suivantes :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)
- [Déploiements hybrides Exchange Server](/exchange/exchange-hybrid)
- [Assistant de configuration hybride](/exchange/hybrid-configuration-wizard)
- [FAQ de l’assistant Configuration hybride](/exchange/hybrid-configuration-wizard-faqs)
- [Configuration requise pour un déploiement hybride](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Effectuer une mise à niveau vers une version plus récente de Exchange Server localement

Nous croyons fermement que vous bénéficiez de la meilleure valeur et de l’expérience utilisateur en migrant entièrement vers Microsoft 365. Toutefois, nous comprenons que certaines organisations doivent conserver certains serveurs Exchange en local. Cela peut être dû à des exigences réglementaires, à la garantie que les données ne sont pas stockées dans un centre de données étranger, parce que vous avez des paramètres ou des exigences uniques qui ne peuvent pas être satisfaits dans le cloud, ou parce que vous avez besoin d’Exchange pour gérer les boîtes aux lettres cloud, car vous utilisez toujours Active Directory localement. Dans tous les cas, si vous conservez Exchange en local, vous devez vous assurer que votre environnement Exchange 2010 est mis à niveau vers au moins Exchange 2013 ou Exchange 2016.

Pour une expérience optimale, nous vous recommandons de mettre à niveau votre environnement local restant vers Exchange 2016. Vous n’avez pas besoin d’installer Exchange Server 2013 si vous souhaitez passer directement de Exchange Server 2010 à Exchange Server 2016.

Exchange 2016 inclut toutes les fonctionnalités des versions précédentes d’Exchange. Il correspond le plus à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités soient disponibles uniquement dans Microsoft 365. Découvrez quelques-unes des choses que vous avez manquées :

|Version d’Exchange|Fonctionnalités|
|---|---|
|**Exchange 2013**|L’architecture simplifiée réduit le nombre de rôles serveur à trois (boîte aux lettres, accès client, transport Edge)|
||Stratégies de protection contre la perte de données (DLP) qui aident à empêcher la fuite d’informations sensibles|
||Amélioration de l’expérience Outlook Web App|
|**Exchange 2016**|*Fonctionnalités d’Exchange 2013 et ...*|
||Autres rôles serveur simplifiés pour uniquement les boîtes aux lettres et le transport edge|
||Amélioration de la protection contre la perte de données avec l’intégration à SharePoint|
||Résilience améliorée de la base de données|
||Collaboration de documents en ligne|


|Considération|Plus d’informations|
|---|---|
|Dates de fin du support|Comme Exchange 2010, chaque version d’Exchange a sa propre date de fin de support : <br/><br/> Exchange 2013 - Avril 2023 <br/><br/> Exchange 2016 - Octobre 2025 <br/><br/> Plus la date de fin du support est précoce, plus tôt vous devrez effectuer une autre migration. Avril 2023 est beaucoup plus proche que vous ne le pensez!|
|Chemin de migration vers Exchange 2013 ou 2016|Le chemin de migration d’Exchange 2010 vers une version plus récente est le même que vous choisissiez Exchange 2013 ou Exchange 2016 : <br/><br/> Installez Exchange 2013 ou 2016 dans votre organisation Exchange 2010 existante. <br/><br/> Déplacer des services et d’autres infrastructures vers Exchange 2013 ou 2016. <br/><br/> Déplacer des boîtes aux lettres et des dossiers publics vers des serveurs Exchange 2013 ou 2016 Désaffectant les serveurs Exchange 2010 restants.|
|Coexistence de versions|Lors de la migration vers Exchange 2013 ou Exchange 2016, vous pouvez installer l’une des versions dans une organisation Exchange 2010 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2013 ou Exchange 2016 et d’effectuer votre migration.|
|Matériel serveur|La configuration matérielle requise pour le serveur a changé à partir d’Exchange 2010. Assurez-vous que votre matériel est compatible. Pour en savoir plus sur la configuration matérielle requise pour chaque version, cliquez ici : <br/><br/> [Configuration requise pour Exchange 2016](/Exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true) <br/><br/> [Configuration requise pour Exchange 2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help) <br/><br/> Avec les améliorations significatives des performances d’Exchange et l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus nouveaux, vous aurez probablement besoin de moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.|
|Version du système d'exploitation|Les versions minimales du système d’exploitation prises en charge pour chaque version sont les suivantes : <br/><br/> Exchange 2016 - Windows Server 2012 <br/><br/> Exchange 2013 - Windows Server 2008 R2 SP1 <br/><br/> Pour plus d’informations sur la prise en charge du système d’exploitation, consultez [la matrice de prise en charge d’Exchange](/exchange/plan-and-deploy/supportability-matrix).|
|Niveau fonctionnel de la forêt Active Directory|Les niveaux fonctionnels de forêt Active Directory minimum pris en charge pour chaque version sont les suivants : <br/><br/> Exchange 2016 - Windows Server 2008 R2 SP1 <br/><br/> Exchange 2013 - Windows Server 2003 <br/><br/> Vous trouverez plus d’informations sur la prise en charge des niveaux fonctionnels de forêt dans [la matrice de support Exchange](/exchange/plan-and-deploy/supportability-matrix).|
|Versions du client Office|Les versions minimales du client Office prises en charge pour chaque version sont les suivantes : <br/><br/> Exchange 2016 - Office 2010 (avec les dernières mises à jour) <br/><br/> Exchange 2013 - Office 2007 SP3 <br/><br/> Pour plus d’informations sur le support client Office, consultez [la matrice de support Exchange](/exchange/plan-and-deploy/supportability-matrix).|

Utilisez les ressources suivantes pour faciliter votre migration :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)
- Modifications du schéma Active Directory pour Exchange [2016](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)
- Configuration système requise pour Exchange [2016](/exchange/plan-and-deploy/system-requirements?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-system-requirements-exchange-2013-help)
- Prérequis pour Exchange [2016](/exchange/plan-and-deploy/prerequisites?view=exchserver-2016&preserve-view=true), [2013](/Exchange/exchange-2013-prerequisites-exchange-2013-help)

## <a name="summary-of-options-for-office-2010-client-and-servers-and-windows-7"></a>Récapitulatif des options pour le client et les serveurs Office 2010 et Windows 7

Pour consulter une synthèse visuelle des options de mise à jour, de migration et de déplacement vers le Cloud pour les produits serveur et client Office 2010 et Windows 7, voir l’[affiche de fin de prise en charge](../downloads/Office2010Windows7EndOfSupport.pdf).

[![Fin du support pour les clients et serveurs Office 2010 et l’affiche Windows 7.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Cette affiche d’une page illustre les différents chemins d’accès que vous pouvez suivre pour répondre aux produits client et serveur Office 2010 et à la fin du support windows 7, avec les chemins d’accès et la prise en charge des options préférés dans Microsoft 365 Entreprise mis en évidence.

Vous pouvez également [télécharger](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) cette affiche et l’imprimer au format lettre, légal ou tabloïd (11 x 17).

## <a name="what-if-i-need-help"></a>Que se passe-t-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Microsoft 365, vous pouvez utiliser notre service Microsoft FastTrack. FastTrack fournit les meilleures pratiques, outils et ressources pour rendre votre migration vers Microsoft 365 aussi transparente que possible. Mieux encore, un ingénieur du support technique vous guidera de la planification et de la conception à la migration de votre dernière boîte aux lettres. Pour plus d’informations sur FastTrack, consultez [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes lors de votre migration vers Microsoft 365 et que vous n’utilisez pas FastTrack, ou si vous effectuez une migration vers une version plus récente de Exchange Server, voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-articles"></a>Articles connexes

[Ressources facilitant la mise à jour de vos clients et serveurs Office 2010](upgrade-from-office-2010-servers-and-products.md)
