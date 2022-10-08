---
title: Préparer la synchronisation d'annuaires pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- scotvorg
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Décrit comment préparer l’approvisionnement d’utilisateurs dans Microsoft 365 à l’aide de la synchronisation d’annuaires et des avantages à long terme de cette méthode.
ms.openlocfilehash: cda02933f0f7da95c27af01497ebbb3ab3b121a7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68188964"
---
# <a name="prepare-for-directory-synchronization-to-microsoft-365"></a>Préparer la synchronisation d'annuaires pour Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez choisi le modèle d’identité hybride et configuré la protection des comptes d’administrateur à [l’étape 2](protect-your-global-administrator-accounts.md) et des comptes d’utilisateur à [l’étape 3](microsoft-365-secure-sign-in.md) de cette solution, votre prochaine tâche consiste à déployer la synchronisation d’annuaires. Les avantages de la synchronisation d’annuaires pour votre organisation sont les suivants :

- Réduction des programmes d’administration dans votre organisation
- Activation éventuelle d’un scénario d’authentification unique
- Automatisation des modifications de compte dans Microsoft 365

Pour plus d’informations sur les avantages de l’utilisation de la synchronisation d’annuaires, consultez [l’identité hybride avec Azure Active Directory (Azure AD).](/azure/active-directory/hybrid/whatis-hybrid-identity)

Toutefois, la synchronisation d’annuaires nécessite une planification et une préparation pour vous assurer que votre services de domaine Active Directory (AD DS) se synchronise avec le locataire Azure AD de votre abonnement Microsoft 365 avec un minimum d’erreurs.

Suivez ces étapes pour obtenir les meilleurs résultats.

> [!NOTE]
> Les caractères non ASCII ne sont synchronisés pour aucun attribut sur le compte d’utilisateur AD DS.

## <a name="ad-ds-preparation"></a>Préparation d’AD DS

Pour garantir une transition transparente vers Microsoft 365 à l’aide de la synchronisation, vous devez préparer votre forêt AD DS avant de commencer votre déploiement de synchronisation d’annuaires Microsoft 365.
  
La préparation de votre répertoire doit se concentrer sur les tâches suivantes :

- Supprimez les attributs **proxyAddress** et **userPrincipalName** en double.
- Mettez à jour les attributs **userPrincipalName** vides et non valides avec des attributs **userPrincipalName** valides.
- Supprimez les caractères non valides et contestables dans les attributs **givenName**, surname ( **sn** ), **sAMAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname** et **userPrincipalName** . Pour plus d’informations sur la préparation des attributs, consultez [La liste des attributs synchronisés par l’outil de synchronisation Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Il s’agit des mêmes attributs qu’Azure AD Connect synchronise. 
  
## <a name="multi-forest-deployment-considerations"></a>Considérations relatives au déploiement de forêts multiples

Pour plusieurs forêts et options d’authentification unique, utilisez une [installation personnalisée d’Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-custom).
  
Si votre organisation dispose de plusieurs forêts pour l’authentification (forêts d’ouverture de session), nous vous recommandons vivement les éléments suivants :
  
- **Envisagez de consolider vos forêts.** En général, il y a plus de surcharge requise pour gérer plusieurs forêts. À moins que votre organisation ne dispose de contraintes de sécurité qui déterminent la nécessité de forêts distinctes, envisagez de simplifier votre environnement local.
- **Utilisez uniquement dans votre forêt d’ouverture de session principale.** Envisagez de déployer Microsoft 365 uniquement dans votre forêt d’ouverture de session principale pour votre déploiement initial de Microsoft 365. 

Si vous ne pouvez pas consolider votre déploiement AD DS multi-forêt ou si vous utilisez d’autres services d’annuaire pour gérer les identités, vous pouvez les synchroniser avec l’aide de Microsoft ou d’un partenaire.
  
Pour plus d’informations, consultez [Topologies pour Azure AD Connect](/azure/active-directory/hybrid/plan-connect-topologies) .
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Fonctionnalités qui dépendent de la synchronisation d’annuaires
  
La synchronisation d’annuaires est requise pour les fonctionnalités et fonctionnalités suivantes :
  
- Azure AD Seamless Single Sign-On (SSO)
- Coexistence de Skype
- Déploiement hybride Exchange, notamment :
  - Liste d’adresses globale (GAL) entièrement partagée entre votre environnement Exchange local et Microsoft 365.
  - Synchronisation des informations GAL provenant de différents systèmes de messagerie.
  - Possibilité d’ajouter et de supprimer des utilisateurs des offres de service Microsoft 365. Cette possibilité nécessite ce qui suit :
  - La synchronisation bidirectionnelle doit être configurée lors de la configuration de la synchronisation d’annuaires. Par défaut, les outils de synchronisation d’annuaires écrivent des informations de répertoire uniquement dans le cloud. Lorsque vous configurez la synchronisation bidirectionnelle, vous activez la fonctionnalité d’écriture différée afin qu’un nombre limité d’attributs d’objet soient copiés à partir du cloud, puis réécrits dans votre service AD DS local. La réécriture est également appelée mode hybride Exchange. 
  - Un déploiement exchange hybride local
  - Possibilité de déplacer certaines boîtes aux lettres utilisateur vers Microsoft 365 tout en conservant d’autres boîtes aux lettres utilisateur en local.
  - Les expéditeurs sécurisés et les expéditeurs bloqués en local sont répliqués vers Microsoft 365.
  - Fonctionnalité de délégation de base et d’envoi de courrier « de la part de ».
  - Vous disposez d’une carte à puce locale intégrée ou d’une solution d’authentification multifacteur.
- Synchronisation de photos, miniatures, salles de conférence et groupes de sécurité

## <a name="1-directory-cleanup-tasks"></a>1. Tâches de nettoyage d’annuaire

Avant de synchroniser votre service AD DS avec votre locataire Azure AD, vous devez nettoyer votre service AD DS.

> [!IMPORTANT]
> Si vous n’effectuez pas de nettoyage AD DS avant la synchronisation, cela peut entraîner un impact négatif significatif sur le processus de déploiement. Le cycle de synchronisation d’annuaires, l’identification des erreurs et la re-synchronisation peuvent prendre des jours, voire des semaines.

Dans votre service AD DS, effectuez les tâches de nettoyage suivantes pour chaque compte d’utilisateur auquel une licence Microsoft 365 sera attribuée :

1. Vérifiez une adresse e-mail valide et unique dans l’attribut **proxyAddresses** .

2. Supprimez toutes les valeurs dupliquées dans l’attribut **proxyAddresses** .

3. Si possible, vérifiez une valeur valide et unique pour **l’attribut userPrincipalName** dans l’objet **utilisateur de l’utilisateur** . Pour une expérience de synchronisation optimale, assurez-vous que l’UPN AD DS correspond à l’UPN Azure AD. Si un utilisateur n’a pas de valeur pour l’attribut **userPrincipalName** , l’objet **utilisateur** doit contenir une valeur valide et unique pour **l’attribut sAMAccountName** . Supprimez toutes les valeurs dupliquées dans **l’attribut userPrincipalName** .

4. Pour une utilisation optimale de la liste d’adresses globale (GAL), vérifiez que les informations contenues dans les attributs suivants du compte d’utilisateur AD DS sont correctes :

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

## <a name="2-directory-object-and-attribute-preparation"></a>2. Préparation de l’objet directory et de l’attribut

La synchronisation d’annuaires réussie entre votre AD DS et Microsoft 365 nécessite que vos attributs AD DS soient correctement préparés. Par exemple, vous devez vous assurer que des caractères spécifiques ne sont pas utilisés dans certains attributs synchronisés avec l’environnement Microsoft 365. Les caractères inattendus ne provoquent pas l’échec de la synchronisation d’annuaires, mais peuvent retourner un avertissement. Des caractères non valides entraînent l’échec de la synchronisation d’annuaires.

La synchronisation d’annuaires échoue également si certains de vos utilisateurs AD DS ont un ou plusieurs attributs en double. Chaque utilisateur doit avoir des attributs uniques.

Les attributs que vous devez préparer sont répertoriés ici :

- **displayName**

  - Si l’attribut existe dans l’objet utilisateur, il est synchronisé avec Microsoft 365.
  - Si cet attribut existe dans l’objet utilisateur, il doit y avoir une valeur pour celui-ci. Autrement dit, l’attribut ne doit pas être vide.
  - Nombre maximal de caractères : 256

- **givenName**

  - Si l’attribut existe dans l’objet utilisateur, il est synchronisé avec Microsoft 365, mais Microsoft 365 n’en a pas besoin ni ne l’utilise.
  - Nombre maximal de caractères : 64

- **mail**

  - La valeur d’attribut doit être unique dans le répertoire.

    > [!NOTE]
    > S’il existe des valeurs en double, le premier utilisateur avec la valeur est synchronisé. Les utilisateurs suivants n’apparaîtront pas dans Microsoft 365. Vous devez modifier la valeur dans Microsoft 365 ou modifier les deux valeurs dans AD DS pour que les deux utilisateurs apparaissent dans Microsoft 365.

- **mailNickname** (alias Exchange)

  - La valeur d’attribut ne peut pas commencer par un point (.).
  - La valeur d’attribut doit être unique dans le répertoire.

    > [!NOTE]
    > Les traits de soulignement (« _ ») dans le nom synchronisé indiquent que la valeur d’origine de cet attribut contient des caractères non valides. Pour plus d’informations sur cet attribut, consultez [l’attribut d’alias Exchange](/powershell/module/exchange/set-mailbox).
    >

- **proxyAddresses**

  - Attribut à valeurs multiples
  - Nombre maximal de caractères par valeur : 256
  - La valeur d’attribut ne doit pas contenir d’espace.
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides : \< \> ( ) ; , [ ] »
  - Les lettres avec des marques diacritiques, telles que des umlauts, des accents et des tildes, sont des caractères non valides.

    Les caractères non valides s’appliquent aux caractères suivant le délimiteur de type et « : », de sorte que SMTP:User@contso.com est autorisé, mais SMTP:user:M@contoso.com ne l’est pas.

    > [!IMPORTANT]
    > Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent respecter les normes de messagerie électronique. Supprimez les adresses dupliquées ou indésirables si elles existent.

- **Samaccountname**

  - Nombre maximal de caractère : 20
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides : [ \ " | , / : \< \> + = ; ? \* ']
  - Si un utilisateur a un attribut **sAMAccountName** non valide mais qu’il a un attribut **userPrincipalName** valide, le compte d’utilisateur est créé dans Microsoft 365.
  - Si **sAMAccountName** et **userPrincipalName** ne sont pas valides, l’attribut **userPrincipalName** AD DS doit être mis à jour.

- **sn** (nom de famille)

  - Si l’attribut existe dans l’objet utilisateur, il est synchronisé avec Microsoft 365, mais Microsoft 365 n’en a pas besoin ni ne l’utilise.

- **targetAddress**

    Il est nécessaire que l’attribut **targetAddress** (par exemple, SMTP:tom@contoso.com) rempli pour l’utilisateur apparaisse dans la gal Microsoft 365. Dans les scénarios de migration de messagerie tiers, cela nécessiterait l’extension de schéma Microsoft 365 pour AD DS. L’extension de schéma Microsoft 365 ajoute également d’autres attributs utiles pour gérer les objets Microsoft 365 qui sont remplis à l’aide d’un outil de synchronisation d’annuaires d’AD DS. Par exemple, l’attribut **msExchHideFromAddressLists** pour gérer les boîtes aux lettres masquées ou les groupes de distribution est ajouté.

  - Nombre maximal de caractères : 256
  - La valeur d’attribut ne doit pas contenir d’espace.
  - La valeur d’attribut doit être unique dans le répertoire.
  - Caractères non valides : \ \< \> ( ) ; , [ ] »
  - Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent respecter les normes de messagerie électronique.

- **userPrincipalName**

  - **L’attribut userPrincipalName** doit être au format de connexion de style Internet, où le nom d’utilisateur est suivi du signe at (@) et d’un nom de domaine : par exemple, user@contoso.com. Toutes les adresses SMTP (Simple Mail Transport Protocol) doivent respecter les normes de messagerie électronique.
  - Le nombre maximal de caractères pour **l’attribut userPrincipalName** est de 113. Un nombre spécifique de caractères est autorisé avant et après le signe at (@), comme suit :
  - Nombre maximal de caractères pour le nom d’utilisateur qui se trouve devant le signe at (@) : 64
  - Nombre maximal de caractères pour le nom de domaine suivant le signe at (@) : 48
  - Caractères non valides : \ % &amp; \* + / = ? { } | \< \> ( ) ; : , [ ] "
  - Caractères autorisés : A – Z, a - z, 0 – 9, ' . - _ ! # ^ ~
  - Les lettres avec des marques diacritiques, telles que des umlauts, des accents et des tildes, sont des caractères non valides.
  - Le caractère @ est requis dans chaque valeur **userPrincipalName** .
  - Le caractère @ ne peut pas être le premier caractère dans chaque valeur **userPrincipalName** .
  - Le nom d’utilisateur ne peut pas se terminer par un point (.), un ampersand (&amp;), un espace ou un signe at (@).
  - Le nom d’utilisateur ne peut pas contenir d’espaces.
  - Les domaines routables doivent être utilisés ; Par exemple, les domaines locaux ou internes ne peuvent pas être utilisés.
  - Unicode est converti en caractères de trait de soulignement.
  - **userPrincipalName** ne peut pas contenir de valeurs en double dans le répertoire.

## <a name="3-prepare-the-userprincipalname-attribute"></a>3. Préparer l’attribut userPrincipalName

Active Directory est conçu pour permettre aux utilisateurs finaux de votre organisation de se connecter à votre annuaire à l’aide de **sAMAccountName** ou **userPrincipalName**. De même, les utilisateurs finaux peuvent se connecter à Microsoft 365 à l’aide du nom d’utilisateur principal (UPN) de leur compte professionnel ou scolaire. La synchronisation d’annuaires tente de créer des utilisateurs dans Azure Active Directory à l’aide du même UPN que celui de votre service AD DS. L’UPN est mis en forme comme une adresse e-mail.

Dans Microsoft 365, l’UPN est l’attribut par défaut utilisé pour générer l’adresse e-mail. Il est facile d’obtenir **userPrincipalName** (dans AD DS et azure AD) et l’adresse e-mail principale dans **proxyAddresses** définie sur différentes valeurs. Lorsqu’elles sont définies sur des valeurs différentes, il peut y avoir confusion pour les administrateurs et les utilisateurs finaux.

Il est préférable d’aligner ces attributs pour réduire la confusion. Pour répondre aux exigences de l’authentification unique avec Services ADFS (AD FS) 2.0, vous devez vous assurer que les upN dans Azure Active Directory et votre AD DS correspondent et utilisent un espace de noms de domaine valide.

## <a name="4-add-an-alternative-upn-suffix-to-ad-ds"></a>4. Ajouter un suffixe UPN alternatif à AD DS

Vous devrez peut-être ajouter un suffixe UPN de remplacement pour associer les informations d’identification d’entreprise de l’utilisateur à l’environnement Microsoft 365. Un suffixe UPN est la partie d’un UPN située à droite du caractère @. Les UPN qui sont utilisés pour l’authentification unique peuvent contenir des lettres, des chiffres, des points, des traits d’unions et des traits de soulignement, mais aucun autre type de caractère.

Pour plus d’informations sur l’ajout d’un suffixe UPN alternatif à Active Directory, consultez [Préparer la synchronisation d’annuaires](https://go.microsoft.com/fwlink/p/?LinkId=525430).

## <a name="5-match-the-ad-ds-upn-with-the-microsoft-365-upn"></a>5. Faire correspondre l’UPN AD DS à l’UPN Microsoft 365

Si vous avez déjà configuré la synchronisation d’annuaires, l’UPN de l’utilisateur pour Microsoft 365 peut ne pas correspondre à l’UPN AD DS de l’utilisateur défini dans votre AD DS. Cela peut se produire lorsqu’un utilisateur obtient une licence avant la vérification du domaine. Pour résoudre ce problème, utilisez [PowerShell pour corriger l’UPN en double](https://go.microsoft.com/fwlink/p/?LinkId=396730) pour mettre à jour l’UPN de l’utilisateur afin de vérifier que l’UPN Microsoft 365 correspond au nom d’utilisateur et au domaine de l’entreprise. Si vous mettez à jour l’UPN dans AD DS et souhaitez qu’il se synchronise avec l’identité Azure Active Directory, vous devez supprimer la licence de l’utilisateur dans Microsoft 365 avant d’apporter les modifications dans AD DS.

Découvrez également [comment préparer un domaine non routable (par exemple, un domaine .local) pour la synchronisation d’annuaires](prepare-a-non-routable-domain-for-directory-synchronization.md).

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez effectué la commande 1 à 5 ci-dessus, consultez [Configurer la synchronisation d’annuaires](set-up-directory-synchronization.md).
