---
title: "using, instruction (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a>using, instruction (référence C#)
Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’instruction using.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Remarques  
 <xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil). Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler. Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.  
  
Lorsque la durée de vie d’un `IDisposable` objet est limité à une méthode unique, vous devez déclarer et instancier dans un `using` instruction. L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée. Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.  
  
 L’instruction `using` garantit que la méthode <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit lors de l’appel de méthodes sur l’objet. Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc try, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc finally ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur. L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Il est possible de déclarer plusieurs instances d’un type dans une instruction `using`, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`. En effet, l’objet reste dans la portée une fois que le contrôle a quitté le bloc `using`, même s’il ne peut probablement plus accéder à ses ressources non managées. En d’autres termes, il ne sera plus complètement initialisé. Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception. C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Pour plus d’informations sur la suppression de `IDisposable` , consultez [à l’aide des objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [using, directive](../../../csharp/language-reference/keywords/using-directive.md)  
 [Nettoyage de la mémoire](../../../standard/garbage-collection/index.md)  
 [Utilisation d’objets implémentant IDisposable](../../../standard/garbage-collection/using-objects.md)  
 [Interface IDisposable](xref:System.IDisposable)
