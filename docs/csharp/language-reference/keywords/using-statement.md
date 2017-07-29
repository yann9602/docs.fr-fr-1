---
title: "using, instruction (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-statement-c-reference"></a>using, instruction (référence C#)
Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’instruction using.  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Remarques  
 <xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil). Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler. Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.  
  
 En générale, quand vous utilisez un objet `IDisposable`, vous devez le déclarer et l’instancier dans une instruction `using`. L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée. Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.  
  
 L’instruction `using` garantit que la méthode <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit lors de l’appel de méthodes sur l’objet. Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc try, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc finally ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur. L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Il est possible de déclarer plusieurs instances d’un type dans une instruction `using`, comme indiqué dans l’exemple suivant.  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`. En effet, l’objet reste dans la portée une fois que le contrôle a quitté le bloc `using`, même s’il ne peut probablement plus accéder à ses ressources non managées. En d’autres termes, il ne sera plus complètement initialisé. Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception. C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [using, directive](../../../csharp/language-reference/keywords/using-directive.md)   
 [Garbage collection](../../../standard/garbage-collection/index.md)   
 [Implémentation d’une méthode Dispose](../../../standard/garbage-collection/implementing-dispose.md)

