---
title: "Sérialisation vers des fichiers, TextWriters et XmlWriters1"
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
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
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
ms.openlocfilehash: 94a2b3e16703496d2e59b08677395db30d944d56
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="14b74-102">Sérialisation vers des fichiers, TextWriters et XmlWriters</span><span class="sxs-lookup"><span data-stu-id="14b74-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="14b74-103">Vous pouvez sérialiser des arborescences XML vers un objet <xref:System.IO.File>, <xref:System.IO.TextWriter> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="14b74-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="14b74-104">Vous pouvez sérialiser n'importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, vers une chaîne à l'aide de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="14b74-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="14b74-105">Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="14b74-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="14b74-106">Le comportement par défaut lors de la sérialisation vers un fichier consiste à mettre en forme (mettre en retrait) le document XML obtenu.</span><span class="sxs-lookup"><span data-stu-id="14b74-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="14b74-107">Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="14b74-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="14b74-108">Pour sérialiser avec la mise en forme, utilisez l'une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="14b74-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 <span data-ttu-id="14b74-109">Si vous souhaitez avoir l'option de ne pas mettre en retrait et de conserver les espaces blancs non significatifs dans l'arborescence XML, utilisez l'une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions> comme argument :</span><span class="sxs-lookup"><span data-stu-id="14b74-109">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 <span data-ttu-id="14b74-110">Pour obtenir des exemples, consultez la rubrique de référence appropriée.</span><span class="sxs-lookup"><span data-stu-id="14b74-110">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b74-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14b74-111">See Also</span></span>  
 [<span data-ttu-id="14b74-112">Sérialisation d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="14b74-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

