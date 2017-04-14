---
title: "R&#233;vision de l&#39;adaptabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "applications universelles, adaptabilité"
  - "développement d’applications (.NET Framework), localisation"
  - "adaptabilité (.NET Framework)"
  - "applications internationales (.NET Framework), adaptabilité"
  - "globalisation (.NET Framework), adaptabilité"
  - "culture, adaptabilité"
  - "localisation (.NET Framework), adaptabilité"
  - "applications globales, adaptabilité"
  - "localiser des ressources"
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# R&#233;vision de l&#39;adaptabilit&#233;
L'examen de l'adaptabilité est une étape intermédiaire de le développement d'une application mondialisable.  Il vérifie qu'une application généralisée est prête pour la localisation et identifie tout code ou de tous les aspects de l'interface utilisateur qui nécessitent une gestion spéciale.  Cette étape permet de s'assurer que le processus de localisation n'introduira pas de défauts fonctionnels dans votre application.  Lorsque tous les problèmes générés par l'examen de l'adaptabilité ont été traités, l'application est prête pour la localisation.  Si l'examen de l'adaptabilité est complet, vous n'avez pas à ne pas modifier le code source pendant le processus de localisation.  
  
 L'examen de l'adaptabilité inclut les trois contrôles suivants :  
  
-   [Les recommandations de globalisation ont elles été implémenté?](#global)  
  
-   [Est\-ce\-que fonctionnalités dépendantes de la culture sont gérées correctement ?](#culture)  
  
-   [Avez\-vous testé votre application avec des données internationales ?](#test)  
  
<a name="global"></a>   
## Implémentation des recommandations de globalisation  
 Si vous avez conçu et avez développé votre application avec l'emplacement lors, et si vous avez suivi les indications décrites dans l'article de [Globalisation](../../../docs/standard/globalization-localization/globalization.md), examinez l'adaptabilité est essentiellement un test d'assurance qualité.  Sinon, pendant cette étape vous devez examiner et exécuter les recommandations pour [globalisation](../../../docs/standard/globalization-localization/globalization.md), et corrigez les erreurs dans le code source qui empêchent l'emplacement.  
  
<a name="culture"></a>   
## Gestion des fonctionnalités dépendantes de la culture  
 Le .NET Framework ne fournit pas de prise en charge de programmation dans plusieurs éléments qui varient considérablement par la culture.  Dans la plupart des cas, vous devez écrire un code personnalisé et les fonctionnalités de ce handle comme suit :  
  
-   Adresses.  
  
-   Numéros de téléphone.  
  
-   Formats de papier.  
  
-   Unités de mesure utilisés pour les longueurs, les poids, la zone, le volume, et de températures.  Bien que .NET Framework n'offre pas prise en charge intégrée pour convertir les unités de mesure, vous pouvez utiliser la propriété de <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=fullName> pour déterminer si un pays ou une région spécifique utilise le système de mesure, comme le montre l'exemple suivant montre.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## Test de votre application  
 Avant de localiser votre application, vous devriez la tester à l'aide de les données internationales dans les versions internationales du système d'exploitation.  Bien que la plupart de l'interface utilisateur ne peut être localisée à ce stade, vous pouvez détecter les problèmes tels que :  
  
-   Sérialisée données qui ne désérialise pas correctement sur plusieurs versions du système d'exploitation.  
  
-   Données numériques qui ne reflètent pas les conventions de la culture actuelle.  Par exemple, les nombres peuvent être affichés avec les séparateurs de groupes, les séparateurs décimaux, ou les symboles monétaires inexact.  
  
-   Données de date et d'heure qui ne reflètent pas les conventions de la culture actuelle.  Par exemple, les chiffres qui représente le mois et le jour peut apparaître dans l'ordre incorrect, séparateur de date peuvent être incorrectes, les informations de fuseau horaire peuvent être incorrectes.  
  
-   Ressources qui ne peuvent pas être trouvées car il n'est pas reconnu une culture par défaut pour votre application.  
  
-   Chaînes affichées dans une commande non courante pour une culture spécifique.  
  
-   Les comparaisons de chaînes et les comparaisons de l'égalité qui retournent des résultats inattendus.  
  
 Si vous avez suivi les recommandations de globalisation lorsque vous développez votre application, fonctionnalités dépendantes de la culture gérées correctement, et que vous avez identifiés et avez traité les problèmes de localisation qui ont surgi pendant le test, vous pouvez passer à l'étape suivante, [Localisation](../../../docs/standard/globalization-localization/localization.md).  
  
## Voir aussi  
 [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)   
 [Localisation](../../../docs/standard/globalization-localization/localization.md)   
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)   
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)