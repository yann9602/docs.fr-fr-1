---
title: "Génériques et réflexion (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cea1f48f336e4c73fa317d1cbbab3d06ceb6045f
ms.lasthandoff: 03/13/2017

---
# <a name="generics-and-reflection-c-programming-guide"></a>Génériques et réflexion (Guide de programmation C#)
Étant donné que le common language runtime (CLR) a accès aux informations concernant les types génériques au moment de l’exécution, vous pouvez utiliser la réflexion pour obtenir des informations sur les types génériques de la même manière que pour les types non génériques. Pour plus d’informations, consultez [Génériques dans le runtime](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
 Dans le [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)], plusieurs nouveaux membres ont été ajoutés à la classe <xref:System.Type> pour générer des informations d’exécution pour les types génériques. Pour plus d’informations sur l’utilisation de ces méthodes et de ces propriétés, consultez la documentation relative à ces classes. L’espace de noms <xref:System.Reflection.Emit> contient également de nouveaux membres qui prennent en charge les génériques. Consultez [Comment : définir un type générique avec l’émission de réflexion](http://msdn.microsoft.com/library/07d5f01a-7b5b-40ea-9b15-f21561098fe4).  
  
 Pour obtenir la liste des conditions invariables pour les termes utilisés dans la réflexion générique, consultez les notes sur la propriété <xref:System.Type.IsGenericType%2A>.  
  
|Nom de membre System.Type|Description|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|Retourne la valeur true si un type est générique.|  
|<xref:System.Type.GetGenericArguments%2A>|Retourne un tableau d’objets `Type` qui représentent les arguments de type fournis pour un type construit, ou les paramètres de type d’une définition de type générique.|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|Retourne la définition de type générique sous-jacente pour le type construit actuel.|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|Retourne un tableau d'objets `Type` qui représentent les contraintes qui s'exercent sur le paramètre de type générique actuel.|  
|<xref:System.Type.ContainsGenericParameters%2A>|Retourne la valeur true si le type ou l’un de ses types ou méthodes englobants contient des paramètres de type pour lesquels des types spécifiques n’ont pas été fournis.|  
|<xref:System.Type.GenericParameterAttributes%2A>|Obtient une combinaison d’indicateurs `GenericParameterAttributes` décrivant les contraintes spéciales du paramètre de type générique actuel.|  
|<xref:System.Type.GenericParameterPosition%2A>|Pour un objet `Type` qui représente un paramètre de type, obtient la position du paramètre de type dans la liste de paramètres de type de la définition de type générique ou de la définition de méthode générique qui a déclaré le paramètre de type.|  
|<xref:System.Type.IsGenericParameter%2A>|Obtient une valeur indiquant si le `Type` actuel représente un paramètre de type d’un type générique ou d’une définition de méthode.|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|Obtient une valeur qui indique si le <xref:System.Type> actuel représente une définition de type générique, à partir de laquelle d’autres types génériques peuvent être construits. Retourne la valeur true si le type représente la définition d’un type générique.|  
|<xref:System.Type.DeclaringMethod%2A>|Retourne la méthode générique qui a défini le paramètre de type générique actuel, ou Null si le paramètre de type n’a pas été défini par une méthode générique.|  
|<xref:System.Type.MakeGenericType%2A>|Substitue les éléments d’un tableau de types aux paramètres de type de la définition du type générique actuel, et retourne un objet <xref:System.Type> qui représente le type construit résultant.|  
  
 De plus, de nouveaux membres ont été ajoutés à la classe <xref:System.Reflection.MethodInfo> pour générer des informations d’exécution pour les types génériques. Pour obtenir la liste des conditions invariables des termes utilisés pour réfléchir les méthodes génériques, consultez les notes relatives à la propriété <xref:System.Reflection.MethodInfo.IsGenericMethod%2A>.  
  
|Nom de membre System.Reflection.MemberInfo|Description|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|Retourne la valeur true si une méthode est générique.|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|Retourne un tableau d’objets de type qui représentent les arguments de type d’une méthode générique construite, ou les paramètres de type d’une définition de méthode générique.|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|Retourne la définition de méthode générique sous-jacente pour la méthode construite actuelle.|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|Retourne la valeur true si la méthode ou l’un de ses types englobants contient des paramètres de type pour lesquels des types spécifiques n’ont pas été fournis.|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|Retourne la valeur true si le <xref:System.Reflection.MethodInfo> actuel représente la définition d’une méthode générique.|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|Substitue les éléments d’un tableau de types aux paramètres de type de la définition de méthode générique actuelle et retourne un objet <xref:System.Reflection.MethodInfo> représentant la méthode construite résultante.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Réflexion et types génériques](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)   
 [Génériques](https://msdn.microsoft.com/library/ms172192)
