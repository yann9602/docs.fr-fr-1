---
title: "Vue d’ensemble des espaces de noms (LINQ to XML) | Documents Microsoft"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
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
ms.openlocfilehash: 7e9536615871b83099a11e46125ed85b44d9335d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="namespaces-overview-linq-to-xml"></a><span data-ttu-id="9d350-102">Vue d'ensemble des espaces de noms (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9d350-102">Namespaces Overview (LINQ to XML)</span></span>
<span data-ttu-id="9d350-103">Cette rubrique présente les espaces de noms, <xref:System.Xml.Linq.XName>classe et la <xref:System.Xml.Linq.XNamespace>classe.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9d350-103">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>  
  
## <a name="xml-names"></a><span data-ttu-id="9d350-104">Noms XML</span><span class="sxs-lookup"><span data-stu-id="9d350-104">XML Names</span></span>  
 <span data-ttu-id="9d350-105">Les noms XML constituent souvent une source de complexité dans la programmation XML.</span><span class="sxs-lookup"><span data-stu-id="9d350-105">XML names are often a source of complexity in XML programming.</span></span> <span data-ttu-id="9d350-106">Un nom XML est constitué d'un espace de noms XML (également appelé URI d'espace de noms XML) et d'un nom local.</span><span class="sxs-lookup"><span data-stu-id="9d350-106">An XML name consists of an XML namespace (also called an XML namespace URI) and a local name.</span></span> <span data-ttu-id="9d350-107">Un espace de noms XML est similaire à un espace de noms dans un programme [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d350-107">An XML namespace is similar to a namespace in a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]-based program.</span></span> <span data-ttu-id="9d350-108">Il permet de qualifier de manière unique les noms d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="9d350-108">It enables you to uniquely qualify the names of elements and attributes.</span></span> <span data-ttu-id="9d350-109">Cela permet d'éviter les conflits de noms entre différentes parties d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="9d350-109">This helps avoid name conflicts between various parts of an XML document.</span></span> <span data-ttu-id="9d350-110">Lorsque vous avez déclaré un espace de noms XML, vous pouvez sélectionner un nom local qui n'exige d'être unique que dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9d350-110">When you have declared an XML namespace, you can select a local name that only has to be unique within that namespace.</span></span>  
  
 <span data-ttu-id="9d350-111">Un autre aspect des noms XML est XML *les préfixes d’espace de noms*.</span><span class="sxs-lookup"><span data-stu-id="9d350-111">Another aspect of XML names is XML *namespace prefixes*.</span></span> <span data-ttu-id="9d350-112">Les préfixes XML sont la cause de la plupart de la complexité des noms XML.</span><span class="sxs-lookup"><span data-stu-id="9d350-112">XML prefixes cause most of the complexity of XML names.</span></span> <span data-ttu-id="9d350-113">Ces préfixes vous permettent de créer un raccourci pour un espace de noms XML, ce qui rend le document XML plus concis et plus compréhensible.</span><span class="sxs-lookup"><span data-stu-id="9d350-113">These prefixes enable you to create a shortcut for an XML namespace, which makes the XML document more concise and understandable.</span></span> <span data-ttu-id="9d350-114">Toutefois, la signification des préfixes XML dépend de leur contexte, ce qui augmente la complexité.</span><span class="sxs-lookup"><span data-stu-id="9d350-114">However, XML prefixes depend on their context to have meaning, which adds complexity.</span></span> <span data-ttu-id="9d350-115">Par exemple, le préfixe XML `aw` pourrait être associé à un espace de noms XML dans une partie d'une arborescence XML et à un espace de noms XML différent dans une autre partie de l'arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="9d350-115">For example, the XML prefix `aw` could be associated with one XML namespace in one part of an XML tree, and with a different XML namespace in a different part of the XML tree.</span></span>  
  
 <span data-ttu-id="9d350-116">Lorsque vous utilisez [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] avec Visual Basic et des littéraux XML, vous devez utiliser des préfixes d’espace de noms lorsque vous travaillez avec des documents dans des espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="9d350-116">When using [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] with Visual Basic and XML literals, you must use namespace prefixes when working with documents in namespaces.</span></span>  
  
 <span data-ttu-id="9d350-117">Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], la classe qui représente les noms XML est <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9d350-117">In [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the class that represents XML names is <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="9d350-118">Les noms XML apparaissent fréquemment dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, et chaque fois qu’un nom XML est requis, vous trouverez un <xref:System.Xml.Linq.XName>paramètre.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9d350-118">XML names appear frequently throughout the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, and wherever an XML name is required, you will find an <xref:System.Xml.Linq.XName> parameter.</span></span> <span data-ttu-id="9d350-119">Toutefois, vous travaillez rarement directement avec un <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9d350-119">However, you rarely work directly with an <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="9d350-120"><xref:System.Xml.Linq.XName>contient une conversion implicite de chaîne.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9d350-120"><xref:System.Xml.Linq.XName> contains an implicit conversion from string.</span></span>  
  
 <span data-ttu-id="9d350-121">Pour plus d’informations, consultez <xref:System.Xml.Linq.XNamespace>et <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="9d350-121">For more information, see <xref:System.Xml.Linq.XNamespace> and <xref:System.Xml.Linq.XName>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d350-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d350-122">See Also</span></span>  
 [<span data-ttu-id="9d350-123">Utilisation des espaces de noms XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d350-123">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
