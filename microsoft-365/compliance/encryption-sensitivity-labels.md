---
title: Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Lorsque vous créez une étiquette de sensibilité, vous pouvez restreindre l’accès au contenu auquel l’étiquette sera appliquée. Les étiquettes de sensibilité peuvent utiliser le chiffrement pour protéger le contenu.
ms.openlocfilehash: ef4b5c9768687864427a0805039a35958c476142
ms.sourcegitcommit: 1f04eb8a32aed8571ac37bcfef61e0d0ef181eda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "42278770"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Restreindre l'accès au contenu grâce à la mise en place d'un chiffrement par les étiquettes de confidentialité 

Lorsque vous créez une étiquette de sensibilité, vous pouvez restreindre l’accès au contenu auquel l’étiquette sera appliquée. Par exemple, avec les paramètres de chiffrement d’une étiquette de sensibilité, vous pouvez protéger le contenu comme suit :

- Seuls les utilisateurs de votre organisation peuvent ouvrir un document ou un e-mail confidentiel.
- Seuls les utilisateurs du département marketing peuvent modifier et imprimer le document ou l’e-mail d’annonce de promotion, alors que tous les autres utilisateurs de votre organisation peuvent uniquement le lire.
- Les utilisateurs ne peuvent pas transférer un e-mail ou y copier tout contenu relatif à une réorganisation interne.
- La liste de prix à jour envoyée aux partenaires ne peut pas être ouverte après une date spécifiée.

Lorsqu’un document ou un e-mail est chiffré, l’accès à son contenu est restreint de l’une des façons suivantes :

- Il peut uniquement être déchiffré par les utilisateurs autorisés par les paramètres de chiffrement de l’étiquette.
- Il reste chiffré quel que soit son emplacement, interne ou externe à votre organisation, même si le fichier est renommé.
- Il est chiffré lorsqu’il est inactif (par exemple dans un compte OneDrive) et en transit (par exemple, un e-mail envoyé).

Enfin, en tant qu’administrateur, lorsque vous configurez une étiquette de confidentialité pour appliquer le chiffrement, vous pouvez choisir d’effectuer l’une des opérations suivantes :

- **Attribuer des autorisations maintenant**, afin de déterminer précisément les utilisateurs autorisés à accéder au contenu associé à cette étiquette.
- **Permettre aux utilisateurs d'attribuer des autorisations** lorsqu’ils appliquent l’étiquette au contenu. De cette façon, vous pouvez proposer aux membres de votre organisation la souplesse nécessaire pour mieux collaborer et accomplir leur travail.

Les paramètres de chiffrement sont disponibles lorsque vous [créez une étiquette de sensibilité](create-sensitivity-labels.md) dans le Centre de conformité Microsoft 365, dans le Centre de sécurité Microsoft 365 ou dans le Centre de sécurité et conformité Office 365.

## <a name="understand-how-the-encryption-works"></a>Comprendre comment fonctionne le chiffrement

Le chiffrement utilise le service Azure Rights Management (Azure RMS) à partir d’Azure Information Protection. Cette solution de protection utilise les stratégies de chiffrement, d’identité et d’autorisation. Pour plus d’informations, consultez [Qu’est-ce que Azure Rights Management ?](https://docs.microsoft.com/azure/information-protection/what-is-azure-rms) dans la documentation Azure Information Protection. 

Lorsque vous utilisez cette solution de chiffrement, la fonctionnalité **super utilisateur** s'assurer que les personnes et services autorisés peuvent toujours consulter et examiner les données qui ont été cryptées pour votre organisation. Le chiffrement peut ensuite être supprimé ou modifié si nécessaire. Pour plus d’informations, consultez la [Configuration de super utilisateurs pour les services Azure Information Protection et les services de découverte ou de la récupération de données](https://docs.microsoft.com/azure/information-protection/configure-super-users).

## <a name="how-to-configure-a-label-for-encryption"></a>La configuration d’une étiquette pour le chiffrement

[Créez ou modifiez une étiquette de confidentialité](create-sensitivity-labels.md#create-and-configure-sensitivity-labels), puis dans la page **Chiffrement** de l’Assistant, sélectionnez l’une des options suivantes :

- **Aucun** : il s'agit du paramètre par défaut d'une nouvelle étiquette. Aucun nouveau chiffrement n’est appliqué.
- **Appliquer** : active le chiffrement, puis vous spécifiez les paramètres de chiffrement.
- **Supprimer** : supprime le chiffrement si le document ou le courrier est chiffré.

> [!NOTE]
> L’option **Supprimer** est uniquement prise en charge par le client de l’étiquetage unifié d’Azure Information Protection. Lorsque vous utilisez l’étiquetage intégré, une étiquette incluant cette option est visible dans les applications Office et, si l'option est sélectionnée, le comportement de chiffrement est identique à **Aucun**.

Configuration des options de chiffrement :

![Options de chiffrement d’une étiquette de confidentialité](../media/encrytion-options-sensitivity-label.png)


### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Qu’advient-il du chiffrement existant lorsqu’une nouvelle étiquette est appliquée ?

Si une étiquette de confidentialité est appliquée à du contenu non chiffré, le résultat des options de chiffrement que vous pouvez sélectionner est explicite. Par exemple, si le chiffrement est paramétré sur **Aucun**, le contenu reste non chiffré.

Toutefois, il est possible que le contenu soit déjà chiffré. Par exemple, un autre utilisateur peut avoir appliqué :

- Ses propres autorisations, y compris les autorisations définies par l’utilisateur lorsqu'il y est invité par une étiquette, les autorisations personnalisées par le client Azure Information Protection et la protection de documents par l'**Accès restreint** dans une application Office.
- Un modèle de protection Azure Rights Management chiffrant le contenu d’une étiquette de manière individuelle. Cette catégorie inclut les règles de flux de courrier qui appliquent le chiffrement à l’aide de la protection des droits.
- Une étiquette appliquant le chiffrement par le biais des autorisations attribuées par l’administrateur.

Le tableau ci-après précise ce qu’il advient du chiffrement existant lorsqu’une étiquette de niveau de confidentialité est appliquée à ce contenu :

| |**Chiffrement : Aucun**|**Chiffrement : Appliquer**|**Chiffrement : Supprimer**|
|:-----|:-----|:-----|:-----|
|**Autorisations spécifiées par l'utilisateur**|Le chiffrement d’origine est conservé|Le nouveau chiffrement d'étiquettes est appliqué|Le chiffrement d’origine est supprimé|
|**Modèle de protection**|Le chiffrement d’origine est conservé|Le nouveau chiffrement d'étiquettes est appliqué|Le chiffrement d’origine est supprimé|
|**Étiquette incluant les autorisations définies par l’administrateur**|Le chiffrement d’origine est supprimé|Le nouveau chiffrement d'étiquettes est appliqué|Le chiffrement d’origine est supprimé|

Notez que, dans le cas où le nouveau chiffrement d’étiquettes est appliqué ou si le chiffrement d’origine est supprimé, cela se produit uniquement si l’utilisateur appliquant l’étiquette dispose d'un droit ou d'un rôle qui prend en charge cette action :
- Le [droit d'utilisation](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Exportation ou Contrôle total.
- Rôle du [propriétaire ou de l'émetteur des Rights Management](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) ou du [super utilisateur](https://docs.microsoft.com/azure/information-protection/configure-super-users).

Si l’utilisateur ne dispose pas de ces droits ou rôles, l’étiquette ne peut pas être appliquée et le chiffrement d’origine est préservé. L’utilisateur voit le message suivant : **Vous n’êtes pas autorisé à effectuer cette modification dans l’étiquette de confidentialité. Veuillez contacter le propriétaire du contenu.**

Par exemple, la personne appliquant Ne pas transférer à un courrier électronique peut étiqueter de nouveau le thread afin de remplacer ou de supprimer le chiffrement, car elle est propriétaire des Rights Management de cet e-mail. À l’exception des super utilisateurs, les destinataires de ce message ne peuvent pas lui attribuer une nouvelle étiquette, car ils disposent pas des droits d’utilisation requis.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Pièces jointes des courriers électroniques chiffrés

Lorsqu’un courrier électronique est chiffré par une quelconque méthode, les documents Office non chiffrés joints au message héritent automatiquement des mêmes paramètres de chiffrement.

Les documents déjà chiffrés, puis ajoutés sous forme de pièces jointes, conservent leur chiffrement d’origine. 

## <a name="configure-encryption-settings"></a>Configurer les paramètres du chiffrement

Lorsque vous sélectionnez **Appliquer** dans la page de **Chiffrement** de l’Assistant pour créer ou modifier une étiquette de confidentialité, choisissez si vous souhaitez :

- **Attribuer des autorisations maintenant**, afin de déterminer précisément les utilisateurs autorisés à accéder au contenu auquel l'étiquette est appliquée. Pour plus d’informations, voir la section suivante [Attribuer des autorisations maintenant](#assign-permissions-now).
- **Permettre aux utilisateurs d'attribuer des autorisations** lorsque vos utilisateurs appliquent l’étiquette au contenu. Grâce à cette option, vous permettez aux membres de votre organisation de bénéficier d'une certaine souplesse pour mieux collaborer et accomplir leur travail. Pour plus d’informations, voir la section ci-dessous [Permettre aux utilisateurs d’attribuer des autorisations](#let-users-assign-permissions).

Par exemple, si vous avez une étiquette de confidentialité appelée **Hautement confidentiel** qui sera appliquée à votre contenu le plus sensible, vous souhaiterez peut-être choisir le type d’autorisations qui lui sont associées.

Par ailleurs, si vous avez une étiquette de confidentialité appelée **Contrats professionnels** et que le flux de travail de votre organisation exige que vos collègues collaborent sur ce contenu avec d'autres personnes de façon ponctuelle, vous souhaiterez peut-être autoriser vos utilisateurs à décider qui obtient les autorisations lorsqu’ils attribuent l’étiquette. Cette flexibilité permet à la fois à vos utilisateurs de gagner en productivité et de réduire les demandes aux administrateurs de mise à jour ou de création de nouvelles étiquettes de confidentialité pour résoudre des scénarios spécifiques.

Choisissez d’attribuer des autorisations maintenant ou de permettre aux utilisateurs d’affecter des autorisations : 

![Option pour ajouter des autorisations définies par l’utilisateur ou l’administrateur](../media/sensitivity-label-user-or-admin-defined-permissions.png)


## <a name="assign-permissions-now"></a>Attribuer des autorisations maintenant

Utilisez les options suivantes pour contrôler les utilisateurs autorisés à accéder aux e-mails ou aux documents auxquels cette étiquette est appliquée. Vous pouvez :

1. **Autoriser l’expiration des accès au contenu portant l’étiquette**, à une date spécifique ou au bout d’un certain nombre de jours après l’application de l’étiquette. Après cette période, les utilisateurs ne sont plus en mesure d’ouvrir l’élément étiqueté. Si vous spécifiez une date, elle prend effet le jour choisi à minuit dans votre fuseau horaire actuel. (Notez que certains clients de messagerie pourraient ne pas imposer l'expiration et ne pas afficher les e-mails dont la date d'expiration est dépassée, en raison de leurs mécanismes de mise en cache).

2. **Autoriser l’accès hors connexion** : Jamais, Toujours ou pendant un nombre de jours déterminé après que l’étiquette a été appliquée. Si vous limitez l’accès hors connexion sur Jamais ou sur un nombre de jours, lorsque ce seuil est atteint, les utilisateurs doivent s’authentifier à nouveau et leur accès est journalisé. Pour plus d’informations, reportez-vous à la section suivante sur la licence d’utilisation de Rights Management.

Paramètres de contrôle d’accès pour du contenu chiffré :

![Paramètres pour les autorisations définies par l’administrateur](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

### <a name="rights-management-use-license-for-offline-access"></a>Licence d’utilisation de Rights Management pour l’accès en mode hors connexion

Lorsqu’un utilisateur ouvre un document ou un courrier électronique qui a été protégé par le chiffrement à partir du service Azure Rights Management, une licence d’utilisation d’Azure Rights Management est accordée à l’utilisateur pour ce contenu. Cette licence d’utilisation est un certificat qui contient les droits d’utilisation de l’utilisateur pour le document ou le courrier électronique, ainsi que la clé de chiffrement qui a été utilisée pour chiffrer le contenu. La licence d’utilisation inclut également une date d’expiration, si elle est activée, ainsi que sa durée de validité.

Si aucune date d’expiration n’a été configurée, la période de validité par défaut de la licence d’utilisation est de 30 jours. Pendant la durée de la licence, l’utilisateur n’a pas besoin d’être authentifié ou autorisé à nouveau pour accéder au contenu. Ce procédé permet à l'utilisateur de continuer à ouvrir le document ou l’e-mail protégé sans connexion à Internet. Lorsque la période de validité de la licence d’utilisation a expiré, l’utilisateur doit à nouveau s’authentifier ou être autorisé lorsqu’il souhaite accéder au document ou à l’e-mail protégé.

Outre la réauthentification, les paramètres de chiffrement et l’appartenance au groupe d’utilisateurs sont réévalués. Autrement dit, les utilisateurs peuvent constater des résultats d’accès différents au même document ou au même e-mail si des modifications ont été apportées aux paramètres de chiffrement ou à l’appartenance au groupe depuis leur dernier accès au contenu.

Pour savoir comment modifier le paramètre de 30 jours par défaut, reportez-vous à [Licence d’utilisation Rights Management](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Attribuer des autorisations à des utilisateurs ou des groupes spécifiques

Vous pouvez accorder des autorisations à des personnes spécifiques, de manière à ce qu’elles soient les seules à pouvoir interagir avec le contenu étiqueté :

1. Ajoutez tout d’abord les utilisateurs ou les groupes qui vont recevoir les autorisations sur le contenu étiqueté.

2. Choisissez ensuite les autorisations que les utilisateurs doivent avoir sur le contenu étiqueté.

Attribution d'autorisations :

![Options d’attribution des autorisations aux utilisateurs](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Ajouter des utilisateurs ou des groupes

Lorsque vous attribuez des autorisations, vous pouvez choisir :

- Tous les membres de votre organisation (tous les membres du client). Ce paramètre exclut les comptes Invité.
- Tout utilisateur authentifié. Assurez-vous de bien comprendre la [configuration requise et les limitations](#requirements-and-limitations-for-add-any-authenticated-users) de ce paramètre avant de le sélectionner.
- N’importe quel utilisateur, groupe de sécurité à extension messagerie, groupe de distribution, groupe Office 365 ou groupe de distribution dynamique. 
- Une adresse e-mail ou un domaine en dehors de votre organisation, tels que gmail.com, hotmail.com ou outlook.com. 

Lorsque vous choisissez tous les membres de client ou parcourez l’annuaire, les utilisateurs ou les groupes doivent avoir une adresse e-mail.

Nous vous recommandons d’utiliser des groupes plutôt que des utilisateurs. En effet, avec cette stratégie, votre configuration reste plus simple.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>Configuration requise et restrictions pour **Ajouter des utilisateurs authentifiés**

Ce paramètre ne limite pas les personnes autorisées à accéder au contenu chiffré par l’étiquette, même s'il chiffre le contenu et vous propose des options permettant de limiter la façon dont le contenu peut être utilisé (autorisations) ou consulté (expiration et accès en mode hors connexion). Toutefois, l’application ouvrant le contenu chiffré doit pouvoir prendre en charge l’authentification utilisée. Pour cette raison, les réseaux sociaux tels que Google et l'authentification unique par mot de passe conviennent seulement pour la messagerie électronique, et uniquement lorsque vous utilisez Exchange Online et les nouvelles fonctionnalités du chiffrement de messages d’Office 365. Les comptes Microsoft peuvent être utilisés avec les applications Office 365 et le [visionneur Azure Information Protection](https://portal.azurerms.com/#/download).

Voici des scénarios classiques pour les paramètres des utilisateurs authentifiés :
- Peu vous importe la personne qui affiche le contenu, mais vous souhaitez limiter son utilisation. Par exemple, vous ne voulez pas que le contenu soit modifié, copié ou imprimé.
- Vous n’avez pas besoin de restreindre l’accès au contenu, mais vous voulez être en mesure d'approuver la personne qui l'ouvre.
- Vous exigez que le contenu soit chiffré au repos et en transit, mais il ne nécessite pas de contrôle d’accès.

#### <a name="choose-permissions"></a>Choisir les autorisations

Lorsque vous choisissez les autorisations à attribuer à ces utilisateurs ou ces groupes, vous pouvez sélectionner :

- Un [niveau d’autorisation prédéfini](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) avec un groupe de droits prédéfini, par exemple, Co-auteur ou Réviseur.
- Un groupe d’autorisations personnalisé, avec lequel vous choisissez les autorisations que vous voulez.

Pour plus d’informations sur chacune des autorisations spécifiques, reportez-vous à [Descriptions et droits d’utilisation](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Options de choix d’autorisations prédéfinies ou personnalisées](../media/Sensitivity-Choose-permissions-settings.png)

Notez qu’une même étiquette peut accorder différentes autorisations à différents utilisateurs. Par exemple, une étiquette unique peut affecter à certains utilisateurs des droits de réviseur et à un autre utilisateur des droits de co-auteur, comme illustré sur la capture d'écran suivante.

Pour ce faire, ajoutez des utilisateurs ou groupes, attribuez-leur des autorisations et enregistrez ces paramètres. Répétez ensuite ces étapes : ajoutez des utilisateurs, attribuez-leur des autorisations et enregistrez les paramètres à chaque fois. Vous pouvez répéter cette configuration autant de fois que nécessaire, afin de définir différentes autorisations pour différents utilisateurs.

![Différents utilisateurs avec différentes autorisations](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>L’émetteur de Rights Management (celui qui applique l’étiquette de sensibilité) bénéficie toujours d’un contrôle total.

Le chiffrement d'une étiquette de confidentialité utilise le service Azure Rights Management à partir d’Azure Information Protection. Lorsqu’un utilisateur applique une étiquette de sensibilité pour protéger un document ou un e-mail à l’aide du chiffrement, il devient l’émetteur Rights Management sur ce contenu.

L’émetteur Rights Management bénéficie continuellement d’autorisations en contrôle total sur le document ou l’e-mail et, par ailleurs :

- Si les paramètres de chiffrement comportent une date d’expiration, l’émetteur Rights Management peut toujours ouvrir et modifier le document ou l’e-mail après cette date.
- L’émetteur Rights Management peut toujours accéder au document ou à l’e-mail hors connexion.
- L’émetteur Rights Management peut toujours ouvrir un document après sa révocation.

Pour plus d’informations, reportez-vous à [Émetteur Rights Management et propriétaire Rights Management](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

## <a name="let-users-assign-permissions"></a>Permettre aux utilisateurs d’attribuer des autorisations

Vous pouvez utiliser ces options pour permettre aux utilisateurs d’attribuer des autorisations lorsqu’ils appliquent manuellement une étiquette de confidentialité à un contenu :

- Dans Outlook, un utilisateur peut sélectionner des restrictions équivalant à l’option [ne pas transférer](https://docs.microsoft.com/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) pour les bénéficiaires qu'il a choisis.

- Dans Word, PowerPoint et Excel, l’utilisateur est invité à sélectionner ses propres niveaux d’autorisation pour des utilisateurs, des groupes ou des organisations spécifiques. 
    > [!NOTE]
    > Cette option pour Word, PowerPoint et Excel est prise en charge par le client de l’étiquetage unifié d’Azure Information Protection. Pour les applications utilisant l’étiquetage intégré, la prise en charge est actuellement disponible dans la [Version d'évaluation pour Windows et Mac](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint). 
    > 
    > Si cette option est sélectionnée, mais n’est pas prise en charge pour l’application d’un utilisateur, celle-ci ne s’affiche pas pour l’utilisateur, ou (actuellement disponible dans la version d’évaluation pour iOS et Android) l’étiquette s’affiche pour assurer la cohérence, mais elle ne peut pas être appliquée avec un message d’explication aux utilisateurs.

Lorsque les options sont prises en charge, utilisez le tableau suivant pour déterminer le moment où les utilisateurs voient l’étiquette de confidentialité :

|Paramètres |Étiquette visible dans Outlook|Étiquette visible dans Word, Excel et PowerPoint|
|:-----|:-----|:-----|:-----|
|**Appliquer dans Outlook des restrictions équivalant à l’option Ne pas transférer**|Oui |Non |
|**Dans Word, PowerPoint et Excel, inviter les utilisateurs à spécifier des autorisations**|Non |Oui|

Lorsque les deux paramètres sont sélectionnés, l’étiquette est par conséquent visible dans Outlook et dans Word, Excel et PowerPoint.

Une étiquette de confidentialité permettant aux utilisateurs d’attribuer des autorisations peut être appliquée au contenu uniquement manuellement par les utilisateurs. Elle ne peut pas être appliquée automatiquement ou utilisée comme étiquette recommandée.

Configuration d'autorisations attribuées par utilisateur :

![Paramètres de chiffrement pour les autorisations définies par l’utilisateur](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>Restrictions Outlook

Dans Outlook, lorsqu’un utilisateur applique une étiquette de confidentialité qui lui permet d’attribuer des autorisations à un message, les restrictions sont identiques à celles de l’option ne pas transférer. L’utilisateur voit le nom et la description de l’étiquette dans la partie supérieure du message, ce qui indique que le contenu est protégé. Contrairement à Word, PowerPoint et Excel (voir la [section suivante](#word-powerpoint-and-excel-permissions)), les utilisateurs ne sont pas invités à sélectionner des autorisations spécifiques.

![Étiquette de niveau de confidentialité appliquée à un message dans Outlook](../media/sensitivity-label-outlook-protection-applied.png)

Lorsque l’option ne pas transférer est appliquée à un e-mail, celui-ci est chiffré et les destinataires doivent être authentifiés. Les destinataires ne peuvent alors pas le transférer, l’imprimer ou en faire une copie. Par exemple, dans le client Outlook, le bouton transférer n’est pas disponible, les options du menu enregistrer sous et imprimer ne sont pas disponibles, et vous ne pouvez pas ajouter ou modifier des destinataires dans les zones à, CC ou CCI.

Les documents Office non chiffrés qui sont joints à un courrier électronique héritent automatiquement des mêmes restrictions. Les droits d’utilisation appliqués à ces documents sont modifier le contenu, modifier; afficher, ouvert, lu et autoriser les macros. Si l’utilisateur souhaite appliquer des droits d’utilisation différents pour une pièce jointe, ou si la pièce jointe n’est pas un document Office qui prend en charge cette protection héritée, l’utilisateur doit protéger le fichier avant de le joindre à l’e-mail.

### <a name="word-powerpoint-and-excel-permissions"></a>Autorisations Word, PowerPoint et Excel

Dans Word, PowerPoint et Excel, lorsqu’un utilisateur applique une étiquette de confidentialité qui lui permet d’attribuer des autorisations à un document, il est invité à préciser son choix en matière d'utilisateurs et d'autorisations au moment où le chiffrement est appliqué.

Par exemple, avec un client d’étiquetage unifié Azure Information Protection, les utilisateurs peuvent :

- Sélectionner un niveau d’autorisation, tel que visionneuse (qui attribue l’autorisation Afficher uniquement) ou co-auteur (qui affecte les autorisations afficher, modifier, copier et imprimer).
- Sélectionner les utilisateurs, les groupes ou les organisations. Cela peut inclure des personnes à l’intérieur ou à l’extérieur de votre organisation.
- Sélectionnez une date d’expiration, après laquelle les utilisateurs sélectionnés ne pourront pas accéder au contenu. Pour plus d’informations, voir la section ci-dessus [licence d'utilisation de la gestion des droits pour l’accès hors connexion](#rights-management-use-license-for-offline-access).

![Options de protection pour l’utilisateur avec les autorisations personnalisées](../media/sensitivity-aip-custom-permissions-dialog.png)

Pour l’étiquetage intégré, les utilisateurs consultent la même boîte de dialogue s’ils sélectionnent ce qui suit :

- Windows : onglet **Fichier** > **Informations** > **Protéger le document** > **Restreindre l'accès** > **Accès restreint**

- MacOS : onglet **Révision** > **Protection** > **Autorisations** > **Accès restreint**


## <a name="considerations-for-encrypted-content"></a>Considérations relatives au contenu chiffré

Le chiffrement de vos documents et messages électroniques les plus confidentiels permet de s’assurer que seules les personnes autorisées peuvent accéder à ces données. Il existe toutefois des éléments dont vous devez tenir compte :

- Si votre organisation n'a pas [activé les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](sensitivity-labels-sharepoint-onedrive-files.md) :
    
    - Recherche, eDiscovery et Delve ne seront pas opérationnels avec les fichiers chiffrés. 
    - Les stratégies de protection contre la perte de données DLP fonctionnent avec les métadonnées de ces fichiers chiffrés (notamment les informations de l'étiquette de rétention), mais pas avec leur contenu (comme des numéros de carte de crédit dans des fichiers).
    - Les utilisateurs ne peuvent pas ouvrir les fichiers chiffrés à l’aide d’Office sur le web. Lorsque des étiquettes de confidentialité sont activées pour les fichiers Office dans SharePoint et OneDrive, les utilisateurs peuvent se servir d'Office sur le web pour ouvrir des fichiers chiffrés, avec certaines [restrictions](sensitivity-labels-sharepoint-onedrive-files.md#limitations) qui incluent le chiffrement appliqué avec une clé locale (connue sous le nom de « conservez de votre propre clé » ou HYOK) et le chiffrement appliqué indépendamment d’une étiquette de confidentialité.

- Pour permettre à plusieurs utilisateurs de modifier un fichier chiffré au même moment, ils doivent tous utiliser Office pour le web. Si ce n’est pas le cas et que le fichier est déjà ouvert :
    
    - Dans les applications Office (Windows, Mac, Android et iOS), les utilisateurs remarquent le message **Fichier en cours d'utilisation** incluant le nom de la personne ayant extrait le fichier. Ils peuvent ensuite afficher une copie en lecture seule, enregistrer et modifier une copie du fichier, et recevoir une notification lorsque le fichier est disponible.
    - Dans Office pour le web, les utilisateurs remarquent un message d’erreur indiquant qu’ils ne peuvent pas modifier le document avec d’autres personnes. Ils peuvent ensuite sélectionner **Ouvrir en mode Lecture**.

- La fonctionnalité [Enregistrement automatique](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) dans les applications Office (Windows, Mac, Android et iOS) est désactivée pour les fichiers chiffrés. Un message s'affiche indiquant aux utilisateurs que le fichier dispose d'autorisations restreintes qui doivent être supprimées avant que l’Enregistrement automatique puisse être activé.

- L’ouverture des fichiers chiffrés peut être plus longue dans les applications Office (Windows, Mac, Android et iOS).

- Les actions suivantes pour les fichiers chiffrés ne sont pas prises en charge dans les applications Office (Windows, Mac, Android et iOS), et un message d'erreur s'affiche aux utilisateurs indiquant qu’un problème s’est produit. Les fonctionnalités de SharePoint peuvent toutefois être utilisées en tant qu'alternative :
    
    - Afficher, restaurer et enregistrer des copies de versions précédentes. Les utilisateurs peuvent également effectuer ces actions à l’aide d’Office sur le web lorsque vous [activez et configurez le contrôle de version d'une liste ou d'une bibliothèque](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37). 
    - Modifier le nom ou l’emplacement des fichiers. Les utilisateurs peuvent également [renommer un fichier, un dossier ou un lien dans une bibliothèque de documents](https://support.office.com/article/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185) dans SharePoint.

Pour bénéficier d’une expérience de collaboration optimale en ce qui concerne les fichiers chiffrés par une étiquette de confidentialité, nous vous recommandons d’utiliser les [étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) et Office pour le web. 

## <a name="important-prerequisites"></a>Conditions préalables importantes

Pour utiliser le chiffrement, vous devrez peut-être effectuer des tâches de configuration.

### <a name="activate-protection-from-azure-information-protection"></a>Activer la protection à partir d’Azure Information Protection

Pour que le chiffrement soit appliqué par les étiquettes de confidentialité, le service de protection (Azure Rights Management) à partir d’Azure Information Protection doit être activé pour votre client. Chez les nouveaux clients, il s’agit du paramètre par défaut, mais vous devrez peut-être activer manuellement le service. Pour plus d’informations, consultez [Activation du service de protection à partir d’Azure Information Protection](https://docs.microsoft.com/azure/information-protection/activate-service).

### <a name="configure-exchange-for-azure-information-protection"></a>Configurer Exchange pour Azure Information Protection

Il n’est pas nécessaire de configurer Exchange pour Azure Information Protection pour que les utilisateurs puissent appliquer des étiquettes dans Outlook pour protéger leurs e-mails. Toutefois, tant qu’Exchange n’a pas été configuré pour Azure Information Protection, vous ne bénéficiez pas de toutes les fonctionnalités de protection Azure Rights Management avec Exchange.
 
Par exemple, les utilisateurs ne peuvent pas afficher les e-mails protégés sur des téléphones mobiles ou avec Outlook sur le web, les messages e-mails protégés ne peuvent pas être indexés pour la recherche et vous ne pouvez pas configurer la protection contre la perte de données (DLP) Exchange Online pour la protection Rights Management. 

Pour vous assurer qu’Exchange est en mesure de prendre en charge ces scénarios supplémentaires, reportez-vous aux rubriques suivantes :

- Pour Exchange Online, consultez les instructions de la section [Exchange Online : configuration de la gestion des droits relatifs à l’information](https://docs.microsoft.com/azure/information-protection/configure-office365#exchangeonline-irm-configuration).
- Pour Exchange en local, vous devez déployer le [connecteur RMS et configurer vos serveurs Exchange](https://docs.microsoft.com/azure/information-protection/deploy-rms-connector). 
