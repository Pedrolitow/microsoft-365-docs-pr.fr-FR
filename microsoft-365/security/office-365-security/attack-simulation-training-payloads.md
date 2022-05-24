---
title: Créer des charges utiles personnalisées pour la formation à la simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Les administrateurs peuvent apprendre à créer des charges utiles personnalisées pour la formation à la simulation d’attaque dans Microsoft Defender pour Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: f0f91eb3936d1dc4ed6c028552b37fecb5df2ff6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648302"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Créer des charges utiles personnalisées pour l’entraînement de simulation d’attaque dans Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans la formation à la simulation d’attaque, une _charge utile_ est le message électronique de hameçonnage et les pages web qui sont présentées aux utilisateurs dans des simulations. La formation à la simulation d’attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2 offre un catalogue de charges utiles intégré robuste pour les techniques d’ingénierie sociale disponibles. Toutefois, vous souhaiterez peut-être créer des charges utiles personnalisées qui fonctionneront mieux pour votre organisation.

Cet article explique comment créer vos propres charges utiles dans l’entraînement de simulation d’attaque. Vous pouvez créer des charges utiles personnalisées aux emplacements suivants :

- Onglet **Charges utiles** : dans le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse **e-mail &'onglet** **Charges utiles** d’entraînement \> de **simulation d’attaque** de collaboration\>. Pour accéder directement à l’onglet **Charges utiles**, utilisez <https://security.microsoft.com/attacksimulator?viewid=payload>.
- Lors de la création de la simulation : vous pouvez créer des charges utiles personnalisées sur la page **Sélectionner une charge utile** (la troisième page) de l’Assistant création de simulation. Pour plus d’informations, consultez [Simuler une attaque par hameçonnage dans Defender pour Office 365](attack-simulation-training.md).

Pour obtenir des informations sur la formation à la simulation d’attaque, consultez [Démarrage l’utilisation de la formation de simulation d’attaque](attack-simulation-training-get-started.md).

> [!NOTE]
> Certaines marques, logos, symboles, insignias et autres identificateurs sources bénéficient d’une protection renforcée en vertu des lois et lois locales, d’État et fédérales. L’utilisation non autorisée de ces indicateurs peut exposer les utilisateurs à des sanctions, y compris des amendes pénales. Bien qu’il ne s’agit pas d’une liste exhaustive, il s’agit des scellés présidentiels, vice-présidentiels et du Congrès, de la CIA, du FBI, de la Sécurité sociale, de l’assurance-maladie et de Medicaid, du États-Unis internal revenue service et des Jeux olympiques. Au-delà de ces catégories de marques, l’utilisation et la modification d’une marque tierce comportent un risque inhérent. L’utilisation de vos propres marques et logos dans une charge utile serait moins risquée, en particulier lorsque votre organisation autorise l’utilisation. Si vous avez d’autres questions sur ce qui est ou n’est pas approprié à utiliser lors de la création ou de la configuration d’une charge utile, vous devez consulter vos conseillers juridiques.

## <a name="create-a-payload"></a>Créer une charge utile

Après avoir cliqué sur ![Créer une icône de charge utile.](../../media/m365-cc-sc-create-icon.png) **Créez une charge utile** à partir de l’onglet **Charges utiles** de l’entraînement de simulation d’attaque ou, dans la page **[Sélectionner une charge utile](attack-simulation-training.md#select-a-payload)** de l’Assistant création de simulation, l’Assistant création de charge utile démarre et est décrit dans cette section.

### <a name="select-a-payload-type"></a>Sélectionner un type de charge utile

Dans la page **Sélectionner un type** , la seule valeur que vous pouvez sélectionner actuellement est **e-mail**.

Cliquez sur **Suivant**.

### <a name="select-a-social-engineering-technique"></a>Sélectionner une technique d’ingénierie sociale

Dans la page **Sélectionner une technique** , les options disponibles sont les mêmes que dans la page [Sélectionner une technique](attack-simulation-training.md#select-a-social-engineering-technique) dans l’Assistant Création de simulation :

- **Collecte des informations d’identification**
- **Pièce jointe de programme malveillant**
- **Lien dans la pièce jointe**
- **Lien vers un programme malveillant**
- **Drive-by URL**

Lorsque vous avez terminé, cliquez sur **Suivant**.

### <a name="name-and-describe-the-payload"></a>Nommez et décrivez la charge utile

Dans la page **Nom de la charge utile** , configurez les paramètres suivants :

- **Nom** : entrez un nom unique et descriptif pour la charge utile.
- **Description** : entrez une description détaillée facultative pour la charge utile.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="configure-the-payload"></a>Configurer la charge utile

Dans la page **Configurer la charge utile** , il est temps de générer votre charge utile. La plupart des paramètres disponibles sont déterminés par la sélection que vous avez effectuée sur la page **Sélectionner la technique** (par exemple, les liens et les pièces jointes).

- **Section Détails de l’expéditeur** : Configurez les paramètres suivants :
  - **À partir du nom**
  - **Utilisez le prénom comme nom d’affichage** : par défaut, ce paramètre n’est pas sélectionné.
  - **À partir de l’e-mail** : si vous choisissez une adresse e-mail interne pour l’expéditeur de votre charge utile, la charge utile semble provenir d’un collègue. Cette adresse e-mail de l’expéditeur augmente la sensibilité d’un utilisateur à la charge utile et aide à informer les employés sur le risque de menaces internes.
  - **Sujet de l’e-mail**

- **Section Détails de** la pièce jointe : cette section est disponible uniquement si vous avez sélectionné **La pièce jointe du programme malveillant**, **lier en pièce jointe** ou **lier à un programme malveillant** dans la page **Sélectionner une technique** . Configurez les paramètres suivants :
  - **Nommer votre pièce jointe**
  - **Sélectionnez un type de pièce jointe** : Actuellement, la seule valeur disponible est **Docx**.

- **Lien pour la section pièce jointe** : cette section est disponible uniquement si vous avez sélectionné **Lien vers un programme malveillant** dans la page **Sélectionner une technique** . Dans la zone **Sélectionner une URL que vous souhaitez être votre lien de pièce jointe de programme malveillant** , sélectionnez l’une des URL disponibles (les mêmes URL que celles décrites pour la section Lien de **hameçonnage** ).

  Plus tard, vous incorporerez l’URL dans le corps du message.

- Section **lien d’hameçonnage** : cette section est disponible uniquement si vous avez sélectionné **La récolte des informations d’identification**, **lier en pièce jointe** ou **l’URL de lecteur sur** la page **Sélectionner la technique**.

  Pour la **collecte des informations d’identification** ou l’URL **drive-by**, le nom de la zone est **Sélectionner une URL que vous souhaitez être votre lien d’hameçonnage**. Plus tard, vous incorporerez l’URL dans le corps du message.

  Pour **Lien dans la pièce jointe**, le nom de la zone est **Sélectionner une URL dans cette pièce jointe que vous souhaitez être votre lien d’hameçonnage**. Plus tard, vous incorporerez l’URL dans la pièce jointe.

  Sélectionnez l’une des valeurs d’URL disponibles :
  
  - <https://www.mcsharepoint.com>
  - <https://www.attemplate.com>
  - <https://www.doctricant.com>
  - <https://www.mesharepoint.com>
  - <https://www.officence.com>
  - <https://www.officenced.com>
  - <https://www.officences.com>
  - <https://www.officentry.com>
  - <https://www.officested.com>
  - <https://www.prizegives.com>
  - <https://www.prizemons.com>
  - <https://www.prizewel.com>
  - <https://www.prizewings.com>
  - <https://www.shareholds.com>
  - <https://www.sharepointen.com>
  - <https://www.sharepointin.com>
  - <https://www.sharepointle.com>
  - <https://www.sharesbyte.com>
  - <https://www.sharession.com>
  - <https://www.sharestion.com>
  - <https://www.templateau.com>
  - <https://www.templatent.com>
  - <https://www.templatern.com>
  - <https://www.windocyte.com>

  > [!NOTE]
  > Un service de réputation d’URL peut identifier une ou plusieurs de ces URL comme étant non sécurisées. Vérifiez la disponibilité de l’URL dans vos navigateurs web pris en charge avant d’utiliser l’URL dans une simulation. Pour plus d’informations, consultez [URL de simulation d’hameçonnage bloquées par Google Coffre Navigation](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing).

- **Section Contenu de** la pièce jointe : cette section est disponible uniquement si vous avez sélectionné **Lien en pièce jointe** dans la page **Sélectionner la technique** .

  Un éditeur de texte enrichi est disponible pour vous permettre de créer le contenu dans la charge utile de votre pièce jointe de fichier.

  Utilisez le contrôle de **lien d’hameçonnage** pour ajouter l’URL de hameçonnage précédemment sélectionnée dans la pièce jointe.

- Paramètres courants :
  - **Ajouter des balises**
  - **Thème** : Les valeurs disponibles sont : **Activation** du **compte, vérification du compte**, **facturation**, nettoyage du **courrier**, **Document reçu**, **Dépenses**, **Télécopie**, **Rapport financier**, **Messages entrants**, **Facture**, **Élément reçu**, Alerte de **connexion**, **Courrier reçu**, **Autre**, **Mot de passe**, **Paiement**, **Paie**, **Offre personnalisée**, **Quarantaine** , **Travail à distance**, **passer en revue le message**, **mise à jour de sécurité**, **service suspendu**, **signature requise**, **mise à niveau de la boîte aux lettres Stockage**, vérifier la **boîte aux lettres** ou la **messagerie vocale**.
  - **Marque** : Les valeurs disponibles sont **: American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** ou **Autres**.
  - **Secteur** : Les valeurs disponibles sont : **banque**, **services aux entreprises**, **services à la consommation**, **éducation**, **énergie**, **construction**, **conseil**, **services financiers**, **gouvernement**, **hospitalité**, **assurance**, **juridique**, **services de messagerie**, **informatique**, **santé**, **fabrication**, **vente au détail**, **télécommunications**, **immobilier**, ou **Autre.**
  - **Événement actuel** : Les valeurs disponibles sont **Oui** ou **Non**.
  - **Controversé** : Les valeurs disponibles sont **Oui** ou **Non**.

- **Section Langue** : Sélectionnez la langue de la charge utile. Les valeurs disponibles sont : **anglais**, **espagnol**, **allemand**, **japonais**, **Français**, **portugais**, **néerlandais**, **italien**, **suédois**, **chinois (simplifié)**, **norvégien bokmål**, **polonais**, **russe**, **finnois**, **coréen**, **turc**, **hongrois**, **hébreu**, **thaï, arabe**, **vietnamien**, **slovaque**, **grec**, **indonésien**, **roumain**, **slovène**, **croate**, **catalan** ou **autre**.

- **Section e-mail** :

  - Vous pouvez cliquer sur **Importer un e-mail** , puis **choisir un fichier** pour importer un fichier de message en texte brut existant.

  - Sous l’onglet **Texte** , un éditeur de texte enrichi est disponible pour vous permettre de créer votre charge utile de message électronique.

    - Utilisez le contrôle **de balise dynamique** pour personnaliser le message électronique de chaque utilisateur en insérant les balises disponibles :
      - **Nom d’insertion** : la valeur ajoutée dans le corps du message est `${userName}`.
      - **Insérer un e-mail** : la valeur ajoutée dans le corps du message est `${emailAddress}`.

      :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Section E-mail de la page Configurer la charge utile dans l’Assistant Création de charge utile dans l’entraînement de simulation d’attaque dans Microsoft Defender pour Office 365" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

      **Contrôle de lien d’hameçonnage** : ce contrôle n’est disponible que si vous avez sélectionné **La collecte des informations d’identification**, **lier en pièce jointe** ou **l’URL drive-by** sur la page **Sélectionner la technique** . Utilisez ce contrôle pour insérer l’URL que vous avez sélectionnée précédemment dans la section **Lien d’hameçonnage** .

      **Contrôle de lien de pièce jointe** de programme malveillant : ce contrôle n’est disponible que si vous avez sélectionné **Lien vers un programme malveillant** dans la page **Sélectionner la technique** . Utilisez ce contrôle pour insérer l’URL que vous avez précédemment sélectionnée dans la section **Lien pour pièce jointe** .

      Si vous cliquez sur **le lien Hameçonnage** ou le **lien de pièce jointe du programme malveillant**, une boîte de dialogue s’ouvre pour vous demander de nommer le lien. Lorsque vous avez terminé, cliquez sur **Confirmer**.

      La valeur ajoutée dans le corps du message (visible sous l’onglet **Code** ) est `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

  - Sous l’onglet **Code** , vous pouvez afficher et modifier le code HTML directement. La mise en forme et d’autres contrôles tels que la **balise dynamique** et le **lien hameçonnage** ou **le lien De pièces jointes de programme malveillant** ne sont pas disponibles.

  - Le bouton **Bascule Remplacer tous les liens du message électronique par le bouton bascule de lien d’hameçonnage** n’est disponible que si vous avez sélectionné La **collecte des informations d’identification**, **Lien vers un programme malveillant** ou **URL drive-by** sur la page **Sélectionner la technique** . Ce bouton bascule peut gagner du temps en remplaçant tous les liens du message par le **lien d’hameçonnage** ou l’URL de **la pièce jointe** précédemment sélectionné. Pour ce faire, activez le paramètre sur ![Activer l’icône bascule.](../../media/scc-toggle-on.png)

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="add-indicators-to-phishing-clues"></a>Ajouter des indicateurs aux indices d’hameçonnage

> [!NOTE]
> Les indicateurs ne sont pas disponibles si vous avez sélectionné **La pièce jointe** ou **lier des programmes malveillants à des programmes malveillants** dans la page **Sélectionner une technique** .

Les indicateurs aident les employés qui passent par la simulation d’attaque à identifier les signes révélateurs des messages de hameçonnage.

Dans la page **Ajouter des indicateurs** , cliquez sur **Ajouter un indicateur**. Dans le menu volant qui s’affiche, configurez les paramètres suivants :

- **Nom de l’indicateur** et **emplacement de l’indicateur** : ces valeurs sont liées. L’emplacement où vous pouvez placer l’indicateur dépend de l’indicateur lui-même. Les valeurs disponibles sont décrites dans le tableau suivant :

  |Nom de l’indicateur|Emplacement de l’indicateur|
  |---|---|
  |**Type de pièce jointe**|Corps du message|
  |**Détails distrayants**|Corps du message|
  |**Usurpation de domaine**|Corps du message <p> À partir de l’adresse e-mail|
  |**Message d’accueil générique**|Corps du message|
  |**Appels humanitaires**|Corps du message|
  |**Incohérence**|Corps du message|
  |**Absence de détails sur l’expéditeur**|Corps du message|
  |**Langage juridique**|Corps du message|
  |**Offre limitée dans le temps**|Corps du message|
  |**Imitation de logo ou personnalisation datée**|Corps du message|
  |**Imite un processus professionnel ou professionnel**|Corps du message|
  |**Personnalisation non/minimale**|Corps du message|
  |**Pose en tant qu’ami, collègue, superviseur ou figure d’autorité**|Corps du message|
  |**Demande d’informations sensibles**|Corps du message|
  |**Icônes et indicateurs de sécurité**|Corps du message <p> Objet du message|
  |**Nom d’affichage et adresse e-mail de l’expéditeur**|À partir du nom <p> À partir de l’adresse e-mail|
  |**Sentiment d’urgence**|Corps du message <p> Objet du message|
  |**Fautes d’orthographe et de grammaire**|Corps du message <p> Objet du message|
  |**Langue menaçante**|Corps du message <p> Objet du message|
  |**Trop beau pour être de vraies offres**|Corps du message|
  |**Conception ou mise en forme non professionnelle**|Corps du message|
  |**Lien hypertexte d’URL**|Corps du message|
  |**Vous êtes spécial.**|Corps du message|
  
  Cette liste est organisée pour contenir les indices les plus courants qui apparaissent dans les messages de hameçonnage.

  Si vous **sélectionnez** l’objet du message électronique ou le corps du message comme emplacement de l’indicateur, un bouton Sélectionner un texte est disponible. Cliquez sur ce bouton pour sélectionner le texte dans l’objet du message ou le corps du message où vous souhaitez que l’indicateur apparaisse. Lorsque vous avez terminé, cliquez sur **Sélectionner**.

  :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Emplacement du texte sélectionné dans le corps du message à ajouter à un indicateur dans l’Assistant Création de charge utile dans l’entraînement de simulation d’attaque" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

  - **Description de** l’indicateur : vous pouvez accepter la description par défaut de l’indicateur ou le personnaliser.

  - **Aperçu de** l’indicateur : pour voir à quoi ressemble l’indicateur actuel, cliquez dans cette section.

  Lorsque vous avez terminé, cliquez sur **Ajouter**

Répétez les étapes de cette section pour ajouter plusieurs indicateurs.

Pour modifier un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur l’icône ![Modifier l’indicateur.](../../media/m365-cc-sc-edit-icon.png) **Modifiez la charge utile**.

Pour supprimer un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="review-payload"></a>Examiner la charge utile

Dans la page **Examiner la charge utile** , vous pouvez passer en revue les détails de votre charge utile.

Cliquez sur l’icône ![Envoyer un test.](../../media/m365-cc-sc-send-icon.png) **Envoyez un bouton de test** pour vous envoyer une copie de l’e-mail de charge utile (l’utilisateur actuellement connecté) à des fins d’inspection.

Cliquez sur l’icône d’indicateur d’aperçu ![.](../../media/m365-cc-sc-open-icon.png) **Le bouton Aperçu de l’indicateur** ouvre la charge utile dans un menu volant d’aperçu. La préversion inclut tous les indicateurs de charge utile que vous avez créés.

Dans la page principale **de la charge utile de révision** , vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

Lorsque vous avez terminé, cliquez sur **Envoyer**. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

:::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Page Examiner la charge utile dans l’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

> [!IMPORTANT]
> Les charges utiles que vous avez créées ont la valeur **Locataire** pour la propriété **Source** . Lorsque vous créez des simulations et sélectionnez des charges utiles, veillez à ne pas filtrer le **locataire** de valeur **source**.

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Découvrez les formations à la simulation d’attaque](attack-simulation-training-insights.md)
