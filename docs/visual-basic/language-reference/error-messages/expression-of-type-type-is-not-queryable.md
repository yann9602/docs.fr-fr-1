---
title: "Expression de type &lt;type&gt; ne peut pas être interrogée | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
dev_langs:
- VB
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
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
ms.openlocfilehash: 84563c7339ffe7415017280d74a13d6501236da5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="fb392-102">Expression de type &lt;type&gt; ne peut pas être interrogée</span><span class="sxs-lookup"><span data-stu-id="fb392-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="fb392-103">Expression de type \<type > ne peut pas être interrogée.</span><span class="sxs-lookup"><span data-stu-id="fb392-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="fb392-104">Assurez-vous que vous ne manque une importation d’espace de noms de référence ou d’assembly pour le fournisseur LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb392-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="fb392-105">Types pouvant être interrogés sont définis dans le <xref:System.Linq>, <xref:System.Data.Linq>, et <xref:System.Xml.Linq>espaces de noms.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="fb392-106">Vous devez importer un ou plusieurs de ces espaces de noms pour effectuer des requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb392-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="fb392-107">Le <xref:System.Linq>espace de noms vous permet de requêtes sur des objets tels que des collections et des tableaux à l’aide de LINQ.</xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="fb392-108">Le <xref:System.Data.Linq>vous permet d’interroger des groupes de données ADO.NET et des bases de données SQL Server à l’aide de LINQ.</xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="fb392-109">Le <xref:System.Xml.Linq>espace de noms vous permet d’interroger XML à l’aide de LINQ et à utiliser les fonctionnalités XML dans Visual Basic.</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="fb392-110">**ID d’erreur :** BC36593</span><span class="sxs-lookup"><span data-stu-id="fb392-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb392-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="fb392-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="fb392-112">Ajouter un `Import` instruction pour le <xref:System.Linq>, <xref:System.Data.Linq>, ou <xref:System.Xml.Linq>espace de noms à votre fichier de code.</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="fb392-113">Vous pouvez également importer des espaces de noms pour votre projet à l’aide de la **références** page du Concepteur de projets (**mon projet**).</span><span class="sxs-lookup"><span data-stu-id="fb392-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="fb392-114">Vérifiez que le type que vous avez identifié comme source de votre requête est un type requêtable.</span><span class="sxs-lookup"><span data-stu-id="fb392-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="fb392-115">Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="fb392-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb392-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb392-116">See Also</span></span>  
 <span data-ttu-id="fb392-117"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-117"><xref:System.Linq></span></span>   
 <span data-ttu-id="fb392-118"><xref:System.Data.Linq></xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-118"><xref:System.Data.Linq></span></span>   
 <span data-ttu-id="fb392-119"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="fb392-119"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="fb392-120"> [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="fb392-120"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="fb392-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb392-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="fb392-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb392-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="fb392-123"> [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fb392-123"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="fb392-124"> [Instruction Imports (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="fb392-124"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="fb392-125"> [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="fb392-125"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
