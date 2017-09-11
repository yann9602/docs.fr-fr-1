---
title: "Comment : utiliser des arborescences d’Expression pour générer des requêtes dynamiques (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="7deb3-102">Comment : utiliser des arborescences d’Expression pour générer des requêtes dynamiques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7deb3-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>
<span data-ttu-id="7deb3-103">Dans LINQ, les arborescences d’expression sont utilisés pour représenter des requêtes structurées qui cible des sources de données qui implémentent <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="7deb3-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="7deb3-104">Par exemple, le fournisseur LINQ implémente la <xref:System.Linq.IQueryable%601>interface pour l’interrogation de données relationnelles.</xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="7deb3-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="7deb3-105">Le compilateur Visual Basic compile les requêtes qui ciblent des sources dans le code qui génère une arborescence d’expression lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7deb3-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="7deb3-106">Le fournisseur de requête peut ensuite parcourir la structure de données arborescente expression et traduire dans un langage de requête approprié pour la source de données.</span><span class="sxs-lookup"><span data-stu-id="7deb3-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>  
  
 <span data-ttu-id="7deb3-107">Arborescences d’expression sont également utilisées dans LINQ pour représenter des expressions lambda qui sont associées aux variables de type <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601></span><span class="sxs-lookup"><span data-stu-id="7deb3-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>  
  
 <span data-ttu-id="7deb3-108">Cette rubrique décrit comment utiliser des arborescences d’expression pour créer des requêtes LINQ dynamiques.</span><span class="sxs-lookup"><span data-stu-id="7deb3-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="7deb3-109">Les requêtes dynamiques sont utiles lorsque les caractéristiques d’une requête ne sont pas connus au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7deb3-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="7deb3-110">Par exemple, une application peut fournir une interface utilisateur qui permet aux utilisateurs de spécifier un ou plusieurs prédicats pour filtrer les données.</span><span class="sxs-lookup"><span data-stu-id="7deb3-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="7deb3-111">Pour utiliser LINQ pour interroger, ce type d’application doit utiliser les arborescences d’expression pour créer la requête LINQ au runtime.</span><span class="sxs-lookup"><span data-stu-id="7deb3-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7deb3-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="7deb3-112">Example</span></span>  
 <span data-ttu-id="7deb3-113">L’exemple suivant montre comment utiliser des arborescences d’expression pour construire une requête sur un `IQueryable` de source de données et de l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="7deb3-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="7deb3-114">Le code génère une arborescence d’expression pour représenter la requête suivante :</span><span class="sxs-lookup"><span data-stu-id="7deb3-114">The code builds an expression tree to represent the following query:</span></span>  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 <span data-ttu-id="7deb3-115">Les méthodes de fabrique dans la <xref:System.Linq.Expressions>espace de noms sont utilisés pour créer des arborescences d’expression qui représentent les expressions composant la requête globale.</xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="7deb3-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="7deb3-116">Les expressions qui représentent des appels aux méthodes d’opérateur de requête standard font référence à la <xref:System.Linq.Queryable>des implémentations de ces méthodes.</xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="7deb3-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="7deb3-117">La dernière arborescence d’expression est passée à la <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>implémentation du fournisseur de la `IQueryable` source de données pour créer une requête exécutable de type `IQueryable`.</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29></span><span class="sxs-lookup"><span data-stu-id="7deb3-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="7deb3-118">Les résultats sont obtenus par énumération de cette variable de requête.</span><span class="sxs-lookup"><span data-stu-id="7deb3-118">The results are obtained by enumerating that query variable.</span></span>  
  
<span data-ttu-id="7deb3-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7deb3-119"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7deb3-120">Ce code utilise un nombre fixe d’expressions dans le prédicat qui est transmis à la `Queryable.Where` (méthode).</span><span class="sxs-lookup"><span data-stu-id="7deb3-120">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="7deb3-121">Toutefois, vous pouvez écrire une application qui combine un nombre variable d’expressions de prédicat qui dépend de l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7deb3-121">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="7deb3-122">Vous pouvez également varier les opérateurs de requête standard qui sont appelées dans la requête, en fonction de l’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7deb3-122">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7deb3-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7deb3-123">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7deb3-124">Créer un nouveau **Application Console** projet.</span><span class="sxs-lookup"><span data-stu-id="7deb3-124">Create a new **Console Application** project.</span></span>  
  
-   <span data-ttu-id="7deb3-125">Ajoutez une référence à System.Core.dll si elle n’est pas déjà référencée.</span><span class="sxs-lookup"><span data-stu-id="7deb3-125">Add a reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="7deb3-126">Inclure l’espace de noms System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="7deb3-126">Include the System.Linq.Expressions namespace.</span></span>  
  
-   <span data-ttu-id="7deb3-127">Copiez le code de l’exemple et collez-le dans le `Main` `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="7deb3-127">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7deb3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7deb3-128">See Also</span></span>  
 <span data-ttu-id="7deb3-129">[Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="7deb3-129">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="7deb3-130"> [Comment : exécuter des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span><span class="sxs-lookup"><span data-stu-id="7deb3-130"> [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)</span></span>
