---
title: "Utilisation du CodeDOM | Microsoft Docs"
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
  - "compilateurs de code"
  - "modèle CodeDOM (Code Document Object Model)"
  - "modèle CodeDOM (Code Document Object Model), graphiques"
  - "générateurs de code"
  - "CodeDOM"
  - "CodeDOM, graphiques"
  - "compilation dynamique"
  - "représenter du code source dynamiquement"
  - "graphique CodeDOM"
  - "espaces de noms (.NET Framework), CodeDOM"
  - "modèles de code source"
  - "génération de code basé sur un modèle"
  - "types, CodeDOM"
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Utilisation du CodeDOM
Le CodeDOM fournit des types qui représentent beaucoup de types courants d'éléments du code source.  Vous pouvez concevoir un programme qui génère un modèle de code source à l'aide d'éléments CodeDOM pour assembler un graphique d'objets.  Ce graphique d'objets peut être rendu sous forme de code source à l'aide d'un générateur de code CodeDOM pour un langage de programmation pris en charge.  Le CodeDOM permet également de compiler du code source dans un assembly binaire.  
  
 Les usages courants du CodeDOM sont les suivants :  
  
-   Génération d'un code modèle : génération du code pour ASP.NET, les proxies clients de services Web XML, les Assistants Code, les concepteurs ou d'autres mécanismes d'émission de code.  
  
-   Compilation dynamique : prise en charge de la compilation du code dans un ou plusieurs langages.  
  
## Génération d'un graphique CodeDOM  
 L'espace de noms <xref:System.CodeDom> fournit des classes représentant la structure logique du code source, indépendamment de la syntaxe d'un langage.  
  
### Structure d'un graphique CodeDOM  
 La structure d'un graphique CodeDOM est comparable à une arborescence de conteneurs.  Le conteneur de niveau supérieur, ou conteneur racine, de chaque graphique CodeDOM compilable est un <xref:System.CodeDom.CodeCompileUnit>.  Chaque élément de votre modèle de code source doit être lié au graphique par le biais d'une propriété d'un <xref:System.CodeDom.CodeObject> du graphique.  
  
### Génération d'un modèle de code source pour un exemple de programme Hello World  
 L'exemple ci\-dessous montre comment générer un graphique d'objets CodeDOM représentant le code d'une application exemple Hello world.  Pour obtenir le code source complet pour cet exemple, consultez la rubrique <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName>.  
  
#### Création d'une unité de compilation  
 Le CodeDOM définit un objet appelé <xref:System.CodeDom.CodeCompileUnit> qui peut référencer un graphique d'objets CodeDOM modélisant le code source à compiler.  **CodeCompileUnit** possède des propriétés pour le stockage des références aux attributs, espaces de noms et assemblys.  
  
 Les fournisseurs CodeDOM qui dérivent de la classe <xref:System.CodeDom.Compiler.CodeDomProvider> contiennent des méthodes qui traitent le graphique d'objets référencé par **CodeCompileUnit**.  
  
 Pour créer un graphique d'objets pour une application simple, vous devez assembler le modèle de code source et le référencer à partir de **CodeCompileUnit**.  
  
 Vous pouvez créer une nouvelle unité de compilation avec la syntaxe illustrée dans l'exemple suivant :  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <xref:System.CodeDom.CodeSnippetCompileUnit> peut contenir une section de code source qui figure déjà dans le langage cible mais ne peut pas être rendue dans un autre langage.  
  
#### Définition d'un espace de noms  
 Pour définir un espace de noms, créez un nouveau <xref:System.CodeDom.CodeNamespace> et assignez\-lui un nom à l'aide du constructeur approprié ou en définissant sa propriété **Name**.  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### Importation d'un espace de noms  
 Pour ajouter une directive d'importation d'espace de noms à l'espace de noms, ajoutez <xref:System.CodeDom.CodeNamespaceImport> qui spécifie l'espace de noms à importer dans la collection **CodeNamespace.Imports**.  
  
 Le code suivant ajoute une importation de l'espace de noms **System** à la collection **Imports** d'un **CodeNamespace** appelé `samples` :  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### Liaison d'éléments de code à l'intérieur du graphique d'objets  
 Tous les éléments de code qui forment un graphique CodeDOM doivent être liés au <xref:System.CodeDom.CodeCompileUnit> qui constitue l'élément racine de l'arborescence par une série de références entre des éléments directement référencés à partir des propriétés de l'objet racine du graphique.  Assignez un objet à une propriété d'un objet conteneur pour établir une référence à partir de cet objet.  
  
 L'instruction suivante ajoute **CodeNamespace** `samples` à la propriété de collection **Namespaces** du **CodeCompileUnit** racine.  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### Définition d'un type  
 Pour déclarer une classe, une structure, une interface ou une énumération à l'aide du CodeDOM, créez un nouveau <xref:System.CodeDom.CodeTypeDeclaration> et assignez\-lui un nom.  L'exemple suivant illustre cette opération à l'aide d'une surcharge de constructeur définissant la propriété **Name** :  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 Pour ajouter un type à un espace de noms, ajoutez un <xref:System.CodeDom.CodeTypeDeclaration> représentant ce type à la collection **Types** de **CodeNamespace**.  
  
 L'exemple suivant montre comment ajouter une classe nommée `class1` à un **CodeNamespace** nommé `samples` :  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### Ajout de membres de classe à une classe  
 L'espace de noms <xref:System.CodeDom> fournit divers éléments qui permettent de représenter des membres de classe.  Chaque membre de classe peut être ajouté à la collection **Members** de <xref:System.CodeDom.CodeTypeDeclaration>.  
  
#### Définition d'une méthode de point d'entrée de code pour un exécutable  
 Si vous créez le code d'un programme exécutable, il est nécessaire d'indiquer le point d'entrée du programme en créant un nouveau <xref:System.CodeDom.CodeEntryPointMethod> qui représente la méthode à laquelle doit commencer l'exécution du programme.  
  
 L'exemple suivant montre comment définir une méthode de point d'entrée qui contient un <xref:System.CodeDom.CodeMethodInvokeExpression> qui appelle **System.Console.WriteLine** pour imprimer « Hello World\! » :  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 L'instruction suivante ajoute la méthode de point d'entrée appelée `Start` à la collection **Members** de `class1` :  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 À présent, l'objet <xref:System.CodeDom.CodeCompileUnit> appelé `compileUnit` contient le graphique CodeDOM d'un simple programme Hello World.  Pour plus d'informations sur la génération et la compilation de code à partir d'un graphique CodeDOM, consultez [Génération du code source et compilation d'un programme à partir d'un graphique CodeDOM](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).  
  
### Complément d'information sur la génération d'un graphique CodeDOM  
 Le CodeDOM prend en charge les nombreux types communs d'éléments de code des langages de programmation prenant en charge le Common Language Runtime.  Le CodeDOM n'a pas été conçu pour fournir des éléments pour représenter toutes les fonctionnalités de langage de programmation possibles.  Le code qui ne peut pas être facilement représenté à l'aide d'éléments CodeDOM peut être encapsulé dans <xref:System.CodeDom.CodeSnippetExpression>, <xref:System.CodeDom.CodeSnippetStatement>, <xref:System.CodeDom.CodeSnippetTypeMember>ou <xref:System.CodeDom.CodeSnippetCompileUnit>.  Toutefois, certains extraits de code ne peuvent pas être traduits automatiquement dans d'autres langages par le CodeDOM.  
  
 Pour plus d'informations sur chacun des types CodeDOM, consultez la documentation de référence sur l'espace de noms <xref:System.CodeDom>.  
  
 Pour obtenir un graphique permettant de retrouver rapidement l'élément CodeDOM à utiliser pour représenter un type d'élément de code particulier, consultez [CodeDOM Quick Reference](http://msdn.microsoft.com/fr-fr/c77b8bfd-0a32-4e36-b59a-4f687f32c524).