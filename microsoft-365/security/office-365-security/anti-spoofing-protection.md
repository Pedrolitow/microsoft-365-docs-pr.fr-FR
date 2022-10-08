---
title: Protection contre l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
search.appverid:
- MET150
ms.assetid: d24bb387-c65d-486e-93e7-06a4f1a436c0
ms.collection:
- m365-security
- Strat_O365_IP
- m365initiative-defender-office365
- EngageScoreSep2022
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
description: Les administrateurs peuvent découvrir les fonctionnalités d’usurpation d’identité disponibles dans Exchange Online Protection (EOP), qui peuvent vous aider à atténuer les attaques par hameçonnage d’expéditeurs et de domaines usurpés.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 2ad4ab1bb3a3cdd4eb4cd05f4fefc0deedb326b1
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68069180"
---
# <a name="anti-spoofing-protection-in-eop"></a>Protection contre l’usurpation d’identité dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365, les organisations avec des boîtes aux lettres dans Exchange Online ou une organisation Exchange Online Protection autonome (EOP) dépourvu de boîtes aux lettres Exchange Online, EOP comprend des fonctionnalités permettant de protéger votre organisation contre les faux expéditeurs (falsifiés).

Pour protéger ses utilisateurs, Microsoft prend la menace du hameçonnage au sérieux. L’usurpation d’identité est une technique couramment utilisée par les intrus. **Les messages usurpant une identité semblent provenir d’une personne ou d’un emplacement autre que la source réelle**. Cette technique est souvent utilisée dans des campagnes de hameçonnage qui visent à dérober des informations d’identification d’utilisateur. La technologie anti-usurpation dans EOP examine spécifiquement les falsifications de l’en-tête De dans le corps de message (utilisé pour afficher l’expéditeur du message dans les clients de courrier électronique). Lorsque EOP est convaincu que l'en-tête De est falsifié, le message est identifié comme étant falsifié.

Les technologies anti-usurpation suivantes sont disponibles dans EOP :

- **Authentification de messagerie électronique** : l’utilisation de l’authentification de messagerie électronique (également appelée validation de messagerie électronique) pour les enregistrements SPF, DKIM et DMARC dans DNS fait partie intégrante de tout effort anti-usurpation d’identité. Vous pouvez configurer ces enregistrements pour vos domaines de sorte que les systèmes de messagerie électronique de destination peuvent vérifier la validité des messages censés provenir d’expéditeurs figurant de vos domaines. Pour les messages entrants, Microsoft 365 requiert une authentification de messagerie électronique pour les domaines d’expéditeur. Si vous souhaitez en savoir plus, consultez la page [Authentification de messagerie électronique dans Microsoft 365](email-validation-and-authentication.md).

  EOP analyse et bloque les messages qui ne peuvent pas être authentifiés par la combinaison de méthodes standard d'authentification de messagerie électronique et de techniques de réputation de l'expéditeur.

  :::image type="content" source="../../media/eop-anti-spoofing-protection.png" alt-text="Contrôles anti-usurpation d’identité EOP" lightbox="../../media/eop-anti-spoofing-protection.png":::

- **Spoof intelligence insight**: Review spoofed messages from senders in internal and external domains during the last 7 days, and allow or block those senders. For more information, see [Spoof intelligence insight in EOP](learn-about-spoof-intelligence.md).

- **Autoriser ou bloquer les expéditeurs usurpés dans la liste d’autorisation/de** blocage du locataire : lorsque vous remplacez le verdict dans l’insight d’intelligence de l’usurpation d’identité, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisations/blocs du locataire. Vous pouvez également créer manuellement des entrées d'autorisation ou de blocage pour les faux expéditeurs avant qu'ils ne soient détectés par la veille contre l’usurpation d’identité. Pour plus d’informations, voir [Gérer liste rouge/verte du client dans EOP](manage-tenant-allow-block-list.md).

- **Stratégies anti-hameçonnage** : dans EOP et Microsoft Defender pour Office 365, les stratégies anti-hameçonnage contiennent les paramètres suivants contre l’usurpation d’adresse :
  - Activer ou désactiver la veille contre l’usurpation d’identité.
  - Activer ou désactiver l’identification de l’expéditeur non authentifié dans Outlook.
  - Spécifier l’action à effectuer pour les expéditeurs usurpés d’adresse.

  Si vous souhaitez en savoir plus, consultez l’article [Paramètres d’usurpation dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

  **Remarque** : les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365 contiennent d’autres protections, notamment la protection contre l’**usurpation d’identité**. Pour plus d’informations, consultez [Paramètres exclusifs des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- **Rapport sur les détections d’usurpation d’identité** : pour plus d’informations, consultez le [rapport sur les détections d’usurpation d’identité](view-email-security-reports.md#spoof-detections-report).

  **Note**: Defender for Office 365 organizations can also use Real-time detections (Plan 1) or Threat Explorer (Plan 2) to view information about phishing attempts. For more information, see [Microsoft 365 threat investigation and response](office-365-ti.md).

## <a name="how-spoofing-is-used-in-phishing-attacks"></a>Comment l’usurpation est utilisée dans les attaques par hameçonnage

Les messages d'usurpation d'identité ont les conséquences négatives suivantes pour les utilisateurs :

- **Les messages usurpant une identité sont trompeurs pour les utilisateurs** : un message usurpant une identité peut leurrer un utilisateur en l’incitant à cliquer sur un lien l’amenant à révéler ses identifiants, à télécharger un programme malveillant ou à répondre à un message au contenu sensible (compromission de courrier professionnel).

  Le message suivant est un exemple de hameçonnage qui utilise l’expéditeur dont l'identité a été usurpée msoutlook94@service.outlook.com :

  ![Message d’hameçonnage usurpant le domaine service.outlook.com.](../../media/1a441f21-8ef7-41c7-90c0-847272dc5350.jpg)

  Ce message ne provient pas de service.outlook.com, mais l’intrus a usurpé le champ d’en-tête **De** afin de lui donner l’apparence souhaitée. Il s'agissait d'une tentative de tromper le destinataire pour qu'il clique sur le lien **Changez votre mot de passe** et dévoile ses informations d'identification.

  Le message suivant est un exemple de BEC qui utilise le domaine de courrier électronique usurpé contoso.com :

  ![Message d’hameçonnage: compromission du courrier professionnel](../../media/da15adaa-708b-4e73-8165-482fc9182090.jpg)

  Le message semble légitime, mais l’identité de l’expéditeur a été usurpée.

- **Les utilisateurs confondent les vrais messages et les faux**: même les utilisateurs qui connaissent le hameçonnage peuvent éprouver des difficultés à voir les différences entre les messages réels et les messages usurpant une identité.

  Le message suivant est un exemple de message de réinitialisation de mot de passe authentique provenant du compte Microsoft Sécurité :

  ![Réinitialisation du mot de passe légitime de Microsoft](../../media/58a3154f-e83d-4f86-bcfe-ae9e8c87bd37.jpg)

  The message really did come from Microsoft, but users have been conditioned to be suspicious. Because it's difficult to the difference between a real password reset message and a fake one, users might ignore the message, report it as spam, or unnecessarily report the message to Microsoft as phishing.

## <a name="different-types-of-spoofing"></a>Différents types d’usurpation

Microsoft distingue deux types de messages usurpant une identité :

- **Intra-org spoofing**: Also known as _self-to-self_ spoofing. For example:

  - L’expéditeur et le destinataire figurent dans le même domaine :
    > De : chris@contoso.com <br> À : michelle@contoso.com

  - L'expéditeur et le destinataire figurent dans des sous-domaines du même domaine :
    > De : laura@marketing.fabrikam.com <br> À : julia@engineering.fabrikam.com

  - L’expéditeur et le destinataire figurent dans différents domaines appartenant à la même organisation (autrement dit, les deux domaines sont configurés comme des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) au sein d’une même organisation) :
    > De: expéditeur @ microsoft.com <br> À : destinataire @ bing.com

    Les espaces sont utilisés dans les adresses de messagerie électronique pour empêcher la récolte spambots.

  Les messages qui échouent à l’[authentification composite](email-validation-and-authentication.md#composite-authentication) en raison d’une usurpation inter-domaines contiennent les valeurs d’en-tête suivantes :

  `Authentication-Results: ... compauth=fail reason=6xx`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.11`

  - `reason=6xx` indique l’usurpation intra-organisationnelle.

  - SFTY est le niveau de sécurité du message. 9 indique un hameçonnage, .11 indique une usurpation intra-organisationnelle.

- **Usurpation inter-domaines** : les domaines de l’expéditeur et du destinataire sont différents et n’ont aucune relation entre eux (également appelés domaines externes). Par exemple :
    > De : chris@contoso.com <br> À : michelle@tailspintoys.com

  Les messages qui échouent à l’[authentification composite](email-validation-and-authentication.md#composite-authentication) en raison d’une usurpation inter-domaines contiennent les valeurs d’en-têtes suivantes :

  `Authentication-Results: ... compauth=fail reason=000/001`

  `X-Forefront-Antispam-Report: ...CAT:SPOOF;...SFTY:9.22`

  - `reason=000` indique que le message a échoué à l’authentification explicite de courrier électronique. `reason=001` indique que le message a échoué à l’authentification implicite de courrier électronique.

  - `SFTY` est le niveau de sécurité du message. 9 indique un hameçonnage, .22 indique une usurpation inter-domaines.

> [!NOTE]
> If you've gotten a message like ***compauth=fail reason=###** _ and need to know about composite authentication (compauth), and the values related to spoofing, see [_Anti-spam message headers in Microsoft 365*](anti-spam-message-headers.md). Or go directly to the [*reason*](anti-spam-message-headers.md) codes.

Si vous souhaitez en savoir plus sur DMARC, consultez la page [Utiliser DMARC pour valider les messages électroniques dans Microsoft 365](use-dmarc-to-validate-email.md).

## <a name="problems-with-anti-spoofing-protection"></a>Problèmes liés à la protection contre l’usurpation d’identité

Les listes de diffusion (également connues sous le nom de listes de discussion) sont connues pour avoir des problèmes liés à la protection contre l’usurpation d’identité en raison de la manière dont elles transmettent et modifient les messages.

Par exemple, Gabriela Laureano (glaureano@contoso.com) s'intéresse à l'observation des oiseaux. Elle s'inscrit à la liste de diffusion birdwatchers@fabrikam.com et envoie le message suivant à la liste :

> **De :** « Denise Bourgeois » \<glaureano@contoso.com\> <br> **À :** liste de discussion des Ornithologues\<birdwatchers@fabrikam.com\> <br> **Subject:** Great viewing of blue jays at the top of Mt. Rainier this week <p> Quelqu’un veut-il voir l’observation de cette semaine au Mont Rainier. Rainier ?

Le serveur de liste de diffusion reçoit le message, modifie son contenu et le rediffuse aux membres de la liste. Le message rediffusé a la même adresse De (glaureano@contoso.com), mais une balise est ajoutée à la ligne d’objet, et un pied de page est ajouté au bas du message. Ce type de modification est courant dans les listes de diffusion et peut entraîner des faux positifs en matière d’usurpation d'identité.

> **De :** « Denise Bourgeois » \<glaureano@contoso.com\> <br> **À :** liste de discussion des Ornithologues\<birdwatchers@fabrikam.com\> <br> **Subject:** [BIRDWATCHERS] Great viewing of blue jays at the top of Mt. Rainier this week <p> Quelqu’un veut-il voir l’observation de cette semaine au Mont Rainier. Rainier ? <p> Ce message a été envoyé à la liste de discussion Ornithologues. Vous pouvez vous désabonner à tout moment.

Pour aider les messages de la liste de diffusion à passer les vérifications d’usurpation d’identité, procédez comme suit selon que vous contrôlez ou non la liste de diffusion :

- La liste de diffusion appartient à votre organisation :

  - Consultez le FAQ sur DMARC.org : [J’utilise une liste de diffusion et je souhaite interagir avec DMARC, que dois-je faire ?](https://dmarc.org/wiki/FAQ#I_operate_a_mailing_list_and_I_want_to_interoperate_with_DMARC.2C_what_should_I_do.3F).

  - Lisez les instructions de ce billet de blog : [Une astuce pour les opérateurs de listes de diffusion afin d'interagir avec DMARC pour éviter les défaillances](/archive/blogs/tzink/a-tip-for-mailing-list-operators-to-interoperate-with-dmarc-to-avoid-failures).

  - Envisagez d'installer des mises à jour sur le serveur de votre liste de diffusion pour soutenir l'ARC, voir <http://arc-spec.org>.

- La liste de diffusion n’appartient pas à votre organisation :

  - Demandez au chargé de maintenance de la liste de diffusion de configurer l’authentification de la messagerie électronique pour le domaine à partir duquel la liste de diffusion est relayée.

    Lorsque suffisamment d’expéditeurs répondent aux propriétaires de domaine qu’ils devraient configurer des enregistrements d’authentification de courrier, cela les incite à agir. Bien que Microsoft collabore avec les propriétaires de domaine pour les inciter à publier les enregistrements requis, c’est encore plus efficace lorsque des utilisateurs individuels le demandent.

  - Créez des règles de boîte aux lettres dans votre client de messagerie électronique pour déplacer les messages vers la Boîte de réception. Vous pouvez également demander à vos administrateurs de configurer les remplacements, comme décrit dans [Informations sur la veille contre l’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md) et [Gérer les listes rouge/verte du client](manage-tenant-allow-block-list.md).

  - Utilisez la liste d’adresses client autoriser/bloquer pour créer un remplacement pour la liste de publipostage afin de la traiter comme légitime. Pour plus d’informations, consultez [Créer des entrées d’autorisation pour les expéditeurs usurpés d’identité](allow-block-email-spoof.md#create-allow-entries-for-spoofed-senders).

En cas d’échec de l’opération, vous pouvez signaler le message à Microsoft comme étant un faux positif. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="considerations-for-anti-spoofing-protection"></a>Considérations relatives à la protection contre l’usurpation d’identité

Si vous êtes un administrateur qui envoie actuellement des messages à Microsoft 365, vous devez vous assurer que votre messagerie électronique est correctement authentifiée. Dans le cas contraire, il peut être marqué comme courrier indésirable ou hameçonnage. Pour plus d’informations, voir [Solutions pour les expéditeurs légitimes qui envoient du courrier électronique non authentifié](email-validation-and-authentication.md#solutions-for-legitimate-senders-who-are-sending-unauthenticated-email).

Senders in an individual user's (or admin's) Safe Senders list will bypass parts of the filtering stack, including spoof protection. For more information, see [Outlook Safe Senders](create-safe-sender-lists-in-office-365.md#use-outlook-safe-senders).

Les administrateurs doivent éviter (si possible) d’utiliser des listes d’expéditeurs autorisés ou des listes de domaines autorisés. Ces expéditeurs contournent toutes les protections contre le courrier indésirable, l’usurpation d’identité et le hameçonnage, ainsi que l’authentification de l’expéditeur (SPF, DKIM, DMARC). Pour plus d’informations, voir [Utiliser des listes d’expéditeurs autorisés ou de domaines autorisés](create-safe-sender-lists-in-office-365.md#use-allowed-sender-lists-or-allowed-domain-lists).
