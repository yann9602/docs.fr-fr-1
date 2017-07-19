---
title: "Suppression d&#39;espaces et de caract&#232;res de cha&#238;nes dans .NET Framework | Microsoft Docs"
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
  - "Remove (méthode)"
  - "supprimer des caractères"
  - "chaînes (.NET Framework), supprimer des caractères"
  - "Trim (méthode)"
  - "TrimEnd (méthode)"
  - "enlever des caractères"
  - "TrimStart (méthode)"
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Suppression d&#39;espaces et de caract&#232;res de cha&#238;nes dans .NET Framework
Si vous analysez une phrase en mots séparés, vous risquez d'obtenir des mots présentant des espaces vides \(également appelés espaces blancs\) à chaque extrémité du mot.  Dans cette situation, vous pouvez utiliser les méthodes de suppression \(trim\) dans la classe **System.String** pour supprimer un certain nombre d'espaces ou d'autres caractères à d'une position spécifiée dans la chaîne.  Le tableau suivant décrit les méthodes de suppression disponibles.  
  
|Nom de la méthode|Utilisation|  
|-----------------------|-----------------|  
|<xref:System.String.Trim%2A?displayProperty=fullName>|Supprime les espaces blancs ou les caractères spécifiés dans un tableau de caractères à partir du début et de la fin d'une chaîne.|  
|<xref:System.String.TrimEnd%2A?displayProperty=fullName>|Supprime les caractères spécifiés dans un tableau de caractères de la fin d'une chaîne.|  
|<xref:System.String.TrimStart%2A?displayProperty=fullName>|Supprime les caractères spécifiés dans un tableau de caractères du début d'une chaîne.|  
|<xref:System.String.Remove%2A?displayProperty=fullName>|Supprime un nombre spécifié de caractères d'une position d'index spécifiée dans une chaîne.|  
  
## Trim  
 Vous pouvez aisément supprimer les espaces blancs aux deux extrémités d'une chaîne en utilisant la méthode <xref:System.String.Trim%2A?displayProperty=fullName>, comme illustré par l'exemple suivant.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Vous pouvez également supprimer les caractères que vous spécifiez dans un tableau de caractères à partir du début et de la fin d'une chaîne.  L'exemple suivant supprime les espaces blancs, les points, et les astérisques.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## TrimEnd  
 La méthode **String.TrimEnd** supprime des caractères de la fin d'une chaîne en créant un nouvel objet chaîne.  Un tableau de caractères est passé à cette méthode pour spécifier les caractères à supprimer.  L'ordre des éléments dans le tableau de caractères n'affecte pas l'opération de suppression.  La suppression s'arrête dès qu'un caractère non spécifié est détecté dans le tableau.  
  
 L'exemple suivant supprime les dernières lettres d'une chaîne à l'aide de la méthode **TrimEnd**.  Dans cet exemple, la position du caractère `'r'` et du caractère `'W'` est inversée pour illustrer le fait que l'ordre des caractères dans le tableau n'a pas d'importance.  Remarquez que ce code supprime le dernier mot de `MyString` plus une partie du premier.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Ce code affiche `He` dans la console.  
  
 L'exemple suivant supprime le dernier mot d'une chaîne à l'aide de la méthode **TrimEnd**.  Dans ce code, une virgule suit le mot `Hello` et, vu qu'elle n'est pas spécifiée dans le tableau de caractères à supprimer, la suppression s'achève au niveau de cette virgule.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Ce code affiche `Hello,` dans la console.  
  
## TrimStart  
 La méthode **String.TrimStart** est similaire à la méthode **String.TrimEnd** à l'exception du fait qu'elle crée une nouvelle chaîne en supprimant des caractères du début d'un objet chaîne existant.  Un tableau de caractères est passé à la méthode **TrimStart** pour spécifier les caractères à supprimer.  Comme dans le cas de la méthode **TrimEnd**, l'ordre des éléments dans le tableau de caractères n'affecte pas l'opération de suppression.  La suppression s'arrête dès qu'un caractère non spécifié est détecté dans le tableau.  
  
 L'exemple suivant supprime le premier mot d'une chaîne.  Dans cet exemple, la position du caractère `'l'` et du caractère `'H'` est inversée pour illustrer le fait que l'ordre des caractères dans le tableau n'a pas d'importance.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Ce code affiche `World!` dans la console.  
  
## Enlever  
 La méthode <xref:System.String.Remove%2A?displayProperty=fullName> supprime un nombre de caractères donné à partir d'une position spécifiée d'une chaîne existante.  Cette méthode suppose un index de base zéro.  
  
 L'exemple suivant supprime dix caractères d'une chaîne à partir de la position cinq d'un index de base zéro de la chaîne.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Vous pouvez également supprimer un caractère ou une sous\-chaîne donnés dans une chaîne en appelant la méthode <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=fullName> et en spécifiant une chaîne vide \(<xref:System.String.Empty?displayProperty=fullName>\) comme remplacement.  L'exemple suivant supprime toutes les virgules d'une chaîne.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)