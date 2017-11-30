---
title: "Conversion des types de données XML"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="085dc-102">Conversion des types de données XML</span><span class="sxs-lookup"><span data-stu-id="085dc-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="085dc-103">La plupart des méthodes se trouve dans un **XmlConvert** classe sont utilisées pour convertir des données entre des chaînes et des formats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="085dc-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="085dc-104">Ces méthodes sont indépendantes des paramètres régionaux.</span><span class="sxs-lookup"><span data-stu-id="085dc-104">Methods are locale independent.</span></span> <span data-ttu-id="085dc-105">Cela signifie qu'elles ne prennent pas en compte les paramètres régionaux éventuels lors de la conversion.</span><span class="sxs-lookup"><span data-stu-id="085dc-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="085dc-106">Lecture de chaînes comme des types</span><span class="sxs-lookup"><span data-stu-id="085dc-106">Reading String as types</span></span>  
 <span data-ttu-id="085dc-107">L’exemple suivant lit une chaîne et la convertit en un **DateTime** type.</span><span class="sxs-lookup"><span data-stu-id="085dc-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="085dc-108">En supposant l'entrée XML suivante :</span><span class="sxs-lookup"><span data-stu-id="085dc-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="085dc-109">**Entrée**</span><span class="sxs-lookup"><span data-stu-id="085dc-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="085dc-110">Ce code convertit la chaîne à la **DateTime** format :</span><span class="sxs-lookup"><span data-stu-id="085dc-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="085dc-111">Écriture de chaînes comme des types</span><span class="sxs-lookup"><span data-stu-id="085dc-111">Writing Strings as types</span></span>  
 <span data-ttu-id="085dc-112">L’exemple suivant lit un **Int32** et la convertit en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="085dc-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="085dc-113">En supposant l'entrée XML suivante :</span><span class="sxs-lookup"><span data-stu-id="085dc-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="085dc-114">**Entrée**</span><span class="sxs-lookup"><span data-stu-id="085dc-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="085dc-115">Ce code convertit la **Int32** dans un **chaîne**:</span><span class="sxs-lookup"><span data-stu-id="085dc-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="085dc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="085dc-116">See Also</span></span>  
 [<span data-ttu-id="085dc-117">Conversion de chaînes en Types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="085dc-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="085dc-118">Conversion de Types .NET Framework en chaînes</span><span class="sxs-lookup"><span data-stu-id="085dc-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
