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
# <a name="xml-document-creation"></a>Création d'un document XML
Il existe deux façons de créer un document XML. Consiste à créer un **XmlDocument** sans paramètres. L’autre manière consiste à créer un **XmlDocument** et passer à XmlNameTable sous la forme d’un paramètre. L’exemple suivant montre comment créer un vide **XmlDocument** sans paramètres.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Une fois qu’un document est créé, vous pouvez le charger avec des données à partir d’une chaîne, flux, URL, lecteur de texte, ou un **XmlReader** dérivés à l’aide de la classe le **charger** (méthode). Il existe également une autre méthode de chargement, le **LoadXML** (méthode), qui lit du XML à partir d’une chaîne. Pour plus d’informations sur les différents **charge** méthodes, consultez [la lecture d’un Document XML dans le DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Il existe une classe appelée le **XmlNameTable**. Cette classe est une table d'objets chaîne atomisés. Cette table constitue un moyen efficace pour que l'analyseur XML utilise le même objet chaîne pour tous les noms d'éléments et d'attributs répétés dans un document XML. Un **XmlNameTable** est automatiquement créé lorsqu’un document est créé comme indiqué ci-dessus et est chargé avec des noms d’élément et d’attribut lorsque le document est chargé. Si vous disposez déjà d’un document avec une table de noms, et que ces noms pourraient être utiles dans un autre document, vous pouvez créer un document à l’aide du **charge** méthode qui accepte un **XmlNameTable** en tant que paramètre. Lorsque le document est créé avec cette méthode, il utilise existants **XmlNameTable** avec tous les attributs et éléments déjà chargés en son sein à partir de l’autre document. Celui-ci peut être employé pour comparer efficacement des noms d'éléments et d'attributs. Pour plus d’informations sur la **XmlNameTable**, consultez [comparaison d’objets à l’aide de XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Pour référence, consultez <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Voir aussi  
 [Document Object Model (DOM) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
