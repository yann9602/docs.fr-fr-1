---
title: "Vue d’ensemble de la programmation LINQ to XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2dfa9b6f-5890-461d-b81c-316853c7f320
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bc22991f53920b045280d3e74b9b8dd73e63c944
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-programming-overview-c"></a><span data-ttu-id="833b4-102">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-102">LINQ to XML Programming Overview (C#)</span></span>
<span data-ttu-id="833b4-103">Ces rubriques fournissent des informations de haut niveau concernant les classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ainsi que des informations détaillées sur trois des classes les plus importantes.</span><span class="sxs-lookup"><span data-stu-id="833b4-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="833b4-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="833b4-104">In This Section</span></span>  
  
|<span data-ttu-id="833b4-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="833b4-105">Topic</span></span>|<span data-ttu-id="833b4-106">Description</span><span class="sxs-lookup"><span data-stu-id="833b4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="833b4-107">Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-107">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="833b4-108">Fournit une vue d'ensemble des deux principales approches de l'écriture d'applications LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="833b4-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="833b4-109">Vue d’ensemble des classes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-109">LINQ to XML Classes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="833b4-110">Fournit une vue d'ensemble des classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="833b4-110">Provides an overview of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes.</span></span>|  
|[<span data-ttu-id="833b4-111">Vue d’ensemble de la classe XElement (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-111">XElement Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="833b4-112">Présente la classe <xref:System.Xml.Linq.XElement>, qui représente des éléments XML.</span><span class="sxs-lookup"><span data-stu-id="833b4-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="833b4-113"><xref:System.Xml.Linq.XElement> est l’une des classes fondamentales dans la hiérarchie de classes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="833b4-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="833b4-114">Vue d’ensemble de la classe XAttribute (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-114">XAttribute Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="833b4-115">Présente la classe <xref:System.Xml.Linq.XAttribute>, qui représente des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="833b4-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="833b4-116">Vue d’ensemble de la classe XDocument (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-116">XDocument Class Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="833b4-117">Présente la classe <xref:System.Xml.Linq.XDocument>, qui représente des documents XML.</span><span class="sxs-lookup"><span data-stu-id="833b4-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="833b4-118">Guide pratique pour générer des exemples LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-118">How to: Build LINQ to XML Examples (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="833b4-119">Contient les directives `Using` nécessaires pour générer les exemples LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="833b4-119">Contains the `Using` directives that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="833b4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="833b4-120">See Also</span></span>  
 [<span data-ttu-id="833b4-121">Guide de programmation (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="833b4-121">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

