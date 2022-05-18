---
title: Exchange feuille de route de fin de support 2013
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: e150e7b9-c432-4c8d-a0ae-c11847129a7d
f1.keywords:
- NOCSH
description: Exchange 2013 prendra fin en avril 2023. Utilisez cette feuille de route de planification pour préparer la mise à niveau vers Exchange Online ou vers une version ultérieure de Exchange Server localement.
ms.openlocfilehash: 0d0cf068ad018e710c6d8e861ac04acfd261def9
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468501"
---
# <a name="exchange-2013-end-of-support-roadmap"></a>Exchange feuille de route de fin de support 2013

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2013 prendra fin le **11 avril 2023**. Si vous n’avez pas encore commencé votre migration de Exchange 2013 vers Microsoft 365, Office 365 ou Exchange 2019, il est temps de commencer à planifier.

## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

La plupart des produits Microsoft ont un cycle de vie de support pendant lequel ils bénéficient de nouvelles fonctionnalités, correctifs de bogues, correctifs de sécurité, et ainsi de suite. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Étant donné que Exchange 2013 atteint sa fin de support le 11 avril 2023, Microsoft ne fournira plus les éléments suivants après cette date :

- Support technique pour les problèmes qui peuvent se produire.
- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.
- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.
- Mises à jour de fuseau horaire.

Votre installation de Exchange 2013 continuera à s’exécuter après cette date. Toutefois, en raison des modifications répertoriées ci-dessus, nous vous recommandons vivement de migrer de Exchange 2013 vers Exchange 2019 dès que possible.


## <a name="what-are-my-options"></a>Quelles sont mes options ?

C’est le moment idéal pour explorer vos options et préparer un plan de migration. Vous pouvez :

- Migrer vers Microsoft 365. Migrez des boîtes aux lettres, des dossiers publics et d’autres données à l’aide du basculement, d’une migration hybride minimale ou d’une migration hybride complète. Ensuite, supprimez les serveurs Exchange locaux et Active Directory.
- Mise à niveau Exchange 2013. Passez à Exchange 2019 pour vos serveurs locaux.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de continuer à utiliser Azure AD Connecter pour gérer des comptes d’utilisateur dans Active Directory, vous devez conserver au moins un serveur Microsoft Exchange en local. Si vous supprimez tous les serveurs Exchange, vous ne pourrez pas apporter de modifications à Exchange destinataires dans Exchange Online, car la source d’autorité est votre Active Directory local. Dans ce scénario, vous disposez des options suivantes :
>
>- *Recommandé:* Migrez vos boîtes aux lettres vers Microsoft 365 et mettez à niveau votre environnement vers Exchange 2019 d’ici le 11 avril 2023. Utilisez Exchange 2013 pour vous connecter à Microsoft 365 et migrer des boîtes aux lettres. Ensuite, effectuez une mise à niveau de Exchange 2013 vers Exchange 2019 et désactivez les serveurs exécutés Exchange 2013.
>- Si vous ne pouvez pas effectuer une migration vers Exchange Online et mettre à niveau vos serveurs locaux avant le 11 avril 2023, effectuez d’abord une mise à niveau de Exchange 2013 vers Exchange 2019, puis utilisez Exchange 2019 pour migrer les boîtes aux lettres vers Microsoft 365.

Voici les trois chemins que vous pouvez suivre pour éviter la fin du support pour Exchange Server 2013.

## <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration vers Microsoft 365 est la meilleure option et la plus simple pour vous aider à mettre hors service votre déploiement Exchange 2013. Avec une migration vers Microsoft 365, vous pouvez effectuer un tronçon unique de l’ancienne technologie vers les fonctionnalités actuelles, notamment :

- Boîtes aux lettres plus volumineuses avec une plus grande résilience des données ;
- Fonctionnalités de sécurité telles que la protection anti-courrier indésirable et anti-programme malveillant, 
- Fonctionnalités de conformité telles que la protection contre la perte de données, les stratégies de rétention, les In-Place et la conservation des litiges, la découverte électronique sur place, etc.
- Intégration à SharePoint Online, OneDrive, Teams, Power BI et d’autres services Microsoft 365 ;
- Boîte de réception prioritaire ; Et
- Analytique avancée et Viva Insights.

Microsoft 365 obtient également de nouvelles fonctionnalités et expériences en premier, afin que votre organisation puisse commencer à les utiliser immédiatement. En outre, vous n’aurez pas à vous soucier de :

- Achat et maintenance du matériel;
- Paiement pour exécuter et refroidir vos serveurs ;
- Maintenir les serveurs à jour sur les correctifs de sécurité, de produit et de fuseau horaire ;
- Gestion du stockage serveur et des logiciels pour prendre en charge les exigences de conformité ; Ou
- Mise à niveau vers une nouvelle version de Exchange ; vous êtes toujours sur la dernière version avec Microsoft 365.

### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment migrer vers Microsoft 365 ?

Selon votre organisation, vous avez quelques options pour accéder à Microsoft 365. Tout d’abord, vous devez prendre en compte quelques éléments, par exemple :

- Nombre de boîtes aux lettres que vous devez déplacer ;
- Durée pendant laquelle vous souhaitez que la migration dure ; Et
- Si vous avez besoin d’une intégration transparente entre votre environnement local et Microsoft 365 pendant la migration.

Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser.

<br>

****

|Option de migration|Taille de l’organisation|Durée|
|---|---|---|
|Migration à basculement|Moins de 150 boîtes aux lettres|Une semaine ou moins|
|Migration hybride minimale|Moins de 150 boîtes aux lettres|Quelques semaines ou moins|
|Migration complète hybride|Plus de 150 boîtes aux lettres|Quelques semaines ou plus|
|

Les sections suivantes vous donnent une vue d’ensemble de ces méthodes. Pour plus d’informations, consultez [Décider d’un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

### <a name="cutover-migration"></a>Migration à basculement

Dans une migration de basculement, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, et ainsi de suite vers Office 365 à une date et une heure définies. Lorsque vous avez terminé, vous arrêtez vos serveurs Exchange locaux et commencez à utiliser Microsoft 365 exclusivement.

La migration par basculement est idéale pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent Microsoft 365 rapidement et qui ne veulent pas gérer la complexité des autres méthodes. Mais il devrait être terminé dans une semaine ou moins. Et cela oblige les utilisateurs à reconfigurer leurs profils Outlook. La migration de basculement peut migrer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons de l’utiliser pour un maximum de 150. Si vous essayez de migrer davantage, vous risquez de manquer de temps pour transférer toutes les boîtes aux lettres avant votre échéance, et votre personnel du support informatique risque d’être submergé par les demandes d’aide aux utilisateurs à reconfigurer Outlook.

Voici quelques éléments à prendre en compte concernant la migration de basculement :

- Microsoft 365 devez vous connecter à vos serveurs Exchange 2013 à l’aide de Outlook Anywhere via le port TCP 443.
- Toutes les boîtes aux lettres locales seront déplacées vers Microsoft 365.
- Vous aurez besoin d’un compte d’administrateur local disposant d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
- Les domaines acceptés Exchange 2013 que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
- Entre le moment où vous démarrez la migration et le début de la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et locales. Cela vous permet d’effectuer la migration sans vous soucier de la perte de courrier dans vos boîtes aux lettres locales.
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leur compte Microsoft 365. Ils devront les modifier lorsqu’ils se connectent à leurs boîtes aux lettres pour la première fois.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-mails que Outlook téléchargera peut varier. Pour plus d’informations, consultez [Travailler hors connexion dans Outlook](https://support.microsoft.com/office/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

Pour en savoir plus sur la migration de basculement, consultez :

- [Ce que vous devez savoir sur une migration d’e-mail de basculement](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration)
- [Effectuer une migration de basculement de l’e-mail vers Office 365](/Exchange/mailbox-migration/cutover-migration-to-office-365)

### <a name="minimal-hybrid-migration"></a>Migration hybride minimale

Dans une migration hybride ou rapide minimale, vous déplacez quelques centaines de boîtes aux lettres vers Microsoft 365 en quelques semaines. Cette méthode ne prend pas en charge les fonctionnalités avancées de migration hybride, telles que les informations de calendrier libre/occupé partagées.

La migration hybride minimale est idéale pour les organisations qui doivent prendre plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365, mais qui prévoient toujours d’effectuer la migration dans quelques semaines. Vous bénéficiez de certains des avantages de la *migration hybride complète* plus avancée sans trop de complexité. Vous pouvez contrôler le nombre et les boîtes aux lettres à migrer à un moment donné. Microsoft 365 boîtes aux lettres seront créées avec les noms d’utilisateur et les mots de passe des comptes locaux. Et, contrairement aux migrations de basculement, vos utilisateurs n’ont pas à recréer leurs profils Outlook.

Voici quelques éléments à prendre en compte concernant la migration hybride minimale :

- Vous devez effectuer une synchronisation d’annuaires unique entre vos serveurs Active Directory local et Microsoft 365.
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’avant leur boîte aux lettres.
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’auront pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leurs e-mails.

Pour plus d’informations, consultez [Utiliser un hybride minimal pour migrer rapidement Exchange boîtes aux lettres vers Office 365](/Exchange/mailbox-migration/use-minimal-hybrid-to-quickly-migrate).

### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, vous avez plusieurs centaines, jusqu’à des dizaines de milliers, de boîtes aux lettres, et vous déplacez tout ou partie vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides permettent d’effectuer les opérations suivantes :

- Affichez aux utilisateurs locaux les informations de calendrier gratuit/occupé pour les utilisateurs dans Microsoft 365, et vice versa.
- Consultez une liste d’adresses globale unifiée qui contient des destinataires en local et en Microsoft 365.
- Affichez les propriétés complètes Outlook destinataire pour tous les utilisateurs, qu’ils soient locaux ou en Microsoft 365.
- Sécuriser la communication par e-mail entre les serveurs Exchange locaux et les Office 365 à l’aide de TLS et de certificats.
- Traitez les messages envoyés entre des serveurs Exchange locaux et des Microsoft 365 comme internes, ce qui leur permet de :
  - Être correctement évalué et traité par les agents de transport et de conformité ciblant les messages internes.
  - Contournez les filtres anti-courrier indésirable.

Les migrations hybrides complètes sont idéales pour les organisations qui s’attendent à rester dans une configuration hybride pendant plusieurs mois ou plus. Vous obtenez les fonctionnalités répertoriées plus haut dans cette section, ainsi que la synchronisation d’annuaires, de meilleures fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide de déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation locale.

Éléments à prendre en compte concernant la migration hybride complète :

- Elles ne sont pas adaptées à toutes les organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas d’avantages qui justifient l’effort et le coût impliqués. Dans ce cas, nous vous recommandons d’envisager plutôt le basculement ou la migration hybride minimale.
- Vous devez configurer la synchronisation d’annuaires à l’aide de Azure Active Directory (Azure AD) Connecter entre vos serveurs Active Directory local et Microsoft 365.
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 avec le même nom d’utilisateur et mot de passe qu’ils utilisent lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite Azure AD Connecter avec synchronisation de mot de passe et/ou Services ADFS).
- Vous avez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’ont pas besoin de recharger leurs e-mails.

> [!IMPORTANT]
> Si votre organisation choisit de migrer des boîtes aux lettres vers Microsoft 365 mais prévoit de conserver Azure AD Connecter pour gérer les comptes d’utilisateur dans Active Directory, vous devez conserver au moins un serveur Exchange en local. Si tous les serveurs Exchange sont supprimés, vous ne pourrez pas apporter de modifications à Exchange destinataires. Cela est dû au fait que la source d’autorité est Active Directory et qu’il faut y apporter des modifications.

Si une migration hybride complète vous convient, consultez les ressources utiles suivantes :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)
- [Déploiements hybrides Exchange Server](/exchange/exchange-hybrid)
- [Assistant de configuration hybride](/exchange/hybrid-configuration-wizard)
- [FAQ de l’assistant Configuration hybride](/exchange/hybrid-configuration-wizard-faqs)
- [Configuration requise pour un déploiement hybride](/exchange/hybrid-deployment-prerequisites)

## <a name="upgrade-to-a-newer-version-of-exchange-server-on-premises"></a>Effectuer une mise à niveau vers une version plus récente de Exchange Server localement

Nous croyons fermement que vous bénéficiez de la meilleure valeur et de l’expérience utilisateur en migrant entièrement vers Microsoft 365. Toutefois, nous comprenons que certaines organisations doivent conserver certains serveurs Exchange localement. Cela peut être dû à des exigences réglementaires, à la garantie que les données ne sont pas stockées dans un centre de données étranger, parce que vous avez des paramètres ou des exigences uniques qui ne peuvent pas être satisfaits dans le cloud, ou parce que vous avez besoin de Exchange pour gérer les boîtes aux lettres cloud, car vous utilisez toujours Active Directory localement. Dans tous les cas, si vous conservez Exchange localement, vous devez vous assurer que votre environnement Exchange 2013 est mis à niveau.

Pour une expérience optimale, nous vous recommandons de mettre à niveau votre environnement local restant vers Exchange 2019. Vous n’avez pas besoin d’installer Exchange Server 2016, car vous pouvez passer directement de Exchange Server 2013 à Exchange Server 2019. Exchange 2019 correspond le plus à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités soient disponibles uniquement dans Microsoft 365.



****
Vous trouverez ci-dessous des informations importantes sur la mise à niveau Exchange 2013 :

|Élément|Informations supplémentaires|
|---|---|
|Dates de fin du support|Comme Exchange 2013, chaque version de Exchange a sa propre date de fin de prise en charge : <p> Exchange 2013 - Avril 2023 <p> Avril 2023 est beaucoup plus proche que vous ne le pensez!|
|Chemin de migration vers Exchange 2019|Le chemin de migration de Exchange 2013 vers une version plus récente est simple : <p> Installez Exchange 2019 dans votre organisation Exchange 2013 existante. <p> Déplacez les services et les données de Exchange 2013 vers Exchange 2019 et désactivez les serveurs Exchange 2013.|
|Matériel serveur|La configuration matérielle requise pour le serveur a changé par Exchange 2013. Assurez-vous que votre matériel est compatible. En savoir plus sur la configuration matérielle requise ici : <p> [configuration requise pour Exchange 2019](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019) <p>Avec les améliorations significatives des performances Exchange et l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus nouveaux, vous aurez probablement besoin de moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.|
|Version du système d'exploitation|La version minimale du système d’exploitation prise en charge pour Exchange 2019 est Windows Server 2019. la prise en charge de Windows Server 2022 sera bientôt disponible <p> Pour plus d’informations sur la prise en charge du système d’exploitation[, consultez Exchange Matrice de prise en charge](/exchange/plan-and-deploy/supportability-matrix).|
|Niveau fonctionnel de la forêt Active Directory|Le niveau fonctionnel minimal de forêt Active Directory pris en charge est Windows Server 2012 R2. Vous trouverez plus d’informations sur la prise en charge au niveau fonctionnel de la forêt dans [Exchange Matrice de prise en charge](/exchange/plan-and-deploy/supportability-matrix).|
|versions clientes Office|La version minimale prise en charge Office client est également documentée dans la [matrice de prise en charge Exchange](/exchange/plan-and-deploy/supportability-matrix?view=exchserver-2019#clients).|
|

Utilisez les ressources suivantes pour faciliter votre migration :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)
- Modifications du schéma Active Directory [pour Exchange 2019](/exchange/plan-and-deploy/active-directory/ad-schema-changes?view=exchserver-2019)
- Configuration [requise pour Exchange 2019](/exchange/plan-and-deploy/system-requirements?view=exchserver-2019)


## <a name="what-if-i-need-help"></a>Que se passe-t-il si j’ai besoin d’aide ?

Si vous effectuez une migration vers Microsoft 365, vous pouvez utiliser notre service Microsoft FastTrack. FastTrack fournit les meilleures pratiques, outils et ressources pour rendre votre migration vers Microsoft 365 aussi transparente que possible. Mieux encore, un ingénieur du support technique vous guidera de la planification et de la conception à la migration de votre dernière boîte aux lettres. Pour plus d’informations sur FastTrack, consultez [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes lors de votre migration vers Microsoft 365 et que vous n’utilisez pas FastTrack, ou si vous migrez vers une version plus récente de Exchange Server, voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
- [Support client](https://support.microsoft.com/gp/support-options-for-business)


