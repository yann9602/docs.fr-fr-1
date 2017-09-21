---
title: "Comment : sérialiser un objet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: e988b7b56fca3f7e71c94155086bd242f8f9637b
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-serialize-an-object"></a>Comment : sérialiser un objet
Pour sérialiser un objet, créez tout d'abord l'objet à sérialiser et définissez ses propriétés et champs publics. Pour ce faire, vous devez déterminer le format de transport dans lequel le flux de données XML sera stocké, sous forme de flux de données ou de fichier. Par exemple, si le flux de données XML doit être enregistré dans un formulaire permanent, créez un objet <xref:System.IO.FileStream>.  
  
> [!NOTE]
>  Pour obtenir plus d’exemples de sérialisation XML, consultez [Exemples de sérialisation XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Pour sérialiser un objet  
  
1.  Créez l'objet et définissez ses champs et propriétés publics.  
  
2.  Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type de l'objet. Pour plus d'informations, consultez les constructeurs de classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
3.  Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> pour générer un flux de données XML ou une représentation de fichier des propriétés et des champs publics de l'objet. L'exemple suivant illustre la création d'un fichier.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)   
 [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

