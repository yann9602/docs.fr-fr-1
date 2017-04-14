---
title: "Modification des d&#233;clarations d&#39;espace de noms dans un document XML | Microsoft Docs"
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
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Modification des d&#233;clarations d&#39;espace de noms dans un document XML
**XmlDocument** expose des déclarations d'espace de noms et des attributs **xmlns** dans le cadre du modèle objet de document.  Ceux\-ci sont stockés dans **XmlDocument**, c'est pourquoi le document, lorsqu'il est enregistré, peut préserver l'emplacement de ces attributs.  Modifier ces attributs n'a aucun effet sur les propriétés **Name**, **NamespaceURI** et **Prefix** d'autres nœuds figurant déjà dans l'arborescence.  Par exemple, si vous chargez le document suivant, l'élément `test` a un **NamespaceURI** `123.`  
  
```  
<test xmlns="123"/>  
```  
  
 Si vous supprimez l'attribut `xmlns` comme suit, l'élément `test` a encore un **NamespaceURI** de `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 De même, si vous ajoutez un autre attribut `xmlns` à l'élément `doc` comme suit, l'élément `test` a encore le **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 C'est pourquoi, la modification d'attributs `xmlns` n'a aucune incidence tant que vous n'avez pas enregistré et rechargé l'objet **XmlDocument**.  
  
## Voir aussi  
 [DOM \(Document Object Model\) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)