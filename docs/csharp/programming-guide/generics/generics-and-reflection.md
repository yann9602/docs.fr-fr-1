---
title: "G&#233;n&#233;riques et r&#233;flexion (Guide de programmation C#) | Microsoft Docs"
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
  - "génériques (C#), réflexion"
  - "réflexion (C#), types génériques"
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# G&#233;n&#233;riques et r&#233;flexion (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Étant donné que le Common Language Runtime \(CLR\) a accès aux informations de type générique au moment de l'exécution, vous pouvez utiliser la réflexion pour obtenir des informations sur les types génériques de la même manière que sur les types non génériques.  Pour plus d'informations, consultez [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Dans le [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)], plusieurs nouveaux membres sont ajoutés à la classe <xref:System.Type> pour activer des informations d'exécution pour les types génériques.  Consultez la documentation sur ces classes pour plus d'informations sur l'utilisation de ces méthodes et propriétés. L'espace de noms <xref:System.Reflection.Emit> contient également des nouveaux membres qui prennent en charge les génériques.  Consultez [Comment : définir un type générique avec l'émission de réflexion](../Topic/How%20to:%20Define%20a%20Generic%20Type%20with%20Reflection%20Emit.md).  
  
 Pour obtenir la liste des conditions invariables des termes utilisés dans une réflexion générique, consultez les notes sur la propriété <xref:System.Type.IsGenericType%2A>.  
  
|Nom de membre System.Type|Description|  
|-------------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Retourne true si un type est générique.|  
|<xref:System.Type.GetGenericArguments%2A>|Retourne un tableau d'objets `Type` qui représentent les arguments de type fournis pour un type construit, ou les paramètres de type d'une définition de type générique.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Retourne la définition de type générique sous\-jacente pour le type construit en cours.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Retourne un tableau d'objets `Type` qui représentent les contraintes qui s'exercent sur le paramètre de type générique actuel.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Retourne true si le type ou l'un de ses types englobants ou de ses méthodes englobantes contient des paramètres de type pour lesquels les types spécifiques n'ont pas été fournis.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Obtient une combinaison d'indicateurs `GenericParameterAttributes` qui décrivent les contraintes spéciales du paramètre de type générique actuel.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pour un objet `Type` qui représente un paramètre de type, obtient la position du paramètre de type dans la liste des paramètres de type de la définition du type générique ou de la méthode générique qui a déclaré le paramètre de type.|  
|<xref:System.Type.IsGenericParameter%2A>|Obtient une valeur qui indique si le `Type` actuel représente un paramètre de type d'une définition de type ou de méthode générique.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Obtient une valeur qui indique si le <xref:System.Type> actuel représente une définition de type générique, à partir de laquelle d'autres types génériques peuvent être construits.  Retourne true si le type représente la définition d'un type générique.|  
|<xref:System.Type.DeclaringMethod%2A>|Retourne la méthode générique qui a défini le paramètre de type générique actuel, ou null si le paramètre de type n'a pas été défini par une méthode générique.|  
|<xref:System.Type.MakeGenericType%2A>|Substitue les éléments d'un tableau de types aux paramètres de type de la définition de type générique actuelle et retourne un objet <xref:System.Type> représentant le type construit résultant.|  
  
 De plus, les nouveaux membres sont ajoutés à la classe <xref:System.Reflection.MethodInfo> pour activer des informations liées à l'exécution pour les méthodes génériques.  Consultez les remarques concernant la propriété <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> pour obtenir une liste des conditions invariables pour les termes utilisés pour réfléchir aux méthodes génériques.  
  
|Nom de membre System.Reflection.MemberInfo|Description|  
|------------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|Retourne true si une méthode est générique.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Retourne un tableau d'objets Type qui représentent les arguments de type d'une méthode générique construite ou les paramètres de type d'une définition de méthode générique.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Retourne la définition de méthode générique sous\-jacente pour la méthode construite actuelle.|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|Retourne true si la méthode ou l'un de ses types englobants contient l'un des paramètres de type pour lesquels les types spécifiques n'ont pas été fournis.|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|Retourne true si le <xref:System.Reflection.MethodInfo> actuel représente la définition d'une méthode générique.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Substitue les éléments d'un tableau de types aux paramètres de type de la définition de méthode générique actuelle et retourne un objet <xref:System.Reflection.MethodInfo> représentant la méthode construite résultante.|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Réflexion et types génériques](../Topic/Reflection%20and%20Generic%20Types.md)   
 [Génériques](../Topic/Generics%20in%20the%20.NET%20Framework.md)