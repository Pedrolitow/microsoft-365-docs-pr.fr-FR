---
title: 'Étape 6 : configurer le chiffrement du courrier électronique'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/19/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: ''
description: Familiarisez-vous avec la gestion des accès privilégiés pour Office 365 et apprenez à la configurer.
ms.openlocfilehash: 7747f5a0905a9477e9d3fd17b00eae740d76f640
ms.sourcegitcommit: 78fa107271252d902e600196a75cfa746bca73e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "37050295"
---
# <a name="step-6-configure-email-encryption"></a>Étape 6 : configurer le chiffrement du courrier électronique

*Cette étape facultative s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/infoprotection_icon-small.png)

Il existe trois types de chiffrement de courrier électronique dans Microsoft 365.

|||
|:-------|:-----|
| Chiffrement des messages Office (OME) | Chiffrement pour le courrier électronique Exchange Online envoyé à l’extérieur de votre organisation. |
| Gestion des droits relatifs à l'information (IRM) | Le chiffrement et les autorisations qui transitent avec le courrier électronique. |
| S/MIME (Secure/Multipurpose Internet Mail Extension) | Protection de la messagerie avec chiffrement et signatures numériques. |
|||

## <a name="office-365-message-encryption"></a>Chiffrement de messages Office 365

Avec OME, votre organisation peut envoyer et recevoir des messages électroniques chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. OME fonctionne avec Outlook.com, Yahoo !, Gmail et d’autres services de messagerie. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le message.

![Chiffrement des messages électroniques OME](./media/infoprotect-email-encryption/ome-encryption.png)

Vous configurez des règles de transport qui définissent les conditions de chiffrement. Lorsqu’un utilisateur envoie un message qui correspond à une règle, le chiffrement est automatiquement appliqué.

Pour afficher les messages chiffrés, les destinataires peuvent obtenir un code secret à usage unique, se connecter avec un compte Microsoft ou se connecter avec un compte professionnel ou scolaire associé à Microsoft 365. Les destinataires peuvent également envoyer des réponses chiffrées. Ils n’ont pas besoin de leur propre abonnement Microsoft 365 pour afficher les messages chiffrés ou envoyer des réponses chiffrées.

Pour plus d'informations, consultez la rubrique [Chiffrement dans Office 365](https://docs.microsoft.com/Office365/SecurityCompliance/ome).

## <a name="irm"></a>IRM

La gestion des droits relatifs à l’information (IRM) dans Microsoft 365 vous aide à sécuriser vos informations avec un chiffrement supplémentaire et à appliquer une stratégie intelligente qui indique qui a accès à ce qu’ils peuvent faire. Pour les messages électroniques, vous pouvez utiliser IRM pour le chiffrement et appliquer des restrictions d’utilisation. Par exemple, vous pouvez spécifier que certains destinataires disposent de toutes les capacités pour gérer le courrier électronique et que d’autres n’ont pas la possibilité d’imprimer ou de transférer le courrier électronique. 

Les stratégies IRM sont configurées dans Microsoft 365 et peuvent s’appliquer à des documents dans SharePoint Online et des messages électroniques. Un message électronique protégé par IRM inclut les paramètres de stratégie appliqués et en voyage avec. 

![Protection IRM des messages électroniques](./media/infoprotect-email-encryption/irm-protection.png)

Lorsque le destinataire ouvre le courrier électronique avec la stratégie incluse, les paramètres de stratégie sont utilisés pour déchiffrer le message et déterminer ce que le destinataire peut faire avec. 

Pour plus d'informations, consultez la rubrique [Gestion des droits relatifs à l'information (IRM) dans Exchange Online]( https://docs.microsoft.com/office365/SecurityCompliance/information-rights-management-in-exchange-online).

## <a name="smime"></a>S/MIME

S/MIME est une solution de protection de messagerie numérique basée sur des certificats, qui vous permet de chiffrer et de signer numériquement un message. Le chiffrement des messages permet de garantir que seul le destinataire prévu puisse ouvrir et lire le message. Une signature numérique permet au destinataire de valider l’identité de l’expéditeur et de déterminer que seul l’expéditeur aurait pu l’envoyer.

![Protection S/MIME des messages électroniques](./media/infoprotect-email-encryption/smime-protection.png)

S/MIME peut être utilisé pour envoyer des courriers électroniques à d’autres boîtes aux lettres dans votre abonnement Microsoft 365 ou à des utilisateurs externes.
Le chiffrement de messages et les signatures numériques sont rendus possibles grâce à l’utilisation de certificats numériques qui contiennent les clés publique et privée pour le chiffrement ou le déchiffrement des messages, ainsi que la création et la vérification des signatures numériques.
Pour utiliser S/MIME, vous devez disposer des clés publiques pour chaque destinataire. Les destinataires conservent leurs propres clés privées, qui doivent rester sécurisées. Si votre clé privée est compromise, vous devez obtenir un nouveau certificat numérique et redistribuer les clés publiques à tous les expéditeurs potentiels.

Pour plus d'informations, reportez-vous à la rubrique [S/MIME pour la signature et le chiffrement des messages](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).


Comme point de contrôle intermédiaire, consultez les [critères de sortie](infoprotect-exit-criteria.md#crit-infoprotect-step6) correspondant à cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step7.png)|[Configurez la gestion des accès privilégiés pour Office 365](infoprotect-configure-privileged-access-management.md)|
