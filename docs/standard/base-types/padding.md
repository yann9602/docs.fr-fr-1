---
title: "Remplissage de chaînes dans .NET"
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a>Remplissage de chaînes dans .NET
Utilisez une des opérations suivantes <xref:System.String> méthodes pour créer une nouvelle chaîne qui se compose d’une chaîne d’origine remplie à l’aide de début ou de fin des caractères à une longueur totale spécifiée. Le caractère de remplissage peut être un espace ou un caractère spécifié ; il apparaît donc aligné à droite ou aligné à gauche.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.|  
  
## <a name="padleft"></a>PadLeft  
 Le <xref:System.String.PadLeft%2A?displayProperty=nameWithType> méthode crée une nouvelle chaîne en concaténant suffisamment de caractères de remplissage au début à une chaîne d’origine pour atteindre une longueur totale spécifiée. Le <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> méthode utilise l’espace blanc comme caractère de remplissage et la <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> méthode vous permet de spécifier votre propre caractère de remplissage.  
  
 Le code suivant exemple utilise le <xref:System.String.PadLeft%2A> méthode pour créer une nouvelle chaîne qui est de 20 caractères. L’exemple affiche « `--------Hello World!` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 Le <xref:System.String.PadRight%2A?displayProperty=nameWithType> méthode crée une nouvelle chaîne en concaténant suffisamment caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée. Le <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> méthode utilise l’espace blanc comme caractère de remplissage et la <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> méthode vous permet de spécifier votre propre caractère de remplissage.  
  
 Le code suivant exemple utilise le <xref:System.String.PadRight%2A> méthode pour créer une nouvelle chaîne qui est de 20 caractères. L’exemple affiche « `Hello World!--------` » sur la console.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)
