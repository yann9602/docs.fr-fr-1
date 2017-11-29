---
title: "Références et l'instruction Imports (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="f714f-102">Références et l'instruction Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f714f-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="f714f-103">Vous proposer des objets externes à votre projet en choisissant le **ajouter une référence** commande sur le **projet** menu.</span><span class="sxs-lookup"><span data-stu-id="f714f-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="f714f-104">Références de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] peut pointer vers des assemblys qui sont semblables à des bibliothèques de types, mais contiennent plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f714f-104">References in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="f714f-105">L’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="f714f-105">The Imports Statement</span></span>  
 <span data-ttu-id="f714f-106">Assemblys incluent un ou plusieurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="f714f-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="f714f-107">Lorsque vous ajoutez une référence à un assembly, vous pouvez également ajouter un `Imports` instruction à un module qui contrôle la visibilité des espaces de noms de l’assembly dans le module.</span><span class="sxs-lookup"><span data-stu-id="f714f-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="f714f-108">La `Imports` instruction offre une portée qui vous permet d’utiliser uniquement la partie de l’espace de noms nécessaire pour fournir une référence unique.</span><span class="sxs-lookup"><span data-stu-id="f714f-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="f714f-109">La `Imports` instruction présente la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="f714f-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="f714f-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="f714f-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="f714f-111">`Aliasname`fait référence à un nom court, que vous pouvez utiliser dans du code pour faire référence à un espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="f714f-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="f714f-112">`Namespace`est un espace de noms disponible via une référence de projet, d’une définition dans le projet, ou par une précédente `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="f714f-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="f714f-113">Un module peut contenir un nombre quelconque de `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="f714f-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="f714f-114">Ils doivent apparaître après toutes `Option` instructions, le cas échéant, mais avant tout autre code.</span><span class="sxs-lookup"><span data-stu-id="f714f-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f714f-115">Ne confondez pas les références de projet avec le `Imports` instruction ou la `Declare` instruction.</span><span class="sxs-lookup"><span data-stu-id="f714f-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="f714f-116">Références de projet rendent les objets externes, tels que les objets dans des assemblys, disponibles pour [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projets.</span><span class="sxs-lookup"><span data-stu-id="f714f-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projects.</span></span> <span data-ttu-id="f714f-117">La `Imports` instruction permet de simplifier l’accès aux références du projet, mais ne donne pas accès à ces objets.</span><span class="sxs-lookup"><span data-stu-id="f714f-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="f714f-118">La `Declare` instruction est utilisée pour déclarer une référence à une procédure externe dans une bibliothèque de liens dynamiques (DLL).</span><span class="sxs-lookup"><span data-stu-id="f714f-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="f714f-119">L’utilisation d’alias avec l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="f714f-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="f714f-120">La `Imports` instruction facilite accès aux méthodes des classes en éliminant la nécessité d’entrer de manière explicite les noms complets des références.</span><span class="sxs-lookup"><span data-stu-id="f714f-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="f714f-121">Les alias vous permettent d’attribuer un nom plus convivial à seulement une partie d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f714f-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="f714f-122">Par exemple, la retour chariot/ligne de flux de séquence qui provoque un seul élément de texte à afficher sur plusieurs lignes fait partie de la <xref:Microsoft.VisualBasic.ControlChars> module dans le <xref:Microsoft.VisualBasic?displayProperty=nameWithType> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f714f-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f714f-123">Pour utiliser cette constante dans un programme sans alias, vous devez taper le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f714f-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="f714f-124">`Imports`instructions doivent toujours être immédiatement après les premières lignes `Option` instructions d’un module.</span><span class="sxs-lookup"><span data-stu-id="f714f-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="f714f-125">Le fragment de code suivant montre comment importer et assigner un alias à la <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module :</span><span class="sxs-lookup"><span data-stu-id="f714f-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="f714f-126">Références ultérieures à cet espace de noms peuvent être beaucoup plus courtes :</span><span class="sxs-lookup"><span data-stu-id="f714f-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="f714f-127">Si un `Imports` instruction n’inclut pas un nom d’alias, les éléments définis dans l’espace de noms importé peuvent être utilisés dans le module sans qualification.</span><span class="sxs-lookup"><span data-stu-id="f714f-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="f714f-128">Si le nom d’alias est spécifié, il doit être utilisé en tant que qualificateur pour les noms contenus dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f714f-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f714f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f714f-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [<span data-ttu-id="f714f-130">NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence</span><span class="sxs-lookup"><span data-stu-id="f714f-130">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="f714f-131">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f714f-131">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="f714f-132">Assemblys et le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="f714f-132">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="f714f-133">Guide pratique : créer et utiliser des assemblys à l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="f714f-133">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="f714f-134">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="f714f-134">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
