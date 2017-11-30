---
title: "Comment : accéder à des éléments descendants XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="91a66-102">Comment : accéder à des éléments descendants XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91a66-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="91a66-103">Cet exemple montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML qui ont un nom spécifié et qui sont contenus sous un élément XML.</span><span class="sxs-lookup"><span data-stu-id="91a66-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="91a66-104">En particulier, il utilise le `Value` propriété à obtenir la valeur du premier élément dans la collection qui le `name` retourne de propriété d’axe descendant.</span><span class="sxs-lookup"><span data-stu-id="91a66-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="91a66-105">Le `name` propriété d’axe descendant Obtient tous les éléments nommés `name` qui sont contenues dans le `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="91a66-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="91a66-106">Cet exemple utilise également la `phone` propriété d’axe descendant pour accéder à tous les descendants nommés `phone` qui sont contenues dans le `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="91a66-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91a66-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="91a66-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="91a66-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="91a66-108">Compiling the Code</span></span>  
 <span data-ttu-id="91a66-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="91a66-109">This example requires:</span></span>  
  
-   <span data-ttu-id="91a66-110">une référence à l'espace de noms <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="91a66-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a66-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91a66-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="91a66-112">Propriété d’axe descendant XML</span><span class="sxs-lookup"><span data-stu-id="91a66-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [<span data-ttu-id="91a66-113">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="91a66-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="91a66-114">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91a66-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="91a66-115">XML</span><span class="sxs-lookup"><span data-stu-id="91a66-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
