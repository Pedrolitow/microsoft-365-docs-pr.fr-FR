---
title: Préparer la synchronisation d'annuaires pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment préparer la mise en service des utilisateurs Microsoft 365 l’aide de la synchronisation d’annuaires et les avantages à long terme de l’utilisation de cette méthode.
ms.openlocfilehash: 389f0ca682538baed21432220c16ad7cb269daa0
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209210"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Préparer la synchronisation d'annuaires pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les avantages de la synchronisation d’annuaires et de l’identité hybride de votre organisation sont les suivants :

- Réduction des programmes d’administration dans votre organisation
- Activation facultative du scénario d' sign-on unique
- Automatisation des modifications de compte dans Microsoft 365

Pour plus d’informations sur les avantages de l’utilisation de la synchronisation d’annuaires, voir identité hybride avec [Azure Active Directory (Azure AD)](/azure/active-directory/hybrid/whatis-hybrid-identity) et identité hybride pour [Microsoft 365](plan-for-directory-synchronization.md).

Toutefois, la synchronisation d’annuaires nécessite une planification et une préparation pour vous assurer que vos services de domaine Active Directory (AD DS) se synchronisent avec le client Azure AD de votre abonnement Microsoft 365 avec un minimum d’erreurs.

Suivez ces étapes pour obtenir les meilleurs résultats.

## <a name="1-directory-cleanup-tasks"></a>1. Tâches de nettoyage de l’annuaire

Avant de synchroniser vos AD DS avec votre client Azure AD, vous devez nettoyer vos AD DS.

> [!IMPORTANT]
> Si vous n’effectuez pas de nettoyage AD DS avant la synchronisation, cela peut entraîner un impact négatif significatif sur le processus de déploiement. Le cycle de synchronisation d’annuaires, d’identification des erreurs et de resynchronisation peut prendre des jours, voire des semaines.

Dans vos AD DS, effectuer les tâches de nettoyage suivantes pour chaque compte d’utilisateur à qui une licence Microsoft 365 attribuée :

1. Assurez-vous qu’il s’agit d’une adresse de messagerie valide et unique dans **l’attribut proxyAddresses.**

2. Supprimez les valeurs en double dans **l’attribut proxyAddresses.**

3. Si possible, assurez-vous d’une valeur valide et unique pour l’attribut **userPrincipalName** dans l’objet utilisateur de **l’utilisateur.** Pour une meilleure expérience de synchronisation, assurez-vous que l’UPN AD DS correspond à l’UPN Azure AD. Si un utilisateur n’a pas de valeur pour l’attribut **userPrincipalName,** l’objet utilisateur doit contenir une valeur valide et unique pour l’attribut **sAMAccountName.**  Supprimez les valeurs dupliquées dans **l’attribut userPrincipalName.**

4. Pour une utilisation optimale de la liste d’adresses globale(LAL), assurez-vous que les informations des attributs suivants du compte d’utilisateur AD DS sont correctes :

   - givenName
   - surname
   - displayName
   - Fonction
   - Service
   - Bureau
   - Téléphone (bureau)
   - Téléphone mobile
   - Numéro de télécopie
   - Rue
   - Ville
   - Département ou région
   - Code postal
   - Pays ou région

## <a name="2-directory-object-and-attribute-preparation"></a>2. Préparation de l’objet directory et des attributs

Une synchronisation d’annuaires réussie entre vos services AD DS et Microsoft 365 exige que vos attributs AD DS soient correctement préparés. Par exemple, vous devez vous assurer que des caractères spécifiques ne sont pas utilisés dans certains attributs synchronisés avec l’environnement Microsoft 365 de sécurité. Les caractères inattendus n’entraînent pas l’échec de la synchronisation d’annuaires, mais peuvent renvoyer un avertissement. Les caractères non valides entraînent l’échec de la synchronisation d’annuaires.

La synchronisation d’annuaires échoue également si certains de vos utilisateurs AD DS ont un ou plusieurs attributs en double. Chaque utilisateur doit avoir des attributs uniques.

Les attributs que vous devez préparer sont répertoriés ici :

- **displayName**

  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Microsoft 365.
  - Si cet attribut existe dans l’objet utilisateur, il doit y avoir une valeur pour celui-ci. Autrement dit, l’attribut ne doit pas être vide.
  - Nombre maximal de caractères : 256

- **givenName**

  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Microsoft 365, mais Microsoft 365 ne l’exige pas ou ne l’utilise pas.
  - Nombre maximal de caractères : 64

- **mail**

  - La valeur d’attribut doit être unique dans le répertoire.

    > [!NOTE]
    > S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé. Les utilisateurs suivants n’apparaîtront pas dans Microsoft 365. Vous devez modifier la valeur dans Microsoft 365 ou modifier les deux valeurs dans AD DS afin que les deux utilisateurs apparaissent dans Microsoft 365.

- **mailNickname** (Exchange alias)

  - La valeur d’attribut ne peut pas commencer par un point (.).
  - La valeur d’attribut doit être unique dans le répertoire.

    > [!NOTE]
    > Les traits de soulignement (« _ ») dans le nom synchronisé indiquent que la valeur d’origine de cet attribut contient des caractères non valides. Pour plus d’informations sur cet attribut, voir [Exchange’alias.](/powershell/module/exchange/set-mailbox)
    >

- **proxyAddresses**

  - Attribut à valeurs multiples
  - Nombre maximal de caractères par valeur : 256
  - La valeur d’attribut ne doit pas contenir d’espace.
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides \< \> : ( ) ; , [ ] »

    Notez que les caractères non valides s’appliquent aux caractères qui suivent le délimiteur de type et « : », de telle sorte que SMTP:User@contso.com est autorisé, SMTP:user:M@contoso.com’est pas le cas.

    > [!IMPORTANT]
    > Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent être conformes aux normes de messagerie électronique. Supprimez les adresses en double ou indésirables si elles existent.

- **sAMAccountName**

  - Nombre maximal de caractère : 20
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides : [ \ " | , / : \< \> + = ; ? \* ']
  - Si un utilisateur possède un attribut **sAMAccountName** non valide mais un attribut **userPrincipalName** valide, le compte d’utilisateur est créé dans Microsoft 365.
  - Si **sAMAccountName** et **userPrincipalName** ne sont pas valides, l’attribut **userPrincipalName** AD DS doit être mis à jour.

- **sn** (surname)

  - Si l’attribut existe dans l’objet utilisateur, il sera synchronisé avec Microsoft 365, mais Microsoft 365 ne l’exige pas ou ne l’utilise pas.

- **targetAddress**

    Il est nécessaire que l’attribut **targetAddress** (par exemple, SMTP:tom@contoso.com) qui est rempli pour l’utilisateur apparaisse dans la Microsoft 365 LAL. Dans les scénarios de migration de messagerie tiers, cela nécessite l’extension Microsoft 365 schéma pour les services AD DS. L Microsoft 365 d’extension de schéma ajoute également d’autres attributs utiles pour gérer les objets Microsoft 365 qui sont remplis à l’aide d’un outil de synchronisation d’annuaires à partir d’AD DS. Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution est ajouté.

  - Nombre maximal de caractères : 256
  - La valeur d’attribut ne doit pas contenir d’espace.
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides : \ \< \> ( ) ; , [ ] »
  - Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent être conformes aux normes de messagerie électronique.

- **userPrincipalName**

  - L’attribut **userPrincipalName** doit être au format de connexion de style Internet où le nom d’utilisateur est suivi du signe at (@) et d’un nom de domaine : par exemple, user@contoso.com. Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent être conformes aux normes de messagerie électronique.
  - Le nombre maximal de caractères pour **l’attribut userPrincipalName** est 113. Un nombre spécifique de caractères est autorisé avant et après le signe at (@), comme suit :
  - Nombre maximal de caractères pour le nom d’utilisateur devant le signe at (@) : 64
  - Nombre maximal de caractères pour le nom de domaine suivant le signe at (@) : 48
  - Caractères non valides : \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Caractères autorisés : A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Les lettres avec des marques diacritiques, telles que les umlauts, les accents et les tildes, sont des caractères non valides.
  - Le caractère @ est requis dans chaque **valeur userPrincipalName.**
  - Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName**.
  - Le nom d’utilisateur ne peut pas se terminer par un point (.), une eterr e ( ), un espace ou un &amp; signe at (@).
  - Le nom d’utilisateur ne peut pas contenir d’espaces.
  - Les domaines routables doivent être utilisés ; par exemple, les domaines locaux ou internes ne peuvent pas être utilisés.
  - Unicode est converti en caractères de trait de soulignement.
  - **userPrincipalName ne** peut pas contenir de valeurs en double dans le répertoire.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Préparer l’attribut userPrincipalName

Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation de se connectent à votre annuaire à l’aide de **sAMAccountName** ou **userPrincipalName**. De même, les utilisateurs finaux peuvent se Microsoft 365 à l’aide du nom d’utilisateur principal (UPN) de leur compte scolaire ou scolaire. La synchronisation d’annuaires tente de créer des utilisateurs dans Azure Active Directory à l’aide du même UPN que celui de vos services AD DS. L’UPN est mis en forme comme une adresse de messagerie.

Dans Microsoft 365, l’UPN est l’attribut par défaut utilisé pour générer l’adresse e-mail. Il est facile d’obtenir **userPrincipalName** (dans AD DS et dans Azure AD) et l’adresse de messagerie principale dans **proxyAddresses** définie sur différentes valeurs. Lorsqu’elles sont définies sur des valeurs différentes, il peut y avoir de la confusion pour les administrateurs et les utilisateurs finaux.

Il est préférable d’aligner ces attributs pour réduire la confusion. Pour répondre aux exigences de l' sign-on unique avec active Directory Federation Services (AD FS) 2.0, vous devez vous assurer que les UPN dans Azure Active Directory et vos services AD DS correspondent et utilisent un espace de noms de domaine valide.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Ajouter un autre suffixe UPN à AD DS

Vous devrez peut-être ajouter un autre suffixe UPN pour associer les informations d’identification d’entreprise de l’utilisateur à Microsoft 365'environnement. Un suffixe UPN est la partie d’un UPN située à droite du caractère @. Les UPN qui sont utilisés pour l’authentification unique peuvent contenir des lettres, des chiffres, des points, des traits d’unions et des traits de soulignement, mais aucun autre type de caractère.

Pour plus d’informations sur l’ajout d’un autre suffixe UPN à Active Directory, voir Préparer la synchronisation [d’annuaires.](https://go.microsoft.com/fwlink/p/?LinkId=525430)

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Faire correspondre l’UPN AD DS avec le Microsoft 365 UPN

Si vous avez déjà défini la synchronisation d’annuaires, il se peut que l’UPN de l’utilisateur pour Microsoft 365 ne corresponde pas à l’UPN AD DS de l’utilisateur défini dans vos services AD DS. Cela peut se produire lorsqu’un utilisateur obtient une licence avant la vérification du domaine. Pour résoudre ce problème, utilisez PowerShell pour corriger le nom d’utilisateur [upn](https://go.microsoft.com/fwlink/p/?LinkId=396730) en double afin de mettre à jour l’UPN de l’utilisateur pour vous assurer que l’UPN Microsoft 365 correspond au nom d’utilisateur et au domaine de l’entreprise. Si vous actualisez l’UPN dans les AD DS et souhaitez qu’il se synchronise avec l’identité Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Microsoft 365 avant d’apporter les modifications dans AD DS.

Voir également comment préparer un domaine non routable (tel que le domaine [.local) pour la synchronisation d’annuaires.](prepare-a-non-routable-domain-for-directory-synchronization.md)

## <a name="next-steps"></a>Étapes suivantes

Si vous avez effectué les étapes 1 à 5 ci-dessus, voir [Configurer la synchronisation d’annuaires.](set-up-directory-synchronization.md)
