---
title: Utiliser des modèles d’explication dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: En savoir plus sur l’utilisation et l’enregistrement des modèles d’explication dans Microsoft Syntex.
ms.openlocfilehash: c075a084077479fe1cbb9890203f7e2e6b15843d
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662816"
---
# <a name="use-explanation-templates-in-microsoft-syntex"></a>Utiliser des modèles d’explication dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; traitement de documents non structurés</sup>

Bien que vous puissiez ajouter manuellement différentes valeurs de liste d'expressions pour votre explication, il peut être plus facile d’utiliser les modèles qui vous sont fournis dans la bibliothèque d’explications.

Par exemple, au lieu d’ajouter manuellement toutes les variantes de *Date*, vous pouvez utiliser le modèle de liste d’expressions pour *Date*, car il comprend déjà de nombreuses valeurs de listes d’expressions :

![Bibliothèque d’explications.](../media/content-understanding/explanation-template.png)

La bibliothèque d’explications comprend des explications de *liste d’expressions* couramment utilisées, notamment :

- Date : Dates du calendrier, tous les formats. Inclut du texte et des nombres (par exemple, « 9 décembre 2022 »).
- Date (numérique) : Dates du calendrier, tous les formats. Inclut des nombres (par exemple, 1-11-2022).
- Heure : formats 12 heures et 24 heures.
- Nombre : Nombres positifs et négatifs jusqu'à deux décimales.
- Pourcentage : Une liste de motifs représentant un pourcentage. Par exemple : 1%, 11%, 100%, ou 11.11%.
- Numéro de téléphone : Formats américains et internationaux courants. Par exemple, 000 000 0000, 000-000-0000, (000)000-0000, ou (000) 000-0000.
- Code postal : Formats de code postal américain. Par exemple, 11111, 11111-1111.
- Premier mot de la phrase : Modèles courants pour les mots jusqu'à neuf caractères.
- Fin de phrase : Ponctuation courante pour la fin d'une phrase.
- Carte de crédit : Formats courants de numéros de cartes de crédit. Par exemple, 1111-1111-1111-1111.
- Numéro de sécurité sociale : Format du numéro de sécurité sociale américain. Par exemple, 111-11-1111.
- Case à cocher : Une liste de phrases représentant des variations d'une case à cocher remplie. Par exemple, _X_, _ _X_.
- La monnaie : Principaux symboles internationaux. Par exemple, $.
- E-mail CC : Une liste de phrases avec le terme « CC : », que l'on trouve souvent près des noms ou des adresses e-mail de personnes ou des autres groupes auxquels le message a été envoyé.
- Date de l' e-mail : Une liste de phrases avec le terme « Envoyé le :», qui se trouve souvent près de la date d'envoi de l' e-mail.
- Message d'accueil par e-mail : Lignes d'ouverture courantes pour les e-mails.
- Destinataire de l' e-mail : Une liste de phrases avec le terme « À :», que l'on trouve souvent près des noms ou des adresses e-mail des personnes ou des groupes auxquels le message a été envoyé.
- Expéditeur de l' email : Une liste de phrases avec le terme « De : », que l'on trouve souvent près du nom ou de l'adresse électronique de l'expéditeur.
- Objet de l' e-mail : Une liste de phrases avec le terme « Objet : », qui se trouve souvent près de l'objet de l' e-mail.

La bibliothèque d’explications inclut également des explications *expression régulière* couramment utilisées, notamment :

- Numéros de 6 à 17 chiffres : Correspond à tout numéro de 6 à 17 chiffres. Les numéros de compte bancaire américain correspondent à ce modèle.
- Adresse e-mail : correspond à un type commun d’adresse de messagerie telle que meganb@contoso.com.
- Numéro d’identification du contribuable américain : correspond à un nombre à trois chiffres commençant par 9 suivi d’un numéro à 6 chiffres commençant par 7 ou 8
- Adresse web (URL) : correspond au format d’une adresse web, en commençant par http:// ou https://.

En outre, la bibliothèque d’explications inclut trois types de modèles automatiques qui fonctionnent avec les données que vous avez étiquetées dans vos exemples de fichiers :

- Après l’étiquette : mots ou caractères qui apparaissent après les étiquettes dans les exemples de fichiers.
- Après l’étiquette : mots ou caractères qui apparaissent avant les étiquettes dans les exemples de fichiers.
- Étiquettes : jusqu’aux 10 premières étiquettes des exemples de fichiers.

Pour vous donner un exemple du fonctionnement des modèles automatiques, dans l’exemple de fichier suivant, nous allons utiliser le modèle d’explication avant étiquette pour fournir au modèle plus d’informations pour obtenir une correspondance plus précise.

![Fichier d’exemple.](../media/content-understanding/before-label.png)

Lorsque vous sélectionnez le modèle d’explication Avant étiquette, il recherche le premier jeu de mots qui apparaît avant l’étiquette dans vos exemples de fichiers. Dans l’exemple, l’ensemble des mots identifiés dans le premier exemple de fichier sont « En tant que ».

![Modèle d’avant étiquette.](../media/content-understanding/before-label-explanation.png)

Vous pouvez sélectionner **Ajouter** pour créer une explication à partir du modèle. À mesure que vous ajoutez d’autres exemples de fichiers, des mots supplémentaires sont identifiés et ajoutés à la liste des expressions.

![Ajouter l'étiquette.](../media/content-understanding/before-label-add.png)

## <a name="use-a-template-from-the-explanation-library"></a>Utiliser un modèle de la bibliothèque d’explications

1. Dans la section **Explications** de la page **Entraîner** de votre modèle, sélectionnez **Nouveau**, puis **À partir d’un modèle**.

   ![Ajouter avant l’étiquette.](../media/content-understanding/from-template.png)

2.  Sur la page **Modèles d’explication**, sélectionnez l’explication que vous souhaitez utiliser, puis **Ajouter**.

    ![Sélectionnez un modèle.](../media/content-understanding/phone-template.png)

3. Les informations relatives au modèle que vous avez sélectionné s’affichent sur la page **Créer une explication**. Si nécessaire, modifiez le nom de l’explication et ajoutez ou supprimez des éléments de la liste d’expressions.

    ![Modifier le modèle.](../media/content-understanding/phone-template-live.png)

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="save-a-template-to-the-explanation-library"></a>Enregistrer un modèle dans la bibliothèque d’explications

Vous pouvez enregistrer une explication en tant que modèle pour la rendre disponible dans la bibliothèque d’explications d’un centre de contenu à utiliser avec d’autres modèles. Le modèle inclut les paramètres de base et avancés pour l’explication, à l’exception de l’option d’état où les expressions apparaissent dans un document.

> [!NOTE]
> Seules les explications de liste d’expressions et d’expressions régulières peuvent être enregistrées en tant que modèle.

1. Dans la section **Explications** de la page **Entraîner** de votre modèle :

   a. Dans la liste des explications, sélectionnez celle que vous souhaitez enregistrer en tant que modèle.

   b. Sélectionnez **Enregistrer en tant que modèle.**

    ![Capture d’écran de la section Explications affichant l’option Enregistrer sous le modèle.](../media/content-understanding/explanation-save-as-template.png)

2. Dans la page **Enregistrer le modèle d’explication** :

   a. Dans la section **Nom,** renommons l’explication si nécessaire.

   b. Dans la section **Description,** ajoutez une description pour que d’autres personnes sachent comment utiliser l’explication.

   c. Sélectionnez **Enregistrer**.

    ![Capture d’écran de la page Modèle d’explication Enregistrer.](../media/content-understanding/save-explanation-template.png)

### <a name="see-also"></a>Voir aussi

[Types d’explication dans Microsoft Syntex](explanation-types-overview.md)