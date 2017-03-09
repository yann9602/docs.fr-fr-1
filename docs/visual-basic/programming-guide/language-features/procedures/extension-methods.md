---
title: "M&#233;thodes d&#39;extension (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ExtensionMethods"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "étendre les types de données"
  - "méthodes d'extension (Visual Basic)"
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 41
---
# M&#233;thodes d&#39;extension (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les méthodes d'extension permettent aux développeurs d'ajouter des fonctionnalités personnalisées aux types de données déjà définis sans créer de type dérivé.  Les méthodes d'extension permettent d'écrire une méthode qui peut être appelée comme une méthode d'instance du type existant.  
  
## Remarques  
 Une méthode d'extension peut uniquement être une procédure `Sub` ou `Function`.  Vous ne pouvez pas définir une propriété d'extension, un champ ou un événement.  Toutes les méthodes d'extension doivent être marquées avec l'attribut d'extension, `<Extension()>`, à partir de l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=fullName>.  
  
 Le premier paramètre d'une définition de méthode d'extension spécifie le type de données étendu par la méthode.  Lorsque la méthode est exécutée, le premier paramètre est lié à l'instance du type de données qui appelle la méthode.  
  
## Exemple  
  
### Description  
 L'exemple suivant définit une extension `Print` pour le type de données <xref:System.String>.  La méthode utilise `Console.WriteLine` pour afficher une chaîne.  Le paramètre de la méthode `Print`, `aString`, indique que la méthode étend la classe <xref:System.String>.  
  
 [!code-vb[VbVbalrExtensionMethods#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/StringExtensions.vb#1)]  
  
 Notez que la définition de méthode d'extension est marquée avec l'attribut d'extension `<Extension()>`.  Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d'extension doit être marquée.  <xref:System.Runtime.CompilerServices> doit être importé pour que l'attribut d'extension soit accessible.  
  
 Les méthodes d'extension ne peuvent être déclarées que dans des modules.  En général, le module dans lequel une méthode d'extension est définie n'est pas le même que celui dans lequel elle est appelée.  À la place, le module qui contient la méthode d'extension est importé, si nécessaire, pour être placé dans la portée.  Une fois que le module qui contient `Print` est placé dans la portée, la méthode peut être appelée comme une méthode d'instance ordinaire qui ne prend pas d'arguments, telle que `ToUpper` :  
  
 [!code-vb[VbVbalrExtensionMethods#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class1.vb#2)]  
  
 L'exemple suivant, `PrintAndPunctuate`, est également une extension vers <xref:System.String>, cette fois définie avec deux paramètres.  Le premier paramètre, `aString`, indique que la méthode d'extension étend <xref:System.String>.  Le deuxième paramètre, `punc`, est une chaîne de signes de ponctuation passée comme un argument lorsque la méthode est appelée.  La méthode affiche la chaîne suivie des signes de ponctuation.  
  
 [!code-vb[VbVbalrExtensionMethods#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class2.vb#3)]  
  
 La méthode est appelée en envoyant un argument de chaîne pour `punc` : `example.PrintAndPunctuate(".")`  
  
 Dans l'exemple suivant, les méthodes `Print` et `PrintAndPunctuate` sont définies et appelées.  <xref:System.Runtime.CompilerServices> est importé dans le module de définition pour permettre l'accès à l'attribut d'extension.  
  
### Code  
  
```vb#  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
  
    <Extension()>   
    Public Sub Print(ByVal aString As String)  
        Console.WriteLine(aString)  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 Ensuite, les méthodes d'extension sont placées dans la portée et appelées.  
  
```vb#  
Imports ConsoleApplication2.StringExtensions  
Module Module1  
  
    Sub Main()  
  
        Dim example As String = "Example string"  
        example.Print()  
  
        example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
    End Sub  
End Module  
```  
  
### Commentaires  
 Pour que ces méthodes d'extension ou des méthodes similaires puissent être exécutées, il faut qu'elles soient placées dans la portée.  Si le module qui contient une méthode d'extension se trouve dans la portée, il apparaît dans IntelliSense et peut être appelé comme une méthode d'instance ordinaire.  
  
 Notez que lorsque les méthodes sont appelées, aucun argument n'est envoyé pour le premier paramètre.  Le paramètre `aString` dans les définitions de méthode précédentes est lié à `example`, l'instance de `String` qui les appelle.  Le compilateur utilise `example` comme argument envoyé au premier paramètre.  
  
 Si une méthode d'extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d'extension s'exécute.  Cela ne s'applique pas aux méthodes d'instance ordinaires.  Vous pouvez explicitement vérifier `Nothing` dans la méthode d'extension.  
  
## Types qui peuvent être étendus  
 Vous pouvez définir une méthode d'extension pour la plupart des types qui peuvent être représentés dans une liste de paramètres Visual Basic, notamment les éléments suivants :  
  
-   Classes \(types référence\)  
  
-   Structures \(types valeur\)  
  
-   Interfaces  
  
-   Délégués  
  
-   Arguments ByRef et ByVal  
  
-   Paramètres de méthode générique  
  
-   Tableaux  
  
 Étant donné que le premier paramètre spécifie le type de données étendu par la méthode d'extension, il est requis et ne peut pas être facultatif.  Pour cette raison, les paramètres `Optional` et `ParamArray` ne peuvent pas être le premier paramètre de la liste de paramètres.  
  
 Les méthodes d'extension ne sont pas prises en compte dans la liaison tardive.  Dans l'exemple suivant, l'instruction `anObject.PrintMe()` lève une exception <xref:System.MissingMemberException> qui correspond à celle levée si la deuxième définition de méthode d'extension `PrintMe` est supprimée.  
  
 [!code-vb[VbVbalrExtensionMethods#9](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class6.vb#9)]  
  
## Meilleures pratiques  
 Les méthodes d'extension fournissent une façon pratique et puissante d'étendre un type existant.  Toutefois, pour les utiliser correctement, certains points doivent être considérés.  Ces considérations s'appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter n'importe quelle application utilisant des méthodes d'extension.  
  
 La plupart du temps, les méthodes d'extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d'extension ajoutées aux types que vous contrôlez.  Plusieurs événements peuvent se produire dans les classes que vous ne possédez pas, pouvant interférer avec vos méthodes d'extension.  
  
-   Si un membre d'instance accessible existe avec une signature compatible avec les arguments dans l'instruction d'appel, sans conversions restrictives requises d'un argument en un paramètre, la méthode d'instance sera utilisée de préférence à toute méthode d'extension.  Par conséquent, si une méthode d'instance appropriée est ajoutée à une classe à un moment donné, un membre d'extension existant auquel vous vous conformez peut devenir inaccessible.  
  
-   L'auteur d'une méthode d'extension ne peut pas empêcher d'autres programmeurs d'écrire des méthodes d'extension en conflit qui peuvent être prioritaires sur l'extension d'origine.  
  
-   Vous pouvez améliorer la robustesse en plaçant les méthodes d'extension dans leur propre espace de noms.  Les consommateurs de votre bibliothèque peuvent ensuite inclure ou exclure un espace de noms, ou réaliser une sélection parmi les espaces de noms, de manière séparée pour le reste de la bibliothèque.  
  
-   Il peut être plus sûr d'étendre les interfaces plutôt que d'étendre les classes, notamment si vous ne possédez pas l'interface ou la classe.  Une modification dans une interface affecte chaque classe implémentée.  Par conséquent, l'auteur peut être moins tenté d'ajouter ou de modifier les méthodes dans une interface.  Toutefois, si une classe implémente deux interfaces qui ont des méthodes d'extension avec la même signature, aucune méthode d'extension n'est visible.  
  
-   Étendez le type le plus spécifique possible.  Dans une hiérarchie de types, si vous sélectionnez un type à partir duquel d'autres types sont dérivés, l'introduction de méthodes d'instance ou d'autres méthodes d'extension peuvent interférer avec les vôtres.  
  
## Méthodes d'extension, méthodes d'instance et propriétés  
 Lorsqu'une méthode d'instance dans la portée a une signature qui est compatible avec les arguments d'une instruction appelante, la méthode d'instance est choisie dans la préférence à toute méthode d'extension.  La méthode d'instance a même la priorité si la méthode d'extension est une meilleure correspondance.  Dans l'exemple suivant, `ExampleClass` contient une méthode d'instance nommée `ExampleMethod` qui a un paramètre de type `Integer`.  La méthode d'extension `ExampleMethod` étend `ExampleClass`et a un paramètre de type `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class4.vb#4)]  
  
 Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d'extension, parce que `arg1` est de type `Long` et est compatible uniquement avec le paramètre `Long` dans la méthode d'extension.  Le deuxième appel à `ExampleMethod` a un argument `Integer`, `arg2`, et il appelle la méthode d'instance.  
  
 [!code-vb[VbVbalrExtensionMethods#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class4.vb#5)]  
  
 Maintenant inversez les types de données des paramètres dans les deux méthodes :  
  
 [!code-vb[VbVbalrExtensionMethods#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class5.vb#6)]  
  
 Cette fois, le code dans `Main` appelle la méthode d'instance les deux fois.  C'est parce que `arg1` et `arg2` ont une conversion étendue à `Long`, et que la méthode d'instance est prioritaire sur la méthode d'extension dans les deux cas.  
  
 [!code-vb[VbVbalrExtensionMethods#7](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Class5.vb#7)]  
  
 Par conséquent, une méthode d'extension ne peut pas remplacer une méthode d'instance existante.  Toutefois, lorsqu'une méthode d'extension porte le même nom qu'une méthode d'instance, les deux méthodes sont accessibles tant que les signatures ne sont pas en conflit.  Par exemple, si la classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui ne prend pas d'arguments, une méthode d'extension portant le même nom mais avec une signature différente est autorisée, comme illustré dans le code ci\-après.  
  
 [!code-vb[VbVbalrExtensionMethods#8](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/visualbasic/ConsoleApplication1/Module3.vb#8)]  
  
 La sortie de ce code est la suivante :  
  
 `Extension method`  
  
 `Instance method`  
  
 La situation est plus simple avec des propriétés : si une méthode d'extension a le même nom qu'une propriété de la classe qu'elle étend, la méthode d'extension n'est pas visible et n'est pas accessible.  
  
## Priorité de méthode d'extension  
 Lorsque deux méthodes d'extension ayant des signatures identiques se trouvent dans la portée et sont accessibles, la méthode prioritaire sera appelée.  La priorité d'une méthode d'extension est basée sur le mécanisme utilisé pour placer la méthode dans la portée.  La liste suivante présente la hiérarchie de priorité par ordre décroissant.  
  
1.  Méthodes d'extension définies au sein du module actuel.  
  
2.  Méthodes d'extension définies au sein de types de données dans l'espace de noms actuel ou dans l'un de ses parents, les espaces de noms enfants étant prioritaires sur les espaces de noms parents.  
  
3.  Méthodes d'extension définies dans les importations de type dans le fichier en cours.  
  
4.  Méthodes d'extension définies dans les importations d'espaces de noms dans le fichier en cours.  
  
5.  Méthodes d'extension définies dans les importations de type au niveau du projet.  
  
6.  Méthodes d'extension définies dans les importations d'espaces de noms au niveau du projet.  
  
 Si la priorité ne résout pas l'ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez.  Si la méthode `Print` dans l'exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Méthodes d'extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Attributs](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)