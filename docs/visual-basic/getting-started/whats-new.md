---
title: "Nouveautés de Visual Basic | Microsoft Docs"
ms.date: 2017-04-27
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
dev_langs:
- VB
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
author: rpetrusha
ms.author: ronpet
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d3f21e32c162133e70a124da125c30afc7303738
ms.openlocfilehash: 18544a0311e24cf427111e364421db6e9fc27326
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="whats-new-for-visual-basic"></a>Nouveautés de Visual Basic

Cette rubrique liste les noms des principales fonctionnalités de chaque version de Visual Basic et décrit en détail les fonctionnalités nouvelles et améliorées de la dernière version du langage.
  
## <a name="current-version"></a>Version actuelle

Visual Basic / Visual Studio .NET 2017   
Pour connaître les nouvelles fonctionnalités, consultez [Visual Basic 2017](#visual-basic-2017)

## <a name="previous-versions"></a>Versions antérieures

Visual Basic / Visual Studio .NET 2015   
Pour connaître les nouvelles fonctionnalités, consultez [Visual Basic 14](#visual-basic-14)

Visual Basic / Visual Studio .NET 2013  
Aperçus des technologies de la plateforme des compilateurs .NET (« Roslyn »)

Visual Basic / Visual Studio .NET 2012   
Mots clés `Async` et `await`, itérateurs, attributs des informations de l’appelant

Visual Basic, Visual Studio .NET 2010   
Propriétés implémentées automatiquement, initialiseurs de collection, continuation de ligne implicite, variance co/contra générique, dynamique, accès de l’espace de noms global

Visual Basic / Visual Studio .NET 2008   
LINQ (Language Integrated Query), littéraux XML, inférence de type local, initialiseurs d’objet, types anonymes, méthodes d’extension, inférence de type `var` local, expressions lambda, opérateur `if`, méthodes partielles, types de valeur nullable  

Visual Basic / Visual Studio .NET 2005   
Type `My` et types d’assistance (accès à l’application, ordinateur, système de fichiers, réseau)

Visual Basic / Visual Studio .NET 2003   
Opérateurs de décalage de bits, déclaration de variable de boucle

Visual Basic / Visual Studio .NET 2002   
Première version de Visual Basic .NET

## <a name="visual-basic-2017"></a>Visual Basic 2017

[Tuples](../programming-guide/language-features/data-types/tuples.md)

Les tuples sont une structure de données légère qui est le plus souvent utilisée pour retourner plusieurs valeurs à partir d’un seul appel de méthode. En règle générale, pour retourner plusieurs valeurs à partir d’une méthode, vous devez effectuer l’une des opérations suivantes :

- Définir un type personnalisé (`Class` ou `Structure`). Il s’agit d’une solution lourde.

- Définir un ou plusieurs paramètres `ByRef`, en plus de retourner une valeur à partir de la méthode.
 
La prise en charge des tuples par Visual Basic vous permet de définir rapidement un tuple, d’affecter éventuellement des noms de sémantique à ses valeurs et de récupérer rapidement ses valeurs. L’exemple suivant encapsule un appel à la méthode <xref:System.Int32.TryParse%2A> et retourne un tuple.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Vous pouvez ensuite appeler la méthode et gérer le tuple retourné avec du code comme celui-ci.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**Littéraux binaires et séparateurs numériques**

Vous pouvez définir un littéral binaire à l’aide du préfixe `&B` ou `&b`. Vous pouvez aussi utiliser le trait de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité. L’exemple suivant utilise les deux fonctionnalités pour affecter une valeur `Byte` et l’afficher sous la forme d’un nombre décimal, hexadécimal et binaire.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Pour plus d’informations, consultez la section « Affectations de littéraux » des types de données [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) et [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments).

**Prise en charge des valeurs de retour de référence C#**

Depuis C# 7, C# prend en charge les valeurs de retour de référence. Autrement dit, quand la méthode d’appel reçoit une valeur retournée par référence, elle peut modifier la valeur de la référence. Visual Basic ne vous autorise pas à créer des méthodes avec des valeurs de retour de référence, mais vous permet d’utiliser et de modifier ces valeurs.

Par exemple, la classe `Sentence` suivante écrite en C# inclut une méthode `FindNext` qui recherche le mot suivant dans une phrase qui commence par une sous-chaîne spécifiée. La chaîne est retournée comme valeur de retour de référence et une variable `Boolean` passée par référence à la méthode indique si la recherche a réussi. Cela signifie que l’appelant peut non seulement lire la valeur retournée, mais il peut également la modifier et cette modification est répercutée dans la classe `Sentence`.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Sous sa forme la plus simple, vous pouvez modifier le mot trouvé dans la phrase à l’aide de code semblable au suivant. Notez que vous n’affectez pas de valeur à la méthode, mais plutôt à l’expression retournée par la méthode, qui est la valeur de retour de référence.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Ce code pose cependant un problème : si aucune correspondance n’est trouvée, la méthode retourne le premier mot. Comme l’exemple n’examine pas la valeur de l’argument `Boolean` pour déterminer si une correspondance est trouvée, il modifie le premier mot en l’absence de correspondance. L’exemple suivant corrige ce comportement en remplaçant le premier mot par lui-même en l’absence de correspondance.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Une meilleure solution consiste à utiliser une méthode d’assistance à laquelle la valeur de retour de référence est passée par référence. La méthode d’assistance peut ensuite modifier l’argument qui lui est passé par référence. L’exemple suivant effectue cette opération.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Pour plus d’informations, consultez [Valeurs de retour de référence](../programming-guide/language-features/procedures/ref-return-values.md).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Vous pouvez obtenir le nom de chaîne non qualifié d’un type ou membre et l’utiliser dans un message d’erreur sans effectuer de codage irréversible de chaîne.  Votre code reste alors correct lors de la refactorisation.  Cette fonctionnalité est également utile pour placer des liens MVC modèle-vue-contrôleur et activer des événements de modification de propriété.  
  
[Interpolation de chaîne](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Vous pouvez utiliser des expressions d’interpolation de chaîne pour construire des chaînes.  Une expression de chaîne interpolée s’apparente à une chaîne de modèle contenant des expressions.  Les arguments d’une chaîne interpolée sont plus compréhensibles que dans une [Mise en forme composite](../../standard/base-types/composite-format.md).  
  
[Indexation et accès aux membres conditionnels Null](../../csharp/language-reference/operators/null-conditional-operators.md)  
Vous pouvez rechercher les valeurs Null à l’aide d’une syntaxe très légère avant d’effectuer une opération d’accès aux membres (`?.`) ou d’indexation (`?[]`).  Ces opérateurs permettent d’écrire moins de code pour gérer les vérifications Null, notamment pour l’exploration des structures de données.  Si la référence objet ou l’opérande gauche est Null, l’opération retourne la valeur Null.  
  
[Littéraux de chaîne multiligne](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Les littéraux de chaîne peuvent contenir des séquences de saut de ligne.  Il n’est plus nécessaire de passer par la méthode `<xml><![CDATA[...text with newlines...]]></xml>.Value`.  
  
Commentaires  
Vous pouvez placer des commentaires après les continuations de ligne implicite, dans les expressions d’initialiseur et dans les termes d’expression LINQ.  
  
 Résolution de nom qualifié complet plus intelligente  
 En présence de code tel que `Threading.Thread.Sleep(1000)`, Visual Basic recherchait l’espace de noms « Threading », détectait l’ambiguïté entre System.Threading et System.Windows.Threading, et signalait une erreur.  Visual Basic prend désormais en compte les deux espaces de noms possibles.  Lorsque vous affichez la liste de saisie semi-automatique, les membres de ces deux types y sont recensés par l’éditeur Visual Studio.  
  
 Littéraux de date avec année en premier  
 Vous pouvez avoir des littéraux de date au format aaaa-mm-jj, `#2015-03-17 16:10 PM#`.  
  
 Propriétés d’interface en lecture seule  
 Vous pouvez implémenter des propriétés d’interface en lecture seule à l’aide d’une propriété readwrite.  L’interface garantit les fonctionnalités minimales et n’empêche pas une classe d’implémentation d’autoriser la définition de la propriété.  
  
 [TypeOf \<expr> IsNot \<type>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Pour une meilleure lisibilité du code, vous pouvez maintenant utiliser `TypeOf` avec `IsNot`.  
  
 [#Disable Warning \<ID> et #Enable Warning \<ID>](../../visual-basic/language-reference/directives/directives.md)  
 Vous pouvez désactiver et activer des avertissements spécifiques pour les zones d’un fichier source.  
  
 Améliorations de la fonctionnalité de commentaires de document XML  
 Lorsque vous écrivez des commentaires de document, vous bénéficiez d’un éditeur intelligent et de la prise en charge de version pour la validation des noms de paramètres, le gestion appropriée des `crefs` (génériques, opérateurs, etc.), la colorisation et la refactorisation.  
  
 [Définitions d’interface et de module partielles](../../visual-basic/language-reference/modifiers/partial.md)  
 En plus des classes et structures, vous pouvez déclarer des interfaces et des modules partiels.  
  
 [Directives #Region dans le corps de la méthode](../../visual-basic/language-reference/directives/region-directive.md)  
 Vous pouvez placer des délimiteurs #Region…#End Region n’importe où dans un fichier, dans des fonctions, ou encore répartis à différents endroits du corps d’une fonction.  
  
 [Les définitions de substitutions sont implicitement des surcharges](../../visual-basic/language-reference/modifiers/overrides.md)  
 Si vous ajoutez le modificateur `Overrides` à une définition, le compilateur ajoute `Overloads` de manière implicite, de sorte que vous pouvez taper moins de code dans les situations courantes.  
  
 CObj autorisé dans les arguments d’attributs  
 Le compilateur signalait l’erreur indiquant que CObj(...) n’est pas une constante lorsqu’il est utilisé dans les constructions d’attribut.  
  
 Déclaration et utilisation de méthodes ambiguës issues d’interfaces différentes  
 Auparavant, le code suivant générait des erreurs qui vous empêchaient de déclarer `IMock` ou d’appeler `GetDetails` (s’ils avaient été déclarés en C#) :  
  
```vb  
Interface ICustomer  
  Sub GetDetails(x As Integer)  
End Interface  
  
Interface ITime  
  Sub GetDetails(x As String)  
End Interface  
  
Interface IMock : Inherits ICustomer, ITime  
  Overloads Sub GetDetails(x As Char)  
End Interface  
  
Interface IMock2 : Inherits ICustomer, ITime  
End Interface  
```  
  
 À présent, le compilateur utilise les règles de résolution de surcharge normales pour choisir le `GetDetails` à appeler le plus approprié, et vous pouvez déclarer des relations d’interface dans Visual Basic comme indiqué dans l’exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/ide/whats-new-in-visual-studio)

