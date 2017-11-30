---
title: "Création d'un document XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="e5c54-102">Création d'un document XML</span><span class="sxs-lookup"><span data-stu-id="e5c54-102">XML Document Creation</span></span>
<span data-ttu-id="e5c54-103">Il existe deux façons de créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="e5c54-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="e5c54-104">Consiste à créer un **XmlDocument** sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="e5c54-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="e5c54-105">L’autre manière consiste à créer un **XmlDocument** et passer à XmlNameTable sous la forme d’un paramètre.</span><span class="sxs-lookup"><span data-stu-id="e5c54-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="e5c54-106">L’exemple suivant montre comment créer un vide **XmlDocument** sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="e5c54-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="e5c54-107">Une fois qu’un document est créé, vous pouvez le charger avec des données à partir d’une chaîne, flux, URL, lecteur de texte, ou un **XmlReader** dérivés à l’aide de la classe le **charger** (méthode).</span><span class="sxs-lookup"><span data-stu-id="e5c54-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="e5c54-108">Il existe également une autre méthode de chargement, le **LoadXML** (méthode), qui lit du XML à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e5c54-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="e5c54-109">Pour plus d’informations sur les différents **charge** méthodes, consultez [la lecture d’un Document XML dans le DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e5c54-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="e5c54-110">Il existe une classe appelée le **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="e5c54-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="e5c54-111">Cette classe est une table d'objets chaîne atomisés.</span><span class="sxs-lookup"><span data-stu-id="e5c54-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="e5c54-112">Cette table constitue un moyen efficace pour que l'analyseur XML utilise le même objet chaîne pour tous les noms d'éléments et d'attributs répétés dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="e5c54-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="e5c54-113">Un **XmlNameTable** est automatiquement créé lorsqu’un document est créé comme indiqué ci-dessus et est chargé avec des noms d’élément et d’attribut lorsque le document est chargé.</span><span class="sxs-lookup"><span data-stu-id="e5c54-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="e5c54-114">Si vous disposez déjà d’un document avec une table de noms, et que ces noms pourraient être utiles dans un autre document, vous pouvez créer un document à l’aide du **charge** méthode qui accepte un **XmlNameTable** en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="e5c54-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="e5c54-115">Lorsque le document est créé avec cette méthode, il utilise existants **XmlNameTable** avec tous les attributs et éléments déjà chargés en son sein à partir de l’autre document.</span><span class="sxs-lookup"><span data-stu-id="e5c54-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="e5c54-116">Celui-ci peut être employé pour comparer efficacement des noms d'éléments et d'attributs.</span><span class="sxs-lookup"><span data-stu-id="e5c54-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="e5c54-117">Pour plus d’informations sur la **XmlNameTable**, consultez [comparaison d’objets à l’aide de XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="e5c54-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="e5c54-118">Pour référence, consultez <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="e5c54-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c54-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5c54-119">See Also</span></span>  
 [<span data-ttu-id="e5c54-120">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="e5c54-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
