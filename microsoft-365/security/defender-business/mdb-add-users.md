---
title: Ajouter des utilisateurs et attribuer des licences dans Microsoft Defender pour entreprises
description: Ajouter des utilisateurs et attribuer des licences Defender Entreprise pour protéger leurs appareils
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.date: 08/24/2022
ms.collection: M365-security-compliance
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: e2e6ec0fca05aabe49ad720f1991d1b846c1678a
ms.sourcegitcommit: 2d1302a6165b83cbbc8c2df2c608d43b6b0498b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2022
ms.locfileid: "67433668"
---
# <a name="add-users-and-assign-licenses-in-microsoft-defender-for-business"></a>Ajouter des utilisateurs et attribuer des licences dans Microsoft Defender pour entreprises

Dès que vous vous êtes inscrit à Defender Entreprise, la première étape consiste à ajouter des utilisateurs et à attribuer des licences. Cet article explique comment ajouter des utilisateurs et inclut les étapes suivantes.

## <a name="add-users-and-assign-licenses"></a>Ajouter des utilisateurs et attribuer des licences

> [!IMPORTANT]
> Vous devez être un administrateur global pour effectuer cette tâche.  La personne qui a inscrit votre entreprise pour Microsoft 365 ou Defender Entreprise est un administrateur général par défaut.

1. Accédez au Centre d'administration Microsoft 365 et [https://admin.microsoft.com](https://admin.microsoft.com) connectez-vous.

2. Accédez à **Utilisateurs** > **actifs**, puis **sélectionnez Ajouter un utilisateur**.

3. Dans le volet **Configurer les informations de base**, renseignez les informations de base de l’utilisateur, puis sélectionnez **Suivant**.

   - **Nom** : renseignez le prénom et le nom, le nom complet et le nom d’utilisateur.
   - **Domaine** Choisissez le domaine pour le compte de l’utilisateur. Par exemple, si le nom d’utilisateur de l’utilisateur est `Pat`, et que le domaine l’est `contoso.com`, il se connecte à l’aide `pat@contoso.com`de .
   - **Paramètres de mot de passe** : choisissez d’utiliser le mot de passe généré automatiquement ou de créer votre propre mot de passe fort pour l’utilisateur. L’utilisateur devra modifier son mot de passe après 90 jours. Vous pouvez également choisir l’option **d’exiger que cet utilisateur modifie son mot de passe lors de sa première connexion**. Vous pouvez également choisir d’envoyer le mot de passe de l’utilisateur par e-mail lorsque l’utilisateur est ajouté.

4. Dans la page **Attribuer des licences de produit**, sélectionnez Defender entreprise (ou Microsoft 365 Business Premium). Sélectionnez **Suivant**. 

   Si vous n’avez pas de licence disponible, vous pouvez toujours ajouter un utilisateur et acheter des licences supplémentaires. Pour plus d’informations sur l’ajout d’utilisateurs, consultez [Ajouter des utilisateurs et attribuer des licences en même temps](../../admin/add-users/add-users.md).

5. Dans la page **Paramètres facultatifs** , vous pouvez développer les **informations de profil** et renseigner des détails, tels que le titre du travail de l’utilisateur, le service, l’emplacement, etc. Sélectionnez **Suivant**.

6. Dans la page **Révision et fin** , passez en revue les détails, puis sélectionnez **Terminer l’ajout** pour ajouter l’utilisateur. Si vous devez apporter des modifications, **choisissez Retour** pour revenir à une page précédente.

## <a name="next-steps"></a>Prochaines étapes

- [Visitez le portail Microsoft 365 Defender](mdb-get-started.md)
- [Utilisez l’Assistant Installation dans Defender entreprise](mdb-use-wizard.md).
