---
title: "Cha&#238;nes de format d&#39;&#233;num&#233;ration | Microsoft Docs"
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
  - "chaînes de format d'énumération"
  - "spécificateurs de format, chaînes de format d'énumération"
  - "mise en forme (.NET Framework), énumération"
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Cha&#238;nes de format d&#39;&#233;num&#233;ration
Vous pouvez utiliser la méthode <xref:System.Enum.ToString%2A?displayProperty=fullName> pour créer un nouvel objet chaîne qui représente la valeur numérique, hexadécimale ou de chaîne d'un membre de l'énumération.  Cette méthode prend une des chaînes de format d'énumération pour spécifier la valeur à retourner.  
  
 Le tableau suivant répertorie les chaînes de format d'énumération et les valeurs qu'elles retournent.  Ces spécificateurs de format ne respectent pas la casse.  
  
|Chaîne de format|Résultat|  
|----------------------|--------------|  
|G ou g|Affiche l'entrée d'énumération sous la forme d'une valeur de chaîne dans la mesure du possible ; sinon, affiche la valeur entière de l'instance actuelle.  Si l'énumération est configurée et si l'attribut **Flags** est défini, les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules.  Si l'attribut **Flags** n'est pas défini, une valeur non valide s'affiche comme entrée numérique.  L'exemple suivant illustre le spécificateur de format G.<br /><br /> [!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
 [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]|  
|F ou f|Affiche, dans la mesure du possible, l'entrée d'énumération en tant que valeur de chaîne.  Si la valeur peut être complètement affichée en tant que somme des entrées de l'énumération \(même en cas d'absence de l'attribut **Flags**\), les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules.  Si la valeur ne peut pas être complètement déterminée par les entrées de l'énumération, la valeur est mise en forme en tant que valeur entière.  L'exemple suivant illustre le spécificateur de format F.<br /><br /> [!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
 [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]|  
|D ou d|Affiche l'entrée d'énumération sous la forme d'une valeur entière dans la plus courte représentation possible.  L'exemple suivant illustre le spécificateur de format D.<br /><br /> [!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
 [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]|  
|X ou x|Affiche l'entrée d'énumération sous la forme d'une valeur hexadécimale.  La valeur est représentée avec des zéros à gauche le cas échéant, pour garantir que la valeur comprend au moins huit chiffres.  L'exemple suivant illustre le spécificateur de format X.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
 [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]|  
  
## Exemple  
 L'exemple suivant définit une énumération appelée `Colors` qui se compose de trois entrées : `Red`, `Blue` et `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Une fois l'énumération définie, une instance peut être déclarée de la manière suivante.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 La méthode `Color.ToString(System.String)` peut ensuite être utilisée pour afficher la valeur d'énumération de différentes façons, selon le spécificateur de format qui lui est passé.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## Voir aussi  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)