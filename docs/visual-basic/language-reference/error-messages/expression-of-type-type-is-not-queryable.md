---
title: "Expression de type &lt;type&gt; n’est pas utilisable dans une requête"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="bca46-102">Expression de type &lt;type&gt; n’est pas utilisable dans une requête</span><span class="sxs-lookup"><span data-stu-id="bca46-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="bca46-103">Expression de type \<type > ne peut pas être interrogée.</span><span class="sxs-lookup"><span data-stu-id="bca46-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="bca46-104">Assurez-vous que vous ne manque pas une importation d’espace de noms de référence ou d’assembly pour le fournisseur LINQ.</span><span class="sxs-lookup"><span data-stu-id="bca46-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="bca46-105">Types pouvant être interrogés sont définis dans le <xref:System.Linq>, <xref:System.Data.Linq>, et <xref:System.Xml.Linq> espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="bca46-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="bca46-106">Vous devez importer un ou plusieurs de ces espaces de noms pour effectuer des requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="bca46-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="bca46-107">Le <xref:System.Linq> espace de noms vous permet de requêtes sur des objets tels que des collections et tableaux à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="bca46-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="bca46-108">Le <xref:System.Data.Linq> vous permet d’interroger des jeux de données ADO.NET et des bases de données SQL Server à l’aide de LINQ.</span><span class="sxs-lookup"><span data-stu-id="bca46-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="bca46-109">Le <xref:System.Xml.Linq> espace de noms vous permet d’interroger XML à l’aide de LINQ et à utiliser les fonctionnalités XML en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bca46-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="bca46-110">**ID d’erreur :** BC36593</span><span class="sxs-lookup"><span data-stu-id="bca46-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bca46-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bca46-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="bca46-112">Ajouter un `Import` instruction pour le <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq> espace de noms à votre fichier de code.</span><span class="sxs-lookup"><span data-stu-id="bca46-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="bca46-113">Vous pouvez également importer des espaces de noms pour votre projet à l’aide de la **références** page du Concepteur de projets (**mon projet**).</span><span class="sxs-lookup"><span data-stu-id="bca46-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="bca46-114">Vérifiez que le type que vous avez identifié comme source de votre requête est un type requêtable.</span><span class="sxs-lookup"><span data-stu-id="bca46-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="bca46-115">Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="bca46-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca46-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca46-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="bca46-117">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bca46-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="bca46-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="bca46-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="bca46-119">XML</span><span class="sxs-lookup"><span data-stu-id="bca46-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="bca46-120">Références et l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="bca46-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="bca46-121">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="bca46-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="bca46-122">Page Références, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bca46-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
