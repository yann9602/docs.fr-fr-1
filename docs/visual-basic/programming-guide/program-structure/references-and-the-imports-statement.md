---
title: "Références et l’instruction Imports (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 283a27e7703b31a9aeed8f7e4104e89b7ff78525
ms.lasthandoff: 03/13/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a>Références et l'instruction Imports (Visual Basic)
Vous pouvez permettre des objets externes à votre projet en choisissant le **ajouter une référence** commande le **projet** menu. Les références dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peut pointer vers des assemblys qui sont semblables à des bibliothèques de types, mais contiennent plus d’informations.  
  
## <a name="the-imports-statement"></a>L’instruction Imports  
 Assemblys incluent un ou plusieurs espaces de noms. Lorsque vous ajoutez une référence à un assembly, vous pouvez également ajouter un `Imports` instruction à un module qui contrôle la visibilité des espaces de noms de l’assembly dans le module. La `Imports` instruction offre une portée qui vous permet d’utiliser uniquement la partie de l’espace de noms nécessaire pour fournir une référence unique.  
  
 La `Imports` instruction présente la syntaxe suivante :  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`fait référence à un nom court, que vous pouvez utiliser dans le code pour faire référence à un espace de noms importé. `Namespace`est un espace de noms disponible via une référence de projet, d’une définition dans le projet, ou par une précédente `Imports` instruction.  
  
 Un module peut contenir un nombre quelconque de `Imports` instructions. Ils doivent apparaître après toutes `Option` instructions, le cas échéant, mais avant tout autre code.  
  
> [!NOTE]
>  Ne confondez pas les références de projet avec le `Imports` instruction ou la `Declare` instruction. Références de projet rendent les objets externes, tels que les objets dans des assemblys, disponibles pour [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projets. La `Imports` instruction permet de simplifier l’accès aux références de projet, mais ne donne pas accès à ces objets. La `Declare` instruction est utilisée pour déclarer une référence à une procédure externe dans une bibliothèque de liens dynamiques (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>L’utilisation d’alias avec l’instruction Imports  
 La `Imports` instruction facilite accès aux méthodes des classes en éliminant la nécessité d’entrer de manière explicite les noms complets des références. Les alias vous permettent d’attribuer un nom plus convivial à seulement une partie d’un espace de noms. Par exemple, la retour chariot/ligne séquence qui provoque un seul élément de texte à afficher sur plusieurs lignes fait partie de la <xref:Microsoft.VisualBasic.ControlChars>module dans le <xref:Microsoft.VisualBasic?displayProperty=fullName>espace de noms.</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.ControlChars> Pour utiliser cette constante dans un programme sans alias, vous devez taper le code suivant :  
  
 [!code-vb[VbVbalrApplication n °&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`instructions doivent toujours être immédiatement après les premières lignes `Option` instructions d’un module. Le fragment de code suivant montre comment importer et assigner un alias à la <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>module :</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>  
  
 [!code-vb[VbVbalrApplication n °&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Références ultérieures à cet espace de noms peuvent être considérablement plus courts :  
  
 [!code-vb[VbVbalrApplication n °&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Si un `Imports` instruction n’inclut pas de nom d’alias, les éléments définis dans l’espace de noms importé peuvent être utilisés dans le module sans qualification. Si le nom d’alias est spécifié, il doit être utilisé en tant que qualificateur pour les noms contenus dans cet espace de noms.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic>   
 [NIB Guide pratique pour ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
