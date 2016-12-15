---
title: "Cha&#238;nes (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, chaînes"
  - "chaînes (C#)"
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
caps.handback.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Cha&#238;nes (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une chaîne est un objet de type <xref:System.String> dont la valeur est du texte.  En interne, le texte est stocké comme une collection en lecture seule séquentielle d'objets <xref:System.Char>.  Il n'y a aucun caractère Null de fin à la fin d'une chaîne C\# ; par conséquent, une chaîne C\# peut contenir n'importe quel nombre de caractères Null incorporés \('\\0'\).  La propriété <xref:System.String.Length%2A> d'une chaîne représente le nombre d'objets `Char` qu'elle contient, et pas le nombre de caractères Unicode.  Pour accéder aux divers points de code Unicode d'une chaîne, utilisez l'objet <xref:System.Globalization.StringInfo>.  
  
## string etSystem.String  
 En C\#, le mot clé `string` est un alias de <xref:System.String>.  Par conséquent, `String` et `string` sont équivalents et vous pouvez utiliser la convention d'affectation de noms que vous préférez.  La classe `String` propose diverses méthodes pour créer, manipuler et comparer des chaînes en toute sécurité.  De plus, le langage C\# surcharge des opérateurs pour simplifier les opérations de chaînes courantes.  Pour plus d'informations sur le mot clé, consultez [chaîne](../../../csharp/language-reference/keywords/string.md).  Pour plus d'informations sur le type et ses méthodes, consultez <xref:System.String>.  
  
## Déclaration et initialisation de chaînes  
 Vous pouvez déclarer et initialiser des chaînes de différentes façons, comme l'illustre l'exemple suivant :  
  
 [!code-cs[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Notez que vous n'utilisez pas l'opérateur [new](../../../csharp/language-reference/keywords/new-operator.md) pour créer un objet String sauf au moment d'initialiser la chaîne au moyen d'un tableau de caractères.  
  
 Initialisez une chaîne avec la valeur de constante <xref:System.String.Empty> pour créer un objet <xref:System.String> dont la chaîne est de longueur zéro.  La représentation sous forme de littéral de chaîne d'une chaîne de longueur zéro est "".  En initialisant les chaînes avec la valeur <xref:System.String.Empty> au lieu de la valeur [null](../../../csharp/language-reference/keywords/null.md), vous pouvez réduire les risques de survenue d'une <xref:System.NullReferenceException>.  Utilisez la méthode <xref:System.String.IsNullOrEmpty%28System.String%29> statique pour vérifier la valeur d'une chaîne avant d'essayer d'y accéder.  
  
## Immuabilité des objets chaîne  
 Les objets chaîne sont *immuables* dans le sens où ils ne peuvent pas être modifiés une fois qu'ils ont été créés.  Tous les opérateurs C\# et méthodes <xref:System.String> qui semblent modifier une chaîne retournent en fait les résultats dans un nouvel objet chaîne.  Dans l'exemple suivant, lorsque le contenu de `s1` et celui de `s2` sont concaténés pour former une chaîne unique, les deux chaînes d'origine ne sont pas modifiées.  L'opérateur `+=` crée une nouvelle chaîne qui contient le contenu combiné.  Ce nouvel objet est assigné à la variable `s1` et l'objet d'origine qui a été assigné à `s1` est libéré pour le garbage collection parce qu'aucune autre variable n'y fait référence.  
  
 [!code-cs[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Parce qu'une « modification » de chaîne est en fait une création de chaîne, vous devez être prudent lorsque vous créez des références aux chaînes.  Si vous créez une référence à une chaîne, puis « modifiez » la chaîne d'origine, la référence continue à pointer sur l'objet d'origine, et non sur le nouvel objet créé lorsque la chaîne a été modifiée.  Le code suivant illustre ce comportement :  
  
 [!code-cs[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Pour plus d'informations sur la création de nouvelles chaînes basées sur des modifications telles que les opérations de recherche et de remplacement sur la chaîne d'origine, consultez [Comment : modifier du contenu de chaîne](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md).  
  
## Littéraux de chaîne ordinaires et textuels  
 Utilisez les littéraux de chaîne ordinaires lorsque vous devez incorporer des caractères d'échappement fournis par C\#, comme l'illustre l'exemple suivant :  
  
 [!code-cs[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Utilisez les chaînes textuelles pour des raisons de commodité et pour une meilleure lisibilité lorsque le texte de la chaîne contient des barres obliques inverses, par exemple dans les chemins d'accès des fichiers.  Parce que les chaînes textuelles conservent les caractères de retour à la ligne dans le texte de la chaîne, elles peuvent être utilisées pour initialiser des chaînes multilignes.  Utilisez des guillemets anglais doubles pour insérer des guillemets anglais dans une chaîne textuelle.  L'exemple suivant présente des utilisations courantes des chaînes textuelles :  
  
 [!code-cs[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## Séquences d'échappement de chaîne  
  
|Séquence d'échappement|Nom du caractère|Encodage Unicode|  
|----------------------------|----------------------|----------------------|  
|\\'|Guillemet simple|0x0027|  
|\\"|Guillemet double|0x0022|  
|\\\\|Barre oblique inverse|0x005C|  
|\\0|Null|0x0000|  
|\\a|Alerte|0x0007|  
|\\b|Retour arrière|0x0008|  
|\\f|Saut de page|0x000C|  
|\\n|une nouvelle ligne|0x000A|  
|\\r|Retour chariot|0x000D|  
|\\t|Tabulation horizontale|0x0009|  
|\\U|Séquence d'échappement Unicode pour les paires de substitution|\\Unnnnnnnn|  
|\\u|Séquence d'échappement Unicode|\\u0041 \= "A"|  
|\\v|Tabulation verticale|0x000B|  
|\\x|Séquence d'échappement Unicode semblable à « \\u », sauf au niveau de la longueur variable|\\x0041 \= "A"|  
  
> [!NOTE]
>  Lors de la compilation, les chaînes textuelles sont converties en chaînes ordinaires comportant les mêmes séquences d'échappement.  Par conséquent, si vous consultez une chaîne textuelle dans la fenêtre Espion du débogueur, vous voyez les caractères d'échappement ajoutés par le compilateur, pas la version textuelle de votre code source.  Par exemple, la chaîne textuelle @"C:\\files.txt" apparaît dans la fenêtre Espion sous la forme "C:\\\\files.txt".  
  
## Chaînes de format  
 Une chaîne de format est une chaîne dont le contenu peut être déterminé dynamiquement pendant l'exécution.  Vous créez une chaîne de format en utilisant la méthode <xref:System.String.Format%2A> statique et en insérant entre accolades des espaces réservés qui seront remplacés pendant l'exécution par d'autres valeurs.  L'exemple suivant utilise une chaîne de format pour sortir le résultat de chaque itération d'une boucle :  
  
 [!code-cs[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Une surcharge de la méthode <xref:System.Console.WriteLine%2A> accepte une chaîne de format en tant que paramètre.  Par conséquent, vous pouvez simplement incorporer un littéral de chaîne de format sans utiliser d'appel explicite à la méthode.  Toutefois, si vous utilisez la méthode <xref:System.Diagnostics.Trace.WriteLine%2A> pour afficher la sortie de débogage dans la fenêtre **Sortie** de Visual Studio, vous devez appeler la méthode <xref:System.String.Format%2A> explicitement parce que <xref:System.Diagnostics.Trace.WriteLine%2A> accepte seulement une chaîne, pas une chaîne de format.  Pour plus d'informations sur les chaînes de format, consultez [Mise en forme des types](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  
  
## Sous\-chaînes  
 Une sous\-chaîne est une séquence de caractères contenue dans une chaîne.  Utilisez la méthode <xref:System.String.Substring%2A> pour créer une nouvelle chaîne à partir d'une partie de la chaîne d'origine.  Vous pouvez rechercher une ou plusieurs occurrences d'une sous\-chaîne en utilisant la méthode <xref:System.String.IndexOf%2A>.  Utilisez la méthode <xref:System.String.Replace%2A> pour remplacer toutes les occurrences d'une sous\-chaîne spécifiée par une nouvelle chaîne.  Comme la méthode <xref:System.String.Substring%2A>, <xref:System.String.Replace%2A> retourne en fait une nouvelle chaîne et ne modifie pas la chaîne d'origine.  Pour plus d'informations, consultez [Comment : rechercher des chaînes à l'aide de méthodes String](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md) et [Comment : modifier du contenu de chaîne](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md).  
  
 [!code-cs[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## Accès à des caractères  
 Vous pouvez utiliser la notation de tableau avec une valeur d'index pour accéder en lecture seule aux différents caractères, comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Si les méthodes <xref:System.String> ne fournissent pas les fonctionnalités dont vous avez besoin pour modifier les différents caractères d'une chaîne, vous pouvez utiliser un objet <xref:System.Text.StringBuilder> pour modifier les différents caractères « sur place », puis créer une chaîne pour stocker les résultats en utilisant les méthodes <xref:System.Text.StringBuilder>.  Dans l'exemple suivant, supposons que vous devez modifier la chaîne d'origine d'une façon particulière, puis stocker les résultats pour une utilisation ultérieure :  
  
 [!code-cs[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## Chaînes null et chaînes vides  
 Une chaîne vide est l'instance d'un objet <xref:System.String?displayProperty=fullName> qui contient des caractères nuls \(0\).  Les chaînes vides sont souvent utilisées dans divers scénarios de programmation pour représenter un champ de texte vierge.  Vous pouvez appeler les méthodes sur des chaînes vides, car il s'agit d'objets <xref:System.String?displayProperty=fullName> valides.  Les chaînes vides sont initialisées comme suit :  
  
```  
string s = String.Empty;  
```  
  
 Par contraste, une chaîne vide ne fait pas référence à l'instance d'un objet <xref:System.String?displayProperty=fullName> et toute tentative d'appeler une méthode sur une chaîne vide provoque une <xref:System.NullReferenceException>.  Toutefois, vous pouvez utiliser les chaînes null dans les opérations de concaténation et de comparaison avec d'autres chaînes.  Les exemples suivants illustrent certains cas dans lesquels la référence à une chaîne vide provoque ou non la levée d'une exception :  
  
 [!code-cs[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## Utilisation de StringBuilder pour créer rapidement une chaîne  
 Les opérations de chaînes dans .NET sont hautement optimisées. Dans la plupart des cas, elles n'altèrent pas beaucoup les performances.  Toutefois, les opérations de chaînes peuvent affecter les performances dans quelques cas tels que les boucles serrées exécutées des centaines ou des milliers de fois.  La classe <xref:System.Text.StringBuilder> crée une mémoire tampon de chaîne qui offre de meilleures performances si votre programme exécute un grand nombre de traitements de chaînes.  La chaîne <xref:System.Text.StringBuilder> vous permet également de réassigner des caractères, option que le type de données String intégré ne prend pas en charge.  Par exemple, ce code modifie le contenu d'une chaîne sans créer une nouvelle chaîne :  
  
 [!code-cs[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 Dans cet exemple, un objet <xref:System.Text.StringBuilder> est utilisé pour créer une chaîne à partir d'un jeu de types numériques :  
  
 [!code-cs[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## Chaînes, méthodes d'extension et LINQ  
 Étant donné que le type <xref:System.String> implémente <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez appliquer les méthodes d'extension définies dans la classe <xref:System.Linq.Enumerable> aux chaînes.  Pour des raisons de lisibilité, ces méthodes sont exclues d'IntelliSense pour le type <xref:System.String>. Elles sont toutefois disponibles.  Vous pouvez également appliquer les expressions de requête [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] aux chaînes.  Pour plus d'informations, consultez [LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md).  
  
## Rubriques connexes  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Comment : modifier du contenu de chaîne](../../../csharp/programming-guide/strings/how-to-modify-string-contents.md)|Fournit un exemple de code qui montre comment modifier le contenu de chaînes.|  
|[Comment : concaténer plusieurs chaînes](../../../csharp/programming-guide/strings/how-to-concatenate-multiple-strings.md)|Montre comment utiliser l'opérateur `+` et la classe `Stringbuilder` pour joindre des chaînes au moment de la compilation et de l'exécution.|  
|[Comment : comparer des chaînes](../../../csharp/programming-guide/strings/how-to-compare-strings.md)|Indique comment effectuer des comparaisons ordinales de chaînes.|  
|[Comment : analyser des chaînes à l’aide de String.Split ](../../../csharp/programming-guide/strings/how-to-parse-strings-using-string-split.md)|Contient un exemple de code qui montre comment utiliser la méthode `String.Split` pour analyser des chaînes.|  
|[Comment : rechercher des chaînes à l'aide de méthodes String](../../../csharp/programming-guide/strings/how-to-search-strings-using-string-methods.md)|Explique comment utiliser des méthodes spécifiques pour rechercher des chaînes.|  
|[Comment : rechercher des chaînes à l'aide d'expressions régulières](../../../csharp/programming-guide/strings/how-to-search-strings-using-regular-expressions.md)|Explique comment utiliser des expressions régulières pour rechercher des chaînes.|  
|[Comment : déterminer si une chaîne représente une valeur numérique](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Indique comment analyser sans risque une chaîne pour voir si elle a une valeur numérique valide.|  
|[Comment : convertir une chaîne en DateTime](../../../csharp/programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)|Indique comment convertir une chaîne telle que « 24\/01\/2008 » en objet <xref:System.DateTime?displayProperty=fullName>.|  
|[Opérations de chaînes de base](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)|Fournit des liens vers les rubriques qui utilisent les méthodes <xref:System.String?displayProperty=fullName> et <xref:System.Text.StringBuilder?displayProperty=fullName> pour exécuter des opérations de chaîne de base.|  
|[Analyse de chaînes](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md)|Décrit comment insérer des caractères ou des espaces vides dans une chaîne.|  
|[Comparaison de chaînes](../Topic/Comparing%20Strings%20in%20the%20.NET%20Framework.md)|Inclut des informations à propos de la comparaison de chaînes et fournit des exemples en C\# et Visual Basic.|  
|[Utilisation de la classe StringBuilder](../Topic/Using%20the%20StringBuilder%20Class%20in%20the%20.NET%20Framework.md)|Montre comment créer et modifier des objets String dynamiques à l'aide de la classe <xref:System.Text.StringBuilder>.|  
|[LINQ and Strings](../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)|Fournit des informations à propos de la façon d'effectuer différentes opérations sur une chaîne en utilisant des requêtes LINQ.|  
|[Guide de programmation C\#](../../../csharp/programming-guide/index.md)|Fournit des liens vers les rubriques qui proposent des explications sur les constructions de programmation en C\#.|  
  
## Chapitre proposé  
 [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) dans [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)