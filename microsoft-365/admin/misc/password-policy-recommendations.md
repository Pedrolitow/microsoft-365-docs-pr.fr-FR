---
title: Recommandations en matière de stratégie de mot de passe
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9fa2539a-2211-41fd-85a0-bc37b9619ca4
description: Sécuriser votre organisation contre les attaques par mot de passe, et interdire les mots de passe courants et activer l’authentification multifacteur basée sur les risques.
ms.openlocfilehash: 782d2066fba52a5135c32987d8d32824b8a97be0
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67087086"
---
# <a name="password-policy-recommendations-for-microsoft-365-passwords"></a>Recommandations en matière de stratégie de mot de passe pour Microsoft 365

En tant qu’administrateur d’une organisation, vous êtes chargé de la configuration d'une stratégie de mot de passe pour les utilisateurs au sein de votre organisation. La configuration d'une stratégie de mot de passe peut être complexe et déconcertante. Cet article vous fournit des recommandations pour renforcer la sécurité de votre organisation contre les attaques par mot de passe.

Les comptes Microsoft cloud uniquement ont une stratégie de mot de passe prédéfinie qui ne peut pas être modifiée. Les seuls éléments que vous pouvez modifier sont le nombre de jours avant l’expiration d’un mot de passe et l’expiration ou non des mots de passe. 
  
Pour déterminer la fréquence d’expiration des mots de passe Microsoft 365 dans votre organisation, consultez la page [Définir une stratégie d’expiration de mot de passe pour Microsoft 365](../manage/set-password-expiration-policy.md).

Pour obtenir plus d’informations sur les mots de passe Microsoft 365, consultez :

[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)

[Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais](../add-users/set-password-to-never-expire.md) (article)

[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)

[Renvoyer le mot de passe d’un utilisateur – Aide de l’administrateur](../add-users/resend-user-password.md) (article)
  
## <a name="understanding-password-recommendations"></a>Présentation des recommandations concernant les mots de passe

Les pratiques pour mot de passe recommandées sont classées en plusieurs catégories :
  
- **Résistance aux attaques courantes** il s’agit du choix de l’emplacement dans lequel les utilisateurs entrent les mots de passe (les appareils connus et fiables ayant une bonne détection de programmes malveillants, sites validés) et le choix du mot de passe à adopter (longueur et unicité).

- **Contenir les attaques fructueuses** la résistance aux attaques réussies de pirates informatiques consiste à limiter l’exposition à un service précis ou à empêcher les dommages purs et simples, si le mot de passe d’un utilisateur est volé. Par exemple, s’assurer qu’une violation de vos informations d’identification de réseaux sociaux ne rende pas votre compte bancaire vulnérable, ou ne pas laisser un compte peu protégé accepter des liens de réinitialisation pour un compte important.

- **Comprendre la nature humaine** de nombreuses pratiques valides en matière de mot de passe échouent face à des comportements humains naturels. Une compréhension de la nature humaine est essentielle, car les recherches démontrent que pratiquement toutes les règles que vous imposez à vos utilisateurs entraînent une fragilisation de la qualité des mots de passe. Les exigences de longueur, de caractères spéciaux et de modification du mot de passe entraînent une normalisation des mots de passe, ce qui permet aux pirates informatiques de deviner ou de déchiffrer les mots de passe plus facilement.

## <a name="password-guidelines-for-administrators"></a>Conseils relatifs aux mots de passe pour les administrateurs

La diversité des mots de passe représente l’objectif principal d’un système de mot de passe sécurisé. Votre stratégie de mot de doit contenir de nombreux mots de passe différents qui sont de plus difficiles à deviner. Voici quelques recommandations pour garantir la sécurité de votre organisation.
  

- Appliquer une exigence de longueur minimale de huit caractères

- N'exigez pas de composition de caractères. For exemple, \*&amp;(^%$

- Ne demandez pas la réinitialisation de mot de passe régulière obligatoire pour les comptes utilisateur

- Interdisez les mots de passe communs pour empêcher les mots de passe vulnérables d'envahir votre système

- Former vos utilisateurs à ne pas réutiliser les mots de passe de leur organisation à des fins non professionnelles

- Renforcer l'Inscription des utilisateurs au service d'[authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md)

- Autoriser les enjeux liés à l’authentification multifacteur basée sur le risque

### <a name="password-guidance-for-your-users"></a>Conseils liés aux mots de passe pour vos utilisateurs

Voici quelques conseils en matière de mots de passe destinés aux utilisateurs de votre organisation. Assurez-vous d'informer vos utilisateurs sur ces recommandations et d'appliquer les stratégies de mot de passe recommandées au niveau de l’organisation.
  
- N’utilisez pas de mot de passe identique ou similaire à celui utilisé sur d’autres sites web

- N’utilisez pas de mot unique (par exemple, **motdepasse** ou une expression couramment utilisée de type **jetaime)**

- Veillez à ce que les mots de passe soient difficiles à deviner, même par des personnes qui vous connaissent bien, telles que les noms et les anniversaires de vos amis et de votre famille, vos groupes préférés et les phrases que vous aimez utiliser

## <a name="some-common-approaches-and-their-negative-impacts"></a>Approches courantes et leurs répercussions négatives

Voici quelques-unes des pratiques les plus couramment utilisées en matière de gestion des mots de passe, bien que des recherches nous avertissent de leurs conséquences négatives.
  
### <a name="password-expiration-requirements-for-users"></a>Exigences d’expiration du mot de passe pour les utilisateurs

Les exigences d’expiration de mot de passe font plus de mal que de bien, car ces exigences font en sorte que les utilisateurs sélectionnent des mots de passe prévisibles, composés de mots séquentiels et de nombres étroitement liés les uns aux autres. Dans ce cas, le mot de passe suivant peut être déterminé en se basant sur le mot de passe précédent. Les exigences d’expiration de mot de passe n’offrent aucun avantage en matière de contenu, car les cybercriminels utilisent presque toujours les informations d’identification dès qu’ils les compromettent. Pour plus d’informations, consultez [Il est temps de reconsidérer les changements de mots de passe obligatoires](https://go.microsoft.com/fwlink/p/?linkid=861018).
  
### <a name="requiring-long-passwords"></a>Exigence de mots de passe longs

Les exigences de longueur de mot de passe (plus de 10 caractères environ) peuvent entraîner un comportement utilisateur prévisible et non souhaitable. Par exemple, il est possible que les utilisateurs devant utiliser un mot de passe de 16 caractères choisissent de répéter des modèles tels que **quatrequatrequatre** ou **motdepassemotdepasse** qui respectent les exigences de longueur de caractères, mais qui sont faciles à deviner. En outre, les exigences de longueur augmentent les chances que les utilisateurs adoptent d’autres pratiques non sécurisées, telles que l’écriture de leurs mots de passe, leur réutilisation ou leur stockage non chiffré dans leurs documents. Pour inciter les utilisateurs à considérer un mot de passe unique, nous vous recommandons de conserver une exigence raisonnable d'une longueur minimale de 8 caractères.
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Nécessité d’utiliser plusieurs jeux de caractères

L'exigence de complexité de mots de passe permet de réduire l’espace de clé et d'amener les utilisateurs à agir de façon prévisible, faisant ainsi plus de mal que de bien. La plupart des systèmes appliquent des exigences de complexité des mots de passe d'un certain niveau. Par exemple, les mots de passe doivent contenir des caractères faisant partie des trois catégories suivantes :
  
- caractères majuscules

- caractères minuscules

- caractères non alphanumériques

Beaucoup de personnes utilisent des modèles similaires par exemple, une lettre majuscule en premier, un symbole en dernier et un nombre dans les deux derniers caractères. Les cybercriminels le savent. Ils exécutent donc leurs attaques par dictionnaire à l’aide des substitutions les plus courantes, « $ » pour « s », « @ » pour « a », « 1 » pour « l ». Le fait de contraindre vos utilisateurs à choisir une combinaison de majuscules, minuscules et caractères spéciaux a une incidence négative. Certaines exigences de complexité empêchent également les utilisateurs d’utiliser des mots de passe sécurisés et mémorables, et de les contraint à faire usage de mots de passe moins sécurisés et moins marquants.
  
## <a name="successful-patterns"></a>Modèles performants

En revanche, voici quelques recommandations favorisant une variété des mots de passe.
  
### <a name="ban-common-passwords"></a>Interdire les mots de passe courants

L'exigence de mot de passe la plus importante que vous devez imposer à vos utilisateurs lors de la création de mots de passe est d'interdire l'utilisation de mots de passe courants afin de réduire la susceptibilité de votre organisation aux attaques de mot de passe par force brute. Les mots de passe utilisateur courants incluent : **abcdefg**, **password**, **monkey**.
  
### <a name="educate-users-to-not-reuse-organization-passwords-anywhere-else"></a>Former les utilisateurs à ne pas réutiliser les mots de passe de l’organisation ailleurs

L’un des messages les plus importants à passer aux utilisateurs de votre organisation consiste à ne pas réutiliser leur mot de passe d’organisation ailleurs. L’utilisation de mots de passe d’organisation dans des sites web externes augmente considérablement la probabilité que les cybercriminels compromettent ces mots de passe.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Imposer l'inscription avec service d'authentification multifacteur

Veillez à ce que les utilisateurs mettent à jour leurs informations de sécurité et de contact, telles que l'adresse e-mail secondaire, le numéro de téléphone ou l'appareil enregistré pour les services de notifications Push afin qu'ils puissent répondre aux questions challenges et être informés des évènements de sécurité. Les informations de contact et de sécurité mises à jour permettent aux utilisateurs de vérifier leur identité en cas d'oubli de leur mot de passe, ou si un autre utilisateur tente de prendre le contrôle de leur compte. Elles fournissent en outre un canal de notification de type hors plage en cas d'évènements de sécurité, tels que des tentatives de connexion ou des modifications de mots de passe. 
  
Pour plus d'informations, voir [Configurer l'authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Activer le service d'authentification multifacteur basé sur le risque

L’authentification multifacteur basée sur le risque s'assure que, lorsque notre système détecte une activité suspecte, il peut défier l’utilisateur pour s’assurer qu’il s’agit bien du propriétaire du compte. 
  
## <a name="next-steps"></a>Étapes suivantes

Vous voulez en savoir plus sur la gestion des mots de passe ? Voici quelques recommandations de lecture :

- [Oubliez les mots de passe, passez au sans mot de passe](https://www.microsoft.com/security/business/identity-access-management/passwordless-authentication)

- [Conseils sur les mots de passe Microsoft](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf)

- [Les mots de passe web sont-ils performants ?](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Portefeuilles de mots de passe et utilisateur à effort limité](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Prévenir les mots de passe vulnérables en lisant dans les pensées de l'utilisateur](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Choix de mots de passe sécurisés](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [L'heure est venue de reconsidérer les changement de mots de passe obligatoires](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [Plus mauvais mots de passe en 2015](https://go.microsoft.com/fwlink/p/?linkid=861020)

## <a name="related-content"></a>Contenu associé

[Réinitialiser les mots de passe](../add-users/reset-passwords.md) (article)\
[Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais](../add-users/set-password-to-never-expire.md) (article)\
[Autoriser les utilisateurs à réinitialiser leur mot de passe](../add-users/let-users-reset-passwords.md) (article)\
[Renvoyer le mot de passe d’un utilisateur – Aide de l’administrateur](../add-users/resend-user-password.md) (article)
