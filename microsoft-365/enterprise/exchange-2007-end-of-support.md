---
title: Feuille de route pour la fin de l’assistance pour Exchange 2007
ms.author: dstrome
author: dstrome
manager: scotv
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Découvrez vos options après Exchange Server fin du support en 2007 et commencez à planifier la migration vers Microsoft 365, Office 365 ou Exchange 2016.
ms.openlocfilehash: 7b8cad31c04d5cd1cd9e618e8e38e872a1b32634
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092666"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Exchange 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2007 a atteint sa fin en avril 2017. Si vous n’avez pas démarré votre migration de Exchange 2007 vers Microsoft 365, Office 365 ou Exchange 2016, il est temps de commencer à planifier.

## <a name="what-does-end-of-support-mean"></a>Que signifie *la fin du support* ?

Exchange Server, comme presque tous les produits Microsoft, a un cycle de vie de support au cours duquel nous fournissons de nouvelles fonctionnalités, des correctifs de bogues, des correctifs de sécurité, et ainsi de suite. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est connue sous le nom de fin de support du produit. Depuis que Exchange 2007 a atteint sa fin de support le 11 avril 2017, Microsoft ne fournit plus :

- Support technique pour les problèmes qui peuvent se produire.

- Résolutions de bogues pour les problèmes susceptibles d’avoir un impact sur la stabilité et la facilité d’utilisation du serveur.

- Correctifs de sécurité pour les vulnérabilités susceptibles de rendre le serveur vulnérable aux violations de sécurité.

- Mises à jour de fuseau horaire.

Votre installation de Exchange 2007 continuera à s’exécuter après la date de fin du support. Toutefois, étant donné qu’il n’existe aucune nouvelle mise à jour ou prise en charge, nous vous recommandons vivement de migrer à partir de Exchange 2007 dès que possible.

Pour plus d’informations sur les serveurs Office 2007 vers la fin du support, consultez [Planifier votre mise à niveau à partir de Office serveurs et produits 2007](upgrade-from-office-2007-servers-and-products.md).

## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vous pouvez :

- Migrez vers Microsoft 365 à l’aide d’une migration par basculement, intermédiaire ou hybride.

- Migrez vos serveurs Exchange 2007 vers une version plus récente de Exchange sur vos serveurs locaux.

Les sections suivantes explorent chaque option plus en détail.

### <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration de votre e-mail vers Microsoft 365 est la meilleure et la plus simple option pour vous aider à mettre hors service votre déploiement Exchange 2007. Avec une migration vers Microsoft 365, vous pouvez effectuer un saut unique de la technologie de 10 ans vers des fonctionnalités de pointe, notamment :

- Fonctionnalités de conformité telles que les stratégies de rétention, In-Place et la conservation des litiges, eDiscovery sur place, etc.

- Groupes Microsoft 365

- Boîte de réception triée

- MyAnalytics

- API REST pour l’accès par programmation aux e-mails, calendriers, contacts, et ainsi de suite

Microsoft 365 obtient également de nouvelles fonctionnalités et expériences en premier, de sorte que vous et vos utilisateurs pouvez généralement commencer à les utiliser immédiatement. Et vous n’aurez pas à vous soucier de :

- Achat et maintenance du matériel.

- Payer pour chauffer et refroidir vos serveurs.

- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire.

- Gestion du stockage et des logiciels pour prendre en charge les exigences de conformité.

- Mise à niveau vers une nouvelle version de Exchange. Avec Microsoft 365, vous êtes toujours sur la dernière version de Exchange.

#### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment migrer vers Microsoft 365 ?

Vous disposez de quelques options de migration. Vous devez prendre en compte quelques éléments, notamment :

- Nombre de sièges ou de boîtes aux lettres que vous devez déplacer.
- Durée pendant laquelle vous souhaitez que la migration dure.
- Indique si vous avez besoin d’une intégration transparente entre votre installation locale et Microsoft 365 pendant la migration.

Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser :

|Option de migration|Taille de l’organisation|Durée|
|---|---|---|
|Migration à basculement|Moins de 150 sièges|Une semaine ou moins|
|Migration intermédiaire|Plus de 150 sièges|Quelques semaines|
|Migration complète hybride|Plusieurs centaines à milliers de sièges|Quelques mois ou plus|

Les sections suivantes fournissent une vue d’ensemble de ces méthodes. Pour plus d’informations, consultez [Décider d’un chemin de migration](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27).

#### <a name="cutover-migration"></a>Migration à basculement

Dans une migration de basculement, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, et ainsi de suite vers Microsoft 365 à une date et une heure présélectionnées. Une fois la migration terminée, vous arrêtez vos serveurs Exchange locaux et commencez à utiliser Microsoft 365 exclusivement.

La migration de basculement est idéale pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent Microsoft 365 rapidement et qui ne veulent pas gérer certaines des complexités des autres méthodes. Toutefois, elle doit être effectuée dans une semaine ou moins, et elle oblige les utilisateurs à reconfigurer leurs profils Outlook. La migration de basculement peut gérer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons vivement de l’utiliser pour migrer un maximum de 150 boîtes aux lettres. Si vous essayez de migrer davantage, vous risquez de manquer de temps pour transférer toutes les boîtes aux lettres avant votre échéance, et votre personnel du support informatique risque d’être submergé par les demandes d’aide aux utilisateurs à reconfigurer Outlook.

Si vous envisagez d’effectuer une migration de basculement, voici les éléments à prendre en compte :

- Microsoft 365 devez vous connecter à vos serveurs Exchange 2007 à l’aide de Outlook Anywhere via le port TCP 443.

- Toutes les boîtes aux lettres locales seront déplacées vers Microsoft 365.

- Vous aurez besoin d’un compte d’administrateur local disposant d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.

- Les domaines acceptés Exchange 2007 que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.

- Entre le moment où vous démarrez la migration et le début de la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et locales. Cela vous permet d’effectuer la migration sans vous soucier de la perte de courrier dans vos boîtes aux lettres locales.

- Les utilisateurs recevront de nouveaux mots de passe temporaires pour leurs comptes Microsoft 365. Ils devront modifier leur mot de passe lorsqu’ils se connectent à leur boîte aux lettres pour la première fois.

- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.

- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-mails que Outlook téléchargera peut varier. Pour plus d’informations, consultez [Modifier la quantité de courrier à conserver hors connexion](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Pour plus d’informations sur la migration de basculement, consultez :

- [Ce que vous devez savoir sur une migration d’e-mail de basculement](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)

- [Effectuer une migration de basculement d’e-mail](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)

#### <a name="staged-migration"></a>Migration intermédiaire

Dans une migration intermédiaire, vous avez quelques centaines ou quelques milliers de boîtes aux lettres que vous souhaitez migrer vers Microsoft 365, devez prendre une semaine ou plus pour terminer la migration et n’avez besoin d’aucune des fonctionnalités de migration hybride avancées telles que les informations de calendrier libre/occupé partagées.

La migration intermédiaire est idéale pour les organisations qui doivent prendre plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365, mais qui prévoient toujours d’effectuer la migration dans quelques semaines. Vous pouvez migrer des boîtes aux lettres par lots. Vous contrôlez le nombre et les boîtes aux lettres qui sont migrées à un moment donné. Vous pouvez traiter par lots des boîtes aux lettres d’utilisateurs dans le même service, par exemple, pour vous assurer qu’elles sont toutes déplacées en même temps. Vous pouvez également laisser les boîtes aux lettres de direction jusqu’au dernier lot. Comme pour les migrations de basculement, vos utilisateurs doivent recréer leurs profils Outlook.

Si vous envisagez d’effectuer une migration intermédiaire, voici les éléments à prendre en compte :

- Microsoft 365 devez vous connecter à vos serveurs Exchange 2007 à l’aide de Outlook Anywhere via le port TCP 443.

- Vous aurez besoin d’un compte d’administrateur local disposant d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.

- Les domaines acceptés Exchange 2007 que vous envisagez d’utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.

- Vous devez créer un fichier CSV avec le nom complet et l’adresse e-mail de chaque boîte aux lettres que vous envisagez de migrer dans un lot. Vous devez également inclure un nouveau mot de passe pour chaque boîte aux lettres que vous migrez et envoyer ce mot de passe à chaque utilisateur. L’utilisateur est invité à modifier le mot de passe la première fois qu’il se connecte à sa nouvelle boîte aux lettres Microsoft 365.

- Entre le moment où vous démarrez le lot de migration et le début de la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et locales incluses dans le lot. Cela vous permet d’effectuer la migration sans vous soucier de la perte de courrier dans vos boîtes aux lettres locales.

- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.

- Les utilisateurs devront configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-mails que Outlook téléchargera peut varier. Pour plus d’informations, consultez [Modifier la quantité de courrier à conserver hors connexion](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1).

Pour plus d’informations sur la migration intermédiaire, consultez :

- [Ce que vous devez savoir sur une migration par e-mail intermédiaire](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)

- [Effectuer une migration intermédiaire de l’e-mail](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)

#### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, votre organisation a plusieurs centaines, jusqu’à des dizaines de milliers, de boîtes aux lettres, et vous souhaitez déplacer une partie ou la totalité d’entre elles vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides permettent d’effectuer les opérations suivantes :

- Affichez aux utilisateurs locaux les informations de calendrier gratuit/occupé pour les utilisateurs dans Microsoft 365, et vice versa.

- Consultez une liste d’adresses globale unifiée qui contient des destinataires en local et en Microsoft 365.

- Affichez les propriétés complètes Outlook destinataire pour tous les utilisateurs, qu’ils soient locaux ou en Microsoft 365.

- Sécuriser la communication par e-mail entre les serveurs Exchange locaux et les Microsoft 365 à l’aide de TLS et de certificats.

- Traitez les messages envoyés entre des serveurs Exchange locaux et des Microsoft 365 comme internes, ce qui leur permet de :

  - Être correctement évalué et traité par les agents de transport et de conformité ciblant les messages internes.

  - Contournez les filtres anti-courrier indésirable.

La migration hybride complète est préférable pour les organisations qui s’attendent à rester dans une configuration hybride pendant plusieurs mois ou plus. Vous obtiendrez les fonctionnalités répertoriées plus haut dans cette section, ainsi que la synchronisation d’annuaires, de meilleures fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide de déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation locale.

Si vous envisagez d’effectuer une migration hybride complète, voici les éléments à prendre en compte :

- La migration hybride complète n’est pas adaptée à tous les types d’organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas les avantages qui justifient l’effort et le coût nécessaires pour en configurer une. Si cela ressemble à votre organisation, nous vous recommandons d’envisager plutôt une migration intermédiaire ou de basculement.

- Vous devez déployer au moins un serveur Exchange 2013 dans votre organisation Exchange 2007 pour agir en tant que « serveur hybride ». Ce serveur communiquera avec Microsoft 365 au nom de vos serveurs Exchange 2007.

- Microsoft 365 devez vous connecter au « serveur hybride » à l’aide de Outlook n’importe où sur le port TCP 443.

- Vous devez configurer la synchronisation d’annuaires à l’aide de Connecter Azure Active Directory (Azure AD) entre vos serveurs Active Directory local et Microsoft 365.

- Les utilisateurs peuvent se connecter à leur boîte aux lettres Microsoft 365 à l’aide du même nom d’utilisateur et mot de passe que lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite Azure AD Connecter avec synchronisation de mot de passe et/ou Services ADFS.)

- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online pour chaque boîte aux lettres utilisateur que vous migrez.

- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook sur la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’auront pas à recharger leurs e-mails.

Si la migration hybride complète vous convient, consultez les ressources suivantes pour faciliter votre migration :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)

- [Déploiements hybrides Exchange Server](/exchange/exchange-hybrid)

- [Assistant de configuration hybride](/exchange/hybrid-configuration-wizard)

- [FAQ de l’assistant Configuration hybride](/exchange/hybrid-configuration-wizard-faqs)

- [Configuration requise pour un déploiement hybride](/exchange/hybrid-deployment-prerequisites)

### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrer vers une version plus récente de Exchange Server

Nous croyons fermement que vous pouvez obtenir la meilleure valeur et la meilleure expérience utilisateur en migrant vers Microsoft 365. Mais nous comprenons également que certaines organisations doivent conserver leurs e-mails localement. Cela peut être dû à des exigences réglementaires, pour garantir que les données ne sont pas stockées dans un centre de données situé dans un autre pays, ou similaire. Si vous choisissez de conserver votre messagerie localement, vous pouvez migrer votre environnement Exchange 2007 vers Exchange 2010, Exchange 2013 ou Exchange 2016.

Si vous ne pouvez pas migrer vers Microsoft 365, nous vous recommandons de migrer vers Exchange 2016. Exchange 2016 inclut toutes les fonctionnalités des versions précédentes de Exchange. Il correspond également le plus à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités soient disponibles uniquement dans Microsoft 365. Découvrez quelques-unes des choses que vous avez manquées :

|version Exchange|Fonctionnalités|
|---|---|
|Exchange 2010| Role-Based Access Control (autorisations sans ACL) <br/> Stratégies de boîte aux lettres de Outlook Web App <br/> Possibilité de partager des calendriers gratuits/occupés et délégués entre les organisations|
|Exchange 2013| *Fonctionnalités de Exchange 2010 et ...* <br/> Architecture simplifiée qui a réduit le nombre de rôles serveur à trois (boîte aux lettres, accès client, transport Edge) <br/> Stratégies de protection contre la perte de données (DLP) qui aident à empêcher la fuite d’informations sensibles <br/> Amélioration de l’expérience d’application web Outlook|
|Exchange 2016| *Fonctionnalités de Exchange 2013 et ...* <br/> Autres rôles serveur simplifiés pour uniquement les boîtes aux lettres et le transport edge <br/> Amélioration de la protection contre la perte de données avec intégration à SharePoint <br/> Résilience améliorée de la base de données <br/> Collaboration de documents en ligne|

#### <a name="which-version-should-i-migrate-to"></a>Vers quelle version dois-je migrer ?

Nous vous recommandons de supposer initialement que vous allez migrer vers Exchange 2016. Utilisez ensuite les informations suivantes pour confirmer votre hypothèse ou exclure Exchange 2016. Si vous ne pouvez pas migrer vers Exchange 2016 pour une raison quelconque, effectuez le même processus avec Exchange 2013, et ainsi de suite.

|Considération|Plus d’informations|
|---|---|
|Dates de fin du support| Comme Exchange 2007, chaque version de Exchange a sa propre date de fin de support : <br/> *Exchange 2010* - Janvier 2020 <br/> *Exchange 2013* - Avril 2023 <br/> *Exchange 2016* - Octobre 2025 <br/> Plus la fin du support est précoce, plus tôt vous devrez effectuer une autre migration.|
|Chemin de migration vers Exchange 2010 et 2013.|Voici les phases générales de la migration vers Exchange 2010 ou Exchange 2013 : <br/> - Installez Exchange 2010 ou 2013 dans votre organisation Exchange 2007 existante. <br/>- Déplacer des services et d’autres infrastructures vers Exchange 2010 ou 2013.<br/>- Déplacer les boîtes aux lettres et les dossiers publics vers Exchange 2010 ou 2013.<br/>- Désaffecter les serveurs restants Exchange 2007.|
|Chemin de migration vers Exchange 2016|Voici les phases générales de la migration vers Exchange 2016 : <br/> - Installez Exchange 2013 dans votre organisation Exchange 2007 existante.<br/>- Déplacer des services et d’autres infrastructures vers Exchange 2013.<br/>- Déplacer les boîtes aux lettres et les dossiers publics vers Exchange 2013.<br/>- Désaffecter les serveurs restants Exchange 2007.<br/>- Installez Exchange 2016 dans votre organisation Exchange 2013 existante.<br/>- Déplacer des boîtes aux lettres, des dossiers publics, des services et d’autres infrastructures vers Exchange 2016 (l’ordre n’a pas d’importance). Désaffectez les serveurs restants Exchange 2013.<br/><br/> **Note:** La migration de Exchange 2013 vers Exchange 2016 est simple. Les deux versions ont presque les mêmes exigences matérielles, et ces versions sont très compatibles. Vous pouvez donc reconstruire un serveur que vous avez acheté pour Exchange 2013 et y installer Exchange 2016. Pour les déplacements de boîtes aux lettres en ligne, la plupart des utilisateurs ne remarquent même pas que leur boîte aux lettres a été déplacée hors du serveur, puis de nouveau après l’avoir reconstruite avec Exchange 2016.|
|Coexistence de versions| Lors de la migration vers ... <br/> **Exchange 2016 :** Exchange 2016 ne peut pas être installé dans une organisation qui inclut un serveur Exchange 2007. Vous devez d’abord migrer vers Exchange 2010 ou 2013 (nous vous recommandons vivement Exchange 2013), supprimer tous les serveurs Exchange 2007, puis migrer vers Exchange 2016. <br/> **Exchange 2010 ou Exchange 2013 :** vous pouvez installer Exchange 2010 ou Exchange 2013 dans une organisation Exchange 2007 existante. Cela vous permet d’installer un ou plusieurs serveurs Exchange 2010 ou 2013 et d’effectuer votre migration.|
|Matériel serveur| La configuration matérielle requise du serveur a changé par Exchange 2007. Assurez-vous que votre matériel est compatible. Pour obtenir des informations détaillées, voir : <br/> [configuration requise pour Exchange 2016](/Exchange/plan-and-deploy/system-requirements) <br/> [configuration requise pour Exchange 2013](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [configuration requise pour Exchange 2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/> Vous constaterez que les améliorations significatives des performances de Exchange et l’augmentation de la puissance de calcul et de la capacité de stockage dans les serveurs plus nouveaux signifient que vous aurez probablement besoin de moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.|
|Version du système d'exploitation| Les versions minimales du système d’exploitation prises en charge pour chaque version sont les suivantes : <br/> **Exchange 2016** - Windows Server 2012 <br/> **Exchange 2013** - Windows Server 2008 R2 SP1 <br/> **Exchange 2010** - Windows Server 2008 SP2 <br/> Pour plus d’informations sur la prise en charge du système d’exploitation[, consultez Exchange Matrice de prise en charge](/Exchange/plan-and-deploy/supportability-matrix).|
|Niveau fonctionnel de la forêt Active Directory| Les niveaux fonctionnels de forêt Active Directory minimum pris en charge pour chaque version sont les suivants : <br/> **Exchange 2016** Windows Server 2008 R2 SP1 <br/> **Exchange 2013** Windows Server 2003 <br/> **Exchange 2010** Windows Server 2003 <br/> Pour plus d’informations sur la prise en charge au niveau fonctionnel de la forêt[, consultez Exchange Matrice de support](/Exchange/plan-and-deploy/supportability-matrix).|
|versions clientes Office| Les versions minimales prises en charge Office client pour chaque version sont les suivantes : <br/> **Exchange 2016** - Office 2010 (avec les dernières mises à jour) <br/> **Exchange 2013** - Office 2007 SP3 <br/> **Exchange 2010** - Office 2003 <br/> Pour plus d’informations sur Office support client, consultez [Exchange Matrice de support](/Exchange/plan-and-deploy/supportability-matrix).|

#### <a name="how-do-i-migrate"></a>Comment faire migrer ?

Si vous avez décidé de conserver votre e-mail localement, utilisez les ressources suivantes pour faciliter votre migration :

- [Assistant Déploiement Exchange](/exchange/exchange-deployment-assistant)

- Modifications du schéma Active Directory pour Exchange [2016](/Exchange/plan-and-deploy/active-directory/ad-schema-changes), [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help), [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)

- Configuration système requise pour Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))

- Prérequis pour Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))

## <a name="get-help"></a>Obtenir de l’aide

Si vous effectuez une migration vers Microsoft 365, vous pouvez utiliser notre service Microsoft FastTrack. FastTrack fournit les meilleures pratiques, outils et ressources pour rendre votre migration vers Microsoft 365 aussi transparente que possible. Mieux encore, un ingénieur du support technique vous guide tout au long de votre migration, de la planification et de la conception jusqu’à la migration de votre dernière boîte aux lettres. Pour plus d’informations sur FastTrack, consultez [Microsoft FastTrack](https://fasttrack.microsoft.com/).

Si vous rencontrez des problèmes lors de votre migration vers Microsoft 365 et que vous n’utilisez pas FastTrack ou votre migration vers une version plus récente de Exchange Server, nous sommes là pour vous aider. Voici quelques ressources que vous pouvez utiliser :

- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)

- [Support client](https://support.microsoft.com/gp/support-options-for-business)

## <a name="related-topics"></a>Voir aussi

[Ressources pour vous aider à mettre à niveau vos serveurs et clients Office 2007](upgrade-from-office-2007-servers-and-products.md)
