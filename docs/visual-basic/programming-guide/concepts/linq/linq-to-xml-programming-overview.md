---
title: "Présentation de programmation XML (Visual Basic) de LINQ to | Documents Microsoft"
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
ms.assetid: a7c07d0a-1fae-4610-ae51-56dd7075cc14
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 57d52b1bc46263e4e8e662be6a83bf4718813b43
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-programming-overview-visual-basic"></a><span data-ttu-id="550a4-102">LINQ to XML programmation présentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-102">LINQ to XML Programming Overview (Visual Basic)</span></span>
<span data-ttu-id="550a4-103">Ces rubriques fournissent des informations de haut niveau concernant les classes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], ainsi que des informations détaillées sur trois des classes les plus importantes.</span><span class="sxs-lookup"><span data-stu-id="550a4-103">These topics provide high-level overview information about the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes, as well as detailed information about three of the most important classes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="550a4-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="550a4-104">In This Section</span></span>  
  
|<span data-ttu-id="550a4-105">Rubrique</span><span class="sxs-lookup"><span data-stu-id="550a4-105">Topic</span></span>|<span data-ttu-id="550a4-106">Description</span><span class="sxs-lookup"><span data-stu-id="550a4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="550a4-107">Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-107">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-vs-procedural-programming-linq-to-xml.md)|<span data-ttu-id="550a4-108">Fournit une vue d'ensemble des deux principales approches de l'écriture d'applications LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="550a4-108">Provides a high level view of the two principle approaches to writing LINQ to XML applications.</span></span>|  
|[<span data-ttu-id="550a4-109">LINQ to XML la vue d’ensemble de Classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-109">LINQ to XML Classes Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-classes-overview.md)|<span data-ttu-id="550a4-110">Fournit une vue d'ensemble des classes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="550a4-110">Provides an overview of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes.</span></span>|  
|[<span data-ttu-id="550a4-111">Vue d’ensemble de la classe XElement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-111">XElement Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)|<span data-ttu-id="550a4-112">Introduit la <xref:System.Xml.Linq.XElement>classe, qui représente les éléments XML.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="550a4-112">Introduces the <xref:System.Xml.Linq.XElement> class, which represents XML elements.</span></span> <span data-ttu-id="550a4-113"><xref:System.Xml.Linq.XElement>est une des classes fondamentales dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] hiérarchie de classes.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="550a4-113"><xref:System.Xml.Linq.XElement> is one of the fundamental classes in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] class hierarchy.</span></span>|  
|[<span data-ttu-id="550a4-114">Vue d’ensemble de la classe XAttribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-114">XAttribute Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)|<span data-ttu-id="550a4-115">Introduit la <xref:System.Xml.Linq.XAttribute>classe qui représente des attributs XML.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="550a4-115">Introduces the <xref:System.Xml.Linq.XAttribute> class, which represents XML attributes.</span></span>|  
|[<span data-ttu-id="550a4-116">Vue d’ensemble de la classe XDocument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-116">XDocument Class Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)|<span data-ttu-id="550a4-117">Introduit la <xref:System.Xml.Linq.XDocument>classe qui représente des documents XML.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="550a4-117">Introduces the <xref:System.Xml.Linq.XDocument> class, which represents XML documents.</span></span>|  
|[<span data-ttu-id="550a4-118">Comment : générer des exemples LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-118">How to: Build LINQ to XML Examples (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-build-linq-to-xml-examples.md)|<span data-ttu-id="550a4-119">Contient le `Imports` instructions nécessaires pour générer l’exemples LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="550a4-119">Contains the `Imports` statements that are required to build the LINQ to XML examples.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="550a4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="550a4-120">See Also</span></span>  
 [<span data-ttu-id="550a4-121">Guide de programmation (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="550a4-121">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
