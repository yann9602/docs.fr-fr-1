---
title: "Modification des déclarations d'espace de noms dans un document XML"
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
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 627882efcbc41310ee177cba984e4add5b07bd15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Modification des déclarations d'espace de noms dans un document XML
Le **XmlDocument** expose des déclarations d’espace de noms et **xmlns** attributs en tant que partie du modèle objet de document. Ils sont stockés dans le **XmlDocument**, de sorte que lorsque vous enregistrez le document, il peut préserver l’emplacement de ces attributs. Modifier ces attributs n’a aucun effet sur le **nom**, **NamespaceURI**, et **préfixe** propriétés d’autres nœuds figurant déjà dans l’arborescence. Par exemple, si vous chargez le document suivant, puis le `test` élément a **NamespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Si vous supprimez le `xmlns` d’attribut, procédez comme suit le `test` élément a toujours la **NamespaceURI** de `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 De même, si vous ajoutez un autre `xmlns` attribut le `doc` élément comme suit, puis le `test` élément a toujours **NamespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Par conséquent, la modification `xmlns` attributs n’a aucun effet jusqu'à ce que vous enregistrerez et recharger le **XmlDocument** objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
