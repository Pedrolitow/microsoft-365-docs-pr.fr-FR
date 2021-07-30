---
title: Microsoft Defender pour l’état et les paramètres du capteur d’identité dans Microsoft 365 Defender
description: Découvrez comment configurer Microsoft Defender pour les capteurs d’identité et surveiller leur état d’Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.openlocfilehash: 4f2972e86d024c9e7ec223d2ee8d7ddf283e7ac4
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53544167"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender pour l’état et les paramètres du capteur d’identité dans Microsoft 365 Defender

**S’applique à :**

- Microsoft 365 Defender
- Defender pour l’identité

Cet article explique comment configurer et surveiller les capteurs [d’identité Microsoft Defender](/defender-for-identity) dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Dans le cadre de la convergence avec Microsoft 365 Defender, certaines options et détails ont changé par rapport à leur emplacement dans le portail Defender pour l’identité. Veuillez lire les détails ci-dessous pour découvrir où trouver les fonctionnalités connues et nouvelles.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Affichage des paramètres et de l’état du capteur d’identité View Defender

1. In [Microsoft 365 Defender](https://security.microsoft.com/), go to **Paramètres** and then **Identities**.

    ![Go to Paramètres, then Identities](../../media/defender-identity/settings-identities.png)

1. Sélectionnez **la** page Capteurs, qui affiche tous vos capteurs Defender pour l’identité. Pour chaque capteur, vous verrez son nom, son appartenance au domaine, le numéro de version, si les mises à jour doivent être retardées, l’état du service, l’état de mise à jour, l’état d’état, le nombre de problèmes d’état et la création du capteur.

    [![Page Capteur](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >Dans le portail Defender pour l’identité, les paramètres du capteur et les informations d’état se sont produits dans des emplacements distincts. Notez que dans Microsoft 365 Defender ils sont maintenant sur la même page.

1. Si vous sélectionnez **Filtres,** vous pouvez choisir les filtres qui seront disponibles. Ensuite, avec chaque filtre, vous pouvez choisir les capteurs à afficher.

    [![Filtres de capteur](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    ![Capteur filtré](../../media/defender-identity/filtered-sensor.png)

1. Si vous sélectionnez l’un des capteurs, un volet s’affiche avec des informations sur le capteur et son état d’état.

    [![Détails du capteur](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Si vous sélectionnez l’un des problèmes d’état de santé, vous obtenez un volet avec plus de détails à leur sujet. Si vous choisissez un problème fermé, vous pouvez le rouvrir à partir d’ici.

    ![Détails du problème](../../media/defender-identity/issue-details.png)

1. Si vous sélectionnez **Gérer le capteur,** un volet s’ouvre et vous permet de configurer les détails du capteur.

    ![Gérer le capteur](../../media/defender-identity/manage-sensor.png)

    ![Configurer les détails du capteur](../../media/defender-identity/configure-sensor-details.png)

1. Dans la page **Capteurs,** vous pouvez exporter votre liste de capteurs vers un fichier .csv en sélectionnant **Exporter.**

    ![Exporter la liste des capteurs](../../media/defender-identity/export-sensors.png)

## <a name="add-a-sensor"></a>Ajouter un capteur

À partir de **la** page Capteurs, vous pouvez ajouter un nouveau capteur.

1. Sélectionnez **Ajouter un capteur.**

    ![Ajouter un capteur](../../media/defender-identity/add-sensor.png)

1. Un volet s’ouvre, vous fournissant un bouton permettant de télécharger le programme d’installation du capteur et une touche d’accès rapide générée.

    ![Télécharger le programme d’installation et la touche d’accès rapide](../../media/defender-identity/installer-access-key.png)

1. Sélectionnez **Télécharger le programme** d’installation pour enregistrer le package localement. Le fichier zip inclut les fichiers suivants :

    - Programme d’installation du capteur Defender pour l’identité

    - Fichier de paramètre de configuration avec les informations requises pour se connecter au service cloud Defender for Identity

1. Copiez **la touche d’accès rapide.** La touche d’accès rapide est requise pour que le capteur Defender for Identity se connecte à votre instance de Defender for Identity. La touche d’accès rapide est un mot de passe unique pour le déploiement du capteur, après quoi toutes les communications sont effectuées à l’aide de certificats pour l’authentification et le chiffrement TLS. Utilisez le **bouton de clé** Régénérer si vous avez besoin de régénérer la nouvelle touche d’accès rapide. Elle n’affecte aucun capteur précédemment déployé, car elle est utilisée uniquement pour l’inscription initiale du capteur.

1. Copiez le package sur le serveur ou le contrôleur de domaine dédié sur lequel vous installez le capteur Defender for Identity.

## <a name="configure-directory-services-account"></a>Configurer le compte des services d’annuaire

Pour connecter le capteur à vos domaines Active Directory, vous devez configurer les comptes des services d’annuaire.

1. In [Microsoft 365 Defender](https://security.microsoft.com/), go to **Paramètres** and then **Identities**.

    ![Go to Paramètres, then Identities](../../media/defender-identity/settings-identities.png)

1. Sélectionnez **des comptes de service d’annuaire.** Vous verrez quels comptes sont associés à quels domaines.

    ![Comptes de service d’annuaire](../../media/defender-identity/directory-service-accounts.png)

1. Si vous sélectionnez un compte, un volet s’ouvre avec les paramètres de ce compte.

    ![Paramètres du compte](../../media/defender-identity/account-settings.png)

1. Pour ajouter un nouveau compte  de services d’annuaire, sélectionnez Créer un compte et remplissez le nom de **compte,** le domaine **et** le mot de **passe.** Vous pouvez également choisir s’il s’agit d’un compte de **service** géré de groupe (gMSA) et s’il appartient à un **domaine d’étiquette unique.**

    ![Nouveau compte de service d’annuaire](../../media/defender-identity/new-directory-service-account.png)

1. Sélectionnez **Enregistrer**.

## <a name="see-also"></a>Voir aussi

- [Gérer les alertes de sécurité De Defender pour l’identité](manage-security-alerts.md)