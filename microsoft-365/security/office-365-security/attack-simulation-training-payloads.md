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
ms.custom: admindeeplinkDEFENDER
description: Les administrateurs peuvent apprendre à créer des charges utiles personnalisées pour la formation à la simulation d’attaques dans Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 79e530a6635079bcf262b23e887f06ab5ebe79b3
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2021
ms.locfileid: "60962878"
---
# <a name="create-custom-payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Créer des charges utiles personnalisées pour la formation à la simulation d’attaques dans Defender pour Office 365

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans la formation à la simulation d’attaque, une charge _utile_ est le message électronique de hameçonnage et les pages web présentées aux utilisateurs dans des simulations. La formation à la simulation d’attaques dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2 offre un catalogue de charges utiles intégré robuste pour les techniques d’ingénierie sociale disponibles. Toutefois, vous pouvez créer des charges utiles personnalisées qui fonctionneront mieux pour votre organisation.

Cet article explique comment créer vos propres charges utiles dans une formation à la simulation d’attaques. Vous pouvez créer des charges utiles personnalisées aux emplacements suivants :

- Onglet **Charges utiles** : Dans le portail Microsoft 365 Defender à l’adresse , go <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> to Email & **collaboration** Attack \> **simulation** \> **payloads** tab. Pour aller directement à l’onglet **Charges utiles,** utilisez <https://security.microsoft.com/attacksimulator?viewid=payload> .
- Lors de la création de la simulation : vous pouvez créer des charges utiles personnalisées dans la **page** Sélectionner une charge utile (la troisième page) de l’Assistant de création de simulation. Pour plus d’informations, voir Simuler une attaque par [hameçonnage dans Defender pour Office 365](attack-simulation-training.md).

Pour plus d’informations sur la formation à la simulation d’attaques, voir [Commencer à utiliser la formation sur la simulation d’attaque.](attack-simulation-training-get-started.md)

> [!NOTE]
> Certaines marques, logos, symboles, insignias et autres identificateurs source bénéficient d’une protection renforcée en vertu de lois et lois locales, nationales et fédérales. L’utilisation non autorisée de ces indicateurs peut imposer des sanctions aux utilisateurs, y compris des amendes pénales. Bien qu’il ne s’agit pas d’une liste complète, il s’agit notamment des personnes qui ont l’avantage de ne pas avoir à se servir de cette liste. Au-delà de ces catégories de marques, l’utilisation et la modification d’une marque tierce impliquent un risque inhérent. L’utilisation de vos propres marques et logos dans une charge utile serait moins risquée, en particulier lorsque votre organisation autorise l’utilisation. Si vous avez d’autres questions sur ce qui est approprié ou non à utiliser lors de la création ou de la configuration d’une charge utile, vous devez consulter vos conseillers juridiques.

## <a name="create-a-payload"></a>Créer une charge utile

Après avoir cliqué ![ sur Créer une icône de charge utile.](../../media/m365-cc-sc-create-icon.png) **Créez une** charge utile à partir de l’onglet **Charge utile** de la formation sur la simulation d’attaque ou, dans la **[page](attack-simulation-training.md#select-a-payload)** Sélectionner une charge utile de l’Assistant création de simulation, l’Assistant de création de charge utile démarre et est décrit dans cette section.

### <a name="select-a-payload-type"></a>Sélectionner un type de charge utile

Dans la page **Sélectionner un type,** la seule valeur que vous pouvez actuellement sélectionner est **Email**.

Cliquez sur **Suivant**.

### <a name="select-a-social-engineering-technique"></a>Sélectionner une technique d’ingénierie sociale

Dans la page **Sélectionner une technique,** les options disponibles sont les mêmes que dans la page Sélectionner [une technique](attack-simulation-training.md#select-a-social-engineering-technique) de l’Assistant création de simulation :

- **Informations d’identification**
- **Pièce jointe de programme malveillant**
- **Lien dans la pièce jointe**
- **Lien vers un programme malveillant**
- **URL de lecteur par**

Lorsque vous avez terminé, cliquez sur **Suivant**.

### <a name="name-and-describe-the-payload"></a>Nommer et décrire la charge utile

Dans la page **Nom de la** charge utile, configurez les paramètres suivants :

- **Nom**: entrez un nom unique et descriptif pour la charge utile.
- **Description**: entrez une description détaillée facultative de la charge utile.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="configure-the-payload"></a>Configurer la charge utile

Dans la page **Configurer la** charge utile, il est temps de créer votre charge utile. La plupart des paramètres disponibles sont déterminés par la sélection que vous avez faite sur la page **de technique** Sélectionner (par exemple, les liens et les pièces jointes).

- **Section Détails de l’expéditeur** : Configurez les paramètres suivants :
  - **De nom**
  - **Utilisez le prénom comme nom d’affichage**: par défaut, ce paramètre n’est pas sélectionné.
  - **À partir du** courrier électronique : si vous choisissez une adresse de messagerie interne pour l’expéditeur de votre charge utile, la charge utile semblera être un collègue. Cette adresse de messagerie de l’expéditeur augmente la sensibilité de l’utilisateur à la charge utile et aide à informer les employés sur les risques de menaces internes.
  - **Sujet de l’e-mail**

- **Section Détails de la** pièce jointe : cette section est disponible  uniquement si vous avez sélectionné la pièce jointe anti-programme **malveillant,** le lien dans la pièce jointe ou le lien vers des programmes malveillants dans la page de **technique Sélectionner.** Configurez les paramètres suivants :
  - **Nommer votre pièce jointe**
  - **Sélectionnez un type de pièce** jointe : Actuellement, la seule valeur disponible est **Docx**.

- **Lien pour la** section pièce jointe : cette section est disponible uniquement si vous avez sélectionné Lien vers un programme malveillant **dans** la page Sélectionner **une technique.** Dans la **zone** Sélectionner une **URL** qui doit être votre lien de pièce jointe contre les programmes malveillants, sélectionnez l’une des URL disponibles (les mêmes URL décrites pour la section Lien de hameçonnage).

  Plus tard, vous incorporerez l’URL dans le corps du message.

- **Section Lien de hameçonnage** : cette section est disponible uniquement si vous avez sélectionné la recherche d’informations d’identification, le lien dans la pièce jointe ou l’URL de lecteur sur la page de technique **Sélectionner.** 

  Pour **la recherche d’informations** d’identification ou **l’URL** de lecteur par lecteur, le nom de la zone est Sélectionner une URL que vous souhaitez être votre lien **de hameçonnage.** Plus tard, vous incorporerez l’URL dans le corps du message.

  Pour **le lien dans la pièce** jointe, le nom de la zone est Sélectionner une URL dans cette pièce jointe que vous souhaitez être votre lien de **hameçonnage.** Plus tard, vous incorporerez l’URL dans la pièce jointe.

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
  > Un service de réputation d’URL peut identifier une ou plusieurs de ces URL comme étant non sécurisées. Vérifiez la disponibilité de l’URL dans vos navigateurs web pris en charge avant d’utiliser l’URL dans une simulation. Pour plus d’informations, voir URL de simulation de hameçonnage bloquées par [Google Coffre navigation.](attack-simulation-training-faq.md#phishing-simulation-urls-blocked-by-google-safe-browsing)

- **Section Contenu des** pièces jointes : cette section est disponible uniquement si vous avez sélectionné **Lien** dans la pièce jointe dans la page Sélectionner **une technique.**

  Un éditeur de texte enrichi est disponible pour créer le contenu de la charge utile de votre pièce jointe de fichier.

  Utilisez le **contrôle de lien de hameçonnage** pour ajouter l’URL de hameçonnage précédemment sélectionnée à la pièce jointe.

- Paramètres courants :
  - **Ajouter des balises**
  - Thème : les valeurs disponibles sont : **Activation** du **compte,** vérification de **compte,** facturation **,** nettoyage du courrier , **document** reçu **,** dépense , **télécopie**, rapport **financier** **,** messages entrants **,** **facture**, élément reçu **,** alerte de connexion **,** courrier reçu **,** autre **,** mot de passe **,** paiement **,** paie , **offre** personnalisée **,** mise en quarantaine , **Travail à distance**, Passer en revue le **message**, **Mise** à jour de sécurité , **Service** suspendu , **Signature** requise , Mettre à niveau la boîte aux **lettres Stockage**, vérifier la boîte aux lettres ou la messagerie **vocale**. 
  - **Marque**: les valeurs disponibles sont **: American Express**, Capital **One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, Netflix , **Netflix** **,Bank,** **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Cloud Syrinx**, ou **autre**.
  - **Secteur** d’activité : les valeurs disponibles sont : **Banque,** **Services** professionnels, **Services** grand public, **Éducation,** **Énergie,** **Construction,** **Conseil**, **Services** financiers, **Secteur public,** **Hôpital,** **Assurance,** **Juridique,** **Courier services,** **INFORMATIQUE,** Soins de **santé,** **Fabrication,** **Commerce,** **Telecom,** **Immobilier,** ou **Autre**.
  - **Événement actuel**: les valeurs disponibles sont **Oui** ou **Non**.
  - **Politique**: les valeurs disponibles sont **Oui** ou **Non**.

- **Section Langue** : sélectionnez la langue pour la charge utile. Les valeurs disponibles sont : **anglais** **,** espagnol **,** **allemand** **,** japonais **,** français **,** portugais **,** néerlandais , italien , **suédois**, chinois **(simplifié)**, norvégien **Bokmål**, **polonais** **,** russe , **finnois** **,** coréen **,** turc **,** hongrois **,** hébreu **,** thaï **,** **arabe**, vietnamien **,** slovaque , **grec**, **indonésien**, **roumain**, **slovène** **,** croate , **catalan** ou **autre**.

- **Section Message électronique** :

  - Vous pouvez cliquer **sur Importer le courrier** électronique, puis choisir un **fichier** pour importer un fichier de message en texte simple existant.

  - Sous **l’onglet Texte,** un éditeur de texte enrichi est disponible pour créer la charge utile de votre message électronique.

    - Utilisez le **contrôle de balise dynamique** pour personnaliser le message électronique de chaque utilisateur en insérant les balises disponibles :
      - **Nom d’insertion**: la valeur ajoutée dans le corps du message est `${userName}` .
      - **Insérer un** e-mail : la valeur ajoutée dans le corps du message est `${emailAddress}` .

      ![La section Message électronique de la page Configurer la charge utile dans l’Assistant Création de la charge utile dans la formation sur la simulation d’attaque dans Microsoft Defender Office 365.](../../media/attack-sim-training-payloads-configure-payload-email-message.png)

      **Contrôle de lien de** hameçonnage : ce contrôle est disponible uniquement si vous avez sélectionné la recherche d’informations d’identification, le lien dans la pièce jointe ou l’URL de lecteur sur la page **de technique Sélectionner.**   Utilisez ce contrôle pour insérer l’URL que vous avez précédemment sélectionnée dans la section Lien **de hameçonnage.**

      **Contrôle de lien de** pièce jointe de programmes malveillants : ce contrôle est disponible uniquement si vous avez sélectionné Lien vers un programme malveillant **dans** la page **Sélectionner une technique.** Utilisez ce contrôle pour insérer l’URL que vous avez précédemment sélectionnée dans la section Lien pour la pièce **jointe.**

      Si vous cliquez sur **lien hameçonnage** ou lien de pièce jointe anti-programme **malveillant,** une boîte de dialogue s’ouvre et vous demande de nommer le lien. Lorsque vous avez terminé, cliquez sur **Confirmer.**

      La valeur ajoutée dans le corps du message (visible sous **l’onglet Code)** est `<a href="${phishingUrl}" target="_blank">Name value you specified</a>` .

  - Sous **l’onglet Code,** vous pouvez afficher et modifier directement le code HTML. La mise en forme et d’autres contrôles tels que la balise **dynamique** et le lien de **hameçonnage** ou le lien de pièce jointe anti-programme malveillant **ne** sont pas disponibles.

  - Le basculement Remplacer tous les liens du **message** électronique par le basculement de lien de hameçonnage est disponible uniquement si vous avez sélectionné la recherche d’informations d’identification, le lien vers un programme malveillant ou l’URL de lecteur sur la page Sélectionner une **technique.**  Ce basculement peut gagner du temps en remplaçant tous les  liens du message par le lien de hameçonnage ou l’URL  de pièce jointe précédemment sélectionné. Pour ce faire, basculez le paramètre sur l’icône ![ Bascule. ](../../media/scc-toggle-on.png)

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="add-indicators-to-phishing-clues"></a>Ajouter des indicateurs à des indices de hameçonnage

> [!NOTE]
> Les indicateurs ne sont pas  disponibles si vous avez sélectionné une pièce jointe anti-programme malveillant ou un lien vers un programme malveillant **dans** la page Sélectionner **une technique.**

Les indicateurs aident les employés à passer par la simulation d’attaque pour identifier les signes de message d’hameçonnage.

Dans la page **Ajouter des indicateurs,** cliquez **sur Ajouter un indicateur.** Dans le volant qui s’affiche, configurez les paramètres suivants :

- **Nom de l’indicateur** **et emplacement de l’indicateur**: ces valeurs sont interdépendantes. L’endroit où vous pouvez placer l’indicateur dépend de l’indicateur lui-même. Les valeurs disponibles sont décrites dans le tableau suivant :

  <br>

  ****

  |Nom de l’indicateur|Emplacement de l’indicateur|
  |---|---|
  |**Type de pièce jointe**|Corps du message|
  |**Détails gênants**|Corps du message|
  |**Usurpation de domaine**|Corps du message <p> À partir de l’adresse e-mail|
  |**Message d’accueil générique**|Corps du message|
  |**Appels d’assistance**|Corps du message|
  |**Incohérence**|Corps du message|
  |**Absence de détails sur l’expéditeur**|Corps du message|
  |**Langage juridique**|Corps du message|
  |**Offre de temps limitée**|Corps du message|
  |**Logo logo logo ou branding obsolète**|Corps du message|
  |**Imite un processus de travail ou d’entreprise**|Corps du message|
  |**Branding non/minimal**|Corps du message|
  |**Se pose en tant qu’ami, collègue, superviseur ou figure d’autorité**|Corps du message|
  |**Demande d’informations sensibles**|Corps du message|
  |**Indicateurs et icônes de sécurité**|Corps du message <p> Objet du message|
  |**Nom d’affichage de l’expéditeur et adresse e-mail**|De nom <p> À partir de l’adresse e-mail|
  |**Sentiment d’urgence**|Corps du message <p> Objet du message|
  |**Fautes d’orthographe et de grammaire**|Corps du message <p> Objet du message|
  |**Langue de l’anglais**|Corps du message <p> Objet du message|
  |**Trop bon pour être de vraies offres**|Corps du message|
  |**Conception ou mise en forme non professionnelle**|Corps du message|
  |**Lien hypertexte d’URL**|Corps du message|
  |**Vous êtes spécial**|Corps du message|
  |
  
  Cette liste est organisée pour contenir les indices les plus courants qui apparaissent dans les messages d’hameçonnage.

  Si vous sélectionnez l’objet du message électronique ou  le corps du message comme emplacement pour l’indicateur, un bouton Sélectionner un texte est disponible. Cliquez sur ce bouton pour sélectionner le texte dans l’objet ou le corps du message où vous souhaitez que l’indicateur apparaisse. Lorsque vous avez terminé, cliquez sur **Sélectionner.**

  ![Emplacement du texte sélectionné dans le corps du message à ajouter à un indicateur dans l’Assistant Création de la charge utile dans la formation sur la simulation d’attaque.](../../media/attack-sim-training-payloads-add-indicators-select-location.png)

  - **Description de l’indicateur**: vous pouvez accepter la description par défaut de l’indicateur ou la personnaliser.

  - **Aperçu de l’indicateur**: pour voir à quoi ressemble l’indicateur actuel, cliquez dans cette section.

  Lorsque vous avez terminé, cliquez sur **Ajouter**

Répétez les étapes de cette section pour ajouter plusieurs indicateurs.

Pour modifier un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur Icône Modifier ![ l’indicateur.](../../media/m365-cc-sc-edit-icon.png) **Modifier la charge utile**.

Pour supprimer un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur ![ Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="review-payload"></a>Examiner la charge utile

Dans la page **Examiner la** charge utile, vous pouvez passer en revue les détails de votre charge utile.

Cliquez sur ![ l’icône Envoyer un test.](../../media/m365-cc-sc-send-icon.png) **Envoyez un bouton de test** pour envoyer une copie de l’e-mail de charge utile à vous-même (l’utilisateur actuellement connecté) pour inspection.

Cliquez sur ![ l’icône de l’indicateur d’aperçu.](../../media/m365-cc-sc-open-icon.png) **Le bouton d’indicateur** d’aperçu ouvre la charge utile dans un aperçu volant. L’aperçu inclut tous les indicateurs de charge utile que vous avez créés.

Dans la page principale **de la** charge utile de révision, vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

Lorsque vous avez terminé, cliquez sur **Envoyer**. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

![Examinez la page de charge utile dans la formation sur la simulation d’attaques Microsoft 365 Defender portail.](../../media/attack-sim-training-payloads-review-payload.png)

> [!IMPORTANT]
> Les charges utiles que vous avez créées auront la valeur **Client** pour la **propriété Source.** Lorsque vous créez des simulations et sélectionnez des charges utiles, veillez à ne pas filtrer la valeur **source** **Client**.

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Découvrez les formations à la simulation d’attaque](attack-simulation-training-insights.md)
