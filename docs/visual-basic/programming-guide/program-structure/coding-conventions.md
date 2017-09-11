---
title: Conventions de codage Visual Basic | Documents Microsoft
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
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 16d4ddccd3a16c48e58f297faf8909148899013f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="25b72-102">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25b72-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="25b72-103">Microsoft développe des exemples et une documentation qui suivent les instructions de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="25b72-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="25b72-104">Si vous suivez les mêmes conventions de codage, vous pouvez bénéficiez des avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="25b72-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="25b72-105">Votre code aura une apparence cohérente, afin que les lecteurs peuvent mieux se concentrer sur le contenu, pas sur la disposition.</span><span class="sxs-lookup"><span data-stu-id="25b72-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="25b72-106">Lecteurs de comprennent votre code plus rapidement car ils peuvent apporter des hypothèses selon leur expérience précédente.</span><span class="sxs-lookup"><span data-stu-id="25b72-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="25b72-107">Vous pouvez copier, modifier et mettre à jour le code plus facilement.</span><span class="sxs-lookup"><span data-stu-id="25b72-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="25b72-108">Vous assurer que votre code illustre les « meilleures pratiques » pour Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="25b72-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="25b72-109">Conventions d'affectation de noms</span><span class="sxs-lookup"><span data-stu-id="25b72-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="25b72-110">Pour plus d’informations sur les instructions d’affectation de noms, consultez [recommandées](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) rubrique.</span><span class="sxs-lookup"><span data-stu-id="25b72-110">For information about naming guidelines, see [Naming Guidelines](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) topic.</span></span>  
  
-   <span data-ttu-id="25b72-111">N’utilisez pas « Mon » ou « my » en tant que partie d’un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="25b72-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="25b72-112">Cela crée la confusion avec le `My` objets.</span><span class="sxs-lookup"><span data-stu-id="25b72-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="25b72-113">Vous n’avez pas à modifier les noms des objets dans le code généré automatiquement pour les rendre conformes aux indications.</span><span class="sxs-lookup"><span data-stu-id="25b72-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="25b72-114">Conventions de disposition</span><span class="sxs-lookup"><span data-stu-id="25b72-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="25b72-115">Insérer des tabulations en espaces et utiliser la mise en retrait intelligente avec retrait de quatre espaces.</span><span class="sxs-lookup"><span data-stu-id="25b72-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="25b72-116">Utilisez **liste assez (Reformatage) d’un code** pour remettre en forme votre code dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="25b72-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="25b72-117">Pour plus d’informations, consultez [Options, éditeur de texte, Basic (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="25b72-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="25b72-118">Utiliser qu’une seule instruction par ligne.</span><span class="sxs-lookup"><span data-stu-id="25b72-118">Use only one statement per line.</span></span> <span data-ttu-id="25b72-119">N’utilisez pas le caractère de séparation de ligne Visual Basic ( :).</span><span class="sxs-lookup"><span data-stu-id="25b72-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="25b72-120">Évitez d’utiliser le caractère de continuation de ligne explicite « _ » en faveur de la continuation de ligne implicite partout où il permet à la langue.</span><span class="sxs-lookup"><span data-stu-id="25b72-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="25b72-121">Utilisez uniquement une seule déclaration par ligne.</span><span class="sxs-lookup"><span data-stu-id="25b72-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="25b72-122">Si **liste assez (Reformatage) d’un code** ne les lignes de continuation format automatiquement, manuellement mettre en retrait continuation lignes un taquet de tabulation.</span><span class="sxs-lookup"><span data-stu-id="25b72-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="25b72-123">Toutefois, toujours aligner à gauche des éléments dans une liste.</span><span class="sxs-lookup"><span data-stu-id="25b72-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="25b72-124">Ajoutez au moins une ligne vide entre les définitions de méthode et de propriété.</span><span class="sxs-lookup"><span data-stu-id="25b72-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="25b72-125">Conventions de commentaires</span><span class="sxs-lookup"><span data-stu-id="25b72-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="25b72-126">Placer des commentaires sur une ligne distincte et non à la fin d’une ligne de code.</span><span class="sxs-lookup"><span data-stu-id="25b72-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="25b72-127">Démarrer le commentaire par une lettre majuscule et le texte de commentaire fin avec une période.</span><span class="sxs-lookup"><span data-stu-id="25b72-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="25b72-128">Insérez un espace entre le délimiteur de commentaire (') et le texte du commentaire.</span><span class="sxs-lookup"><span data-stu-id="25b72-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     <span data-ttu-id="25b72-129">[!code-vb[VbVbalrGuidelines n °&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-129">[!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-130">N’encadrez pas de commentaires avec des blocs d’astérisques mis en forme.</span><span class="sxs-lookup"><span data-stu-id="25b72-130">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="25b72-131">Structure du programme</span><span class="sxs-lookup"><span data-stu-id="25b72-131">Program Structure</span></span>  
  
-   <span data-ttu-id="25b72-132">Lorsque vous utilisez la `Main` (méthode), utilisez la construction par défaut pour les nouvelles applications de console et `My` pour les arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="25b72-132">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     <span data-ttu-id="25b72-133">[!code-vb[VbVbalrGuidelines n °&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-133">[!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="25b72-134">Directives du langage</span><span class="sxs-lookup"><span data-stu-id="25b72-134">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="25b72-135">String, type de données</span><span class="sxs-lookup"><span data-stu-id="25b72-135">String Data Type</span></span>  
  
-   <span data-ttu-id="25b72-136">Pour concaténer des chaînes, utilisez une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="25b72-136">To concatenate strings, use an ampersand (&).</span></span>  
  
     <span data-ttu-id="25b72-137">[!code-vb[VbVbalrGuidelines n °&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-137">[!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-138">Pour ajouter des chaînes dans des boucles, utilisez le <xref:System.Text.StringBuilder>objet.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="25b72-138">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     <span data-ttu-id="25b72-139">[!code-vb[VbVbalrGuidelines n °&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-139">[!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]</span></span>  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="25b72-140">Délégués souples dans les gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="25b72-140">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="25b72-141">Ne qualifiez pas explicitement les arguments (objet et EventArgs) aux gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="25b72-141">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="25b72-142">Si vous n’utilisez pas les arguments d’événement sont passés à un événement (par exemple, l’expéditeur en tant qu’objet, e comme EventArgs), utilisez les délégués non stricts et laisser de côté les arguments d’événement dans votre code :</span><span class="sxs-lookup"><span data-stu-id="25b72-142">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 <span data-ttu-id="25b72-143">[!code-vb[VbVbalrGuidelines&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-143">[!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]</span></span>  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="25b72-144">Type de données non signé</span><span class="sxs-lookup"><span data-stu-id="25b72-144">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="25b72-145">Utilisez `Integer` plutôt que les types non signés, sauf s’ils sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="25b72-145">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="25b72-146">Tableaux</span><span class="sxs-lookup"><span data-stu-id="25b72-146">Arrays</span></span>  
  
-   <span data-ttu-id="25b72-147">Utilisez la syntaxe courte lorsque vous initialisez des tableaux sur la ligne de déclaration.</span><span class="sxs-lookup"><span data-stu-id="25b72-147">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="25b72-148">Par exemple, utilisez la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="25b72-148">For example, use the following syntax.</span></span>  
  
     <span data-ttu-id="25b72-149">[!code-vb[VbVbalrGuidelines n °&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-149">[!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]</span></span>  
  
     <span data-ttu-id="25b72-150">N’utilisez pas la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="25b72-150">Do not use the following syntax.</span></span>  
  
     <span data-ttu-id="25b72-151">[!code-vb[VbVbalrGuidelines&#9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-151">[!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-152">Placez l’indicateur de tableau sur le type, et non sur la variable.</span><span class="sxs-lookup"><span data-stu-id="25b72-152">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="25b72-153">Par exemple, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="25b72-153">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="25b72-154">[!code-vb[VbVbalrGuidelines&#11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-154">[!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]</span></span>  
  
     <span data-ttu-id="25b72-155">N’utilisez pas la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="25b72-155">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="25b72-156">[!code-vb[VbVbalrGuidelines&#10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-156">[!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-157">Utilisez la syntaxe {} lorsque vous déclarez et initialisez des tableaux de types de base de données.</span><span class="sxs-lookup"><span data-stu-id="25b72-157">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="25b72-158">Par exemple, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="25b72-158">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="25b72-159">[!code-vb[VbVbalrGuidelines&#12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-159">[!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]</span></span>  
  
     <span data-ttu-id="25b72-160">N’utilisez pas la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="25b72-160">Do not use the following syntax:</span></span>  
  
     <span data-ttu-id="25b72-161">[!code-vb[VbVbalrGuidelines&#13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-161">[!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]</span></span>  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="25b72-162">Utilisez le mot clé</span><span class="sxs-lookup"><span data-stu-id="25b72-162">Use the With Keyword</span></span>  
 <span data-ttu-id="25b72-163">Lorsque vous effectuez une série d’appels à un objet, envisagez d’utiliser le `With` mot clé :</span><span class="sxs-lookup"><span data-stu-id="25b72-163">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 <span data-ttu-id="25b72-164">[!code-vb[VbVbalrGuidelines&#15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-164">[!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]</span></span>  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="25b72-165">Utilisez les instructions Try... Catch et les instructions Using lorsque vous utilisez la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="25b72-165">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="25b72-166">N’utilisez pas `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="25b72-166">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="25b72-167">Utilisez le mot-clé IsNot</span><span class="sxs-lookup"><span data-stu-id="25b72-167">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="25b72-168">Utilisez le `IsNot` (mot clé) au lieu de `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="25b72-168">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="25b72-169">Nouveau mot clé</span><span class="sxs-lookup"><span data-stu-id="25b72-169">New Keyword</span></span>  
  
-   <span data-ttu-id="25b72-170">Utilisez l’instanciation courte.</span><span class="sxs-lookup"><span data-stu-id="25b72-170">Use short instantiation.</span></span> <span data-ttu-id="25b72-171">Par exemple, utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="25b72-171">For example, use the following syntax:</span></span>  
  
     <span data-ttu-id="25b72-172">[!code-vb[VbVbalrGuidelines n °&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-172">[!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]</span></span>  
  
     <span data-ttu-id="25b72-173">La ligne précédente est équivalente à ceci :</span><span class="sxs-lookup"><span data-stu-id="25b72-173">The preceding line is equivalent to this:</span></span>  
  
     <span data-ttu-id="25b72-174">[!code-vb[VbVbalrGuidelines&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-174">[!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-175">Utilisez des initialiseurs d’objets pour les nouveaux objets au lieu du constructeur sans paramètre :</span><span class="sxs-lookup"><span data-stu-id="25b72-175">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     <span data-ttu-id="25b72-176">[!code-vb[VbVbalrGuidelines n °&23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-176">[!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]</span></span>  
  
### <a name="event-handling"></a><span data-ttu-id="25b72-177">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="25b72-177">Event Handling</span></span>  
  
-   <span data-ttu-id="25b72-178">Utilisez `Handles` plutôt que `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="25b72-178">Use `Handles` rather than `AddHandler`:</span></span>  
  
     <span data-ttu-id="25b72-179">[!code-vb[VbVbalrGuidelines&#24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-179">[!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-180">Utilisez `AddressOf`et vous n’instanciez pas le délégué explicitement :</span><span class="sxs-lookup"><span data-stu-id="25b72-180">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     <span data-ttu-id="25b72-181">[!code-vb[VbVbalrGuidelines&#25;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-181">[!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-182">Lorsque vous définissez un événement, utilisez la syntaxe courte et laissez le compilateur définir le délégué :</span><span class="sxs-lookup"><span data-stu-id="25b72-182">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     <span data-ttu-id="25b72-183">[!code-vb[VbVbalrGuidelines&#26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-183">[!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-184">Ne pas vérifier si un événement est `Nothing` (null) avant d’appeler le `RaiseEvent` (méthode).</span><span class="sxs-lookup"><span data-stu-id="25b72-184">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="25b72-185">`RaiseEvent`vérifie le `Nothing` avant de déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="25b72-185">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="25b72-186">À l’aide de membres partagés</span><span class="sxs-lookup"><span data-stu-id="25b72-186">Using Shared Members</span></span>  
 <span data-ttu-id="25b72-187">Appelez `Shared` membres en utilisant le nom de classe, pas à partir d’une variable d’instance.</span><span class="sxs-lookup"><span data-stu-id="25b72-187">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="25b72-188">Utiliser des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="25b72-188">Use XML Literals</span></span>  
 <span data-ttu-id="25b72-189">Les littéraux XML simplifient les tâches les plus courantes que vous rencontrez lorsque vous utilisez XML (par exemple, charge, requête et transformation).</span><span class="sxs-lookup"><span data-stu-id="25b72-189">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="25b72-190">Lorsque vous développez avec XML, suivez ces instructions :</span><span class="sxs-lookup"><span data-stu-id="25b72-190">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="25b72-191">Utiliser des littéraux XML pour créer des documents XML et des fragments au lieu d’appeler directement des API XML.</span><span class="sxs-lookup"><span data-stu-id="25b72-191">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="25b72-192">Importez les espaces de noms XML au niveau du fichier ou du projet pour tirer parti des optimisations des performances des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="25b72-192">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="25b72-193">Utilisez les propriétés d’axe XML pour accéder aux éléments et attributs dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="25b72-193">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="25b72-194">Utiliser des expressions incorporées pour inclure des valeurs et créer du code XML à partir de valeurs existantes au lieu d’utiliser des appels d’API tels que la `Add` méthode :</span><span class="sxs-lookup"><span data-stu-id="25b72-194">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     <span data-ttu-id="25b72-195">[!code-vb[27 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-195">[!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="25b72-196">Requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="25b72-196">LINQ Queries</span></span>  
  
-   <span data-ttu-id="25b72-197">Utilisez des noms explicites pour les variables de requête :</span><span class="sxs-lookup"><span data-stu-id="25b72-197">Use meaningful names for query variables:</span></span>  
  
     <span data-ttu-id="25b72-198">[!code-vb[VbVbalrGuidelines&#28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-198">[!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-199">Fournir des noms pour les éléments dans une requête pour vous assurer que les noms de propriété des types anonymes sont correctement écrits en majuscules à l’aide de la casse Pascal casse :</span><span class="sxs-lookup"><span data-stu-id="25b72-199">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     <span data-ttu-id="25b72-200">[!code-vb[VbVbalrGuidelines&#29;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-200">[!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-201">Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus.</span><span class="sxs-lookup"><span data-stu-id="25b72-201">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="25b72-202">Par exemple, si votre requête retourne un client, nom et un ID de commande, les renommer au lieu de les laisser en tant que `Name` et `ID` dans le résultat :</span><span class="sxs-lookup"><span data-stu-id="25b72-202">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     <span data-ttu-id="25b72-203">[!code-vb[30 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-203">[!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-204">Utiliser l’inférence de type dans la déclaration de variables de requête et des variables de portée :</span><span class="sxs-lookup"><span data-stu-id="25b72-204">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     <span data-ttu-id="25b72-205">[!code-vb[VbVbalrGuidelines&#31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-205">[!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-206">Alignez les clauses de requête sous la `From` instruction :</span><span class="sxs-lookup"><span data-stu-id="25b72-206">Align query clauses under the `From` statement:</span></span>  
  
     <span data-ttu-id="25b72-207">[!code-vb[VbVbalrGuidelines n°&32;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-207">[!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-208">Utilisez `Where` clauses avant les autres clauses de requête afin que les clauses de requête ultérieures opèrent sur l’ensemble filtré de données :</span><span class="sxs-lookup"><span data-stu-id="25b72-208">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     <span data-ttu-id="25b72-209">[!code-vb[VbVbalrGuidelines&#33;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-209">[!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]</span></span>  
  
-   <span data-ttu-id="25b72-210">Utilisez le `Join` clause pour définir explicitement une opération de jointure au lieu d’utiliser le `Where` clause définir implicitement une opération de jointure :</span><span class="sxs-lookup"><span data-stu-id="25b72-210">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     <span data-ttu-id="25b72-211">[!code-vb[VbVbalrGuidelines&#34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span><span class="sxs-lookup"><span data-stu-id="25b72-211">[!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b72-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25b72-212">See Also</span></span>  
 [<span data-ttu-id="25b72-213">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="25b72-213">Secure Coding Guidelines</span></span>](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
