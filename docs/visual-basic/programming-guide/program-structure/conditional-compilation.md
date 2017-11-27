---
title: Compilation conditionnelle en Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="57bb5-102">Compilation conditionnelle en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57bb5-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="57bb5-103">Dans *compilation conditionnelle*, blocs de code dans un programme spécifiques compiler de façon sélective tandis que d’autres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="57bb5-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="57bb5-104">Par exemple, vous souhaitez écrire des instructions de débogage qui comparent la rapidité de différentes approches pour la même tâche de programmation, ou vous peuvent souhaiter localiser une application dans plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="57bb5-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="57bb5-105">Instructions de compilation conditionnelle sont conçues pour s’exécuter pendant la compilation, pas au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="57bb5-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="57bb5-106">Vous désignez des blocs de code à compiler de façon conditionnelle avec la `#If...Then...#Else` la directive.</span><span class="sxs-lookup"><span data-stu-id="57bb5-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="57bb5-107">Par exemple, pour créer le Français et allemand versions de la même application à partir de la même du code source, incorporez des segments de code spécifique à la plateforme dans `#If...Then` instructions à l’aide de l’une des constantes prédéfinies `FrenchVersion` et `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="57bb5-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="57bb5-108">L’exemple suivant montre comment :</span><span class="sxs-lookup"><span data-stu-id="57bb5-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="57bb5-109">Si vous définissez la valeur de la `FrenchVersion` constante de compilation conditionnelle à `True` au moment de la compilation, le code conditionnel de la version Français est compilé.</span><span class="sxs-lookup"><span data-stu-id="57bb5-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="57bb5-110">Si vous définissez la valeur de la `GermanVersion` constante `True`, le compilateur utilise la version allemande.</span><span class="sxs-lookup"><span data-stu-id="57bb5-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="57bb5-111">Si aucune n’est définie `True`, le code de la dernière `Else` bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="57bb5-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57bb5-112">La saisie semi-automatique ne fonctionne pas lorsque vous modifiez du code et à l’aide de directives de compilation conditionnelles si le code ne fait pas partie de la branche active.</span><span class="sxs-lookup"><span data-stu-id="57bb5-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="57bb5-113">Déclarer des constantes de Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="57bb5-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="57bb5-114">Vous pouvez définir des constantes de compilation conditionnelle dans un des trois façons :</span><span class="sxs-lookup"><span data-stu-id="57bb5-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="57bb5-115">Dans la **Concepteur de projets**</span><span class="sxs-lookup"><span data-stu-id="57bb5-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="57bb5-116">Sur la ligne de commande lorsque vous utilisez le compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="57bb5-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="57bb5-117">Dans votre code</span><span class="sxs-lookup"><span data-stu-id="57bb5-117">In your code</span></span>  
  
 <span data-ttu-id="57bb5-118">Constantes de compilation conditionnelle ont une portée spéciale et ne sont pas accessibles à partir du code standard.</span><span class="sxs-lookup"><span data-stu-id="57bb5-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="57bb5-119">La portée d’une constante de compilation conditionnelle est dépendante de la façon dont elle est définie.</span><span class="sxs-lookup"><span data-stu-id="57bb5-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="57bb5-120">Le tableau suivant répertorie la portée des constantes déclarées à l’aide de chacune des trois méthodes mentionnées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="57bb5-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="57bb5-121">La constante a la valeur</span><span class="sxs-lookup"><span data-stu-id="57bb5-121">How constant is set</span></span>|<span data-ttu-id="57bb5-122">Étendue de constante</span><span class="sxs-lookup"><span data-stu-id="57bb5-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="57bb5-123">**Concepteur de projets**</span><span class="sxs-lookup"><span data-stu-id="57bb5-123">**Project Designer**</span></span>|<span data-ttu-id="57bb5-124">Public à tous les fichiers dans le projet</span><span class="sxs-lookup"><span data-stu-id="57bb5-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="57bb5-125">Ligne de commande</span><span class="sxs-lookup"><span data-stu-id="57bb5-125">Command line</span></span>|<span data-ttu-id="57bb5-126">Public à tous les fichiers passés au compilateur de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="57bb5-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="57bb5-127">`#Const`instruction dans le code</span><span class="sxs-lookup"><span data-stu-id="57bb5-127">`#Const` statement in code</span></span>|<span data-ttu-id="57bb5-128">Privé pour le fichier dans lequel elle est déclarée</span><span class="sxs-lookup"><span data-stu-id="57bb5-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="57bb5-129">Pour définir des constantes dans le Concepteur de projets</span><span class="sxs-lookup"><span data-stu-id="57bb5-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="57bb5-130">-Avant de créer votre fichier exécutable, définissez des constantes dans le **Concepteur de projets** en suivant les étapes fournies dans [gestion de projet et les propriétés de la Solution](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="57bb5-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="57bb5-131">Pour définir des constantes au niveau de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="57bb5-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="57bb5-132">-Utilisez le **/d** commutateur pour entrer des constantes de compilation conditionnelle, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="57bb5-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="57bb5-133">Aucun espace n’est nécessaire entre la **/d** commutateur et la première constante.</span><span class="sxs-lookup"><span data-stu-id="57bb5-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="57bb5-134">Pour plus d’informations, consultez [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="57bb5-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="57bb5-135">Les déclarations de ligne de commande substituent les déclarations entrées dans le **Concepteur de projet**, mais ne les suppriment pas.</span><span class="sxs-lookup"><span data-stu-id="57bb5-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="57bb5-136">Arguments définis **Concepteur de projets** restent en vigueur pour les compilations ultérieures.</span><span class="sxs-lookup"><span data-stu-id="57bb5-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="57bb5-137">Lorsque vous écrivez des constantes dans le code lui-même, ne sont pas des règles strictes sur leur emplacement, car leur étendue est l’ensemble du module dans lequel ils sont déclarés.</span><span class="sxs-lookup"><span data-stu-id="57bb5-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="57bb5-138">Pour définir des constantes dans votre code</span><span class="sxs-lookup"><span data-stu-id="57bb5-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="57bb5-139">-Placez les constantes dans le bloc de déclaration du module dans lequel ils sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="57bb5-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="57bb5-140">Cela permet de garder votre code organisé et plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="57bb5-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="57bb5-141">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="57bb5-141">Related Topics</span></span>  
  
|<span data-ttu-id="57bb5-142">Titre</span><span class="sxs-lookup"><span data-stu-id="57bb5-142">Title</span></span>|<span data-ttu-id="57bb5-143">Description</span><span class="sxs-lookup"><span data-stu-id="57bb5-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="57bb5-144">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="57bb5-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="57bb5-145">Fournit des suggestions pour rendre votre code facile à lire et mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="57bb5-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="57bb5-146">Référence</span><span class="sxs-lookup"><span data-stu-id="57bb5-146">Reference</span></span>  
 [<span data-ttu-id="57bb5-147">#Const (directive)</span><span class="sxs-lookup"><span data-stu-id="57bb5-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="57bb5-148">#If...Then...#Else, directives</span><span class="sxs-lookup"><span data-stu-id="57bb5-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="57bb5-149">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57bb5-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
