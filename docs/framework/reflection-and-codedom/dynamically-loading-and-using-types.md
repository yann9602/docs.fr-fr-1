---
title: "Chargement et utilisation dynamiques des types | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "charger et utiliser des types de manière dynamique"
  - "liaison anticipée"
  - "liaison tardive implicite"
  - "liaison tardive, à propos de la liaison tardive"
  - "réflexion, utiliser des types de manière dynamique"
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Chargement et utilisation dynamiques des types
La réflexion fournit l'infrastructure utilisée par les compilateurs de langages tels que [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] et JScript pour implémenter la liaison tardive implicite.  La liaison est le processus de localisation de la déclaration \(en d'autres termes, l'implémentation\) qui correspond à un type spécifié unique.  Lorsque ce processus se produit au moment de l'exécution plutôt qu'au moment de la compilation, il est appelé liaison tardive.  [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] vous permet d'utiliser la liaison tardive implicite dans votre code ; le compilateur Visual Basic appelle une méthode d'assistance qui utilise la réflexion pour obtenir le type d'objet.  Les arguments passés à la méthode d'assistance entraînent l'appel de la méthode appropriée au moment de l'exécution.  Ces arguments sont l'instance \(un objet\) sur laquelle appeler la méthode, le nom de la méthode appelée \(une chaîne\) et les arguments passés à la méthode appelée \(un tableau d'objets\).  
  
 Dans l'exemple suivant, le compilateur Visual Basic utilise implicitement la réflexion pour appeler une méthode sur un objet dont le type n'est pas connu au moment de la compilation.  Une classe **HelloWorld** possède une méthode **PrintHello** qui imprime "Hello World" concaténé à du texte passé à la méthode **PrintHello**.  La méthode **PrintHello** appelée dans cet exemple équivaut en fait à un <xref:System.Type.InvokeMember%2A?displayProperty=fullName> ; le code Visual Basic permet à la méthode **PrintHello** d'être appelée comme si le type de l'objet \(helloObj\) était connu au moment de la compilation \(liaison anticipée\) au lieu de l'être au moment de l'exécution \(liaison tardive\).  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## Liaison personnalisée  
 Outre son utilisation implicite par les compilateurs, la réflexion peut également être utilisée explicitement dans le code pour exécuter la liaison tardive.  
  
 Le [Common Language Runtime](../../../docs/standard/clr.md) prend en charge plusieurs langages de programmation dont les règles de liaison diffèrent.  Dans le cadre de la liaison anticipée, les générateurs de code peuvent contrôler complètement cette liaison.  Cependant, dans la liaison tardive par réflexion, celle\-ci doit être contrôlée par une liaison personnalisée.  La classe <xref:System.Reflection.Binder> assure un contrôle personnalisé de la sélection et de l'appel de membres.  
  
 Grâce à la liaison personnalisée, vous pouvez charger un assembly au moment de l'exécution, obtenir des informations sur les types de cet assembly, spécifier le type souhaité, puis appeler les méthodes ou accéder aux champs ou propriétés de ce type.  Cette technique est très utile lorsque vous ne connaissez pas le type d'un objet au moment de la compilation, par exemple lorsque le type de l'objet dépend de l'entrée d'utilisateur.  
  
 L'exemple suivant illustre un binder personnalisé simple qui ne fournit aucune conversion de type d'argument.  Du code pour la création de `Simple_Type.dll` précède l'exemple principal.  Créez `Simple_Type.dll`, puis incluez une référence à ce fichier dans le projet au moment de la génération.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### InvokeMember et CreateInstance  
 Utilisez <xref:System.Type.InvokeMember%2A?displayProperty=fullName> pour appeler le membre d'un type.  Les méthodes **CreateInstance** de diverses classes, par exemple [System.Activator](frlrfSystemActivatorClassCreateInstanceTopic) et [System.Reflection.Assembly](frlrfSystemReflectionAssemblyClassCreateInstanceTopic), sont des formes particulières de **InvokeMember** qui créent des instances du type spécifié.  La classe **Binder** est utilisée pour la résolution de surcharge et la contrainte d'argument dans ces méthodes.  
  
 L'exemple suivant montre les trois combinaisons possibles de contrainte d'argument \(conversion de type\) et de sélection de membre.  Dans le cas n 1, aucune contrainte d'argument ou sélection de membre n'est nécessaire.  Dans le cas n 2, seule la sélection de membre est nécessaire.  Dans le cas n 3, seule la contrainte d'argument est nécessaire.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 La résolution de surcharge est nécessaire lorsque plusieurs membres possédant le même nom sont disponibles.  Les méthodes <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=fullName> et <xref:System.Reflection.Binder.BindToField%2A?displayProperty=fullName> permettent de résoudre la liaison à un seul membre.  **Binder.BindToMethod** permet également la résolution des propriétés via les accesseurs de propriété **get** et **set**.  
  
 **BindToMethod** retourne le <xref:System.Reflection.MethodBase> à appeler ou une référence nulle \(**Nothing** en Visual Basic\) si aucun appel n'est possible.  La valeur de retour de **MethodBase** n'est pas forcément contenue dans le paramètre *match*, même si cela est souvent le cas.  
  
 Lorsque les arguments ByRef sont présents, l'appelant a la possibilité de les retourner.  Par conséquent, **Binder** autorise un client à mapper le tableau des arguments vers sa forme d'origine si **BindToMethod** a manipulé le tableau des arguments.  Pour ce faire, l'appelant doit avoir la garantie que l'ordre des arguments n'a pas été modifié.  Lorsque des arguments sont passés par nom, **Binder** réorganise le tableau d'arguments et c'est ce que voit l'appelant.  Pour plus d'informations, consultez <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=fullName>.  
  
 L'ensemble des membres disponibles correspond aux membres définis dans le type ou n'importe quel type de base.  Si [BindingFlags.NonPublic](frlrfSystemReflectionBindingFlagsClassTopic) est spécifié, les membres d'une accessibilité sont retournés dans l'ensemble.  Si **BindingFlags.NonPublic** n'est pas spécifié, binder doit appliquer les règles d'accessibilité.  Lors de la spécification de l'indicateur de liaison **Public** ou **NonPublic**, vous devez également spécifier l'indicateur de liaison **Instance** ou **Static**, sinon aucun membre n'est retourné.  
  
 S'il n'existe qu'un seul membre avec le nom spécifié, aucun rappel n'est nécessaire, et la liaison s'effectue sur cette méthode.  Le cas n1 de l'exemple de code illustre ce point : une seule méthode **PrintBob** est disponible et par conséquent, aucun rappel n'est nécessaire.  
  
 Si plusieurs membres existent dans l'ensemble disponible, toutes ces méthodes sont passées à **BindToMethod**, qui sélectionne la méthode appropriée et la retourne.  Dans le cas n 2 de l'exemple de code, il existe deux méthodes nommées **PrintValue**.  La méthode appropriée est sélectionnée par l'appel à **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> effectue une contrainte d'argument \(conversion de type\) qui convertit les arguments réels au type des arguments formels de la méthode sélectionnée.  **ChangeType** est appelé pour chaque argument même si les types correspondent exactement.  
  
 Dans le cas n 3 de l'exemple de code, un argument réel de type **String** avec la valeur "5,5" est passé à une méthode avec un argument formel de type **Double**.  Pour que l'appel réussisse, la valeur de chaîne "5,5" doit être convertie en valeur double.  **ChangeType** se charge d'effectuer cette conversion.  
  
 **ChangeType** n'effectue que des [contraintes étendues](../../../docs/standard/base-types/type-conversion.md) ou sans perte, comme l'illustre le tableau suivant.  
  
|Type de source|Type de cible|  
|--------------------|-------------------|  
|Tout type|Son type de base|  
|Tout type|L'interface implémentée|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, Single, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, Single, Double|  
|UInt64|Single, Double|  
|Int64|Single, Double|  
|Single|Double|  
|Type non référence|Type référence|  
  
 La classe <xref:System.Type> dispose de méthodes **Get** qui utilisent des paramètres de type **Binder** pour résoudre les références à un membre particulier.  <xref:System.Type.GetConstructor%2A?displayProperty=fullName>, <xref:System.Type.GetMethod%2A?displayProperty=fullName>et <xref:System.Type.GetProperty%2A?displayProperty=fullName> recherchent un membre particulier du type actuel en fournissant les informations de signature pour ce membre.  <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=fullName> et <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=fullName> sont rappelés pour sélectionner les informations de signature données des méthodes appropriées.  
  
## Voir aussi  
 <xref:System.Type.InvokeMember%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 [Affichage des informations de type](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [Conversion de type dans le .NET Framework](../../../docs/standard/base-types/type-conversion.md)