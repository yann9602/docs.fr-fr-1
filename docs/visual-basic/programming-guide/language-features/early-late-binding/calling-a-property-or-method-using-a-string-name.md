---
title: "Calling a Property or Method Using a String Name (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "passing operators"
  - "strings [Visual Basic], passing new operators as"
  - "objects [Visual Basic], setting properties"
  - "setting properties, object properties at run time"
  - "method calls, strings"
  - "methods [Visual Basic], calling with string names"
  - "calling methods, string names"
  - "properties [Visual Basic], setting at run time"
  - "CallByName function"
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Calling a Property or Method Using a String Name (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Dans la plupart des cas, vous pouvez découvrir les propriétés et méthodes d'un objet au moment du design et écrire du code pour les gérer.  Dans quelques cas, cependant, vous ne connaîtrez peut\-être pas les propriétés et méthodes d'un objet à l'avance ou vous voudrez tout simplement offrir à l'utilisateur la possibilité de spécifier les propriétés et d'exécuter les méthodes au moment de l'exécution.  
  
## CallByName, fonction  
 Prenons l'exemple d'une application cliente qui évalue des expressions entrées par l'utilisateur en passant un opérateur au composant COM.  Supposons que vous voulez constamment ajouter de nouvelles fonctions au composant requérant de nouveaux opérateurs.  Lorsque vous utilisez les techniques d'accès standard, vous devez recompiler et redistribuer l'application cliente avant qu'elle ne puisse utiliser les nouveaux opérateurs.  Pour éviter ce problème, vous pouvez appeler la fonction `CallByName` pour passer les nouveaux opérateurs en tant que chaînes sans modifier l'application.  
  
 La fonction `CallByName` vous permet d'utiliser une chaîne pour spécifier une propriété ou une méthode au moment de l'exécution.  La signature de la fonction `CallByName` ressemble à ceci :  
  
 *Résultat* \= `CallByName`\(*Objet*, *NomProcédure*, *TypeAppel*, *Arguments*\(\)\)  
  
 Le premier argument, *Objet*, prend le nom de l'objet sur lequel vous voulez agir.  L'argument *NomProcédure* accepte une chaîne contenant le nom de la procédure de méthode ou de propriété à appeler.  L'argument *TypeAppel* accepte une constante représentant le type de procédure à appeler : une méthode \(`Microsoft.VisualBasic.CallType.Method`\), une lecture de propriété \(`Microsoft.VisualBasic.CallType.Get`\) ou une définition de propriété \(`Microsoft.VisualBasic.CallType.Set`\).  L'argument *Arguments*, facultatif, accepte un tableau de type `Object` contenant n'importe quel argument de la procédure.  
  
 Vous pouvez utiliser la fonction `CallByName` avec des classes de votre solution en cours, mais elle est plus souvent employée pour accéder à des objets COM ou des objets d'assemblys [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)].  
  
 Supposons que vous ajoutez une référence à un assembly contenant une classe appelée `MathClass` dotée d'une nouvelle fonction appelée `SquareRoot`, comme illustré dans le code suivant :  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#53)]  
  
 Votre application peut utiliser des contrôles de zone de texte pour contrôler la méthode et les arguments qui seront appelés.  Par exemple, si `TextBox1` contient l'expression à évaluer et si `TextBox2` est utilisé pour entrer le nom de la fonction, vous pouvez utiliser le code suivant pour appeler la fonction `SquareRoot` pour l'expression contenue dans `TextBox1` :  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/visualbasic/VbVbalrOOP/OOP.vb#54)]  
  
 Si vous entrez "64" dans `TextBox1`, "SquareRoot" dans `TextBox2` et que vous appelez ensuite la procédure `CallMath`, la racine carrée du nombre contenu dans `TextBox1` est évaluée.  Le code de cet exemple appelle la fonction `SquareRoot` \(qui accepte une chaîne qui contient l'expression à évaluer comme un argument obligatoire\) et retourne « 8 » dans `TextBox1` \(la racine carrée de 64\).  Évidemment, si l'utilisateur entre une chaîne non valide dans `TextBox2`, si la chaîne contient le nom d'une propriété et non celui d'une méthode ou si la méthode possède un argument obligatoire supplémentaire, il se produit une erreur d'exécution.  Vous devez ajouter un code robuste de gestion des erreurs lorsque vous utilisez la fonction `CallByName` afin d'anticiper les erreurs de ce type.  
  
> [!NOTE]
>  `CallByName` peut être utile dans certains cas, mais pesez bien ses avantages par rapport à ses inconvénients en matière de performances — l'appel d'une procédure à l'aide de la fonction `CallByName` est un peu plus lent qu'un appel à liaison tardive.  Si la fonction est appelée de façon répétitive, comme dans une boucle, `CallByName` peut avoir un impact négatif sur les performances.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)