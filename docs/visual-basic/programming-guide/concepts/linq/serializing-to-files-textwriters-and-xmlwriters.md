---
title: "Sérialisation vers des fichiers, TextWriters et XmlWriters3 | Documents Microsoft"
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
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
ms.openlocfilehash: f8f8672004b0704b00ff60e5b58256f664bcbd82
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a><span data-ttu-id="6926c-102">Sérialisation vers des fichiers, TextWriters et XmlWriters</span><span class="sxs-lookup"><span data-stu-id="6926c-102">Serializing to Files, TextWriters, and XmlWriters</span></span>
<span data-ttu-id="6926c-103">Vous pouvez sérialiser des arborescences XML vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter>, ou un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="6926c-103">You can serialize XML trees to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="6926c-104">Vous pouvez sérialiser n’importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument>et <xref:System.Xml.Linq.XElement>, en une chaîne à l’aide de la `ToString` méthode.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="6926c-104">You can serialize any XML component, including <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement>, to a string by using the `ToString` method.</span></span>  
  
 <span data-ttu-id="6926c-105">Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>méthode.</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6926c-105">If you want to suppress formatting when serializing to a string, you can use the <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="6926c-106">Comportement Thedefault lors de la sérialisation vers un fichier consiste à mettre en forme (en retrait) le code XML résultant document.</span><span class="sxs-lookup"><span data-stu-id="6926c-106">Thedefault behavior when serializing to a file is to format (indent) the resulting XML document.</span></span> <span data-ttu-id="6926c-107">Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="6926c-107">When you indent, the insignificant white space in the XML tree is not preserved.</span></span> <span data-ttu-id="6926c-108">Pour sérialiser avec mise en forme, utilisez une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions>en tant qu’argument :</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="6926c-108">To serialize with formatting, use one of the overloads of the following methods that do not take <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="6926c-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6926c-109"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="6926c-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6926c-110"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="6926c-111">Si vous souhaitez que l’option ne pas pour mettre en retrait et de conserver les espaces non significatifs dans l’arborescence XML, utilisez une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions>en tant qu’argument :</xref:System.Xml.Linq.SaveOptions></span><span class="sxs-lookup"><span data-stu-id="6926c-111">If you want the option not to indent and to preserve the insignificant white space in the XML tree, use one of the overloads of the following methods that takes <xref:System.Xml.Linq.SaveOptions> as an argument:</span></span>  
  
-   <span data-ttu-id="6926c-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6926c-112"><xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></span></span>  
  
-   <span data-ttu-id="6926c-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6926c-113"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></span></span>  
  
 <span data-ttu-id="6926c-114">Pour obtenir des exemples, consultez la rubrique de référence appropriée.</span><span class="sxs-lookup"><span data-stu-id="6926c-114">For examples, see the appropriate reference topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6926c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6926c-115">See Also</span></span>  
 [<span data-ttu-id="6926c-116">Sérialisation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6926c-116">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
