---
title: "What&#39;s New for Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "VB.StartPage.WhatsNew"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "new features, Visual Basic"
  - "what's new [Visual Basic]"
  - "Visual Basic, what's new"
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 145
---
# What&#39;s New for Visual Basic
[!INCLUDE[vs2017banner](../../visual-basic/includes/vs2017banner.md)]

Cette page recense les noms des principales fonctionnalités pour chaque version de Visual Basic et décrit les fonctionnalités nouvelles et améliorées de la dernière version du langage.  
  
## Versions antérieures  
 Visual Basic \/ Visual Studio .NET 2002  
 Première version  
  
 Visual Basic \/ Visual Studio .NET 2003  
 Opérateurs de décalage de bits, déclaration de variable de boucle  
  
 Visual Basic \/ Visual Studio .NET 2005  
 Type `My` et types d’assistance \(accès à l’application, ordinateur, système de fichiers, réseau\)  
  
 Visual Basic \/ Visual Studio .NET 2008  
 Language Integrated Query \(LINQ\), littéraux XML, inférence de type local, initialiseurs d’objet, types anonymes, méthodes d’extension, inférence de type `var` local, expressions lambda, opérateur `if`, méthodes partielles, types de valeur nullable  
  
 Visual Basic, Visual Studio .NET 2010  
 Propriétés implémentées automatiquement, initialiseurs de collection, continuation de ligne implicite, variance co\/contra générique, dynamique, accès de l’espace de noms global  
  
 Visual Basic \/ Visual Studio .NET 2012  
 `Async` \/ `await`, itérateurs, attributs des informations de l’appelant  
  
 Visual Basic \/ Visual Studio .NET 2013  
 aperçus des technologies de la plateforme des compilateurs .NET \(« Roslyn »\)  
  
 Visual Basic \/ Visual Studio .NET 2015  
 Version actuelle, voir ci\-dessous  
  
## Version actuelle  
 [Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Vous pouvez obtenir le nom de chaîne non qualifié d’un type ou membre et l’utiliser dans un message d’erreur sans effectuer de codage irréversible de chaîne.  Votre code reste alors correct lors de la refactorisation.  Cette fonctionnalité est également utile pour placer des liens MVC modèle\-vue\-contrôleur et activer des événements de modification de propriété.  
  
 [Interpolation de chaîne](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Vous pouvez utiliser des expressions d’interpolation de chaîne pour construire des chaînes.  Une expression de chaîne interpolée s’apparente à une chaîne de modèle contenant des expressions.  C\# crée une chaîne en remplaçant les expressions par les représentations ToString des résultats des expressions.  Les arguments d’une chaîne interpolée sont plus compréhensibles que dans une [Mise en forme composite](../Topic/Composite%20Formatting.md).  
  
 [Accès aux membres et indexation Null\-condition](../../csharp/language-reference/operators/null-conditional-operators.md)  
 Vous pouvez rechercher les valeurs Null à l’aide d’une syntaxe très légère avant d’effectuer une opération d’accès aux membres \(`?.`\) ou d’indexation \(`?[]`\).  Ces opérateurs permettent d’écrire moins de code pour gérer les vérifications Null, notamment pour l’exploration des structures de données.  Si la référence objet ou l’opérande gauche est Null, l’opération renvoie la valeur Null.  
  
 [Littéraux de chaîne multiligne](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Les littéraux de chaîne peuvent contenir des séquences de saut de ligne.  Il n’est plus nécessaire de passer par la méthode `<xml><![CDATA[...text with newlines...]]></xml>.Value`.  
  
 Commentaires  
 Vous pouvez placer des commentaires après les continuations de ligne implicite, dans les expressions d’initialiseur et dans les termes d’expression LINQ.  
  
 Résolution de nom qualifié complet plus intelligente  
 En présence de code tel que `Threading.Thread.Sleep(1000)`, Visual Basic recherchait l’espace de noms « Threading », détectait l’ambiguïté entre System.Threading et System.Windows.Threading, et signalait une erreur.  Visual Basic prend désormais en compte les deux espaces de noms possibles.  Lorsque vous affichez la liste de saisie semi\-automatique, les membres de ces deux types y sont recensés par l’éditeur Visual Studio.  
  
 Littéraux de date avec année en premier  
 Vous pouvez avoir des littéraux de date au format aaaa\-mm\-jj, `#2015-03-17 16:10 PM#`.  
  
 Propriétés d’interface en lecture seule  
 Vous pouvez implémenter des propriétés d’interface en lecture seule à l’aide d’une propriété readwrite.  L’interface garantit les fonctionnalités minimales et n’empêche pas une classe d’implémentation d’autoriser la définition de la propriété.  
  
 [TypeOf \<expr\> IsNot \<type\>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Pour une meilleure lisibilité du code, vous pouvez maintenant utiliser `TypeOf` avec `IsNot`.  
  
 [\#Disable Warning \<ID\> et \#Enable Warning \<ID\>](../../visual-basic/language-reference/directives/directives.md)  
 Vous pouvez désactiver et activer des avertissements spécifiques pour les zones d’un fichier source.  
  
 Améliorations de la fonctionnalité de commentaires de document XML  
 Lorsque vous écrivez des commentaires de document, vous bénéficiez d’un éditeur intelligent et de la prise en charge de version pour la validation des noms de paramètres, le gestion appropriée des `crefs` \(génériques, opérateurs, etc.\), la colorisation et la refactorisation.  
  
 [Module et définitions d’interface partiels](../../visual-basic/language-reference/modifiers/partial.md)  
 En plus des classes et structures, vous pouvez déclarer des interfaces et des modules partiels.  
  
 [Instructions \#Region dans le corps de la méthode](../../visual-basic/language-reference/directives/region-directive.md)  
 Vous pouvez placer des délimiteurs \#Region…\#End Region n’importe où dans un fichier, dans des fonctions, ou encore répartis à différents endroits du corps d’une fonction.  
  
 [Les définitions de substitutions sont implicitement des surcharges](../../visual-basic/language-reference/modifiers/overrides.md)  
 Si vous ajoutez le modificateur `Overrides` à une définition, le compilateur ajoute `Overloads` de manière implicite, de sorte que vous pouvez taper moins de code dans les situations courantes.  
  
 CObj autorisé dans les arguments d’attributs  
 Le compilateur signalait l’erreur indiquant que CObj\(...\) n’est pas une constante lorsqu’il est utilisé dans les constructions d’attribut.  
  
 Déclaration et utilisation de méthodes ambiguës issues d’interfaces différentes  
 Auparavant, le code suivant générait des erreurs qui vous empêchaient de déclarer `IMock` ou d’appeler `GetDetails` \(s’ils avaient été déclarés en C\#\) :  
  
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
  
## Voir aussi  
 [Nouveautés de Visual Studio 2015](/visual-studio/ide/what-s-new-in-visual-studio-2015)