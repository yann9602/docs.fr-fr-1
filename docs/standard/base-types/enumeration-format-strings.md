---
title: "Chaînes de format d'énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0992d8591711073f9094c29fad980a8e652e686
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="enumeration-format-strings"></a>Chaînes de format d'énumération
Vous pouvez utiliser la <xref:System.Enum.ToString%2A?displayProperty=nameWithType> méthode pour créer un nouvel objet de chaîne qui représente le numérique, hexadécimal ou valeur de chaîne d’un membre d’énumération. Cette méthode prend l’une des chaînes de mise en forme d’énumération pour spécifier la valeur à retourner.  
  
 Le tableau suivant liste les chaînes de mise en forme d’énumération et les valeurs qu’elles retournent. Ces spécificateurs de format ne respectent pas la casse.  
  
| Chaîne de mise en forme | Résultat |  
| ------------- | ------ |  
| G ou g | Affiche l’entrée d’énumération comme valeur de chaîne, dans la mesure du possible ; sinon, affiche la valeur entière de l’instance actuelle. Si l’énumération est définie avec l’attribut **Flags** défini, les valeurs de chaîne de chaque entrée valide sont concaténées et séparées par des virgules. Si l’attribut **Flags** n’est pas défini, une valeur non valide s’affiche comme entrée numérique. L’exemple suivant illustre le spécificateur de format G.<br><br>[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)] |  
| F ou f | Affiche l’entrée d’énumération comme valeur de chaîne, si possible. Si la valeur peut être complètement affichée comme somme des entrées de l’énumération (même si l’attribut **Flags** n’est pas présent), les valeurs de chaîne de chaque entrée valide sont concaténées ensemble, séparées par des virgules. Si la valeur ne peut pas être complètement déterminée par les entrées de l’énumération, la valeur est mise en forme comme valeur entière. L’exemple suivant illustre le spécificateur de format F.<br><br>[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)] |  
| D ou d | Affiche l’entrée d’énumération comme valeur entière dans la représentation la plus courte possible. L’exemple suivant illustre le spécificateur de format D.<br><br>[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)] |  
| X ou x | Affiche l’entrée d’énumération comme valeur hexadécimale. La valeur est représentée avec des zéros non significatifs, afin qu’elle comporte au minimum huit chiffres. L’exemple suivant illustre le spécificateur de format X.<br /><br /> [!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)] |  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit une énumération appelée `Colors` qui se compose de trois entrées : `Red`, `Blue` et `Green`.  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 Une fois que l’énumération est définie, une instance peut être déclarée de la manière suivante.  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 La méthode `Color.ToString(System.String)` peut ensuite être utilisée pour afficher la valeur d’énumération de différentes manières, selon le spécificateur de format qui lui est passé.  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)
