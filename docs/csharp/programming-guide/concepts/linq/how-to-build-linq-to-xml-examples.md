---
title: "Guide pratique pour générer des exemples LINQ to XML (C#)"
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
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
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
ms.openlocfilehash: d95748a69ac42f1c767dcf19c9f6d2edc8c872ee
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="3f443-102">Guide pratique pour générer des exemples LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3f443-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="3f443-103">Les différents extraits et exemples présentés dans cette documentation utilisent des classes et des types de différents espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="3f443-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="3f443-104">Lors de la compilation de code Visual C#, vous devez fournir des directives `using` appropriées.</span><span class="sxs-lookup"><span data-stu-id="3f443-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f443-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f443-105">Example</span></span>  
 <span data-ttu-id="3f443-106">Le code suivant contient les directives `using` requises pour la génération et l'exécution des exemples C#.</span><span class="sxs-lookup"><span data-stu-id="3f443-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="3f443-107">Toutes les directives `using` ne sont pas requises pour tous les exemples.</span><span class="sxs-lookup"><span data-stu-id="3f443-107">Not all `using` directives are required for every example.</span></span>  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f443-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f443-108">See Also</span></span>  
 [<span data-ttu-id="3f443-109">Vue d’ensemble de la programmation LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3f443-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

