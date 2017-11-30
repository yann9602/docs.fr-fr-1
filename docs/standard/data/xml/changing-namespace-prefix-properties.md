---
title: "Modification des propriétés de préfixe d'espace de noms"
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
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="70298-102">Modification des propriétés de préfixe d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="70298-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="70298-103">Le **XmlNode** classe vous permet de modifier le préfixe d’espace de noms associé à un nœud donné.</span><span class="sxs-lookup"><span data-stu-id="70298-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="70298-104">Par exemple, le code suivant montre la modification du préfixe d'un élément.</span><span class="sxs-lookup"><span data-stu-id="70298-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="70298-105">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="70298-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="70298-106">La modification du préfixe d'un nœud n'entraîne pas la modification de son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="70298-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="70298-107">Ce dernier peut être défini uniquement au moment de la création du nœud.</span><span class="sxs-lookup"><span data-stu-id="70298-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="70298-108">Lorsque vous rendez persistante l'arborescence, de nouveaux attributs d'espace de noms peuvent ne plus être persistants pour satisfaire le préfixe défini.</span><span class="sxs-lookup"><span data-stu-id="70298-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="70298-109">Si le nouvel espace de noms ne peut pas être créé, le préfixe est modifié de telle sorte que le nœud préserve son nom local et son espace de noms.</span><span class="sxs-lookup"><span data-stu-id="70298-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="70298-110">L'exemple suivant illustre l'ajout d'un attribut d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="70298-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="70298-111">**Sortie**</span><span class="sxs-lookup"><span data-stu-id="70298-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="70298-112">Lorsque l’arborescence a été rendue persistante à une chaîne à la suite de l’appel à **doc. InnerXml**, le `xmlns:a='123'` attribut a été ajouté pour préserver l’espace de noms de la `test` élément.</span><span class="sxs-lookup"><span data-stu-id="70298-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="70298-113">Sa valeur était `'123'` et est restée `'123'`.</span><span class="sxs-lookup"><span data-stu-id="70298-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70298-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70298-114">See Also</span></span>  
 [<span data-ttu-id="70298-115">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="70298-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
