---
title: "Classes - Guide C#"
description: "En savoir plus sur les types de classe et découvrir comment les créer"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="classes"></a>Classes
Une *classe* est une construction qui vous permet de créer des types personnalisés en regroupant des variables d’autres types, méthodes et événements. Une classe s’apparente à un plan. Elle définit les données et le comportement d’un type. Si la classe n’est pas déclarée comme static, le code client peut l’utiliser en créant des *objets* ou des *instances* assignés à une variable. La variable reste en mémoire jusqu’à ce que toutes les références à celle-ci soient hors de portée. À ce stade, le CLR la marque comme admissible pour le garbage collection. Si la classe est déclarée comme [static](language-reference/keywords/static.md), il existe une seule copie en mémoire et le code client peut y accéder uniquement par le biais de la classe elle-même, et non par une *variable d’instance*. Pour plus d’informations, consultez [Classes static et membres de classe static](programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Types référence  
Un type défini comme [class](language-reference/keywords/class.md) est un *type référence*. Au moment de l’exécution, quand vous déclarez une variable de type référence, celle-ci contient la valeur [null](language-reference/keywords/null.md) tant que vous n’avez pas explicitement créé une instance de l’objet à l’aide de l’opérateur [new](language-reference/keywords/new.md) ou que vous ne lui avez pas assigné un objet créé ailleurs à l’aide de [new](language-reference/keywords/new.md), comme indiqué dans l’exemple suivant :  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Quand l’objet est créé, la mémoire est allouée sur le tas managé et la variable contient uniquement une référence à l’emplacement de l’objet. Les types sur le tas managé entraînent une surcharge quand ils sont alloués et récupérés par la fonctionnalité de gestion automatique de la mémoire du CLR (appelée *garbage collection*). Toutefois, le garbage collection est également optimisé, et dans la plupart des cas, ne nuit pas aux performances. Pour plus d’informations sur le garbage collection, consultez [Gestion automatique de la mémoire et garbage collection](../standard/garbage-collection/gc.md).  
  
Les types référence prennent entièrement en charge l’*héritage*, caractéristique fondamentale de la programmation orientée objet. Quand vous créez une classe, vous pouvez hériter de toute autre interface ou classe qui n’est pas définie comme [sealed](language-reference/keywords/sealed.md), et d’autres classes peuvent hériter de votre classe et substituer vos méthodes virtuelles. Pour plus d’informations, consultez [Héritage](programming-guide/classes-and-structs/inheritance.md).

## <a name="declaring-classes"></a>Déclaration de classes  
Les classes sont déclarées à l’aide du mot clé [class](language-reference/keywords/class.md), comme l’illustre l’exemple suivant :  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
Le mot clé **class** est précédé du modificateur d’accès. Comme [public](language-reference/keywords/public.md) est utilisé dans ce cas, n’importe qui peut créer des objets à partir de cette classe. Le nom de la classe suit le mot clé **class**. Le reste de la définition est le corps de la classe, où le comportement et les données sont définis. Les champs, propriétés, méthodes et événements d’une classe sont désignés collectivement par le terme « *membres de classe* ».  
  
## <a name="creating-objects"></a>Création d’objets  
Une classe définit un type d’objet, mais il ne s’agit pas d’un objet en soi. Un objet, qui est une entité concrète basée sur une classe, est parfois désigné par le terme « instance de classe ».  
  
Vous pouvez créer des objets en utilisant le mot clé [new](language-reference/keywords/new.md) suivi du nom de la classe sur laquelle l’objet est basé, comme suit :  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Quand une instance d’une classe est créée, une référence à l’objet est repassée au programmeur. Dans l’exemple précédent, `object1` est une référence à un objet basé sur `Customer`. Cette référence fait référence au nouvel objet, mais elle ne contient pas ses données. En fait, vous pouvez créer une référence d’objet sans créer d’objet :  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Nous vous déconseillons de créer des références d’objet comme celle-ci, sans référence à un objet, car toute tentative d’accès à un objet à l’aide d’une telle référence échoue au moment de l’exécution. Vous pouvez toutefois créer une telle référence pour faire référence à un objet : soit en créant un objet, soit en l’assignant à un objet existant, comme suit :  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Ce code crée deux références d’objet qui font toutes deux référence au même objet. Toute modification apportée à l’objet par le biais de `object3` est donc reflétée dans les utilisations suivantes de `object4`. Les objets qui sont basés sur des classes étant désignés par référence, les classes sont appelées des « types référence ».  
  
## <a name="class-inheritance"></a>Héritage de classe  
L’héritage se fait par le biais d’une *dérivation*, ce qui signifie qu’une classe est déclarée à l’aide d’une *classe de base* dont elle hérite les données et le comportement. Pour spécifier une classe de base, ajoutez deux-points et le nom de la classe de base après le nom de la classe dérivée, comme suit :  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Quand une classe déclare une classe de base, elle hérite de tous les membres de la classe de base à l’exception des constructeurs.  
  
Contrairement à C++, une classe en C# ne peut hériter directement que d’une classe de base. Toutefois, une classe de base pouvant elle-même hériter d’une autre classe, une classe peut hériter indirectement de plusieurs classes de base. En outre, une classe peut implémenter directement plusieurs interfaces. Pour plus d’informations, consultez [Interfaces](programming-guide/interfaces/index.md).  
  
Une classe peut être déclarée [abstract](language-reference/keywords/abstract.md). Une classe abstraite contient des méthodes abstraites qui ont une définition de signature, mais aucune implémentation. Les classes abstraites ne peuvent pas être instanciées. Elles peuvent être utilisées uniquement à travers des classes dérivées qui implémentent les méthodes abstraites. En revanche, une classe [sealed](language-reference/keywords/sealed.md) ne permet pas à d’autres classes de dériver d’elle. Pour plus d’informations, consultez [Classes abstract et sealed et membres de classe](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Les définitions de classe peuvent être fractionnées entre différents fichiers sources. Pour plus d’informations, consultez [Définitions de classes partielles](programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
 
## <a name="example"></a>Exemple
Dans l’exemple suivant, une classe publique qui contient un champ unique, une méthode et une méthode spéciale appelée un constructeur est définie. Pour plus d’informations, consultez [Constructeurs](programming-guide/classes-and-structs/constructors.md). La classe est ensuite instanciée à l’aide du mot clé **new**.

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>spécification du langage C#  
Pour plus d’informations, consultez [Spécification du langage C#](language-reference/language-specification/index.md). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi  
[Guide de programmation C#](programming-guide/index.md)   
[Polymorphisme](programming-guide/classes-and-structs/polymorphism.md)   
[Membres de classe et de struct](programming-guide/classes-and-structs/members.md)   
[Méthodes de classe et de struct](programming-guide/classes-and-structs/methods.md)   
[Constructeurs](programming-guide/classes-and-structs/constructors.md)   
[Finaliseurs](programming-guide/classes-and-structs/destructors.md)   
[Objets](programming-guide/classes-and-structs/objects.md)

