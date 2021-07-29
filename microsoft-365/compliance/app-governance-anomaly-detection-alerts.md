---
title: Examiner les alertes de détection d’anomalie
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: m365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Examinez les alertes de détection d’anomalies.
ms.openlocfilehash: 41dd60de86d7583169845ae185f9f715011ea3e4
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541372"
---
# <a name="investigate-anomaly-detection-alerts"></a>Examiner les alertes de détection d’anomalie

 La gouvernance des applications Microsoft fournit des détections de sécurité et des alertes pour les activités malveillantes. L’objectif de ce guide est de vous fournir des informations générales et pratiques sur chaque alerte, afin de faciliter vos tâches d’investigation et de correction. Ce guide contient des informations générales sur les conditions de déclenchement des alertes. Étant donné que les détections d’anomalies ne sont pas déterministes par nature, elles sont déclenchées uniquement en cas de comportement qui s’écarte de la norme. Enfin, certaines alertes peuvent être en préversion. Consultez donc régulièrement la documentation officielle pour connaître l’état des alertes mis à jour.

## <a name="mitre-attck"></a>MITRE ATT&CK

Pour faciliter la mise en correspondance de la relation entre les alertes de gouvernance des applications Microsoft et la matrice MITRE ATT&CK familière, nous avons classé les alertes par tactique MITRE ATT&CK correspondante. Cette référence supplémentaire facilite la compréhension de la technique d’attaques suspectes potentiellement utilisée lorsque l’alerte de gouvernance des applications est déclenchée.

Ce guide fournit des informations sur l’examen et la correction des alertes de gouvernance des applications dans les catégories suivantes.

- Accès initial
- Exécution
- Persistance
- Réaffectation des privilèges
- Fraude à la défense
- Accès informations d'identification
- Collection
- Exfiltration
- Impact

<!-->
## <a name="security-alert-classifications"></a>Classifications des alertes de sécurité

Après examen correct, toutes les alertes de gouvernance des applications Microsoft peuvent être classées comme l’un des types d’activités suivants :

- Vrai positif (TP) : alerte sur une activité malveillante confirmée.
- Vrai positif sans gravité (B-TP) : alerte en cas d’activité suspecte mais non malveillante, telle qu’un test d’intrusion ou toute autre action suspecte autorisée.
- Faux positif (FP) : alerte sur une activité non malveillante.
-->

## <a name="general-investigation-steps"></a>Étapes d’investigation générales

Utilisez les instructions générales suivantes lors de l’examen d’un type d’alerte pour mieux comprendre la menace potentielle avant d’appliquer l’action recommandée.

- Passez en revue le niveau de gravité de l’application et comparez-le au reste de l’application dans votre client. Cette révision vous aidera à identifier les applications de votre client qui présentent le plus de risques.
- Si vous identifiez un TP, passez en revue toutes les activités de l’application pour mieux comprendre l’impact. Par exemple, passez en revue les informations d’application suivantes :

  - Étendues d’accès accordées
  - Comportement inhabituel  
  - Adresse IP et emplacement

## <a name="initial-access-alerts"></a>Alertes d’accès initial

Cette section décrit les alertes indiquant qu’une application malveillante tente peut-être de maintenir son pied de page dans votre organisation.  

### <a name="encoded-app-name-with-suspicious-consent-scopes"></a>Nom d’application encodé avec des étendues de consentement suspectes

**Gravité :** moyen

**Description**: cette détection identifie les applications OAuth avec des caractères, tels que des caractères Unicode ou encodés, demandés pour les étendues de consentement suspectes et qui ont accédé aux dossiers de messagerie des utilisateurs via le API Graph. Cette alerte peut indiquer une tentative d’étiquetage d’une application malveillante en tant qu’application connue et approuvée afin que les adversaires puissent induire les utilisateurs en erreur en consentant à l’application malveillante.

**TP ou FP ?**

- **TP**: si vous pouvez confirmer que l’application OAuth a encodé le nom complet avec des étendues suspectes fournies à partir d’une source inconnue, un vrai positif est indiqué.  

  **Action recommandée**: vérifiez le niveau d’autorisation demandé par cette application et les utilisateurs auxquels l’accès a été accordé. En fonction de votre enquête, vous pouvez choisir d’interdire l’accès à cette application.

  Pour interdire l’accès à l’application, dans la page applications OAuth, sur la ligne dans laquelle l’application que vous souhaitez interdire apparaît, sélectionnez l’icône d’exclusion. Vous pouvez choisir d’indiquer aux utilisateurs que l’application qu’ils ont installée et autorisée a été interdite. La notification indique aux utilisateurs que l’application sera désactivée et qu’ils n’auront pas accès à l’application connectée. Si vous ne souhaitez pas qu’ils le sachent, désélectionnez Avertir les utilisateurs qui ont autorisé l’accès à cette application interdite dans la boîte de dialogue. Nous vous recommandons d’informer les utilisateurs de l’application que leur application est sur le point d’être interdite.

- **FP**: si vous souhaitez confirmer que l’application a un nom encodé mais qu’elle a une utilisation commerciale légitime dans l’organisation.

  **Action recommandée**: ignorer l’alerte.

#### <a name="understand-the-scope-of-the-breach"></a>Comprendre l’étendue de la violation

Suivez le didacticiel sur la façon d’[examiner les applications OAuth à risque](/cloud-app-security/investigate-risky-oauth).

### <a name="oauth-app-with-read-scopes-have-suspicious-reply-url"></a>L’application OAuth avec étendues de lecture a une URL de réponse suspecte

**Gravité :** moyen

**Description**: cette détection identifie une application OAuth avec uniquement des étendues de lecture telles que User.Read, People.Read, Contacts.Read, Mail.Read, Contacts.Read.Shared redirige vers une URL de réponse suspecte via API Graph. Cette activité tente d’indiquer que l’application malveillante disposant d’autorisations moins privilégiées (telles que les étendues de lecture) peut être exploitée pour effectuer une reconnaissance de compte d’utilisateurs.

**TP ou FP ?**

- **TP**: si vous êtes en mesure de confirmer que l’application OAuth avec étendue de lecture est fournie à partir d’une source inconnue et qu’elle est redirigée vers une URL suspecte, un vrai positif est indiqué.

  **Action recommandée**: examinez l’URL de réponse et les étendues demandées par l’application. En fonction de votre enquête, vous pouvez choisir d’interdire l’accès à cette application. Examinez le niveau d’autorisation demandé par cette application et les utilisateurs qui ont accordé l’accès.

  Pour interdire l’accès à l’application, dans la page applications OAuth, sur la ligne dans laquelle l’application que vous souhaitez interdire apparaît, sélectionnez l’icône d’exclusion. Vous pouvez choisir d’indiquer aux utilisateurs que l’application qu’ils ont installée et autorisée a été interdite. La notification indique aux utilisateurs que l’application sera désactivée et qu’ils n’auront pas accès à l’application connectée. Si vous ne souhaitez pas qu’ils le sachent, désélectionnez Avertir les utilisateurs qui ont autorisé l’accès à cette application interdite dans la boîte de dialogue. Nous vous recommandons d’informer les utilisateurs de l’application que leur application est sur le point d’être interdite.

- **B-TP**: si vous effectuez une investigation, vous pouvez confirmer que l’application a une utilisation commerciale légitime dans l’organisation.

  **Action recommandée**: ignorer l’alerte.

#### <a name="understand-the-scope-of-the-breach"></a>Comprendre l’étendue de la violation 

1. Passez en revue toutes les activités effectuées par l’application.
1. Si vous pensez qu’une application est suspecte, nous vous recommandons d’examiner le nom et l’URL de réponse de l’application dans différents magasins d’applications. Lors de la vérification des magasins d’applications, concentrez-vous sur les types d’applications suivants :
   - Applications qui ont été créées récemment.
   - Applications avec une URL de réponse suspecte
   - Applications qui n’ont pas été récemment mises à jour. L’absence de mises à jour peut indiquer que l’application n’est plus prise en charge.
1. Si vous pensez toujours qu’une application est suspecte, vous pouvez rechercher le nom de l’application, le nom de l’éditeur et l’URL de réponse en ligne  

## <a name="persistence-alerts"></a>Alertes de persistance

Cette section décrit les alertes indiquant qu’un acteur malveillant tente peut-être de maintenir son pied dans votre organisation.

### <a name="app-with-suspicious-oauth-scope-creates-inbox-rule"></a>Une application avec une étendue OAuth suspecte crée une règle de boîte de réception  

**Gravité :** moyen

**MITRE ID’s**: T1137.005, T1114  

Cette détection identifie une application OAuth qui a accepté des étendues suspectes, crée une règle de boîte de réception suspecte, puis accède aux dossiers de courrier et aux messages des utilisateurs via le API Graph. Les règles de boîte de réception, telles que le transfert de tout ou de certains e-mails vers un autre compte de messagerie, et les appels Graph pour accéder aux e-mails et les envoyer à un autre compte de messagerie, peuvent être une tentative d’exfiltrer des informations de votre organisation.  

**TP ou FP ?**

- **TP**: si vous pouvez confirmer que la règle de boîte de réception a été créée par une application tierce OAuth avec des étendues suspectes fournies à partir d’une source inconnue, un vrai positif est indiqué.

  **Action recommandée**: désactivez et supprimez l’application, réinitialisez le mot de passe et supprimez la règle de boîte de réception.

  Suivez le didacticiel sur la réinitialisation d’un mot de passe à l’aide de Azure Active Directory et suivez le didacticiel sur la suppression de la règle de boîte de réception.

- **FP**: si vous pouvez confirmer que l’application a créé une règle de boîte de réception dans un compte de messagerie externe nouveau ou personnel pour des raisons légitimes.

  **Action recommandée**: ignorer l’alerte.

#### <a name="understand-the-scope-of-the-breach"></a>Comprendre l’étendue de la violation

1. Passez en revue toutes les activités effectuées par l’application.
1. Passez en revue les étendues accordées par l’application.
1. Passez en revue l’action et la condition de règle de boîte de réception créées par l’application.

## <a name="collection-alerts"></a>Alertes de collecte

Cette section décrit les alertes indiquant qu’un acteur malveillant tente peut-être de recueillir des données d’intérêt pour son objectif auprès de votre organisation.

### <a name="app-made-anomalous-graph-calls-to-read-e-mail"></a>L’application a effectué des appels Graph anormaux pour lire le courrier électronique

**Gravité :** moyen

**MITRE ID**: T1114

Cette détection identifie le moment où l’application OAuth métier accède à un volume inhabituel et élevé de dossiers de messagerie et de messages de l’utilisateur via le API Graph, ce qui peut indiquer une tentative de violation de votre organisation.

**TP ou FP ?**

- **TP**: si vous pouvez confirmer que l’activité de graphe inhabituelle a été effectuée par l’application OAuth métier, un vrai positif est indiqué.

  **Actions recommandées**: désactivez temporairement l’application et réinitialisez le mot de passe, puis réactivez l’application.

  Suivez le didacticiel sur la réinitialisation d’un mot de passe à l’aide de Azure Active Directory.

- **FP**: si vous pouvez confirmer que l’application est destinée à effectuer un volume anormalement élevé d’appels de graphe.

  **Action recommandée**: ignorer l’alerte.

#### <a name="understand-the-scope-of-the-breach"></a>Comprendre l’étendue de la violation

1. Consultez le journal d’activité des événements effectués par cette application pour mieux comprendre les autres activités Graph afin de lire les e-mails et de tenter de collecter les informations sensibles des utilisateurs.
1. Recherchez les informations d’identification inattendues ajoutées à l’application.
