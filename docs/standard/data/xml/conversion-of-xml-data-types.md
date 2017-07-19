---
title: "Conversion des types de donn&#233;es XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Conversion des types de donn&#233;es XML
La majorité des méthodes présentes dans la classe **XmlConvert** sont utilisées pour convertir des données du format de chaînes à un format fortement typé.  Ces méthodes sont indépendantes des paramètres régionaux.  Cela signifie qu'elles ne prennent pas en compte les paramètres régionaux éventuels lors de la conversion.  
  
## Lecture de chaînes comme des types  
 L'exemple suivant lit une chaîne et la convertit en type **DateTime**.  
  
 En supposant l'entrée XML suivante :  
  
 **Entrée**  
  
```  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Ce code convertit la chaîne au format **DateTime** :  
  
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
  
## Écriture de chaînes comme des types  
 L'exemple suivant lit un type **Int32** et le convertit en chaîne.  
  
 En supposant l'entrée XML suivante :  
  
 **Entrée**  
  
```  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Ce code convertit le type **Int32** en type **String**  :  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## Voir aussi  
 [Conversion de chaînes en types de données .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)   
 [Conversion de types .NET Framework en chaînes](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)