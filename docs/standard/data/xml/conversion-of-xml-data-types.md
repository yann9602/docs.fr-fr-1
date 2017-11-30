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
# <a name="conversion-of-xml-data-types"></a>Conversion des types de données XML
La plupart des méthodes se trouve dans un **XmlConvert** classe sont utilisées pour convertir des données entre des chaînes et des formats de fortement typée. Ces méthodes sont indépendantes des paramètres régionaux. Cela signifie qu'elles ne prennent pas en compte les paramètres régionaux éventuels lors de la conversion.  
  
## <a name="reading-string-as-types"></a>Lecture de chaînes comme des types  
 L’exemple suivant lit une chaîne et la convertit en un **DateTime** type.  
  
 En supposant l'entrée XML suivante :  
  
 **Entrée**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Ce code convertit la chaîne à la **DateTime** format :  
  
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
  
## <a name="writing-strings-as-types"></a>Écriture de chaînes comme des types  
 L’exemple suivant lit un **Int32** et la convertit en une chaîne.  
  
 En supposant l'entrée XML suivante :  
  
 **Entrée**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Ce code convertit la **Int32** dans un **chaîne**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion de chaînes en Types de données .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [Conversion de Types .NET Framework en chaînes](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
