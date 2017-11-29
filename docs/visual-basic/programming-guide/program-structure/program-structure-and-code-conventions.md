---
title: Structure de programme et conventions de codage (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b38ba9623a20dcd1be4bc96f4aff1eb646b0a053
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="f71ab-102">Structure de programme et conventions de codage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f71ab-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="f71ab-103">Cette section présente le type [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] structure du programme, fournit un simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] du programme, « Hello, World » et présente [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] conventions de code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-103">This section introduces the typical [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program structure, provides a simple [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program, "Hello, World", and discusses [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code conventions.</span></span> <span data-ttu-id="f71ab-104">Conventions de code sont des suggestions qui reposent pas sur la logique d’un programme mais sur sa structure physique et son apparence.</span><span class="sxs-lookup"><span data-stu-id="f71ab-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="f71ab-105">Suivant les rend plus faciles à lire, comprendre et gérer votre code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="f71ab-106">Conventions de code incluent, entre autres :</span><span class="sxs-lookup"><span data-stu-id="f71ab-106">Code conventions can include, among others:</span></span>  
  
-   <span data-ttu-id="f71ab-107">Formats normalisés pour l’étiquetage et les commentaires de code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-107">Standardized formats for labeling and commenting code.</span></span>  
  
-   <span data-ttu-id="f71ab-108">Instructions pour l’espacement, la mise en forme et la mise en retrait du code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
-   <span data-ttu-id="f71ab-109">Conventions d’affectation de noms pour les objets, des variables et des procédures.</span><span class="sxs-lookup"><span data-stu-id="f71ab-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="f71ab-110">Les rubriques suivantes présentent un ensemble de la programmation des recommandations pour [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programmes, ainsi que des exemples d’utilisation appropriée.</span><span class="sxs-lookup"><span data-stu-id="f71ab-110">The following topics present a set of programming guidelines for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f71ab-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f71ab-111">In This Section</span></span>  
 [<span data-ttu-id="f71ab-112">Structure d’un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="f71ab-113">Fournit une vue d’ensemble des éléments qui composent un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="f71ab-113">Provides an overview of the elements that make up a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="f71ab-114">Procédure Main dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="f71ab-115">Décrit la procédure qui sert le démarrage du point de contrôle général pour votre application.</span><span class="sxs-lookup"><span data-stu-id="f71ab-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="f71ab-116">Références et l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="f71ab-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="f71ab-117">Explique comment référencer des objets dans d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="f71ab-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="f71ab-118">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="f71ab-119">Décrit comment les espaces de noms organisent les objets dans les assemblys.</span><span class="sxs-lookup"><span data-stu-id="f71ab-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="f71ab-120">Conventions d’affectation de noms de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="f71ab-121">Comprend des instructions générales de nommer les procédures, de constantes, variables, arguments et objets.</span><span class="sxs-lookup"><span data-stu-id="f71ab-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="f71ab-122">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="f71ab-123">Passe en revue les instructions utilisées pour le développement des exemples de cette documentation.</span><span class="sxs-lookup"><span data-stu-id="f71ab-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="f71ab-124">Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="f71ab-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="f71ab-125">Décrit comment compiler sélectivement des blocs de code spécifiques tout en demandant au compilateur d’ignorer d’autres.</span><span class="sxs-lookup"><span data-stu-id="f71ab-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="f71ab-126">Guide pratique : diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="f71ab-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="f71ab-127">Montre comment répartir les instructions longues sur plusieurs lignes et associer des instructions courtes sur une seule ligne.</span><span class="sxs-lookup"><span data-stu-id="f71ab-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="f71ab-128">Guide pratique : réduire et masquer des sections de code</span><span class="sxs-lookup"><span data-stu-id="f71ab-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="f71ab-129">Montre comment réduire et masquer des sections de code dans le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-129">Shows how to collapse and hide sections of code in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code editor.</span></span>  
  
 [<span data-ttu-id="f71ab-130">Guide pratique : étiqueter des instructions</span><span class="sxs-lookup"><span data-stu-id="f71ab-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="f71ab-131">Montre comment marquer une ligne de code pour identifier pour une utilisation avec des instructions telles que `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="f71ab-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="f71ab-132">Caractères spéciaux dans le code</span><span class="sxs-lookup"><span data-stu-id="f71ab-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="f71ab-133">Explique comment et où utiliser des caractères non numériques et non alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="f71ab-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="f71ab-134">Commentaires dans le code</span><span class="sxs-lookup"><span data-stu-id="f71ab-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="f71ab-135">Explique comment ajouter des commentaires descriptifs à votre code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="f71ab-136">Utilisation des mots clés comme noms d’éléments dans le code</span><span class="sxs-lookup"><span data-stu-id="f71ab-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="f71ab-137">Décrit comment utiliser des crochets (`[]`) pour délimiter les noms de variables qui sont également [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] mots clés.</span><span class="sxs-lookup"><span data-stu-id="f71ab-137">Describes how to use brackets (`[]`) to delimit variable names that are also [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keywords.</span></span>  
  
 [<span data-ttu-id="f71ab-138">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="f71ab-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="f71ab-139">Décrit différentes manières pour faire référence aux éléments d’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="f71ab-139">Describes various ways to refer to elements of a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 [<span data-ttu-id="f71ab-140">Limitations de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71ab-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="f71ab-141">Traite de la suppression des limites de codage connues dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f71ab-141">Discusses the removal of known coding limits within [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f71ab-142">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="f71ab-142">Related Sections</span></span>  
 [<span data-ttu-id="f71ab-143">Conventions typographiques</span><span class="sxs-lookup"><span data-stu-id="f71ab-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="f71ab-144">Fournit les conventions de codage standard pour [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f71ab-144">Provides standard coding conventions for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="f71ab-145">Écriture de code</span><span class="sxs-lookup"><span data-stu-id="f71ab-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="f71ab-146">Décrit les fonctionnalités qui facilitent l’écriture et la gestion de votre code.</span><span class="sxs-lookup"><span data-stu-id="f71ab-146">Describes features that make it easier for you to write and manage your code.</span></span>
