---
title: Manipulation de code XML dans Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 061617524659ac2f8793e2030f26a2d6b2724a64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="13292-102">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13292-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="13292-103">Vous pouvez utiliser *littéraux XML* charger XML à partir d’une source externe, telles que les flux, d’un fichier ou d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="13292-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="13292-104">Vous pouvez ensuite utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pour manipuler le document XML et utiliser [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] pour interroger le document XML.</span><span class="sxs-lookup"><span data-stu-id="13292-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13292-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="13292-105">In This Section</span></span>  
 [<span data-ttu-id="13292-106">Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux</span><span class="sxs-lookup"><span data-stu-id="13292-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="13292-107">Montre comment charger du code XML dans un <xref:System.Xml.Linq.XDocument> ou <xref:System.Xml.Linq.XElement> objet à partir d’un fichier texte, une chaîne ou un flux.</span><span class="sxs-lookup"><span data-stu-id="13292-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="13292-108">Guide pratique : transformer du code XML à l’aide de LINQ</span><span class="sxs-lookup"><span data-stu-id="13292-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="13292-109">Montre comment transformer le contenu d’un <xref:System.Xml.Linq.XDocument> objet dans un nouveau document XML.</span><span class="sxs-lookup"><span data-stu-id="13292-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="13292-110">Guide pratique : modifier des littéraux XML</span><span class="sxs-lookup"><span data-stu-id="13292-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="13292-111">Montre comment modifier des éléments, des attributs et des valeurs dans un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="13292-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="13292-112">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="13292-112">Related Sections</span></span>  
 [<span data-ttu-id="13292-113">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="13292-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 <span data-ttu-id="13292-114">Fournit des liens vers des sections qui décrivent les différentes propriétés d’accès XML.</span><span class="sxs-lookup"><span data-stu-id="13292-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="13292-115">Vue d’ensemble de LINQ to XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13292-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="13292-116">Fournit une introduction à l’utilisation de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13292-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13292-117">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13292-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="13292-118">Fournit une introduction à l’aide de littéraux XML en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13292-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13292-119">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13292-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="13292-120">Montre comment accéder aux parties d’un élément ou document XML en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13292-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="13292-121">XML</span><span class="sxs-lookup"><span data-stu-id="13292-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="13292-122">Fournit des liens vers des sections qui décrivent comment utiliser [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="13292-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13292-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13292-123">See Also</span></span>  
 [<span data-ttu-id="13292-124">XML</span><span class="sxs-lookup"><span data-stu-id="13292-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="13292-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="13292-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="13292-126">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13292-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
