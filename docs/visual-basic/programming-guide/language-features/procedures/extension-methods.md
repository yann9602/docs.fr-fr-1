---
title: "Méthodes d’extension (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ExtensionMethods
dev_langs:
- VB
helpviewer_keywords:
- extending data types
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
caps.latest.revision: 41
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 381fa0db2d92590d23ebd71a7823a8465e94a6e6
ms.lasthandoff: 03/13/2017

---
# <a name="extension-methods-visual-basic"></a>Méthodes d’extension (Visual Basic)
Méthodes d’extension permettent aux développeurs d’ajouter des fonctionnalités personnalisées aux types de données qui sont déjà définis sans créer un type dérivé. Méthodes d’extension permettent d’écrire une méthode qui peut être appelée comme s’il s’agissait d’une méthode d’instance du type existant.  
  
## <a name="remarks"></a>Notes  
 Une méthode d’extension peut uniquement être un `Sub` procédure ou d’un `Function` procédure. Vous ne pouvez pas définir une propriété d’extension, un champ ou un événement. Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension `<Extension()>` à partir de la <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms.</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 Le premier paramètre dans une définition de méthode d’extension Spécifie le type de données s’étend de la méthode. Lorsque la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant définit un `Print` extension pour le <xref:System.String>type de données.</xref:System.String> Utilise la méthode `Console.WriteLine` pour afficher une chaîne. Le paramètre de la `Print` (méthode), `aString`, indique que la méthode étend la <xref:System.String>classe.</xref:System.String>  
  
 [!code-vb[VbVbalrExtensionMethods n °&1;](./codesnippet/VisualBasic/extension-methods_1.vb)]  
  
 Notez que la définition de méthode d’extension est marquée avec l’attribut d’extension `<Extension()>`. Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d’extension doit être marqué. <xref:System.Runtime.CompilerServices>doit être importé pour accéder à l’attribut d’extension.</xref:System.Runtime.CompilerServices>  
  
 Méthodes d’extension peuvent être déclarées dans des modules. En règle générale, le module dans lequel une méthode d’extension est définie n’est pas le même module que celui dans lequel il est appelé. Au lieu de cela, le module qui contient la méthode d’extension est importé, si nécessaire, pour qu’il soit dans l’étendue. Une fois le module qui contient `Print` est dans la portée, la méthode peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire qui n’accepte aucun argument, tel que `ToUpper`:  
  
 [!code-vb[VbVbalrExtensionMethods n °&2;](./codesnippet/VisualBasic/extension-methods_2.vb)]  
  
 L’exemple suivant, `PrintAndPunctuate`, est également une extension <xref:System.String>, cette fois définie avec deux paramètres.</xref:System.String> Le premier paramètre, `aString`, indique que la méthode d’extension étend <xref:System.String>.</xref:System.String> Le deuxième paramètre, `punc`, est destinée à être une chaîne de signes de ponctuation qui est passée comme un argument lorsque la méthode est appelée. La méthode affiche la chaîne suivie par les signes de ponctuation.  
  
 [!code-vb[VbVbalrExtensionMethods n °&3;](./codesnippet/VisualBasic/extension-methods_3.vb)]  
  
 La méthode est appelée en envoyant un argument de chaîne pour `punc`:`example.PrintAndPunctuate(".")`  
  
 L’exemple suivant `Print` et `PrintAndPunctuate` définies et appelées. <xref:System.Runtime.CompilerServices>est importé dans le module de définition pour permettre l’accès à l’attribut d’extension.</xref:System.Runtime.CompilerServices>  
  
### <a name="code"></a>Code  
  
```vb  
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
  
 Ensuite, les méthodes d’extension sont placées dans la portée et appelées.  
  
```vb  
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
  
### <a name="comments"></a>Commentaires  
 Il est requis pour pouvoir exécuter ces ou comme méthodes d’extension est qu’elles dans l’étendue. Si le module qui contient une méthode d’extension est dans la portée, il est visible dans IntelliSense et peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire.  
  
 Notez que lorsque les méthodes sont appelées, aucun argument n’est envoyé au premier paramètre. Paramètre `aString` dans la méthode précédente définitions est lié au `example`, l’instance de `String` qui les appelle. Le compilateur utilise `example` comme argument envoyé au premier paramètre.  
  
 Si une méthode d’extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d’extension s’exécute. Cela ne s’applique pas aux méthodes d’instance ordinaire. Vous pouvez vérifier explicitement `Nothing` dans la méthode d’extension.  
  
## <a name="types-that-can-be-extended"></a>Types qui peuvent être étendus  
 Vous pouvez définir une méthode d’extension sur la plupart des types qui peuvent être représentées dans une liste de paramètres Visual Basic, notamment les suivantes :  
  
-   Classes (types référence)  
  
-   Structures (types valeur)  
  
-   Interfaces  
  
-   Délégués  
  
-   Arguments ByRef et ByVal  
  
-   Paramètres de méthode générique  
  
-   Tableaux  
  
 Étant donné que le premier paramètre spécifie le type de données qui s’étend de la méthode d’extension, il est obligatoire et ne peut pas être facultatif. Pour cette raison, `Optional` paramètres et `ParamArray` paramètres ne peut pas être le premier paramètre dans la liste de paramètres.  
  
 Méthodes d’extension ne sont pas considérés dans la liaison tardive. Dans l’exemple suivant, l’instruction `anObject.PrintMe()` déclenche un <xref:System.MissingMemberException>d’exceptions, la même exception que vous verriez si la seconde `PrintMe` définition de méthode d’extension ont été supprimés.</xref:System.MissingMemberException>  
  
 [!code-vb[VbVbalrExtensionMethods&#9;](./codesnippet/VisualBasic/extension-methods_4.vb)]  
  
## <a name="best-practices"></a>Meilleures pratiques  
 Méthodes d’extension fournissent un moyen pratique et puissant d’étendre un type existant. Toutefois, pour les utiliser avec succès, il existe certains points à prendre en compte. Ces considérations s’appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter les applications qui utilisent des méthodes d’extension.  
  
 Plus généralement, les méthodes d’extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d’extension ajoutées aux types que vous contrôlez. Un certain nombre de choses peut se produire dans les classes que vous ne possédez pas pouvant interférer avec vos méthodes d’extension.  
  
-   Si un membre d’instance accessible existe qui a une signature qui est compatible avec les arguments dans l’instruction d’appel, sans conversions restrictives requises d’un argument pour un paramètre, la méthode d’instance servira plutôt que n’importe quelle méthode d’extension. Par conséquent, si une méthode d’instance appropriée est ajoutée à une classe à un moment donné, un membre d’extension existant que vous fier peut devenir inaccessible.  
  
-   L’auteur d’une méthode d’extension ne peut pas empêcher d’autres programmeurs d’écrire des méthodes d’extension en conflit qui peuvent être prioritaires sur l’extension d’origine.  
  
-   Vous pouvez améliorer la robustesse en plaçant les méthodes d’extension dans leur propre espace de noms. Les consommateurs de votre bibliothèque peuvent ensuite inclure un espace de noms exclure ou sélection parmi les espaces de noms, séparément du reste de la bibliothèque.  
  
-   Il peut être plus sûr d’étendre les interfaces plutôt que d’étendre les classes, surtout si vous ne possédez pas l’interface ou la classe. Une modification dans une interface affecte chaque classe qui l’implémente. Par conséquent, l’auteur peut être moins susceptible d’ajouter ou modifier des méthodes dans une interface. Toutefois, si une classe implémente deux interfaces qui ont des méthodes d’extension avec la même signature, aucune méthode d’extension est visible.  
  
-   Étendez le type le plus spécifique que vous pouvez. Dans une hiérarchie de types, si vous sélectionnez un type à partir de laquelle d’autres types sont dérivés, il existe des couches de l’introduction de méthodes d’instance ou d’autres méthodes d’extension qui peuvent interférer avec les vôtres.  
  
## <a name="extension-methods-instance-methods-and-properties"></a>Méthodes d’extension, les propriétés et les méthodes d’Instance  
 Lorsqu’une méthode d’instance dans la portée a une signature qui est compatible avec les arguments d’une instruction d’appel, la méthode d’instance est choisie plutôt que n’importe quelle méthode d’extension. La méthode d’instance est prioritaire même si la méthode d’extension est une meilleure correspondance. Dans l’exemple suivant, `ExampleClass` contient une méthode d’instance nommée `ExampleMethod` qui a un paramètre de type `Integer`. Méthode d’extension `ExampleMethod` étend `ExampleClass`, et a un paramètre de type `Long`.  
  
 [!code-vb[VbVbalrExtensionMethods n °&4;](./codesnippet/VisualBasic/extension-methods_5.vb)]  
  
 Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d’extension, car `arg1` est `Long` et est compatible uniquement avec le `Long` paramètre dans la méthode d’extension. Le deuxième appel à `ExampleMethod` a un `Integer` argument, `arg2`, et il appelle la méthode d’instance.  
  
 [!code-vb[VbVbalrExtensionMethods n °&5;](./codesnippet/VisualBasic/extension-methods_6.vb)]  
  
 Maintenant inversez les types de données des paramètres dans les deux méthodes :  
  
 [!code-vb[VbVbalrExtensionMethods n °&6;](./codesnippet/VisualBasic/extension-methods_7.vb)]  
  
 Cette fois, le code de `Main` appelle la méthode d’instance les deux fois. C’est parce que les deux `arg1` et `arg2` ont une conversion étendue à `Long`, et la méthode d’instance est prioritaire sur la méthode d’extension dans les deux cas.  
  
 [!code-vb[VbVbalrExtensionMethods&#7;](./codesnippet/VisualBasic/extension-methods_8.vb)]  
  
 Par conséquent, une méthode d’extension ne peut pas remplacer une méthode d’instance existante. Toutefois, lorsqu’une méthode d’extension a le même nom qu’une méthode d’instance, mais les signatures n’entrent pas en conflit, les deux méthodes sont accessibles. Par exemple, si classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui ne prend aucun arguments, les méthodes d’extension portant le même nom mais des signatures différentes sont autorisées, comme indiqué dans le code suivant.  
  
 [!code-vb[VbVbalrExtensionMethods n °&8;](./codesnippet/VisualBasic/extension-methods_9.vb)]  
  
 La sortie de ce code est la suivante :  
  
 `Extension method`  
  
 `Instance method`  
  
 La situation est plus simple avec des propriétés : si une méthode d’extension a le même nom en tant que propriété de la classe qu’elle étend, la méthode d’extension n’est pas visible et n’est pas accessible.  
  
## <a name="extension-method-precedence"></a>Priorité de méthode d’extension  
 Lorsque deux méthodes d’extension qui ont des signatures identiques sont dans la portée et accessible, avec une priorité plus élevée est appelé. Priorité d’une méthode d’extension est basée sur le mécanisme utilisé pour placer la méthode dans la portée. La liste suivante montre la hiérarchie des priorités, du plus élevé au plus bas.  
  
1.  Méthodes d’extension définies dans le module actuel.  
  
2.  Méthodes d’extension définies à l’intérieur des données types dans l’espace de noms actuel ou l’un de ses parents, les espaces de noms enfants étant prioritaires sur les espaces de noms parent.  
  
3.  Méthodes d’extension définies dans les importations de type dans le fichier actuel.  
  
4.  Méthodes d’extension définies dans les importations d’espace de noms dans le fichier actuel.  
  
5.  Méthodes d’extension définies dans les importations de type au niveau du projet.  
  
6.  Méthodes d’extension définies dans les importations de l’espace de noms au niveau du projet.  
  
 Si la priorité ne résout pas l’ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez. Si le `Print` méthode dans l’exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices></xref:System.Runtime.CompilerServices>   
 <xref:System.Runtime.CompilerServices.ExtensionAttribute></xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Module, instruction](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Paramètres facultatifs](./optional-parameters.md)   
 [Tableaux de paramètres](./parameter-arrays.md)   
 [Vue d’ensemble des attributs](../../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
