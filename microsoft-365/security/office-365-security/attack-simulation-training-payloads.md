---
title: Charges utiles pour l’entraînement de simulation d’attaque
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
description: Les administrateurs peuvent apprendre à créer et à gérer des charges utiles pour la formation à la simulation d’attaque dans Microsoft Defender pour Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: a21e3e72e435e9aaa53fb5fab825be6c490017fe
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840230"
---
# <a name="payloads-for-attack-simulation-training-in-defender-for-office-365"></a>Formation à la simulation d’attaque pour les charges utiles dans Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans la formation de simulation d’attaque, une _charge utile_ est le message électronique de hameçonnage et les liens ou le contenu de pièce jointe qui sont présentés aux utilisateurs dans des simulations. La formation à la simulation d’attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2 offre un catalogue de charges utiles intégré robuste pour les techniques d’ingénierie sociale disponibles. Toutefois, vous souhaiterez peut-être créer des charges utiles personnalisées qui fonctionneront mieux pour votre organisation.

Pour afficher les charges utiles disponibles, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse \> **e-mail &** onglet **Simulation de simulation** **d’attaque** \> de collaboration\>, puis sélectionnez **Charges utiles**. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **Charges utiles**, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Les charges utiles** de l’onglet **Bibliothèque de contenu simulation** comportent deux onglets :

- **Charges utiles globales** : contient les charges utiles intégrées non modifiables.
- **Charges utiles de locataire** : contient les charges utiles personnalisées que vous avez créées.

Les informations suivantes s’affichent pour chaque charge utile :

- **Nom de la charge utile**
- **Type** : Actuellement, cette valeur est toujours **des ingénieries sociales**.
- **Langue** : si la charge utile contient plusieurs traductions, les deux premières langues sont affichées directement. Pour afficher les langues restantes, pointez sur l’icône numérique (par exemple, **+10**).
- **Source** : pour les charges utiles intégrées, la valeur est **Global**. Pour les charges utiles personnalisées, la valeur est **Locataire**.
- **Simulations lancées** : nombre de simulations lancées qui utilisent la charge utile.
- **Taux compromis (%)**: pour les charges utiles intégrées, cette valeur correspond au taux de compromission moyen prédit pour les simulations d’entraînement de simulation d’attaque qui utilisent le même type de charge utile dans toutes les autres organisations Microsoft 365.
- **Créé par** : Pour les charges utiles intégrées, la valeur est **Microsoft**. Pour les charges utiles personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la charge utile.
- **Dernière modification**
- **Technique** : Une des [techniques d’ingénierie sociale](attack-simulation-training.md#select-a-social-engineering-technique) disponibles :
  - **Collecte des informations d’identification**
  - **Pièce jointe de programme malveillant**
  - **Lien dans la pièce jointe**
  - **Lien vers un programme malveillant**
  - **Drive-by URL**
- **État** : la valeur est **Ready** ou **Draft**. Sous l’onglet **Charges utiles globales** , la valeur est toujours **Prête**.

Pour rechercher une charge utile dans la liste, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom de la charge utile.

Clic  ![Icône filtre.](../../media/m365-cc-sc-filter-icon.png) pour filtrer les charges utiles d’une ou des valeurs suivantes :

- **Complexité** : **élevée**, **moyenne** et **faible**.
- **Language**
- **Ajouter des balises**
- **Theme**
- **Marque**
- **Secteur d’activité**
- **Événement actuel** : **Oui** ou **Non**.
- **Controversé** : **Oui** ou **Non**.

Pour supprimer une ou plusieurs colonnes affichées, cliquez sur ![l’icône Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes**. Par défaut, la seule colonne qui n’est pas affichée est **Platform**, et cette valeur est actuellement toujours **Email**.

Lorsque vous sélectionnez une charge utile dans la liste, un menu volant de détails s’affiche avec les informations suivantes :

- **Onglet Vue d’ensemble** : affichez la charge utile au fur et à mesure que les utilisateurs la verront. Les propriétés de charge utile sont également visibles :
  - **Description de la charge utile**
  - **À partir du nom**
  - **À partir de l’e-mail**
  - **Sujet de l’e-mail**
  - **Source** : pour les charges utiles intégrées, la valeur est **Global**. Pour les charges utiles personnalisées, la valeur est **Locataire**.
  - **Theme**
  - **Marque**
  - **Secteur d’activité**
  - **Controversé**
  - **Événement actuel**
  - **Tags**

- **Onglet Simulations lancées** :
  - **Nom de la simulation**
  - **Taux de clics**
  - **Taux compromis**
  - **Action**

## <a name="create-payloads"></a>Créer des charges utiles

> [!NOTE]
> Certaines marques, logos, symboles, insignias et autres identificateurs sources bénéficient d’une protection renforcée en vertu des lois et lois locales, d’État et fédérales. L’utilisation non autorisée de ces indicateurs peut exposer les utilisateurs à des sanctions, y compris des amendes pénales. Bien qu’il ne s’agit pas d’une liste exhaustive, il s’agit des scellés présidentiels, vice-présidentiels et du Congrès, de la CIA, du FBI, de la Sécurité sociale, de l’assurance-maladie et de Medicaid, du États-Unis internal revenue service et des Jeux olympiques. Au-delà de ces catégories de marques, l’utilisation et la modification d’une marque tierce comportent un risque inhérent. L’utilisation de vos propres marques et logos dans une charge utile serait moins risquée, en particulier lorsque votre organisation autorise l’utilisation. Si vous avez d’autres questions sur ce qui est ou n’est pas approprié à utiliser lors de la création ou de la configuration d’une charge utile, vous devez consulter vos conseillers juridiques.

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à l’onglet Charges utiles du locataire de la **simulation** \> d’attaque de l’onglet **e-mail & collaboration** \> simulation de **simulation** d’attaque sous l’onglet \> **Charges utiles** \> **du locataire payloads**. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **Charges utiles** et onglet **Charges utiles du locataire**, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

   Cliquez sur ![Créer une icône de charge utile.](../../media/m365-cc-sc-create-icon.png) **Créez une charge utile** sous l’onglet **Charges utiles du locataire** dans **Payloads** pour démarrer l’Assistant Création de charge utile.

   ![Créez une charge utile sous l’onglet Charges utiles du locataire dans Payloads in Attack simulation training in the Microsoft 365 Defender portal.](../../media/attack-sim-training-payload-create.png)

   > [!NOTE]
   > ![Créer une icône de charge utile.](../../media/m365-cc-sc-create-icon.png) **Créer une charge utile** est également disponible sur la page **Sélectionner la charge utile** de l’Assistant création de simulation. Pour plus d’informations, consultez [Simuler une attaque par hameçonnage dans Defender pour Office 365](attack-simulation-training.md).
   >
   > À tout moment pendant l’Assistant création, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer la charge utile ultérieurement. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant la notification sous l’onglet **Charges utiles du locataire** dans **Charges utiles**, puis en ![cliquant sur l’icône Modifier la charge utile.](../../media/m365-cc-sc-edit-icon.png) **Modifiez la charge utile**. La charge utile partiellement terminée aura la valeur **d’état** **Draft**.

2. Dans la page **Sélectionner un type** , la seule valeur que vous pouvez sélectionner actuellement est **e-mail**.

   Cliquez sur **Suivant**.

3. Dans la page **Sélectionner une technique** , les options disponibles sont les mêmes que dans la page **Sélectionner une technique** dans l’Assistant Création de simulation :

   - **Collecte des informations d’identification**
   - **Pièce jointe de programme malveillant**
   - **Lien dans la pièce jointe**
   - **Lien vers un programme malveillant**
   - **Drive-by URL**

   Pour plus d’informations, consultez [Simuler une attaque par hameçonnage avec l’entraînement de simulation d’attaque dans Defender pour Office 365](attack-simulation-training.md).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Nom de la charge utile** , configurez les paramètres suivants :

   - **Nom** : entrez un nom unique et descriptif pour la charge utile.
   - **Description** : entrez une description détaillée facultative pour la charge utile.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Configurer la charge utile** , il est temps de générer votre charge utile. La plupart des paramètres disponibles sont déterminés par la sélection que vous avez effectuée sur la page **Sélectionner la technique** (par exemple, les liens et les pièces jointes).

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

   - Paramètres courants sur la page **Configurer la charge utile** :

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
         - **Insérer un nom d’utilisateur** : la valeur ajoutée dans le corps du message est `${userName}`.
         - **Insérer le prénom** : la valeur ajoutée dans le corps du message est `${firstName}`.
         - **Insérer le nom** : la valeur ajoutée dans le corps du message est `${lastName}`.
         - **Insérer upn** : la valeur ajoutée dans le corps du message est `${upn}`.
         - **Insérer un e-mail** : la valeur ajoutée dans le corps du message est `${emailAddress}`.
         - **Insérer le service** : la valeur ajoutée dans le corps du message est `${department}`.
         - **Gestionnaire d’insertion** : la valeur ajoutée dans le corps du message est `${manager}`.
         - **Insérer un téléphone mobile** : la valeur ajoutée dans le corps du message est `${mobilePhone}`.
         - **Insérer une ville** : la valeur ajoutée dans le corps du message est `${city}`.
         - **Date d’insertion** : la valeur ajoutée dans le corps du message est `${date|MM/dd/yyyy|offset}`.

         :::image type="content" source="../../media/attack-sim-training-payloads-configure-payload-email-message.png" alt-text="Section E-mail de la page Configurer la charge utile dans l’Assistant Création de charge utile dans l’entraînement de simulation d’attaque dans Microsoft Defender pour Office 365" lightbox="../../media/attack-sim-training-payloads-configure-payload-email-message.png":::

       - **Contrôle de lien d’hameçonnage** : ce contrôle n’est disponible que si vous avez sélectionné **La collecte des informations d’identification**, **lier en pièce jointe** ou **l’URL drive-by** sur la page **Sélectionner la technique** . Utilisez ce contrôle pour nommer et insérer l’URL que vous avez sélectionnée précédemment dans la section **Lien d’hameçonnage** .

       - **Contrôle de lien de pièce jointe** de programme malveillant : ce contrôle n’est disponible que si vous avez sélectionné **Lien vers un programme malveillant** dans la page **Sélectionner la technique** . Utilisez ce contrôle pour nommer et insérer l’URL que vous avez précédemment sélectionnée dans la section **Lien pour pièce jointe** .

       Lorsque vous cliquez sur **le lien Hameçonnage** ou le **lien De pièces jointes de programme malveillant**, une boîte de dialogue s’ouvre pour vous demander de nommer le lien. Lorsque vous avez terminé, cliquez sur **Confirmer**.

       La valeur ajoutée dans le corps du message (visible sous l’onglet **Code** ) est `<a href="${phishingUrl}" target="_blank">Name value you specified</a>`.

     - Sous l’onglet **Code** , vous pouvez afficher et modifier le code HTML directement. La mise en forme et d’autres contrôles tels que la **balise dynamique** et le **lien hameçonnage** ou **le lien De pièces jointes de programme malveillant** ne sont pas disponibles.

     - Le bouton **Bascule Remplacer tous les liens du message électronique par le bouton bascule de lien d’hameçonnage** n’est disponible que si vous avez sélectionné La **collecte des informations d’identification**, **Lien vers un programme malveillant** ou **URL drive-by** sur la page **Sélectionner la technique** . Ce bouton bascule peut gagner du temps en remplaçant tous les liens du message par le **lien d’hameçonnage** ou l’URL de **la pièce jointe** précédemment sélectionné. Pour ce faire, activez le paramètre sur ![Activer l’icône bascule.](../../media/scc-toggle-on.png)

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. La page **Ajouter des indicateurs** n’est disponible que si vous avez sélectionné **La récolte des informations d’identification**, **lier en pièce jointe** ou **URL drive-by** dans la page **Sélectionner une technique** .

   Les indicateurs aident les employés à identifier les signes de détection des messages d’hameçonnage.

   Dans la page **Ajouter des indicateurs** , cliquez sur **Ajouter un indicateur**. Dans le menu volant qui s’affiche, configurez les paramètres suivants :

   - **Sélectionnez et indiquez que vous souhaitez utiliser** et **où voulez-vous placer cet indicateur sur la charge utile ?** :

     Ces valeurs sont liées entre elles. L’emplacement où vous pouvez placer l’indicateur dépend du type d’indicateur. Les valeurs disponibles sont décrites dans le tableau suivant :

     |Type d’indicateur|Emplacement de l’indicateur|
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

     Si vous **sélectionnez** l’objet du message électronique ou le corps du message comme emplacement de l’indicateur, un bouton Sélectionner un texte s’affiche. Cliquez sur ce bouton pour sélectionner le texte dans l’objet du message ou le corps du message où vous souhaitez que l’indicateur apparaisse. Lorsque vous avez terminé, cliquez sur **Sélectionner**.

     :::image type="content" source="../../media/attack-sim-training-payloads-add-indicators-select-location.png" alt-text="Emplacement du texte sélectionné dans le corps du message à ajouter à un indicateur dans l’Assistant Création de charge utile dans l’entraînement de simulation d’attaque" lightbox="../../media/attack-sim-training-payloads-add-indicators-select-location.png":::

     - **Description de** l’indicateur : vous pouvez accepter la description par défaut de l’indicateur ou le personnaliser.

     - **Aperçu de** l’indicateur : pour voir à quoi ressemble l’indicateur actuel, cliquez n’importe où dans la section.

     Lorsque vous avez terminé, cliquez sur **Ajouter**

   Répétez ces étapes pour ajouter plusieurs indicateurs.

   De retour sur la page **Ajouter des indicateurs** , vous pouvez passer en revue les indicateurs que vous avez sélectionnés :

   - Pour modifier un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur l’icône ![Modifier l’indicateur.](../../media/m365-cc-sc-edit-icon.png) **Modifier l’indicateur**.

   - Pour supprimer un indicateur existant, sélectionnez-le dans la liste, puis cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**.

   - Pour déplacer des indicateurs vers le haut ou vers le bas dans la liste, sélectionnez l’indicateur dans la liste, puis cliquez sur l’icône ![Monter.](../../media/m365-cc-sc-increase-icon.png) **Icône Monter** ou ![Descendre.](../../media/m365-cc-sc-decrease-icon.png) **Descends**.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Examiner la charge utile** , vous pouvez passer en revue les détails de votre charge utile.

   Cliquez sur l’icône ![Envoyer un test.](../../media/m365-cc-sc-send-icon.png) **Envoyez un bouton de test** pour vous envoyer une copie de l’e-mail de charge utile (l’utilisateur actuellement connecté) à des fins d’inspection.

   Cliquez sur l’icône d’indicateur d’aperçu ![.](../../media/m365-cc-sc-open-icon.png) **Le bouton Aperçu de l’indicateur** ouvre la charge utile dans un menu volant d’aperçu. La préversion inclut tous les indicateurs de charge utile que vous avez créés.

   Dans la page principale **de la charge utile de révision** , vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

   :::image type="content" source="../../media/attack-sim-training-payloads-review-payload.png" alt-text="Page Examiner la charge utile dans l’entraînement de simulation d’attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-payloads-review-payload.png":::

## <a name="modify-payloads"></a>Modifier des charges utiles

Vous ne pouvez pas modifier les charges utiles intégrées sous l’onglet **Charges utiles globales** . Vous pouvez uniquement modifier des charges utiles personnalisées sous l’onglet **Charges utiles du locataire** .

Pour modifier une charge utile existante sous l’onglet **Charges utiles du locataire** , effectuez l’une des étapes suivantes :

- Sélectionnez la charge utile dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône Modifier la ![charge utile.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier la charge utile** qui s’affiche.
- Sélectionnez la charge utile dans la liste en cliquant n’importe où dans la ligne, à l’exception de la case à cocher. Dans le menu volant d’informations qui s’ouvre, cliquez sur **Modifier la charge utile**.

L’Assistant charge utile s’ouvre avec les paramètres et les valeurs de la charge utile sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des charges utiles](#create-payloads) .

## <a name="copy-payloads"></a>Copier des charges utiles

Pour copier une charge utile existante sous les **onglets Charges utiles du locataire** ou **Charges utiles globales** , sélectionnez la charge utile dans la liste en cochant la case, puis cliquez sur l’icône Copier la ![charge utile.](../../media/m365-cc-sc-edit-icon.png) **Icône de charge utile de copie** qui s’affiche.

L’Assistant Création d’une charge utile s’ouvre avec les paramètres et les valeurs de la charge utile sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des charges utiles](#create-payloads) .

> [!NOTE]
> Lorsque vous copiez une charge utile intégrée sous l’onglet **Charges utiles globales** , veillez à modifier la valeur **Name** . Si ce n’est pas le cas, la charge utile s’affiche sur la page **Charges utiles du locataire** avec le même nom que la charge utile intégrée.

## <a name="send-a-test"></a>Envoyer un test

Sous les **onglets Charges utiles du locataire** ou **Charges utiles globales** , vous pouvez vous envoyer une copie de l’e-mail de charge utile (l’utilisateur actuellement connecté) à des fins d’inspection.

Sélectionnez la charge utile dans la liste en cochant la case, puis cliquez sur l’icône ![Envoyer un test.](../../media/m365-cc-sc-send-icon.png) **Envoyer un bouton de test** qui s’affiche.

## <a name="related-links"></a>Liens connexes

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Découvrez les formations à la simulation d’attaque](attack-simulation-training-insights.md)
