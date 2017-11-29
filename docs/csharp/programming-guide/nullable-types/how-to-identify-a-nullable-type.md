---
title: "Comment : identifier un type Nullable (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Comment : identifier un type Nullable (Guide de programmation C#)
Vous pouvez utiliser l’opérateur C# [typeof](../../../csharp/language-reference/keywords/typeof.md) pour créer un objet <xref:System.Type> qui représente un type Nullable :  
  
```  
System.Type type = typeof(int?);  
```  
  
 Vous pouvez également utiliser les classes et méthodes de l’espace de noms <xref:System.Reflection> pour générer des objets <xref:System.Type> qui représentent des types Nullable. Toutefois, si, pendant l’exécution, vous essayez d’obtenir des informations de type à partir de variables Nullable à l’aide de la méthode <xref:System.Object.GetType%2A> ou de l’opérateur `is`, le résultat est un objet <xref:System.Type> qui représente le type sous-jacent, pas le type Nullable lui-même.  
  
 L’appel de `GetType` sur un type Nullable entraîne l’exécution d’une opération de boxing quand le type est converti implicitement en <xref:System.Object>. Par conséquent, <xref:System.Object.GetType%2A> retourne toujours un objet <xref:System.Type> qui représente le type sous-jacent, pas le type Nullable.  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 L’opérateur C# [is](../../../csharp/language-reference/keywords/is.md) fonctionne également sur le type sous-jacent d’un type Nullable. Par conséquent, vous ne pouvez pas utiliser `is` pour déterminer si une variable est un type Nullable. L’exemple suivant montre que l’opérateur `is` traite une variable Nullable\<int> comme un int.  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a>Exemple  
 Utilisez le code suivant pour déterminer si un objet <xref:System.Type> représente un type Nullable. N’oubliez pas que ce code retourne toujours la valeur false si l’objet`Type` a été retourné à partir d’un appel à <xref:System.Object.GetType%2A>, comme expliqué plus haut dans cette rubrique.  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)  
 [Boxing des types Nullable](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
