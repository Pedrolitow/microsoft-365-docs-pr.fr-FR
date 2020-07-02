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
localization_priority: Priority
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 9fa2539a-2211-41fd-85a0-bc37b9619ca4
description: Découvrez comment renforcer la sécurité de votre organisation contre les attaques par mot de passe et la raison pour laquelle vous devez interdire les mots de passe courants et activer l’authentification multifacteur basée sur le risque.
ms.openlocfilehash: 1d6e399acb83751ec6a45eb0c811dedec394127e
ms.sourcegitcommit: 0650da0e54a2b484a3156b3aabe44397fbb38e00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "45015922"
---
# <a name="password-policy-recommendations"></a>Recommandations en matière de stratégie de mot de passe
 
En tant qu’administrateur d’une organisation, vous êtes chargé de la configuration d'une stratégie de mot de passe pour les utilisateurs au sein de votre organisation. La configuration d'une stratégie de mot de passe peut être complexe et déconcertante. Cet article vous fournit des recommandations pour renforcer la sécurité de votre organisation contre les attaques par mot de passe.
  
Pour déterminer la fréquence d’expiration des mots de passe Microsoft 365 dans votre organisation, consultez la page [Définir une stratégie d’expiration de mot de passe pour Microsoft 365](../manage/set-password-expiration-policy.md).

Pour obtenir plus d’informations sur les mots de passe Microsoft 365, consultez ces [articles connexes](#related-articles).
  
## <a name="understanding-password-recommendations"></a>Présentation des recommandations concernant les mots de passe

Les pratiques pour mot de passe recommandées sont classées en plusieurs catégories :
  
- **Résistance aux attaques courantes** il s’agit du choix de l’emplacement dans lequel les utilisateurs entrent les mots de passe (les appareils connus et fiables ayant une bonne détection de programmes malveillants, sites validés) et le choix du mot de passe à adopter (longueur et unicité).

- **Contenir les attaques fructueuses** la résistance aux attaques réussies de pirates informatiques consiste à limiter l’exposition à un service précis ou à empêcher les dommages purs et simples, si le mot de passe d’un utilisateur est volé. Par exemple, s’assurer qu’une violation de vos informations d’identification de réseaux sociaux ne rende pas votre compte bancaire vulnérable, ou ne pas laisser un compte peu protégé accepter des liens de réinitialisation pour un compte important.

- **Comprendre la nature humaine** de nombreuses pratiques valides en matière de mot de passe échouent face à des comportements humains naturels. Une compréhension de la nature humaine est essentielle, car les recherches démontrent que pratiquement toutes les règles que vous imposez à vos utilisateurs entraînent une fragilisation de la qualité des mots de passe. Les exigences de longueur, de caractères spéciaux et de modification du mot de passe entraînent une normalisation des mots de passe, ce qui permet aux pirates informatiques de deviner ou de déchiffrer les mots de passe plus facilement.

## <a name="password-guidelines-for-administrators"></a>Conseils relatifs aux mots de passe pour les administrateurs

La diversité des mots de passe représente l’objectif principal d’un système de mot de passe sécurisé. Votre stratégie de mot de doit contenir de nombreux mots de passe différents qui sont de plus difficiles à deviner. Voici quelques recommandations pour garantir la sécurité de votre organisation.
  
- Conserver une exigence de longueur minimale de 8 caractères (une longueur supérieure n'est pas forcément recommandable)

- N'exigez pas de composition de caractères. For exemple, \*&amp;(^%$

- Ne demandez pas la réinitialisation de mot de passe régulière obligatoire pour les comptes utilisateur

- Interdisez les mots de passe communs pour empêcher les mots de passe vulnérables d'envahir votre système

- Informez vos utilisateurs pour qu'ils ne réutilisent pas leur mot de passe d'organisation à des fins autres que professionnelles

- Renforcer l'Inscription des utilisateurs au service d'[authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md)

- Autoriser les enjeux liés à l’authentification multifacteur basée sur le risque

### <a name="password-guidance-for-your-users"></a>Conseils liés aux mots de passe pour vos utilisateurs

Voici quelques conseils sur les mots de passe destinés aux utilisateurs de votre organisation. Assurez-vous d'informer vos utilisateurs sur ces recommandations et d'appliquer les stratégies de mot de passe recommandées au niveau de l’organisation.
  
- N’utilisez pas de mot de passe identique ou similaire à celui utilisé sur d’autres sites web

- N’utilisez pas de mot unique (par exemple, **code**ou une expression couramment utilisée de type**jetaime)**

- Veillez à ce que les mots de passe soient difficiles à deviner, même par des personnes qui vous connaissent bien, telles que les noms et les anniversaires de vos amis et de votre famille, vos groupes préférés et les phrases que vous aimez utiliser

## <a name="some-common-approaches-and-their-negative-impacts"></a>Approches courantes et leurs répercussions négatives

Voici quelques-unes des pratiques les plus couramment utilisées en matière de gestion des mots de passe, bien que des recherches nous avertissent de leurs conséquences négatives.
  
### <a name="password-expiration-requirements-for-users"></a>Exigences d’expiration du mot de passe pour les utilisateurs

Les conditions d’expiration du mot de passe sont plus néfastes que bénéfiques, car elles permettent aux utilisateurs de sélectionner des mots de passe sans surprise, composés de mots et de chiffres à caractère séquentiel très liés entre eux. Dans ce cas, le mot de passe suivant peut être déterminé en se basant sur le mot de passe précédent. Les exigences en matière d’expiration de mot de passe ne présentent aucun avantage de confinement, car les cybercriminels utilisent pratiquement toujours les informations d’identification dès qu’ils les compromettent.
  
### <a name="requiring-long-passwords"></a>Exigence de mots de passe longs

Les exigences de longueur de mot de passe (plus de 10 caractères environ) peuvent entraîner un comportement utilisateur prévisible et non souhaitable. Par exemple, il est possible que les utilisateurs devant utiliser un mot de passe de 16 caractères choisissent de répéter des modèles tels que **quatrequatrequatre** ou **motdepassemotdepasse** qui respectent les exigences de longueur de caractères, mais qui sont faciles à deviner. De plus, les exigences de longueur augmentent les risques d’adoption par les utilisateurs d’autres méthodes non sécurisées, telles que l’écriture sur papier de leurs mots de passe, leur réutilisation ou leur stockage non chiffré dans leurs documents. Pour inciter les utilisateurs à considérer un mot de passe unique, nous vous recommandons de conserver une exigence raisonnable d'une longueur minimale de 8 caractères. 
  
### <a name="requiring-the-use-of-multiple-character-sets"></a>Nécessité d’utiliser plusieurs jeux de caractères

L'exigence de complexité de mots de passe permet de réduire l’espace de clé et d'amener les utilisateurs à agir de façon prévisible, faisant ainsi plus de mal que de bien. La plupart des systèmes appliquent des exigences de complexité des mots de passe d'un certain niveau. Par exemple, les mots de passe doivent contenir des caractères faisant partie des trois catégories suivantes :
  
- caractères majuscules

- caractères minuscules

- caractères non alphanumériques

Beaucoup de personnes utilisent des modèles similaires par exemple, une lettre majuscule en premier, un symbole en dernier et un nombre dans les deux derniers caractères. Les cybercriminels le savent, de sorte qu’ils exécutent leurs attaques de dictionnaire en utilisant les substitutions les plus courantes, « $ » pour « s », « @ » pour « a », « 1 » pour « l ». Le fait de contraindre vos utilisateurs à choisir une combinaison de majuscules, minuscules et caractères spéciaux a une incidence négative. Certaines exigences de complexité empêchent également les utilisateurs d’utiliser des mots de passe sécurisés et mémorables, et de les contraint à faire usage de mots de passe moins sécurisés et moins marquants.
  
## <a name="successful-patterns"></a>Modèles performants

En revanche, voici quelques recommandations favorisant une variété des mots de passe.
  
### <a name="ban-common-passwords"></a>Interdire les mots de passe courants

L’exigence de mot de passe la plus importante à imposer à vos utilisateurs lors de la création de mots de passe consiste à interdire l’utilisation de mots de passe communs afin de limiter la vulnérabilité de votre organisation aux attaques de mot de passe par force brute. Les mots de passe utilisateur courants incluent **abdcefg**, **motdepasse** et **singe**.
  
### <a name="educate-users-to-not-re-use-organization-passwords-anywhere-else"></a>Apprenez à vos utilisateurs à ne pas réutiliser ailleurs les mots de passe d’organisation

L’un des plus importants messages à faire passer auprès des utilisateurs de votre organisation est de ne pas réutiliser autre part leur mot de passe d’organisation. L’utilisation de mots de passe d’organisation sur des sites web externes augmente considérablement la probabilité de compromission de ces mots de passe par des cybercriminels.
  
### <a name="enforce-multi-factor-authentication-registration"></a>Imposer l'inscription avec service d'authentification multifacteur

Veillez à ce que les utilisateurs mettent à jour leurs informations de sécurité et de contact, telles que l'adresse e-mail secondaire, le numéro de téléphone ou l'appareil enregistré pour les services de notifications Push afin qu'ils puissent répondre aux questions challenges et être informés des évènements de sécurité. Les informations de contact et de sécurité mises à jour permettent aux utilisateurs de vérifier leur identité en cas d'oubli de leur mot de passe, ou si un autre utilisateur tente de prendre le contrôle de leur compte. Elles fournissent en outre un canal de notification de type hors plage en cas d'évènements de sécurité, tels que des tentatives de connexion ou des modifications de mots de passe. 
  
Pour plus d'informations, voir [Configurer l'authentification multifacteur](../security-and-compliance/set-up-multi-factor-authentication.md).
  
### <a name="enable-risk-based-multi-factor-authentication"></a>Activer le service d'authentification multifacteur basé sur le risque

L’authentification multifacteur basée sur le risque s'assure que, lorsque notre système détecte une activité suspecte, il peut défier l’utilisateur pour s’assurer qu’il s’agit bien du propriétaire du compte. 
  
## <a name="want-to-know-more-recommended-reading"></a>Vous souhaitez en savoir plus ? Lecture recommandée

- [Les mots de passe web sont-ils performants ?](https://go.microsoft.com/fwlink/p/?linkid=861008)

- [Portefeuilles de mots de passe et utilisateur à effort limité](https://go.microsoft.com/fwlink/p/?linkid=861014)

- [Prévenir les mots de passe vulnérables en lisant dans les pensées de l'utilisateur](https://go.microsoft.com/fwlink/p/?linkid=861015)

- [Choix de mots de passe sécurisés](https://go.microsoft.com/fwlink/p/?linkid=861016)

- [L'heure est venue de reconsidérer les changement de mots de passe obligatoires](https://go.microsoft.com/fwlink/p/?linkid=861018)

- [Plus mauvais mots de passe en 2015](https://go.microsoft.com/fwlink/p/?linkid=861020)

- [Télécharger des fichiers sur le web](https://go.microsoft.com/fwlink/p/?linkid=861029)

## <a name="related-articles"></a>Articles connexes

[Réinitialiser les mots de passe](https://docs.microsoft.com/microsoft-365/admin/add-users/reset-passwords)

[Définir le mot de passe d’un utilisateur de façon à ce qu’il n’expire jamais](https://docs.microsoft.com/microsoft-365/admin/add-users/set-password-to-never-expire)

[Autoriser les utilisateurs à réinitialiser leur mot de passe](https://docs.microsoft.com/microsoft-365/admin/add-users/let-users-reset-passwords)

[Renvoyer le mot de passe d’un utilisateur – Aide de l’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/resend-user-password)
