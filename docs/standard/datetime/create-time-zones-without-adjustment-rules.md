---
title: "Comment&#160;: cr&#233;er des fuseaux horaires sans r&#232;gles d&#39;ajustement | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "règle d'ajustement (.NET Framework)"
  - "fuseaux horaires (.NET Framework), règle d'ajustement"
  - "fuseaux horaires (.NET Framework), créer"
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er des fuseaux horaires sans r&#232;gles d&#39;ajustement
Les informations de fuseau horaire précises requises par une application peuvent être absentes d'un système particulier pour plusieurs raisons :  
  
-   Le fuseau horaire n'a jamais été défini dans le Registre du système local.  
  
-   Les données relatives au fuseau horaire ont été modifiées ou supprimées du Registre.  
  
-   Le fuseau horaire existe, mais ne dispose pas d'informations exactes sur les ajustements des fuseaux horaires pour une période donnée.  
  
 Dans ces cas précis, vous pouvez appeler la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> pour définir le fuseau horaire requis par votre application.  Vous pouvez utiliser les surcharges de cette méthode pour créer un fuseau horaire avec ou sans règles d'ajustement.  Si le fuseau horaire prend en charge l'heure d'été, vous pouvez définir des ajustements avec des règles d'ajustement de date fixe ou flottante. \(Pour obtenir les définitions de ces termes, consultez la section « Terminologie de fuseau horaire » dans [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md).\)  
  
> [!IMPORTANT]
>  Les fuseaux horaires personnalisés créés en appelant la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> ne sont pas ajoutés au Registre.  Seule la référence d'objet retournée par l'appel de méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> permet d'y accéder.  
  
 Cette rubrique indique comment créer un fuseau horaire sans règles d'ajustement.  Pour créer un fuseau horaire qui prend en charge les règles d'ajustement de l'heure d'été, consultez [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).  
  
### Pour créer un fuseau horaire sans règles d'ajustement  
  
1.  Définissez le nom complet du fuseau horaire.  
  
     Le nom complet respecte un format relativement standard dans lequel l'offset du fuseau horaire par rapport au temps universel coordonné \(UTC, Coordinated Universal Time\) est mis entre parenthèses et suivi d'une chaîne qui identifie le fuseau horaire, ainsi qu'une ou plusieurs villes ou un ou plusieurs pays ou régions du fuseau horaire.  
  
2.  Définissez le nom de l'heure d'hiver du fuseau horaire.  En général, cette chaîne est également utilisée comme identificateur de fuseau horaire.  
  
3.  Si vous souhaitez utiliser un identificateur différent du nom standard du fuseau horaire, définissez l'identificateur de fuseau horaire.  
  
4.  Instanciez un objet <xref:System.TimeSpan> qui définit l'offset du fuseau horaire par rapport à l'heure UTC.  Les fuseaux horaires dont les heures sont ultérieures à l'heure UTC présentent un offset positif.  Inversement, les fuseaux horaires dont les heures sont antérieures à l'heure UTC présentent un offset négatif.  
  
5.  Appelez la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=fullName> pour instancier le nouveau fuseau horaire.  
  
## Exemple  
 L'exemple suivant définit un fuseau horaire personnalisé sans règles d'ajustement pour la région de Mawson, en Antarctique.  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
 [!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]  
  
 La chaîne assignée à la propriété <xref:System.TimeZoneInfo.DisplayName%2A> respecte un format standard dans lequel l'offset du fuseau horaire par rapport à l'heure UTC est suivi d'une description du fuseau horaire.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que les espaces de noms suivants soient importés :  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Vue d'ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)   
 [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)