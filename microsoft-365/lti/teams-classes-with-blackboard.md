---
title: Utiliser des classes Microsoft Teams avec Blackboard Learn Ultra
ms.author: danismith
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Utilisez les classes Microsoft Teams avec Blackboard Learn Ultra.
ms.openlocfilehash: 6e133b01dc2c70e87812e88590055fb48b6cbb99
ms.sourcegitcommit: cd9df1a681265905eef99c039f7036b2fa6e8b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2022
ms.locfileid: "67275909"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Utiliser des classes Microsoft Teams avec Blackboard Learn Ultra

Le travail d’équipe est au cœur de chaque organisation moderne. En favorisant la collaboration, il s’agit d’une caractéristique essentielle de chaque établissement qui réussit. Vous pouvez améliorer toutes les fonctionnalités de Blackboard Learn Ultra en les associant à des classes Microsoft Teams.

Vos classes peuvent inclure des conversations en temps réel, des réunions vidéo ou des interactions asynchrones. Vous pouvez ajouter des expériences de partage et de cocréation de fichiers pour vos étudiants, le tout au même endroit. Les classes Microsoft Teams avec Learn Ultra redéfinissent la dynamique de l’enseignement et ce que signifie l’apprentissage efficace.

> [!IMPORTANT]
> Vérifiez que vous avez correctement configuré le champ Institution Email dans votre [système d’information des étudiants (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>L’intégration des classes Microsoft Teams s’appuie sur le champ de messagerie de l’établissement dans votre SIS pour mapper au nom d’utilisateur principal [(UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) de l’Microsoft Azure Active Directory (AAD) correct. Si aucun e-mail d’établissement n’a été approvisionné, il s’agit par défaut de l’e-mail existant. Il est recommandé de définir ce champ pour que chaque utilisateur s’assure que ses données sont synchronisées correctement et qu’il n’existe aucun conflit de données de messagerie entre AAD et Blackboard Learn Ultra.
>
> Si vous n’avez pas défini ce champ correctement dans votre mappage SIS, l’intégration continue de fonctionner, mais les utilisateurs peuvent ne pas apparaître dans les classes Teams créées et des erreurs peuvent se produire.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Prise en charge du mappage des données institutionnelles – Domaine Email sis de l’établissement

Dans le cadre de l’évolution avec les intégrations de fournisseurs cloud, Blackboard Learn Ultra a créé un nouveau champ **Institution Email**, à la fois dans l’intégration de Student Information System Framework et les API REST publiques, ce qui permet aux institutions de gérer efficacement le processus de synchronisation des données entre Blackboard Learn Ultra et AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Que signifie l’institution Email et qu’est-ce qu’elle appuie ?

Le champ **Institution Email** permet des mappages de champs personnalisés entre les sources de données prises en charge en externe d’un client et Blackboard Learn Ultra. Si les sources de données sont des fournisseurs de cloud, tels que Microsoft, le nom d’utilisateur principal (UPN) est un identificateur unique principal pour chaque utilisateur composé d’un préfixe UPN (nom de compte de l’utilisateur) et d’un suffixe UPN (nom de domaine DNS) joint à un symbole @. Cela crée une adresse e-mail unique pour chaque utilisateur spécifique dans le Microsoft Azure Active Directory.

Pour garantir que les données sont exactes et que les inscriptions ou appartenances entre les classes Blackboard Learn Ultra et Microsoft Teams sont correctement obtenues, l’adresse e-mail d’un utilisateur doit correspondre entre les deux systèmes. Dans Blackboard Learn Ultra, les utilisateurs peuvent modifier ou remplacer leur adresse e-mail existante dans l’interface utilisateur, ce qui peut entraîner des erreurs de synchronisation et l’ajout incorrect de l’utilisateur à une équipe de classes. Le mappage des champs **de l’établissement Email** garantit que ce niveau de contrôle de sécurité et de validation peut être correctement géré, que les utilisateurs aient modifié leur e-mail dans Blackboard Learn Ultra ou non.

 Lorsque deux adresses e-mail sont différentes, l’une ou l’autre :

- Une décision doit être prise quant à la source qui est prioritaire et sera prise en tant qu’e-mails de personne et d’établissement.
  Ou
- Une institution peut définir un mappage de champs personnalisé dans son Email d’établissement, ce qui peut résoudre un conflit potentiel.

**L’établissement Email** mappage de champs est désormais disponible pour tous les types d’intégration SIS **existants dans Advanced Configuration Settings** > **Users Learn Object Type** > **Field Mapping**.

> [!NOTE]
> Il est important de noter que, par défaut, le **Email d’établissement** est défini sur le **Email de** personne pour tous les formats SIS et doit être unique pour chaque personne. Toutes les intégrations existantes configurées et en cours d’exécution disposeront de ce mappage de données, car SIS ne pourra pas importer les utilisateurs si leur e-mail est dupliqué. Si un établissement a besoin de la possibilité de modifier l’Email d’établissement sur **personnalisé**, il doit gérer cela par le biais **des paramètres de configuration avancés** dans le SIS.

## <a name="requirements"></a>Conditions requises

L’intégration des classes Microsoft Teams est disponible **uniquement pour les cours d’affichage de cours Ultra**. Votre établissement doit remplir les conditions suivantes pour l’utiliser :

- Avoir Blackboard Learn Ultra Learn SaaS avec la navigation ultra de base activée

  ![Un exemple de la fonctionnalité est activé dans les cours.](media/feature-availability.png)

- Activez LTI pour une utilisation dans les cours.

  a. Accédez au **panneau** >  Administrateur les **fournisseurs d’outils** >  LTI **gèrent les propriétés globales**.

  b. Sélectionnez **LTI Activé dans les cours**, puis éventuellement **Activer dans les organisations**.

  c. Sélectionnez **Envoyer**.

- Doit avoir configuré LTI

- Ajouter l’intégration LTI des classes Ultra Teams Blackboard Learn

- Ajouter l’outil Microsoft Teams Classes LTI 1.3

- Ajouter l’outil API REST et le partage de ressources cross-origin

- Configurer et approuver l’intégration des classes Microsoft Teams

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Ajouter l’outil Blackboard Learn Ultra Teams Classes LTI 1.3

1. Dans le **volet Administrateur**, sélectionnez **Fournisseurs d’outils LTI**.

2. Sélectionnez **inscrire l’outil LTI 1.3**.

3. Dans le champ **ID client** , tapez ou copiez-collez cet ID :

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Passez en revue tous les paramètres qui ont été préremplis et dans **l’état de l’outil**, puis **sélectionnez Activé**.

5. Dans **Stratégies d’établissement**, sélectionnez **Rôle dans Cours, Nom** et **Adresse Email**, puis **sélectionnez Oui** pour les deux.

6. Sélectionnez **Autoriser l’accès au service de niveau** et **Autoriser l’accès au service d’appartenance**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Ajouter l’outil Microsoft Teams Classes LTI 1.3

1. Dans le **volet Administrateur**, sélectionnez **Fournisseurs d’outils LTI**.

2. Sélectionnez **inscrire l’outil LTI 1.3**.

3. Dans le champ **ID client** , tapez ou copiez-collez cet ID :

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Passez en revue tous les paramètres qui ont été préremplis et dans *l’état de l’outil* , puis *sélectionnez Activé.*

5. Dans **Stratégies d’établissement**, sélectionnez **Rôle dans Cours, Nom** et **Adresse Email**. Sélectionnez **Oui** pour les deux.

6. Sélectionnez **Autoriser l’accès au service de niveau** et **Autoriser l’accès au service d’appartenance**.

## <a name="add-the-rest-api-tool"></a>Ajouter l’outil API REST

1. Dans le **volet Administrateur**, accédez à **Intégrations** et sélectionnez **Intégrations d’API Rest**.

2. Sélectionnez **Créer une intégration**.

3. Dans le champ **ID d’application** , tapez ou copiez-collez cet ID :

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Tapez un utilisateur pour cette intégration.

   Cet utilisateur est celui qui dispose de l’accès à l’API d’accueil à partir duquel l’application est associée.

5. Sélectionnez **Envoyer**.

## <a name="add-the-cross-origin-resource-sharing"></a>Ajouter le partage de ressources cross-origin

1. Dans le **panneau Administrateur**, accédez à **Intégrations** et sélectionnez **Partage des ressources cross-origin*.

2. Sélectionnez **Créer une configuration**.

3. Dans le champ **Origine** , tapez copier et coller cette URL :

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. Dans le champ **En-têtes autorisés** , tapez **Autorisation**.

5. Défini **sur** **Oui**.

6. Sélectionnez **Envoyer**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Configurer et approuver l’intégration des classes Microsoft Teams

Pour intégrer correctement votre instance Blackboard Learn Ultra aux classes Microsoft Teams, vous devez vous assurer que l’application Blackboard Learn Ultra est approuvée pour l’accès au sein de votre locataire Microsoft Azure. Il s’agit d’un processus qui doit être effectué par le Administration microsoft 365 global de votre établissement.

Ce processus peut être effectué avant ou après avoir configuré les applications LTI dans votre instance Blackboard Learn Ultra.

### <a name="before-configuring-the-lti-applications"></a>Avant de configurer les applications LTI

Si vous choisissez d’approuver l’application Azure Classes Ultra Teams Blackboard Learn avant de configurer les intégrations LTI, vous devez rediriger vers la **plateforme d’identités Microsoft Administration** point de terminaison de consentement. L’URL s’affiche :

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Vous allez remplacer **{Tenant}** par votre ID de locataire Microsoft Azure institutionnel spécifique.

Vous verrez une fenêtre d’autorisations qui explique que vous accordez l’autorisation à Blackboard Learn Ultra d’accéder à Microsoft Teams.

![fenêtre d’autorisations pour Microsoft et Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Après avoir configuré les applications LTI

1. Dans le **volet Administrateur**, accédez à **Outils et utilitaires**, puis sélectionnez **Microsoft Teams Integration Administration**.

2. Sélectionnez **Activer Microsoft Teams**.

3. Ajoutez votre **ID de locataire Microsoft** dans le champ de texte disponible.

4. Sélectionnez l’une des options suivantes :

   - Si l’application a un pré-consentement, elle affiche une petite coche. Si la coche s’affiche, **sélectionnez Envoyer**.

   - Si le consentement n’a pas été approuvé, suivez les étapes décrites pour générer l’URL de consentement et l’envoyer à microsoft 365 Global Administration pour approbation.

5. Une fois que vous avez confirmé l’approbation, **sélectionnez Nouvelle tentative** pour confirmer, puis **sélectionnez Envoyer**.
