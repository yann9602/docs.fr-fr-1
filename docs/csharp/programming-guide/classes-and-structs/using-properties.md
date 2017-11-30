---
title: "Utilisation de propriétés (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aae36195f4a6eb2ab49ec27e1e07debff7289b37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-properties-c-programming-guide"></a>Utilisation de propriétés (Guide de programmation C#)
Les propriétés allient des caractéristiques des champs et des méthodes. Pour l’utilisateur d’un objet, une propriété s’apparente à un champ. Pour accéder à celle-ci, il doit utiliser la même syntaxe. Pour l’implémenteur d’une classe, une propriété est constituée d’un ou deux blocs de code, représentant un accesseur [get](../../../csharp/language-reference/keywords/get.md) et/ou un accesseur [set](../../../csharp/language-reference/keywords/set.md). Le bloc de code correspondant à l’accesseur `get` est exécuté à la lecture de la propriété ; le bloc de code correspondant à l’accesseur `set` est exécuté au moment où une nouvelle valeur est assignée à la propriété. Une propriété sans accesseur `set` est considérée comme étant en lecture seule. Une propriété sans accesseur `get` est considérée comme étant en écriture seule. Une propriété qui possède les deux accesseurs est en lecture-écriture.  
  
 Contrairement aux champs, les propriétés ne sont pas classifiées en tant que variables. Par conséquent, vous ne pouvez pas passer une propriété en tant que paramètre [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md).  
  
 Les propriétés ont diverses utilisations : elles peuvent valider les données avant d’autoriser une modification ; elles peuvent exposer de manière transparente les données d’une classe quand celles-ci sont effectivement extraites d’une autre source, telle qu’une base de données ; elles peuvent effectuer une action quand des données sont modifiées, comme déclencher un événement ou modifier la valeur d’autres champs.  
  
 Les propriétés sont déclarées dans le bloc de classe en spécifiant le niveau d’accès du champ, suivi du type de la propriété, du nom de la propriété et d’un bloc de code qui déclare un accesseur `get` et/ou un accesseur `set`. Exemple :  
  
 [!code-csharp[csProgGuideProperties#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_1.cs)]  
  
 Dans cet exemple, `Month` est déclaré en tant que propriété pour permettre à l’accesseur `set` de vérifier que la valeur définie de `Month` se trouve bien entre 1 et 12. La propriété `Month` utilise un champ privé pour assurer le suivi de la valeur réelle. L’emplacement réel des données d’une propriété est souvent appelé « magasin de stockage » de la propriété. Il est courant que les propriétés utilisent des champs privés comme magasin de stockage. Le champ est marqué comme étant privé pour garantir qu’il ne peut être modifié qu’en appelant la propriété. Pour plus d’informations sur les restrictions d’accès public et privé, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Les propriétés implémentées automatiquement fournissent une syntaxe simplifiée pour des déclarations de propriété simples. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Accesseur get  
 Le corps de l’accesseur `get` ressemble à celui d’une méthode. Il doit retourner une valeur du type de la propriété. L’exécution de l’accesseur `get` revient à lire la valeur du champ. Par exemple, quand vous retournez la variable privée de l’accesseur `get` et que les optimisations sont activées, l’appel à la méthode de l’accesseur `get` est intégré (inline) par le compilateur, si bien il n’existe aucune surcharge d’appel de méthode. Cependant, une méthode d’accesseur `get` virtuelle ne peut pas être inline, car le compilateur ne sait pas au moment de la compilation quelle méthode peut être effectivement appelée au moment de l’exécution. Voici un exemple d’accesseur `get` qui retourne la valeur d’un champ privé `name` :  
  
 [!code-csharp[csProgGuideProperties#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_2.cs)]  
  
 Quand vous faites référence à la propriété (pas en tant que cible d’une assignation), l’accesseur `get` est appelé pour lire la valeur de la propriété. Exemple :  
  
 [!code-csharp[csProgGuideProperties#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_3.cs)]  
  
 L’accesseur `get` doit se terminer dans une instruction [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md) et le contrôle ne peut pas déborder du corps de l’accesseur.  
  
 Modifier l’état de l’objet en utilisant l’accesseur `get` n’est pas un style de programmation approprié. Par exemple, l’accesseur suivant s’accompagne d’un effet secondaire, à savoir que l’état de l’objet est modifié chaque fois que le champ `number` fait l’objet d’un accès.  
  
 [!code-csharp[csProgGuideProperties#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_4.cs)]  
  
 L’accesseur `get` peut être utilisé pour retourner la valeur du champ ou pour la calculer et la retourner. Exemple :  
  
 [!code-csharp[csProgGuideProperties#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_5.cs)]  
  
 Dans le segment de code précédent, si vous n’assignez pas de valeur à la propriété `Name`, elle retourne la valeur NA.  
  
## <a name="the-set-accessor"></a>Accesseur Set  
 L’accesseur `set` ressemble à une méthode dont le type de retour est [void](../../../csharp/language-reference/keywords/void.md). Il utilise un paramètre implicite nommé `value`, dont le type est celui de la propriété. Dans l’exemple ci-dessous, un accesseur `set` est ajouté à la propriété `Name` :  
  
 [!code-csharp[csProgGuideProperties#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_6.cs)]  
  
 Quand vous assignez une valeur à la propriété, l’accesseur `set` est appelé en utilisant un argument qui fournit la nouvelle valeur. Exemple :  
  
 [!code-csharp[csProgGuideProperties#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_7.cs)]  
  
 Il s’agit d’une erreur d’utiliser le nom de paramètre implicite, `value`, pour une déclaration de variable locale dans un accesseur `set`.  
  
## <a name="remarks"></a>Remarques  
 Les propriétés peuvent être marquées comme `public`, `private`, `protected`, `internal`, `protected internal` ou `private protected`. Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder à la propriété. Les accesseurs `get` et `set` d’une même propriété peuvent avoir des modificateurs d’accès différents. Par exemple, l’accesseur `get` peut être `public` pour autoriser l’accès en lecture seule en dehors du type, tandis que l’accesseur `set` peut être `private` ou `protected`. Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Une propriété peut être déclarée en tant que propriété statique à l’aide du mot clé `static`. La propriété devient ainsi accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe. Pour plus d’informations, consultez [Classes static et membres de classe static](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Une propriété peut être marquée comme étant une propriété virtuelle à l’aide du mot clé [virtual](../../../csharp/language-reference/keywords/virtual.md). Cela permet aux classes dérivées de substituer le comportement de la propriété à l’aide du mot clé [override](../../../csharp/language-reference/keywords/override.md). Pour plus d'informations sur ces options, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Un propriété qui se substitue à une propriété virtuelle peut aussi être [sealed](../../../csharp/language-reference/keywords/sealed.md), ce qui signifie que pour les classes dérivées, elle n’est plus virtuelle. Enfin, une propriété peut être déclarée comme étant [abstract](../../../csharp/language-reference/keywords/abstract.md). Cela signifie qu’il n’existe aucune implémentation dans la classe et que les classes dérivées doivent écrire leur propre implémentation. Pour plus d’informations sur ces options, consultez [Classes abstract et sealed et membres de classe](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
>  Il s’agit d’une erreur d’utiliser un modificateur [virtual](../../../csharp/language-reference/keywords/virtual.md), [abstract](../../../csharp/language-reference/keywords/abstract.md) ou [override](../../../csharp/language-reference/keywords/override.md) sur un accesseur de propriété [static](../../../csharp/language-reference/keywords/static.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre les propriétés d’instance, statiques et en lecture seule. Il accepte le nom de l’employé à partir du clavier, incrémente `NumberOfEmployees` de 1 et affiche le nom et le numéro de l’employé.  
  
 [!code-csharp[csProgGuideProperties#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_8.cs)]  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment accéder à une propriété de classe de base qui est masquée par une autre propriété qui porte le même nom dans une classe dérivée.  
  
 [!code-csharp[csProgGuideProperties#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_9.cs)]  
  
 Voici les points importants de l’exemple précédent :  
  
-   La propriété `Name` de la classe dérivée masque la propriété `Name` de la classe de base. En pareil cas, le modificateur `new` est utilisé dans la déclaration de la propriété de la classe dérivée :  
  
     [!code-csharp[csProgGuideProperties#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_10.cs)]  
  
-   La conversion de type `(Employee)` est utilisée pour accéder à la propriété masquée de la classe de base :  
  
     [!code-csharp[csProgGuideProperties#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_11.cs)]  
  
     Pour plus d’informations sur le masquage des membres, consultez [new, modificateur](../../../csharp/language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, deux classes, `Cube` et `Square`, implémentent une classe abstract, `Shape`, et remplacent sa propriété `Area` abstract. Notez l’utilisation du modificateur [override](../../../csharp/language-reference/keywords/override.md) sur les propriétés. Le programme accepte le côté (« side ») comme entrée et calcule les surfaces (« areas ») du carré (« square ») et du cube. De même, il accepte la surface (« area ») comme entrée et calcule le côté (« side ») correspondant du carré (« square ») et du cube.  
  
 [!code-csharp[csProgGuideProperties#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-properties_12.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Propriétés de l’interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
 [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
