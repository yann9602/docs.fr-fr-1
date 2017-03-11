---
title: "References and the Imports Statement (Visual Basic) | Microsoft Docs"
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
  - "assemblies [Visual Basic], namespaces"
  - "references, assembly"
  - "namespaces, assemblies"
  - "referencing assemblies"
  - "Imports statement, referencing assemblies"
  - "assemblies [Visual Basic], references"
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# References and the Imports Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez rendre les objets externes disponibles pour votre projet en cliquant sur la commande **Ajouter une référence** dans le menu **Projet**.  Les références en [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] peuvent pointer vers des assemblys qui sont semblables à des bibliothèques de types, mais contiennent davantage d'informations.  
  
## L'instruction Imports  
 Les assemblys incluent un ou plusieurs espaces de noms.  Lorsque vous ajoutez une référence à un assembly, vous pouvez également ajouter une instruction `Imports`à un module pour contrôler la visibilité des espaces de noms de l'assembly dans le module.  L'instruction `Imports` offre une portée qui vous permet d'utiliser uniquement la portion d'espace de noms nécessaire pour fournir une référence unique.  
  
 La syntaxe de l'instruction `Imports` est la suivante :  
  
 `Imports` \[         `|` `Aliasname` \=\] `Namespace`  
  
 `Aliasname` fait référence à un nom court que vous pouvez utiliser dans le code pour faire référence à un espace de noms importé.  `Namespace` est un espace de noms disponible via une référence de projet, une définition présente dans le projet ou une instruction `Imports` précédente.  
  
 Un module peut contenir autant d'instructions `Imports` que vous le souhaitez.  Celles\-ci doivent apparaître après toutes les instructions `Option`, le cas échéant, mais avant tout autre code.  
  
> [!NOTE]
>  Ne confondez pas les références de projet avec les instructions `Imports` ou `Declare`.  Les références de projet rendent les objets externes, tels que les objets des assemblys, disponibles pour les projets [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  L'utilisation de l'instruction `Imports` permet de simplifier l'accès aux références de projet, mais ne constitue pas un accès à ces objets.  L'instruction `Declare` permet de déclarer une référence à une procédure externe dans une bibliothèque de liens dynamiques \(DLL\).  
  
## Utilisation des alias avec l'instruction Imports  
 L'instruction `Imports` facilite l'accès aux méthodes des classes en éliminant le besoin d'entrer de manière explicite les noms complets des références.  Les alias vous permettent d'assigner un nom plus convivial à seulement une partie d'un espace de noms.  Par exemple, la séquence du retour chariot ou du changement de ligne qui entraîne l'affichage d'un bloc de texte sur plusieurs lignes fait partie du module <xref:Microsoft.VisualBasic.ControlChars> de l'espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>.  Pour utiliser cette constante dans un programme sans recourir à un alias, vous devez entrer le code suivant :  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/references-and-the-impor_1.vb)]  
  
 Les instructions `Imports` doivent toujours représenter les premières lignes situées immédiatement après les instructions `Option` d'un module.  Le fragment de code suivant montre comment importer et assigner un alias au module <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/references-and-the-impor_2.vb)]  
  
 Les références ultérieures à cet espace de noms peuvent être considérablement plus courtes :  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/references-and-the-impor_3.vb)]  
  
 Si une instruction `Imports` n'inclut pas de nom d'alias, les éléments définis dans l'espace de noms importé peuvent être utilisés dans le module sans nécessiter de qualification.  Si le nom d'alias est spécifié, il doit être utilisé comme qualificateur pour les noms contenus dans l'espace de noms.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic>   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)