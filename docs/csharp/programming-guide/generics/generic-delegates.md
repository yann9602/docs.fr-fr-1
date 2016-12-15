---
title: "D&#233;l&#233;gu&#233;s g&#233;n&#233;riques (guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "délégués (C#), génériques"
  - "génériques (C#), délégués"
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# D&#233;l&#233;gu&#233;s g&#233;n&#233;riques (guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un [délégué](../../../csharp/language-reference/keywords/delegate.md) peut définir ses propres paramètres de type.  Le code qui référence le délégué générique peut spécifier l'argument de type pour créer un type construit fermé, comme lors de l'instanciation d'une classe générique ou d'un appel d'une méthode générique, ainsi que l'illustre l'exemple ci\-dessous :  
  
 [!code-cs[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 Le langage C\# version 2.0 possède une nouvelle fonctionnalité appelée conversion de groupe de méthodes, qui s'applique pour aussi bien aux types concrets qu'aux types délégués génériques et vous permet d'écrire la ligne précédente avec la syntaxe simplifiée suivante :  
  
 [!code-cs[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Les délégués définis dans une classe générique peuvent utiliser les paramètres de type de classe générique, à l'instar des méthodes de classe.  
  
 [!code-cs[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Le code qui référence le délégué doit spécifier l'argument de type de la classe conteneur, comme suit :  
  
 [!code-cs[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Les délégués génériques sont particulièrement utiles pour définir des événements basés sur le modèle de design type parce que l'argument de l'expéditeur peut être fortement typé et il n'est plus nécessaire d'en effectuer un cast vers et depuis <xref:System.Object>.  
  
 [!code-cs[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Classes génériques](../../../csharp/programming-guide/generics/generic-classes.md)   
 [Interfaces génériques](../../../csharp/programming-guide/generics/generic-interfaces.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Génériques](../Topic/Generics%20in%20the%20.NET%20Framework.md)