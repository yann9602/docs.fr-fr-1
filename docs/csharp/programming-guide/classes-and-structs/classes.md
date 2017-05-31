---
title: Classes (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 1f327e7171df8b91d4c5a787c879069a4e44f562
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="classes-c-programming-guide"></a>Classes (Guide de programmation C#)
Une *classe* est une construction qui vous permet de créer vos propres types personnalisés en regroupant des variables d’autres types, méthodes et événements. Une classe s’apparente à un plan. Elle définit les données et le comportement d’un type. Si la classe n’est pas déclarée comme static, le code client peut l’utiliser en créant des *objets* ou des *instances* assignés à une variable. La variable reste en mémoire jusqu’à ce que toutes les références à celle-ci soient hors de portée. À ce stade, le CLR la marque comme admissible pour le garbage collection. Si la classe est déclarée comme [static](../../../csharp/language-reference/keywords/static.md), il existe une seule copie en mémoire et le code client peut y accéder uniquement par le biais de la classe elle-même, et non par le biais d’une *variable d’instance*. Pour plus d’informations, consultez [Classes static et membres de classe static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Contrairement aux structs, les classes prennent en charge l’*héritage*, caractéristique fondamentale de la programmation orientée objet. Pour plus d’informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Déclaration de classes  
 Les classes sont déclarées à l’aide du mot clé [class](../../../csharp/language-reference/keywords/class.md), comme l’illustre l’exemple suivant :  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 Le mot clé `class` est précédé du niveau d’accès. Comme [public](../../../csharp/language-reference/keywords/public.md) est utilisé dans ce cas, n’importe qui peut créer des objets à partir de cette classe. Le nom de la classe suit le mot clé `class`. Le reste de la définition est le corps de la classe, où le comportement et les données sont définis. Les champs, propriétés, méthodes et événements d’une classe sont désignés collectivement par le terme « *membres de classe* ».  
  
## <a name="creating-objects"></a>Création d'objets  
 Bien qu’ils soient parfois employés indifféremment, une classe et un objet sont deux choses différentes. Une classe définit un type d’objet, mais il ne s’agit pas d’un objet en soi. Un objet, qui est une entité concrète basée sur une classe, est parfois désigné par le terme « instance de classe ».  
  
 Vous pouvez créer des objets en utilisant le mot clé [new](../../../csharp/language-reference/keywords/new.md) suivi du nom de la classe sur laquelle l’objet est basé, comme suit :  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Quand une instance d’une classe est créée, une référence à l’objet est repassée au programmeur. Dans l’exemple précédent, `object1` est une référence à un objet basé sur `Customer`. Cette référence fait référence au nouvel objet, mais elle ne contient pas ses données. En fait, vous pouvez créer une référence d’objet sans créer d’objet :  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Nous vous déconseillons de créer des références d’objet comme celle-ci, sans référence à un objet, car toute tentative d’accès à un objet à l’aide d’une telle référence échoue au moment de l’exécution. Vous pouvez toutefois créer une telle référence pour faire référence à un objet : soit en créant un objet, soit en l’assignant à un objet existant, comme suit :  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Ce code crée deux références d’objet qui font toutes deux référence au même objet. Toute modification apportée à l’objet par le biais de `object3` est donc reflétée dans les utilisations suivantes de `object4`. Les objets qui sont basés sur des classes étant désignés par référence, les classes sont appelées des « types référence ».  
  
## <a name="class-inheritance"></a>Héritage de classe  
 L’héritage se fait par le biais d’une *dérivation*, ce qui signifie qu’une classe est déclarée à l’aide d’une *classe de base* dont elle hérite les données et le comportement. Pour spécifier une classe de base, ajoutez deux-points et le nom de la classe de base après le nom de la classe dérivée, comme suit :  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Quand une classe déclare une classe de base, elle hérite de tous les membres de la classe de base à l’exception des constructeurs.  
  
 Contrairement à C++, une classe en C# ne peut hériter directement que d’une classe de base. Toutefois, une classe de base pouvant elle-même hériter d’une autre classe, une classe peut hériter indirectement de plusieurs classes de base. En outre, une classe peut implémenter directement plusieurs interfaces. Pour plus d’informations, consultez [Interfaces](../../../csharp/programming-guide/interfaces/index.md).  
  
 Une classe peut être déclarée [abstract](../../../csharp/language-reference/keywords/abstract.md). Une classe abstraite contient des méthodes abstraites qui ont une définition de signature, mais aucune implémentation. Les classes abstraites ne peuvent pas être instanciées. Elles peuvent être utilisées uniquement à travers des classes dérivées qui implémentent les méthodes abstraites. En revanche, une classe [sealed](../../../csharp/language-reference/keywords/sealed.md) ne permet pas à d’autres classes de dériver d’elle. Pour plus d’informations, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Les définitions de classe peuvent être fractionnées entre différents fichiers sources. Pour plus d’informations, consultez [Classes et méthodes partielles](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Description  
 Dans l’exemple suivant, une classe publique qui contient un champ unique, une méthode et une méthode spéciale appelée un constructeur est définie. Pour plus d’informations, consultez [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md). La classe est ensuite instanciée à l’aide du mot clé `new`.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Programmation orientée objet](../concepts/object-oriented-programming.md)   
 [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [Membres](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [Objets](../../../csharp/programming-guide/classes-and-structs/objects.md)
