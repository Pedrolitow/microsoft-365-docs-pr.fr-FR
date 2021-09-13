---
title: Feuille de route pour la fin de l’assistance pour Exchange 2007
ms.author: dstrome
author: dstrome
manager: laurawi
ms.date: 1/31/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.assetid: c3024358-326b-404e-9fe6-b618e54d977d
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Découvrez vos options après Exchange Server 2007 et commencez à planifier la migration vers Microsoft 365, Office 365 ou Exchange 2016.
ms.openlocfilehash: d7e8f50118dab6fcb618273f5c28497c80d4a549
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207612"
---
# <a name="exchange-2007-end-of-support-roadmap"></a>Feuille de route pour la fin de l’assistance pour Exchange 2007

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Exchange Server 2007 a atteint la fin du support en avril 2017. Si vous n’avez pas commencé la migration de Exchange 2007 vers Microsoft 365, Office 365 ou Exchange 2016, il est temps de commencer la planification.
  
## <a name="what-does-end-of-support-mean"></a>*Qu’est-ce que la fin du support* signifie ?

Exchange Server, comme presque tous les produits Microsoft, a un cycle de vie de support pendant lequel nous fournissons de nouvelles fonctionnalités, des correctifs de bogue, des correctifs de sécurité, etc. Ce cycle de vie dure généralement 10 ans à partir de la version initiale du produit. La fin de ce cycle de vie est appelée fin de support du produit. Étant Exchange 2007 a atteint sa fin de support le 11 avril 2017, Microsoft ne fournit plus :
  
- Support technique pour les problèmes qui peuvent se produire.
    
- Résolutions de bogues pour les problèmes qui peuvent avoir un impact sur la stabilité et la convivialité du serveur.
    
- Correctifs de sécurité pour les vulnérabilités qui peuvent rendre le serveur vulnérable aux violations de sécurité.
    
- Mises à jour de fuseau horaire.
    
Votre installation de Exchange 2007 continuera à s’exécuter après la date de fin de prise en charge. Toutefois, étant donné qu’il n’existe aucune nouvelle mise à jour ou prise en charge, nous vous recommandons vivement de migrer de Exchange 2007 dès que possible.
  
Pour plus d’informations sur Office 2007 vers la fin de la prise en charge, voir Planifier votre mise à niveau à partir de Office [2007.](upgrade-from-office-2007-servers-and-products.md)
  
## <a name="what-are-my-options"></a>Quelles sont mes options ?

Vous pouvez :
  
- Migrez vers Microsoft 365 à l’aide d’une migration à cutover, par étapes ou hybride.
    
- Migrez Exchange serveurs 2007 vers une version plus récente de Exchange sur vos serveurs locaux.
    
Les sections suivantes explorent chaque option plus en détail.
  
### <a name="migrate-to-microsoft-365"></a>Migrer vers Microsoft 365

La migration de votre courrier vers Microsoft 365 est la meilleure option et la plus simple pour vous aider à retirer votre déploiement Exchange 2007. Avec une migration vers Microsoft 365, vous pouvez effectuer un saut unique entre une technologie de 10 ans et des fonctionnalités de pointe, notamment :
  
- Fonctionnalités de conformité telles que les stratégies de rétention, In-Place conservation pour litige, eDiscovery sur place, et bien plus encore
    
- Groupes Microsoft 365
    
- Boîte de réception triée
    
- MyAnalytics
    
- API REST pour l’accès par programme à la messagerie, aux calendriers, aux contacts, et ainsi de suite
    
Microsoft 365 de nouvelles fonctionnalités et expériences en premier, vous et vos utilisateurs pouvez généralement commencer à les utiliser immédiatement. Et vous n’avez pas à vous soucier des :
  
- Achat et maintenance du matériel.
    
- Payer à la température et à la température de vos serveurs.
    
- Tenir à jour les correctifs de sécurité, de produit et de fuseau horaire.
    
- Maintenance du stockage et des logiciels pour prendre en charge les exigences de conformité.
    
- Mise à niveau vers une nouvelle version de Exchange. Avec Microsoft 365, vous êtes toujours sur la dernière version de Exchange.
    
#### <a name="how-should-i-migrate-to-microsoft-365"></a>Comment migrer vers Microsoft 365 ?

Vous avez plusieurs options de migration. Vous devez prendre en compte plusieurs éléments, notamment :

- Nombre de sièges ou de boîtes aux lettres à déplacer.
- Durée de la migration.
- Si vous avez besoin d’une intégration transparente entre votre installation locale et Microsoft 365 lors de la migration.

Ce tableau présente vos options de migration et les facteurs les plus importants qui déterminent la méthode à utiliser :
  

|**Option de migration**|**Taille de l’organisation**|**Duration**|
|:-----|:-----|:-----|
|Migration à basculement  <br/> |Moins de 150 sièges  <br/> |Une semaine ou moins  <br/> |
|Migration intermédiaire  <br/> |Plus de 150 sièges  <br/> |Quelques semaines  <br/> |
|Migration complète hybride  <br/> |Plusieurs centaines à milliers de sièges  <br/> |Quelques mois ou plus  <br/> |
   
Les sections suivantes fournissent une vue d’ensemble de ces méthodes. Pour plus d’informations, [voir Décider d’un chemin de migration.](https://support.office.com/article/Decide-on-a-migration-path-0d4f2396-9cef-43b8-9bd6-306d01df1e27) 
  
#### <a name="cutover-migration"></a>Migration à basculement

Dans une migration à cutover, vous migrez toutes vos boîtes aux lettres, groupes de distribution, contacts, etc., vers Microsoft 365 à une date et une heure pré-sélectionnés. Une fois la migration terminée, vous devez arrêter vos serveurs Exchange locaux et commencer à utiliser Microsoft 365 exclusivement.
  
La migration à cutover est très efficace pour les petites organisations qui n’ont pas beaucoup de boîtes aux lettres, qui souhaitent Microsoft 365 rapidement et qui ne souhaitent pas gérer certaines des complexités des autres méthodes. Toutefois, il doit s’achever dans une semaine ou moins et nécessite que les utilisateurs reconfigurent Outlook profils. La migration à cutover peut gérer jusqu’à 2 000 boîtes aux lettres, mais nous vous recommandons vivement de l’utiliser pour migrer un maximum de 150 boîtes aux lettres. Si vous essayez de migrer davantage, vous risquez de ne plus pouvoir transférer toutes les boîtes aux lettres avant l’échéance, et votre personnel de support technique risque d’être submergé par les demandes d’aide aux utilisateurs pour reconfigurer les Outlook.
  
Si vous envisagez d’une migration àover, voici les éléments à prendre en compte :
  
- Microsoft 365 vous connecter à vos serveurs Exchange 2007 à l’aide de Outlook Anywhere sur le port TCP 443.
    
- Toutes les boîtes aux lettres sur site sont déplacées vers Microsoft 365.
    
- Vous aurez besoin d’un compte d’administrateur local qui dispose d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
    
- Les Exchange 2007 acceptés que vous souhaitez utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
    
- Entre le début de la migration et la phase d’achèvement, Microsoft 365 synchronise régulièrement les boîtes aux lettres Microsoft 365 et sur site. Cela vous permet d’effectuer la migration sans vous soucier du fait que le courrier électronique soit laissé dans vos boîtes aux lettres sur site.
    
- Les utilisateurs recevront de nouveaux mots de passe temporaires pour Microsoft 365 comptes. Ils devront modifier leur mot de passe lorsqu’ils se connectent à leur boîte aux lettres pour la première fois.
    
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
    
- Les utilisateurs doivent configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-Outlook que vous téléchargerez peut varier. Pour plus d’informations, [voir Modifier la quantité de messages à conserver hors connexion.](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)
    
Pour plus d’informations sur la migration à cutover, voir :
  
- [Ce que vous devez savoir sur une migration de messagerie à cutover](https://support.office.com/article/What-you-need-to-know-about-a-cutover-email-migration-to-Office-365-961978ef-f434-472d-a811-1801733869da)
    
- [Effectuer une migration à cutover de la messagerie](https://support.office.com/article/Perform-a-cutover-migration-of-email-to-Office-365-9496e93c-1e59-41a8-9bb3-6e8df0cd81b4)
    
#### <a name="staged-migration"></a>Migration intermédiaire

Dans une migration par étapes, vous avez quelques centaines ou quelques milliers de boîtes aux lettres que vous souhaitez migrer vers Microsoft 365, vous devez prendre une semaine ou plus pour effectuer la migration et vous n’avez pas besoin de fonctionnalités de migration hybride avancées telles que les informations de calendrier de libre/occupé partagées.
  
La migration par étapes est très bien pour les organisations qui ont besoin de plus de temps pour migrer leurs boîtes aux lettres vers Microsoft 365 mais qui prévoient de terminer la migration dans un délai de quelques semaines. Vous pouvez migrer des boîtes aux lettres par lots. Vous contrôlez le nombre et les boîtes aux lettres migrées à un moment donné. Vous pouvez par exemple lotr des boîtes aux lettres d’utilisateurs dans le même service pour vous assurer qu’elles sont toutes déplacées en même temps. Vous pouvez également laisser des boîtes aux lettres de direction jusqu’au dernier lot. Comme avec les migrations à cutover, vos utilisateurs devront recréer leurs profils Outlook de migration.
  
Si vous envisagez d’une migration par étapes, voici les éléments à prendre en compte :
  
- Microsoft 365 vous connecter à vos serveurs Exchange 2007 à l’aide de Outlook Anywhere sur le port TCP 443.
    
- Vous aurez besoin d’un compte d’administrateur local qui dispose d’un accès en lecture aux boîtes aux lettres de vos utilisateurs.
    
- Les Exchange 2007 acceptés que vous prévoyez d’utiliser dans Microsoft 365 doivent être ajoutés en tant que domaines vérifiés dans le service.
    
- Vous devez créer un fichier CSV avec le nom complet et l’adresse e-mail de chaque boîte aux lettres que vous prévoyez de migrer dans un lot. Vous devez également inclure un nouveau mot de passe pour chaque boîte aux lettres que vous migrez et envoyer ce mot de passe à chaque utilisateur. L’utilisateur est invité à modifier le mot de passe la première fois qu’il se connecte à sa nouvelle boîte Microsoft 365 lettres.
    
- Entre le moment où vous démarrez le lot de migration et la phase d’achèvement, Microsoft 365 synchronise périodiquement les boîtes aux lettres Microsoft 365 et sur site incluses dans le lot. Cela vous permet d’effectuer la migration sans vous soucier du fait que le courrier électronique soit laissé dans vos boîtes aux lettres sur site.
    
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
    
- Les utilisateurs doivent configurer un nouveau profil Outlook sur chacun de leurs appareils et télécharger à nouveau leur courrier électronique. La quantité d’e-Outlook que vous téléchargerez peut varier. Pour plus d’informations, [voir Modifier la quantité de messages à conserver hors connexion.](https://support.office.com/article/Change-how-much-mail-to-keep-offline-f3a1251c-6dd5-4208-aef9-7c8c9522d633?ui=en-US&amp;rs=en-US&amp;ad=US&amp;fromAR=1)
    
Pour plus d’informations sur la migration par étapes, voir :
  
- [Ce que vous devez savoir sur une migration de messagerie par étapes](https://support.office.com/article/What-you-need-to-know-about-a-staged-email-migration-to-Office-365-7e2c82be-5f3d-4e36-bc6b-e5b4d411e207)
    
- [Effectuer une migration de courrier électronique par étapes](https://support.office.com/article/Perform-a-staged-migration-of-email-to-Office-365-83bc0b69-de47-4cc4-a57d-47e478e4894e)
    
#### <a name="full-hybrid"></a>Hybride complet

Dans une migration hybride complète, votre organisation dispose de plusieurs centaines, jusqu’à des dizaines de milliers, de boîtes aux lettres et vous souhaitez déplacer une partie ou la totalité d’entre elles vers Microsoft 365. Étant donné que ces migrations sont généralement à plus long terme, les migrations hybrides rendent possible :
  
- Affichez les informations de calendrier des utilisateurs locaux pour les utilisateurs dans Microsoft 365, et vice versa.
    
- Consultez une liste d’adresses globale unifiée qui contient des destinataires à la fois en local et Microsoft 365.
    
- Affichez toutes Outlook propriétés du destinataire pour tous les utilisateurs, qu’ils soient locaux ou Microsoft 365.
    
- Sécuriser la communication par courrier électronique entre les serveurs Exchange locaux et Microsoft 365 l’aide de TLS et de certificats.
    
- Traitez les messages envoyés entre des serveurs Exchange locaux et Microsoft 365 comme internes, ce qui leur permet de :
    
  - Être correctement évaluées et traitées par les agents de transport et de conformité ciblant les messages internes.
    
  - Contourner les filtres anti-courrier indésirable.
    
La migration hybride complète est la meilleure solution pour les organisations qui prévoient de rester dans une configuration hybride pendant de nombreux mois ou plus. Vous obtenez les fonctionnalités répertoriées plus tôt dans cette section, ainsi que la synchronisation d’annuaires, de meilleures fonctionnalités de conformité intégrées et la possibilité de déplacer des boîtes aux lettres vers et depuis Microsoft 365 à l’aide de déplacements de boîtes aux lettres en ligne. Microsoft 365 devient une extension de votre organisation sur site.
  
Si vous envisagez d’une migration hybride complète, voici les éléments à prendre en compte :
  
- La migration hybride complète n’est pas adaptée à tous les types d’organisations. En raison de la complexité des migrations hybrides complètes, les organisations avec moins de quelques centaines de boîtes aux lettres ne voient généralement pas d’avantages qui justifient l’effort et le coût nécessaires pour en configurer une. Si cela ressemble à votre organisation, nous vous recommandons d’envisager plutôt une migration à cutover ou par étapes.
    
- Vous devez déployer au moins un serveur Exchange 2013 dans votre organisation Exchange 2007 pour agir en tant que « serveur hybride ». Ce serveur communiquera avec Microsoft 365 de la part de vos serveurs Exchange 2007.
    
- Microsoft 365 vous connecter au « serveur hybride » à l’aide de Outlook Anywhere sur le port TCP 443.
    
- Vous devez configurer la synchronisation d’annuaires à l’aide de Azure Active Directory (Azure AD) Connecter entre vos serveurs Active Directory locaux et Microsoft 365.
    
- Les utilisateurs pourront se connecter à leur boîte aux lettres Microsoft 365 à l’aide des mêmes nom d’utilisateur et mot de passe que lorsqu’ils se connectent au réseau local. (Cette fonctionnalité nécessite azure AD Connecter synchronisation de mot de passe et/ou services de fédération Active Directory.)
    
- Vous aurez besoin d’une licence Microsoft 365 qui inclut Exchange Online boîte aux lettres utilisateur que vous migrez.
    
- Les utilisateurs n’ont pas besoin de configurer un nouveau profil Outlook la plupart de leurs appareils, même si certains téléphones Android plus anciens peuvent avoir besoin d’un nouveau profil. Les utilisateurs n’auront pas à recharger leur courrier électronique.
    
Si la migration hybride complète vous semble appropriées, consultez les ressources suivantes pour vous aider dans votre migration :
  
- [Exchange Assistant de déploiement](/exchange/exchange-deployment-assistant)
    
- [Déploiements hybrides Exchange Server](/exchange/exchange-hybrid)
    
- [Assistant de configuration hybride](/exchange/hybrid-configuration-wizard)
    
- [FAQ de l’assistant Configuration hybride](/exchange/hybrid-configuration-wizard-faqs)
    
- [Configuration requise pour un déploiement hybride](/exchange/hybrid-deployment-prerequisites)
    
### <a name="migrate-to-a-newer-version-of-exchange-server"></a>Migrer vers une version plus récente de Exchange Server

Nous pensons vivement que vous pouvez obtenir la meilleure valeur et la meilleure expérience utilisateur en migrer vers Microsoft 365. Toutefois, nous comprenons également que certaines organisations doivent conserver leurs messages en local. Cela peut être dû à des exigences réglementaires, afin de garantir que les données ne sont pas stockées dans un centre de données situé dans un autre pays, ou d’une manière similaire. Si vous choisissez de conserver votre messagerie en local, vous pouvez migrer votre environnement Exchange 2007 vers Exchange 2010, Exchange 2013 ou Exchange 2016.
  
Si vous ne pouvez pas migrer vers Microsoft 365, nous vous recommandons de migrer vers Exchange 2016. Exchange 2016 inclut toutes les fonctionnalités des versions précédentes de Exchange. Il correspond également le mieux à l’expérience disponible avec Microsoft 365, bien que certaines fonctionnalités soient disponibles uniquement dans Microsoft 365. Découvrez quelques-uns des éléments manquants :
  
|**Exchange version**|**Composants**|
|:-----|:-----|
|Exchange 2010  <br/> | Role-Based contrôle d’accès (autorisations sans AAL)  <br/>  Stratégies de boîte aux lettres de Outlook Web App  <br/>  Possibilité de partager des calendriers de libre/occupé et de déléguer des calendriers entre des organisations  <br/> |
|Exchange 2013  <br/> | *Fonctionnalités de Exchange 2010 et ...*  <br/>  Architecture simplifiée qui a réduit le nombre de rôles serveur à trois (boîte aux lettres, accès au client, transport Edge)  <br/>  Stratégies de protection contre la perte de données (DLP) qui empêchent la fuite d’informations sensibles  <br/>  Amélioration de Outlook Web App  <br/> |
|Exchange 2016  <br/> | *Fonctionnalités de Exchange 2013 et ...*  <br/>  Autres rôles serveur simplifiés pour les boîtes aux lettres et le transport Edge  <br/>  Amélioration de la DLP avec l’intégration avec SharePoint  <br/>  Résilience de base de données améliorée  <br/>  Collaboration sur des documents en ligne |
   
#### <a name="which-version-should-i-migrate-to"></a>Vers quelle version dois-je migrer ?

Nous vous recommandons de supposer initialement que vous allez migrer vers Exchange 2016. Ensuite, utilisez les informations suivantes pour confirmer votre hypothèse ou pour exclure Exchange 2016. Si vous ne pouvez pas migrer vers Exchange 2016 pour une raison quelconque, faites le même processus avec Exchange 2013, etc.
  
|**Considération**|**Plus d’informations**|
|:-----|:-----|
|Dates de fin du support  <br/> | Comme Exchange 2007, chaque version de Exchange a sa propre date de fin de prise en charge :  <br/> *Exchange 2010* - Janvier 2020  <br/> *Exchange 2013* - Avril 2023  <br/> *Exchange 2016* - Octobre 2025  <br/>  Plus la fin du support est antérieure, plus vite vous devrez effectuer une autre migration.<br/> |
|Chemin de migration Exchange 2010 et 2013.  <br/> |Voici les phases générales de migration vers Exchange 2010 ou Exchange 2013 :  <br/> - Installez Exchange 2010 ou 2013 dans votre organisation Exchange 2007 existante. <br/>- Déplacez les services et autres infrastructures vers Exchange 2010 ou 2013.<br/>- Déplacer des boîtes aux lettres et des dossiers publics vers Exchange 2010 ou 2013.<br/>- Désaffecter les serveurs Exchange 2007. |
|Chemin de migration vers Exchange 2016  <br/> |Voici les phases générales de migration vers Exchange 2016 :  <br/> - Installez Exchange 2013 dans votre organisation Exchange 2007 existante.<br/>- Déplacez les services et autres infrastructures vers Exchange 2013.<br/>- Déplacer des boîtes aux lettres et des dossiers publics vers Exchange 2013.<br/>- Désaffecter les serveurs Exchange 2007.<br/>- Installez Exchange 2016 dans votre organisation Exchange 2013 existante.<br/>- Déplacer des boîtes aux lettres, des dossiers publics, des services et d’autres infrastructures vers Exchange 2016 (l’ordre n’a pas d’importance). Désaffecter les Exchange serveurs 2013.<br/><br/> **Remarque :** La migration de Exchange 2013 vers Exchange 2016 est simple. Les deux versions ont presque la même configuration matérielle requise, et ces versions sont très compatibles. Vous pouvez donc reconstruire un serveur que vous avez acheté Exchange 2013 et installer Exchange 2016 dessus. Pour les déplacements de boîtes aux lettres en ligne, la plupart des utilisateurs ne remarqueront même pas que leur boîte aux lettres a été déplacée hors du serveur, puis de nouveau après l’avoir reconstruite avec Exchange 2016.           |
|Coexistence de version  <br/> | Lors de la migration vers...  <br/> **Exchange 2016** : Exchange 2016 ne peut pas être installé dans une organisation qui inclut un serveur Exchange 2007. Vous devez d’abord migrer vers Exchange 2010 ou 2013 (nous vous recommandons vivement Exchange 2013), supprimer tous les serveurs Exchange 2007, puis migrer vers Exchange 2016.  <br/> **Exchange 2010 ou Exchange 2013 :** Vous pouvez installer Exchange 2010 ou Exchange 2013 dans une organisation Exchange 2007 existante. Cela vous permet d’installer un ou Exchange serveurs 2010 ou 2013 et d’effectuer votre migration.  <br/> |
|Matériel serveur  <br/> | La configuration matérielle requise pour le serveur Exchange 2007. Assurez-vous que votre matériel est compatible. Pour obtenir des informations détaillées, voir :  <br/> [Exchange system requirements 2016](/Exchange/plan-and-deploy/system-requirements) <br/> [Exchange system requirements 2013](/exchange/exchange-2013-system-requirements-exchange-2013-help) <br/> [Exchange system requirements 2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141)) <br/>  Vous verrez que les améliorations significatives des performances de Exchange et l’augmentation de la puissance informatique et de la capacité de stockage sur les serveurs plus nouveaux signifient que vous aurez probablement besoin de moins de serveurs pour prendre en charge le même nombre de boîtes aux lettres.  <br/> |
|Version du système d'exploitation  <br/> | Les versions minimales de système d’exploitation pris en charge pour chaque version sont les :  <br/> **Exchange 2016** - Windows Server 2012  <br/> **Exchange 2013** - Windows Server 2008 R2 SP1  <br/> **Exchange 2010** - Windows Server 2008 SP2  <br/>  Pour plus d’informations sur la prise en charge du système [d’exploitation, Exchange Matrice de prise en charge.](/Exchange/plan-and-deploy/supportability-matrix)  <br/> |
|Niveau fonctionnel de la forêt Active Directory  <br/> | Les niveaux fonctionnels minimaux de forêt Active Directory pris en charge pour chaque version sont :  <br/> **Exchange 2016** Windows Server 2008 R2 SP1  <br/> **Exchange 2013** Windows Server 2003  <br/> **Exchange 2010** Windows Server 2003  <br/>  Pour plus d’informations sur la prise en charge du niveau fonctionnel de la forêt, [voir Exchange Supportability Matrix](/Exchange/plan-and-deploy/supportability-matrix).  <br/> |
|Office versions clientes  <br/> | Les versions minimales Office client pour chaque version sont les Office les plus récentes :  <br/> **Exchange 2016** - Office 2010 (avec les dernières mises à jour)  <br/> **Exchange 2013** - Office 2007 SP3  <br/> **Exchange 2010** - Office 2003  <br/>  Pour plus d’informations sur Office prise en charge du client, [voir Exchange Matrice de prise en charge.](/Exchange/plan-and-deploy/supportability-matrix)  <br/> |
   
#### <a name="how-do-i-migrate"></a>Comment migrer ?

Si vous avez décidé de conserver votre courrier électronique en local, utilisez les ressources suivantes pour faciliter votre migration :
  
- [Exchange Assistant de déploiement](/exchange/exchange-deployment-assistant)
    
- Modifications apportées au schéma Active Directory Exchange [2016,](/Exchange/plan-and-deploy/active-directory/ad-schema-changes) [2013](/exchange/exchange-2013-active-directory-schema-changes-exchange-2013-help)et [2010](https://www.microsoft.com/download/en/details.aspx?displaylang=en&amp;id=5401)
    
- System requirements for Exchange [2016](/Exchange/plan-and-deploy/system-requirements), [2013](/exchange/exchange-2013-system-requirements-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/aa996719(v=exchg.141))
    
- Conditions préalables Exchange [2016](/Exchange/plan-and-deploy/prerequisites), [2013](/exchange/exchange-2013-prerequisites-exchange-2013-help), [2010](/previous-versions/office/exchange-server-2010/bb691354(v=exchg.141))
    
## <a name="get-help"></a>Obtenir de l’aide

Si vous migrez vers Microsoft 365, vous pouvez utiliser notre service Microsoft FastTrack. FastTrack fournit les meilleures pratiques, outils et ressources pour rendre votre migration vers Microsoft 365 aussi transparente que possible. Mieux encore, un ingénieur du support technique vous aidera tout au long de votre migration, de la planification et de la conception jusqu’à la migration de votre dernière boîte aux lettres. Pour plus d’informations FastTrack, voir [Microsoft FastTrack](https://fasttrack.microsoft.com/).
  
Si vous avez des problèmes lors de votre migration vers Microsoft 365 et que vous n’utilisez pas FastTrack ou votre migration vers une version plus récente de Exchange Server, nous sommes là pour vous aider. Voici quelques ressources que vous pouvez utiliser :
  
- [Communauté technique](https://social.technet.microsoft.com/Forums/office/home?category=exchangeserver)
    
- [Support client](https://support.microsoft.com/gp/support-options-for-business)
    
## <a name="related-topics"></a>Rubriques connexes

[Ressources pour vous aider à mettre à niveau Office serveurs et clients 2007](upgrade-from-office-2007-servers-and-products.md)