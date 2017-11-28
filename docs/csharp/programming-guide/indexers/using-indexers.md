---
title: Utilisation d'indexeurs (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5c727edbbea116d858c6acf6b600f8fd9f43ee2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-indexers-c-programming-guide"></a>Utilisation d'indexeurs (Guide de programmation C#)
Les indexeurs simplifient, d’un point de vue syntaxique, la création d’une [classe](../../../csharp/language-reference/keywords/class.md), d’un [struct](../../../csharp/language-reference/keywords/struct.md) ou d’une [interface](../../../csharp/language-reference/keywords/interface.md) auxquels les applications clientes peuvent accéder exactement comme à un tableau. Le plus souvent, les indexeurs sont implémentés dans les types dont l’objectif premier est d’encapsuler une collection ou un tableau interne. Par exemple, supposons que vous avez une classe nommée TempRecord qui représente la température, en Farenheit, enregistrée à 10 moments différents sur une période de 24 heures. La classe contient un tableau de type float nommé « temps » pour représenter les températures, et un <xref:System.DateTime> qui représente la date à laquelle les températures ont été enregistrées. En implémentant un indexeur dans cette classe, les clients peuvent accéder aux températures dans une instance TempRecord sous la forme `float temp = tr[4]` et non sous la forme `float temp = tr.temps[4]`. La notation d’indexeur simplifie non seulement la syntaxe pour les applications clientes, mais elle permet également aux autres développeurs de comprendre de façon plus intuitive l’objectif de la classe.  
  
 Pour déclarer un indexeur sur une classe ou un struct, utilisez le mot clé [this](../../../csharp/language-reference/keywords/this.md), comme dans l’exemple suivant :  
  
```  
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```  
  
## <a name="remarks"></a>Remarques  
 Le type d’un indexeur et le type de ses paramètres doivent être au moins aussi accessibles que l’indexeur lui-même. Pour plus d’informations sur les niveaux d’accessibilité, consultez [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Pour plus d’informations sur l’utilisation d’indexeurs avec une interface, consultez [Indexeurs d’interface](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md).  
  
 La signature d’un indexeur est composée du nombre et des types de ses paramètres formels. Elle n’inclut pas le type de l’indexeur ni les noms des paramètres formels. Si vous déclarez plusieurs indexeurs dans la même classe, ils doivent avoir des signatures différentes.  
  
 Une valeur d’indexeur n’est pas classée comme variable ; vous ne pouvez donc pas la passer comme paramètre [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 Pour affecter à l’indexeur un nom exploitable dans d’autres langages, utilisez un attribut `name` dans la déclaration. Exemple :  
  
```  
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this [int index]   // Indexer declaration  
{  
}  
```  
  
 Cet indexeur portera le nom `TheItem`. Si vous ne précisez pas le nom de l’attribut, `Item` est utilisé comme nom par défaut.  
  
## <a name="example-1"></a>Exemple 1  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment déclarer un champ de tableau privé `temps`, et un indexeur. L’indexeur permet d’accéder directement à l’instance `tempRecord[i]`. Comme alternative à l’utilisation de l’indexeur, vous pouvez déclarer le tableau comme membre [public](../../../csharp/language-reference/keywords/public.md) et accéder directement à ses membres, `tempRecord.temps[i]`.  
  
 Notez que quand l’accès à un indexeur est évalué, par exemple dans une instruction `Console.Write`, l’accesseur [get](../../../csharp/language-reference/keywords/get.md) est appelé. C’est pourquoi une erreur de compilation se produit s’il n’existe aucun accesseur `get`.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideIndexers#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_1.cs)]  
  
## <a name="indexing-using-other-values"></a>Indexation en utilisant d’autres valeurs  
 C# ne limite pas les index au type entier. Par exemple, il peut être utile d’utiliser une chaîne avec un indexeur. Il est possible d’implémenter un tel indexeur en recherchant la chaîne dans la collection et en retournant la valeur appropriée. Comme les accesseurs peuvent être surchargés, les versions chaîne et entier peuvent coexister.  
  
## <a name="example-2"></a>Exemple 2  
  
### <a name="description"></a>Description  
 Cet exemple déclare une classe qui stocke les jours de la semaine. Un accesseur `get` déclaré prend une chaîne, le nom d’un jour, et retourne l’entier correspondant. Par exemple, dimanche retourne 0, lundi retourne 1, et ainsi de suite.  
  
### <a name="code"></a>Code  
 [!code-csharp[csProgGuideIndexers#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-indexers_2.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 La sécurité et la fiabilité des indexeurs peuvent être améliorées de deux manières principales :  
  
-   N’oubliez pas d’incorporer une stratégie de gestion des erreurs au cas où le code client passerait une valeur d’index non valide. Dans le premier exemple décrit plus haut dans cette rubrique, la classe TempRecord fournit une propriété Length qui permet au code client de vérifier l’entrée avant de la passer à l’indexeur. Vous pouvez également placer le code de gestion des erreurs à l’intérieur de l’indexeur lui-même. N’oubliez pas d’indiquer aux utilisateurs toutes les exceptions que vous levez dans un accesseur d’indexeur.  
  
-   Définissez l’accessibilité des accesseurs `get` et [set](../../../csharp/language-reference/keywords/set.md) afin qu’elle soit aussi restrictive que possible. Cela est particulièrement important dans le cas de l’accesseur `set`. Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)  
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)
