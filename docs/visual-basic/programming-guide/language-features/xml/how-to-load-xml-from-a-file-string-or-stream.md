---
title: "Comment : charger du code XML à partir d’un fichier, une chaîne ou un flux de données (Visual Basic) | Documents Microsoft"
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
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 6361ef29b88b4a05b774cf67ca0f3832a8e214fa
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="83c4a-102">Comment : charger du code XML à partir d'un fichier, d'une chaîne ou d'un flux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83c4a-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="83c4a-103">Vous pouvez créer [littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) et les remplir avec le contenu à partir d’une source externe, comme un fichier, une chaîne ou un flux de données à l’aide de plusieurs méthodes.</span><span class="sxs-lookup"><span data-stu-id="83c4a-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="83c4a-104">Ces méthodes sont illustrées dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="83c4a-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="83c4a-105">Charger XML à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="83c4a-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="83c4a-106">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet à partir d’un fichier, utilisez la `Load` méthode.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="83c4a-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="83c4a-107">Cette méthode peut prendre un chemin d’accès de fichier, un flux de texte ou un flux de données XML comme entrée.</span><span class="sxs-lookup"><span data-stu-id="83c4a-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="83c4a-108">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Load%28System.String%29>méthode pour remplir un <xref:System.Xml.Linq.XDocument>objet XML à partir d’un fichier texte.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Load%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="83c4a-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     <span data-ttu-id="83c4a-109">[!code-vb[VbXMLSamples&#43;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="83c4a-109">[!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]</span></span>  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="83c4a-110">Charger XML à partir d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="83c4a-110">To load XML from a string</span></span>  
  
-   <span data-ttu-id="83c4a-111">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>de l’objet à partir d’une chaîne, vous pouvez utiliser la `Parse` méthode.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="83c4a-111">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="83c4a-112">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName>méthode pour remplir un <xref:System.Xml.Linq.XDocument>objet XML à partir d’une chaîne.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-112">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     <span data-ttu-id="83c4a-113">[!code-vb[VbXMLSamples&#47;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="83c4a-113">[!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]</span></span>  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="83c4a-114">Charger XML à partir d’un flux de données</span><span class="sxs-lookup"><span data-stu-id="83c4a-114">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="83c4a-115">Pour remplir un littéral XML tel qu’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>de l’objet à partir d’un flux de données, vous pouvez utiliser la `Load` (méthode) ou la <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>méthode.</xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="83c4a-115">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="83c4a-116">L’exemple de code suivant illustre l’utilisation de la <xref:System.Xml.Linq.XNode.ReadFrom%2A>méthode pour remplir un <xref:System.Xml.Linq.XDocument>objet XML à partir d’un flux XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XNode.ReadFrom%2A></span><span class="sxs-lookup"><span data-stu-id="83c4a-116">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 <span data-ttu-id="83c4a-117">[!code-vb[VbXMLSamples&#46;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="83c4a-117">[!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c4a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83c4a-118">See Also</span></span>  
 <span data-ttu-id="83c4a-119"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-119"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="83c4a-120"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-120"><xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="83c4a-121"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-121"><xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="83c4a-122"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-122"><xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="83c4a-123"><xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="83c4a-123"><xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="83c4a-124"> [Littéraux XML](../../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="83c4a-124"> [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="83c4a-125"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="83c4a-125"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="83c4a-126"> [Manipulation de XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="83c4a-126"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)</span></span>

