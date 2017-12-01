---
title: "Comparaison d'objets à l'aide de XmlNameTable"
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
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a>Comparaison d'objets à l'aide de XmlNameTable
**XmlDocument**, lors de la création, une table de noms créée spécifiquement pour ce document. Lorsque XML est chargé dans le document ou de nouveaux éléments ou attributs sont créés, les noms d’élément et d’attribut sont placés dans le **XmlNameTable**. Vous pouvez également créer un **XmlDocument** utilisant un existant **NameTable** à partir d’un autre document. Lorsque **XmlDocument** sont créés avec le constructeur qui prend un **XmlNameTable** paramètre, le document a accès aux noms de nœud, les espaces de noms et les préfixes déjà stockés dans le  **XmlNameTable**. Quelle que soit la manière dont les noms sont chargés dans la table de noms, une fois les noms stockés dans la table, ils peuvent être comparés rapidement par la comparaison d'objets et non au moyen de la comparaison de chaînes. Chaînes peuvent également être ajoutés à la table de nom à l’aide du <xref:System.Xml.NameTable.Add%2A>. L’exemple de code suivant montre une table de noms en cours de création et de la chaîne **MyString** ajoutées à la table. Après cela, une **XmlDocument** est créé à l’aide de cette table et les noms d’élément et d’attribut dans **Myfile.xml** sont ajoutés à la table de noms existant.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 L'exemple de code suivant illustre la création d'un document, l'ajout de deux nouveaux éléments au document, qui les ajoute par ailleurs à sa table de noms, et l'exécution d'une comparaison d'objets sur les noms.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 Le scénario ci-avant, qui montre une table de noms passée entre deux documents, est courant lorsque le même type de document est traité de façon répétée (tel que des documents de commande sur un site de commerce électronique), ces documents étant conformes à un schéma en langage XSD (XML Schema Definition) ou une définition de type de document (DTD) et contenant une répétition des mêmes chaînes. L'utilisation de la même table de noms permet d'améliorer les performances puisque le même nom d'élément se retrouve dans plusieurs documents.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
